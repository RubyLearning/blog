---
draft: false
title: Almost everything is an object (and everything is almost an object!)
date: 2010-09-27
author: David Black
categories:
- Beginners
- Ruby
- Ruby Masters
layout: post
permalink: /2010/09/27/almost-everything-is-an-object-and-everything-is-almost-an-object/
tags:
- David A. Black
- programming
- Ruby
- ruby beginner
- Ruby for Noobs
topsy_short_url:
- http://bit.ly/cpn3BG
---
This guest post is contributed by **David A. Black**, a Senior Developer
with [Cyrus Innovation, Inc.](http://www.cyrusinnovation.com) David has
been programming in Ruby for ten years, and is the author of<!--more--> [The
Well-Grounded Rubyist](http://www.manning.com/black2) (Manning, 2009).
He’s one of the founding directors of [Ruby Central,
Inc.](http://www.rubycentral.org), the parent organization of the
[International Ruby Conference](http://www.rubyconf.org) (RubyConf).
David is also one of the most experienced Ruby and Rails trainers in the
the business. One of his current projects is [The Compleat
Rubyist](http://www.compleatrubyist.com), a training event taught by
David, Gregory Brown, and Jeremy McAnally. David is a frequent invited
speaker and keynoter at Ruby and Rails conferences, as well as users
groups, in the U.S. and abroad.

![David A.
Black](http://www.rubylearning.com/images/dblack.jpg "David A. Black")

## Almost everything is an object

### (and everything is almost an object!)

You’ll sometimes hear the statement that *Everything is an object in
Ruby.* But is that true?

It’s almost true, but not quite. No, this doesn’t mean we’ve caught Ruby
doing something wrong! It’s just an opportunity to look more closely at
how objects operate.

Here’s an example of something that isn’t an object: an argument list.
Consider a method call like this:

    create_person("David", "Black", "New Jersey")

Three strings are serving as method arguments, and those strings are
objects. But the argument list *itself* is not an object. There’s no
ArgumentList class. Moreover, it would be hard to imagine one. Consider
this code:

    arglist = ArgumentList.new  # no such thing; a thought experiment!
    arglist << "David"
    arglist << "Black"
    arglist << "New Jersey"

Already there’s a problem. The `<<` “operator” is actually a method.
That means that the code we’ve got is equivalent to this:

    arglist = ArgumentList.new
    arglist.<<("David")
    # etc.

So in order to use an ArgumentList object, we need to be able to
construct… an argument list.

The way out of this circularity is to include something in the language
that isn’t an object. Argument lists are part of the syntax of the
language. They’re not objects.

In addition to syntactic constructs like argument lists, Ruby also
includes non-objects in the form of keywords like `if`, `class`,
`alias`, and `begin`, `end`, `rescue`. Some of these keywords provide
control flow techniques; some, like `alias`, let you conduct business
with the interpreter that affects the world in which your objects live.
Non-object keywords help to create the framework inside of which your
objects can come into being and do everything they have to do.

So not everything is Ruby is an object, and for good reason. But there’s
a corollary to this point, and an important one: even though not
everything is an object, *everything does evaluate to an object*.

* * * * *

New to Ruby? Join our online Core Ruby course. Read details
[here](http://rubylearning.com/blog/2010/09/06/new-course-ruby-programming-101/).

* * * * *

## Everything (really, everything!) evaluates to an object

Every Ruby statement or expression evaluates to a single object. This is
true not only of variables, object literals, and method calls, but of
control-flow structures, keyword-based statements, class and method
definitions, and everything else. The object a statement evaluates to
may be `nil`, but it will always be something. Understanding this
principle can help you make sense of things that happen in your code,
and also provides some techniques you can take advantage of.

You can get lots of information about how statements evaluate to objects
by using irb. irb is very literal-minded, and will always print out the
value of the statement you type in. Sometimes the value is obvious;
sometimes what irb shows you is instructive. Let’s start with an irb
classic: `puts`.

    >> puts "Hi"
    Hi
    => nil

Note the `nil` at the end: that’s the return value from `puts`. After
all, `puts` is a method, so it has to return something. As it happens,
it always returns `nil`. The printing out of the string is a
side-effect.

Knowing that `puts` returns `nil` will help you predict the result of
evaluating this code:

    ["one", "two", "three"].map {|n| puts n.upcase }

It’s a common learner mistake to expect the result to be
`["ONE", "TWO", "THREE"]`. In fact, it’s `[nil, nil, nil]`. Each time
through the block, the block evaluates to the return value of
`puts`—namely, `nil`.

If every statement reduces to a single object, then the principle must
apply to things you probably don’t usually think of in this way, such as
class definitions. Sure enough:

    >> class MyClass; end
    => nil

An empty class definition body evaluates to `nil`. A non-empty class
definition body evaluates to the last expression evaluated inside it:

    >> class AnotherClass
    >>   2 + 3
    >> end
    => 5

You can, if you want to, assign this value to a variable:

    >> x = class C; "Hi!"; end
    => "Hi!"
    >> puts x
    Hi!
    => nil

It’s kind of silly to do that, usually. But there’s one very common
idiom that uses this technique. Remember that inside a class body,
`self` is the class object itself:

    >> class Thing
    >>   self
    >> end
    => Thing

You’ll often see this fact used for the purpose of grabbing hold, in a
variable, of an object’s singleton class:

    >> t = Thing.new
    => #<Thing:0x18cf18>
    >> singleton_class_of_t = class << t; self; end
    => #<Class:#<Thing:0x18cf18>>

We go into the singleton class using the `class << t` construct,
evaluate `self`, and exit the class body. The result of this fishing
expedition is that we’ve landed the singleton class itself and saved it
to a variable. Now it’s possible to do things with the class that you
can’t do as long as it remains anonymous, such as calling `class_eval`
on it.

(Note that in Ruby 1.9.2 there’s a singleton\_class method, so the above
technique is probably going to start disappearing as more people move to
1.9.2 and higher versions.)

Most class bodies evaluate to `nil` because, typically, class
definitions end with a method definition—and method definitions always
evaluate to `nil`:

    >> def my_method
    >>   "Doesn't matter what I put here"
    >> end
    => nil

Of course, when you call the method it returns a string:

    >> my_method
    => "Doesn't matter what I put here"

But the method definition *itself* evaluates to `nil`.

Conditionals, including if statements and case statements, also always
evaluate to an object. This isn’t exactly an obscure point; after all,
the ultimate value of a conditional is often put to use.

    >> action = "stop"
    => "stop"
    >> message = if action == "stop" then "Bye!" else "Continue!" end
    => "Bye!"

There’s an interesting general rule, though: If no condition is true, or
no case matched, then an if statement or case statement always evaluates
to nil.

    >> if 3 > 5
    >>   "Universe is in trouble!"
    >> end
    => nil

    >> case 1 + 1
    >> when 3
    >>   "My world is upside-down!"
    >> end
    => nil

One place you’ll see this put to use is in templating situations where
someone wants to include something conditionally. Consider this erb
fragment:

    <%= "#{first} #{"#{middle} " if middle}#{last}" %>

The expression `"#{middle }" if middle` will evaluate to `nil` if
`middle` is `nil`. Interpolating `nil` into a string is the same as
interpolating an empty string, so that whole part of the larger string
will simply be an empty string. If `middle` isn’t `nil`, then `middle`
plus a space will be interpolated into the larger string. Mind you, if
you actually use this technique, people might accuse you of having
overly clever or “cute” code—and they may be right! But even if you
don’t use it in real code, it’s an instructive example.

So even though not everything is an object in Ruby, an object is never
very far away. Every statement eventually reduces to a single object.
You might say that almost everything is an object—and everything is
almost an object. Much of the time, the objects produced by control flow
statements, class and method definitions, and keyword statements are
ignored. But when you want or need them, they’re available. And
exploring what statements evaluate to can teach you a lot about what
Ruby is “thinking”.

***Post supported by [Zencoder Inc.](http://zencoder.com/)*:** Zencoder
does [video encoding](http://zencoder.com/), as a service, in the cloud.
Hook up to their API, and within minutes, you’ll be ready to process
video, whether it’s 10,000 videos or just 10. Zencoder is highly
optimized for speed, uses the best compression technology around, and
handles hundreds of video/audio formats (including obscure and corrupt
files). Also check out their open-source [HTML5 video
player](http://videojs.com/) – [VideoJS](http://videojs.com/).

***Do read* these awesome Guest Posts:**

-   [So… you’re new to
    Ruby!](http://rubylearning.com/blog/2010/09/24/so-youre-new-to-ruby/)
-   [Incorporating Web APIs to spark computer programming
    exercises](http://rubylearning.com/blog/2010/09/23/incorporating-web-apis-to-spark-computer-programming-exercises/)
-   [14 Ways To Have Fun Coding
    Ruby](http://rubylearning.com/blog/2010/09/22/14-ways-to-have-fun-coding-ruby/)
-   [Writing modular web applications with
    Rack](http://rubylearning.com/blog/2010/09/21/writing-modular-web-applications-with-rack/)
-   [How to Learn Ruby (or any programming
    language)](http://rubylearning.com/blog/2010/09/20/how-to-learn-ruby-or-any-programming-language/)

