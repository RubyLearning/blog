---
draft: false
title: 'Blake Mizerany: How do I learn and master Sinatra?'
date: 2009-08-11
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
permalink: /2009/08/11/blake-mizerany-how-do-i-learn-and-master-sinatra/
tags:
- Blake Mizerany
- Learning Sinatra
- ruby programming
- Sinatra
---
Welcome to the **last** installment on the RL blog, of a mini series --
"**How do I learn and master Sinatra?**" -- by top Rubyists using
*Sinatra*. The interview series will provide insight and commentary from
these notable *Sinatra* developers, with the goal of facilitating and
providing answers to the questions Ruby beginners face on *how to learn
and master Sinatra*.<!--more-->

**Satish\>\>** Blake Mizerany, could you tell us something about
yourself -- your background, where you are based?

![Blake
Mizerany](http://www.rubylearning.com/images/blake_mizerany.jpg "Blake Mizerany")**Blake
Mizerany\>\>** I'm one of the many Mad-Scientiests at Heroku. I started
the Sinatra project in September of '07. I create useless, and sometimes
useful, things out of Ruby, Erlang, and sometimes C.

**Satish\>\>** Are there any pre-requisites for a person to start
learning Sinatra?

**Blake\>\>** Be prepared to throw out what the big frameworks taught
you and be prepared to learn what they hide from you. It's not
difficult.

**Satish\>\>** Would you suggest that a beginner learns Sinatra before
learning Ruby on Rails? Why?

**Blake\>\>** Absolutely. When you learn a large framework first, you're
introduced to an abundance of ideas, constraints, and magic. Worst of
all, they start you with a pattern. In the case of Rails, that's MVC.
MVC doesn't fit most web-applications from the start or at all. You're
doing yourself a disservice starting with it. Back into patterns, never
start with them. Don't think you'll win that big bet on the golf course
just because you bought that \$10,000 set of golf clubs.
![;)](http://rubylearning.com/blog/wp-includes/images/smilies/icon_wink.gif)

> Sinatra -- quickly create tiny web apps and services

**Satish\>\>** Any features of Sinatra that you consider awesome?

**Blake\>\>** Sinatra features that I consider awesome are:

1.  **The community**. I've met so many bright people on the mailing
    list and in IRC. Including those I work with at Heroku today. These
    people are fantastic and always willing to help. Drop in anytime.
2.  **halt and pass**. See the README.
    ![:)](http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif)
3.  **Sinatra::Base**

**Satish\>\>** How should one start learning Sinatra?

**Blake\>\>** Read the README. It has \*everything\* you need to start.
Use Heroku to deploy.

Then learn Rack. Understand how Rack works. Write basic apps in Rack.
Write a simple peice of middleware.

**Satish\>\>** Which area of Sinatra should a beginner pay particular
attention to?

**Blake\>\>** It's not a MVC framework that starts you with CRUD. You
can separate your concerns how you like. Don't start using it they way
you would use a MVC framework. You \*can\* use it like a MVC framework;
but it will make you a better person to keep things simpler until you
need those abstractions.

**Satish\>\>** Is the official documentation on Sinatra good enough for
a beginner? Are there areas which need improvement or need to be
re-written

**Blake\>\>** Yes. The README is a fantastic place to start.

**Satish\>\>** Sequel, DataMapper, ActiveRecord -- which one would you
recommend to use with Sinatra and why?

**Blake\>\>** Any. When I do use a SQL database, which is rare these
days, I use Sequel because it's light on memory and dependencies (see
[http://github.com/rtomayko/sinatra-sequel/tree/master](http://github.com/rtomayko/sinatra-sequel/tree/master)).
It just always works. I'll use ActiveRecord (AR) when I have something
CRUD'y that I know is CRUD'y; AR is awesome at that.

![Sinatra
Icon](http://rubylearning.com/images/sinatralogo.jpg "Sinatra micro-framework")

**Satish\>\>** Is an understanding of Rack important while learning
Sinatra? Why? Which area of Rack should one be really comfortable with?

**Blake\>\>** You don't need to know Rack to learn Sinatra. It would
behoove you to understand it to ensure you get the most out of Sinatra.
Rack is the foundation of Sinatra.

**Satish\>\>** How should one hone one's skills in Sinatra?

**Blake\>\>** Read the source. It's less than 1,200 LOC. Thanks to the
all the great contributions, it's a fantastic example of how to get a
ton of features out of Ruby with little, clean, pretty Ruby code.

**Satish\>\>** What type of projects should a beginner work on to gain
more expertise in Sinatra?

**Blake\>\>** Build a JSON web service. Build a small blog. Build a url
shortner. Any of those will get your feet wet. You'll see how Sinatra
gets you going quickly and how it can grow to great heights to fit most
of your needs as a framework.

*Thank you Blake. In case you have any queries and/or questions, kindly
post your questions here (as comments to this blog post) and Blake would
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
-   [Chris
    Strom](http://rubylearning.com/blog/2009/07/15/chris-strom-how-do-i-learn-and-master-sinatra/)
-   [Nick
    Plante](http://rubylearning.com/blog/2009/07/17/nick-plante-how-do-i-learn-and-master-sinatra/)
-   [Julio Javier
    Cicchelli](http://rubylearning.com/blog/2009/07/20/julio-javier-cicchelli-how-do-i-learn-and-master-sinatra/)
-   [Carlos
    Gabaldon](http://rubylearning.com/blog/2009/07/21/carlos-gabaldon-how-do-i-learn-and-master-sinatra/)

