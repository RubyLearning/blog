---
title: All about Struct
author: Steve Klabnik
date: 2012/09/06
layout: post
permalink: /2012/09/06/all-about-struct/
thesis_description:
  - Steve Klabnik shows us how to take advantage of Struct and OStruct in Ruby.
thesis_keywords:
  - struct, Programming,Ruby programming
topsy_short_url:
  - http://bit.ly/TkmLgm
categories:
  - Beginners
  - Ruby
tags:
  - programming
  - ruby programming
  - struct
---
<div>
  <h3>
    All about Struct
  </h3>
  
  <p class="update">
    This guest post is by <strong><a href="https://github.com/steveklabnik">Steve Klabnik</a></strong>. Steve is a Rubyist, writer, and teaches Ruby and Rails classes with Jumpstart Lab. He maintains Draper, Hackety Hack, and Shoes, and<br /> contributes to Rails from time to time.
  </p>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/steve_cropped.jpg" alt="Steve Klabnik" /> <span class="drop_cap">O</span>ne of my favorite classes in Ruby is <code>Struct</code>, but I feel like many Rubyists don&#8217;t know when to take advantage of it. The standard library has a lot of junk in it, but <code>Struct</code> and <code>OStruct</code> are super awesome.
  </p>
  
  <h3 id="struct">
    Struct
  </h3>
  
  <p>
    If you haven&#8217;t used <code>Struct</code> before, here&#8217;s <a href="http://www.ruby-doc.org/core-1.9.3/Struct.html" rel="">the documentation of Struct from the Ruby standard library</a>.
  </p>
  
  <p>
    Structs are used to create super simple classes with some instance variables and a simple constructor. Check it:
  </p>
  
  <pre>Struct.new("Point", :x, :y) #=&gt; Struct::Point
origin = Struct::Point.new(0,0) #=&gt; #</pre>
  
  <p>
    Nobody uses it this way, though. Here&#8217;s the way I first saw it used:
  </p>
  
  <pre>class Point &lt; Struct.new(:x, :y)
end
origin = Point.new(0,0)</pre>
  
  <p>
    Wait, what? Inherit&#8230;from an instance of something? Yep!
  </p>
  
  <pre>1.9.3p194 :001 &gt; Struct.new(:x,:y) =&gt; #&lt;Class:0x007f8fc38da2e8&gt;</pre>
  
  <p>
    <code>Struct.new</code> gives us a <code>Class</code>. We can inherit from this just like any other <code>Class</code>. Neat!
  </p>
  
  <p>
    However, if you&#8217;re gonna make an empty class like this, I prefer this way:
  </p>
  
  <pre>Point = Struct.new(:x, :y)
origin = Point.new(0,0)</pre>
  
  <p>
    Yep. Classes are just constants, so we assign a constant to that particular <code>Class</code>.
  </p>
  
  <p>
    If you&#8217;d like, you can pass a block to the <code>Struct</code>:
  </p>
  
  <pre>Point = Struct.new(:x, :y) do
  def translate(x,y)
    self.x += x
    self.y += y
  end
end</pre>
  
  <p>
    Now we can do this:
  </p>
  
  <pre>origin = Point.new(0,0)
origin.translate(1,2)
puts origin #=&gt; &lt;struct Point x=1, y=2&gt;</pre>
  
  <h3 id="ostruct">
    OStruct
  </h3>
  
  <p>
    <a href="http://ruby-doc.org/stdlib-1.9.3/libdoc/ostruct/rdoc/OpenStruct.html" rel=""><code>OStruct</code></a>s are like <code>Struct</code> on steroids. Check it:
  </p>
  
  <pre>require 'ostruct'
origin = OpenStruct.new
origin.x = 0
origin.y = 0
origin = OpenStruct.new(:x =&gt; 0, :y =&gt; 0)</pre>
  
  <p>
    <code>OStruct</code>s are particularly good for configuration objects. Since any method works to set data in an <code>OStruct</code>, you do not have to worry about enumerating every single option that you need:
  </p>
  
  <pre>require 'ostruct'

def set_options 
  opts = OpenStruct.new
  yield opts
  opts
end

options = set_options do |o|
  o.set_foo = true
  o.load_path = "whatever:something"
end

options #=&gt; #</pre>
  
  <p>
    Neat, eh?
  </p>
  
  <h3 id="structs_for_domain_concepts">
    Structs for domain concepts
  </h3>
  
  <p>
    You can use <code>Struct</code>s to help reify domain concepts into simple little classes. For example, say we have this code, which uses a date:
  </p>
  
  <pre>class Person
  attr_accessor :name, :day, :month, :year

  def initialize(opts = {})
    @name = opts[:name]
    @day = opts[:day]
    @month = opts[:month]
    @year = opts[:year]
  end

  def birthday
    "#@day/#@month/#@year"
  end
end</pre>
  
  <p>
    and we have this spec
  </p>
  
  <pre>$:.unshift("lib")
require 'person'

describe Person do
  it "compares birthdays" do
    joe = Person.new(:name =&gt; "Joe", :day =&gt; 5, :month =&gt; 6, :year =&gt; 1986)
    jon = Person.new(:name =&gt; "Jon", :day =&gt; 7, :month =&gt; 6, :year =&gt; 1986)

    joe.birthday.should == jon.birthday
  end
end</pre>
  
  <p>
    It fails, of course. Like this:
  </p>
  
  <pre>$ rspec
F

Failures:

1) Person compares birthdays
Failure/Error: joe.birthday.should == jon.birthday
expected: "7/6/1986"
got: "5/6/1986" (using ==)
# ./spec/person_spec.rb:9:in `block (2 levels) in'

Finished in 0.00053 seconds
1 example, 1 failure

Failed examples:

rspec ./spec/person_spec.rb:5 # Person compares birthdays</pre>
  
  <p>
    Now. We have these two birthdays. In this case, we know about why the test was failing, but imagine this failure in a real codebase. Are these month/day/year or day/month/year? You can&#8217;t tell, it could be either. If we switched our code to this:
  </p>
  
  <pre>class Person
  attr_accessor :name, :birthday

  Birthday = Struct.new(:day, :month, :year)

  def initialize(opts = {})
    @name = opts[:name]
    @birthday = Birthday.new(opts[:day], opts[:month], opts[:year])
  end
end</pre>
  
  <p>
    We get this failure instead:
  </p>
  
  <pre>$ rspec
F

Failures:

1) Person compares birthdays
Failure/Error: joe.birthday.should == jon.birthday
expected: #
got: # (using ==)

Diff:
@@ -1,2 +1,2 @@
-#
+#
# ./temp.rb:18:in `block (2 levels) in '

Finished in 0.00514 seconds

1 example, 1 failure Failed examples: rspec ./spec/person_spec.rb:5 # Person compares birthdays</pre>
  
  <p>
    We have a way, way more clear failure. We can clearly see that its our days that are off.
  </p>
  
  <p>
    Of course, there are other good reasons to package related instance variables into <code>Struct</code>s, too: it makes more conceptual sense. This code represents our intent better: a Person has a Birthday, they don&#8217;t have three unrelated numbers stored inside them somehow. If we need to add something to our concept of birthdays, we now have a place to put it.
  </p>
  
  <p class="update">
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post.</em> Also, do check out Steve&#8217;s other articles: &#8220;<a href="http://rubylearning.com/blog/2011/07/28/how-do-i-test-my-code-with-minitest/">How do I test my code with Minitest?</a> and &#8220;<a href="http://rubylearning.com/blog/2010/12/20/how-do-i-keep-multiple-ruby-projects-separate/">How do I keep multiple Ruby projects separate?</a>&#8221; on RubyLearning. Thanks!
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/struct" rel="tag">struct</a>, <a href="http://technorati.com/tag/Programming" rel="tag"> Programming</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>
