---
draft: false
title: 'Nick Plante: How do I learn and master Sinatra?'
date: 2009-07-17
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
permalink: /2009/07/17/nick-plante-how-do-i-learn-and-master-sinatra/
tags:
- Learning Sinatra
- Nick Plante
- ruby programming
- Sinatra
---
Welcome to the **sixth** installment on the RL blog, of a mini series –
“**How do I learn and master Sinatra?**” – by top Rubyists using
*Sinatra*. The interview series will provide insight and commentary from
these notable *Sinatra* developers, with the goal of facilitating and
providing answers to the questions Ruby beginners face on *how to learn
and master Sinatra*.<!--more-->

**Satish\>\>** Nick Plante, could you tell us something about yourself –
your background, where you are based?

![Nick
Plante](http://www.rubylearning.com/images/nap.jpg "Nick Plante")**Nick
Plante\>\>** I’m Nick Plante, a freelance web app developer living in
Portsmouth, NH — USA. I’ve been doing application development
professionally for quite some time, but I don’t think I really ever
enjoyed it all that much until I found Ruby, which was about 3 years ago
now. I do client work for startups and small businesses and we work on
incubating our own projects too. I’m also involved in a bunch of
community stuff such as working as an organizer for the Rails Rumble
event. In my spare time, I enjoy film, comics, travel, loud droning
music, racquetball and mountain biking.

**Satish\>\>** Are there any pre-requisites for a person to start
learning Sinatra?

**Nick\>\>** A basic understanding of HTTP verbs would be useful. It
would certainly help to have a firm grasp on Ruby too. But honestly,
it’s not really that important. Writing a Sinatra application is a good
way to learn Ruby itself, if you’re focused on web-based projects. It’s
not large enough to be overly complex or unwieldy, and is easily
understood. For example, I’d recommend that a person learn Sinatra
before attempting to use Rails for a project, and for a lot of people,
Rails is their first experience with Ruby.

**Satish\>\>** How should one start learning Sinatra?

**Nick\>\>** Start by looking at the Sinatra official site; the README
there is well written and very brief, and will teach you most of what
you need to know. Sinatra isn’t a huge framework with all sorts of
esoteric methods, so it’s easy to get started. I’d next suggest that you
check out the list of Sinatra applications “in the wild”; many of these
are open source (including several of my own projects).

I’m a firm believer that the best way to learn a framework is to find
practical small-scope examples to look at, and there are plenty of these
for Sinatra now — just check GitHub. Once you understand the basics,
pick something you’re interested in that’s relatively minimalist and
start coding. The docs and the community are there to help you when and
if you need help.

> Sinatra – quickly create tiny web apps and services

**Satish\>\>** Which area of Sinatra should a beginner pay particular
attention to?

**Nick\>\>** Start with the basics; Sinatra’s RESTful syntax is a joy to
work with. Stay practical. Once you’ve got that down, spend some time
playing around with Rack itself. Understand how it works and how you can
write and use middleware.

**Satish\>\>** Is the official documentation on Sinatra good enough for
a beginner? Are there areas which need improvement or need to be
re-written

**Nick\>\>** I think it’s fine. The micro-site / README is a great read
and the Sinatra book is another option. Since Sinatra is relatively
unopinionated about your choice of ORM, templating language, testing
framework, javascript library, etc — you’ll get to make your own choices
about what you use. The documentation there will probably be worse than
Sinatra’s own ;-).

**Satish\>\>** Sequel, DataMapper, ActiveRecord – which one would you
recommend to use with Sinatra and why?

**Nick\>\>** Whichever one you personally like the best, or are most
familiar with. I’m a big fan of DataMapper for several reasons, although
it’s documentation (see previous question) admittedly leaves a bit to be
desired. If you’ve already got a background with Rails, ActiveRecord
might be a better place to start. Use what you know and learn one new
thing at a time. Once you’re comfortable with Sinatra try experimenting
with something different to see how it works for you.

![Sinatra
Icon](http://rubylearning.com/images/sinatralogo.jpg "Sinatra micro-framework")

**Satish\>\>** Is an understanding of Rack important while learning
Sinatra? Why? Which area of Rack should one be really comfortable with?

**Nick\>\>** I don’t think you really need to know much of anything
about Rack to start using Sinatra, other than how to write a rackup file
(which is easy and well documented; you can pretty much copy and paste).
However, if you do know Rack you’ve got a lot of advantages, and I’d
recommend learning it. There’s some really powerful middleware out there
like Rack::Cache that can save you from reinventing the wheel when you
need the extras that aren’t already baked-in.

**Satish\>\>** How should one hone one’s skills in Sinatra?

**Nick\>\>** Practice makes perfect. Pick an idea you’re interested in
and build it. You can also learn a lot by looking at other peoples’
work.

**Satish\>\>** What type of projects should a beginner work on to gain
more expertise in Sinatra?

**Nick\>\>** Small ones that do one simple task and do it well. Focus on
writing tight elegant code that leverages Sinatra’s RESTful DSL. Don’t
forget to use Rack::Test to write tests for your application.

**Satish\>\>** Could you suggest some web services that a Sinatra
beginner could develop himself / herself?

**Nick\>\>** Write a minimalist time tracker or a pastebin service or
something else similarly small in scope. Sinatra is great for creating
micro-apps; maybe spend some time thinking about how you could leverage
the Twitter API. Also, consider building services that are entirely web
APIs and don’t need a traditional HTML frontend. Sinatra really excels
for that sort of thing.

**Satish\>\>** Anything else you would like to add?

**Nick\>\>** Whatever you do, just remember to have fun doing it. We’re
all better developers when we’re working with technologies and tools
that we enjoy, and creating things that we’re personally passionate
about. For me, working on Sinatra-based apps is a lot of fun. It’s not
the right choice for everything, and I definitely favor Rails for
certain types of applications, but for creating small clean micro-apps
it’s hard to beat imo.

*Thank you Nick. In case you have any queries and/or questions, kindly
post your questions here (as comments to this blog post) and Nick would
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

***Post supported by 1st Easy Limited*:** UK based 1st Easy Limited
offer Sinatra and Rails hosting running on a Phusion Passenger
(mod\_rails) and LAMP stack. If you want to try your hand at developing
with Sinatra, why not let them arrange a [trial hosting
account](http://www.1steasy.com/ruby-on-rails.htm#try) for you? You’ll
get to deploy your app, with full technical support from their team!

