---
title: Ruby gems — what, why and how
author: Gonçalo Silva
date: 2010-12-14
layout: post
permalink: /2010/12/14/ruby-gems-%e2%80%94-what-why-and-how/
thesis_description:
  - "Gems are one of the wonders of the Ruby land - it's important to understand what they are, why they exist and how they work."
thesis_keywords:
  - programming,ruby,gem,rubygems
topsy_short_url:
  - http://bit.ly/fwjMLp
categories:
  - Beginners
  - Ruby
  - Ruby Masters
tags:
  - programming
  - Ruby Gems
  - ruby programming
---
<div>
  <h3>
    Ruby gems — what, why and how
  </h3>
  
  <p class="update">
    This guest post is by <strong>Gonçalo Silva</strong>, who is a full-time Ruby on Rails developer at <a href="http://escolinhas.pt/">escolinhas.pt</a> and has participated in the Ruby Summer of Code 2010. He loves and contributes to many open-source projects, being a fan of Linux, Ruby and Android. He likes to call himself a hacker, but that&#8217;s just an excuse for being in front of the computer all the time. Oh, and he tweets at <a href="http://twitter.com/goncalossilva">@goncalossilva</a>.
  </p>
  
  <h3>
    What is a gem
  </h3>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/Goncalo_Silva_125x125.jpg" alt="Gonçalo Silva" /> <span class="drop_cap">A</span>t its most basic form, a Ruby gem is a package. It has the necessary files and information for being installed on the system. Quoting <a href="http://docs.rubygems.org/read/chapter/1%20Introducing%20RubyGems">RubyGems</a>: «A gem is a packaged Ruby application or library. It has a name (e.g. rake) and a version (e.g. 0.4.16)».
  </p>
  
  <p>
    Being very powerful, gems are of great importance in the Rubyland. They can easily be used to extend or change functionality within Ruby applications.
  </p>
  
  <h4>
    Structure
  </h4>
  
  <p>
    Every gem is different, but most follow a basic structure:
  </p>
  
  <pre>gem/
|-- lib/
|   |-- gem.rb
|-- test/
|-- README
|-- Rakefile
|-- gem.gemspec</pre>
  
  <p>
    Your gem&#8217;s code is located under <em>lib/</em> which typically holds a Ruby file with the name of the gem. You can choose to have all the magic happening in this file, but you can also use it to load some other Ruby files also located under <em>lib/</em>, typically inside a folder with the gem&#8217;s name. Confused? Have a look:
  </p>
  
  <pre>your_gem/
|-- lib/
|   |-- your_gem.rb
|   |-- your_gem/
|   |   |-- source1.rb
|   |   |-- source2.rb
|-- ...</pre>
  
  <p>
    The test folder&#8217;s name is not necessarily named <em>test/</em>. When you&#8217;re working with <a href="http://rspec.info/%20RSpec">RSpec</a>, for instance, its name is usually <em>spec/</em>. As you&#8217;ve probably guessed, this folder holds tests for your gem.
  </p>
  
  <p>
    After the <em>README</em> file, which hopefully doesn&#8217;t need any introduction, comes the <em>Rakefile</em>. In a gem&#8217;s context, the <em>Rakefile</em> is extremely useful. It can hold various tasks to help building, testing and debugging your gem, among all other things that you might find useful.
  </p>
  
  <p>
    The <em>gemspec</em>—as the name implies—contains your gem&#8217;s specification by defining several attributes. An example <em>gemspec</em> file could be:
  </p>
  
  <pre>Gem::Specification.new do |s|
  s.name              = "gem"
  s.version           = "0.0.1"
  s.platform          = Gem::Platform::RUBY
  s.authors           = ["Gonçalo Silva"]
  s.email             = ["goncalossilva@gmail.com"]
  s.homepage          = "http://github.com/goncalossilva/gem_template"
  s.summary           = "Sample gem"
  s.description       = "A gem template"
  s.rubyforge_project = s.name

  s.required_rubygems_version = "&gt;= 1.3.6"

  # If you have runtime dependencies, add them here
  # s.add_runtime_dependency "other", "~&gt; 1.2"

  # If you have development dependencies, add them here
  # s.add_development_dependency "another", "= 0.9"

  # The list of files to be contained in the gem
  s.files         = `git ls-files`.split("\n")
  # s.executables   = `git ls-files`.split("\n").map{|f| f =~ /^bin\/(.*)/ ? $1 : nil}.compact
  # s.extensions    = `git ls-files ext/extconf.rb`.split("\n")

  s.require_path = 'lib'

  # For C extensions
  # s.extensions = "ext/extconf.rb"
end</pre>
  
  <p>
    Some attributes like the name, version, platform and summary are required others are optional. If you use git with your project, you can use the nifty trick shown above to list the project&#8217;s files, executables and extensions. If you don&#8217;t, you can simply fall back to using pure Ruby code like:
  </p>
  
  <pre>s.files = Dir["{lib}/**/*.rb", "{lib}/**/*.rake", "{lib}/**/*.yml", "LICENSE", "*.md"]</pre>
  
  <p>
    The <a href="http://github.com/goncalossilva/dummy">dummy</a> gem is very simple. Because of this, it perfectly illustrates some of the ideas explained above. Some interesting bits are shown below:
  </p>
  
  <pre>dummy/
|-- lib/
|   |-- dummy/
|   |   |-- core_ext/
|   |   |   |-- array.rb
|   |   |   |-- string.rb
|   |   |-- address.rb
|   |   |-- company.rb
|   |   |-- ...
|   |-- dummy.rb</pre>
  
  <p>
    This gem is organized into several source files inside <em>lib/</em>. The <em>dummy.rb</em> implements the <strong>top-level module</strong> and <strong>loads all functionality</strong> from the Ruby files inside <em>lib/dummy/</em>. It also includes some core extensions, namely to the <em>Array</em> and <em>String</em> classes (which are part of Ruby&#8217;s core).
  </p>
  
  <h4>
    RubyGems
  </h4>
  
  <p>
    Finally, RubyGems. It is a package manager which became part of the standard library in Ruby 1.9. It allows developers to search, install and build gems, among other features. All of this is done by using the <code>gem</code> command-line utility. You can find its website at <a href="http://rubygems.org%20rubygems.org%20%7C%20your%20community%20gem%20host/">rubygems.org</a>.
  </p>
  
  <h3>
    Why is this useful
  </h3>
  
  <p>
    Gems are very useful for not reinventing the wheel and avoiding duplication. That&#8217;s basically it. Many Ruby developers create and publish awesome gems which address specific requirements, solve specific problems or add specific functionality. Anyone who comes across similar requirements or problems can use them and eventually improve them. That&#8217;s the joint awesomeness of Ruby&#8217;s strong open-source foundation and extreme flexibility. Anyway, you&#8217;re reading this article&#8230; so you&#8217;ve probably understood the concept and grasped its usefulness long before reading this paragraph.
  </p>
  
  <h3>
    How to make your own
  </h3>
  
  <p>
    Making your own gem is nothing more than packaging your library or application according to the structure stated above. Put all your code under <em>lib/</em>, all your tests under <em>test/</em> or <em>spec/</em>, your gem specification under <em>your_gem.gemspec</em> and you&#8217;re good to go. Of course, a few other files might come in handy, namely a <em>Rakefile</em>, a <em>README</em> and a <em>LICENSE</em>. A <em>CHANGELOG</em>, sometimes, might be useful as well.
  </p>
  
  <h4>
    Ruby Idioms
  </h4>
  
  <p>
    When developing a gem, you are probably creating, extending or overriding functionality. You might want people to include your module in their classes, or perhaps you just want to extend a given class with your module—it&#8217;s your choice. What you shouldn&#8217;t really do, however, is reinventing Ruby&#8217;s module system. There is an <a href="http://yehudakatz.com/2009/11/12/better-ruby-idioms/">excellent blog post</a> on this which can help if you—like many gem authors I&#8217;ve seen—start overriding <code>include</code> to behave like <code>extend</code>. It&#8217;s very important to understand the difference between the two and, fortunately, there are <a href="http://railstips.org/blog/archives/2009/05/15/include-vs-extend-in-ruby/">great resources</a> about this out there.
  </p>
  
  <h4>
    Developing with Bundler
  </h4>
  
  <p>
    Using <a href="http://gembundler.com/%20Bundler">Bundler</a> to manage your gem&#8217;s dependencies is also pretty easy. Just create a <em>Gemfile</em> and add:
  </p>
  
  <pre>gemspec</pre>
  
  <p>
    After this, fire Bundler:
  </p>
  
  <pre>bundle install</pre>
  
  <p>
    And yes, you got it right. After adding <code>gemspec</code> to your <em>Gemfile</em>, Bundler can scan your <em>gemspec</em>, find your runtime and development dependencies and install them for you.
  </p>
  
  <p>
    While not being mandatory, I <strong>strongly</strong> recommend you to consider using Bundler to manage your gem&#8217;s dependencies. If used correctly, it can probably be a time saver.
  </p>
  
  <h4>
    Testing
  </h4>
  
  <p>
    When it comes to testing, you&#8217;ve got plenty of good options. Some people rely on test-unit (or minitest in 1.9), others prefer RSpec. It&#8217;s really up to you. The only bad choice you can possibly make is opting to <strong>not</strong> testing your gems at all.
  </p>
  
  <p>
    Once again, I&#8217;m going to use dummy&#8217;s simplicity to explain this a bit further. All tests were built on test-unit and are organized as follows:
  </p>
  
  <pre>dummy/
|-- test/
|   |-- address_test.rb
|   |-- company_test.rb
|   |-- ...
|   |-- test_helper.rb</pre>
  
  <p>
    As you&#8217;ve seen, tests are structured similarly to dummy itself. The test_helper is in charge of loading the necessary libraries and setting up any variables or methods used across most (if not all) tests. All tests are organized into files which target specific functionality in dummy. The tests contained in <em>address_test.rb</em> run against <em>address.rb</em> and so on.
  </p>
  
  <h4>
    Publishing
  </h4>
  
  <p>
    After everything is coded and tested, all you got left to do is packaging and publishing. The previously mentioned <em>gem</em> utility makes it all very simple. Just run <code>gem build your_gem.gemspec</code> and you should see something along these lines:
  </p>
  
  <pre>Successfully built RubyGem
Name: your_gem
Version: 0.0.1
File: your_gem-0.0.1.gem</pre>
  
  <p>
    Pushing your gem to RubyGems is as easy as it is to build it. Just <code>gem push your_gem-0.0.1.gem</code> and soon it&#8217;ll be published. Be aware that the first time you issue this command you&#8217;ll be prompted to login with a RubyGems.org account.
  </p>
  
  <p>
    Concerning this, I like keeping these simple tasks in my <em>Rakefile</em>:
  </p>
  
  <pre>desc "Validate the gemspec"
task :gemspec do
  gemspec.validate
end

desc "Build gem locally"
task :build =&gt; :gemspec do
  system "gem build #{gemspec.name}.gemspec"
  FileUtils.mkdir_p "pkg"
  FileUtils.mv "#{gemspec.name}-#{gemspec.version}.gem", "pkg"
end

desc "Install gem locally"
task :install =&gt; :build do
  system "gem install pkg/#{gemspec.name}-#{gemspec.version}"
end</pre>
  
  <p>
    These help me build and install my gems. They also aid at keeping all packages in the <em>pkg/</em> folder, which is useful for keeping the root directory clean and tidy.
  </p>
  
  <h4>
    Gems for building gems
  </h4>
  
  <p>
    There are a few gems which were specifically created to help developers build their own gems. Among them are the renowned <a href="https://github.com/technicalpickles/jeweler%20jeweler">jeweler</a>, <a href="https://github.com/seattlerb/hoe%20hoe">hoe</a> and <a href="https://github.com/fauna/echoe%20echoe">echoe</a>. I can&#8217;t go into detail in any of these since I&#8217;ve never really used them &#8211; I started building my gem skeleton from scratch right at the beginning. However, some of these tools are very helpful so you should <strong>really</strong> take a look and see if any fits your needs.
  </p>
  
  <h4>
    Gem template
  </h4>
  
  <p>
    As I mentioned, I&#8217;ve been using a gem skeleton for some time now, which <a href="https://github.com/goncalossilva/gem_template%20gem_template">you can find at GitHub</a>. Every gem I&#8217;ve built started with that template, which I kept trying to improve over time.
  </p>
  
  <p>
    You can start your gems from scratch, but that&#8217;s just nonsense. You should create your own skeleton, use one made by someone else or use a third-party gem to help creating your gem.
  </p>
  
  <h4>
    Legen—<em>wait for it</em>—dary
  </h4>
  
  <p>
    Ruby gems are filled with awesomeness. Hop in and start making your own!
  </p>
  
  <p>
    <em>Feel free to ask questions and give feedback in the comments section of this post. Thanks and Good Luck!</em>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>, <a href="http://technorati.com/tag/Ruby+Gems" rel="tag"> Ruby Gems</a>
