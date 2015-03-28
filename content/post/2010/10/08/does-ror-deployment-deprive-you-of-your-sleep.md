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
topsy_short_url:
- http://bit.ly/d8v2FW
---

<div>
  <h3>
    Inploy: The No Brainer Deployment Solution
  </h3>
  
  <p class="update">
    This guest post is contributed by <strong>Fabio Akita</strong>, who works as Project Manager for GoNow Tecnologia, in Brazil, leading Ruby on Rails projects. He worked for Locaweb, the largest web hosting company in Latin America where he helped implement the support for Rails in a shared web hosting for the first time. He and Locaweb also joined forces to create the successful Rails Summit Conference which now changed to RubyConf Brasil. He worked as Brazil Rails Practice Manager for Surgeworks LLC. Fabio travelled all around Brazil evangelizing the Ruby on Rails Ecosystem and modern Agile-based best practices for project management. He blogs at <a href="http://akitaonrails.com/">AkitaOnRails.com</a>.
  </p>
  
  <p>
    <span class="drop_cap">R</span>uby on Rails deployment is something that has been constantly evolving over the years. For many people &#8220;deployment&#8221; still means connecting through FTP to a remote server and dragging and dropping a bunch of files to a folder.
  </p>
  
  <p>
    You can certainly do something similar with Rails. Products such as <a href="http://www.modrails.com/">Phusion Passenger</a> for Apache/Nginx makes this process easier: you just define a folder and drop files in there.
  </p>
  
  <p class="block">
    <img class="size-full wp-image-4989 alignright" src="http://rubylearning.com/blog/wp-content/uploads/Fabio-Akita.jpeg" alt="Fabio Akita" title="Fabio Akita" width="200" height="256" />
  </p>
  
  <p>
    Problem is, this is usually not something you do just once. You will fix bugs, improve your code, add new features, and you will keep on redeploying, overwriting old files and so on. The process of manually moving files around for deployment, even for small websites, can lead to unexpected human failure and, so, sleep deprivation, which is bad. So this process is not recommended and considered a big liability. Rule of thumb: <em>thou shall not update production servers manually</em>.
  </p>
  
  <p>
    We all had bad experiences like this before. We also know that the best route for a safe deployment is proper automation. System administrators should always strive to automate as much as possible. If you are repeating trivial tasks manually, you are probably doing it wrong.
  </p>
  
  <p>
    We have the hardcore tools such as Puppet and Chef, but for small to medium deployments we always relied on the good old Capistrano. For a long time it was the de facto way to automate deployments, even to many machines. It was able to do the initial setup, push new versions of your apps to your production machines reliably and even to maintain old versions so you could easily rollback to a working version with a single command.
  </p>
  
  <p>
    Capistrano, created and maintained by Rails Core Team Alumni Jamis Buck, was a great tool. It helped perfect the Net::SSH libraries so you can script SSH connections through Ruby.
  </p>
  
  <p>
    But we learned new tricks. One big change since then is that we started adopting Git as the version control system of choice. We can leverage the same thing that Capistrano provided in a much simpler way leveraging tools such as Git to simplify the whole process.
  </p>
  
  <p>
    Thus, <strong><a href="http://github.com/dcrec1/inploy">Inploy</a></strong> was born, by the skillful hands of <a href="http://www.mouseoverstudio.com/blog/">Diego Carrion</a>. His intentions were clear: Capistrano is way big and complex for simpler deployments. You need to customize too much for stuff that could have been the default way of doing things. <em>Convention over Configuration</em>, that&#8217;s what Inploy is all about.
  </p>
  
  <p>
    Right now it supports Mongrel, Thin, Passenger and Unicorn. It assumes you are using Git. It already defines many tasks that can be executed either remotely or locally, such as restarting the web application server&#8217;s processes or running Rails&#8217; database migrations. It also supports templates, so that you can reuse a specific deployment strategy across many hosting solutions. It doesn&#8217;t have nearly as many options as Capistrano, so it is not a full replacement. This is an alternative for small to medium deployments.
  </p>
  
  <p>
    To be a competent Ruby on Rails developer, we always assume that you already know the basics of system administration at the very least, such as installing and hardening your own Linux box, installing and configuring a web server, installing a database system, setting up your firewall and so on, so I won&#8217;t detail into those simple tasks.
  </p>
  
  <p>
    Because Inploy aims for simplicity, even its source code is very minimal and you can skim through it very easily. So I recommend you take a look at it to understand its features and how it is organized. Just to give you an idea, the entire project, if you count raw lines and add the specs and tests, has less than 1.5k lines of code.
  </p>
  
  <p>
    You can install Inploy as a gem:
  </p>
  
  <pre>gem install inploy</pre>
  
  <p>
    Then, in your Rails project, you need to create a <tt>config/deploy.rb</tt> file. You should have something like this:
  </p>
  
  <pre>application = "signal"
repository = 'git://github.com/dcrec1/signal.git'
hosts = ['hooters', 'geni']

#path = '/var/local/apps'
#user = 'deploy'
#ssh_opts = ''
#branch = 'master'
#sudo = false
#cache_dirs = %w(public/cache)
#skip_steps = nil
#app_folder = nil</pre>
  
  <p>
    The best way to understand these options is to actually read the <tt>lib/deploy.rb</tt> from the Inploy project, which has only 100 lines of code. Then you will start figuring out where and how those variables are used. For example:
  </p>
  
  <pre>def remote_setup
  remote_run "cd #{path} && #{@sudo}git clone --depth 1 #{repository} #{application} && cd #{application_folder} #{checkout}#{bundle} && #{@sudo}rake inploy:local:setup environment=#{environment}#{skip_steps_cmd}"
end</pre>
  
  <p>
    The <tt>remote_run</tt> method will connect to all the hosts defined in the <tt>hosts</tt> array and execute the following command. Then the variables are used to create the <tt>git clone</tt> task. Notice that it also runs the <tt>inploy:local:setup</tt> Rake task. It is there if you need &#8211; for some reason &#8211; to manually log in the server and run <tt>rake inploy:local:setup</tt>.
  </p>
  
  <p>
    The DSL is very simple and is entirely based on Module Mixins. Therefore you can also create <strong>Templates</strong>, which are simple Ruby Modules that override the default methods. That way you can customize Inploy for any specific Web Hosting provider and mix in to your <tt>config/deploy.rb</tt> file.
  </p>
  
  <p>
    Once you configure the <tt>config/deploy.rb</tt> file, you will have to run this command just once:
  </p>
  
  <pre>inploy setup</pre>
  
  <p>
    This will connect to all the hosts specified in the configuration file, and make the initial setups.
  </p>
  
  <p>
    Then, every time you need to redeploy, you just run this command:
  </p>
  
  <pre>inploy</pre>
  
  <p>
    Under the hood, the setup task will create a git clone from the git repository you specified (make sure both your development machine and your production server have access to this git repository). Then, when you redeploy it is just a matter of running <tt>git pull</tt> to get the newest code and run maintenance tasks such as <tt>db:migrate</tt>
  </p>
  
  <p>
    There are a lot of tasks Inploy already automate out of the box such as running asset packager if you are using it, informing HopToad if you&#8217;re using it and so on. You can override the <tt>before_restarting_server</tt> if you want to add more update tasks or you can override the entire <tt>after_update_code</tt> method to add your own sequence of update tasks.
  </p>
  
  <p>
    The most current version also includes a <strong>Rails 3 Push</strong> template strategy. You can simply add this line at the top of your <tt>config/deploy.rb</tt> file:
  </p>
  
  <pre>template = "rails3_push"</pre>
  
  <p>
    Now the <tt>inploy setup</tt> command will configure an inplace Git repository approach. It will create a Git repository directly on your production machine. Then every time you run the <tt>inploy</tt> command it will <tt>git push</tt> your new commits to this repository. Then, there is no step 3! It doesn&#8217;t need to <tt>git pull</tt> because you already pushed to the location where your web server is already pointing at. This is a very simple, Heroku-like, kind of deployment.
  </p>
  
  <p>
    And if you have an empty box, with only SSH enabled, you can still automate the installation of packages and other stuff through a web available script. For example, let&#8217;s say you have a web server that contains recipes (Bash scripts) at <tt>http://myserver.com/myscript</tt>. You can execute it on your empty box like this:
  </p>
  
  <pre>inploy install from=http://myserver.com/myscript</pre>
  
  <p>
    And then you can do <tt>inploy setup</tt> and <tt>inploy</tt> as usual.
  </p>
  
  <p>
    One of most notable omissions from Inploy, compared to Capistrano, is the equivalent to <tt>cap rollback</tt>. The entire directory structure and symlink strategy used by Capistrano is done in such a way to make it easier to rollback to previous versions by creating time stamped folders and symlinks to point to the current version.
  </p>
  
  <p>
    It is a clever strategy, but maybe a bit too much for small/medium projects. If you already have Git and you already tag the versions properly, it is only a matter of <tt>git checkout old_tag</tt> to rollback to a previous version.
  </p>
  
  <p>
    Inploy, by itself, does not implement a <tt>rollback</tt> option because it was never requested so, which means that this is a feature that people rarely use. Most of the time, if you do proper testing and continuous integration, you can safely assume that it wouldn&#8217;t break in production. This is not 100%, of course, but it means that the chance of you needing a rollback feature is drastically diminished.
  </p>
  
  <p>
    As you can see, Inploy is a very pragmatic, thin wrapper around SSH automation, that is very easy to set up and use. Try to study the <a href="http://github.com/dcrec1/inploy">source code</a>, you will be surprised to be able to understand it very easily and quickly customize it for your particular needs.
  </p>
  
  <p>
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
  
  <p>
    <strong><em>Do read</em> these awesome Guest Posts:</strong>
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/07/do-you-know-rubys-chainsaw-method/">Do YOU know Ruby’s ‘Chainsaw’ method?</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/01/an-introduction-to-eventmachine-and-how-to-avoid-callback-spaghetti/">An introduction to eventmachine, and how to avoid callback spaghetti</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/30/the-testing-mindset/">The Testing Mindset</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/29/an-introduction-to-desktop-apps-with-ruby/">An Introduction to Desktop Apps with Ruby</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/28/the-ruby-movement/">The Ruby movement</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/27/almost-everything-is-an-object-and-everything-is-almost-an-object/">Almost everything is an object (and everything is almost an object!)</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/24/so-youre-new-to-ruby/">So… you’re new to Ruby!</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/23/incorporating-web-apis-to-spark-computer-programming-exercises/">Incorporating Web APIs to spark computer programming exercises</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/22/14-ways-to-have-fun-coding-ruby/">14 Ways To Have Fun Coding Ruby</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/21/writing-modular-web-applications-with-rack/">Writing modular web applications with Rack</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/20/how-to-learn-ruby-or-any-programming-language/">How to Learn Ruby (or any programming language)</a>
    </li>
  </ul>
</div>

