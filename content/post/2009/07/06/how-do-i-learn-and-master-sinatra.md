---
draft: false
title: How do I learn and master Sinatra?
date: 2009-07-06
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
permalink: /2009/07/06/how-do-i-learn-and-master-sinatra/
tags:
- Corey Donohoe
- Learning Sinatra
- ruby programming
- Sinatra
---
Welcome to the **first** installment on the RL blog, of a mini series –
“**How do I learn and master Sinatra?**” – by top Rubyists using
*Sinatra*. The interview series will provide insight and commentary from
these notable *Sinatra* developers, with the goal of facilitating and
providing answers to the questions Ruby beginners face on *how to learn
and master Sinatra*.<!--more-->

**Satish\>\>** Corey Donohoe, could you tell us something about yourself
– your background, where you are based?

![Corey
Donohoe](http://rubylearning.com/images/CoreyDonohoe.jpg "Corey Donohoe")**Corey
Donohoe\>\>** I’m [Corey Donohoe](http://atmos.org/). I’m based out of
Boulder, Colorado – USA. My background is in computer science and system
administration though I prefer hacking to either of those labels. I’m a
pretty normal dude, I enjoy cycling, music, coffee, micro brews, and all
the other awesomeness that my home state has to offer. I’ve been working
for [Engine Yard](http://www.engineyard.com/) since March of ’07 doing
everything from app support to internal development. I’m currently 1/2
of our internal integrations team.

> Sinatra’s greatest strength is its flexibility

**Satish\>\>** Are there any pre-requisites for a person to start
learning Sinatra

**Corey\>\>** There aren’t any hardcore prerequisites per se; Ruby and
experience in a Ruby web framework is a plus. HTTP verbs play a huge
role in Sinatra, as well as things like query and post params. If you
get those concepts you can hit the ground running.

**Satish\>\>** How should one start learning Sinatra?

**Corey\>\>** Learn Sinatra incrementally. If you have new business
requirements try to think about things like “how would i implement this
in Sinatra?” Take the time to figure that requirement out in Sinatra
then throw the solution out! When the time comes to use Sinatra for
something you’ll have a much more broad understanding of the framework
and you’ll hit fewer blockers.

**Satish\>\>** Which area of Sinatra should a beginner pay particular
attention to?

**Corey\>\>** Understanding the difference between **Sinatra::Base** and
**Sinatra::Default** is definitely something a Sinatra beginner should
focus on early. **Sinatra::Base** is for writing Rack middleware, and
**Sinatra::Default** is normally for writing Rack applications. Learning
the modular style app development is really useful as well as using the
register method to include pieces of functionality. Getting a handle on
those concepts will expose you to the rest of Sinatra, which is
relatively intuitive.

![Sinatra
Icon](http://rubylearning.com/images/sinatralogo.jpg "Sinatra micro-framework")

**Satish\>\>** Is the official documentation on Sinatra good enough for
a beginner? Are there areas which need improvement or need to be
re-written

**Corey\>\>** The Sinatra documentation is well done and I can generally
find answers to my questions just by referencing the docs. There’s
always \#sinatra on freenode or the Sinatra book on github if you need
additional help too. There’s plenty of pretty well tested examples on
github using Sinatra, hancock and integrity come to mind.

**Satish\>\>** Sequel, DataMapper, ActiveRecord – which one would you
recommend to use with Sinatra and why?

**Corey\>\>** I use DataMapper exclusively. It was a bumpy ride a year
ago but these days it’s acceptable for production use. We interface with
more than just relational databases and the ability to keep a consistent
model syntax across various data sources is really attractive to us.
Realistically I feel like I spend less time fighting my framework when
I’m using DataMapper so it’s the clear choice. The one place I wouldn’t
use dm in would be a join heavy relational environment; ActiveRecord is
way better at that.

**Satish\>\>** Is an understanding of Rack important while learning
Sinatra? Why? Which area of Rack should one be really comfortable with?

**Corey\>\>** You don’t need a solid understanding of Rack to get a
Sinatra up and running, but you’ll be missing out on a lot of the power.
It’s extremely beneficial to take the time to learn how the
**Rack::Builder** works as well as the usage of the **use/map/run**
commands in that context. The modularity of Rack really becomes apparent
and you’ll find yourself using Sinatra more effectively.

**Satish\>\>** How should one hone one’s skills in Sinatra?

**Corey\>\>** Read code, write test code, write code. All of the awesome
testing frameworks available for Ruby are available to Sinatra. If you
don’t write tests it might be a good way to familiarize yourself with
testing best practices without the overheard of a larger framework.

**Satish\>\>** What type of projects should a beginner work on to gain
more expertise in Sinatra?

**Corey\>\>** A beginner would benefit from writing something completely
API driven as a first project. So many people couple databases with
dynamic web applications but it’s kind of liberating to just be an
intermediary service. Twitter apps are pretty trivial to implement and
can teach you a lot. They also expose you to a pretty large userbase to
solicit feedback.

**Satish\>\>** Could you suggest some web services that a Sinatra
beginner could develop himself / herself?

**Corey\>\>** Web services are great targets for introducing Sinatra
into your workplace. Identify a pain point in your organization and put
a small app in front of it. It doesn’t have to replace something
overnight but it’s a great way to sneak functionality in at work. Once
you have a few of these built you start to reap the benefits of
microapps and web services.

**Satish\>\>** Anything else you would like to add?

**Corey\>\>** Learning Sinatra is the best thing you can do while we all
wait for Rails 3 to land. The middleware you write will be able to be
dropped right into your Rails 3 applications so it’s not like you’re
wasting time. We’re starting to build really modular systems using
Sinatra by building APIs into those systems. I think a lot of people
would benefit from breaking their monolith apps down into microapps and
Sinatra is a great way to do it.

People looking for a template might want to investigate the singem gem.
It has basic templates for twitter apps or regular webservices. All of
them are bootstrapped for testing with cucumber+rspec.

*Thank you Corey. In case you have any queries and/or questions, kindly
post your questions here (as comments to this blog post) and Corey would
be glad to answer.*

***Post supported by 1st Easy Limited*:** UK based 1st Easy Limited
offer Sinatra and Rails hosting running on a Phusion Passenger
(mod\_rails) and LAMP stack. If you want to try your hand at developing
with Sinatra, why not let them arrange a [trial hosting
account](http://www.1steasy.com/ruby-on-rails.htm#try) for you? You’ll
get to deploy your app, with full technical support from their team!

