---
draft: false
title: 'Follow Cost: A Sinatra app for Twitter'
date: 2009-04-28
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
- Twitter
description:
- RubyLearning caught up with Luke Franci and Barry Hess creators of Follow Cost,
  in this interview.
keywords:
- Follow Cost,Twitter,Luke Francl,Barry Hess,Merb,Sinatra, Ruby
layout: post
permalink: /2009/04/28/follow-cost-a-sinatra-app-for-twitter/
tags:
- Barry Hess
- Follow Cost
- Luke Francl
- Merb
- Ruby
- Sinatra
- Twitter
---
RubyLearning caught up with **Luke Francl** and **Barry Hess** creators
of [Follow Cost](http://followcost.com/) – a **Twitter** tool to help
people decide if following someone is worth it, and talked to them about
Follow Cost and Sinatra in this interview.<!--more-->

![Luke
Francl](http://www.rubylearning.com/images/luke-headshot.jpg "Luke Francl")

**Satish Talim\>\>** Luke and Barry, could you tell us something about
yourselves – your backgrounds, where both of you are based?

**Luke\>\>** I’m a Rails developer based in Minneapolis, USA. I worked
as a Java developer for a number of years before making the jump to
Ruby. I’ve been doing this for about 3 years now.

**Barry\>\>** I work with Ruby and Rails from a rural area, an hour
south of Minneapolis. The start of my career was in a very corporate
environment, mostly working with Java. I’ve been messing with Ruby for
nearly 3 years.

![Barry
Hess](http://www.rubylearning.com/images/barry_hess.jpg "Barry Hess")

**Satish\>\>** Barry, you are the “Prime Hacker” at Iridesco. Tell us
something about this.

**Barry\>\>** I’ve worked with [Iridesco](http://iridesco.com/) for over
2 years now. We’re a 4-man team: 2 founders and jacks-of-all-trade in
New York City, a programmer in Transylvania, and me. So we’re rather
distributed. Our primary app is [Harvest](http://www.getharvest.com/), a
time tracking and invoicing app. To help us work as a distributed team,
we built [Co-op](http://coopapp.com/), a sort of private, group Twitter
that ties in with Harvest rather nicely.

Titles always give me trouble. Am I a software engineer? Developer?
Programmer? Without a corporate overlord to tell me I am a Programmer IV
or some such, it becomes rather difficult. When Danny Wen, one of
Iridesco’s co-founders, signed me up for this year’s SXSWi conference
with the title Prime Hacker, well, I thought that title was better than
any I had thought of!

**Satish\>\>** What is **Follow Cost**?

Follow Cost is a tool to help people decide if following someone is
worth it. Follow Cost will tell you how often someone tweets. Different
people have different standards for how much is “too much” and Follow
Cost can help you decide for yourself, but we do give a special warning
for people who tweet more than Robert Scoble. 1/1000th of Scoble’s
average daily output is called a “milliscoble.”

**Satish\>\>** What was the idea behind Follow Cost ?

**Luke\>\>** Barry and I and a few other Minnesota developers were on a
road trip to the WindyCityRails conference in Chicago. We were
complaining about how certain people just Tweet way too much, and how it
would be cool if there was a tool to warn you before following. That was
the genesis of Follow Cost. After I got home, I whipped up a couple
mockups and asked Barry if he wanted to help build it.

**Satish\>\>** Why did you decide to use Sinatra for Follow Cost ?

For such a simple app, Sinatra was a really good fit. Originally, Follow
Cost did not even have a database — it queried Twitter, then page cached
the results. But the main reason we wanted to use Sinatra was to try
something new. (This was also our first foray into jQuery.) We’ve both
been building Rails apps for years, and we wanted to try something else.

**Satish\>\>** For a person new to web development, how can Sinatra
help?

**Luke\>\>** I think that Sinatra brings the power of Ruby with the
fast-paced development of PHP. One of the things I always liked about
PHP was that you could get something running really quickly. Just upload
it to the server and you were all set. With Passenger, developing in
Sinatra is very much like that, except in a nice language like Ruby
instead of a crufty one like PHP.

**Barry\>\>** Sinatra allows a beginner to see results quickly. Even in
your local environment Sinatra gets you from code to seeing something in
the browser faster than Rails. Deploying a quick Sinatra practice app to
a shared host like Dreamhost, which uses Passenger, is a piece of cake
compared to when we started with Rails. In our day, we also deployed up
hill both ways, in the snow.

**Satish\>\>** How can one go about learning Sinatra?

Well, we heard there’s this **RubyLearning class^[1](#fn-1931-1)^** on
it…

We went about it by following the [Sinatra
book](http://www.sinatrarb.com/book.html) and the source code. It’s nice
that Sinatra’s source is so small because you can easily read it and
understand it.

**Satish\>\>** Do you have any suggestions for RubyLearningâ€™s
“[Introduction to
Sinatra](http://rubylearning.com/blog/2009/04/07/new-sinatra-course-announced/)”
course participants?

Pick something in Sinatra’s sweet spot — small applications that need to
be dynamic — and have fun with it! We find Sinatra to be a perfect tool
to tie into all the hot social network API’s out there. And remember,
the world can always use one more app based on the Twitter API!

*Thank you Luke and Barry. In case you have any queries and/or
questions, kindly post your questions here (as comments to this blog
post) and they would be glad to answer.*

1.  **Introduction to Sinatra**: Here are the [course
    details](http://rubylearning.com/blog/2009/04/07/new-sinatra-course-announced/).
    [↩](#fnref-1931-1)

