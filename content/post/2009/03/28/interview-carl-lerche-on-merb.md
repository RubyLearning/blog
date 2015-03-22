---
draft: true
title: 'Interview: Carl Lerche on Merb'
date: 2009-03-28
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
- Merb
- Ruby
description:
- RubyLearning talks to Carl Lerche, a core Merb developer, on the eve of the online
  Merb course at RubyLearning.
keywords:
- Interviews,Carl Lerche,Merb,Merbist,Ruby,RubyLearning,The Merb Way,Merb in action
layout: post
permalink: /2009/03/28/interview-carl-lerche-on-merb/
tags:
- Carl Lerche
- interviews
- Merb
- Merb in Action
- Merbist
- Ruby
- RubyLearning
- The Merb Way
---
RubyLearning’s 3rd batch of the “**Introduction to Merb**” course starts
today, 28th Mar. 2009. Satish Talim of RubyLearning caught up with
**Carl Lerche**, Merb core team member, to learn more about **Merb**.<!--more-->

![Carl Lerche,
USA](http://rubylearning.com/images/carl.jpg "Carl Lerche, USA")

**Satish\>\>** Welcome, Carl and thanks for taking out time to share
your thoughts. For the benefit of the readers, could you tell us
something about your self?

**Carl\>\>** First off, thanks for having me. So, a little about me?
Let’s see, I’ve been working with Ruby for about 4 or 5 years now. I
discovered Ruby a while back working with FreeBSD. I started using Ruby
on Rails back before it was released as 1.0 software and have been
enjoying the Ruby world since then. I’ve been involved with a number of
open source Ruby projects and am currently employed full time by Engine
Yard to contribute to Ruby on Rails.

**Satish\>\>** How closely have you been associated with Merb?

> Merb – Ruby web framework for the enterprise

**Carl\>\>** I have been actively contributing to the Merb project for
about 9 months and am on the core developer team. I started
investigating Merb about a year ago when I needed a Ruby framework that
offered greater flexibility than Ruby on Rails. It looked quite
promising, but it had a number of drawbacks, such as the router. I
decided to write the missing code and contribute back to the project.
Since then, I have been actively involved in Merb’s development.

![Merb](http://rubylearning.com/images/powered-by-merb-big.png "Merb - Ruby web framework for the enterprise")

**Satish\>\>** If someone wanted to learn and start using Merb, how does
one do that? Can you talk about what all is being done for Merb in terms
of documentation, books, tutorials and training?

**Carl\>\>** Even though Merb adoption has been picking up, it is still
a fairly new framework. As such, learning resources can be scarce. I
would say that one of the best ways to learn Merb is to read the source
code and the specs. We make quite a bit of effort to keep the code
readable and we only spec out the public API, so everything that happens
in the specs is actually something that a developer using Merb should be
using. That being said, the Merb website does have a wiki that is
updated and that contains good information. The Merb community is also
quite helpful and there are lots of people on the IRC channel that
answer questions.

**Satish\>\>** What type of projects would you use Merb for?

**Carl\>\>** You can use for any web application. It is a very flexible
framework that handles the VC bits of MVC in context of the web. This
includes anything from large, complex, web applications to simple web
services. Merb is ORM agnostic, so you can use it with ActiveRecord,
DataMapper, Sequel, or any other library. However, we do recommend using
DataMapper, which is why it is the default ORM when you install the full
Merb stack. Personally, I have never needed to use anything besides Merb
in the context of the web.

[![Sponsor: Railsware for premium-quality web
applications](http://rubylearning.com/images/Railsware125x125.png "Sponsor: Railsware for premium-quality web applications")](http://www.railsware.com/)

**Satish\>\>** With Merb and Rails merging by the end of the year, how
does it benefit the developer?

**Carl\>\>** The Rails/Merb merge is actually quite exciting. First, let
me clear up a misconception that seems to be somewhat common. The Rails
/ Merb merge is not so much of a code base merge as it is a joining of
forces of the developers. Anyway, coming from the Merb side of things,
working on Rails 3 gives me the opportunity to revisit all the things
that are already implemented in Merb and question whether they are as
good as possible, such as AbstractController. As it turns out,
AbstractController is not as abstract as it could be. In other words,
Rails 3 will actually be a significant improvement over current Merb.
Also, since Rails has a much greater reach within businesses, all
developers who use Merb for their hobby projects but have to use Rails
at work will be able to use Rail 3, the framework with everything that
made Merb great and more.

**Satish\>\>** Tell us something about deployment of Merb apps.

**Carl\>\>** Deploying Merb apps is actually relatively easy. Merb has
an executable that handles creating all the child processes. As of the
latest version, it also monitors the processes for memory and will
restart them if they start getting out of hand. Also, apache passenger
works quite well with Merb. Also, something to checkout would be Engine
Yard’s new Solo offering. It’s pretty slick. You can deploy a Merb app
onto amazon’s AWS platform quite painlessly through an easy to use web
interface. No matter which way you want to go, I would definitely
recommend hitting up the IRC channel if you have any questions.

**Satish\>\>** Carl, thank you for your time. Anything else you would
like to add?

**Carl\>\>** Well, I’ll mention a cool new feature that will be in Rails
3 and most likely Merb 1.1. That would be mountable apps. I’ve started
working on this recently and it’s shaping out quite nicely. It’ll
basically let any application developed with Merb or Rails 3 be reusable
in any other application. So, if you develop a blog or forum
application, you could just release that app as a gem and mount it in
any other app and share the models and other fun stuff. I’ll be talking
more about this at railsconf, so, if you are there, be sure to stop by.
I’ll see you all there!

**Satish\>\>** Carl, thank you for your time.

***Disclaimer:***\
*The opinions expressed are those of Carl Lerche and do not necessarily
reflect those of **[www.RubyLearning.com](http://rubylearning.com/)**.*

***Post supported by Railsware*:** At [Railsware](http://railsware.com/)
we chose Ruby on Rails as the core technology from the very beginning.
As a product development company [we build web
applications](http://railsware.com/services) for our clients and for
ourselves and have experienced the benefits of both Rails and Merb. We
are looking forward to this merge of Rails and Merb for better
performance and keeping the best of both frameworks, and a rigorous API
which will definitely result in reliable results and lower amount of
patching. As the big result, developing a web application on Rails 3
will become even faster and cheaper. We are eagerly waiting to start
building and delivering more great web apps using Rails 3.

