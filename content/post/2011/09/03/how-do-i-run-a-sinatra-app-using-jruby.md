---
title: How do I run a Sinatra app using JRuby?
author: Satish Talim
date: 2011-09-03
layout: post
permalink: /2011/09/03/how-do-i-run-a-sinatra-app-using-jruby/
thesis_description:
  - A blog post that explains how to run a Sinatra app using JRuby.
thesis_keywords:
  - JRuby, Ruby, Programming, Ruby programming, Sinatra
topsy_short_url:
  - http://bit.ly/ohxMwq
categories:
  - JRuby
  - Ruby
  - Sinatra
tags:
  - JRuby
  - programming
  - Ruby
  - ruby programming
  - Sinatra
---
<div>
  <h2>
    How do I run a Sinatra app using JRuby?
  </h2>
  
  <p class="alert">
    RubyLearning is conducting a <a href="http://goo.gl/WZDl8">free, online JRuby 101 course</a> &#8211; the first of its kind, on Google+ Some participants wanted an answer to their question &#8220;<strong>How do I run a Sinatra app using JRuby?</strong>&#8221; This blog post explains the same. Read on.
  </p>
  
  <h3>
    Pre-requisite
  </h3>
  
  <p>
    I have a Windows XP box but the following should work on Mac and Linux-based computers too.
  </p>
  
  <p>
    Ensure that you have already installed JDK 6, JRuby and set the relevant system environment variables <b>path</b>, <b>classpath</b>, <b>JAVA_HOME</b> and <b>JRUBY_HOME</b>.
  </p>
  
  <h3>
    Install Bundler
  </h3>
  
  <p>
    <strong><a href="http://gembundler.com/">Bundler</a></strong> helps prevent conflicting or missing gems and shines when it&#8217;s time to configure those dependencies at install time and runtime.
  </p>
  
  <p>
    JRuby comes with a fairly loaded standard library from scratch but that does not mean there aren&#8217;t other things you&#8217;ll need. Almost all of them are installable as Gems. RubyGems is the premier package management tool for Ruby. It works fine with JRuby and JRuby ships with it. You use it through the gem command. We will need to run the JRuby version of the gem command and to ensure that, we use the <code>-S</code> flag to the interpreter.
  </p>
  
  <p>
    Create a project folder (say c:\jrubysinatra) on your hard-disk. Ensure that your internet connection is active. Now, open a command window in this project folder and type:
  </p>
  
  <pre>jruby -S gem install bundler
</pre>
  
  <p>
    <b>Note</b>: This approach (<code>jruby -S</code>) works for any Ruby command-line tool, including gem, rake, spec, and others.
  </p>
  
  <h3>
    Create a Gemfile
  </h3>
  
  <p>
    Next, in your project folder, create a <b>Gemfile</b>. It looks something like this:
  </p>
  
  <pre>source "http://rubygems.org"
gem 'sinatra'
</pre>
  
  <p>
    This Gemfile says a few things. First, it says that bundler should look for gems declared in the Gemfile at <a href="http://rubygems.org/">http://rubygems.org</a>. You can declare multiple Rubygems sources, and bundler will look for gems in the order you declared the sources. Next, you will have to list all your applications dependencies in there. Sinatra&#8217;s direct dependencies (Rack and Tilt) will, however, be automatically fetched and added by Bundler.
  </p>
  
  <p>
    To make bundler install the dependencies, in the already open command window, type:
  </p>
  
  <pre>jruby -S bundle install
</pre>
  
  <p>
    Because all the gems in your Gemfile have dependencies of their own (and some of those have their own dependencies), running <code>jruby -S bundle install</code> on the Gemfile above, will install quite a few gems. If any of the needed gems are already installed, Bundler will use them. After installing any needed gems to your system, bundler writes a snapshot of all the gems and versions that it installed to <b>Gemfile.lock</b>.
  </p>
  
  <h3>
    Write your Sinatra app
  </h3>
  
  <p>
    Create the file <b><a href="https://gist.github.com/1190382">hellojruby.rb</a></b> in the folder c:\jrubysinatra.
  </p>
  
  <pre>require "rubygems"
require "bundler/setup"

require "sinatra"

get '/hi' do
    "Hello JRuby World!"
end
</pre>
  
  <h3>
    Set up your Sinatra application to use Bundler
  </h3>
  
  <p>
    For your Sinatra application, you will need to set up bundler before trying to require any gems. At the top of the first file that your application loads (for Sinatra, the file that calls <code>require "sinatra"</code>), put the following code:
  </p>
  
  <pre>require "rubygems"
require "bundler/setup"
</pre>
  
  <p>
    This will automatically discover your Gemfile, and make all the gems in your Gemfile available to Ruby (in technical terms, it puts the gems &#8220;on the load path&#8221;). You can think of it as an adding some extra powers to require &#8220;rubygems&#8221;.
  </p>
  
  <p>
    Now that your code is available to Ruby, you can require the gems that you need. For instance, you can <code>require "sinatra"</code>.
  </p>
  
  <h3>
    Run your Sinatra application
  </h3>
  
  <p>
    In the already open command window, type:
  </p>
  
  <pre>jruby -S bundle exec jruby hellojruby.rb
</pre>
  
  <p>
    In the command window, you will see:
  </p>
  
  <pre>== Sinatra/1.2.6 has taken the stage on 4567 for development with backup from WEBrick
[2011-09-03 07:21:17] INFO  WEBrick 1.3.1
[2011-09-03 07:21:17] INFO  ruby 1.8.7 (2011-08-23) [java]
[2011-09-03 07:21:17] INFO  WEBrick::HTTPServer#start: pid=5128 port=4567
</pre>
  
  <h3>
    Access the Sinatra application
  </h3>
  
  <p>
    In your browser, visit the URL: <a href="http://localhost:4567/hi">http://localhost:4567/hi</a> &#8211; the browser shall display &#8220;<b>Hello JRuby World!</b>&#8220;
  </p>
  
  <p>
    That&#8217;s it for now.
  </p>
  
  <p class="alert">
    <em>Feel free to ask questions and give feedback in the comments section of this post.</em> Fellow Rubyists, if you would like to write a guest blog post for RubyLearning email me at <b>satish [at] rubylearning.org</b>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/JRuby" rel="tag">JRuby</a>, <a href="http://technorati.com/tag/Ruby" rel="tag"> Ruby</a>, <a href="http://technorati.com/tag/Programming" rel="tag"> Programming</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag"> Ruby programming</a>, <a href="http://technorati.com/tag/Sinatra" rel="tag"> Sinatra</a>
