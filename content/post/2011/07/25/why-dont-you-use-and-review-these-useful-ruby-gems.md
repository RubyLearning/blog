---
author: Satish Talim
categories:
- beginners
- ruby
date: 2011-07-25
layout: post
permalink: /2011/07/25/why-dont-you-use-and-review-these-useful-ruby-gems/
tags:
- programming
- ruby
- ruby gems
- rubyists
thesis_description:
- Showcasing some Ruby Gems written by developers like you and me.
thesis_keywords:
- Ruby,Ruby Gems,Rubyists,Programming
title: Why don't you use and review these useful Ruby Gems?
topsy_short_url:
- http://bit.ly/ogfWey
---

<div>
  <h3>
    Showcasing some Ruby Gems from developers like you and me
  </h3>
  
  <p class="alert">
    Why don&#8217;t you try out some of the Ruby Gems mentioned below, built by developers like you and me, and review them? Maybe there are some real &#8216;hidden&#8217; gems out there, wanting to be exposed!
  </p>
  
  <p>
    <strong><a href="https://github.com/benilovj/ascii-data-tools">ascii-data-tools</a></strong> developed by <a href="http://twitter.com/#!/benilov">Jake Benilov</a>. In his own words &#8211; &#8220;It provides a suite of tools for identifying, reading, enriching and editing ASCII data records. Such records are commonly used for data transfer within the banking (e.g. transfer statements between banks) and telecommunications sectors (e.g. call detail records).&#8221;
  </p>
  
  <p>
    The subject matter may be quite dry, but for me this gem has been a training dojo of sorts and hence may be of interest to you. I&#8217;ve tried to do several things with the development of the code:
  </p>
  
  <ul>
    <li>
      I&#8217;ve polished the code (some parts several times) in order to learn how to follow Uncle Bob&#8217;s clean code concepts and good OO principles (&#8220;tell, don&#8217;t ask&#8221;, etc)
    </li>
    <li>
      I&#8217;ve developed it using acceptance-test driven (with cucumber) and test-driven (with rspec). I&#8217;ve tried to apply <a href="http://specificationbyexample.com/key_ideas.html">Specification by Example</a> ideas to push the tests to the status of living documentation.
    </li>
    <li>
      I&#8217;ve tried to utilize Rubyisms (lots of composition with mixins, some meta-programming, internal DSLs) to maximise code clarity, simplicity, extensibility and testability.
    </li>
  </ul>
  
  <p>
    <strong><a href="https://github.com/mkorfmann/constructable">constructable</a></strong> developed by <a href="http://twitter.com/#!/mkorfmann">Manuel Korfmann</a>. In his own words &#8211; &#8220;constructable is a macro, kinda similar in spirit to <code>attr_reader</code> and <code>attr_accessor</code>, that makes the <code>new</code> method accept a hash, kinda like the way &#8216;create&#8217; does on ActiveRecord models.&#8221;
  </p>
  
  <p>
    <strong><a href="https://github.com/milandobrota/copyrb">copyrb</a></strong> developed by <a href="http://milandobrota.com/">Milan Dobrota</a>. In his own words &#8211; &#8220;I have written a quick gem that allows you to copy and paste Ruby objects across terminals. This gem was created primarily to simplify the process of copying objects between different Rails environments for people who spend a lot of time in the Rails console. For <a href="http://rubylove.info/post/3409677596/copyrb-gem-for-copying-and-pasting-ruby-objects">more details</a>.&#8221;
  </p>
  
  <p>
    <strong><a href="https://github.com/ralph/document_mapper">document_mapper</a></strong> developed by <a href="http://twitter.com/#!/ralph">Ralph von der Heyden</a>. In his own words &#8211; &#8220;A simple model layer that let&#8217;s you query text documents as if they were a database.&#8221;
  </p>
  
  <p>
    <strong><a href="https://github.com/ashbb/green_shoes">green_shoes</a></strong> developed by <a href="http://twitter.com/#!/ashbb">Satoshi Asakawa</a>. In his own words &#8211; &#8220;green_shoes is a Ruby domain specific language for beautiful Desktop Applications. The green_shoes dsl is so simple, even your pointy haired boss can understand it. The green_shoes project is based on _why-the-lucky-stiff&#8217;s Shoes, except for the following:
  </p>
  
  <ul>
    <li>
      green_shoes source code is all Ruby, so even you can contribute.
    </li>
    <li>
      green_shoes takes the Ruby DSL block-style approach, so all you have to do is write what you know: Ruby.
    </li>
    <li>
      green_shoes is a gem, so you can simply install with this command: <b>gem install green_shoes</b>&#8220;
    </li>
  </ul>
  
  <p>
    <strong><a href="https://github.com/dnagir/guard-rails-assets">guard-rails-assets</a></strong> developed by <a href="https://plus.google.com/116807208912177719748/">Dmytrii Nagirniak</a>. In his own words &#8211; &#8220;Automatically compile Rails 3.1 assets when files are modified. You can use it to automatically run the JavaScript tests and always have the files ready for it. It uses guard gem and Rails 3.1 built-in assets pipeline. Works great in combination with guard-jasmine-headless-webkit.&#8221;
  </p>
  
  <p>
    <strong><a href="https://github.com/darxriggs/ip-world-map">ip-world-map</a></strong> developed by <a href="https://plus.google.com/102020526201098205404">Rene Scheibe</a>. In his own words &#8211; &#8220;ip-world-map can be used to visualize web access logfiles (Apache format) on a world map. It performs geo-location resolution on the IPs and can generate fixed images, animated images or even videos.&#8221;
  </p>
  
  <p>
    <strong><a href="https://github.com/jeremygpeterson/jsdebug-rails">jsdebug-rails</a></strong> developed by <a href="https://plus.google.com/u/0/111499813995138329804/">Jeremy Peterson</a>. In his own words &#8211; &#8220;On June 16, 2011, Ruby Rogues described using <code>puts</code> as the best way to debug Ruby code, in same way, I wanted a way to log JavaScript debug statements in Firebug&#8217;s console. The main purpose of jsdebug-rails is to provide console wrapper for debug statements in JavaScript code during development, thus including the file name, line number, and comment/object. Once in production, all debug statements are removed from the JavaScript source code, so they are never processed and much smaller.&#8221;
  </p>
  
  <p>
    <strong><a href="https://github.com/citizen428/methodfinder">methodfinder</a></strong> developed by <a href="https://plus.google.com/u/0/101046237539584353961/">Michael Kohl</a>. In his own words &#8211; &#8220;This isn&#8217;t the first Ruby port of Smalltalk&#8217;s Method Finder, but I couldn&#8217;t find the old one and so decided to write one myself for the benefit of the <a href="http://RubyLearning.org/">RubyLearning.org</a> students. After being mentioned on the Ruby5 podcast, the project really caught on and I got some very good feedback as well as feature suggestions and patches. The main purpose of the library is helping new Rubyists find methods they didn&#8217;t know about. There are various usage examples in the README.&#8221;
  </p>
  
  <p>
    <strong><a href="https://github.com/marksim/omelettes">omelettes</a></strong> developed by <a href="http://twitter.com/#!/marksim">Mark Simoneau</a>. In his own words &#8211; &#8220;omelettes is a low-to-no configuration database obfuscation gem for ActiveRecord that allows you to remove sensitive data from the database and replace it with meaningless words that are the same length. It also integrates with Faker automatically and allows for full configuration in a single file.&#8221;
  </p>
  
  <p>
    <strong><a href="https://github.com/rosenfeld/rails-web-console">rails-web-console</a></strong> developed by <a href="https://plus.google.com/u/1/112046748094887665556/">Rodrigo Rosenfeld Rosas</a>. In his own words &#8211; &#8220;Some time ago I was planning to write an article comparing Rails and Grails and while trying to figure out what I did find useful in Grails that was missing in Rails, the only think I could think of was the console plugin for Grails. So, I decided to write one for Rails, which took only about an hour&#8230; It is just an interface for running Ruby commands in the context of a controller of the application. Think of it as the Rails console on the web, although with no auto-complete (yet). I was planning to add auto-complete, syntax highlight and other features, but couldn&#8217;t find any free time for doing that. There&#8217;s already some auto-complete examples in Github using websockets as well as Javascript code highlighters for Ruby available on the Internet. It is just a matter of getting some free time&#8230; <img src="http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" /> Since, I prefer the new Hash declaring syntax, this gem is not compatible with Ruby 1.8, but there&#8217;s a fork of it just for allowing its usage in Ruby 1.8 (replacing the new Hash declaration style with the old one).&#8221;
  </p>
  
  <p>
    <strong><a href="http://git.alech.de/?p=secretsharing.git">secretsharing</a></strong> developed by <a href="http://twitter.com/#!/alech">Alexander Klink</a>. In his own words &#8211; &#8220;It is not on GitHub, but I&#8217;m hosting the git repository myself. Cryptographic secret sharing is one of the lesser known cryptographic techniques. I&#8217;ve implemented the most prominent version, which was invented by Adi Shamir (the »S« in RSA) and can be used to share a secret (such as a password) between a number of people (let&#8217;s call that n) and only recover it if a certain number (k <= n) come together and combine their secret shares. Interestingly enough, if less than k people combine their shares, they learn nothing at all (in an information-theoretic understanding of »nothing«).&#8221;
  </p>
  
  <p>
    <strong><a href="https://github.com/colincasey/sequel-jdbc-hxtt-adapter">sequel-jdbc-hxtt-adapter</a></strong> developed by <a href="https://plus.google.com/103966022068171083922/">Colin Casey</a>. In his own words &#8211; &#8220;I had to do a lot of work with MS Access databases at my previous job and I found that the options for interacting with these databases programatically on the Windows platform left a lot to be desired. JRuby was beginning to make Ruby development on Windows a lot less painful so, using that interpreter and a pure JDBC driver, I created a Sequel adapter for working with MS Access files.&#8221;
  </p>
  
  <p>
    <strong><a href="https://github.com/Trevoke/SGFParser">SGFParser</a></strong> developed by <a href="http://gplus.to/trevoke">Aldric Giacomoni</a>. In his own words &#8211; &#8220;SgfParser allows you to parse, create and save SGF files. SGF (Smart Game Format) is a plain text format used to record moves in various board games, most famously Go/Weiqi/Baduk but also Chess and Backgammon. When I started this project, there was only one available, and it was a relatively tricky-to-find Ruby file online; no gems. This one aims to be the fastest (currently parses a 1.2 Mb SGF in ~3 seconds) and eventually also keep track of all the potential parsing or format errors that may have occurred without dying.&#8221;
  </p>
  
  <p>
    <strong><a href="https://github.com/thuss/standalone-migrations">standalone-migrations</a></strong> developed by <a href="http://twobitlabs.com/">Todd Huss</a>. In his own words &#8211; &#8220;standalone-migrations allows you to easily use Rails migrations in non-Rails and non-Ruby projects. My company, Two Bit Labs, develops iOS and Android apps for companies looking to go mobile and we usually use Rails on the server side. However, some of our clients use other server side platforms and we noticed that often our non-Rails clients struggled to effectively version and manage their database schema. So in 2008 we created standalone-migrations so non-Rails shops can enjoy all the database migration goodness that Rails offers. It&#8217;s been great to see standalone-migrations grow over the years with an active community!&#8221;
  </p>
  
  <p>
    <strong><a href="https://rubygems.org/gems/xapian_db">xapian_db</a></strong> developed by <a href="mailto:gernot@kogler-informatik.ch">Gernot Kogler</a>. In his own words &#8211; &#8220;xapian_db is a Ruby gem that combines features of nosql databases and fulltext indexing. It is based on Xapian, an efficient and powerful indexing library.&#8221;
  </p>
  
  <p class="update">
    I&#8217;ll be updating this page from time to time. <em>If you have written a Ruby Gem and want to showcase it here, please email me at <b>satish [dot] talim [at] gmail.com</b>. If you know of some real useful, &#8216;hidden&#8217; Ruby Gems, please let us know by commenting on this blog post</em>. Thank you for your time and help.
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Ruby+Gems" rel="tag">Ruby Gems</a>, <a href="http://technorati.com/tag/Rubyists" rel="tag">Rubyists</a>, <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>
