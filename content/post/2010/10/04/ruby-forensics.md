---
draft: false
title: Ruby Forensics
date: 2010-10-04
author: Elise Huard
authorlink: http://twitter.com/elise_huard
categories:
- Beginners
- Ruby
- Ruby Masters
layout: post
permalink: /2010/10/04/ruby-forensics/
tags:
- Elise Huard
- programming
- Ruby
- Ruby Beginners
- Ruby for Noobs
- Ruby Forensics
---
This guest post is contributed by **[Elise
Huard](http://twitter.com/elise_huard)**, who is based in Brussels, Belgium and
is the owner of<!--more--> [Jabberwocky](http://jabberwocky.eu/), a solutions
company mostly focused on Rails. She has worked with a few other technologies
before falling in love with Rails and Ruby about 3 years ago and going
freelance to work with Ruby full time. She contributes to open source projects
as much as she can, and has given talks at a few Ruby and Rails conferences.
She's a jack of all trades, loves reading, tinkering, food, travel, learning,
and people out of the ordinary.

![Elise Huard](http://rubylearning.com/images/pic1-125.jpg)

## Ruby Forensics

Say you want to use a library, but no or very little documentation is
available, and you don't feel like diving into the code right away.

Well, you picked the right language. Ruby is blessed with what is called
[introspection](http://en.wikipedia.org/wiki/Type_introspection): if you
ask a Ruby program/class/module politely, it will tell you almost
anything about itself. This post will tell you some tricks I use on a
daily basis.

    module Layer
      FILLINGS = [:chocolate, :meringue, :jam, :cream, :strawberry]
      def fill(filling)
        puts "fill with #{filling}"
      end
    end

    class Cake
      include Layer
      attr_accessor :calories

      def ice
        @calories = @calories + 200
      end

      def eat
        puts "nom"
      end

      def self.bake
        return new
      end
    end

    class CheeseCake < Cake; end

Say you have a class, but you'd like to know what method it defines.

    Cake.public_instance_methods

Won't be that useful, because Ruby objects (with some exceptions like
`BasicObject`) have got a whole lot of methods out of the box. Rather,
use:

    Cake.public_instance_methods - Object.public_instance_methods
    => [:calories, :calories=, :ice, :eat, :fill]

If you want one particular method, and you have an idea of which name it
should have:

    (Cake.public_instance_methods - Object.public_instance_methods).grep(/eat/)

Will show if your instinct was right or not.

The same can be done for class methods, of course:

    (Cake.methods - Object.methods)
    => [:bake]

(`public_class_methods` also works.)

*Note:* this won't show you the dynamic methods, like `find_by_X` for
ActiveRecord. The class doesn't know it has these kind of methods in
itself. They're executed on the fly when the program hits
`method_missing`. You'd have to look at the classes' `method_missing`
method to find out.

Then there's the case where you'd like to know, exactly, where a method
was defined. Ruby gives us the `method` method, which takes a symbol
as an argument.

    Cake.new.method(:fill)
     => #<Method: Cake(Layer)#fill>

Which tells us it was defined in the Layer module, included in the Cake
class.

    Cake.new.method(:eat)
     => #<Method: Cake#eat>

Sometimes, you want to know which other classes your class was descended
from -- including mixed in modules. The `ancestors` method will show you:

    CheeseCake.ancestors
     => [CheeseCake, Cake, Layer, Object, Kernel, BasicObject]

Should you want to know about any constants, there's a method for that
too:

    Cake.constants
     => [:FILLINGS]

All these methods have a good chance of giving you the information you
want. When used in irb, together with a little experimentation, they can
really help you find the code you're looking for.

*I hope you found this article valuable. Feel free to ask questions and
give feedback in the comments section of this post. Thanks!*

***Do read* these awesome Guest Posts:**

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

