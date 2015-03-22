---
draft: false
title: Patrick McKenzie Winner RPCFN - 5
date: 2010-01-21
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/rubylearning
categories:
- interview
- rpcfn
- ruby
layout: post
permalink: /2010/01/21/patrick-mckenzie-winner-rpcfn-5/
tags:
- japan
- patrick mckenzie
- rpcfn
- ruby
- ruby challenge
- ruby programming
---
In this brief interview, Satish Talim of RubyLearning talks to **Patrick
McKenzie of Japan**, winner of the fifth [Ruby Programming Challenge For
Newbies](http://rubylearning.com/blog/2009/12/27/rpcfn-mazes-5/).<!--more-->

![Patrick
McKenzie](http://www.rubylearning.com/images/patrick-125x125.jpg "Patrick McKenzie")

**Satish\>\>** Welcome Patrick and thanks for taking out time to share
your thoughts. For the benefit of the readers, could you tell us
something about your self?

**Patrick\>\>** Thanks Satish for the opportunity. My name is Patrick
McKenzie and by day I work on big freaking Java web apps at a Japanese
corporation in Nagoya. By night, I run a [small software
business](http://www.bingocardcreator.com/), which sells desktop
software written in Java and a web application written in Ruby on Rails.
I also [blog](http://www.kalzumeus.com/) a bit, mostly on business and
programming topics.

**Satish\>\>** How did you get involved with Ruby programming?

**Patrick\>\>** About two years ago, when I was trying to make my
business’ website a little more impressive than hand-coded HTML
everywhere, I thought writing myself a custom CMS (content management
system) would help me produce things my customers would like faster than
writing them all by hand. However, since I could only do it on nights
and weekends, I couldn’t exactly find the time to do it on the J2EE
stack. I bought a pair of books on Ruby on Rails, fell in love with
Ruby, and the rest is history.

**Satish\>\>** Could you name three features of Ruby that you like the
most, as compared to other languages? Why?

**Patrick\>\>** It would be hard to limit it to three, but here goes:

​1. A lot of Ruby code functions rather like Unix: small, discrete bits
of code which operate together very well. For example, to read a
property file in Ruby:

File.readlines("property.txt")
  .map {|line| line.split("#")[0]}
  .map {|line| line.split("=")}
  .inject({}) {|hash, couplet| hash[couplet[0]]=couplet[1]; hash}

does all the work for you. That is a trivial example in Ruby which would
take me almost a page to write in Java (well, assuming I wasn’t using a
library function, but you get the drift.)

​2. I think the community for a language matters. The Ruby community is
amazing and has been very generous with their time in producing OSS
code, documentation on the Internet, and the gem infrastructure, which
lets me get more impressive things done faster and with less pain.

​3. I really like having IRB and its cousin the Rails console, which
lets me dive right in among my objects and see the world from their
eyes, so to speak. Often when coding I have IRB open in another window
so that I can test my assumption of what a particular bit of code would
result in prior to using it.

**Satish\>\>** How was experience of taking part in the Ruby Programming
Challenge For Newbies (RPCFN)?

**Patrick\>\>** It was amazingly fun — thank you for running the
challenge. As soon as I heard the maze solving challenge I thought
“Well, let’s see, you can read in the maze, construct a graph from it,
and then use breadth first search” but I thought that there would
probably be a hundred implementations of that. So I decided to do
something a little different and solve it with regular expressions. The
key insight for me was that if the width of the maze is constant that
you can write a regular expression which skips to the same column on the
next line.

**Satish\>\>** How is the Ruby and Rails scenario in your country Japan?

**Patrick\>\>** My industry is currently dominated by expensive web
applications written in Java, but I think the future for Ruby is bright.
There is a certain deal of pride in the fact that Ruby is a Japanese
language and probably the most well-known bit of Japanese software that
is not a video game. My impression is that Rails is increasingly
popular, too. I have tried to promote both internally at my company, and
we’ve had some success with them.

**Satish\>\>** What are your future plans?

**Patrick\>\>** I recently made the decision to quit my day job and go
full-time with my software business. I expect I will be developing more
applications in Rails.

*Thank you Patrick and all the very best with your software business. In
case you have any queries and/or questions, kindly post your questions
here (as comments to this blog post) and Patrick would be glad to
answer.*
