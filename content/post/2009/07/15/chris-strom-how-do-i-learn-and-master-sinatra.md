---
draft: false
title: 'Chris Strom: How do I learn and master Sinatra?'
date: 2009-07-15
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
- Learn Sinatra
- Ruby
- Sinatra
layout: post
permalink: /2009/07/15/chris-strom-how-do-i-learn-and-master-sinatra/
tags:
- Chris Strom
- Learning Sinatra
- ruby programming
- Sinatra
---
Welcome to the **fifth** installment on the RL blog, of a mini series –
“**How do I learn and master Sinatra?**” – by top Rubyists using
*Sinatra*. The interview series will provide insight and commentary from
these notable *Sinatra* developers, with the goal of facilitating and
providing answers to the questions Ruby beginners face on *how to learn
and master Sinatra*.<!--more-->

**Satish\>\>** Chris Strom, could you tell us something about yourself –
your background, where you are based?

![Chris
Strom](http://rubylearning.com/images/chris_strom.jpg "Chris Strom")**Chris
Strom\>\>** My name is Chris Strom. In my day job, I am the Director of
Software Engineering for mdlogix, a small company in Baltimore,
Maryland. We develop software that manages clinical research trials and
associated data. We primarily code with Ruby on Rails.

My background is in web development, mostly in Perl until \~2005 when I
made the switch to Ruby.

**Satish\>\>** Are there any pre-requisites for a person to start
learning Sinatra?

**Chris\>\>** There are no prerequisites to getting started with
Sinatra. A basic understanding of Ruby and HTTP will serve you well,
especially as applications become more complicated.

Sinatra is pretty unique in my experience in that it can handle
extremely basic web applications, but is more than capable of handling a
decent amount of complexity. It is good for the beginner, but capable
enough for the pro. It is good for prototyping simple applications, but
can support complexity as well.

**Satish\>\>** How should one start learning Sinatra?

**Chris\>\>** Learn Sinatra by playing!

Imagine small apps (data aggregation, simple API proxies, silly games)
and then implement them. Sinatra makes it easy. Go on… do it!

> Sinatra – quickly create tiny web apps and services

**Satish\>\>** Which area of Sinatra should a beginner pay particular
attention to?

**Chris\>\>** Beginners should pay attention to the HTTP verbs at the
start of action blocks (i.e. the “get” in “get ‘/foo’ do …”). Simple
applications will be all GETs, but as you become more proficient you
will need to use POST and others.

Don’t overlook helpers and templating. Neither are required but their
effective use can significantly cut down on the amount of code in your
Sinatra actions. This will make the application easier to read and
easier to maintain.

**Satish\>\>** Is the official documentation on Sinatra good enough for
a beginner? Are there areas which need improvement or need to be
re-written

**Chris\>\>** The official documentation is excellent.

Any time I find myself wondering, “how would you go about accomplishing
that in Sinatra?”, the documentation has a nice, concise answer, with
links to further reading as necessary.

**Satish\>\>** Sequel, DataMapper, ActiveRecord – which one would you
recommend to use with Sinatra and why?

**Chris\>\>** I do not believe that I have ever used a full blown ORM
with Sinatra. If I find myself thinking in ORM terms, I generally use
Rails. If I am using a data store at all, it is usually one or two
tables, which sqlite handles nicely. For more complex data structures, I
use CouchDB, for which CouchRest works quite well.

![Sinatra
Icon](http://rubylearning.com/images/sinatralogo.jpg "Sinatra micro-framework")

**Satish\>\>** Is an understanding of Rack important while learning
Sinatra? Why? Which area of Rack should one be really comfortable with?

**Chris\>\>** No. Sinatra does an exceptional job of hiding Rack from
the developer. It is there as your skill and need evolves, but
developers can accomplish 95% of what they need to do without any
understanding of Rack.

The only area of Rack with which you need to be really comfortable is\
 the one that you need in order to get you current work done.

**Satish\>\>** How should one hone one’s skills in Sinatra?

**Chris\>\>** Developing applications. Sinatra makes it easy! Look for
small things that can be collected / reported on.

Blog about it. It is amazing how many things you think that you
understand that blogging about it will tell you that you don’t.

**Satish\>\>** What type of projects should a beginner work on to gain
more expertise in Sinatra?

**Chris\>\>** Beginners should work with projects with as few
requirements as possible. The closer to pure Sinatra you can get, the
better. Once you have your bearings, then you can introduce things like
templating or ORM layers.

**Satish\>\>** Could you suggest some web services that a Sinatra
beginner could develop himself / herself?

**Chris\>\>** I would recommend starting with non-DB applications.
Building something on top of an existing service with well established
APIs, such as Twitter / Flickr would be a nice place to start.

**Satish\>\>** Anything else you would like to add?

**Chris\>\>** Do not underestimate the importance of testing. The
temptation with something as seemingly simple as Sinatra is to forgo
testing and just dive straight into the code. This might be OK on very
simple applications, but anything of moderate complexity requires
testing to prevent silly mistakes from compounding into huge ones.

Sinatra makes testing easy. Sinatra wants you to test. Don’t disappoint
Sinatra.

As always, if you write your tests before your code, your code will be
be cleaner, more robust and easier to maintain.

My last bit of advice is to not program by coincidence. Sinatra is very
powerful — so much so that, at times, you will find that things just
seem to work. Always take some time to understand why things work like
they do in Sinatra — Sinatra rewards curiosity.

*Thank you Chris. In case you have any queries and/or questions, kindly
post your questions here (as comments to this blog post) and Chris would
be glad to answer.*

**Others in this series:**

-   [Corey
    Donohoe](http://rubylearning.com/blog/2015/01/07/corey-donohoe-how-do-i-learn-and-master-sinatra/)
-   [Jeremy
    Evans](http://rubylearning.com/blog/2009/07/08/jeremy-evans-how-do-i-learn-and-master-sinatra/)
-   [Graham
    Ashton](http://rubylearning.com/blog/2009/07/10/graham-ashton-how-do-i-learn-and-master-sinatra/)
-   [Karel
    Minarik](http://rubylearning.com/blog/2015/01/07/karel-minarik-how-do-i-learn-and-master-sinatra-reprint/)

***Post supported by 1st Easy Limited*:** UK based 1st Easy Limited
offer Sinatra and Rails hosting running on a Phusion Passenger
(mod\_rails) and LAMP stack. If you want to try your hand at developing
with Sinatra, why not let them arrange a [trial hosting
account](http://www.1steasy.com/ruby-on-rails.htm#try) for you? You’ll
get to deploy your app, with full technical support from their team!

