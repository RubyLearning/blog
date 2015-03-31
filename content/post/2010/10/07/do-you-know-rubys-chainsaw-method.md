---
draft: false
title: Do YOU know Ruby's "Chainsaw" method?
date: 2010-10-07
author: Paolo Perrotta
categories:
- beginners
- popular
- ruby
- ruby masters
layout: post
permalink: /2010/10/07/do-you-know-rubys-chainsaw-method/
tags:
- method_missing
- paolo perrotta
- programming
- ruby
- ruby beginners
- ruby for noobs
---
This guest post is contributed by **[Paolo
Perrotta](http://rubylearning.com/blog/2009/07/01/interview-author-paolo-perrotta/)**,
a freelance geek, currently coaching agile teams for a large phone
company. He also wrotes<!--more--> the [Metaprogramming Ruby
book](http://www.pragprog.com/titles/ppmetr/metaprogramming-ruby) for
the Prags. He lives in Northern Italy with his girlfriend and a cat. He
loves Ruby.

The `method_missing()` method is a wonderful tool for every Ruby
programmer. I love it. There, I said it!

![method\_missing](http://rubylearning.com/images/method_missing.jpg)\
method\_missing()

## Do YOU know Ruby's 'Chainsaw' method?

Some Rubyists [are
surprised](http://jakescruggs.blogspot.com/2010/08/ruby-kaigi-2010-day-2.html)
when I declare my love for `method_missing()`. They do have a point. As
far as tools go, `method_missing()` is a chainsaw: it's powerful, but
it's also potentially dangerous.

![Paolo
Perrotta](http://rubylearning.com/images/PaoloPerrotta.jpg "Paolo Perrotta")
In case you don't know about `method_missing()`, here is how it works.
Imagine that you're calling a method on a Ruby object. For example, you
call `duck.sing("Quacking in the Rain")`. Usually, at this point one of
two things happens: if `duck` has a `sing()` method that takes one
argument, then Ruby executes the method; if `duck` doesn't have that
method, then Ruby raises an error. But wait: there is a third
possibility. If `duck`doesn't have a method named `sing()`, but it does
have a method named `method_missing()`, then Ruby executes
`method_missing()` instead. Ruby also tells to `method_missing()` which
method you originally called, with arguments and all. Here is an
example:

You can say that `duck.sing()` and `duck.dance()` are [Ghost
Methods](http://gist.github.com/534776): they aren't defined anywhere,
but you can call them anyway.

That's what `method_missing() `does. The difficult part is deciding when
and how to use it. Let's see an example of Ghost Methods in action.

Imagine that you have an `InformationDesk` object with many complex
methods that provide some kind of tourist information or service:

To give a break to people working at the `InformationDesk`, you can wrap
the `InformationDesk` in a `DoNotDisturb` object:

`DoNotDisturb` forwards method calls to the wrapped `InformationDesk`,
unless it's lunchtime. During lunch breaks, `DoNotDisturb` responds to
calls by raising an exception -- unless you're calling `emergency()`,
that works at any hour. (If you think that two hours are too much for a
lunch, then you've probably never lived in Italy!)

The problem with the above code is that `DoNotDisturb` contains a lot of
look-alike methods. This is a form of duplication, and duplication
sucks. If a programmer adds methods to `InformationDesk`, she also needs
to remember to add matching methods to `DoNotDisturb`, most likely by
copy-pasting the existing look-alike methods and then modifying them.
One misstep in this procedure, and you have a brand new bug.

When I work with Java or C\#, I accept this kind of code duplication as
a fact of life. In Ruby, I can be more aggressive and replace all the
calls with a single `method_missing()`:

`DoNotDisturb` is now a [Dynamic Proxy](http://gist.github.com/535077):
it forwards each method call to its inner `InformationDesk`, and it also
wraps additional logic around each call. If you add methods to
`InformationDesk`, you needn't worry about `DoNotDisturb`: it will work
for the new methods without any change.

This kind of trickery is useful, but it does have a dark side. If you
abuse `method_missing()`, you can end up with code that's difficult to
read and maintain. I'm still intimidated by some of [the wildest
examples of
`method_missing()`](http://github.com/rails/rails/blob/277c799d58be4b3e0e885d7b3fd6d954facc111b/activerecord/lib/active_record/base.rb)
that abound the Ruby ecosystem. Even if you take care to keep your
`method_missing()`small and maintainable, Ghost Methods are still
inherently less explicit than regular methods. You can easily discover
the regular methods in a class by looking at the auto-generated
documentation, but you have to look at the source code (or the author's
documentation) to spot Ghost Methods.

Also, if you're not careful around `method_missing()`, sneaky bugs can
creep into your code. For example, an overly tolerant `method_missing()`
might accept a mistyped method call without flinching. Chainsaws are
meant to be handled with care!

So, what kind of tree should you use the` method_missing()` chainsaw on?
Here are my simple rules of thumb:

1.  I **use `method_missing()`to remove duplication**. A well placed
    `method_missing()` allows me to remove duplicated code at a level
    that wouldn't otherwise be possible.
2.  On the other hand, I usually **think twice about using
    `method_missing()` for cosmetic reasons**, like getting cool method
    names such as `find_by_name_and_address()`.
3.  I always try to **evaluate whether `method_missing()` is worth the
    extra reading effort**. I dislike duplicated code because it's hard
    to read and modify. If I replace that code with a `method_missing()`
    that's even harder to read and modify, then I've defeated
    `method_missing()`'s purpose.

It's a balancing act: with some experience you can strike the sweet spot
between shortness and clarity in your Ruby code. To do that, you'll
likely use the `method_missing()` chainsaw to cut out unnecessary
branches from your forest of methods.

There are many more neat tricks, caveats and interesting details around
`method_missing()`. In [Metaprogramming
Ruby](http://www.amazon.com/Metaprogramming-Ruby-Program-Like-Pros/dp/1934356476/ref=sr_1_1?ie=UTF8&s=books&qid=1284392039&sr=8-1),
I devoted most of the Methods chapter to it (you can check the first few
pages from that chapter
[here](http://media.pragprog.com/titles/ppmetr/methods.pdf)). You can
also find a lot of information on `method_missing()` on the Web,
including some [pretty crazy bug
reports](http://yehudakatz.com/2010/01/02/the-craziest-fing-bug-ive-ever-seen/).
With this information, and some experience, you'll be able to make up
your own mind about the pros and cons of `method_missing()`.

Me, I already made up my mind. Yes, I use `method_missing()` sparingly.
Yes, I keep it as short as I can. Yeah, I triple-check it for bugs... But
when the duplication begins to sting, I put on my evil grin and grab my
faithful chainsaw.

*Have **you** used `method_missing()` before? Why don't you share your
experiences with us? Let us know in the comments section of this post.
Thanks!*

***Post supported by [Tupalo.com](http://tupalo.com/)*:** Tupalo.com is
a privately-held internet startup located in Vienna, Austria. Their
social yellow-pages app is developed using Ruby on Rails and also uses
many of the other exciting tools like Cucumber, RSpec, Capistrano and
Puppet, Ruby developers came to appreciate.

***Do read* these awesome Guest Posts:**

-   [Gem Sawyer, Modern Day Ruby
    Warrior](http://rubylearning.com/blog/2010/10/06/gem-sawyer-modern-day-ruby-warrior/)
-   [An Introduction to Outside-in
    Development](http://rubylearning.com/blog/2010/10/05/outside-in-development/)
-   [Ruby
    Forensics](http://rubylearning.com/blog/2010/10/04/ruby-forensics/)
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

