---
draft: false
title: So, you're new to Ruby!
date: 2010-09-24
author: Julio Javier Cicchelli
categories:
- beginners
- ruby
- ruby masters
layout: post
permalink: /2010/09/24/so-youre-new-to-ruby/
tags:
- javier cicchelli
- programming
- ruby
---

This guest post is contributed by **[Javier
Cicchelli](http://twitter.com/monsieur_rock)**, a Software Engineer at
[Rock & Code](http://rock-n-code.com), the Software and Marketing
communications shop that rocks! Currently, they are doing their dirty
deeds and conducting their high voltage operations in the (in)famous Red
Light District in Amsterdam, The Netherlands. Some four years ago, he
started developing all the symptoms of a peculiar case of programmer's
schizophrenia. It all happened when<!--more--> he got a copy of the first
edition of ["Agile Web Development with Ruby on
Rails"](http://pragprog.com/titles/rails4/agile-web-development-with-rails) by
[Dave Thomas](http://twitter.com/pragdave) and [David Heinemeier
Hansson](http://twitter.com/dhh). Because of this book, he began spending a lot
of his nights hacking with this amazing new technology.  Back then, he was
using C\# and VB.NET at work and at some point, he simply started feeling
somehow uncomfortable with it. Indeed, he was quite disappointed with the way
the .NET framework and its languages was evolving. So in order to vent out his
frustration, he unconsciously turned to the only relief he had:
[Ruby](http://ruby-lang.org). Indeed, the more vexed he got with .NET, the more
he was getting into Ruby. At that point, he discovered the vibrant Ruby
community in the Ranstad region. An year ago, he got enough courage to quit his
daily job and found his company, [Rock & Code](http://rock-n-code.com). He did
so, determined to use all those new technologies available and simply rock
development to the top.

![Julio Javier
Cicchelli](http://www.rubylearning.com/images/jjcicchelli.jpg)

## So... you're new to Ruby!

Now that you know a bit more about me, let's get down to business and dive in.
First of all, welcome to Ruby! There might be multiple reasons why you are
reading this entry; you might want to get your hands dirty with Ruby, you could
be just curious as to what this whole Ruby thing is all about, or you might be
simply bored with the rest of the technologies out there and you are in a
search for a new technological medicine. The good news is that if you get
hooked on Ruby and you decide to explore it further, there are plenty of useful
docs, tons of blog entries and numerous nice fellas that can help you along the
way. I have been there, I have done that. In addition, every single day, I
learn something new by reading Ruby-related books and blog posts and by
spending some time talking with fellow rubyists on mailing lists, IRC and
Twitter. In order to add certain value to my article, I will attempt to cover
the basic stepping stones for Ruby beginners.

## What did I get myself into?

Before going any further, you should be warned what you are about to
mess with.

In a nutshell, Ruby is an extremely high-level programming language
created in Japan by [Yukihiro "Matz"
Matsumoto](http://twitter.com/yukihiro_matz) almost 20 years ago. It is
heavily influenced by some of the most popular Scripting, Object
Oriented, and Functional languages. It is built on C and its utter goal
is to make programming fun again by obfuscating its vast complexity into
natural syntactic sugar for the masses. Devised mainly as a
Object-Oriented language, Ruby considers (almost) everything as objects
that can have attributes and methods. Even though it might seem
restrictive as it supports simple inheritance only, Ruby considers that
modules containing methods could be plugged-in into classes or objects
and, therefore, it could use these methods as if they were its own. This
is a concept known as "Mixin". Furthermore, this language provides you
with a great deal of flexibility, which means you are able to alter any
class, module or object on-the-fly by adding, modifying or removing
functionality dynamically. In addition, its support for blocks gives
greater flexibility and expressiveness to your methods in a functional
fashion. Moreover, it does not require you to specify the types you are
going to use in your code in advance. Nor does it require you to handle
the memory allocation yourself. Ruby is not the kind of language that
limits you and allows you to write your code in just one way. In fact,
you can write your code in either an imperative, a procedural, an
object-oriented or even a functional fashion.

* * * * *

New to Ruby? Join our online Core Ruby course. Read details
[here](http://rubylearning.com/blog/2010/09/06/new-course-ruby-programming-101/).

* * * * *

Even though Ruby is mainly used for creating web applications due to the
widespread popularity of [Ruby on Rails](http://www.rubyonrails.org), it
is actually a general-purpose programming language and it can be used in
almost any kind of industry. Little by little, Ruby has been gaining a
lot of momentum and it has been slowly but surely incorporated into the
enterprise world. The fact that it makes developers happy is reflected
in the way software has been produced. Indeed, if every member of a
development team is able to quickly write simple code that is close to
the natural language and it describes the domain of the problem, this
will certainly have positive impact on the way this code is read,
understood and maintained. Any beginner with basic notions of
Object-Oriented programming should be able to catch up quickly,
regardless of the kind of project.

Logically, there is always a price to pay and this is no exception:
interpreted languages are usually much slower than their compiled
counterparts and making developers happy has a direct impact on the
overall performance of the interpreter. In addition, the way the
interpreter uses multi-core processors, handles threading, and
implements the memory garbage collector strategy usually raise concerns
among some developers and industries which requires extremely high
processing capabilities. Another problem is the lack of an established
GUI that would allow developers to create cross-platform applications
for either desktop, server and mobile environments. As you can imagine,
these disadvantages are usual referred to when somebody starts the
typical war of words "Ruby vs. (fill in the blanks with your language of
choice)" on Hacker News or any similar site. Evidently, this somehow
undermines the importance of Ruby as an important player in the field of
Programming Languages of the decade.

Because of the Open Source nature of Ruby, a handful of great hackers
and a few courageous people have forked the MRI (the de-facto Matz Ruby
Interpreter) in order to propose their own solutions to the
aforementioned cons. In the meantime, they have added some real value
for developers of a certain niche platform. For example,
[REE](http://www.rubyenterpriseedition.com/) optimizes the garbage
collector of the MRI for web applications and
[Rubinius](http://rubini.us) is a reimplementation of the MRI as a
virtual machine a la Smalltalk, which aims at solving most of the known
disadvantages of Ruby. Still other projects such as
[JRuby](http://jruby.org), [IronRuby](http://ironruby.net) and
[MacRuby](http://www.macruby.org) emphasize on a really tight
integration with the Java, .NET and the OSX platforms.

Still, Ruby has a really friendly and thriving community behind its back
that is systematically pushing its development and evolution forward. If
you ask me, Ruby certainly has a couple of aces up its sleeve.

## How to install Ruby on my machine?

Although some Operating Systems have some version of the MRI interpreter
already installed, I would highly recommend that you use
[RVM](http://rvm.beginrescueend.com) to install, administer, and use
multiple Ruby interpreters and set of gems very easily. This utility,
written by [Wayne E. Seguin](http://twitter.com/wayneeseguin), aims at
addressing the most common, yet painful issues of developing, testing
,and deploying on Ruby, especially if you are looking forward to
supporting different versions of Ruby. It does not really matter if you
are working on your development or production environment. The RVM
resolves complex issues regarding different versions seamlessly and it
provides you with a simple and concise API that does not interfere with
your tasks at hand. Definitely, this is a tool worth studying carefully
because it will surely save you lots of work and time. It is also good
for your mental health.

Unfortunately, RVM is not supported out-of-the-box on Windows
environments and as far as I know, I do not think there is any
alternative to this environment so you should stick to the [Ruby
Installer](http://rubyinstaller.org) executables for the moment, which
will install the MRI on your machine. Unfortunately, it will not give
you the great deal of functionality described above. If any of you knows
of a similar solution for Windows environments, please write a comment
below. Lots of people will surely be interested in this.

Even though it is not specifically related to Ruby,
[Git](http://git-scm.com) is definitely one of the most powerful tools
at your disposal today. It is a quick, efficient, and easy-to-use
distributed version control system that allows you to manage the changes
of your code over time. Basically, you have a local copy of your project
with the history of your changes and you can import those changes into
another repository as branches that can be merged with the local
content. Git was created for non-linear development, so it allows you to
create convenient branches, produce quick merges, and visualize the
changes over time. Unlike RVM, Git is very well supported by every major
environment out there so rejoice!

## Ok... now what?

Probably it is the most common question you may ask to yourself right
after installing on your machine whatever versions of the Ruby
interpreter you have chosen.

Whether you're an adventurous developer or not, I highly recommend that
you read the ["Why's (poignant) Guide to
Ruby"](http://mislav.uniqpath.com/poignant-guide/book/) by the now
missing in action [Why the Lucky
Stiff](http://www.smashingmagazine.com/2010/05/15/why-a-tale-of-a-post-modern-genius/).
This is the most unorthodox, yet extremely didactic programming book I
have ever had the pleasure to read so far. No matter how experienced you
are in the art of coding, read it and enjoy! This book is the very
embodiment of the spirit of the Ruby language and its community. Simply
awesome. Of course, there are hundreds of books about Ruby out there,
mostly for beginners, but really, take my piece of advice and try this
one first. You will not regret it!

One of the best things you can do while reading either a book or a post
blog related to Ruby, is to test the code on the
[IRB](http://www.rubyinside.com/irb-lets-bone-up-on-the-interactive-ruby-shell-1771.html),
the interactive Ruby shell. This tool (or its equivalent on the
different versions of the interpreter) executes every piece of code you
insert in it, one line at the time. Believe me, trying every code
example you may find in your way would really give you a better
understanding of how Ruby works. On top of it, it is real fun!

## What can I do with Ruby?

Although the main use of Ruby is focused on web development due to the
popularity of the Ruby on Rails framework, you are able to easily create
almost all the types of software for work and have tons of fun in the
mean time. From tiny libraries and
[DSLs](http://www.infoq.com/news/2007/06/dsl-or-not) to complex
frameworks and applications, Ruby is a general-purpose programming
language that does not get in the way between your requirements and the
actual implementations.

In any case, the best way to understand what you can do with this
language is by adopting an empirical approach. Experiencing the pros and
cons of the Ruby language yourself would allow you to become an expert
in it.

## Which way to go from here?

If there is something that Ruby normally offers to its developers, this
is a whole range of choices, lots of choices... sometimes too many
choices. Apart from the choices you may have to make in order to settle
on with a text editor, some databases engines, a particular web server,
etc., Ruby does not have just one version of the interpreter. Nor does
it provide only one way of doing things. As you may have already
guessed, neither do the developers out there.

There are many techniques, resources, and approaches to write Ruby code
and since most of the Ruby code is mostly open source and it is
available on [Github](http://github.com) (this is where Git comes
along!), you can take a look at this treasure trove and learn a lot from
it. Just remember: do not be overwhelmed by the huge number of choices
that awaits you.

## Should I write tests all the time?

Ruby has certainly taken testing back from obscurity and it has
re-introduced it to the forefront of development. This is the time I
confessed something: before learning Ruby, testing was the task that I
was always trying to avoid because writing tests on .NET using NUnit is
not the most exciting task in the world. Nonetheless, testing in Ruby
using any library, regardless of whether you are using [Test
Unit](http://ruby-doc.org/stdlib/libdoc/test/unit/rdoc/),
[Rspec](http://%20rspec.info), [Cucumber](http://cukes.info) or else is
not an easy task either. Usually, it takes a lot of time and quite a
substantial experience to learn to write really good tests. It is
certainly an overhead in your development. So, if you plan to play with
the language, develop proofs of concept, and try out code, I really do
not recommend that you dive into testing right away. Take your time to
learn the language first. When you start writing your own libraries or
collaborate on somebody else's project, then you should take a look at
the existing testing libraries, make an educated choice, and be really
patient.

In any case, you should realize that Testing is really important. You
should always ensure that your code verifies and validates both inputs
and outputs, fails when it has to fail, and works when it has to work.
Indirectly, testing is a form of documenting your code, because it
basically shows how your code should work in a somehow realistic
environment. In my opinion, testing is a long-term investment in your
code for you and the people involved in your project. If you are really
interested in how testing can help you structure the way to develop
Software, then you should take a look at the
[TDD](http://en.wikipedia.org/wiki/Test-driven_development) and
[BDD](http://en.wikipedia.org/wiki/Behavior_Driven_Development)
techniques.

I think that my explanations have given you enough food for thought. Now
you are prepared to start your quest in the land of the Rubies. Fear
not! Be confident and ready to experiment. You will not regret it. I
promise you will have lots of fun sticking around! My final piece of
advice to you is that you should really know your tools very well, no
matter what kind of a text editor, database, framework, library, DSL or
anything else you choose to work with.

*Thanks a lot for the attention, boys and girls! I hope you enjoyed
reading this post as much as I enjoyed writing it. I wish you good luck
in your Ruby adventure. Most probably, our paths will cross along the
way. If you have any further questions, please do not hesitate to post
them as comments here. In the meantime, stay tuned for the other great
blog entries of the Ruby Gurus series and enjoy learning Ruby on
RubyLearning!*

***Post supported by Blue Box Group*:** [Blue Box
Group](http://www.blueboxgrp.com/?utm_source=rubylearning&utm_medium=blog&utm_campaign=rubylearning)
is in the business of providing affordable [Rails
hosting](http://www.blueboxgrp.com/?utm_source=rubylearning&utm_medium=blog&utm_campaign=rubylearning)
solutions! They approach web hosting, virtual servers and dedicated
servers differently, treating each client as a partner and working
towards the common goal of success for their business. They have the
experience, talent and equipment to make your site a success!

***Do read* these awesome Guest Posts:**

-   [Incorporating Web APIs to spark computer programming
    exercises](http://rubylearning.com/blog/2010/09/23/incorporating-web-apis-to-spark-computer-programming-exercises/)
-   [14 Ways To Have Fun Coding
    Ruby](http://rubylearning.com/blog/2010/09/22/14-ways-to-have-fun-coding-ruby/)
-   [Writing modular web applications with
    Rack](http://rubylearning.com/blog/2010/09/21/writing-modular-web-applications-with-rack/)
-   [How to Learn Ruby (or any programming
    language)](http://rubylearning.com/blog/2010/09/20/how-to-learn-ruby-or-any-programming-language/)

