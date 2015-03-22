---
draft: false
title: Little Known Ways to Ruby Mastery by Thibaut Barrere
date: 2009-01-13
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
description:
- The Path to Ruby Mastery Interview Series by Ruby Masters, provides guidance to
  and answers questions confronting Ruby beginners from across the globe.
keywords:
- ruby for beginners,ruby beginners,ruby programming,ruby on rails blog,rails blog,rails
  tutorials,ruby beginners' questions,little known ways to ruby mastery,ruby masters,interviews,Thibaut
  Barrere,ruby,the ruby programming language
layout: post
permalink: /2009/01/13/little-known-ways-to-ruby-mastery-by-thibaut-barrere/
---
### A weekly series from the Ruby Masters

Welcome to the next installment of the weekly interview series on the RL
blog – “**Path to Ruby Mastery**” – by top trainers and developers in
the **Ruby community**, from across the globe. The interview series will
provide insight and commentary from these notable Ruby trainers and
developers, with the goal of facilitating and providing answers to the
questions **Ruby beginners** face.

![Thibaut Barrere,
France](http://rubylearning.com/images/thibaut.jpg "Thibaut Barrere, France")

This week, we’re happy to have **Thibaut Barrere** from France.

**Satish Talim\>\>** Welcome, Thibaut and thanks for taking out time to
share your thoughts. For the benefit of the readers, could you tell us
something about your self?

**Thibaut\>\>** Hello! My name is Thibaut Barrere. I’m 31 years old, a
husband and dad who loves to create useful things (either in Ruby or
not). I became a freelancer in 2005, after working for software editors
and consulting companies.

I do my best to share useful thoughts and tools on the [Evolving
Worker](http://evolvingworker.com/) blog. I also write [Ruby tutorials
on my programming
blog](http://blog.logeek.fr/2008/3/31/data-visualization-with-ruby-and-rmagick-where-are-those-bikes).

I pretty much falled in love with programming in 1984 ([this was my
first machine](http://en.wikipedia.org/wiki/Oric#ric-1)). Since then I
used various languages and platforms (Pascal, C++, Java, .Net…). I
discovered Ruby in 2004 as I needed to parse a large amount of logs on a
.Net application to understand a bug. I was amazed by how much could be
achieved without knowing much of the language. Gradually I realised that
Ruby and Rake were an efficient way to create easy to maintain build
scripts. I got addicted to Ruby and it’s now my everyday language for
most tasks.

I started using Rails in 2005 and it got me deeper into Ruby. Since then
I’ve been using Ruby on different kinds of projects, including the
[plumbing behind a holidays rentals
aggregator](http://www.villanao.co.uk/), automation and continuous
integration, logs analysis for measuring speed or business performance,
CMS and blogs,
[datawarehousing](http://blog.logeek.fr/2008/1/19/a-beginner-s-guide-to-datawarehouse),
[data-driven
applications](http://evolvingworker.com/2008/2/28/using-mind-mapping-data-to-drive-your-software-application),
reporting and more regular web applications with Rails and now Merb.

**Willian Molinari, Brazil\>\>** How should one go about learning the
Ruby language? What material (books, eBooks, online tutorials etc.)
would you recommend?

**Thibaut\>\>** Here are a few things that I find useful:

-   Fire up irb each time you wonder if Ruby does this or that – just
    give it a try,
-   Learn by writing your own unit-tests against the standard library –
    a pretty good way to understand how things work,
-   Read existing code (eg:
    [ACTIVEWAREHOUSE-ETL](http://github.com/aeden/activewarehouse/tree/master/),
    [RUBY FACETS](http://facets.rubyforge.org/),
    [CRUISECONTROL.RB](http://github.com/thoughtworks/cruisecontrol.rb/tree/master))
    to see how projects are structured and which idioms are used,
-   Have a look at [PEEPCODE](http://peepcode.com/) and pick a
    screen-cast or a pdf randomly once in a while,
-   Finally, read [THE RUBY PROGRAMMING
    LANGUAGE](http://www.amazon.com/Ruby-Programming-Language-David-Flanagan/dp/0596516177)
    by David Flanagan and Yukihiro Matsumoto. It’s dense yet amazing.

One thing that really surprised me about Ruby is that you can use it for
real without knowing much of it, since the very beginning – and learn as
you go.

**Keith Brady, Australia\>\>** What are the pros and cons of Ruby that
are being discussed in the development community and what is your
opinion on that?

**Thibaut\>\>** Many discussions occur around the pros and cons of X vs.
Y. Part of these discussions is related to fear – will I be blamed for
making the “wrong” choice ?

Instead of trying to compare languages or tools, I prefer to “budget”
the corresponding time into trying new things out, and see what works
for me or my team (eg: spend a couple of hours or one day on
Silverlight, IronRuby, CouchDB, Cucumber/Webrat, Merb or Ramaze and see
if it proves useful, rinse, repeat).

That said, the cons I often meet are:

-   difficult to read for people coming from a static background: people
    used to Java, C\#, C++ sometimes seem to have a hard-time starting,
-   part of the standard library has issues, like downloading files with
    net/http: when I was faced with these issues, I used wget/curl
    instead to do the job instead,
-   Ruby is slow: for what I’ve done, it has always been fast enough, or
    easy to scale out / refactor if needed. As well I remember C\# was
    considered slow in 2001; I never met an issue that could not be
    worked out somehow, either.

The pros are:

-   pleasure: it feels good once you start using it
-   ability to innovate: quite often when having an idea, you try it out
    and it works
-   a lot of reusable stuff already exists so you can focus on writing
    new, useful code

**Dennis Theisen, Germany\>\>** Could you name three features of Ruby
that you like the most, as compared to other languages? Why?

**Thibaut\>\>** One of the things I like most is the overall simplicity
of the core classes. Most people coming from Java and C\# are surprised
by the fact that there is only Hash and Array (and Enumerable). As a
result it’s easier for newcomers to get started.

Speaking of language features, I really like blocks. I believe they are
the reason why we don’t have to build specialized containers that often
in Ruby. I also like opened classes and duck typing, because these two
features make testing and hacking around a lot easier.

An interesting consequence of the simplicity and duck typing is that in
Ruby “actual reuse” is quite common, whereas in Java and C\# I mostly
experienced “reusable components” that were quite difficult to reuse in
reality.

Finally, I love the fact that Ruby code tends to be concise and that it
creates a shorter path between ideas and their implementation.

**Willian Molinari, Brazil\>\>** What has been your biggest challenge
while working with Ruby?

**Thibaut\>\>** Sysadmin! I’m ok with it but it’s really Rails that got
me into that. Each time I have the impression that I somehow surpassed
myself, a bit like if you’re a child driving a car.

It’s exciting more than frightening though
![:)](http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif)

**Jerry Anning, USA\>\>** What best practices are most important for a
new Ruby programmer to learn and understand?

**Thibaut\>\>** I’d focus on these ones:

-   simplicity – ask yourself if the feature or piece of code is
    absolutely necessary, and write it in a way a beginner could
    understand. Remember that no code is faster and easier to maintain
    than any code,
-   source control – even if you work alone, even for a small “labs”
    type of applications, use SVN, Git or whatever you feel comfortable
    with,
-   unit-testing – learn to use Test::Unit, RSpec, mocks – the most
    horrible bugs I’ve tracked down could have all been avoided with a
    one-line unit-test,
-   continuous integration – because it’s like having an tireless
    assistant that can do a lot of repetitive stuff for you!

**Victor Goff, USA\>\>** How do you see the market for Ruby Programmers
in the work place, and do you see it as primarily tied to Rails and Web
related work? Do you see trends in administration or other work?
Whatâ€™s the future for Ruby?

**Thibaut\>\>** From where I stand (I’m in France) and from what I’m
doing now, the Ruby market doesn’t seem to be only tied to Rails and Web
related work.

Ruby can be used in many fashions outside the web. For instance, a lot
of companies have a need to analyze and understand their data: I’m using
Ruby for a lot of different things there (statistics, reporting, data
exchange, ETL…). The more we go, the more websites become front-ends on
top of something that is more complicated. Some of my customers said
they had no issue finding purely web Rails programmers, but that it was
difficult to find people who have a good understanding of data
processing, back-end etc.

On the future of Ruby: it’s very interesting to see more platforms
adopting Ruby (I’m thinking about .Net and Java for instance). I really
believe there is an opportunity for Rubyists here.

**Dennis Theisen, Germany\>\>** Do you think Ruby is ready to be used in
“Enterprise applications”? Kindly justify your answer.

**Thibaut\>\>** There is as many definition of “enterprise applications”
as there are companies, unfortunately. In some companies I work for,
Ruby is pretty good at gluing things together, grabbing out a CSV from
there, cleaning-it up, pushing it to another application ([ENTERPRISE
INTEGRATION WITH
RUBY](http://www.pragprog.com/titles/fr_eir/enterprise-integration-with-ruby)
is an interesting read on that topic). In others, Ruby is pretty good at
creating large and reliable systems, iteratively. In a world-wide
situation where we need to create more with less, I believe Ruby has a
lot of value for Enterprise applications, in a pragmatic way.

So yes, Ruby is ready to create useful things for the enterprise (and
has already been for a long time).

**Satish Talim\>\>** What can / should job candidates (for Ruby) do to
distinguish themselves from their competition?\
**Note**: The candidate has done his/her homework on the company that
they are interviewing with. The candidate understands what they’re
looking for, and the candidate is prepared to show them that he/she fits
the bill, based on the candidate’s skills and experience. What else can
the candidate do, to set themselves apart from other equally
well-qualified and well-prepared candidates?

**Thibaut\>\>** Many coders are eager to propose solutions as soon as
they’ve heard of a topic. A skill that is often missing (and I blame
myself too sometimes) is listening! An efficient way to understand the
user needs and a rare quality.

I also care about finding people who are willing to reuse existing stuff
instead of rolling their own, whenever possible.

Oh yeah and people who have respect for their team-mates, too.

**Satish Talim\>\>** Do you have any other suggestions for these
participants (would-be Ruby developers)?

**Thibaut\>\>** My first suggestion would be to focus your energy on
creating useful code and building things instead of arguing with others
whether Ruby is a good choice or not.

My second suggestion would be to pick up a simple idea you have,
something that would be useful to you first and to implement it. Real
artists ship!

**Satish Talim\>\>** Thanks Thibaut for sharing your views with the
RubyLearning participants.

On 20th Jan. we talk to **Ryan Bates** from USA.

***Disclaimer:***\
*The opinions expressed are those of Thibaut Barrere and do not
necessarily reflect those of
**[www.RubyLearning.com](http://rubylearning.com/)**.*

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

