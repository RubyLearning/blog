---
draft: false
title: Does Ruby Have Too Many Equality Tests?
date: 2010-11-17
author: Eric Anderson
categories:
- Beginners
- Ruby
- Ruby Masters
layout: post
permalink: /2010/11/17/does-ruby-have-too-many-equality-tests/
tags:
- programming
- Ruby Equality Tests
- ruby programming
---

## Does Ruby Have Too Many Equality Tests?

This guest post is by **Eric Anderson**, who develops web-based
applications for small businesses though his company [Pixelware,
LLC](http://pixelwareinc.com/resume.html) in Atlanta, GA. He also runs
[SaveYourCall.com](http://www.saveyourcall.com/) which allows people to
record phone calls from any phone without the need for any complicated
hardware.

![Eric Anderson](http://rubylearning.com/images/eric-anderson.jpg) You
probably started using `==` out of habit from other languages. It seems to
work and that seems good enough. But then you might start seeing `===`,
`=~`, `eql?` and `equal?` and wonder what the heck those are about? How are
they different and why does Ruby make you insane with so many equality
tests?

This article will explain the purpose of each test. It will help you
understand the intention of the test by looking at how the standard
library defines them. Once you understand the intent you will know how
to define that method in your own objects and what you should expect
when you are using standard library and 3rd party objects.

## `==`

`==` is your main equality test. Most of the time when you want to test
for equality this is what you will use. The intent of this method is “do
the objects have the same value regardless of class?” The following are
a few examples that will illustrate the behavior:

    a = Object.new
    a == a                             # true
    a == Object.new                    # false
    "foo"           == "foo"           # true
    "foo".object_id == "foo".object_id # false
    1 == 1.0                           # true
    1.class == 1.0.class               # false

The first two examples show the default behavior when comparing
instances of class `Object`. If the two objects are the same object in
memory it will return `true`. But if it is compared to another instance of
`Object` it will return `false`.

The next example compares two `String` instances with the same value. As
you can see when compared they return true even though they are
different objects in memory (as noted by the fact that their object id
returns `false` when compared). So even though the default behavior is
fairly strict subclasses should open up if they are able to decide the
objects have the same value.

The final example shows us the value comparison carries across different
classes. `1` is a `Fixnum` while `1.0` is a `Float`. But since they still have
the same value they are considered equal. This means when implementing
your own objects you should ignore the class of the other objects and
concentrate solely on the value of the objects.

Also when implementing `==` it is important to ensure the equality test is
reversible. `a == b` should return the same value as `b == a`.

One last note on `==`. You may occasionally see the `!=` operator. `!=` is not
a method you can define but a language feature. It will call your `==`
method and then return the opposite boolean value returned by `==`.

## `eql?`

`eql?` operates slightly more restrictive than `==.` Like `==` it is concerned
with the value of the object and not concerned if two objects are the
same instance. But unlike `==,` `eql?` does care about the class. Let’s look
at some examples:

    a = Object.new
    a.eql? a                             # true
    a.eql? Object.new                    # false
    "foo".eql? "foo"                     # true
    "foo".object_id == "foo".object_id   # false
    1.eql? 1.0                           # false

As you can see eql? starts out like ==, but when comparing the Fixnum to
the Float the result is false even though they have the same value. An
object is data plus behavior. Since == is intended to be ignorant of
class it is basically ignoring differences in behavior and only
concerned with differences in data. By using eql? you are indicating you
not only care that the value is the same but that the behavior of the
object is the same.

## `equal?`

`equal?` is the most strict of any equality tests. It will test to ensure
that the objects being compared are the same instances in memory. This
means the value of their object id will be same as they are literally
two pointers to the same instance.

    a = Object.new
    a.equal? a                           # true
    a.equal? Object.new                  # false
    "foo".equal? "foo"                   # false
    "foo".object_id == "foo".object_id   # false
    1.equal? 1                           # true
    1.object_id == 1.object_id           # true

So our default behavior is like the other equality tests but the
similarities end there. When you compare two difference instances of
`String` with the same value you get `false`. This is because despite having
the same value they are two different instances in memory.

The last example is an interesting quirk of Ruby. For performance and
memory optimization reasons there is only once instance of each value of
`Fixnum`. This means that even though we created our instances separately
they have the same object id and therefore `equal?` will return `true` when
compared.

Ruby requires `equal?` conform to this intent. You should not override
this method in your subclasses. Doing so might cause unpredictable
behavior by the Ruby runtime.

## `===`

`===` can allow you to write code in a very concise and readable way. `===`
is a way you can compare two objects using a single operator but having
the intent change depending on the context of the comparison. Lets give
some examples:

    a = Object.new
    a === a                             # true
    a === Object.new                    # false
    "foo"           === "foo"           # true
    "foo".object_id == "foo".object_id  # false
    1 === 1.0                           # true
    1.class == 1.0.class                # false
    Fixnum  === 1                       # true
    (1..10) === 5                       # true
    /o/ === 'foo'                       # true

As we can see this starts out looking a LOT like `==`. We can see that the
comparison is concerned with value not the instance in memory. It also
doesn’t care about class. The last three examples really show this
method’s uniqueness. When comparing a class with an instance of that
class we get `true`. When comparing a range with a value in that range we
get `true`. When comparing a `regexp` with a string it returns `true` if the
`regexp` matches the string. Why does `Class`, `Range` and `Regexp` define `===`
this way? Because the `===` operator is used in the case control flow
statement. Review the following example:

    case obj
      when "foo"          then ...
      when Fixnum, Float  then ...
      when 1..10          then ...
      when /o/            then ...
    end

This is the magic of `===`. It lets the intent change depending on the
context of the comparison. So sometimes you want a simple value
comparison like `==`. Other times you want to know if an object is an
instance of the given class. Other times you want to know if a value is
in a range and sometimes you want to know if a regexp matches an object.
You have one operator the case statement can use that works for all
these types of comparisons.

It is important to note that just because `a === b`, this does not imply `b
=== a`. The order of the comparison is very important. For example `1 ===
Fixnum` will return `false` while `Fixnum === 1` returns `true`.

## `=~`

`=~` is a pretty special equality operator. `Object` defines it to always
return `false` (even if comparing two objects that are the same instance).
Where this operator gets interesting is with the `Regexp` class. Take a
look at the following examples:

    a = Object.new
    a =~ a                                          # false
    /o/   =~ 'foo'                                  # true
    'foo' =~ /o/                                    # true
    Mime::Type.new('application/xml') =~ 'text/xml' # true

`Regexp` defines `=~` as alias to the match method. This provides the
familiar `=~` syntax found in languages like Perl while still providing a
fully object-oriented regexp library. Note that `String` defines `=~` to
reverse the operands. So `'foo` =~ obj` will execute `obj =~ ‘foo’`. This
allows `=~` to be reversible when comparing a `String` even though `=~` is
not generally reversible.

`Regexp` is the primary place `=~` is used but the last example shows where
`=~` is defined by a class in the Rails framework to allow mime type
aliases to match a specific mime type object.

Like the `==` method there is an inverse of `=~` which is a language
feature and not a method that can be overridden. So if you see `!~` the
`=~` method will be called then the inverse of the result will be
returned.

## Conclusion

So does Ruby have too many equality tests? I think not! `==` obviously is
the work horse equality test. But the case statement would not be nearly
as elegant without `===`. Testing a regexp would not be nearly as concise
without `=~`. `==` is great most of the time but sometimes it is too broad.
`eql?` and `equal?` are great way to be more precise.

When creating your own classes try to make sure that these methods are
conforming to their intent and not just inheriting the default behavior
of `Object`. This can often make your API much more elegant.

*I hope you found this article valuable. Feel free to ask questions and
give feedback in the comments section of this post. Thanks!*

***Do also read* these awesome Guest Posts:**

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

Also check out the [free and paid Ruby-related
eBooks](http://rubylearning.com/blog/ebooks/) from RubyLearning.
