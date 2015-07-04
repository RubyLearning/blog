---
draft: false
title: Don't Know Metaprogramming In Ruby?
date: 2010-11-23
author: Gavin Morrice
categories:
- beginners
- metaprogramming
- popular
- ruby
- ruby masters
layout: post
permalink: /2010/11/23/dont-know-metaprogramming-in-ruby/
tags:
- programming
- ruby metaprogramming
- ruby programming
---
## Don’t Know Metaprogramming In Ruby?

This guest post is by **Gavin Morrice**, Managing Director of [Katana
Code Ltd.](http://katanacode.com), a software boutique based in
Edinburgh, Scotland. He likes sharing Rails tips<!--more--> on [his
site](http://gavinmorrice.com/). When he’s not writing code he’s usually
weightlifting, reading or writing

## Introduction

<img src="http://rubylearning.com/images/GavinMorrice.jpg" alt="Gavin
Morrice" height="320" width="320">

One of the most impressive aspects of Ruby is its metaprogramming
capabilities. As a dynamic language, Ruby gives you the freedom to
define methods and even classes during runtime. Metaprogramming with
Ruby, one can do in a few minutes what other languages may take hours to
do. By cleverly planning your code and applying the techniques mentioned
here, you’ll be able to write code that is DRYer, lighter, more
intuitive and more scalable.

This tutorial assumes you are already familiar with the following
concepts:

-   Ruby Classes and class inheritance
-   Instance methods and instance variables
-   Raising exceptions

and standard Ruby notations:

* to show that method_name is a method in MyClass
  * `MyClass#method_name`
* to show the return value of a method
  * `=>`

## What is Metaprogramming?

According to Wikipedia:

> Metaprogramming is the writing of computer programs that write or
> manipulate other programs (or themselves) as their data, or that do
> part of the work at compile time that would otherwise be done at
> runtime. In many cases, this allows programmers to get more done in
> the same amount of time as they would take to write all the code
> manually, or it gives programs greater flexibility to efficiently
> handle new situations without recompilation. Or, more simply put:
> Metaprogramming is writing **code that writes code** during runtime to
> make your life easier.

## Adding methods in the context of an object {#object_context}

In Ruby, *everything* is an object. The base class in Ruby is called
`Object` (or `BasicObject` in Ruby 1.9) and all other classes inherit
properties from it. Every object in Ruby has its own methods, and
instance variables which can be added, edited or removed during runtime.
Here is a simple example:

    # Example 1: create a new instance of class Object
    my_object = Object.new

    # define a method on my_object to set the instance variable @my_instance_variable
    def my_object.set_my_variable=(var)
      @my_instance_variable = var
    end

    # define a method on my_object to return value of instance variable @my_instance_variable
    def my_object.get_my_variable
      @my_instance_variable
    end

    my_object.set_my_variable = "Hello"
    my_object.get_my_variable # => Hello

In this example, we have created a new instance of the `Object` class
and defined two methods on that instance for writing and reading
(setting and getting). The two new methods that we’ve defined are only
available to our object `my_object` and will not be present on any
other instance of the `Object` class. We can prove this by extending our
example like so:

    # Example 2: create a new instance of class Object
    my_object = Object.new

    # create a second instance of class Object
    my_other_object = Object.new

    # define a method on my_object to set the instance variable @my_instance_variable
    def my_object.set_my_variable=(var)
      @my_instance_variable = var
    end

    # define a method on my_object to return value of instance variable @my_instance_variable
    def my_object.get_my_variable
      @my_instance_variable
    end

    my_object.set_my_variable = "Hello"
    my_object.get_my_variable # => Hello

    my_other_object.get_my_variable = "Hello" # => NoMethodError

When we try to call `get_my_variable()` on our second object
`my_other_object` the interpreter raises a `NoMethodError` to tell us
that `my_other_object` doesn’t recognise the method
`get_my_variable()`.

To see where this feature of Ruby might be useful, let’s look at a more
common example: writing class methods.

### Writing Class Methods

You’ll probably already be aware of this common syntax for writing
methods to your Ruby classes:

    # Example 3
    class MyClass
      def self.capitalize_name
        name.upcase
      end
    end
    print MyClass.capitalize_name # => MYCLASS

Within our class definition we’re defining a method on one particular
object just like we did in Example 1. Only, this time the object is
*self* (in this case MyClass). And as we saw in Example 2, the
capitalize_name() method is only available to this particular object
MyClass and no other class (yet). This is just one example of how to
write a class method. To refer back to Example 3 again, here are three
different approaches to defining the same class methods:

    # Example 4
    # approach 1
    class MyClass
      # defining a class method within the class definition
      def MyClass.capitalize_name
        name.upcase
      end
    end

    # approach 2
    class MyClass;end
    # defining a class method out with the class definition
    def MyClass.capitalize_name
      name.upcase
    end

    # approach 3
    # define a new class named MyClass
    MyClass = Class.new
    # add the capitalize_name to MyClass
    def MyClass.capitalize_name
      name.upcase
    end

See how similar approach 3 here is to Example 1? You will hopefully have
realised that when you write a class method in Ruby, it’s just the same
as creating an instance of any class and adding methods only to that
instance, only this time its an instance of the class “Class”.

## Writing Code That Writes Code {#writing_code_that_writes_code}

An important philosophy in programming is DRY (Don’t Repeat Yourself).
Writing code that is the same (or similar) several times is not only an
inefficient waste of time, it can become a nightmare when you need to
make changes in future. In many cases, it’s possible to remove this
duplication of effort by writing code that writes the code for you.
Here’s an example…
 Consider an application for a car manufacturer to store and access data
on each of it’s models. Within the application we have a class called
CarModel:

    # Example 5
    class CarModel
      def engine_info=(info)
        @engine_info = info
      end

      def engine_info
        @engine_info
      end

      def engine_price=(price)
        @engine_price = price
      end

      def engine_price
        @engine_price
      end

      def wheel_info=(info)
        @wheel_info = info
      end

      def wheel_info
        @wheel_info
      end

      def wheel_price=(price)
        @wheel_price = price
      end

      def wheel_price
        @wheel_price
      end

      def airbag_info=(info)
        @airbag_info = info
      end

      def airbag_info
        @airbag_info
      end

      def airbag_price=(price)
        @airbag_price = price
      end

      def airbag_price
        @airbag_price
      end

      def alarm_info=(info)
        @alarm_info = info
      end

      def alarm_info
        @alarm_info
      end

      def alarm_price=(price)
        @alarm_price = price
      end

      def alarm_price
        @alarm_price
      end

      def stereo_info=(info)
        @stereo_info = info
      end

      def stereo_info
        @stereo_info
      end

      def stereo_price=(price)
        @stereo_price = price
      end

      def stereo_price
        @stereo_price
      end
    end

Each car model comes with various features such as “stereo”, “alarm”
etc. We have a method to get and set the values of each feature of the
car. Each feature has information and price so for every new feature we
add to the CarModel class, we need to define two new methods:
`feature_info` and `feature_price`.
 Since each of these methods are similar, we can do the following to
simplify this code:

    # Example 6
    class CarModel
      FEATURES = ["engine", "wheel", "airbag", "alarm", "stereo"]

      FEATURES.each do |feature|
        define_method("#{feature}_info=") do |info|
          instance_variable_set("@#{feature}_info", info)
        end

        define_method("#{feature}_info") do
          instance_variable_get("@#{feature}_info")
        end

        define_method "feature_price=" do |price|
          instance_variable_set("@#{feature}_price", price)
        end

        define_method("#{feature}_price") do
          instance_variable_get("@#{feature}_price")
        end
      end
    end

In this example, we start by defining an array called `FEATURES` which
includes all the features we wish to add methods for. Then, for each
feature, we use Ruby’s
[Module#define_method](http://www.ruby-doc.org/core/classes/Module.html#M001654)
to define four methods for each feature. Just like in Example 5, the
four methods are getter and setter methods for the feature’s price and
info. The only difference is, they have been written dynamically when
the class is defined and not by us. We use
[Object#instance_variable_set()](http://www.ruby-doc.org/core/classes/Object.html#M000368)
to set the value of instance variables for each feature and
[Object#instance_variable_get](http://www.ruby-doc.org/core/classes/Object.html#M000378)
to return the values for each.

The need to define getter and setter methods like this is quite common
in Ruby so it’s not surprising that Ruby already has methods that do
just that. `Module#attr_accessor` can be used to do the same thing as in
Example 6 with just a single line of code.

    # Example 7
    class CarModel
      attr_accessor :engine_info, :engine_price, :wheel_info, :wheel_price, :airbag_info, :airbag_price, :alarm_info, :alarm_price, :stereo_info, :stereo_price
    end

Great! But this still isn’t ideal. For each feature, we still need to
define two attributes (`feature_info` and `feature_price`). Ideally we
should be able to call a method that can do the same as in Example 7 but
by only listing each feature once.

    # Example 8
    class CarModel
      # define a class macro for setting features
      def self.features(*args)
        args.each do |feature|
          attr_accessor "#{feature}_price", "#{feature}_info"
        end
      end

      # set _info and _price methods for each of these features
      features :engine, :wheel, :airbag, :alarm, :stereo
    end

In this example, we take each of the arguments for `CarModel#features`
and pass them to `attr_accessor` with `_price` and `_info` extensions.
Although this approach is slightly more involved than the one in Example
7, it ensures that each feature is treated the same and means that
adding more attributes in future will be simpler.

## A Brief Explanation of the Ruby Object Model

Before going any further, it’s important that we understand the basics
of Ruby’s Object Model and how Ruby deals with method calls.  Whenever you call
a method on an object, the interpreter first looks through the object’s
instance methods to see if it can find that method.  If the interpreter can
find the method, it will execute it as expected but if not, it will pass the
request up the chain to the object’s class.  If it can’t find the method there
it will continue to look in that class’s parent class, then the parent’s parent
etc. up to the `Object` class itself. But it doesn’t stop there… If the
interpreter can’t find the method anywhere up the object’s chain
of inheritance, it will go back to the object and call another method
called
[method_missing()](http://www.ruby-doc.org/core/classes/Kernel.src/M005925.html).
Just like with our first method, the interpreter looks for
[method_missing()](http://www.ruby-doc.org/core/classes/Kernel.src/M005925.html)
in the object’s methods, then the object’s class’s instance methods etc.
until reaches the `Object` class where
[method_missing()](http://www.ruby-doc.org/core/classes/Kernel.src/M005925.html)
**is** defined and will raise a `NoMethodError` error. This is when
metaprogramming really starts getting fun!

By defining
[method_missing()](http://www.ruby-doc.org/core/classes/Kernel.src/M005925.html)
yourself within a class, it’s possible to change this default behaviour
for some pretty useful effects.
[method_missing()](http://www.ruby-doc.org/core/classes/Kernel.src/M005925.html)
is passed two arguments; the name of the missing method (as a symbol)
and array of its arguments. Let’s look at an example:

    # Example 9
    class MyGhostClass
      def method_missing(name, *args)
        puts "#{name} was called with arguments: #{args.join(',')}"
      end
    end

    m = MyGhostClass.new
    m.awesome_method("one", "two") # => awesome_method was called with arguments: one,two
    m.another_method("three", "four") # => another_method was called with arguments: three,four

There’s no method named awesome_method() or another_method() within
our class yet when we try calling it, we don’t see the usual
`NoMethodError`. Instead, we see the name of the methods and their
arguments, just like we defined in method_missing().

We can expand this idea a little more by adding conditions to this
method. Let’s say, for example, that all methods containing the word
“awesome” should be printed out just like in Example 9. All other
methods should raise the default `NoMethodError`.

    # Example 10
    class MyGhostClass
      def method_missing(name, *args)
        if name.to_s =~ /awesome/
          puts "#{name} was called with arguments: #{args.join(',')}"
        else
          super
        end
      end
    end

    m = MyGhostClass.new
    m.awesome_method("one", "two") # =>  awesome_method was called with arguments: one,two
    m.another_method("three", "four") # =>  NoMethodError

This time, calling `awesome_method` behaves just like in Example 9, but
`another_method` doesn’t contain the word “awesome” so we pass this up
the chain of inheritance so the default behaviour is not broken.

## Ghost Methods

Strictly speaking, `MyGhostClass#awesome_method` is not really a method.
If we create an instance of MyGhostClass and scan it’s methods for any
with “awesome” in the name we won’t find any.

    # Example 11
    @m = MyGhostClass.new
    @m.methods.grep(/awesome/) # => nil

Instead, we call this a ghost method. Ghost methods come with pros and
cons. The major pro is the ability to write code that responds to
methods when you have no way of knowing the names of those methods in
advance. The major con is that changing Ruby’s default behaviour like
this may cause unexpected bugs if you’re not careful with your method
names.
 With that in mind, let’s go back to our CarModel example and see if we
can extend the functionality a little further.

    # Example 12
    class CarModel
      def method_missing(name, *args)
        name = name.to_s
        super unless name =~ /(_info|_price)=?$/
        if name =~ (/=$/)
          instance_variable_set("@#{name.chop}", args.first)
        else
          instance_variable_get("@#{name}")
        end
      end
    end

This example may look a little complex but is really quite simple.
First, we take the name argument and convert it from a symbol to a
string. Next, we say “send this method up the inheritance chain unless
the name ends with `_price`, `_price=`, `_info` or `_info=`". If the
name ends in an equals sign then we know this is a setter method so we
set an instance variable with the same name as our method (minus the
`=`). If there’s no equals sign then we know this is a getter method and
so we return the instance variable with the same name.

Now, we don’t have to specify the features each car model has in
advance. We can simply get and set values on any `_price` or `_info`
attribute during runtime:

    # Example 13
    @car_model = CarModel.new

    @car_model.stereo_info    = "CD/MP3 Player"
    @car_model.stereo_price   = "£79.99"

    @car_model.stereo_info  # => "CD/MP3 Player"
    @car_model.stereo_price # => "£79.99"

## Conclusion

This tutorial has only scratched the surface of Ruby’s metaprogramming
capabilities but hopefully it’s enough to spark your curiosity and will
urge you to learn more about metaprogramming. The [Ruby
API](http://ruby-doc.org/core/) covers all the methods I’ve talked about
here plus more. For further reading, check out:

-   [Module#included](http://ruby-doc.org/core/classes/Module.html#M001660)
-   [Module#class_eval](http://ruby-doc.org/core/classes/Module.html#M001650)
-   [Object#instance_eval](http://ruby-doc.org/core/classes/Object.html#M000334)
-   [Struct](http://ruby-doc.org/core/classes/Struct.html)

*I hope you found this article valuable. Feel free to ask questions and
give feedback in the comments section of this post. Thanks!*

***Do also read* these awesome Guest Posts:**

-   [Does Ruby Have Too Many Equality
    Tests?](http://rubylearning.com/blog/2010/11/17/does-ruby-have-too-many-equality-tests/)
-   [Why Use Single Sign-in Solutions in
    Rails?](http://rubylearning.com/blog/2010/11/16/why-use-single-sign-in-solutions-in-rails/)
-   [How does your code
    smell?](http://rubylearning.com/blog/2010/11/08/how-does-your-code-smell/)
-   [Do YOU know
    Resque?](http://rubylearning.com/blog/2010/11/08/do-you-know-resque/)
-   [Do You Understand Ruby’s Objects, Messages and
    Blocks?](http://rubylearning.com/blog/2010/11/03/do-you-understand-rubys-objects-messages-and-blocks/)
-   [How Does One Use Design Patterns In
    Ruby?](http://rubylearning.com/blog/2010/11/02/how-does-one-use-design-patterns-in-ruby/)
-   [Do you know what’s new in Ruby
    1.9?](http://rubylearning.com/blog/2010/10/26/do-you-know-whats-new-in-ruby-1-9/)
-   [The value of a personal bug
    log](http://rubylearning.com/blog/2010/10/25/the-value-of-a-personal-bug-log/)
-   [Do You Enjoy Your Code
    Quality?](http://rubylearning.com/blog/2010/10/18/do-you-enjoy-your-code-quality/)

If you want to learn **Ruby Metaprogramming** in-depth, join our online
course that starts 4th Dec. 2010. For details [click
here](http://rubylearning.com/blog/2010/11/06/ruby-metaprogramming-course-6th-batch-learn-to-think-in-ruby/).
