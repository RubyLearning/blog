---
draft: false
title: Little Known Ways to Ruby Mastery by Josh Susser
date: 2009-01-06
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/satishtalim/about
categories:
- Beginners
- Interview
- Ruby
- Ruby Masters
layout: post
permalink: /2009/01/06/little-known-ways-to-ruby-mastery-by-josh-susser/
tags:
- interviews
- Josh Susser
- Little Known Ways to Ruby Mastery
- Ruby
- Ruby Beginners' Questions
- The Ruby Programming Language
---
## A weekly series from the Ruby Masters

Welcome to the next installment of the weekly interview series on the RL
blog – “**Path to Ruby Mastery**” – by top trainers and developers in
the **Ruby community**, from across the globe. The interview series will
provide insight and commentary from these notable Ruby trainers and
developers, with the goal of facilitating and providing answers to the
questions **Ruby beginners** face. We welcome your suggestions for
interviewees and questions. Look for a new post every Tuesday!

![Josh Susser,
USA](http://rubylearning.com/images/josh.jpg "Josh Susser, USA")

This week, we’re happy to have **Josh Susser** from USA.

**Satish Talim\>\>** Welcome, Josh and thanks for taking out time to
share your thoughts. For the benefit of the readers, could you tell us
something about your self?

**Josh\>\>** I’ve been doing object-oriented programming since the
mid-80s, back when hardly anyone had heard the term let alone understood
what it was. I’ve worked on a wide range of object technologies, from
Smalltalk applications and virtual machine code to distributed component
systems to defining Sun’s JavaCard virtual machine. Now I’m a senior
developer at [Pivotal Labs](http://pivotallabs.com/), one of the
premiere Rails consulting shops and a seriously awesome place to work.
I’m probably best known in the Ruby community for my blog, [has\_many
:through](http://blog.hasmanythrough.com/) and the occasional conference
presentation.

I almost started using Ruby in 2002, but I couldn’t find much
documentation for it on short notice so I ended up doing the project
with a combination of Perl and PHP instead. It took until 2005 for me,
to really discover Ruby and what it was about. Like so many, I finally
came to Ruby because of Rails, and then kicked myself I hadn’t started
using it earlier. I found Ruby very easy to pick up; I had done
Smalltalk development for years and some functional stuff here and
there, so the basics of the language felt very familiar. But don’t worry
if you don’t have that kind of background; Ruby is a very accessible
language for anyone willing to make the effort.

**Dennis Theisen, Germany\>\>** Could you name three features of Ruby
that you like the most, as compared to other languages? Why?

**Josh\>\>** First off, Ruby is fully object-oriented, as opposed to
Java, C++ and Objective-C which are hybrid languages. In hybrid
languages programs can create data values that aren’t objects but are
some other kind of primitive data type. But in Ruby, every data value
you can name is a first-class object. This makes programs more
consistent and gives you smaller code since you can use polymorphism
everywhere.

Next, Ruby is dynamically typed, also known as “duck typed”, as opposed
to being statically typed. This doesn’t mean Ruby is not strongly typed.
It just means that types are enforced at runtime dynamically (via
dynamic binding and method lookup) rather than by the compiler. Java on
the other hand is statically typed, which is great if you want to be
able to prove your programs are correct, but nearly useless in most
real-world programming. It just means you spend a lot of time making the
compiler happy instead of getting your features working.

Finally, Ruby has a rich set of control structures and exception
handling. The designers of Smalltalk decided that all control structures
must be expressed as message sends. This made for very ugly if-then-else
(actually ifTrue:ifFalse:) chains, and no one has ever managed to create
a useful case statement. Matz rejected this ideological extremism to
include special syntax for a number of control structures. As a result
the code is smaller and much easier to understand. This is a big part of
why I like Ruby better than Smalltalk.

**Willian Molinari, Brazil\>\>** What has been your biggest challenge
while working with Ruby?

**Josh\>\>** As much as I like TextMate, I’m frustrated by the lack of a
really good IDE for Ruby. There have been some decent attempts to
integrate Ruby into products like IntelliJ and NetBeans, but so far
nothing has even reached the point where Smalltalk was 20 years ago.
Some of that is due to the extreme dynamism of the Ruby language, and
how meta-programmable it is. But whatever the cause, I think we should
be able to do better.

The other challenging thing about Ruby is that it doesn’t have a major
corporate sponsor. Engine Yard, bless their hacker hearts, are doing as
much as they can to support Ruby and its ecosystem. But languages like
PHP and Python didn’t really become successful until they got a
corporate sponsor who could afford to support development of the
language and system libraries. It’s a testament to Ruby that it’s come
so far without a Yahoo or Google to throw a lot of money and people at
it. But that still leaves Ruby with some rough spots that are going to
need to be smoothed over before it can live up to its potential.

**Jerry Anning, USA\>\>** What best practices are most important for a
new Ruby programmer to learn and understand?

**Josh\>\>** I’m a big fan of XP so I’d generally encourage developers
to adopt those practices. But specifically, TDD (Test Driven
Development) is important for Ruby development. Ruby is a dynamically
typed language, which means you don’t have a compiler to help you find
type errors. In practice, type errors aren’t all that common, but if you
want to be able to have confidence that your code is doing what you
expect, TDD is the best way to get there. One of the great things about
Ruby development is the ease of doing TDD. There are a number of mature
and well-supported test frameworks to choose among, and good integration
with the popular IDEs and code editors.

Pair programming is also a good practice to adopt, especially when
learning a new language. If you can find a mentor to pair with that’s
great, but pairing with someone who is also learning Ruby is a good way
to go too.

**Jerry Anning, USA\>\>** Can you recommend things to study after
learning Core Ruby, including different frameworks, gems and external
libraries?

**Josh\>\>** This question seems to be based on the assumption that you
can go off and learn the Ruby language, then some add-ons, then do
something with it. I think that’s the backwards way to go at things. I’d
suggest finding a project that interests you and figuring out how to use
Ruby to do that project. That should naturally suggest other
technologies, libraries, frameworks, etc. You can even jump in on an
existing open-source project, and that way you won’t have to think to
hard about making those initial technology choices. My point is that
learning in a vacuum is the worst way to learn. Learning by doing is
more effective and also more satisfying.

That said, there are probably some good foundation libraries you’ll want
to be familiar with. Learn the three major testing frameworks:
test/unit, RSpec and Shoulda. Also get familiar with mocking libraries
like RR and Mocha. Beyond that, most of what you’ll care about is going
to be domain-specific, so there isn’t much point in answering such a
generic question with likely irrelevant recommendations.

As for Ruby itself, there is a lot worth mastering in the Core and
Standard Libraries (stdlib). The most high-leverage classes to learn
about are String, Array and Hash, as well as the Enumerable mixin. File
and IO are pretty useful too. Study and understand those classes and
you’ll be well on your way to Ruby mastery.

**Satish Talim\>\>** Most beginners in Ruby, would like to contribute
their time, skills and expertise to a project but invariably are unaware
of where and how to do so. Could you suggest some?

**Josh\>\>** First off, get an account on [GitHub](http://github.com/).
(If you haven’t learned git yet, get going on that too – it’s the future
for open source SCM.) Then do some exploring around the various projects
and see where you think you can jump in and contribute something. Pick a
project that is currently under development and has an active community.
You’ll have enough going on that you don’t want to be championing a
project just yet.

**Victor Goff, USA\>\>** How do you see the market for Ruby Programmers
in the work place, and do you see it as primarily tied to Rails and Web
related work? Do you see trends in administration or other work?
Whatâ€™s the future for Ruby?

**Josh\>\>** From what I’ve seen over the past year, it’s a very good
market for Ruby developers. Most of the Ruby jobs are about building
Rails applications or web-related things, but not entirely. I know quite
a few developers building all sorts of things in Ruby that aren’t web
apps. But for the moment Ruby is best suited for web development, and
that’s probably going to be true for another year or two. Once we see a
faster VM and better library coverage, I think you’ll see Ruby being
used in a wide variety of applications. And if you want to build desktop
applications, you should watch out for MacRuby.

**Satish Talim\>\>** What can / should job candidates (for Ruby) do to
distinguish themselves from their competition?\
**Note**: The candidate has done his/her homework on the company that
they are interviewing with. The candidate understands what they’re
looking for, and the candidate is prepared to show them that he/she fits
the bill, based on the candidate’s skills and experience. What else can
the candidate do, to set themselves apart from other equally
well-qualified and well-prepared candidates?

**Josh\>\>** This is getting to be a cliche, but contributing to open
source projects is one of the best ways to show your stuff. You can
demonstrate your technical proficiency, as well as your ability to work
in a team, make decisions as a group, resolve conflicts, and deal with
rejection (a big part of open source work!).

The other thing I’d suggest is to keep a technical blog. Contributing
code to a project is great, but that doesn’t show the whole picture of
you. If you keep a blog you can use it to discuss your contributions,
document issues, and sound off about things you care about. This is a
great way to let employers learn about you, and also demonstrates your
communication skills (an essential requirement for almost any job).

**Satish Talim\>\>** Do you have any other suggestions for these
participants (would-be Ruby developers)?

**Josh\>\>** Ruby is a superb language. It is fully object-oriented, has
functional language features like lambdas and higher-order functions, is
very easy to meta-program, and has an accessible syntax and flexible
structure. But Matz didn’t invent all those things himself. In fact Ruby
is a synthesis of some of the most powerful ideas in computer science.
If you want to really appreciate Ruby, you should take some time to
study up on the systems from which it is derived. I would start with
Smalltalk (Squeak is a free, open source implementation), then read up
on Scheme or some other flavor of Lisp. If you haven’t used Perl, take a
look at it just to see how much nicer Ruby’s syntax is.

And finally, get out and meet other Rubyists. A big part of what makes
Ruby awesome is the community of people who use and contribute to it. Go
to a local meetup or a conference and get connected to the community.

**Satish Talim\>\>** Thanks Josh for sharing your views with the
RubyLearning participants.

On 13th Jan. we talk to **Thibaut Barrere** from France.

***Disclaimer:***\
*The opinions expressed are those of Josh Susser and do not necessarily
reflect those of **[www.RubyLearning.com](http://rubylearning.com/)**.*

**The Path to Ruby Mastery Series (So Far)**:

-   #1: [Jamie van Dyke](/blog/2008/09/23/little-known-ways-to-ruby-mastery-by-jamie-van-dyke/)
-   #2: [James Edward Gray II](/blog/2008/09/30/little-known-ways-to-ruby-mastery-by-james-edward-gray-ii/)
-   #3: [Dr Nic Williams](/blog/2008/10/07/little-known-ways-to-ruby-mastery-by-dr-nic-williams/)
-   #4: [Stuart Halloway](/blog/2008/10/14/little-known-ways-to-ruby-mastery-by-stuart-halloway/)
-   #5: [Jay Fields](/blog/2008/10/21/little-known-ways-to-ruby-mastery-by-jay-fields/)
-   #6: [Chris O’Sullivan](/blog/2008/10/28/little-known-ways-to-ruby-mastery-by-chris-osullivan/)
-   #7: [Guy Naor](/blog/2008/11/04/little-known-ways-to-ruby-mastery-by-guy-naor/)
-   #8: [Jonathan Conway](/blog/2008/11/11/little-known-ways-to-ruby-mastery-by-jonathan-conway/)
-   #9: [Ian Dees](/blog/2008/11/18/little-known-ways-to-ruby-mastery-by-ian-dees/)
-   #10: [Bruce Tate](/blog/2008/11/25/little-known-ways-to-ruby-mastery-by-bruce-tate/)
-   #11: [Ezra Zygmuntowicz](/blog/2008/12/02/little-known-ways-to-ruby-mastery-by-ezra-zygmuntowicz/)
-   #12: [Chris Matthieu](/blog/2008/12/09/little-known-ways-to-ruby-mastery-by-chris-matthieu/)
-   #13: [Peter Cooper](/blog/2008/12/16/little-known-ways-to-ruby-mastery-by-peter-cooper/)
-   #14: [Yehuda Katz](/blog/2008/12/23/little-known-ways-to-ruby-mastery-by-yehuda-katz/)
-   #15: [Ilya Grigorik](/blog/2008/12/30/little-known-ways-to-ruby-mastery-by-ilya-grigorik/)
