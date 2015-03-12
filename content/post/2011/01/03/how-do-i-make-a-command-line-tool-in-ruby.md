---
author: Allen Wei
categories:
- Beginners
- Ruby
- Ruby Masters
date: 2011-01-03
layout: post
permalink: /2011/01/03/how-do-i-make-a-command-line-tool-in-ruby/
tags:
- OptionParser
- programming
- ruby programming
- Thor
thesis_description:
- Allen Wei explains how to make a command-line tool in Ruby.
thesis_keywords:
- OptionParser,Programming,Ruby programming,Thor
title: How do I make a command-line tool in Ruby?
topsy_short_url:
- http://bit.ly/hRvh7b
---

<div>
  <h3>
    How do I make a command-line tool in Ruby?
  </h3>
  
  <p class="update">
    This guest post is by <strong>Allen Wei</strong>, who works as Senior Ruby On Rails Engineer for <a href="http://www.seravia.com/">Seravia</a>, in Beijing. He is very enthusiastic about Ruby. He started using Ruby after several years of using Java, .NET and never came back to them. When he has some spare time, he develops <a href="https://github.com/allenwei">Ruby gems</a>, holds tech sessions, and shares his experience in his <a href="http://www.allenwei.cn/">blog</a>. He is also a fan of BDD and TDD, using them in all his open source projects. He gains a lot from the Ruby community and hopes to give back.
  </p>
  
  <h3>
    Introduction
  </h3>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/allen_125x125.jpg" alt="Allen Wei" /> <span class="drop_cap">R</span>uby, as a dynamic language, is always used for quick processing command-line tool for its simplicity and productivity.
  </p>
  
  <p>
    This article talks about three ways to write a command-line tool.
  </p>
  
  <p>
    Before we start, there are a few things you need to know:
  </p>
  
  <ol>
    <li>
      Put line <code>#!/usr/bin/env ruby</code> into the first line of your command-line file which will tell the shell to execute your file using Ruby (<code>#!/usr/bin/env ruby</code> is similar to simply calling <code>ruby</code> from the command line, so the same rules apply. Basically, the individual entries in the <code>$PATH</code> environment variable are checked in order, and the <code>ruby</code> that is found first is used.).
    </li>
    <li>
      Make sure your file is executable, run <code>chmod u+x FILE_PATH</code>.
    </li>
    <li>
      Print help text and return right exit code (0 means success, other number means fail) if the user uses it in the wrong way.
    </li>
  </ol>
  
  <p>
    Note that other people will not be sure how to execute your command-line tool.
  </p>
  
  <h3>
    Conventions
  </h3>
  
  <p>
    I’ll use three definitions:
  </p>
  
  <ol>
    <li>
      Command-line file name
    </li>
    <li>
      Command
    </li>
    <li>
      Option
    </li>
  </ol>
  
  <p>
    For example there is a command: &#8216;server start -e development&#8217;
  </p>
  
  <ol>
    <li>
      Command-line file name is &#8216;server&#8217;
    </li>
    <li>
      Command is the first argument &#8216;start&#8217;
    </li>
    <li>
      Option is the reset of argument pair &#8216;-e development&#8217;
    </li>
  </ol>
  
  <h3>
    Let’s go
  </h3>
  
  <p>
    We shall start from a simple example: write a command-line tool to start, stop and restart the server.
  </p>
  
  <h4>
    Without any lib
  </h4>
  
  <pre># server.rb
case ARGV[0]
when "start"
  STDOUT.puts "called start"
when "stop"
  STDOUT.puts "called stop"
when "restart"
  STDOUT.puts "called restart"
else
  STDOUT.puts &lt;&lt;-EOF
Please provide command name

Usage:
  server start
  server stop
  server restart
EOF
end
</pre>
  
  <p>
    <span class="caps">ARGV, </span>all arguments will be stored as an array in this variable.
  </p>
  
  <p>
    What if you need to pass some options?
  </p>
  
  <pre># server.rb
def parse_options
  options = {}
  case ARGV[1]
  when "-e"
    options[:e] = ARGV[2]
  when "-d"
    options[:d] = ARGV[2]
  end
  options
end

case ARGV[0]
when "start"
  STDOUT.puts "start on #{parse_options.inspect}"
when "stop"
  STDOUT.puts "stop on #{parse_options.inspect}"
when "restart"
  STDOUT.puts "restart on #{parse_options.inspect}"
else
  STDOUT.puts &lt;&lt;-EOF
Please provide command name

Usage:
  server start
  server stop
  server restart

  options:
    -e ENVIRONMENT. Default: development
    -d DEAMON, true or false. Default: true
EOF
end
</pre>
  
  <p>
    This code is simple but it has some disadvantages:
  </p>
  
  <ul>
    <li>
      Writing option parser and help text in different places will bring you troubles when they are not matched.
    </li>
    <li>
      Using array index to get options from <span class="caps">ARGV</span>. These magic numbers will create a maintenance problem.
    </li>
  </ul>
  
  <h4>
    Using OptionParser
  </h4>
  
  <p>
    <a href="http://ruby-doc.org/stdlib/libdoc/optparse/rdoc/classes/OptionParser.html">OptionParser</a> is a built-in Ruby lib to help you parse arguments.
  </p>
  
  <p>
    We can refactor our code like this:
  </p>
  
  <pre>require 'optparse'

options = {}

opt_parser = OptionParser.new do |opt|
  opt.banner = "Usage: opt_parser COMMAND [OPTIONS]"
  opt.separator  ""
  opt.separator  "Commands"
  opt.separator  "     start: start server"
  opt.separator  "     stop: stop server"
  opt.separator  "     restart: restart server"
  opt.separator  ""
  opt.separator  "Options"

  opt.on("-e","--environment ENVIRONMENT","which environment you want server run") do |environment|
    options[:environment] = environment
  end

  opt.on("-d","--daemon","runing on daemon mode?") do
    options[:daemon] = true
  end

  opt.on("-h","--help","help") do
    puts opt_parser
  end
end

opt_parser.parse!

case ARGV[0]
when "start"
  puts "call start on options #{options.inspect}"
when "stop"
  puts "call stop on options #{options.inspect}"
when "restart"
  puts "call restart on options #{options.inspect}"
else
  puts opt_parser
end
</pre>
  
  <p>
    Try to execute this file without arguments; you&#8217;ll find it prints a very nice help text.
  </p>
  
  <p>
    <code>opt_parser.parse!</code> is the method extract options from <span class="caps">ARGV, </span>extracted value will be deleted from <span class="caps">ARGV.</span>
  </p>
  
  <p>
    <code>OptionParser</code> is better than that.
  </p>
  
  <p>
    You can define options value type, then <code>OptionParser</code> will convert value to the type you defined, like this:
  </p>
  
  <pre>opt.on("-e","--environment ENVIRONMENT",Numeric,
       "which environment you want server run") do |environment|
  options[:environment] = environment
       end
opt.on("--delay N", Float, "Delay N seconds before executing") do |n|
  options[:delay] = n
end
opt.on("-j x,y,z","--jurisdictions x,y,z", Array,
       "which jurisdiction will start") do |jurisdictions|
  options[:jurisdictions] = jurisdictions
       end
server_list = %w[a b c]
opt.on("-s SERVERS","--servers SERVERS", server_list,
       "which server will start between #{server_list.join(',')}") do |servers|
  options[:servers] = servers
       end
</pre>
  
  <p>
    You can mark whether the value of the option is mandatory.
  </p>
  
  <pre># Mandatory argument.
opts.on("-r", "--require LIBRARY",
        "Require the LIBRARY before executing your script") do |lib|
  options.library &lt;&lt; lib
        end

# Optional argument; multi-line description.
opts.on("-i", "--inplace [EXTENSION]",
        "Edit ARGV files in place",
        "  (make backup if EXTENSION supplied)") do |ext|
  options.inplace = true
  options.extension = ext || ''
  options.extension.sub!(/A.?(?=.)/, ".")  # Ensure extension begins with dot.
        end
</pre>
  
  <p>
    For more details your can see <a href="http://ruby.about.com/od/advancedruby/a/optionparser.htm">this article</a> and refer the <a href="http://ruby-doc.org/stdlib/libdoc/optparse/rdoc/classes/OptionParser.html">Ruby rdoc</a>.
  </p>
  
  <p>
    Benefit of <code>OptionParser</code> is: we don’t need to use array index to retrieve options and we can write help text along with option definition.
  </p>
  
  <p>
    Disadvantage of <code>OptionParser</code> is: since different commands need using the same option parser, you cannot define different option parsers for different commands. To solve this problem, you can resort to <code>Thor</code>.
  </p>
  
  <h4>
    Using Thor
  </h4>
  
  <p>
    As you know <a href="https://www.github.com/wycats/thor">Thor</a> is a replacement of Rake. Let’s see how we use <code>Thor</code> to refactor our command-line tool.
  </p>
  
  <pre>require 'rubygems'
require 'thor'

class ThorExample &lt; Thor
  desc "start", "start server"
  method_option :environment,:default =&gt; "development", :aliases =&gt; "-e",
:desc =&gt; "which environment you want server run."
  method_option :daemon, :type =&gt; :boolean, :default =&gt; false, :aliases =&gt; "-d",
:desc =&gt; "running on daemon mode?"
  def start
    puts "start #{options.inspect}"
  end

  desc "stop" ,"stop server"
  method_option :delay,  :default =&gt; 0, :aliases =&gt; "-w",
:desc =&gt; "wait server finish it's job"
  def stop
    puts "stop"
  end
end

ThorExample.start
</pre>
  
  <ul>
    <li>
      <code>desc</code> defines command name and long description.
    </li>
    <li>
      <code>method_option</code> defines option parser for this command.
    </li>
    <li>
      <code>ThorExample.start</code> is a method to start parse argument.
    </li>
  </ul>
  
  <p>
    Execute it without argument, the output is:
  </p>
  
  <pre>Tasks:
  thor_example help [TASK]  # Describe available tasks or one specific task
  thor_example start        # start server
  thor_example stop         # stop server
</pre>
  
  <p>
    Execute it with argument <code>help start</code>, you’ll get help text for command start:
  </p>
  
  <pre>Usage:
  thor_example start

Options:
  -e, [--environment=ENVIRONMENT]  # which environment you want server run.
                                   # Default: development
  -d, [--daemon]                   # running on daemon mode?

start server
</pre>
  
  <p>
    As you can see, it’s very clean and easy to write.
  </p>
  
  <p>
    For a more detailed usage, you can visit Thor <a href="https://github.com/wycats/thor">github page</a> and its <a href="http://rdoc.info/github/wycats/thor">rdoc</a>.
  </p>
  
  <h3>
    Summary
  </h3>
  
  <p>
    Of course there are more ways to write a command-line tool. Choose what best fits your need and not the most powerful or latest one.
  </p>
  
  <p>
    All the sample code is on github <a href="https://github.com/allenwei/ruby_command_line_sample">https://github.com/allenwei/ruby_command_line_sample</a>.
  </p>
  
  <p>
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
  
  <p>
    <strong><em>Do also read</em> this awesome Guest Post:</strong>
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/blog/2010/12/21/being-awesome-with-the-mongodb-ruby-driver/">Being Awesome with the MongoDB Ruby Driver</a>
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/OptionParser" rel="tag">OptionParser</a>, <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>, <a href="http://technorati.com/tag/Thor" rel="tag">Thor</a>
