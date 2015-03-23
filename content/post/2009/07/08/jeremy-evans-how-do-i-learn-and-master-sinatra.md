---
draft: false
title: 'Jeremy Evans: How do I learn and master Sinatra?'
date: 2009-07-08
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
permalink: /2009/07/08/jeremy-evans-how-do-i-learn-and-master-sinatra/
tags:
- Jeremy Evans
- Learning Sinatra
- ruby programming
- Sinatra
---
Welcome to the **second** installment on the RL blog, of a mini series –
“**How do I learn and master Sinatra?**” – by top Rubyists using
*Sinatra*. The interview series will provide insight and commentary from
these notable *Sinatra* developers, with the goal of facilitating and
providing answers to the questions Ruby beginners face on *how to learn
and master Sinatra*.<!--more-->

**Satish\>\>** Jeremy Evans, could you tell us something about yourself
– your background, where you are based?

![Jeremy
Evans](http://rubylearning.com/images/jeremy-125.jpg "Jeremy Evans")**Jeremy
Evans\>\>** I am [Jeremy Evans](http://code.jeremyevans.net/) and I do
computer work for the government in Sacramento, CA, USA. I’ve been using
Ruby since 2004.

**Satish\>\>** Are there any pre-requisites for a person to start
learning Sinatra?

**Jeremy\>\>** I think you need a basic understanding of Ruby syntax,
but once you have that you can pretty much dive right in. Sinatra is
simple enough to understand that not much else should be required.

**Satish\>\>** How should one start learning Sinatra?

**Jeremy\>\>** I’d recommend reading the documentation on the Sinatra
website, especially the README, FAQ, and the Sinatra Book.

After that, just start coding an application, referring to those
documentation sources and the RDoc API documentation.

> Sinatra – quickly create tiny web apps and services

**Satish\>\>** Which area of Sinatra should a beginner pay particular
attention to?

**Jeremy\>\>** I’m not sure a beginner should focus on a particular
aspect. The focus should depend on the application the programmer wants
to create.

**Satish\>\>** Is the official documentation on Sinatra good enough for
a beginner? Are there areas which need improvement or need to be
re-written

**Jeremy\>\>** This is hard for me to say, as I was already fairly
experienced with Ruby when I started learning Sinatra (and there wasn’t
nearly as much documentation back then), but I think the introductory
documentation is good enough for a beginner.

If there is one aspect of the documentation that could be improved, I
think it’s that the RDoc API documentation could be more complete, as
some methods are undocumented.

**Satish\>\>** Sequel, DataMapper, ActiveRecord – which one would you
recommend to use with Sinatra and why?

**Jeremy\>\>** As I’m the maintainer of
[Sequel](http://sequel.rubyforge.org/), I’m obviously biased towards
Sequel, at least if you are using an SQL database. If you are using a
non-SQL database and want ORM-like behavior that the native adapter
doesn’t provide, DataMapper may be a good choice. If you want to use
ActiveRecord, you need to make sure your application is single threaded,
or use a Rack middleware to clean up the connection pool manually.

I think Sequel and Sinatra are a good fit for each other as they both
are simple and flexible. Both allow you to accomplish a lot with not
much code.

![Sinatra
Icon](http://rubylearning.com/images/sinatralogo.jpg "Sinatra micro-framework")

**Satish\>\>** Is an understanding of Rack important while learning
Sinatra? Why? Which area of Rack should one be really comfortable with?

**Jeremy\>\>** I think an understanding of Rack is helpful, but not
required. Learning how Rack works, especially how you can use middleware
to reuse common code between applications (even if they use different
frameworks), is definitely worth the small amount of time it takes.
However, if you just want to learn Sinatra basics, I wouldn’t focus on
learning Rack first.

**Satish\>\>** How should one hone one’s skills in Sinatra?

**Jeremy\>\>** Like everything else in programming, once you have the
basics, the best way to improve your skills is to practice. With
Sinatra, the best way to practice is to think of a web
site/application/service that you want to create, and use Sinatra to
create it. As you code, you’ll probably come across situations where you
know what result you want, but not how to get there. That’s when you
need to do some research in the API docs or the source code. If you are
still unsure after doing some research, jump on the \#sinatra IRC
channel and ask questions there.

**Satish\>\>** What type of projects should a beginner work on to gain
more expertise in Sinatra?

**Jeremy\>\>** Start with a small project. I’d recommend a basic web
site with a few pages, but the important thing is to pick something that
interests you.

**Satish\>\>** Could you suggest some web services that a Sinatra
beginner could develop himself / herself?

**Jeremy\>\>** A fairly simple one would be a proxy service where the
user can provide a URL and the Sinatra web service could retrieve the
page and return it to the user. A beginner would need to do some
research on Ruby’s standard library (**net/http**^[1](#fn-2574-1)^ or
**open-uri**), but the Sinatra code for a simple proxy service should
only be a few lines.

Another web service that a beginning Sinatra user could create would be
a URL shortener^[2](#fn-2574-2)^.

**Satish\>\>** Anything else you would like to add?

**Jeremy\>\>** The best way to learn is to have fun doing so, so pick
projects that interest you.

*Thank you Jeremy. In case you have any queries and/or questions, kindly
post your questions here (as comments to this blog post) and Jeremy
would be glad to answer.*

**Others in this series:**

-   [Corey
    Donohoe](http://rubylearning.com/blog/2015/01/07/corey-donohoe-how-do-i-learn-and-master-sinatra/)

***Post supported by 1st Easy Limited*:** UK based 1st Easy Limited
offer Sinatra and Rails hosting running on a Phusion Passenger
(mod\_rails) and LAMP stack. If you want to try your hand at developing
with Sinatra, why not let them arrange a [trial hosting
account](http://www.1steasy.com/ruby-on-rails.htm#try) for you? You’ll
get to deploy your app, with full technical support from their team!

1.  Read 14.20 A Real-World HTTP Client from the **Ruby Cookbook**.
    [↩](#fnref-2574-1)
2.  Read [Clone TinyURL in 40 lines of Ruby
    code](http://blog.saush.com/2009/04/clone-tinyurl-in-40-lines-of-ruby-code/).
    [↩](#fnref-2574-2)

