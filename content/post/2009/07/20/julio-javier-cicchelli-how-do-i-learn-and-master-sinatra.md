---
draft: false
title: 'Julio Javier Cicchelli: How do I learn and master Sinatra?'
date: 2009-07-20
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
permalink: /2009/07/20/julio-javier-cicchelli-how-do-i-learn-and-master-sinatra/
tags:
- Julio Javier Cicchelli
- Learning Sinatra
- ruby programming
- Sinatra
---
Welcome to the **seventh** installment on the RL blog, of a mini series
– “**How do I learn and master Sinatra?**” – by top Rubyists using
*Sinatra*. The interview series will provide insight and commentary from
these notable *Sinatra* developers, with the goal of facilitating and
providing answers to the questions Ruby beginners face on *how to learn
and master Sinatra*.<!--more-->

**Satish\>\>** Julio Javier Cicchelli, could you tell us something about
yourself – your background, where you are based?

![Julio Javier
Cicchelli](http://www.rubylearning.com/images/jjcicchelli.jpg "Julio Javier Cicchelli")**Julio
Javier Cicchelli\>\>** Hey everybody! I am Julio Javier Cicchelli and I
have currently set an anchor in the (in)famous Red Light District in
Amsterdam, the Netherlands. I was born in Buenos Aires and I spent the
formative years of my life there. Six years ago, I decided to set sail
for Europe. I first reached France. Two years ago I decided to head for
the Netherlands.

Initially I planned to become an architect as this is the profession
that runs in the family. Yet I was meant for other things. One day, I
discovered the incredible [Commodore
C64K](http://en.wikipedia.org/wiki/Commodore_64). This proved to mark a
watershed in my life. As a result of my academic and personal pursuits,
I have become a devoted Software Engineer, who is passionate about the
Software development process. I have also developed “unholy” love for
Information Systems and Software. My interest in music and arts
propelled me to seek for the parallels between these disciplines and
Software Engineering. As a result, I consider Software to be yet another
form of expression. Indeed, because of the uniqueness of each piece of
software developed, I equate the process of software creation to a
modern form of craftsmanship. This unorthodox attitude towards the way
of truly experiencing the Software Development lies at the very core of
my newly-founded Software company [Rock &
Code](http://rock-n-code.com/).

Even though my life seems to be deeply rooted in the domain of computers
and source code, I also love those simple joys that make our lives
worthwhile. I am always eager to meet interesting people, to discover
new fascinating cultures, and to visit new places. I am also a music
junkie, a wannabe musician and artist, a passionate concertgoer, a party
person, an incurable dreamer, and a vocal social activist. At the end,
all I want is to live my life to the fullest.

**Satish\>\>** Are there any pre-requisites for a person to start
learning Sinatra?

**Julio\>\>** I do not think there are any pre-requisite for all those
who are keen on learning Sinatra. Fortunately, the Sinatra DSL has been
designed in such a way that it is almost intuitive and easy to grasp and
follow, by developers of different ranks. Nevertheless, a basic
knowledge of Ruby and Rack could save you lots of time. It will also
save you some undesirable headaches. Yet, all those who are new to the
programming language and its evil ways should be able to catch up
simultaneously with both Ruby and Sinatra.

**Satish\>\>** How should one start learning Sinatra?

**Julio\>\>** If you are an absolute beginner, do not panic. I strongly
recommend that you read the core Sinatra documentation. You must pay
special attention to the [README](http://www.sinatrarb.com/intro.html)
and the [FAQ](http://www.sinatrarb.com/faq.html). The
[book](http://www.sinatrarb.com/book.html) is another must read. If you
want to expand your knowledge of the framework even further, you can
review the screencasts and the presentations available on the website.
Finally you can browse through the
[resources](http://www.rubyinside.com/sinatra-29-links-and-resources-for-a-quicker-easier-way-to-build-webapps-1371.html).
Be bold and do not be afraid to try out the example code that you will
encounter while reading!

If you are a developer of some experience, I’d also recommend that you
read the [source code](http://github.com/sinatra/sinatra/tree/master).
Since this framework is basically a very well written DSL of about 2000
lines, the code should pose no problems. It is easy to read and
understand. The benefits of reading it are plenty. First and foremost,
studying this code would give you a more profound insight of how this
framework works intimately with Rack. In the mean time, it will teach
you how to write a DSL properly. In addition, you can find plenty of
real-life applications and their respective source code on the [In the
Wild](http://www.sinatrarb.com/wild.html) and [Extensions in the
Wild](http://www.sinatrarb.com/extensions-wild.html) sections of the
documentation page. They are also posted on
[Github](https://github.com/). So, if you are looking for more realistic
examples, this is your haven!

> Sinatra – quickly create tiny web apps and services

**Satish\>\>** Which area of Sinatra should a beginner pay particular
attention to?

**Julio\>\>** Since Sinatra is very straight-forward, a newbie does not
have to devote extra attention to any particular areas. What really
matters is that a developer should grasp its concepts and be aware of
the possibilities that this framework can offer. From there on, every
developer can make a singular use of it. How he or she is going to do it
depends on external factors such as the kind of software problem that
has to be solved, his or her vision, preferences, methodologies and
practices of writing Software.

**Satish\>\>** Is the official documentation on Sinatra good enough for
a beginner? Are there areas which need improvement or need to be
re-written

**Julio\>\>** As I have already stated, the official documentation is
the pivotal gateway that guarantees the right of passage to the Sinatra
world. I believe it can fully satiate the initial hunger for knowledge
of any starter. When I was a novice, I studied the documentation very
carefully. This allowed me to eventually master it. In addition, I
consider this documentation to be exemplary because it is simple, pithy,
and full of useful examples for all the dilettantes. Certainly, there is
plenty of room for improvement. There are certain parts that are either
incomplete or still unwritten and probably unexplored. One of its
drawbacks is that it is only available in English. This could prove to
be a nuisance for all the developers who are still not comfortable with
English. Hopefully, those weaknesses and insufficiencies will be
addressed in the near future.

**Satish\>\>** Sequel, DataMapper, ActiveRecord – which one would you
recommend to use with Sinatra and why?

**Julio\>\>** I highly recommend that developers use
[DataMapper](http://datamapper.org/doku.php) when they are working on
projects that involve some sort of a data base (not only relational
databases). This ORM has certain characteristics such as eager loading,
laziness, performance, and Ruby-like syntax that I particularly favor.
It is also very simple to use. Please be aware that I am somehow biased.
Although I have used ActiveRecord, I have never used or explored the
approach proposed by Sequel.

![Sinatra
Icon](http://rubylearning.com/images/sinatralogo.jpg "Sinatra micro-framework")

**Satish\>\>** Is an understanding of Rack important while learning
Sinatra? Why? Which area of Rack should one be really comfortable with?

**Julio\>\>** A basic knowledge of [Rack](http://rack.rubyforge.org/)
could be extremely useful during the process of learning Sinatra because
it allows you to consider the vast project possibilities this framework
has to offer. Moreover, exploring the intimate relationship between
these two technologies enables you to write simple, modular and powerful
applications. Taking into account that Rack has become the backbone of
any Web framework written in Ruby, Rack-compatible applications are
guaranteed to work with any Rack-supported framework. It only takes one
Rack to rule them all!

**Satish\>\>** How should one hone one’s skills in Sinatra?

**Julio\>\>** There is nothing more exciting than pushing the limits of
your knowledge even further. In order to succeed in doing this, you have
to be intrepid. Do not be afraid of transforming your ideas into neat
(or not so neat) lines of code. Even if your task appears to be
daunting, do not give up! Carry on until you complete your projects.
Study carefully the concepts and the approach to write applications
proposed by Sinatra. Then go with the flow and start coding. In cases of
a writer’s block, do not despair. Never forget the reason why Internet
has become such a popular tool. It abounds with documentation,
interactive examples, and of course, billions of blogs, forums, and
chats, where kind people are genuinely willing to help you out with your
development quest. So go ahead, write some applications and have lots of
fun at the same time.

**Satish\>\>** What type of projects should a beginner work on to gain
more expertise in Sinatra?

**Julio\>\>** It is entirely up to the beginners to decide. There are
plenty of applications that they can actually write. My sole piece of
advice to all the explorers out there is to be self-centered for just a
moment and ask themselves the following question: “What is the
application I actually need?”. Certainly the answers to that question
will vary from a personal website, to a blog system or an application
that allows you to manage your finances, your record or DVD collection,
etc. In conclusion, just do what you really want but remember to write
it as a Sinatra application. If you are proud of what you have
developed, brag about it by showing it to other developers around the
world!

**Satish\>\>** Could you suggest some web services that a Sinatra
beginner could develop himself / herself?

**Julio\>\>** Let the starters play again! They are numerous services
that they can implement. Consider this to be a gradual process. If you
have just created you first Sinatra application, congratulations, you
are in. Now, in order to make it even more attractive, try to modify it
by adding a RESTful APl if you have not done so already! Make your
application respond to any delivery format you like and… there was
light! Now your application can provide information as a web service in
XML, JSON, HTML or ever CSV to any client. Of course you will have to
develop the client that will consume the API as well. The cool part is
that the client can be almost any kind of Software you can possibly
imagine: it could be a mysterious command-line application, a typical
web admin user interface, a web application, a desktop application, a
smart phone application etc. The choice is yours!

**Satish\>\>** Anything else you would like to add?

**Julio\>\>** It is incredible how much you can accomplish with so
little. Arm yourselves with personal motivation, incessant curiosity,
and an avid desire to explore this tiny Ruby framework. You will be
surprised by the plethora of possibilities that it can offer. Do not
waste this chance girls and boys! You will learn lots of interesting
stuff if you go this way. I cannot promise you instant fame and fortune
but I assure you, it is a whole lot of fun!

*Thank you Julio. In case you have any queries and/or questions, kindly
post your questions here (as comments to this blog post) and Julio would
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

***Post supported by 1st Easy Limited*:** UK based 1st Easy Limited
offer Sinatra and Rails hosting running on a Phusion Passenger
(mod\_rails) and LAMP stack. If you want to try your hand at developing
with Sinatra, why not let them arrange a [trial hosting
account](http://www.1steasy.com/ruby-on-rails.htm#try) for you? You’ll
get to deploy your app, with full technical support from their team!

