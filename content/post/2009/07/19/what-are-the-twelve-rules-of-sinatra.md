---
draft: false
title: What are the Twelve Rules of Sinatra?
date: 2009-07-19
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/rubylearning
categories:
- Beginners
- Ruby
- Sinatra
layout: post
permalink: /2009/07/19/what-are-the-twelve-rules-of-sinatra/
tags:
- Jeremy Evans
- Learning Sinatra
- ruby programming
- Sinatra
- Twelve Rules of Sinatra
---
Jeremy Evans tells us his thoughts on<!--more-->
## The Twelve Rules of Sinatra

**The Twelve Rules of Sinatra: [Download this as a Free
Report](http://rubylearning.com/data/Sinatra12Rules.pdf).**

Recently, I was reading Scott Adams’ (of Dilbert fame) blog post “[Rule
of Twelve](http://www.dilbert.com/blog/entry/rule_of_twelve)” where he
stated:

> The Rule of Twelve states that if you know twelve concepts about a
> given topic you will look like an expert to people who only know two
> or three. If you learn more than twelve concepts about a topic, the
> value of each additional one drops off considerably. Allow me to be
> the first to confess that twelve is not a magic and inviolable number.

He also wrote a follow-up post to support his statement: “[Twelve Rules
of Energy Efficient
Building](http://www.dilbert.com/blog/entry/twelve_rules_of_energy_efficient_building/)“.

This made me wonder, could we apply the same “Rule of Twelve” to
**Sinatra**?

![Jeremy
Evans](http://rubylearning.com/images/jeremy-125.jpg "Jeremy Evans")Here
is **[Jeremy Evans’](http://code.jeremyevans.net/)** take on this:

1.  Just like Rails, keep your controller/actions simple, and put most
    of your business logic in your models. This makes testing and code
    reuse easier.
2.  Also like Rails, avoid excess logic in your views. Add helper
    methods that the views call to keep the views clean.
3.  Unlike Rails, read the Sinatra source. The main part is a single
    file that’s around 1000 lines of quite understandable Ruby code.
    Just reading it will probably make you a better programmer.
4.  If you have a problem that you think other people probably have
    (e.g. a Rails-like flash), look first for a Rack middleware that
    handles it, rather than recreating the wheel.
5.  Untested code will probably break sooner than later, so if you want
    the code to work in the future, write tests.

*Well, Jeremy has set the ball rolling. **What’s your take on this?**
Kindly post your thoughts as comments to this blog post. Looking forward
to some interesting read.*

