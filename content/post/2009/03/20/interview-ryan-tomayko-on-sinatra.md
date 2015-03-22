---
draft: false
title: 'Interview: Ryan Tomayko on Sinatra'
date: 2009-03-20
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/rubylearning
categories:
- Heroku
- Interview
- Ruby
- Sinatra
description:
- Ryan Tomayko key developer for Sinatra talks to RubyLearning on Sinatra micro web-framework.
keywords:
- Ryan Tomayko,Interviews,Ruby,Sinatra,The Ruby Programming Language
layout: post
permalink: /2009/03/20/interview-ryan-tomayko-on-sinatra/
tags:
- interviews
- Ruby
- Ryan Tomayko
- Sinatra
- The Ruby Programming Language
---
On the eve of the first ever online “**Introduction to Sinatra**”
course, Satish Talim of RubyLearning caught up with **Ryan Tomayko** and
talked to him on **Sinatra**, in this interview.

![Ryan Tomayko,
USA](http://rubylearning.com/images/RyanTomayko.jpg "Ryan Tomayko, USA")

**Satish Talim\>\>** Welcome, Ryan and thanks for taking out time to
share your thoughts. For the benefit of the readers, could you tell us
something about your self?

**Ryan Tomayko\>\>** My background is in systems design and general web
architecture — HTTP, REST, and “web services” primarily. I’ve been
involved in the Ruby web development community for a little over three
years and have contributed to Rails, Rack, Sinatra, and a bunch of other
tools and libraries. I live, work, and play in San Francisco, am happily
married, and have two crazy kids with totally awesome websites
([http://lydia.tomayko.com/](http://lydia.tomayko.com/) and
[http://elijah.tomayko.com/](http://elijah.tomayko.com/)).

You can follow me on Twitter
([http://twitter.com/rtomayko](http://twitter.com/rtomayko)) and find
out more about me at my blog
([http://tomayko.com/about](http://tomayko.com/about)).

> Sinatra’s greatest strength is its flexibility

**Satish\>\>** You are one of the lead developers of Sinatra and work at
Heroku. How come you got involved with Sinatra? Tell us more about this.

**Ryan\>\>** I’ve been an advocate for standards based web development
for quite some time, with a particular focus on server-side web
frameworks. In 2005, I wrote an article titled “On HTTP Abuse”
([http://tomayko.com/writings/on-http-abuse](http://tomayko.com/writings/on-http-abuse))
to make the case that the tools we were using to build web applications
were basically… horrible. I also outlined some of the traits I felt
would be present in a good web framework. We’ve made a lot of progress
since then (Rails, for instance, has fully embraced REST and HTTP), but
when I saw what Blake Mizerany had put together in Sinatra, I was blown
away by how closely it resembled the framework I had imagined in my head
when I was writing that article in 2005.

I was hooked and have been fairly active in the project ever since.

**Satish\>\>** What’s your role at Heroku?

**Ryan\>\>** I’ve been going under the working title of “Product
Designer / Architect” but we like to think of ourselves as curators of
technology more than anything. My job is to understand where the Ruby
community is going, to play with the tools and technologies people are
using to get there, and then to make it an order of magnitude easier for
them to be used on Heroku than anywhere else
![:)](http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif)

**Satish\>\>** So many Ruby-based web frameworks – is this good for
Ruby?

**Ryan\>\>** I can’t think of a better situation than the one we have
now, to be honest. Rails is the premier general purpose web development
platform – perfectly suited to a wide range of applications. It’s taken
many of the best practices established by not only the Ruby community
but the web development community in general and made them accessible to
everyone. It’s maturing rapidly, is well documented, and has a large
(but not too large!) community. Rails has become a “safe bet”.

The web is very young, though. There’s still a lot of stuff we’ve yet to
figure out. Frameworks like Merb, Ramaze, Camping, Waves, etc. have a
bit more freedom to experiment with alternative designs and philosophies
or to focus more narrowly on achieving specific goals that might be off
the radar for Rails. There’s very little downside to competition here
(the talk about Rails vs. Merb “tearing the community apart” was mostly
overblown in my estimation). Without this diversity, web development in
Ruby might stagnate a bit.

Sinatra is unique in many ways. In my opinion, Rails and Sinatra aren’t
really competitors in any kind of head-to-head sense. Once you’ve become
familiar with both environments, I think you’ll find that each has a
clear sweet spot and that choosing one over the other is all about using
the best tool for the job. It’s hammer vs. saw as opposed to Craftsmen
vs. Stanley. Using Sinatra to build a traditional CRUD app with 10-15
models and a mostly-HTML-with-some-Ajax front-end is going to feel a bit
wonky compared to Rails. Conversely, using Rails as the server component
in a collaborative, browser-based map/reduce system
([http://www.igvita.com/2009/03/03/collaborative-map-reduce-in-the-browser/](http://www.igvita.com/2009/03/03/collaborative-map-reduce-in-the-browser/))
is going to feel like overkill. Look at some of the apps in the wild
that were built with Sinatra
([http://www.sinatrarb.com/wild.html](http://www.sinatrarb.com/wild.html))
and imagine what they might look like if they had been implemented in
Rails. I think the distinction is clear and the benefits of having
multiple specialized frameworks obvious.

**Satish\>\>** For a person new to web development, how can one go about
learning Sinatra?

**Ryan\>\>** For a person just starting out with web development in
general, I’d suggest something extremely simple and well-understood – a
blog or TODO list, maybe. Choose something that has a lot of prior art
so you can reference how the different resources are linked together and
how the browser and server interact. One thing that sets Sinatra apart
from most web frameworks is that it does not try to hide the web’s basic
concepts and protocols from the developer. We believe that a strong
understanding of HTTP, URLs, and the various media types/formats (HTML,
CSS, JSON/JavaScript, RSS, etc) that make the web work is required to
build good web applications. The more you get comfortable with those
concepts, the more Sinatra will make sense to you.

Once you know what you want to build, the only thing to do is to start
writing code – one line at a time. The Sinatra website has a good
introduction
([http://www.sinatrarb.com/intro.html](http://www.sinatrarb.com/intro.html))
that covers most of the basic features supported by framework at a high
level. From there, you might move on to some of the more detailed
documentation
([http://www.sinatrarb.com/documentation.html](http://www.sinatrarb.com/documentation.html))
or watch the “Classy Web Development with Sinatra” screencasts
([http://www.pragprog.com/screencasts/v-aksinatra/classy-web-development-with-sinatra](http://www.pragprog.com/screencasts/v-aksinatra/classy-web-development-with-sinatra)).

This part is important. Eventually, you’re going to run into a problem
that you don’t know how to solve or something that doesn’t make any
sense at all. When that happens, be sure to either send something to the
Sinatra mailing list
([http://groups.google.com/group/sinatrarb](http://groups.google.com/group/sinatrarb))
or drop by \#sinatra on irc.freenode.net. There’s a large group of
insanely smart developers that are more than happy to help out. It
doesn’t matter how “stupid” the problem is – just ask. This is actually
a very real way of contributing to the project. Those discussions are
archived and searchable via Google so, by asking, you make it easier for
the next person to find their way when they have a problem.

![Sinatra
Icon](http://rubylearning.com/images/sinatralogo.jpg "Sinatra micro-framework")

**Satish\>\>** Where all can Sinatra be used? What kind of projects
should a person learning Sinatra work on?

**Ryan\>\>** Sinatra is a perfect fit for smaller apps/services, APIs,
and sites that are mostly static but with some light server
interactions. There’s a big list of Sinatra apps on the website
([http://www.sinatrarb.com/wild.html](http://www.sinatrarb.com/wild.html)),
most of which have source code available on the GitHub.

**Satish\>\>** Any plans on writing a book on Sinatra?

**Ryan\>\>** Book?! We’re still working on the README!
![;)](http://rubylearning.com/blog/wp-includes/images/smilies/icon_wink.gif)

There’s a community effort underway to produce a free, online book
that’s coming along quite nicely:
[http://www.sinatrarb.com/book.html](http://www.sinatrarb.com/book.html).

As for me personally, I don’t own a single tech book so it would seem
unusual for me to produce one. I wouldn’t be surprised if someone else
put a book together at some point in the near future, though.

**Satish\>\>** Since you are closely involved with both Sinatra and
Heroku and most of the course participants have no Rails background,
could you tell us in simple terms how one can deploy a simple Sinatra
CRUD app on Heroku?

**Ryan\>\>** How about a quick and dirty wiki?

1.  Sign up for a Heroku account at:
    [http://heroku.com/](http://heroku.com/)
2.  Install the heroku gem on your local machine (this will also install
    the Sinatra, Sequel, and Sqlite3-ruby gems as dependencies):\
    `$ sudo gem install heroku`
3.  Create a directory for the wiki app and initialize a git
    repository:\
    `$ mkdir wiki<br />$ cd wiki<br />$ git init<br />Initialized empty Git repository in .git/`
4.  Create a new heroku application. You will be prompted for your
    heroku email address and password (this is required the first time
    you create an app only):\
    `$ heroku create<br />Enter your Heroku credentials<br />Email: joe@example.com<br />Password:<br />Uploading ssh public key /Users/joe/.ssh/id_rsa.pub`

    The final bit of output from the create command will be something
    like this:\
    `Created http://quiet-snow-81.heroku.com/ | git@heroku.com:quiet-snow-81.git<br />Git remote heroku added`

    The app has been created and two URLs are provided: one for the web
    face of your new app, and one for the remote git repository. A git
    remote named “heroku” is added for you automatically — we’ll push to
    this remote when it’s time to deploy in step \#7.

5.  Create wiki.rb and config.ru files based on the following examples:\
    [https://gist.github.com/8ff54cdfd44e1a6485e2](https://gist.github.com/8ff54cdfd44e1a6485e2)

    You can start a development server to test locally. The site is
    available at <http://localhost:4567/>

    `$ ruby wiki.rb<br />== Sinatra/0.9.1.1 has taken the stage on 4567 for development`

6.  Commit the wiki.rb and config.ru files to the git repository:\
    `$ git add wiki.rb config.ru<br />$ git commit -m 'initial commit of simple sinatra wiki'`
7.  Deploy the application to Heroku and open a browser:\
    `$ git push heroku master<br />$ heroku open`
8.  Lather, rinse, repeat
    ![:)](http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif)
    Be sure to see the Heroku documentation
    ([http://heroku.com/docs/](http://heroku.com/docs/)) for more
    information.

**Satish\>\>** Do you have any suggestions for RubyLearningâ€™s
“Introduction to Sinatra” course participants?

**Ryan\>\>** Have fun!

**Satish\>\>** Thanks Ryan for sharing your views with the
**Introduction to Sinatra^[1](#fn-1739-1)^** ” and ” **Introduction to
Merb^[2](#fn-1739-2)^** ” course participants.

***Disclaimer:***\
*The opinions expressed are those of Ryan Tomayko and do not necessarily
reflect those of **[RubyLearning.org](http://rubylearning.org/)**.*

1.  **Introduction to Sinatra**: Here are the [course
    details](http://rubylearning.com/blog/2009/02/25/introduction-to-sinatra-a-new-course/).
    [↩](#fnref-1739-1)
2.  **Introduction to Merb**: Here are the [course
    details](http://rubylearning.com/blog/2009/03/02/introduction-to-merb-3rd-batch/).
    [↩](#fnref-1739-2)

