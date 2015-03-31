---
draft: false
title: Does ROR deployment deprive YOU of your sleep?
date: 2010-10-08
author: Fabio Akita
categories:
- Beginners
- Ruby
- Ruby Masters
layout: post
permalink: /2010/10/08/does-ror-deployment-deprive-you-of-your-sleep/
tags:
- fabio akita
- Inploy
- programming
- Ruby
- Ruby Beginners
- Ruby for Noobs
---

This guest post is contributed by **Fabio Akita**, who works as Project
Manager for GoNow Tecnologia, in Brazil, leading Ruby on Rails projects.
He worked for Locaweb, the largest web hosting company in Latin America
where he helped implement the support for Rails in a shared web hosting
for the first time. He and Locaweb also joined forces to create the<!--more-->
successful Rails Summit Conference which now changed to RubyConf Brasil.
He worked as Brazil Rails Practice Manager for Surgeworks LLC. Fabio
travelled all around Brazil evangelizing the Ruby on Rails Ecosystem and
modern Agile-based best practices for project management. He blogs at
[AkitaOnRails.com](http://akitaonrails.com/).

## Inploy: The No Brainer Deployment Solution

Ruby on Rails deployment is something that has been constantly evolving
over the years. For many people "deployment" still means connecting
through FTP to a remote server and dragging and dropping a bunch of
files to a folder.

You can certainly do something similar with Rails. Products such as
[Phusion Passenger](http://www.modrails.com/) for Apache/Nginx makes
this process easier: you just define a folder and drop files in there.

![Fabio
Akita](http://rubylearning.com/blog/wp-content/uploads/Fabio-Akita.jpeg "Fabio Akita")

Problem is, this is usually not something you do just once. You will fix
bugs, improve your code, add new features, and you will keep on
redeploying, overwriting old files and so on. The process of manually
moving files around for deployment, even for small websites, can lead to
unexpected human failure and, so, sleep deprivation, which is bad. So
this process is not recommended and considered a big liability. Rule of
thumb: *thou shall not update production servers manually*.

We all had bad experiences like this before. We also know that the best
route for a safe deployment is proper automation. System administrators
should always strive to automate as much as possible. If you are
repeating trivial tasks manually, you are probably doing it wrong.

We have the hardcore tools such as Puppet and Chef, but for small to
medium deployments we always relied on the good old Capistrano. For a
long time it was the de facto way to automate deployments, even to many
machines. It was able to do the initial setup, push new versions of your
apps to your production machines reliably and even to maintain old
versions so you could easily rollback to a working version with a single
command.

Capistrano, created and maintained by Rails Core Team Alumni Jamis Buck,
was a great tool. It helped perfect the Net::SSH libraries so you can
script SSH connections through Ruby.

But we learned new tricks. One big change since then is that we started
adopting Git as the version control system of choice. We can leverage
the same thing that Capistrano provided in a much simpler way leveraging
tools such as Git to simplify the whole process.

Thus, **[Inploy](http://github.com/dcrec1/inploy)** was born, by the
skillful hands of [Diego Carrion](http://www.mouseoverstudio.com/blog/).
His intentions were clear: Capistrano is way big and complex for simpler
deployments. You need to customize too much for stuff that could have
been the default way of doing things. *Convention over Configuration*,
that's what Inploy is all about.

Right now it supports Mongrel, Thin, Passenger and Unicorn. It assumes
you are using Git. It already defines many tasks that can be executed
either remotely or locally, such as restarting the web application
server's processes or running Rails' database migrations. It also
supports templates, so that you can reuse a specific deployment strategy
across many hosting solutions. It doesn't have nearly as many options as
Capistrano, so it is not a full replacement. This is an alternative for
small to medium deployments.

To be a competent Ruby on Rails developer, we always assume that you
already know the basics of system administration at the very least, such
as installing and hardening your own Linux box, installing and
configuring a web server, installing a database system, setting up your
firewall and so on, so I won't detail into those simple tasks.

Because Inploy aims for simplicity, even its source code is very minimal
and you can skim through it very easily. So I recommend you take a look
at it to understand its features and how it is organized. Just to give
you an idea, the entire project, if you count raw lines and add the
specs and tests, has less than 1.5k lines of code.

You can install Inploy as a gem:

    gem install inploy

Then, in your Rails project, you need to create a `config/deploy.rb`
file. You should have something like this:

    application = "signal"
    repository = 'git://github.com/dcrec1/signal.git'
    hosts = ['hooters', 'geni']

    #path = '/var/local/apps'
    #user = 'deploy'
    #ssh_opts = ''
    #branch = 'master'
    #sudo = false
    #cache_dirs = %w(public/cache)
    #skip_steps = nil
    #app_folder = nil

The best way to understand these options is to actually read the
`lib/deploy.rb` from the Inploy project, which has only 100 lines of
code. Then you will start figuring out where and how those variables are
used. For example:

    def remote_setup
      remote_run "cd #{path} && #{@sudo}git clone --depth 1 #{repository} #{application} && cd #{application_folder} #{checkout}#{bundle} && #{@sudo}rake inploy:local:setup environment=#{environment}#{skip_steps_cmd}"
    end

The `remote_run` method will connect to all the hosts defined in the
`hosts` array and execute the following command. Then the variables are
used to create the `git clone` task. Notice that it also runs the
`inploy:local:setup` Rake task. It is there if you need -- for some
reason -- to manually log in the server and run
`rake inploy:local:setup`.

The DSL is very simple and is entirely based on Module Mixins. Therefore
you can also create **Templates**, which are simple Ruby Modules that
override the default methods. That way you can customize Inploy for any
specific Web Hosting provider and mix in to your `config/deploy.rb`
file.

Once you configure the `config/deploy.rb` file, you will have to run
this command just once:

    inploy setup

This will connect to all the hosts specified in the configuration file,
and make the initial setups.

Then, every time you need to redeploy, you just run this command:

    inploy

Under the hood, the setup task will create a git clone from the git
repository you specified (make sure both your development machine and
your production server have access to this git repository). Then, when
you redeploy it is just a matter of running `git pull` to get the newest
code and run maintenance tasks such as `db:migrate`

There are a lot of tasks Inploy already automate out of the box such as
running asset packager if you are using it, informing HopToad if you're
using it and so on. You can override the `before_restarting_server` if
you want to add more update tasks or you can override the entire
`after_update_code` method to add your own sequence of update tasks.

The most current version also includes a **Rails 3 Push** template
strategy. You can simply add this line at the top of your
`config/deploy.rb` file:

    template = "rails3_push"

Now the `inploy setup` command will configure an inplace Git repository
approach. It will create a Git repository directly on your production
machine. Then every time you run the `inploy` command it will `git push`
your new commits to this repository. Then, there is no step 3! It
doesn't need to `git pull` because you already pushed to the location
where your web server is already pointing at. This is a very simple,
Heroku-like, kind of deployment.

And if you have an empty box, with only SSH enabled, you can still
automate the installation of packages and other stuff through a web
available script. For example, let's say you have a web server that
contains recipes (Bash scripts) at `http://myserver.com/myscript`. You
can execute it on your empty box like this:

    inploy install from=http://myserver.com/myscript

And then you can do `inploy setup` and `inploy` as usual.

One of most notable omissions from Inploy, compared to Capistrano, is
the equivalent to `cap rollback`. The entire directory structure and
symlink strategy used by Capistrano is done in such a way to make it
easier to rollback to previous versions by creating time stamped folders
and symlinks to point to the current version.

It is a clever strategy, but maybe a bit too much for small/medium
projects. If you already have Git and you already tag the versions
properly, it is only a matter of `git checkout old_tag` to rollback to a
previous version.

Inploy, by itself, does not implement a `rollback` option because it was
never requested so, which means that this is a feature that people
rarely use. Most of the time, if you do proper testing and continuous
integration, you can safely assume that it wouldn't break in production.
This is not 100%, of course, but it means that the chance of you needing
a rollback feature is drastically diminished.

As you can see, Inploy is a very pragmatic, thin wrapper around SSH
automation, that is very easy to set up and use. Try to study the
[source code](http://github.com/dcrec1/inploy), you will be surprised to
be able to understand it very easily and quickly customize it for your
particular needs.

*I hope you found this article valuable. Feel free to ask questions and
give feedback in the comments section of this post. Thanks!*

***Do read* these awesome Guest Posts:**

-   [Do YOU know Ruby's 'Chainsaw'
    method?](http://rubylearning.com/blog/2010/10/07/do-you-know-rubys-chainsaw-method/)
-   [An introduction to eventmachine, and how to avoid callback
    spaghetti](http://rubylearning.com/blog/2010/10/01/an-introduction-to-eventmachine-and-how-to-avoid-callback-spaghetti/)
-   [The Testing
    Mindset](http://rubylearning.com/blog/2010/09/30/the-testing-mindset/)
-   [An Introduction to Desktop Apps with
    Ruby](http://rubylearning.com/blog/2010/09/29/an-introduction-to-desktop-apps-with-ruby/)
-   [The Ruby
    movement](http://rubylearning.com/blog/2010/09/28/the-ruby-movement/)
-   [Almost everything is an object (and everything is almost an
    object!)](http://rubylearning.com/blog/2010/09/27/almost-everything-is-an-object-and-everything-is-almost-an-object/)
-   [So... you're new to
    Ruby!](http://rubylearning.com/blog/2010/09/24/so-youre-new-to-ruby/)
-   [Incorporating Web APIs to spark computer programming
    exercises](http://rubylearning.com/blog/2010/09/23/incorporating-web-apis-to-spark-computer-programming-exercises/)
-   [14 Ways To Have Fun Coding
    Ruby](http://rubylearning.com/blog/2010/09/22/14-ways-to-have-fun-coding-ruby/)
-   [Writing modular web applications with
    Rack](http://rubylearning.com/blog/2010/09/21/writing-modular-web-applications-with-rack/)
-   [How to Learn Ruby (or any programming
    language)](http://rubylearning.com/blog/2010/09/20/how-to-learn-ruby-or-any-programming-language/)

