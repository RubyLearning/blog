---
draft: false
title: Happynerds - Programming Links for Kids
date: 2009-12-21
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/rubylearning
categories:
- heroku
- ruby
- sinatra
layout: post
permalink: /2009/12/21/happynerds-programming-links-for-kids/
tags:
- happynerds
- michael kohl
- ruby
- the ruby programming language
---
**A guest post by [Michael Kohl](http://citizen428.net)**.<!--more-->

![Michael Kohl](http://rubylearning.com/images/michael_kohl.jpg "Michael Kohl")
For quite some time I was planning to create an online resource of
programming tools for kids, because I think developing software is a
beautiful and rewarding experience which is a perfect fit for children’s
natural curiosity. Alas time is always short, so up until recently all I
did was to collect links on [delicious](http://delicious.com) and wait.

Then two weeks ago I went through my personal todo list and realized
that this idea has been sitting around for way too long, so I decided to
finally do something about it. Thanks to the wonderful tools the Ruby
community provides us with, all it took was this initial spark of
motivation and an afternoon of free time to finally create **[Happy
Nerds](http://www.happynerds.net)**.

Happy Nerds is a very small and simple site, so it seemed like a perfect
match for the wonderfully elegant
**[Sinatra](http://www.sinatrarb.com/)** DSL for web applications. I’m
constantly amazed by how productive and *fun* development with Sinatra
can be, especially when used together with the right tools like
**[Shotgun](http://github.com/rtomayko/shotgun)** and
**[Haml](http://haml-lang.com/)**.

Before starting to code I obviously also had to decide where to host the
site once it’s finally done, and **[Heroku](http://heroku.com/)** just
seemed like the most natural choice, due to its excellent support for
everything related to Ruby web frameworks (Need gems? [No
problem!](http://docs.heroku.com/gems)), a very streamlined
[git](http://git-scm.com/)-based workflow and excellent command line
tools. I also wrote a patch to add the –heroku option to
[sinatra-gen](http://github.com/quirkey/sinatra-gen) a while back, so I
was literally up and running within seconds.

Now all that was left to decide was the data store.
**[MongoDB](http://www.mongodb.org/)** had been on my radar for a long
time and I got myself an invite to [MongoHQ](http://www.mongohq.com/)‘s
beta program some weeks back, so this seemed like a good opportunity to
finally give both of them a try. As it turned out, they are as fun to
work with all the other projects mentioned so far!

Once I decided which exact tools to use, creating the actual application
was almost too easy. I started by writing a small Ruby script which
fetched the appropriately tagged bookmarks from delicious (where I
stored name, URL and description) and fed them into MongoDB. After that
all it took was a couple of very simple Sinatra “controllers” and the
actual views, which thanks to Haml also were breeze to create.

So even as somebody who usually doesn’t do web application development,
I had a first functioning version within an afternoon and a finished
site within two. Granted, [Happy Nerds](http://www.happynerds.net) is
very simple at the moment, but I just wanted to finally get the idea out
into the open. I do have a couple of ideas for the future though and
thanks to the used technologies I feel confident that implementing them
will be easy and fun once I get around to do it!

