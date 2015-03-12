---
author: Nick Quaranto
categories:
- Beginners
- Ruby
- Ruby Masters
date: 2010-10-06
layout: post
permalink: /2010/10/06/gem-sawyer-modern-day-ruby-warrior/
tags:
- Gem Sawyer Modern Day Ruby Warrior
- Nick Quaranto
- programming
- Ruby
- Ruby Beginners
- Ruby for Noobs
thesis_description:
- If you're fresh to Ruby and haven't really learned what RubyGems can do for you
  yet, you're about to find out! Nick Quaranto's guest blog post on RubyLearning.
thesis_keywords:
- Ruby, Programming, Nick Quaranto, Ruby for Noobs, Ruby beginners, Gem Sawyer Modern
  Day Ruby Warrior
title: Gem Sawyer, Modern Day Ruby Warrior
topsy_short_url:
- http://bit.ly/ch5ZoF
---

<div>
  <h3>
    Gem Sawyer, Modern Day Ruby Warrior
  </h3>
  
  <p class="update">
    This guest post is contributed by <strong><a href="http://twitter.com/qrush">Nick Quaranto</a></strong>, a web developer at <a href="http://thoughtbot.com/">Thoughtbot</a> in Boston, MA. Nick maintains <a href="http://rubygems.org/">RubyGems.org</a> and he&#8217;s a proud to be a part of the Ruby community. He cut his teeth on classic ASP and ASP.NET at first, but discovered Ruby on Rails through his university and dove in head first. Nick pretends he&#8217;s a bassist with famous prog rock bands when not coding.
  </p>
  
  <p class="block">
    <img class="alignright" src="http://en.gravatar.com/userimage/938917/6d1a54abf9a4ee9d6fd682c193ec2edc.png?size=125" alt="Nick Quaranto" width="125" height="125" /> <span class="drop_cap">Y</span>ou&#8217;re using <a href="http://rubygems.org/">RubyGems</a> on a daily basis when programming with Ruby, but how do they work? Gems are now a ubiquitous part of the Ruby developer&#8217;s toolkit. If you&#8217;re fresh to Ruby and haven&#8217;t really learned what RubyGems can do for you yet, you&#8217;re about to find out!
  </p>
  
  <h3>
    What&#8217;s in a gem?
  </h3>
  
  <p>
    Ruby! Lots of it. Gems are just a simple format for publishing and sharing Ruby code. Let&#8217;s explore a simple one, and one of my favorites, <a href="http://rubygems.org/gems/jekyll">jekyll</a>. First, let&#8217;s see if the gem exists. We could go to RubyGems.org to do this, but the <code>gem</code> command has a lot of built-in searching commands.
  </p>
  
  <pre>% gem list jekyll -r

*** REMOTE GEMS ***

jekyll (0.7.0)
jekyll-epub (0.0.3)
jekyll-localization (0.0.6)
....</pre>
  
  <p>
    This command will ask the remote source (the <code>-r</code> flag specifies this) if there&#8217;s any gems available under that name. By default this looks at RubyGems.org, but it could be any URL. Next, let&#8217;s get the gem on our system:
  </p>
  
  <pre>% gem install jekyll
Successfully installed jekyll-0.7.0
1 gem installed

% gem unpack jekyll
Unpacked gem: '/private/tmp/jekyll-0.7.0'</pre>
  
  <p>
    These two commands downloaded the gem and unzipped it from a compressed state in a new folder from my current directory. The directory structure here is common to all gems. I&#8217;ve ignored a lot of the files here, but here&#8217;s the basics of the internals.
  </p>
  
  <pre>jekyll-0.7.0 % tree -L 2
.
+-- History.txt
+-- LICENSE
+-- README.textile
+-- Rakefile
+-- bin
¦   +-- jekyll
+-- features
+-- jekyll.gemspec
+-- lib
¦   +-- jekyll
¦   +-- jekyll.rb
+-- test</pre>
  
  <p>
    There&#8217;s a few administrative files here, such as the <code>README</code> and code license. Hopefully you&#8217;ll see those in every gem, along with a decent changelog or history. Most gems have a <code>Rakefile</code> which can run tests and perform other automation tasks as well. This gem is pretty well tested, so the test files are included in both the <code>test</code> directory for <a href="http://github.com/thoughtbot/shoulda">shoulda</a> and a <code>features</code> directory for <a href="http://cukes.info/">cucumber</a> tests.
  </p>
  
  <p>
    The meat of a gem really begins with <code>lib</code> directory. RubyGems really just manages your Ruby load path, or how your ruby code is found by the <code>require</code> statement. When you <code>require</code> a gem, really you&#8217;re just placing that gem&#8217;s <code>lib</code> directory onto your <code>$LOAD_PATH</code>. Let&#8217;s try this out in IRB and get some help from the pretty_print library included with Ruby. Passing <code>-r</code> to <code>irb</code> will automatically <code>require</code> a library when loaded.
  </p>
  
  <pre>% irb -rpp
&gt;&gt; pp $LOAD_PATH
["/Users/qrush/.rvm/rubies/ree-1.8.7-2010.02/lib/ruby/site_ruby/1.8",
 "/Users/qrush/.rvm/rubies/ree-1.8.7-2010.02/lib/ruby/site_ruby/1.8/i686-darwin10.3.1",
 "/Users/qrush/.rvm/rubies/ree-1.8.7-2010.02/lib/ruby/site_ruby",
 "/Users/qrush/.rvm/rubies/ree-1.8.7-2010.02/lib/ruby/vendor_ruby/1.8",
 "/Users/qrush/.rvm/rubies/ree-1.8.7-2010.02/lib/ruby/vendor_ruby/1.8/i686-darwin10.3.1",
 "/Users/qrush/.rvm/rubies/ree-1.8.7-2010.02/lib/ruby/vendor_ruby",
 "/Users/qrush/.rvm/rubies/ree-1.8.7-2010.02/lib/ruby/1.8",
 "/Users/qrush/.rvm/rubies/ree-1.8.7-2010.02/lib/ruby/1.8/i686-darwin10.3.1",
 "."]</pre>
  
  <p>
    By default we have just a few system directories on our load path and the Ruby standard libraries. If we were to run <code>require 'rake'</code> right now, it would fail, because RubyGems isn&#8217;t loaded yet.
  </p>
  
  <pre>% irb -rpp
&gt;&gt; require 'rake'
LoadError: no such file to load -- rake
        from (irb):2:in `require'
        from (irb):2
&gt;&gt; require 'rubygems'
=&gt; true
&gt;&gt; require 'rake'
=&gt; true
&gt;&gt; pp $LOAD_PATH[0..1]
["/Users/qrush/.rvm/gems/ree-1.8.7-2010.02/gems/rake-0.8.7/bin",
 "/Users/qrush/.rvm/gems/ree-1.8.7-2010.02/gems/rake-0.8.7/lib"]</pre>
  
  <p>
    Once we&#8217;ve required rake, then RubyGems automatically drops the bin and lib directories onto the <code>$LOAD_PATH</code>. Boom! The <code>bin</code> directory is used for creating executables that use your gem&#8217;s code, such as <code>rake</code>. These are completely optional and you could have multiple per gem if you wanted.
  </p>
  
  <p>
    That&#8217;s basically it for what&#8217;s in a gem. Drop Ruby code into <code>lib</code>, name a Ruby file the same as your gem (so for jekyll, <code>jekyll.rb</code>) and it&#8217;s loaded by RubyGems.
  </p>
  
  <p>
    The <code>lib</code> directory normally contains only one <code>.rb</code> file on the top directory, and then another folder with the same name as the gem with more code in it. Jekyll has plenty, and Rake does too. Before you go any further with this article, download your favorite gem, <code>gem unpack</code> it, and take a peek around.
  </p>
  
  <h3>
    How do I make a gem?
  </h3>
  
  <p>
    Creating and publishing your own gem is simple thanks to the tools baked right into RubyGems. Let&#8217;s make a simple &#8220;hello world&#8221; gem, and feel free to play along at home! This is really as simple as it gets.
  </p>
  
  <p>
    I started with just one Ruby file for my &#8220;hola&#8221; gem, and the gemspec.
  </p>
  
  <pre>% tree
.
+-- hola.gemspec
+-- lib
    +-- hola.rb</pre>
  
  <p>
    The code inside of <code>lib/hola.rb</code> is pretty bare bones, we just want to see some output.
  </p>
  
  <pre>% cat lib/hola.rb
class Hola
  def self.hi
    puts "Hello world!"
  end
end</pre>
  
  <p>
    The gemspec defines what&#8217;s in the gem, who made it, and the version of the gem. It&#8217;s also your interface to RubyGems.org, all of the information you see on a gem page (like <a href="http://rubygems.org/gems/jekyll">jekyll&#8217;s</a>) comes from the gemspec.
  </p>
  
  <pre>% cat hola.gemspec
Gem::Specification.new do |s|
  s.name        = 'hola'
  s.version     = '0.0.0'
  s.date        = '2010-10-03'
  s.summary     = "Hola!"
  s.description = "A simple hello world gem"
  s.authors     = ["Nick Quaranto"]
  s.email       = 'nick@quaran.to'
  s.homepage    = 'http://rubygems.org/gems/hola'
  s.files       = ["lib/hola.rb"]
end</pre>
  
  <p>
    Look familiar? The gemspec is also Ruby, so you could wrap scripts to generate the file names and bump the version number. Once we have our gemspec, we have to build a gem from it. We can then install it locally to test it out.
  </p>
  
  <pre>% gem build hola.gemspec
  Successfully built RubyGem
  Name: hola
  Version: 0.0.0
  File: hola-0.0.0.gem

% gem install ./hola-0.0.0.gem
Successfully installed hola-0.0.0
1 gem installed</pre>
  
  <p>
    Of course, our smoke test isn&#8217;t over yet: Let&#8217;s require our gem and use it!
  </p>
  
  <pre>% irb -rubygems
&gt;&gt; require 'hola'
=&gt; true
&gt;&gt; Hola.hi
Hello world!</pre>
  
  <p>
    Hola now needs to be shared with the rest of the Ruby community. Publishing your gem out to RubyGems.org only takes one command, granted you have an account on the site. Once you&#8217;re signed up, then you can push out a gem.
  </p>
  
  <pre>% gem push hola-0.0.0.gem
Enter your RubyGems.org credentials.
Don't have an account yet? Create one at http://rubygems.org/sign_up
   Email:   nick@quaran.to
   Password:
Signed in.
Pushing gem to RubyGems.org...
Successfully registered gem: hola (0.0.0)</pre>
  
  <p>
    In just a few moments (usually a minute), your gem will be available for installation by anyone.
  </p>
  
  <pre>% gem list -r hola

*** REMOTE GEMS ***

hola (0.0.0)

% gem install hola
Successfully installed hola-0.0.0
1 gem installed</pre>
  
  <p>
    It&#8217;s really that easy to share code with Ruby and RubyGems.
  </p>
  
  <h3>
    Exit the warrior, today&#8217;s Gem Sawyer
  </h3>
  
  <p>
    With this basic understanding of the RubyGems ecosystem on your system, I hope you&#8217;ll be the next developer to share your creations with others on RubyGems.org. For a more detailed explanation of how to build and deploy a gem, check out <a href="http://railscasts.com/episodes/183-gemcutter-jeweler">this railscast</a>.
  </p>
  
  <p class="alert">
    <em>Have <b>you</b> written any Ruby gems? Why don&#8217;t you share them with us? Let us know in the comments section of this post. Thanks!</em>
  </p>
  
  <p>
    <b><em>Do read</em> these awesome Guest Posts:</b>
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/05/outside-in-development/">An Introduction to Outside-in Development</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/04/ruby-forensics/">Ruby Forensics</a>
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

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Programming" rel="tag"> Programming</a>, <a href="http://technorati.com/tag/Nick+Quaranto" rel="tag"> Nick Quaranto</a>, <a href="http://technorati.com/tag/Ruby+for+Noobs" rel="tag"> Ruby for Noobs</a>, <a href="http://technorati.com/tag/Ruby+beginners" rel="tag"> Ruby beginners</a>, <a href="http://technorati.com/tag/Gem+Sawyer+Modern+Day+Ruby+Warrior" rel="tag"> Gem Sawyer Modern Day Ruby Warrior</a>
