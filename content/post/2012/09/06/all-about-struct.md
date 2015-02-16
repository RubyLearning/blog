---
title: All about Struct
author: Steve Klabnik
date: "2012-09-06"
layout: post
permalink: /2012/09/06/all-about-struct/
thesis_description:
  - Steve Klabnik shows us how to take advantage of Struct and OStruct in Ruby.
thesis_keywords:
  - struct, Programming,Ruby programming
topsy_short_url:
  - http://bit.ly/TkmLgm
categories:
  - beginners
  - ruby
tags: ["programming", "ruby", "struct"]
---
### All about Struct

This guest post is by **[Steve
Klabnik](https://github.com/steveklabnik)**. Steve is a Rubyist, writer,
and teaches Ruby and Rails classes with Jumpstart Lab. He maintains
Draper, Hackety Hack, and Shoes, and\
 contributes to Rails from time to time.

![Steve Klabnik](http://rubylearning.com/images/steve_cropped.jpg) One
of my favorite classes in Ruby is `Struct`, but I feel like many
Rubyists don’t know when to take advantage of it. The standard library
has a lot of junk in it, but `Struct` and `OStruct` are super awesome.

### Struct

If you haven’t used `Struct` before, here’s [the documentation of Struct
from the Ruby standard
library](http://www.ruby-doc.org/core-1.9.3/Struct.html).

Structs are used to create super simple classes with some instance
variables and a simple constructor. Check it:

    Struct.new("Point", :x, :y) #=> Struct::Point
    origin = Struct::Point.new(0,0) #=> #

Nobody uses it this way, though. Here’s the way I first saw it used:

    class Point < Struct.new(:x, :y)
    end
    origin = Point.new(0,0)

Wait, what? Inherit…from an instance of something? Yep!

    1.9.3p194 :001 > Struct.new(:x,:y) => #<Class:0x007f8fc38da2e8>

`Struct.new` gives us a `Class`. We can inherit from this just like any
other `Class`. Neat!

However, if you’re gonna make an empty class like this, I prefer this
way:

    Point = Struct.new(:x, :y)
    origin = Point.new(0,0)

Yep. Classes are just constants, so we assign a constant to that
particular `Class`.

If you’d like, you can pass a block to the `Struct`:

    Point = Struct.new(:x, :y) do
      def translate(x,y)
        self.x += x
        self.y += y
      end
    end

Now we can do this:

    origin = Point.new(0,0)
    origin.translate(1,2)
    puts origin #=> <struct Point x=1, y=2>

### OStruct

[`OStruct`](http://ruby-doc.org/stdlib-1.9.3/libdoc/ostruct/rdoc/OpenStruct.html)s
are like `Struct` on steroids. Check it:

    require 'ostruct'
    origin = OpenStruct.new
    origin.x = 0
    origin.y = 0
    origin = OpenStruct.new(:x => 0, :y => 0)

`OStruct`s are particularly good for configuration objects. Since any
method works to set data in an `OStruct`, you do not have to worry about
enumerating every single option that you need:

    require 'ostruct'

    def set_options 
      opts = OpenStruct.new
      yield opts
      opts
    end

    options = set_options do |o|
      o.set_foo = true
      o.load_path = "whatever:something"
    end

    options #=> #

Neat, eh?

### Structs for domain concepts {#structs_for_domain_concepts}

You can use `Struct`s to help reify domain concepts into simple little
classes. For example, say we have this code, which uses a date:

    class Person
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
    end

and we have this spec

    $:.unshift("lib")
    require 'person'

    describe Person do
      it "compares birthdays" do
        joe = Person.new(:name => "Joe", :day => 5, :month => 6, :year => 1986)
        jon = Person.new(:name => "Jon", :day => 7, :month => 6, :year => 1986)

        joe.birthday.should == jon.birthday
      end
    end

It fails, of course. Like this:

    $ rspec
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

    rspec ./spec/person_spec.rb:5 # Person compares birthdays

Now. We have these two birthdays. In this case, we know about why the
test was failing, but imagine this failure in a real codebase. Are these
month/day/year or day/month/year? You can’t tell, it could be either. If
we switched our code to this:

    class Person
      attr_accessor :name, :birthday

      Birthday = Struct.new(:day, :month, :year)

      def initialize(opts = {})
        @name = opts[:name]
        @birthday = Birthday.new(opts[:day], opts[:month], opts[:year])
      end
    end

We get this failure instead:

    $ rspec
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

    1 example, 1 failure Failed examples: rspec ./spec/person_spec.rb:5 # Person compares birthdays

We have a way, way more clear failure. We can clearly see that its our
days that are off.

Of course, there are other good reasons to package related instance
variables into `Struct`s, too: it makes more conceptual sense. This code
represents our intent better: a Person has a Birthday, they don’t have
three unrelated numbers stored inside them somehow. If we need to add
something to our concept of birthdays, we now have a place to put it.

*I hope you found this article valuable. Feel free to ask questions and
give feedback in the comments section of this post.* Also, do check out
Steve’s other articles: “[How do I test my code with
Minitest?](http://rubylearning.com/blog/2011/07/28/how-do-i-test-my-code-with-minitest/)
and “[How do I keep multiple Ruby projects
separate?](http://rubylearning.com/blog/2010/12/20/how-do-i-keep-multiple-ruby-projects-separate/)”
on RubyLearning. Thanks!

Technorati Tags: [struct](http://technorati.com/tag/struct),
[Programming](http://technorati.com/tag/Programming), [Ruby
programming](http://technorati.com/tag/Ruby+programming)
