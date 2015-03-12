---
author: Steve Klabnik
categories:
- Beginners
- Popular
- Ruby
- Ruby Masters
date: 2010-12-20
layout: post
permalink: /2010/12/20/how-do-i-keep-multiple-ruby-projects-separate/
tags:
- Bundler
- programming
- ruby programming
- rvm
thesis_description:
- If you have multiple projects in Ruby, it's a good idea to separate their dependencies.
  Steve shows you how to isolate your Ruby projects from one another, and easily and
  efficiently switch between them.
thesis_keywords:
- Bundler,rvm, Programming,Ruby programming
title: How do I keep multiple Ruby projects separate?
topsy_short_url:
- http://bit.ly/eU1Mf1
---

<div>
  <h3>
    How do I keep multiple Ruby projects separate?
  </h3>
  
  <p class="update">
    This guest post is by <strong><a href="https://github.com/steveklabnik">Steve Klabnik</a></strong>, who is a software craftsman, writer, and former startup CTO. Steve tries to keep his Ruby consulting hours down so that he can focus on maintaining <a href="http://hackety-hack.com/">Hackety Hack</a> and being a core member of Team Shoes, as well as writing regularly for multiple blogs.
  </p>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/steve_cropped.jpg" alt="Steve Klabnik" /> <span class="drop_cap">I</span>f you&#8217;re anything like me, you&#8217;re already starting a new project immediately after wrapping up the last one. There just aren&#8217;t enough hours in the day to code up all the crazy ideas I have floating around in my head. Often, these ideas are the result of checking out some fun new gem, GitHub project, or even a different Ruby. Real quickly, a problem develops: what happens when these projects interfere with one another? What if I want to use Ruby 1.8.7 for an older project, Ruby 1.8.5 for a legacy application, Ruby 1.9.2 for the latest and greatest, and JRuby to use an interesting Ruby library? Luckily, there are a few things that you can do to isolate your different projects from one another, and some settings for that will make them quite painless to use. There are three main things that can go wrong when you try to use different sets of tools on a per-project basis: conflicts between Ruby versions, conflicts between gems, and forgetting which tools you use on which project.
  </p>
  
  <h3>
    Ruby Version Conflicts
  </h3>
  
  <p>
    This is the biggest and most painful kind of problem. If you want to use Ruby 1.8 for one project and Ruby 1.9 for another, you have a problem. If you&#8217;re using Linux, for example, your package manager may see that both ruby18 and ruby19 fulfill a &#8216;ruby&#8217; dependency, and so it won&#8217;t let you have them both installed side by side. The solution isn&#8217;t pretty: install different Rubies from source. This gets ugly really quickly, because it&#8217;s easy to forget where you&#8217;ve compiled different Rubies, and having software outside of your package manager isn&#8217;t a great answer. If you&#8217;re on OS X or Windows, you skip right past the package manager problem and straight to the source &#8216;solution.&#8217; This is no good!
  </p>
  
  <p>
    Luckily, there&#8217;s an awesome project by Wayne E. Seguin named <a href="http://rvm.beginrescueend.com/">rvm</a>. rvm is sort of like a package manager for Ruby. If you&#8217;d like to install both Ruby 1.8.7 and 1.9.2, just type this in:
  </p>
  
  <pre>$ rvm install 1.8.7
$ rvm install 1.9.2</pre>
  
  <p>
    It&#8217;ll go fetch the Ruby source code, compile it, and get you all set up. To use a specific Ruby, you can type &#8216;use':
  </p>
  
  <pre>$ rvm use 1.8.7
$ ruby -v
ruby 1.8.7 (2010-08-16 patchlevel 302) [i686-darwin10.4.0]
$ rvm use 1.9.2
$ ruby -v
ruby 1.9.2p0 (2010-08-18 revision 29036) [x86_64-darwin10.4.0]</pre>
  
  <p>
    Neat! You can even get other Ruby versions:
  </p>
  
  <pre>$ rvm install jruby
$ rvm install rbx
$ rvm install macruby</pre>
  
  <p>
    You can see a full list of these with &#8216;rvm list known&#8217;. For a full list of everything that rvm can do, as well as installation instructions, visit <a href="http://rvm.beginrescueend.com/">the rvm website.</a>
  </p>
  
  <h3>
    Gem Conflicts
  </h3>
  
  <p>
    Once you&#8217;ve gotten your Rubies straight, you can still have conflicts between different gems that your project needs. One project uses Rails 2.3.8, another uses Rails 3&#8230; It gets worse when you have certain gems installed only as a dependency, and you don&#8217;t know exactly which one is correct:
  </p>
  
  <pre>$ gem list | grep net-ssh
net-ssh (2.0.23, 2.0.4, 1.1.4)</pre>
  
  <p>
    rvm has a neat feature called &#8216;gemsets.&#8217; They let you create separate sets of gems per Ruby you have installed. This allows you to isolate each application, giving it its own set of gems. Check it out:
  </p>
  
  <pre>$ gem list

*** LOCAL GEMS ***

aasm (2.1.5)
abstract (1.0.0)
acl9 (0.12.0)
*snip*

$ rvm gemset create new-gemset
$ rvm use 1.9.2@new-gemset
$ gem list

*** LOCAL GEMS ***

$</pre>
  
  <p>
    Cool stuff! As you can see, use an &#8216;@&#8217; symbol to tell rvm which gemset you&#8217;d like to use. Now we&#8217;ve isolated each project&#8217;s gems from each other. There is, however, a much more complicated kind of conflicts that can occur between gems. This happens when two gems have interlocking dependencies.
  </p>
  
  <p>
    Here&#8217;s an example of this from the past: ActionPack 2.3.5 requires Rack =1.0.0, which is the newest version. Unicorn requires Rack >1.0.0. Rack releases a new version, 1.1.0. Now, when starting up a Rails application, the unicorn gem is loaded first, so it loads the newest version of the gem that works, which is rack-1.1.0. Then rails loads, and it loads actionpack, which tries to load rack. It needs =1.0.1, but sees that 1.1.0 has already been loaded, and throws this ugly, ugly error:
  </p>
  
  <pre>Gem::LoadError: can't activate rack (~&gt; 1.0.0, runtime)
for ["actionpack-2.3.5"], already activated rack-1.1.0
for ["unicorn"]</pre>
  
  <p>
    There&#8217;s a set of versions here that works, but the way that the gems are loaded means that it doesn&#8217;t. The problem is that at the time that unicorn loads, it can&#8217;t possibly know that you&#8217;re planning on loading a different version of rack somewhere down the line. What we really need is a tool that knows about all of our dependencies, and can calculate the graph of all of our requirements, and figure out which versions of everything we need, and then only place those versions on the $LOAD_PATH. Luckily, such a project exists: <a href="http://gembundler.com/">bundler</a>.
  </p>
  
  <p>
    To use bundler, you first need to make a file named &#8216;Gemfile&#8217; in the root of your project directory. This file looks something like this:
  </p>
  
  <pre>source "http://rubygems.org"

gem "rails", "~&gt;3.0.0"

group :development do
  gem 'sqlite3-ruby', :require =&gt; 'sqlite3'
end

group :production do
  gem "pg"
end</pre>
  
  <p>
    The first line tells Bundler where to look for gems. The second line says that we want to use the &#8216;rails&#8217; gem, and we want any version that&#8217;s at least 3.0.0 but less than 3.1.0. Finally, the other lines show &#8216;groups&#8217; of gems: in development, we want to use sqlite3-ruby, and we need to require it via the name &#8216;sqlite3&#8242;, but we want to use Postgres in production. To install these gems, just:
  </p>
  
  <pre>$ bundle install</pre>
  
  <p>
    Bundler gets all the information that it needs on all the gems, figures out what versions of everything work together, and then installs the right versions. It then creates a Gemfile.lock file that holds all of this information. It&#8217;s just a simple YAML file, you can open it up and see the specifics. You&#8217;ll want to add the Gemfile and Gemfile.lock into your version control, so that anyone else that&#8217;s developing with you can also get the same gem versions.
  </p>
  
  <p>
    To use the gems in your bundle, just use these two lines:
  </p>
  
  <pre>require "rubygems"
require "bundler/setup"</pre>
  
  <p>
    From there, whenever you require a gem, it&#8217;ll be the version from the bundle. If you want Bundler to automatically require all of your gems for you, just &#8216;<code>Bundler.require</code>&#8216; and it&#8217;ll require the default group of gems.
  </p>
  
  <p>
    Rails 3 automatically comes with a Gemfile and bundler support right out of the box. If you want to use Bundler with Rails 2.3, check out <a href="http://gembundler.com/rails23.html">the Bundler site</a> for setup instructions.
  </p>
  
  <p>
    The combination of gemsets and Bundler will make sure that you don&#8217;t have any nasty gem conflicts. Gemsets keep your projects isolated from each other, and Bundler keeps your gems&#8217; versions from interfering with each other. The two work really well together.
  </p>
  
  <h3>
    I can&#8217;t remember which tool I used!
  </h3>
  
  <p>
    All of these rubies and gemsets can get confusing. Luckily, rvm has an awesome feature to take care of this, too: .rvmrc files. If you put a file named &#8216;.rvmrc&#8217; in your project&#8217;s root directory, when you enter the project, it&#8217;ll switch your Ruby version (and gemset) automatically. It&#8217;s really easy to use, too. Just put the command you&#8217;d use to switch in the file. For example, in the Hackety Hack website project, I have the following <a href="https://github.com/hacketyhack/hackety-hack.com/blob/master/.rvmrc">.rvmrc</a>:
  </p>
  
  <pre>rvm 1.8.7@hackety-hack.com</pre>
  
  <p>
    Astute readers will notice that I left off the &#8216;use,&#8217; rvm defaults to &#8216;use&#8217; if you don&#8217;t give it a different command. Check it out:
  </p>
  
  <pre>$ ruby -v
ruby 1.9.2p0 (2010-08-18 revision 29036) [x86_64-darwin10.4.0]
$ cd hackety-hack.com
$ ruby -v
ruby 1.8.7 (2010-08-16 patchlevel 302) [i686-darwin10.4.0]</pre>
  
  <p>
    Super cool. Now you&#8217;ll never forget which Ruby you were using, and you don&#8217;t even need to switch manually. This is one of the first things that I do when I start a new project in Ruby: Pick a Ruby version, make a gemset with the same name as the project, and set up an .rvmrc. It&#8217;s saved me hours of time and headaches.
  </p>
  
  <h3>
    Multiple projects: super simple
  </h3>
  
  <p>
    rvm is a fantastic tool to help solve your multiple-ruby woes. It really does make using multiple kinds of Ruby really, really easy. And Bundler makes sure that your gems play nice togther. It&#8217;s a great time to be a Rubyist.
  </p>
  
  <p>
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Bundler" rel="tag">Bundler</a>, <a href="http://technorati.com/tag/rvm" rel="tag">rvm</a>, <a href="http://technorati.com/tag/Programming" rel="tag"> Programming</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>
