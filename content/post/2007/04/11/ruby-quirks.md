---
author: Satish Talim
categories:
- code snippets
- ruby
- tricks
date: 2007-04-11
layout: post
title: Ruby Quirks
---

**Ruby Quirks** – peculiarity of behavior? I know this topic is
debatable and remember "one man's meat is another man's poison!" I plan
to write down here (in no particular order), some of the little Ruby
quirks that I've picked up and which, I now use comfortably.

**1.**

Peter Cooper, the author of the book ‘Beginning Ruby' introduced me to
Real-Time chat using an IRC client. On the \#ruby channel at
irc://irc.freenode.net/ I heard of this quirk:

    class MotorCycle
      def initialize(make, color)
        @make, @color = make, color
      end
    end

    m = MotorCycle.new('Honda', 'blue')
    m.instance_variable_set(:@make, 'Kawasaki')
    m.instance_variable_set(:@gears, 4)
    puts m.inspect

Check the output of the above program. In the code above:

    m.instance_variable_set(:@gears, 4)

sets the instance variable names by *symbol* to *object*, thereby
frustrating the efforts of the class's author to attempt to provide
proper encapsulation. The variable did not have to exist prior to this
call. **Update:** Hal Fulton in his excellent book ‘The Ruby Way'
has this to say about `instance_variable_set`:

>> It's true these methods are powerful and potentially dangerous. They should
>> be used cautiously, not casually. But it's impossible to say whether
>> encapsulation is violated without looking at \*how these tools are used\*.
>> If they are used intentionally as part of a good design, then all is well.
>> If they are used to violate the design, or to circumvent a bad design, then
>> all is not well.

**2.**

This one is not really a quirk but appears to be one, especially for people
coming from a Java background. Last year, [Shashank Date][1] gave the
[PuneRuby][2] members a presentation on ‘Why Ruby Shines' and three points
stood out –

'Expressions everywhere', ‘Active Class Definitions' and ‘Everything is
an Object'.

***Expressions everywhere*** – In Ruby, everything
returns some value. Therefore a class definition is an expression and
one can say something like:

    c = class C
    end

The value of c is nil.

***Active Class Definitions*** – Look at
the following program:

    class C
      puts 'In class C'
    end

When this class is read the first time, it executes puts and the output
is – ‘In class C'.

***Everything is an Object*** – After being with Java since 1995, the concept
that classes in Ruby are first-class objects, is hard to digest at first – each
is an instance of class Class. When a new class is defined (typically using
class Name … end), an object of type Class is created and assigned to a
constant (Name. in this case). Hal Fulton's suggests a *mantra* to be recited
everyday – "Class _is an object_, and Object _is a class_."

**3.**

If I want to swap two variables, I would normally use an additional temporary
variable.

In Ruby, this is not necessary:

    x, y = y, x

will interchange the values of `x` and `y`.

**4**.

Jaaron, a reader of
this Learning Ruby Blog has this quirk for us. This one is well known
and is the cause of much frustration.

    x = 7
    [1,2,3].each do |x|
    end

If the name of a block parameter conflicts with the name of a local
variable, the behavior is to assign the local variable to the argument.
In this case, the local variable x gets assigned the value 1, then the
value 2, then the value 3. The value 7 is lost.

**Update (13th April):**

Matt Chen, Matthew King and Ara Vartanian have commented on this behavior. If
you refer to Programming Ruby Second Edition eBook (page 100) it says:

>> The whole issue with variable scope and blocks is one that generates
>> considerable discussion in the Ruby community. The current scheme has
>> definite problems (particularly when variables are unexpectedly aliased
>> inside blocks), but at the same time no one has managed to come up with
>> something thats both better and acceptable to the wider community. Matz is
>> promising changes in Ruby 2.0.

**5.**

Are instance variables inherited by a sub-class? David Black the author
of Ruby for Rails has this to say: Instance variables are per-object,
not per-class, and they're not inherited. But if a method uses one, and
that method is available to subclasses, then it will still use the
variable — but “the variable” in the sense of one per object. See the
following program:

    class C
      def initialize
        @n = 100
      end

      def increase_n
        @n *= 20
      end
    end

    class D < C
      def show_n
        puts "n is #{@n}"
      end
    end

    d = D.new
    d.increase_n
    d.show_n

The output is:

    >ruby p049instvarinherit.rb
    n is 2000
    >Exit code: 0

**6**.

Morgan Schweers, a reader of this blog has this quirk for us.

Imagine for a moment, that you want to be able to set a variable, but if
it's not set, you default to a known value. You'd rather do it on a
single line. One of my co-workers tried this:

    expand = defined?( expand ) ? expand : true

but `expand` is *defined* by being on the left hand side, BEFORE
the RHS is evaluated, so `defined?` returns `true`, but because expand
hasn't got a value yet, it returns nil. I tried:

    expand = true unless defined?(expand)

and it doesn't help either, which really shocked me.

I always believed that the postfix-conditional was evaluated before even
beginning to evaluate the operation, but I was distinctly disabused of this
notion by testing. Note that ‘expand?'' operator returns nil if its argument
(which can be an arbitrary expression) is not defined; otherwise it returns a
description of that argument. I don't understand the reason for the behavior,
and I think it's a bug, but I'd love to know a good language reason for it.

I am sure that you would have noticed many other **Ruby Quirks**. I'd
definitely like to hear and add them here.

**Information** Ruby is an open source thorough language of
utmost balance with combination of Perl, Smalltalk, Lisp, Ada and
Eiffel. With the recent developments in this language, most developers
use this language in the middle tier. Today is the era of developing
online business applications, [mobile software][3]: and its applications.
Most developers deploy their online applications after getting [business
web hosting][4] and then they market for these projects through
[affiliate marketing][5] campaigns or if they do not want to sell their
project they can use [ppc advertising][6] for earning some revenue or
can offer [ppc management][7] programs. When they are in the process of
development usually they [register domain][8] and use [domain
parking][9] facility, so that once their project is ready they can
instantly put it on the internet.

Technorati Tags:

* [Ruby Quirks](http://technorati.com/tag/Ruby+Quirks)

* [1]: http://rubylearning.com/blog/2007/04/11/interview-shashank-date/
* [2]: http://tech.groups.yahoo.com/group/puneruby/
* [3]: http://www.mysoftwarehubs.com
* [4]: http://www.envisionwebhosting.com
* [5]: http://www.getaffiliates.net
* [6]: http://www.qualifytraffic.com/Advertising-Info/PPC-Advertising.html
* [7]: http://www.performanceppc.com
* [8]: http://www.namingwiz.com
* [9]: http://www.nationaldomainreg.com/Domain-Parking.html
