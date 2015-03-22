---
draft: false
title: How do I keep multiple Ruby projects separate?
date: 2010-12-20
author: Steve Klabnik
categories:
- Beginners
- Popular
- Ruby
- Ruby Masters
layout: post
permalink: /2010/12/20/how-do-i-keep-multiple-ruby-projects-separate/
tags:
- Bundler
- programming
- ruby programming
- rvm
---
## How do I keep multiple Ruby projects separate?

This guest post is by **[Steve
Klabnik](https://github.com/steveklabnik)**, who is a software
craftsman, writer, and former startup CTO. Steve tries to keep his Ruby
consulting hours down so that he can focus on maintaining [Hackety
Hack](http://hackety-hack.com/) and being a core member of Team Shoes,
as well as writing regularly for multiple blogs.

![Steve Klabnik](http://rubylearning.com/images/steve_cropped.jpg) If
you’re anything like me, you’re already starting a new project
immediately after wrapping up the last one. There just aren’t enough
hours in the day to code up all the crazy ideas I have floating around
in my head. Often, these ideas are the result of checking out some fun
new gem, GitHub project, or even a different Ruby. Real quickly, a
problem develops: what happens when these projects interfere with one
another? What if I want to use Ruby 1.8.7 for an older project, Ruby
1.8.5 for a legacy application, Ruby 1.9.2 for the latest and greatest,
and JRuby to use an interesting Ruby library? Luckily, there are a few
things that you can do to isolate your different projects from one
another, and some settings for that will make them quite painless to
use. There are three main things that can go wrong when you try to use
different sets of tools on a per-project basis: conflicts between Ruby
versions, conflicts between gems, and forgetting which tools you use on
which project.

## Ruby Version Conflicts

This is the biggest and most painful kind of problem. If you want to use
Ruby 1.8 for one project and Ruby 1.9 for another, you have a problem.
If you’re using Linux, for example, your package manager may see that
both ruby18 and ruby19 fulfill a ‘ruby’ dependency, and so it won’t let
you have them both installed side by side. The solution isn’t pretty:
install different Rubies from source. This gets ugly really quickly,
because it’s easy to forget where you’ve compiled different Rubies, and
having software outside of your package manager isn’t a great answer. If
you’re on OS X or Windows, you skip right past the package manager
problem and straight to the source ‘solution.’ This is no good!

Luckily, there’s an awesome project by Wayne E. Seguin named
[rvm](http://rvm.beginrescueend.com/). rvm is sort of like a package
manager for Ruby. If you’d like to install both Ruby 1.8.7 and 1.9.2,
just type this in:

    $ rvm install 1.8.7
    $ rvm install 1.9.2

It’ll go fetch the Ruby source code, compile it, and get you all set up.
To use a specific Ruby, you can type ‘use':

    $ rvm use 1.8.7
    $ ruby -v
    ruby 1.8.7 (2010-08-16 patchlevel 302) [i686-darwin10.4.0]
    $ rvm use 1.9.2
    $ ruby -v
    ruby 1.9.2p0 (2010-08-18 revision 29036) [x86_64-darwin10.4.0]

Neat! You can even get other Ruby versions:

    $ rvm install jruby
    $ rvm install rbx
    $ rvm install macruby

You can see a full list of these with ‘rvm list known’. For a full list
of everything that rvm can do, as well as installation instructions,
visit [the rvm website.](http://rvm.beginrescueend.com/)

## Gem Conflicts

Once you’ve gotten your Rubies straight, you can still have conflicts
between different gems that your project needs. One project uses Rails
2.3.8, another uses Rails 3… It gets worse when you have certain gems
installed only as a dependency, and you don’t know exactly which one is
correct:

    $ gem list | grep net-ssh
    net-ssh (2.0.23, 2.0.4, 1.1.4)

rvm has a neat feature called ‘gemsets.’ They let you create separate
sets of gems per Ruby you have installed. This allows you to isolate
each application, giving it its own set of gems. Check it out:

    $ gem list

    *** LOCAL GEMS ***

    aasm (2.1.5)
    abstract (1.0.0)
    acl9 (0.12.0)
    *snip*

    $ rvm gemset create new-gemset
    $ rvm use 1.9.2@new-gemset
    $ gem list

    *** LOCAL GEMS ***

    $

Cool stuff! As you can see, use an ‘@’ symbol to tell rvm which gemset
you’d like to use. Now we’ve isolated each project’s gems from each
other. There is, however, a much more complicated kind of conflicts that
can occur between gems. This happens when two gems have interlocking
dependencies.

Here’s an example of this from the past: ActionPack 2.3.5 requires Rack
=1.0.0, which is the newest version. Unicorn requires Rack \>1.0.0. Rack
releases a new version, 1.1.0. Now, when starting up a Rails
application, the unicorn gem is loaded first, so it loads the newest
version of the gem that works, which is rack-1.1.0. Then rails loads,
and it loads actionpack, which tries to load rack. It needs =1.0.1, but
sees that 1.1.0 has already been loaded, and throws this ugly, ugly
error:

    Gem::LoadError: can't activate rack (~> 1.0.0, runtime)
    for ["actionpack-2.3.5"], already activated rack-1.1.0
    for ["unicorn"]

There’s a set of versions here that works, but the way that the gems are
loaded means that it doesn’t. The problem is that at the time that
unicorn loads, it can’t possibly know that you’re planning on loading a
different version of rack somewhere down the line. What we really need
is a tool that knows about all of our dependencies, and can calculate
the graph of all of our requirements, and figure out which versions of
everything we need, and then only place those versions on the
\$LOAD\_PATH. Luckily, such a project exists:
[bundler](http://gembundler.com/).

To use bundler, you first need to make a file named ‘Gemfile’ in the
root of your project directory. This file looks something like this:

    source "http://rubygems.org"

    gem "rails", "~>3.0.0"

    group :development do
      gem 'sqlite3-ruby', :require => 'sqlite3'
    end

    group :production do
      gem "pg"
    end

The first line tells Bundler where to look for gems. The second line
says that we want to use the ‘rails’ gem, and we want any version that’s
at least 3.0.0 but less than 3.1.0. Finally, the other lines show
‘groups’ of gems: in development, we want to use sqlite3-ruby, and we
need to require it via the name ‘sqlite3′, but we want to use Postgres
in production. To install these gems, just:

    $ bundle install

Bundler gets all the information that it needs on all the gems, figures
out what versions of everything work together, and then installs the
right versions. It then creates a Gemfile.lock file that holds all of
this information. It’s just a simple YAML file, you can open it up and
see the specifics. You’ll want to add the Gemfile and Gemfile.lock into
your version control, so that anyone else that’s developing with you can
also get the same gem versions.

To use the gems in your bundle, just use these two lines:

    require "rubygems"
    require "bundler/setup"

From there, whenever you require a gem, it’ll be the version from the
bundle. If you want Bundler to automatically require all of your gems
for you, just ‘`Bundler.require`‘ and it’ll require the default group of
gems.

Rails 3 automatically comes with a Gemfile and bundler support right out
of the box. If you want to use Bundler with Rails 2.3, check out [the
Bundler site](http://gembundler.com/rails23.html) for setup
instructions.

The combination of gemsets and Bundler will make sure that you don’t
have any nasty gem conflicts. Gemsets keep your projects isolated from
each other, and Bundler keeps your gems’ versions from interfering with
each other. The two work really well together.

## I can’t remember which tool I used!

All of these rubies and gemsets can get confusing. Luckily, rvm has an
awesome feature to take care of this, too: .rvmrc files. If you put a
file named ‘.rvmrc’ in your project’s root directory, when you enter the
project, it’ll switch your Ruby version (and gemset) automatically. It’s
really easy to use, too. Just put the command you’d use to switch in the
file. For example, in the Hackety Hack website project, I have the
following
[.rvmrc](https://github.com/hacketyhack/hackety-hack.com/blob/master/.rvmrc):

    rvm 1.8.7@hackety-hack.com

Astute readers will notice that I left off the ‘use,’ rvm defaults to
‘use’ if you don’t give it a different command. Check it out:

    $ ruby -v
    ruby 1.9.2p0 (2010-08-18 revision 29036) [x86_64-darwin10.4.0]
    $ cd hackety-hack.com
    $ ruby -v
    ruby 1.8.7 (2010-08-16 patchlevel 302) [i686-darwin10.4.0]

Super cool. Now you’ll never forget which Ruby you were using, and you
don’t even need to switch manually. This is one of the first things that
I do when I start a new project in Ruby: Pick a Ruby version, make a
gemset with the same name as the project, and set up an .rvmrc. It’s
saved me hours of time and headaches.

## Multiple projects: super simple

rvm is a fantastic tool to help solve your multiple-ruby woes. It really
does make using multiple kinds of Ruby really, really easy. And Bundler
makes sure that your gems play nice togther. It’s a great time to be a
Rubyist.

*I hope you found this article valuable. Feel free to ask questions and
give feedback in the comments section of this post. Thanks!*
