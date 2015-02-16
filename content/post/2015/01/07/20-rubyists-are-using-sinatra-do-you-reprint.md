---
title: '20+ Rubyists are using Sinatra &#8211; Do you? (Reprint)'
author: Satish Talim
date: 2015-01-07
layout: post
permalink: /2015/01/07/20-rubyists-are-using-sinatra-do-you-reprint/
thesis_description:
  - '20+ Rubyists are using Sinatra - Do you?'
thesis_keywords:
  - Rubyists Using Sinatra,Ruby Programming,Rubyists,Sinatra
topsy_short_url:
  - http://bit.ly/1HLdtAP
categories:
  - Beginners
  - Ruby
  - Sinatra
tags:
  - ruby programming
  - Rubyists
  - Rubyists Using Sinatra
  - Sinatra
---

**Note**: This first appeared on 29th June 2009 and is being reprinted
as the original is not accessible.

### 20+ Rubyists are using Sinatra – Do you?

With **Sinatra** you can quickly create your own tiny web-applications
in Ruby and write lots of small services. RubyLearning caught up with
some Rubyists working with Sinatra and asked them as to why, how and
where they use *Sinatra*.

![Aaron
Quint](http://rubylearning.com/images/AaronQuint.jpg "Aaron Quint")**[Aaron
Quint](http://twitter.com/aq)\>\>** I’ve been using Sinatra all over the
place. With [Vegas](http://code.quirkey.com/vegas/) I’ve been using it
as a way to provide simple web interfaces to existing code. I’ve also
been using it to prototype new application ideas. When not using
Sinatra, I’ve been using some of the same basic ideas in JavaScript with
[Sammy.js](http://code.quirkey.com/sammy/). In general, Sinatra is just
fun to use as it provides the most direct and clean route to get an idea
or a piece of code on the web. [Read Aaron’s interview on
Sinatra](http://rubylearning.com/blog/2009/03/20/interview-aaron-quint-on-sinatra/).

![Adam
Keys](http://rubylearning.com/images/AdamKeys.jpg "Adam Keys")**[Adam
Keys](http://twitter.com/therealadam)\>\>** I’m using Sinatra for two
things. For personal stuff, I always reach for Sinatra when I want to
prototype an idea. It’s easy to get something in place so I can iterate
on the idea quickly. Sinatra is great for deploying prototypes too!

At FiveRuns, we use Sinatra as the API endpoint for Dash. We’ve got
hundreds of clients in our public beta sending custom metrics to Dash
once a minute. Sinatra has handled this load with aplomb. Further,
because our API is just a few URL endpoints, Sinatra’s minimal API is a
perfect match for our needs. [Read Adam’s interview on
Sinatra](http://rubylearning.com/blog/2009/03/03/interview-adam-keys-on-sinatra/).

![Andrew
Neil](http://rubylearning.com/images/nelstrom-125.jpg "Andrew Neil")**[Andrew
Neil](http://twitter.com/nelstrom)\>\>** [All
Sorts](http://all-sorts.org/) searches Twitter every minute for the
[\#collectivenouns](http://search.twitter.com/search?q=%23collectivenouns)
hashtag, then parses matching tweets to identify collective nouns. The
requirements were very simple – no user log in, no CRUD, only a handful
of models and routes – so Sinatra was the perfect choice for this
project. I took Nick Plante’s
[retweet](http://github.com/zapnap/retweet/tree/master) source as a
starting point, which proved to be an excellent introduction to Sinatra
and DataMapper. Part of the appeal, of course, was to dabble with new
technologies. The live site runs on passenger, with Rack::Cache taking
care of the caching.

![Bruno
Miranda](http://rubylearning.com/images/bruno.jpg "Bruno Miranda")**[Bruno
Miranda](http://twitter.com/brupm)\>\>** I am using Sinatra on a url
shortner app that I wrote at [s.bopia.com](http://s.bopia.com/) as well
as a proxy app that processes beanstalkd queue items for
[mx.msn.cyloop.com](http://mx.msn.cyloop.com/). Sinatra is a great tool
to accomplish small tasks as a minimal layer on top of http protocol.

![Chris
Strom](http://rubylearning.com/images/chris_strom.jpg "Chris Strom")**[Chris
Strom](http://twitter.com/eee_c)\>\>** I am using Sinatra most
prominently to serve up my family’s cookbook, backed by a CouchDB store.
Excruciating details on how I do this are contained in a series of blog
posts starting with:
[http://japhr.blogspot.com/2009/03/my-chain.htm](http://japhr.blogspot.com/2009/03/my-chain.html).

I chose Sinatra because it felt close to the metal — especially
important because I did not want anything interfering with CouchDB. I
continue to use Sinatra because it complements my BDD workflow
exceedingly well. Sinatra’s lean DSL encourages me to produce similarly
beautiful code. Sinatra never gets in my way. Sinatra goes out of its
way to make my life simple.

![Corey
Donohoe](http://rubylearning.com/images/CoreyDonohoe.jpg "Corey Donohoe")**[Corey
Donohoe](http://twitter.com/atmos)\>\>** Sinatra is great for building
non-trivial rack middleware. [We’re mainly using
Sinatra](http://www.engineyard.com/) for integration applications
between existing pieces of software. Instead of working on a monolithic
app we’re writing a fleet of microapps to handle arising business needs.
We feel that Sinatra gets in the way less frequently than most other
frameworks. With cucumber and good development practices we’re using the
same top notch testing tools the Rails guys are using. In my [personal
hacking](http://atmos.org/index.php/about/) I’ve been using it as the
basis for twitter microapps leveraging twitter’s oauth API.

![Doug
Sparling](http://www.rubylearning.com/images/doug_sparling.jpg "Doug Sparling")**[Doug
Sparling](http://twitter.com/scriptrunner)\>\>** In my former company,
we had started using *Sinatra for web services* and in one instance, a
small app used for mobile advertising that doesn’t use the database.

​1) **Why?** – We don’t always need the full Rails stack, particularly
with web services and anything that doesn’t require the database. It’s
also useful for use with legacy databases, which we have to deal with. I
can use Datamapper, which is thread safe (though I haven’t seen any
performance issues with Rails, which we usually cache anyway).\
2) **How?** – We use Mongrel clusters for our Rails web sites, but with
the Sinatra apps we’re using Passenger. For our Sinatra web services, I
use Datamapper ORM. I have one internal web service in Rails 2.3.2, but
I’m looking at moving it to Sinatra as well.\
3) **Where?** – Mostly internal web services at the moment, but I’m sure
we’ll look at it for external services as well.

![Jeremy
Evans](http://rubylearning.com/images/jeremy-125.jpg "Jeremy Evans")**[Jeremy
Evans](http://code.jeremyevans.net/)\>\>** I use Sinatra on quite a few
projects, mostly for small applications. At work, we use it to handle
the dynamic portion of our mostly static public website, and for some
internal applications. Personally, I use it in
[Giftsmas](http://github.com/jeremyevans/giftsmas/tree/master), my open
source gift-tracking application, and in a couple of other sites I
maintain.

I use Sinatra because it is simple and flexible. It doesn’t require
boilerplate code, and lets you focus on the needs of your application.

![Graham
Ashton](http://www.rubylearning.com/images/graham-ashton.jpeg "Graham Ashton")**[Graham
Ashton](http://grahamashton.net/)\>\>** I first tried Sinatra during an
in house “hack week” at [Wordtracker](http://www.wordtracker.com/) (one
of my main Rails clients). We used Sinatra to great effect to throw up a
user interface for a new keyword research tool that we’d come up with
during hack week. Sinatra was very accessible – the docs are well
written and the mailing list is friendly. I quickly gained a lot of
confidence in the framework by reading the code, which is succinct and
easy to follow (I wish more projects would follow the advice of the
Linux kernel coding style and wrap their code at 80 columns – it
encourages legibility).

After that experience Sinatra was an obvious choice for Nesta, my [file
based CMS](http://effectif.com/nesta). It’s a simple app and Sinatra is
a perfect fit for it. I had the application up and running in a matter
of days, and I really enjoyed writing it. The goal of Nesta was to build
a CMS that people could easily modify to suit their own web sites, and
Sinatra makes it very easy for people to do that. There’s not a lot of
ceremony.

I still use Rails for larger apps, but I’m now turning to Sinatra first
whenever I want to try something out, or if I’m not sure where a new
application is going. It’s more fun.

![Hasham
Malik](http://rubylearning.com/images/hasham_small.jpg "Hasham Malik")**[Hasham
Malik](http://twitter.com/hasham2)\>\>** I have recently started
development with the Sinatra micro framework while working at
[CambridgeDocs](http://www.cambridgedocs.com/). Earlier we have used PHP
/ Ruby on Rails for server-side back ends of native iphone applications
that we have been developing. Sinatra lets you create REST based
services with minimalistic approach which is ideal of mobile back ends.
Sinatra is also lean and fast and at the same time it gives you the
liberty to use whichever ORM / templating system you want. Sinatra has
this positive vibe among Rubyists these days with 1.0 nearing its
release its great time to learn this new framework.

![James Edward Gray
II](http://grayproductions.net/images/james_headshot_square.jpg "James Edward Gray II")**[James
Edward Gray II](http://twitter.com/JEG2)\>\>** At [Highgroove
Studios](http://highgroove.com/), Sinatra is a vital part of the
architecture of our monitoring application,
[Scout](http://scoutapp.com/). We provide the API the agents use to
check-in with data via the micro framework. This is nice because it
separates the two functions of the application, allowing us to do things
like deploy an application update without interrupting the API service.
Still Sinatra gives us a touch more abstraction than something like
Rails Metal would and that makes working on the API a little easier.

![Jeremy
Raines](http://rubylearning.com/images/face_small2.jpg "Jeremy Raines")**[Jeremy
Raines](http://twitter.com/jraines)\>\>** I’m a web developer in Park
City, Utah. I got started using Sinatra because I was interested in REST
and I like the way Sinatra maps controller actions to HTTP verbs. I also
love its lightweight simplicity. It’s great for doing small API based
webapps and mashups. Most of my Sinatra apps use Ruby scripts fired by
cron jobs to pull data from other webservices into a SQLite database,
and serve content with Sinatra. I’ll be using it more in my work with
Purple Raincloud, a new social media consultancy here in Utah. I’m
@jraines on Twitter, and my homepage is at
[jeremyraines.com](http://jeremyraines.com/).

![Julio Javier
Cicchelli](http://www.rubylearning.com/images/jjcicchelli.jpg "Julio Javier Cicchelli")**[Julio
Javier Cicchelli](http://twitter.com/monsieur_rock)\>\>** First of all,
I like the idea to write about Sinatra and, especially, to show its
practical uses to the masses. There are a whole lot of Rails developers
but nobody seems to be taking Sinatra quite seriously (at least, this is
what I’ve been noticing in websites such as
[jobs.rubynow.com](http://jobs.rubynow.com/)).

I’ve just founded a company called “[Rock &
Code](http://rock-n-code.com/)” in Amsterdam, The Netherlands that
offers solutions developed on Sinatra (instead of Rails or even Merb) to
my partners. Why you would ask? Sinatra have definitely broken the MVC
paradigm (widely implemented by frameworks such as Rails, Merb, Django,
Spring, etc.) and decided to give total control back to the developer by
allowing him to build almost any kind of web-based solution (no matter
the complexity) in a very simple manner on top of the abstracted HTTP
layer it implements from Rack. Furthermore, Sinatra applications can
make use of the existing gem library instead of consuming plug-ins
specifically-designed for a particular framework. How my company is
using Sinatra? I’m currently developing RESTful web services that uses
CouchDB and communicates with clients written in both MacRuby and iPhone
(in the near future) using JSON but I’ve planned to use Sinatra in web
development and also server interfacing. Where can it be applied? I
believe that Sinatra suits perfectly for prototyping, client-server
applications, SOA applications and interfacing servers, for starters.

![Karel
Minarík](http://www.rubylearning.com/images/karmi_mugshot.jpg "Karel Minarík")**[Karel
Minarík](http://twitter.com/karmiq)\>\>** Sinatra powers [my
blog](http://www.restafari.org/), deployment automation, internal apps
and is generally the tool of choice whenever I need to build a web app
without overhead. Sinatra excels when doing “freestyle coding” — it’s a
sort of a blank canvas: you’re bound only by HTTP and your Ruby
knowledge. Sinatra doesn’t force anything on you, which can lead to
awesome or evil code, in equal measures — and that’s part of its charm
to me. Sinatra exposes you to Rack intensely, though, which brings
rather different mindset for building web applications then the
prevailing “monolithic” style. See eg.
[www.github.com/rack/rack-contrib](http://github.com/rack/rack-contrib/tree/master)
for inspiration.

**[Markus Prinz](http://twitter.com/cypher)\>\>** I use Sinatra because
it concentrates on one area, and does that very well, leaving the rest
up to me. So whenever I have some idea that requires a web app, I can
try it out very quickly with Sinatra with a minimum of fuss. And since
Sinatra is not a one-size-fits-all solution, but instead essentially a
library, I have a great deal of flexibility in using it. That means I
can try out new approaches to things like data storage, and use
something like Tokyo Cabinet/Tokyo Tyrant or CouchDB instead of a
relational database. But I can also use Sinatra as a component in a
larger application to offer a web interface, without interfering with
the rest of the application.

![Matt
Todd](http://highgroove.com/images/about/mtodd.jpg "Matt Todd")**[Matt
Todd](http://twitter.com/mtodd)\>\>** We at @highgroove ([Highgroove
Studios](http://highgroove.com/)) use Sinatra in a lot of different
projects for memory-efficient web services. One of our products,
[Scout](http://scoutapp.com/) (@scoutapp) uses it to consume thousands
of reports constantly. We are able to fine tune our stack with Sinatra
to keep it minimal, responsive, and powerful.

Highgroove Studios is Charles Brian Quinn (@seebq), Derek Haynes
(@dhaynes23), Andre Lewis (@alewis), James Edward Gray II (@JEG2), and
myself, Matt Todd (@mtodd).

![Nick
Plante](http://www.rubylearning.com/images/nap.jpg "Nick Plante")**[Nick
Plante](http://twitter.com/zapnap)\>\>** We’re using Sinatra for a
variety of small web sites and services. Why? Because Sinatra is small,
RESTful, fast, and intuitive. It’s perfect for lightweight apps and
APIs.

One of our sites, [rdoc.info](http://rdoc.info/), uses it to generate
and host documentation for a variety of Ruby libraries, integrating with
GitHub web hooks to automatically regenerate docs whenever projects are
updated. We could have used Rails, but the additional overhead, helpers,
and other extras that come pre-packaged with it just weren’t necessary.
In fact, they would have probably gotten in our way.

[Tweetdreams](http://tweetdreams.org/) is another small Sinatra-based
project that we launched earlier this year. It’s a Twitter dream
journal. There really isn’t much to it, which is sort of the beauty of
it. The source is available on GitHub as
“[retweet](http://github.com/zapnap/retweet/tree/master)” and it’s been
used as the basis for a number of other Twitter-oriented projects
including the [http://all-sorts.org](http://all-sorts.org/) linguistic
experiment created by Andrew Neil.

I should note that both of these projects use DataMapper and Haml, too.
Sinatra is ORM and templating language agnostic, which can be another
bonus if you already have a predefined set of tools that you’re familiar
with and want to use.

![Peter
Cooper](http://www.rubylearning.com/images/petercooper.jpg "Peter Cooper")**[Peter
Cooper](http://twitter.com/peterc)\>\>** As I don’t work on big
projects, I’m using Sinatra for everything now, where I would have used
Rails before. It’s nearly all local or private stuff for now but I’d
like to be able to release more community projects using it in due
course. I love Sinatra because it’s less opinionated and more Ruby-like
than Rails. It might take me a little longer to achieve certain results
but I can “plug and play” code, libraries, and frameworks wherever I
like with it, rather than have to work around tightly coupled
“conventions.”

![Piyush
Gupta](http://www.rubylearning.com/images/PiyushGupta.jpg "Piyush Gupta")**[Piyush
Gupta](http://twitter.com/mba_piyush)\>\>** When your application is
small, Sinatra helps us to develop applications quickly and easily.
Sinatra is easy to understand and follow. We have recently used it for a
twitter mashup called MillionTwitter Follower which is not yet live.
Expecting it to be live soon.

![Sam
Goebert](http://www.rubylearning.com/images/sam.jpg "Sam Goebert")**[Sam
Goebert](http://twitter.com/bigcurl)\>\>**
[Bigcurl](http://www.bigcurl.de/) uses Sinatra to power its [HTTPush
API](http://www.httpush.com/), which is a hosted gateway to the Apple
Push Notification Service. Our complete api frontend is implemented
using Sinatra. This gave us a tremendous boost during development of the
API specification. We were able to experiment more as the code has very
few lines. Second reason we went with Sinatra was memory consumption,
since we span lot of instances over the course of a day this was crucial
to get the maximum out of a machine but maintaining the beauty in code.

![Sau Sheong
Chang](http://www.rubylearning.com/images/sau.jpg "Sau Sheong Chang")**[Sau
Sheong Chang](http://twitter.com/sausheong)\>\>** I picked up Sinatra
first when I was writing my [search
engine](http://blog.saush.com/2009/03/write-an-internet-search-engine-with-200-lines-of-ruby-code/)
and I was looking for a simple way to write my search engine interface.
The simplicity of Sinatra blew me away and I was soon knee-deep into
writing more apps on Sinatra. After a few more applications, I was
convinced that Sinatra is the way to write web applications as it is
meant to be. Today I use it to write quick and simple web applications,
often in combination with DataMapper, that serve as front-end interfaces
for larger systems.

![Saurabh
Purnaye](http://www.rubylearning.com/images/saurabhpurnaye.jpg "Saurabh Purnaye")**[Saurabh
Purnaye](http://twitter.com/saurabhp)\>\>** I work for Synechron, Pune.
The applications we create are mostly UI based (html/css/jquery and
flex), and I need web services to respond to the calls from UI – that’s
where I use Sinatra. Sinatra is really fast and easy for providing
RESTful web service solutions. There are many options while working with
Sinatra – for example Database: ORM (datamapper/active record),
Templating: (erb/haml/builder), http caching, filters, helpers and error
handling. One of it’s best features is it comes with Rack middleware.
For the last 6 months I am using Sinatra and I feel very happy to work
with it.

### Do YOU use Sinatra?

[![Twitter](http://ad.ly/static/images/referral/square.gif)](http://ad.ly/refer/2014322399)

If you are a Rubyist using Sinatra, *we would like to know as to why,
how and where you are using Sinatra*. Post this as a blog comment.
Thanks.

***Post supported by 1st Easy Limited*:** UK based 1st Easy Limited
offer Sinatra and Rails hosting running on a Phusion Passenger
(mod\_rails) and LAMP stack. If you want to get to know them first, or
simply want to try out your Sinatra or Rails skills, [let them arrange a
free trial hosting
account](http://www.1steasy.com/ruby-on-rails.htm#try) for you – full
technical support from their team is included!

Technorati Tags: [Rubyists Using
Sinatra](http://technorati.com/tag/Rubyists+Using+Sinatra), [Ruby
Programming](http://technorati.com/tag/Ruby+Programming),
[Rubyists](http://technorati.com/tag/Rubyists),
[Sinatra](http://technorati.com/tag/Sinatra)
