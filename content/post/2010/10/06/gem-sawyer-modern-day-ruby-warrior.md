---
draft: false
title: Gem Sawyer, Modern Day Ruby Warrior
date: 2010-10-06
author: Nick Quaranto
categories:
- Beginners
- Ruby
- Ruby Masters
layout: post
permalink: /2010/10/06/gem-sawyer-modern-day-ruby-warrior/
tags:
- Gem Sawyer Modern Day Ruby Warrior
- Nick Quaranto
- programming
- Ruby
- Ruby Beginners
- Ruby for Noobs
---
This guest post is contributed by **[Nick
Quaranto](http://twitter.com/qrush)**, a web developer at
[Thoughtbot](http://thoughtbot.com/) in Boston, MA. Nick maintains<!--more-->
[RubyGems.org](http://rubygems.org/) and he's a proud to be a part of
the Ruby community. He cut his teeth on classic ASP and ASP.NET at
first, but discovered Ruby on Rails through his university and dove in
head first. Nick pretends he's a bassist with famous prog rock bands
when not coding.

![Nick
Quaranto](http://en.gravatar.com/userimage/938917/6d1a54abf9a4ee9d6fd682c193ec2edc.png?size=125)

## Gem Sawyer, Modern Day Ruby Warrior

You're using [RubyGems](http://rubygems.org/) on a daily basis when
programming with Ruby, but how do they work? Gems are now a ubiquitous
part of the Ruby developer's toolkit. If you're fresh to Ruby and
haven't really learned what RubyGems can do for you yet, you're about to
find out!

## What's in a gem?

Ruby! Lots of it. Gems are just a simple format for publishing and
sharing Ruby code. Let's explore a simple one, and one of my favorites,
[jekyll](http://rubygems.org/gems/jekyll). First, let's see if the gem
exists. We could go to RubyGems.org to do this, but the `gem` command
has a lot of built-in searching commands.

    % gem list jekyll -r

    *** REMOTE GEMS ***

    jekyll (0.7.0)
    jekyll-epub (0.0.3)
    jekyll-localization (0.0.6)
    ....

This command will ask the remote source (the `-r` flag specifies this)
if there's any gems available under that name. By default this looks at
RubyGems.org, but it could be any URL. Next, let's get the gem on our
system:

    % gem install jekyll
    Successfully installed jekyll-0.7.0
    1 gem installed

    % gem unpack jekyll
    Unpacked gem: '/private/tmp/jekyll-0.7.0'

These two commands downloaded the gem and unzipped it from a compressed
state in a new folder from my current directory. The directory structure
here is common to all gems. I've ignored a lot of the files here, but
here's the basics of the internals.

    jekyll-0.7.0 % tree -L 2
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
    +-- test

There's a few administrative files here, such as the `README` and code
license. Hopefully you'll see those in every gem, along with a decent
changelog or history. Most gems have a `Rakefile` which can run tests
and perform other automation tasks as well. This gem is pretty well
tested, so the test files are included in both the `test` directory for
[shoulda](http://github.com/thoughtbot/shoulda) and a `features`
directory for [cucumber](http://cukes.info/) tests.

The meat of a gem really begins with `lib` directory. RubyGems really
just manages your Ruby load path, or how your ruby code is found by the
`require` statement. When you `require` a gem, really you're just
placing that gem's `lib` directory onto your `$LOAD_PATH`. Let's try
this out in IRB and get some help from the pretty\_print library
included with Ruby. Passing `-r` to `irb` will automatically `require` a
library when loaded.

    % irb -rpp
    >> pp $LOAD_PATH
    ["/Users/qrush/.rvm/rubies/ree-1.8.7-2010.02/lib/ruby/site_ruby/1.8",
     "/Users/qrush/.rvm/rubies/ree-1.8.7-2010.02/lib/ruby/site_ruby/1.8/i686-darwin10.3.1",
     "/Users/qrush/.rvm/rubies/ree-1.8.7-2010.02/lib/ruby/site_ruby",
     "/Users/qrush/.rvm/rubies/ree-1.8.7-2010.02/lib/ruby/vendor_ruby/1.8",
     "/Users/qrush/.rvm/rubies/ree-1.8.7-2010.02/lib/ruby/vendor_ruby/1.8/i686-darwin10.3.1",
     "/Users/qrush/.rvm/rubies/ree-1.8.7-2010.02/lib/ruby/vendor_ruby",
     "/Users/qrush/.rvm/rubies/ree-1.8.7-2010.02/lib/ruby/1.8",
     "/Users/qrush/.rvm/rubies/ree-1.8.7-2010.02/lib/ruby/1.8/i686-darwin10.3.1",
     "."]

By default we have just a few system directories on our load path and
the Ruby standard libraries. If we were to run `require 'rake'` right
now, it would fail, because RubyGems isn't loaded yet.

    % irb -rpp
    >> require 'rake'
    LoadError: no such file to load -- rake
            from (irb):2:in `require'
            from (irb):2
    >> require 'rubygems'
    => true
    >> require 'rake'
    => true
    >> pp $LOAD_PATH[0..1]
    ["/Users/qrush/.rvm/gems/ree-1.8.7-2010.02/gems/rake-0.8.7/bin",
     "/Users/qrush/.rvm/gems/ree-1.8.7-2010.02/gems/rake-0.8.7/lib"]

Once we've required rake, then RubyGems automatically drops the bin and
lib directories onto the `$LOAD_PATH`. Boom! The `bin` directory is used
for creating executables that use your gem's code, such as `rake`. These
are completely optional and you could have multiple per gem if you
wanted.

That's basically it for what's in a gem. Drop Ruby code into `lib`, name
a Ruby file the same as your gem (so for jekyll, `jekyll.rb`) and it's
loaded by RubyGems.

The `lib` directory normally contains only one `.rb` file on the top
directory, and then another folder with the same name as the gem with
more code in it. Jekyll has plenty, and Rake does too. Before you go any
further with this article, download your favorite gem, `gem unpack` it,
and take a peek around.

## How do I make a gem?

Creating and publishing your own gem is simple thanks to the tools baked
right into RubyGems. Let's make a simple "hello world" gem, and feel
free to play along at home! This is really as simple as it gets.

I started with just one Ruby file for my "hola" gem, and the gemspec.

    % tree
    .
    +-- hola.gemspec
    +-- lib
        +-- hola.rb

The code inside of `lib/hola.rb` is pretty bare bones, we just want to
see some output.

    % cat lib/hola.rb
    class Hola
      def self.hi
        puts "Hello world!"
      end
    end

The gemspec defines what's in the gem, who made it, and the version of
the gem. It's also your interface to RubyGems.org, all of the
information you see on a gem page (like
[jekyll's](http://rubygems.org/gems/jekyll)) comes from the gemspec.

    % cat hola.gemspec
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
    end

Look familiar? The gemspec is also Ruby, so you could wrap scripts to
generate the file names and bump the version number. Once we have our
gemspec, we have to build a gem from it. We can then install it locally
to test it out.

    % gem build hola.gemspec
      Successfully built RubyGem
      Name: hola
      Version: 0.0.0
      File: hola-0.0.0.gem

    % gem install ./hola-0.0.0.gem
    Successfully installed hola-0.0.0
    1 gem installed

Of course, our smoke test isn't over yet: Let's require our gem and use
it!

    % irb -rubygems
    >> require 'hola'
    => true
    >> Hola.hi
    Hello world!

Hola now needs to be shared with the rest of the Ruby community.
Publishing your gem out to RubyGems.org only takes one command, granted
you have an account on the site. Once you're signed up, then you can
push out a gem.

    % gem push hola-0.0.0.gem
    Enter your RubyGems.org credentials.
    Don't have an account yet? Create one at http://rubygems.org/sign_up
       Email:   nick@quaran.to
       Password:
    Signed in.
    Pushing gem to RubyGems.org...
    Successfully registered gem: hola (0.0.0)

In just a few moments (usually a minute), your gem will be available for
installation by anyone.

    % gem list -r hola

    *** REMOTE GEMS ***

    hola (0.0.0)

    % gem install hola
    Successfully installed hola-0.0.0
    1 gem installed

It's really that easy to share code with Ruby and RubyGems.

## Exit the warrior, today's Gem Sawyer

With this basic understanding of the RubyGems ecosystem on your system,
I hope you'll be the next developer to share your creations with others
on RubyGems.org. For a more detailed explanation of how to build and
deploy a gem, check out [this
railscast](http://railscasts.com/episodes/183-gemcutter-jeweler).

*Have **you** written any Ruby gems? Why don't you share them with us?
Let us know in the comments section of this post. Thanks!*

***Do read* these awesome Guest Posts:**

-   [An Introduction to Outside-in
    Development](http://rubylearning.com/blog/2010/10/05/outside-in-development/)
-   [Ruby
    Forensics](http://rubylearning.com/blog/2010/10/04/ruby-forensics/)
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

