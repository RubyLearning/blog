---
draft: false
title: 'Karel Minarik: How do I learn and master Sinatra?'
date: 2009-07-13
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
permalink: /2009/07/13/karel-minarik-how-do-i-learn-and-master-sinatra/
tags:
- Karel Minarik
- Learning Sinatra
- ruby programming
- Sinatra
---
Welcome to the **fourth** installment on the RL blog, of a mini series –
“**How do I learn and master Sinatra?**” – by top Rubyists using
*Sinatra*. The interview series will provide insight and commentary from
these notable *Sinatra* developers, with the goal of facilitating and
providing answers to the questions Ruby beginners face on *how to learn
and master Sinatra*.<!--more-->

**Satish\>\>** Karel Minarik, could you tell us something about yourself
– your background, where you are based?

![Karel
Minarik](http://www.rubylearning.com/images/karmi_mugshot.jpg "Karel Minarik")**Karel
Minarik\>\>** I’m Karel Minarik, web designer and developer living in
Prague, Czech Republic. I have graduated in Philosophy, not Computer
Science, which may explain why I love Ruby a lot, and why I prefer
solving “naming things” over “cache invalidation” problems. I earn my
bread by designing interfaces, writing Ruby, JavaScript, HTML/CSS and
giving people advice or teaching them new tricks. I blog in
undecipherable intervals on [Restafari.org](http://www.restafari.org/)
and publish code regularly at [Github](http://github.com/karmi/).

**Satish\>\>** Are there any pre-requisites for a person to start
learning Sinatra?

**Karel\>\>** Very few: you just need to know Ruby a little bit. The
rest you can and will learn along the way. In fact, Sinatra is wonderful
teaching tool to deepen your knowledge of Ruby as a general programming
language, web application architectures, HTTP and REST principles,
concept of middlewares, and so on. As a wonderful teaching/learning tool
it’s truly on par with \_why’s Shoes.

**Satish\>\>** How should one start learning Sinatra?

**Karel\>\>** You should start with the
[README](http://github.com/sinatra/sinatra/blob/master/README.rdoc),
which contains almost everything you need to know in its 500 or so
lines. Then you should definitely glance over sourcecode of some Sinatra
applications “[in the wild](http://www.sinatrarb.com/wild.html)“.

Some of the noteworthy examples would be eg. simple website in
waferbaby’s
[usesthis](http://github.com/waferbaby/usesthis/tree/master), background
processing tutorial in bmizerany’s
[sinatra-dj](http://github.com/bmizerany/sinatra-dj/tree/master), clever
use of Ruby’s blocks/closures in pjhyett’s
[github-services](http://github.com/pjhyett/github-services/tree/master)
or ultra minimal apps in ichverstehe’s
[gaze](http://github.com/ichverstehe/gaze/blob/master/bin/gaze) or
gnugeek’s [tophat](http://github.com/gnugeek/tophat/tree/master). These
examples really elucidate compact and minimal nature of Sinatra.

Then you should sketch something rather small and well defined: web
frontend for some Ruby code you have, a web API for some of your
services, …

> Sinatra – quickly create tiny web apps and services

**Satish\>\>** Which area of Sinatra should a beginner pay particular
attention to?

**Karel\>\>** Beginners should pay attention to Sinatra’s DSL itself:
helpers, filters, last\_modified and etag support, etc, so they’re not
reinventing the mic and truly make use of it’s API. More advanced
programmers should focus on Rack integration, using Rack middlewares
such as **Rack::Auth** or **Rack::Mime** in your Sinatra app and running
Sinatra apps themselves as middlewares. This opens different
possibilities of service integration – have a look on Jon Crosby’s
wonderful explanation in his [MWRC
talk](http://mwrc2009.confreaks.com/13-mar-2009-11-05-in-a-world-of-middleware-who-needs-monolithic-applications-jon-crosby.html).

**Satish\>\>** Is the official documentation on Sinatra good enough for
a beginner? Are there areas which need improvement or need to be
re-written

**Karel\>\>** Sinatra’s
[documentation](http://www.sinatrarb.com/documentation.html) is pretty
extensive at the moment, covering everything from basics to testing your
applications and writing extensions. It’s just a bit scattered at the
moment, eg. deployment is covered in the [Sinatra
Book](http://www.sinatrarb.com/book.html#deployment) started by Chris
Schneider. There’s still some lack of thorough documentation about Rack
integration.

**Satish\>\>** Sequel, DataMapper, ActiveRecord – which one would you
recommend to use with Sinatra and why?

**Karel\>\>** I prefer ActiveRecord for anything talking to a relational
database, because of it’s clever API, stability, general knowledge and
large user base. Don’t forget that Sinatra is nice playground for
experiments with other ORM’s, key/value stores, etc, though!

![Sinatra
Icon](http://rubylearning.com/images/sinatralogo.jpg "Sinatra micro-framework")

**Satish\>\>** Is an understanding of Rack important while learning
Sinatra? Why? Which area of Rack should one be really comfortable with?

**Karel\>\>** No, you could start learning Sinatra completely oblivious
of something called “Rack”.

However, you can use plethora of various
[bundled](http://rack.rubyforge.org/doc/Rack.html) or
[third-party](http://github.com/rack/rack-contrib) Rack middlewares very
easily by simple ‘**use Rack::Utils**‘ or ‘**use Rack::Locale**‘
declaration for adding some advanced functionality to your application.

And when you plan to plug Sinatra powered app into a Rails one, for
instance, or want to “mount” various separated web applications at
different endpoints, you should definitely have a detailed look on Rack
itself.

**Satish\>\>** How should one hone one’s skills in Sinatra?

**Karel\>\>** By reading huge amounts of code available on Github.
That’s a sure way how to discover clever solutions and open your mind.
(Be sure to include credits if you reuse some code and release your
stuff, though.)

But the most important thing is to focus on Ruby as an expressive
programming language, and to \_not\_ think about browser first. Think
first about the domain of your application and how it translates to
Ruby, not about how it should “look” or behave in a browser. That’s very
important, but comes next. And don’t forget it’s really easy to code
test-first in Ruby and in Sinatra.

**Satish\>\>** What type of projects should a beginner work on to gain
more expertise in Sinatra?

**Karel\>\>** Smallish apps, where Rails would force it’s conventions on
you or which are not primarily focused on database access. Something
like cschneid’s [irclogger](http://irclogger.com/), quirkey’s
[columnlog](http://log.quirkey.com/) or entp’s [Calendar About
Nothing](http://calendaraboutnothing.com/) — all very tight, minimal and
very elegant apps.

**Satish\>\>** Could you suggest some web services that a Sinatra
beginner could develop himself / herself?

**Karel\>\>** The sweet spot for Sinatra is something along the lines of
already mentioned apps. Some ideas I could throw in:

-   An app to display metrics about your team activity in a Git
    repository: who commited most, who commited most lines of code,
    etc., leveraging power of [Grit](http://github.com/mojombo/grit).
-   A web frontend for some command-line tool like ‘top’ or ‘df’ for
    your servers.
-   Simple web hook for [Github’s post-receive
    hooks](http://github.com/guides/post-receive-hooks), notifiying your
    developer mailing-list, Jabber, deploying new code to staging server
    or playing a tune.
-   More advanced example could be an app to show currently deployed
    versions of your applications, using small Sinatra apps on each host
    to emit various metrics like deployed revision and it’s age, system
    load, etc in JSON and a Sinatra app to gather the data — “emulating”
    services like NewRelic, Scout or FiveRun’s Dash.

**Satish\>\>** Anything else you would like to add?

**Karel\>\>** Do come to the \#sinatra IRC channel on Freenode when you
get stuck. There’s usually lots of people from different timezones, so
it’s very likely that we’ll get you out of trouble fast. Just please
read the README first and don’t name your application file “sinatra.rb”
![:)](http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif)
Have fun with Ruby and Sinatra!

*Thank you Karel. In case you have any queries and/or questions, kindly
post your questions here (as comments to this blog post) and Karel would
be glad to answer.*

**Others in this series:**

-   [Corey
    Donohoe](http://rubylearning.com/blog/2009/07/06/how-do-i-learn-and-master-sinatra/)
-   [Jeremy
    Evans](http://rubylearning.com/blog/2009/07/08/jeremy-evans-how-do-i-learn-and-master-sinatra/)
-   [Graham
    Ashton](http://rubylearning.com/blog/2009/07/10/graham-ashton-how-do-i-learn-and-master-sinatra/)

***Post supported by 1st Easy Limited*:** UK based 1st Easy Limited
offer Sinatra and Rails hosting running on a Phusion Passenger
(mod\_rails) and LAMP stack. If you want to try your hand at developing
with Sinatra, why not let them arrange a [trial hosting
account](http://www.1steasy.com/ruby-on-rails.htm#try) for you? You’ll
get to deploy your app, with full technical support from their team!

