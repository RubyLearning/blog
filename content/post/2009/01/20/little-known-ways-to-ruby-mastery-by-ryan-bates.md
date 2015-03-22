---
draft: false
title: Little Known Ways to Ruby Mastery by Ryan Bates
date: 2009-01-20
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/rubylearning
categories:
- Beginners
- Interview
- Ruby
- Ruby Masters
description:
- The Path to Ruby Mastery Interview Series by Ruby Masters, provides guidance to
  and answers questions confronting Ruby beginners from across the globe.
keywords:
- ruby for beginners,ruby beginners,ruby programming,ruby on rails blog,rails blog,rails
  tutorials,ruby beginners' questions,little known ways to ruby mastery,ruby masters,interviews,Ryan
  Bates,ruby,the ruby programming language
layout: post
permalink: /2009/01/20/little-known-ways-to-ruby-mastery-by-ryan-bates/
tags:
- interviews
- Little Known Ways to Ruby Mastery
- Ruby
- Ruby Beginners' Questions
- Ryan Bates
- The Ruby Programming Language
---
## A weekly series from the Ruby Masters

Welcome to the **last** installment of the weekly interview series on
the RL blog – “**Path to Ruby Mastery**” – by top trainers and
developers in the **Ruby community**, from across the globe. The
interview series will provide insight and commentary from these notable
Ruby trainers and developers, with the goal of facilitating and
providing answers to the questions **Ruby beginners** face.

![Ryan Bates,
USA](http://rubylearning.com/images/ryan_bates.jpg "Ryan Bates, USA")

This week, we’re happy to have **Ryan Bates** from USA.

**Satish Talim\>\>** Welcome, Ryan and thanks for taking out time to
share your thoughts. For the benefit of the readers, could you tell us
something about your self?

**Ryan\>\>** I started toying around with static HTML around 1996. A few
years later I created a website for my father’s company using this
little-known scripting language called WebDNA. As the site grew, I
ported it over to PHP, and then later to Rails. Needless to say, Rails
has been by far the most pleasant to work with.

I enjoy teaching, partly because I get to learn along with whoever I’m
helping by researching topics I might not have otherwise. While
beginning with Rails, I started answering questions on
[railsforum.com](http://railsforum.com/). Later I started
[Railscasts](http://railscasts.com/), the free Ruby on Rails screencast
series. I’m also working with the [Pragmatic
Programmers](http://www.pragprog.com/) on a couple screencast series:
[Everyday Active
Record](http://www.pragprog.com/screencasts/v-rbar/everyday-active-record)
and [Mastering Rails Forms]().

**Willian Molinari, Brazil\>\>** How should one go about learning the
Ruby language? What material (books, eBooks, online tutorials etc.)
would you recommend?

**Ryan\>\>** It depends on what your past experience is. If you are very
new to programming, I recommend reading [Learn to
Program](http://www.amazon.com/Learn-Program-Pragmatic-Programmers-Chris/dp/0976694042/).
Next up the tier is [Beginning Ruby: From Novice to
Professional](http://www.amazon.com/Beginning-Ruby-Novice-Professional/dp/1590597664/).
And then there’s the classic [Programming
Ruby](http://www.amazon.com/Programming-Ruby-Pragmatic-Programmers-Second/dp/0974514055/)
(also known as the Pickaxe book).

You may also want to [Try Ruby!](http://tryruby.hobix.com/), where you
can run Ruby commands interactively in your browser. If you enjoy
problem solving, check out [Ruby Quiz](http://rubyquiz.com/) and a
recent project of mine called [Ruby
Warrior](http://github.com/ryanb/ruby-warrior/tree/master) (still in
early development).

Finally, don’t only read books and work through examples. Find a real
world problem, and use Ruby to solve it. Ask questions to the community
if you can’t find the solution on your own.

**Dennis Theisen, Germany\>\>** Could you name three features of Ruby
that you like the most, as compared to other languages? Why?

**Ryan\>\>** Ruby has spoiled me. Since learning it, I’ve found it much
harder to work in other languages. These are the primary culprits.

-   Blocks. They make iterations a breeze and so much more!
-   Everything’s an object. Being able to call methods directly on
    integers, strings, arrays, etc. greatly simplifies the method
    interfaces.
-   Metaprogramming. Injecting behavior at runtime opens up so many
    possibilities.

**Jerry Anning, USA\>\>** Can you recommend things to study after
learning Core Ruby, including different frameworks, gems and external
libraries?

**Ryan\>\>** There’s obviously Rails which I recommend every Ruby
programmer try, even if you aren’t into web development. It handles Ruby
in a different way (both good and bad) than what you see in many other
projects. Also, go through the various methods in Active Support and
[extlib](http://github.com/sam/extlib/tree/master). Doing so will make
reading other projects that use these easier, and may improve the code
you write.

Also, if you haven’t already, I highly recommend signing up to
[GitHub](http://github.com/). It has made a huge impact on improving
myself as a programmer. Get involved with other programmers, read their
code, and share your own code.

**Jerry Anning, USA\>\>** What best practices are most important for a
new Ruby programmer to learn and understand?

**Ryan\>\>** There are three best practices which have made a world of
difference for me: testing, refactoring, and naming.

It took me a long time to grasp automated testing. The best advice I can
give is: don’t give up on it too soon. Start with a project that is easy
to test (maybe the models in a simple Rails app). Once you establish a
testing rhythm it gets easier, and the payoff is well worth it.

One of my favorite things about Ruby is how natural it feels to
refactor. If you don’t know what refactoring is, I recommend reading
[Martin Fowler’s
book](http://www.amazon.com/Refactoring-Improving-Existing-Addison-Wesley-Technology/dp/0201485672/)
on the subject. It’s not in Ruby, but the concepts he teaches still
apply. Also keep an eye out for the [Ruby
edition](http://www.amazon.com/Refactoring-Ruby-Addison-Wesley-Professional/dp/0321603508/)
of this book.

Finally, learning how to give proper names to variables, methods, and
classes will help make your code much more readable. Find concise yet
descriptive names and stay consistent with them across your application.
This does wonders towards improving the readability of the code.

**Victor Goff, USA\>\>** How do you see the market for Ruby Programmers
in the work place, and do you see it as primarily tied to Rails and Web
related work? Do you see trends in administration or other work? What’s
the future for Ruby?

**Ryan\>\>** I think web applications play a very significant role in
the future, not only in Ruby, but also in our society. Every day it
seems we are moving away from the desktop and more into the cloud. But
the buck doesn’t stop at Rails. I suspect Ruby will far outlive Rails in
the web development world as we see other innovative Ruby frameworks
come into play. Overall, I think Ruby has a very bright future in the
work place.

**Michael Uplawski, Germany\>\>** According to you, what is a
comfortable size of a Ruby/Rails-project? Why?

**Ryan\>\>** I find Rails scales very well for a wide range of project
sizes. I’ve worked with apps ranging from 3 models to 100 models and it
has handled both great. The most comfortable size is probably somewhere
around 10-40 models.

Where Rails is not as applicable are the two extremes. If you’re app is
very small (only a few pages, or mostly static content), there are other
languages and frameworks which are lighter weight and easier to deploy.
I don’t have much experience with gigantic enterprise apps, but I
imagine there’s a limit you could reach where Rails isn’t as practical
in how it organizes things. As Rails improves (especially with Rails 3),
it will become more and more applicable to these other types of
projects.

**Satish Talim\>\>** Thanks Ryan for sharing your views with the
RubyLearning participants.

***Disclaimer:***\
*The opinions expressed are those of Ryan Bates and do not necessarily
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
-   #16: [Josh Susser](/blog/2009/01/06/little-known-ways-to-ruby-mastery-by-josh-susser/)
-   #17: [Thibaut Barrere](/blog/2009/01/13/little-known-ways-to-ruby-mastery-by-thibaut-barrere/)

