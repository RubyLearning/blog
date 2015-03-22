---
draft: false
title: 'Interview: Adam Keys on Sinatra'
date: 2009-03-03
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/satishtalim/about
categories:
- Interview
- Ruby
- Sinatra
description:
- |
  Adam Keys talks to RubyLearning's "Introduction to Sinatra" course participants on Sinatra micro web framework.
keywords:
- Adam Keys,Interviews,Ruby,Sinatra,The Ruby Programming Language,web framework
layout: post
permalink: /2009/03/03/interview-adam-keys-on-sinatra/
tags:
- Adam Keys
- interviews
- Ruby
- Sinatra
- The Ruby Programming Language
- web framework
---
On the eve of the first ever online “**Introduction to Sinatra**”
course, Satish Talim of RubyLearning caught up with **Adam Keys** and
talked to him on **Sinatra**, in this interview.<!--more-->

![Adam Keys,
USA](http://rubylearning.com/images/AdamKeys.jpg "Adam Keys, USA")

**Satish Talim\>\>** Welcome, Adam and thanks for taking out time to
share your thoughts. For the benefit of the readers, could you tell us
something about your self?

**Adam Keys\>\>** I enjoy exploring all sorts of topics that are
coincidental with Ruby: information design, functional languages,
linguistics, architecture and other sorts of semi-boring topics.
Entertaining people makes me happy. I live with my wife, three dogs and
two cats in Dallas, TX. My website is
[http://therealadam.com/](http://therealadam.com/) and I’m
[therealadam](http://twitter.com/therealadam) on Twitter.

> Sinatra – quickly create tiny web apps and services

**Satish\>\>** What’s Sinatra and how did you get involved with it?

**Adam\>\>** Sinatra is a tiny little library for writing web
applications. I like to say it’s the smallest possible DSL for
describing HTTP interactions. It’s great for building small to
medium-size web apps and also for building web APIs, REST services, and
web hooks.

**Satish\>\>** For a person new to web development, how can Sinatra
help?

**Adam\>\>** Sinatra is very close to how HTTP works, so it’s a great
introduction to the workings of the protocol and how it’s used to make
REST-structured apps. Further, Sinatra doesn’t put much overhead in your
way. You get right down to writing the interesting part of your app or
figuring out how to extract infrastructure to make writing the
interesting part of your app easier.

**Satish\>\>** How can one go about learning Sinatra?

**Adam\>\>** Check out my screencast, “[Classy Web Development with
Sinatra](http://www.pragprog.com/screencasts/v-aksinatra/classy-web-development-with-sinatra)“!

If you’re experienced with Ruby, just give the Sinatra sources a read.
It’s less than two thousand lines and pretty straight-forward to
understand.

If you’re less experienced, I recommend just searching for Sinatra
applications and add-ons on GitHub and reading their code. I learned a
lot of great things this way.

**Satish\>\>** Where all can Sinatra be used?

**Adam\>\>** It’s great for building mashups. My friend and co-worker
Bruce Williams used Twitter data to build Front Row to History when he
went to Obama’s election-day rally. Sinatra’s small footprint, both
resource-wise and conceptually, made it easy to build this application
in less than twenty-four hours.

There are lots of interesting little
[wikis](http://github.com/sr/git-wiki/tree/master) and
[weblogs](http://github.com/rtomayko/wink/tree/master) written in
Sinatra. There’s also a neat gem documentation server. Sinatra is fun
for building these apps because it you can mix and match the libraries
you are interested in experimenting with.

Sinatra’s ideal for building services. It’s quite easy to sketch out the
resources a REST services presents and then write it directly in
Sinatra.

**Satish\>\>** Who all have been using Sinatra and in what way?

**Adam\>\>** A couple of the guys at [Heroku](http://heroku.com/) work
on Sinatra. I believe they are using it to compose their service out of
many smaller apps.

[GitHub^[1](#fn-1508-1)^](http://github.com/) released sample apps for
their web hooks API as Sinatra apps. Lots of people forked those apps to
make new apps that integrate with the services their interested in.

At FiveRuns, we use Sinatra in our metrics collection API for
[Dash](http://dash.fiveruns.com/). Every number in the system is
uploaded to a Sinatra app before it proceeds through our processing
queues.

![Sinatra
Icon](http://rubylearning.com/images/sinatralogo.jpg "Sinatra microframework")

**Satish\>\>** Is deploying a Sinatra app easy? What would your
recommend?

**Adam\>\>** Since Sinatra is built on top of Rack, you’ve got options.
You can use Phusion Passenger to deploy with Apache. If your needs are
more sophisticated, you can use Mongrel, Thin, Swiftiply or any other
Rack-compliant server. And it’s all just files, so you can use all your
favorite tools: Capistrano or Vlad, Subversion or Git.

**Satish\>\>** Do you have any suggestions for RubyLearning’s ”
**Introduction to Sinatra^[2](#fn-1508-2)^** ” course participants?

**Adam\>\>** Using Sinatra is a great opportunity to learn about what
you miss from other, larger frameworks. Once you’ve decided you need
some feature, write it yourself. I’ve found this is a fantastic way to
learn about web frameworks.

**Satish\>\>** Thanks Adam^[3](#fn-1508-3)^ for sharing your views with
the RubyLearning Sinatra course participants.

***Disclaimer:***\
*The opinions expressed are those of Adam Keys and do not necessarily
reflect those of **[RubyLearning.org](http://rubylearning.org/)**.*

1.  **Introduction to Git & GitHub**: Here are the [course
    details](http://rubylearning.com/blog/2009/02/10/git-and-github-a-free-course/).
    [↩](#fnref-1508-1)
2.  **Introduction to Sinatra**: Here are the [course
    details](http://rubylearning.com/blog/2009/02/25/introduction-to-sinatra-a-new-course/).
    [↩](#fnref-1508-2)
3.  An [earlier
    interview](http://rubylearning.com/blog/2008/04/22/ruby-interview-adam-keys-of-fiveruns/)
    of Adam by RubyLearning. [↩](#fnref-1508-3)

