---
draft: false
title: 'Graham Ashton: How do I learn and master Sinatra?'
date: 2009-07-10
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/rubylearning
categories:
- Beginners
- Learn Sinatra
- Ruby
- Sinatra
layout: post
permalink: /2009/07/10/graham-ashton-how-do-i-learn-and-master-sinatra/
tags:
- Graham Ashton
- Learning Sinatra
- ruby programming
- Sinatra
---
Welcome to the **third** installment on the RL blog, of a mini series –
“**How do I learn and master Sinatra?**” – by top Rubyists using
*Sinatra*. The interview series will provide insight and commentary from
these notable *Sinatra* developers, with the goal of facilitating and
providing answers to the questions Ruby beginners face on *how to learn
and master Sinatra*.<!--more-->

**Satish\>\>** Graham Ashton, could you tell us something about yourself
– your background, where you are based?

![Graham
Ashton](http://www.rubylearning.com/images/graham-ashton.jpeg "Graham Ashton")**Graham
Ashton\>\>** I’m [Graham Ashton](http://grahamashton.net/). When I first
got involved in web development I taught myself Perl. It served me well
for five years, but I felt there had to be a better way. I picked up
Python and loved it, and set about finding a full time Python job.
Another five years later I found my way to Ruby, Rails and eventually
Sinatra. I’m now working in London developing web applications as a
freelancer. I’m mainly using Ruby at the moment, but I’m still keeping
my eye in with Python.

**Satish\>\>** Are there any pre-requisites for a person to start
learning Sinatra?

**Graham\>\>** I think it’s well worth having a basic grasp of the
programming language before you pick up a framework. The first time I
tried Rails I didn’t know any Ruby and couldn’t tell the Rails magic
apart from the Ruby magic. I found it much easier to learn Rails after
spending a day or two getting familiar with the Ruby syntax. Sinatra
doesn’t really do magic (which is great, and appeals to the Python fan
within me), but I still think it’s well worth having a good grasp of
Ruby.

Otherwise, the only thing I’d recommend is a good understanding of the
basics of HTTP (GET, POST, etc.). Sinatra feels like a pretty thin layer
on top of HTTP.

**Satish\>\>** How should one start learning Sinatra?

**Graham\>\>** It may be a cliche, but I’d start with the
[README](http://www.sinatrarb.com/intro.html). It’s a fairly succinct
summary of what you can do with Sinatra, and will bring you up to speed
on what’s possible. You can refer back to the README or the [Sinatra
book](http://www.sinatrarb.com/book.html) for more details later. I hear
the book is still a work in progress, but I found it very useful when I
was starting out.

Once you’ve skim read some docs just get stuck in and start trying to
make stuff. Don’t skimp on the
[testing](http://www.sinatrarb.com/testing.html); it’s pretty easy to do
and is just as important to learn as the main Sinatra API.

> Sinatra – quickly create tiny web apps and services

**Satish\>\>** Which area of Sinatra should a beginner pay particular
attention to?

**Graham\>\>** That’s a tricky question. Sinatra is so simple that no
part stands out as being worthy of attention. Just make sure you write
tests and you’ll be fine.

**Satish\>\>** Is the official documentation on Sinatra good enough for
a beginner? Are there areas which need improvement or need to be
re-written

**Graham\>\>** I think it’s good enough, yes. That’s how I learnt
Sinatra and I managed to write a complete app without resorting to
digging into the code. I hear that the book will be getting some work
done on it in future, but I’m not really up to speed on it’s
deficencies.

**Satish\>\>** Sequel, DataMapper, ActiveRecord – which one would you
recommend to use with Sinatra and why?

**Graham\>\>** I’d say you should use whichever is most suitable to your
task, that you’re familiar with, or interested in learning. Sinatra
doesn’t have a preference.

![Sinatra
Icon](http://rubylearning.com/images/sinatralogo.jpg "Sinatra micro-framework")

**Satish\>\>** Is an understanding of Rack important while learning
Sinatra? Why? Which area of Rack should one be really comfortable with?

**Graham\>\>** Understanding Rack certainly isn’t a pre-requisite. To
deploy a Sinatra application you typically need to write yourself a Rack
config file, but there are plenty of examples online that you could
download if you wanted to.

Having said all that, Rack is pretty simple, very cool, and well worth
reading up on. Check out how to chain various Rack components together
using the **Rack::Builder** DSL (there’s an example in the RDoc).

**Satish\>\>** How should one hone one’s skills in Sinatra?

**Graham\>\>** Make stuff. Deploy it. Repeat.

**Satish\>\>** What type of projects should a beginner work on to gain
more expertise in Sinatra?

**Graham\>\>** When I’m learning a new technology I find that I progress
faster if I’m really motivated to release whatever it is I’m working on.
So make stuff that interests you or excites you. Development is a
creative process, and should be fun.

**Satish\>\>** Could you suggest some web services that a Sinatra
beginner could develop himself / herself?

**Graham\>\>** If you’ve got an existing site that you’ve already
implemented with another technology, consider porting it to Sinatra
(it’s a great way to compare and contrast different approaches). Have
you got a personal web page or blog? They’re easy to make in Sinatra,
and once you’ve got total control of your site using something as simple
as Sinatra you really can do anything you like with it.

That’s exactly what I did when I built
[Nesta](http://effectif.com/nesta) (I had previously been running
Mephisto). You could just use Nesta but you’ll learn more if you write
your own site from scratch. There are plenty of alternatives to Nesta
out there, such as [Marley](http://github.com/karmi/marley/tree/master)
(which inspired me to make Nesta) or the code for
[toolmantim.com](http://github.com/toolmantim/toolmantim/tree/master).

**Satish\>\>** Anything else you would like to add?

**Graham\>\>** Take half an hour out to learn HAML and SASS. The syntax
is so simple, it’ll be well worth the investment.

*Thank you Graham. In case you have any queries and/or questions, kindly
post your questions here (as comments to this blog post) and Graham
would be glad to answer.*

**Others in this series:**

-   [Corey Donohoe](http://rubylearning.com/blog/2015/01/07/corey-donohoe-how-do-i-learn-and-master-sinatra/)
-   [Jeremy Evans](http://rubylearning.com/blog/2009/07/08/jeremy-evans-how-do-i-learn-and-master-sinatra/)

***Post supported by 1st Easy Limited*:** UK based 1st Easy Limited
offer Sinatra and Rails hosting running on a Phusion Passenger
(mod\_rails) and LAMP stack. If you want to try your hand at developing
with Sinatra, why not let them arrange a [trial hosting
account](http://www.1steasy.com/ruby-on-rails.htm#try) for you? You’ll
get to deploy your app, with full technical support from their team!

