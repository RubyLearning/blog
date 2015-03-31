---
draft: false
title: Do you know what's new in Ruby 1.9?
date: 2010-10-26
author: Carlo Pecchia
categories:
- beginners
- ruby
- ruby masters
layout: post
permalink: /2010/10/26/do-you-know-whats-new-in-ruby-1-9/
tags:
- programming
- ruby 1.9
- ruby programming
---
This guest post is by **[Carlo Pecchia](http://carlopecchia.eu/)**, who
is an IT engineer mainly interested on agile methodologies and "good
practices" for developing large and complex systems. He is also
interested in web architectures and emerging programming languages.<!--more-->

![Carlo Pecchia](http://rubylearning.com/images/carlopecchia.jpg "Carlo Pecchia")

## Do you know what's new in Ruby 1.9?

With major version 1.9 the Ruby language took a series of improvements
devoted to rationalizing and better organizing the internal structure of
the language itself.

The language "core" sized from around 3 MB in version 1.0 to 30 in
version 1.9: we see that both internal and external (some interfaces)
refactoring was needed. Let me show you the main improvements
introduced.

## Smart things

A list of a general -- smart -- improvements: `Rubygems` in now officially
a part of Ruby, and so is `Rake`. Some poorly used libraries were
removed from the core -- but always available as gems: soap, jruby, etc.

## Objects hieararchy

A new root in the class hierarchy was introduced `BasicObject`:

    1.8 => [Class, Module, Object, Kernel]
    1.9 => [Class, Module, Object, Kernel, BasicObject]

    BasicObject.instance_methods
    # => [:==, :equal?, :!, :!=, :instance_eval, :instance_exec, :__send__]

This serves to better organize things internally. This class is so
"basic" that it doesn't give even the `object_id`, in fact the last
statement will generate an error ('undefined method...'):

    foo = BasicObject.new
    foo.object_id

## Loving chain methods

More often in Ruby than in other languages, the chain methods style is
used. In order to improve this "technique" the new method `tap` has been
released (and backported into 1.8 too):

    >puts "Hello".reverse
                .tap{ |o| puts "reversed: #{o}" }
                .upcase

    # => reversed: olleH
    # => OLLEH

Basically, we can now also "do something else too" with the object in
the chain.

## Main changes

Let us now see the main areas where changes were introduced: symbols,
arrays, hashes and blocks. And finally, an interesting improvement
toward parallelism: the fibers.

## Symbols

Symbols are now interpreted as string wrt regular expressions:

    >a = [:windows, :mac, :amiga]
    puts a.grep(/ac/)

    # 1.8 => []
    # 1.9 => mac

We can also get a Proc from a symbol:

    u = :upcase.to_proc
    u.call('lorem ipsum...')

## Arrays

Arrays, a fundamental store in any modern language, have been deeply
revisited:

-   the method `to_a` doesn't belong to the `Object` class.
-   arrays can be easily created with the homonym class (eg:
    `a = Array('apple', 'bananas')`) for an improved code readability.
-   in such a creation the implicit separator -- default is "\\n" -- is
    not considered.
-   the splat operator (`*a = some_array_here`) has a more consistent
    behaviour.

## Hashes

Now hashes (finally!) are stable data structures: elements keep order
insertion. Even a Hash is not -- by definition -- such a kind of data
abstraction, that feature can be very handy.

It's now possible to declare hashes differently (use name: value pairs
to create a hash if the keys are symbols):

    data = { jan: 201234, feb: 234234, mar: 234345 }

And that, obviously, make obsolete some other forms: if-then-else with
colon and splat hashes definition (eg:
`h = {"jan", 201234, "feb", 234234, "mar", 234345}`).

**Easy access within a string**:

    puts "First two months of this year was: %{jan} and %{feb}" % data

Finally, to make things more consistently, we have two major
differences:

-   `select` method on hash -- that aim to act like a "filter" -- return a
    hash (in 1.8 it returns an array of arrays...)
-   `to_s` method return and internal representation of the hash, rather
    than join together keys and values.

## Blocks

Still considering the mantra word "rationalization", blocks and methods
share the same syntax for parameters:

    def my_method(foo, bar=10, *baz)
      ...
    end

    lambda {|foo, bar=10, *baz| ...}

An interesting "correction" was made on block parameters: now they are
local variables and don't collide with external references:

    foo = 'this is an external variable'
    bar = 23

    10.times do |foo|
      bar = foo + 1
      # foo here is unrelated from the external name
    end

**This was a major issue in language version 1.8.**

Of course, if `within` a block (outside parameters list) we reference an
external variable, that one will be modified. With 1.9 we can "protect"
such variables declaring an internal homonym:

    foo = 'this is an external variable'
    bar = 23

    10.times do |i;foo|
      bar = bar + 1
      foo = bar % 2
    end

    # foo untouched, but bar modified

## Fibers

We will see an increasing usage of parallelism techniques in
programming, and the spread of (really interesting) languages like
Clojure and Erlang is a clear sign. Ruby too -- with 1.9 -- offers a nice
tool for programmers: fibers.

They are a lightweight processes -- memory footprint is only 4Kbytes --
conceived for a cooperative concurrence. Basically we can think of them
like Procs that maintain status over calls:

    fb = Fiber.new do |val|
      Fiber.yield "That's all... (#{val})"
      Fiber.yield "folks! (#{val})"
    end

    puts fb.resume 10
    ...
    puts fb.resume 20

## A final note

The transition -- fairly smooth in my opinion -- towards version 1.9 is
still in progress. I hope this post helps you to understand the major
differences and to act accordingly when coding, both by your own and on
someone elses code.

![Alert!](http://rubylearning.com/images/icon_warning.png "Alert!")**A
final tip:** pay attention when using a gem -- the interesting project
[http://isitruby19.com/](http://isitruby19.com/) can help you see if a
gem is already ported on Ruby 1.9.

*I hope you found this article valuable. Feel free to ask questions and
give feedback in the comments section of this post. Thanks!*

***Do read* these awesome Guest Posts:**

-   [The value of a personal bug
    log](http://rubylearning.com/blog/2010/10/25/the-value-of-a-personal-bug-log/)
-   [Do You Enjoy Your Code
    Quality?](http://rubylearning.com/blog/2010/10/18/do-you-enjoy-your-code-quality/)

