---
draft: false
title: "Ruby gems — what, why and how"
date: 2010-12-14
author: "Gonçalo Silva"
categories:
- Beginners
- Ruby
- Ruby Masters
layout: post
permalink: /2010/12/14/ruby-gems-%e2%80%94-what-why-and-how/
tags:
- programming
- Ruby Gems
- ruby programming
---
## Ruby gems — what, why and how

This guest post is by **Gonçalo Silva**, who is a full-time Ruby on
Rails developer at [escolinhas.pt](http://escolinhas.pt/) and has
participated in the Ruby Summer of Code 2010. He loves and contributes
to many open-source projects, being a fan of Linux, Ruby and Android. He
likes to call himself a hacker, but that’s just an excuse for being in
front of the computer all the time. Oh, and he tweets at
[@goncalossilva](http://twitter.com/goncalossilva).<!--more-->

## What is a gem

![Gonçalo
Silva](http://rubylearning.com/images/Goncalo_Silva_125x125.jpg) At its
most basic form, a Ruby gem is a package. It has the necessary files and
information for being installed on the system. Quoting
[RubyGems](http://docs.rubygems.org/read/chapter/1%20Introducing%20RubyGems):
«A gem is a packaged Ruby application or library. It has a name (e.g.
rake) and a version (e.g. 0.4.16)».

Being very powerful, gems are of great importance in the Rubyland. They
can easily be used to extend or change functionality within Ruby
applications.

### Structure

Every gem is different, but most follow a basic structure:

    gem/
    |-- lib/
    |   |-- gem.rb
    |-- test/
    |-- README
    |-- Rakefile
    |-- gem.gemspec

Your gem’s code is located under *lib/* which typically holds a Ruby
file with the name of the gem. You can choose to have all the magic
happening in this file, but you can also use it to load some other Ruby
files also located under *lib/*, typically inside a folder with the
gem’s name. Confused? Have a look:

    your_gem/
    |-- lib/
    |   |-- your_gem.rb
    |   |-- your_gem/
    |   |   |-- source1.rb
    |   |   |-- source2.rb
    |-- ...

The test folder’s name is not necessarily named *test/*. When you’re
working with [RSpec](http://rspec.info/%20RSpec), for instance, its name
is usually *spec/*. As you’ve probably guessed, this folder holds tests
for your gem.

After the *README* file, which hopefully doesn’t need any introduction,
comes the *Rakefile*. In a gem’s context, the *Rakefile* is extremely
useful. It can hold various tasks to help building, testing and
debugging your gem, among all other things that you might find useful.

The *gemspec*—as the name implies—contains your gem’s specification by
defining several attributes. An example *gemspec* file could be:

    Gem::Specification.new do |s|
      s.name              = "gem"
      s.version           = "0.0.1"
      s.platform          = Gem::Platform::RUBY
      s.authors           = ["Gonçalo Silva"]
      s.email             = ["goncalossilva@gmail.com"]
      s.homepage          = "http://github.com/goncalossilva/gem_template"
      s.summary           = "Sample gem"
      s.description       = "A gem template"
      s.rubyforge_project = s.name

      s.required_rubygems_version = ">= 1.3.6"

      # If you have runtime dependencies, add them here
      # s.add_runtime_dependency "other", "~> 1.2"

      # If you have development dependencies, add them here
      # s.add_development_dependency "another", "= 0.9"

      # The list of files to be contained in the gem
      s.files         = `git ls-files`.split("\n")
      # s.executables   = `git ls-files`.split("\n").map{|f| f =~ /^bin\/(.*)/ ? $1 : nil}.compact
      # s.extensions    = `git ls-files ext/extconf.rb`.split("\n")

      s.require_path = 'lib'

      # For C extensions
      # s.extensions = "ext/extconf.rb"
    end

Some attributes like the name, version, platform and summary are
required others are optional. If you use git with your project, you can
use the nifty trick shown above to list the project’s files, executables
and extensions. If you don’t, you can simply fall back to using pure
Ruby code like:

    s.files = Dir["{lib}/**/*.rb", "{lib}/**/*.rake", "{lib}/**/*.yml", "LICENSE", "*.md"]

The [dummy](http://github.com/goncalossilva/dummy) gem is very simple.
Because of this, it perfectly illustrates some of the ideas explained
above. Some interesting bits are shown below:

    dummy/
    |-- lib/
    |   |-- dummy/
    |   |   |-- core_ext/
    |   |   |   |-- array.rb
    |   |   |   |-- string.rb
    |   |   |-- address.rb
    |   |   |-- company.rb
    |   |   |-- ...
    |   |-- dummy.rb

This gem is organized into several source files inside *lib/*. The
*dummy.rb* implements the **top-level module** and **loads all
functionality** from the Ruby files inside *lib/dummy/*. It also
includes some core extensions, namely to the *Array* and *String*
classes (which are part of Ruby’s core).

### RubyGems

Finally, RubyGems. It is a package manager which became part of the
standard library in Ruby 1.9. It allows developers to search, install
and build gems, among other features. All of this is done by using the
`gem` command-line utility. You can find its website at
[rubygems.org](http://rubygems.org%20rubygems.org%20%7C%20your%20community%20gem%20host/).

## Why is this useful

Gems are very useful for not reinventing the wheel and avoiding
duplication. That’s basically it. Many Ruby developers create and
publish awesome gems which address specific requirements, solve specific
problems or add specific functionality. Anyone who comes across similar
requirements or problems can use them and eventually improve them.
That’s the joint awesomeness of Ruby’s strong open-source foundation and
extreme flexibility. Anyway, you’re reading this article… so you’ve
probably understood the concept and grasped its usefulness long before
reading this paragraph.

## How to make your own

Making your own gem is nothing more than packaging your library or
application according to the structure stated above. Put all your code
under *lib/*, all your tests under *test/* or *spec/*, your gem
specification under *your\_gem.gemspec* and you’re good to go. Of
course, a few other files might come in handy, namely a *Rakefile*, a
*README* and a *LICENSE*. A *CHANGELOG*, sometimes, might be useful as
well.

### Ruby Idioms

When developing a gem, you are probably creating, extending or
overriding functionality. You might want people to include your module
in their classes, or perhaps you just want to extend a given class with
your module—it’s your choice. What you shouldn’t really do, however, is
reinventing Ruby’s module system. There is an [excellent blog
post](http://yehudakatz.com/2009/11/12/better-ruby-idioms/) on this
which can help if you—like many gem authors I’ve seen—start overriding
`include` to behave like `extend`. It’s very important to understand the
difference between the two and, fortunately, there are [great
resources](http://railstips.org/blog/archives/2009/05/15/include-vs-extend-in-ruby/)
about this out there.

### Developing with Bundler

Using [Bundler](http://gembundler.com/%20Bundler) to manage your gem’s
dependencies is also pretty easy. Just create a *Gemfile* and add:

    gemspec

After this, fire Bundler:

    bundle install

And yes, you got it right. After adding `gemspec` to your *Gemfile*,
Bundler can scan your *gemspec*, find your runtime and development
dependencies and install them for you.

While not being mandatory, I **strongly** recommend you to consider
using Bundler to manage your gem’s dependencies. If used correctly, it
can probably be a time saver.

### Testing

When it comes to testing, you’ve got plenty of good options. Some people
rely on test-unit (or minitest in 1.9), others prefer RSpec. It’s really
up to you. The only bad choice you can possibly make is opting to
**not** testing your gems at all.

Once again, I’m going to use dummy’s simplicity to explain this a bit
further. All tests were built on test-unit and are organized as follows:

    dummy/
    |-- test/
    |   |-- address_test.rb
    |   |-- company_test.rb
    |   |-- ...
    |   |-- test_helper.rb

As you’ve seen, tests are structured similarly to dummy itself. The
test\_helper is in charge of loading the necessary libraries and setting
up any variables or methods used across most (if not all) tests. All
tests are organized into files which target specific functionality in
dummy. The tests contained in *address\_test.rb* run against
*address.rb* and so on.

### Publishing

After everything is coded and tested, all you got left to do is
packaging and publishing. The previously mentioned *gem* utility makes
it all very simple. Just run `gem build your_gem.gemspec` and you should
see something along these lines:

    Successfully built RubyGem
    Name: your_gem
    Version: 0.0.1
    File: your_gem-0.0.1.gem

Pushing your gem to RubyGems is as easy as it is to build it. Just
`gem push your_gem-0.0.1.gem` and soon it’ll be published. Be aware that
the first time you issue this command you’ll be prompted to login with a
RubyGems.org account.

Concerning this, I like keeping these simple tasks in my *Rakefile*:

    desc "Validate the gemspec"
    task :gemspec do
      gemspec.validate
    end

    desc "Build gem locally"
    task :build => :gemspec do
      system "gem build #{gemspec.name}.gemspec"
      FileUtils.mkdir_p "pkg"
      FileUtils.mv "#{gemspec.name}-#{gemspec.version}.gem", "pkg"
    end

    desc "Install gem locally"
    task :install => :build do
      system "gem install pkg/#{gemspec.name}-#{gemspec.version}"
    end

These help me build and install my gems. They also aid at keeping all
packages in the *pkg/* folder, which is useful for keeping the root
directory clean and tidy.

### Gems for building gems

There are a few gems which were specifically created to help developers
build their own gems. Among them are the renowned
[jeweler](https://github.com/technicalpickles/jeweler),
[hoe](https://github.com/seattlerb/hoe) and
[echoe](https://github.com/fauna/echoe). I can’t go into detail
in any of these since I’ve never really used them – I started building
my gem skeleton from scratch right at the beginning. However, some of
these tools are very helpful so you should **really** take a look and
see if any fits your needs.

### Gem template

As I mentioned, I’ve been using a gem skeleton for some time now, which
[you can find at
GitHub](https://github.com/goncalossilva/gem_template).
Every gem I’ve built started with that template, which I kept trying to
improve over time.

You can start your gems from scratch, but that’s just nonsense. You
should create your own skeleton, use one made by someone else or use a
third-party gem to help creating your gem.

### Legen—*wait for it*—dary

Ruby gems are filled with awesomeness. Hop in and start making your own!

*Feel free to ask questions and give feedback in the comments section of
this post. Thanks and Good Luck!*
