---
title: Little Known Ways to Ruby Mastery by James Edward Gray II
author: Satish Talim
date: 2008-09-30
layout: post
permalink: /2008/09/30/little-known-ways-to-ruby-mastery-by-james-edward-gray-ii/
keywords:
  - "ruby for beginners,ruby beginners,ruby programming,ruby on Rails blog,rails blog,rails tutorials,ruby beginners\' questions,little known ways to ruby mastery,ruby masters"
description:
  - The Path to Ruby Mastery Interview Series by Ruby Masters, provides guidance to and answers questions confronting Ruby beginners from across the globe.
topsy_short_url:
  - 
categories:
  - Beginners
  - Interview
  - Ruby
  - Ruby Masters
  - Training
tags:
  - interviews
  - James Edward Gray II
  - Little Known Ways to Ruby Mastery
  - Ruby
  - "Ruby Beginners' Questions"
  - ruby for beginners
  - Ruby Masters
  - The Ruby Programming Language
---
<div>
  <h3>
    A weekly series from the Ruby Masters
  </h3>
  
  <p class="update">
    Welcome to the second installment of the weekly interview series on the <abbr title="RubyLearning">RL</abbr> blog &#8211; &#8220;<strong>Path to Ruby Mastery</strong>&#8221; &#8211; by top trainers and developers in the <strong>Ruby community</strong>, from across the globe. The interview series will provide insight and commentary from these notable Ruby trainers and developers, with the goal of facilitating and providing answers to the questions <strong>Ruby beginners</strong> face. We welcome your suggestions for interviewees and questions. Look for a new post every Tuesday!
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/jamesgray.jpg" alt="James Edward Gray II, USA" title="James Edward Gray II, USA" width="125" height="166" />
  </p>
  
  <p>
    <span class="drop_cap">T</span>his week, we are happy to have <strong>James Edward Gray II</strong> from USA.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Welcome, James and thanks for taking out time to share your thoughts. For the benefit of the readers, could you tell us something about your self?</span>
  </p>
  
  <p>
    <strong>James>></strong> My name is James Edward Gray II and I&#8217;ve been trapped in the Ruby community for almost five years now. I keep trying to get out, but this place is just so much fun I can&#8217;t seem to break away.
  </p>
  
  <p>
    I&#8217;ve tried to give back some contributions for everything Ruby has given me. I started the <a href="http://rubyquiz.com/">Ruby Quiz</a> and ran it for the first three years, I wrote documentation for some standard libraries including ERb and PStore. I created some open source libraries including <a href="http://rubyforge.org/projects/fastercsv/">FasterCSV</a> and <a href="http://highline.rubyforge.org/">HighLine</a>. I wrote a couple of <a href="http://www.pragprog.com/search?q=James+Edward+Gray+II">Pragmatic Programmer books</a> with lots of Ruby in them. I speak at some Ruby conferences, and I now help maintain a few of Ruby&#8217;s standard libraries.
  </p>
  
  <p>
    My day job is building Rails applications for <a href="http://highgroove.com/">Highgroove Studios</a>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Willian Molinari, Brazil>></strong> How should one go about learning the Ruby language? What material (books, eBooks, online tutorials etc.) would you recommend?</span>
  </p>
  
  <p>
    <strong>James>></strong> Books, tutorials, and similar reference materials are wonderful and very needed. However, I truly believe there is only one way to learn a programming language: write 500 programs in it. Obviously I just made that number up, but the point is the same. You learn to code by writing code.
  </p>
  
  <p>
    Programming is about learning to think like a computer. The languages are very small compared to those we speak, so that&#8217;s not the challenge. The challenge is learning to think like a very dumb machine. To do that, you need to have a lot of conversations with the machine. You have to learn how it thinks and give it a chance to dumb you down. That means feeding it code and learning to interpret those cryptic error messages.
  </p>
  
  <p>
    Given that, my number one recommendation for those learning would be to get a pet project and dive right in. Choose something you are interested in or just a simple project that could save you some time with work. Read reference materials as you go to learn the part you are working on now. Ask questions on <a href="http://www.ruby-lang.org/en/community/mailing-lists/">Ruby-Talk</a> when you get stuck. <span style="background-color: #FFFFCC;">The most important thing though is to keep writing code. That&#8217;s how you learn. Believe it.</span>
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Keith Brady, Australia>></strong> What are the pros and cons of Ruby that are being discussed in the development community and what is your opinion on that?</span>
  </p>
  
  <p>
    <strong>James>></strong> You&#8217;ll hear a lot of people say, &#8220;Ruby is slow.&#8221;
  </p>
  
  <p>
    That can be true, but it doesn&#8217;t have to be. I just gave a presentation at the <a href="http://lsrc2008.confreaks.com/02-james-edward-gray-ii-hidden-gems.html">LSRC</a> that showed multiple ways to get Ruby to do work in fractions of a second.
  </p>
  
  <p>
    My opinion on the speed rumors is that you shouldn&#8217;t believe everything you hear. I&#8217;m sure there are tasks Ruby is too slow for, but there are also a surprising number of tasks where you can make it go fast enough.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Willian Molinari, Brazil>></strong> What has been your biggest challenge while working with Ruby?</span>
  </p>
  
  <p>
    <strong>James>></strong> I am in the middle of replacing Ruby&#8217;s old CSV library with my FasterCSV code base. Part of that process includes reworking the parser to work well with 1.9&#8217;s <abbr title="multilingualization">m17n</abbr> implementation. That has been pretty tough.
  </p>
  
  <p>
    Part of that is because Ruby&#8217;s m17n code is new and still has some minor oddities. That&#8217;s improving all the time though as we find bugs. The bigger issue is just that character encodings are hard to get right, especially when working with non-ASCII compatible encodings like UTF-16.
  </p>
  
  <p>
    In a way, you can argue it is a testament to the new m17n implementation that it is making it possible for me to get CSV working with so many popular encodings. I won&#8217;t kid you though, it was hard work.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Jerry Anning, USA>></strong> Can you recommend things to study after learning Core Ruby, including different frameworks, gems and external libraries?</span>
  </p>
  
  <p>
    <strong>James>></strong> I&#8217;m a huge fan of Ruby&#8217;s standard library. Ruby ships with so many great tools. I can&#8217;t count the number of times I&#8217;ve seen someone working on a tough problem and I showed them how to solve it with a require statement and a line or two of code to make use of a standard library.
  </p>
  
  <p>
    Plenty of these libraries are still missing documentation too, so it&#8217;s an excellent opportunity to take your first steps into the community. Crack open one of the libraries, put on your code investigation hat, and try to figure out what it is capable of. Call methods in IRb and try passing them different kinds of data. Take notes as you go and you can turn those into documentation to help other programmers. It&#8217;s surprisingly fun.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Most beginners in Ruby, would like to contribute their time, skills and expertise to a project but invariably are unaware of where and how to do so. Could you suggest some?</span>
  </p>
  
  <p>
    <strong>James>></strong> I asked this exact question at <a href="http://lsrc2008.confreaks.com/18-panel-ruby-designers-producers-and-consumers.html">LSRC panel</a> with many smart Rubyists including Matz and Dave Thomas. Their answer: <span style="background-color: #FFFFCC;">be passionate about what you do</span>. That&#8217;s great advice.
  </p>
  
  <p>
    The biggest thing I can suggest is to get involved today. There are ways you can help no matter what your skill level is. I&#8217;ve already mentioned a documentation tip, but there are plenty of others. Get involved with some Ruby project that interests you. Join their mailing list and help answer questions there. Offer to build a web site for the project if they don&#8217;t have one. Or just install the test release of Ruby 1.9, play around a bit, and write blogs posts about the new features. Don&#8217;t be shy.
  </p>
  
  <p>
    Remember, helping the community isn&#8217;t just about being generous. You are building your portfolio that a future employer will see as an added bonus.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Victor Goff, USA>></strong> How do you see the market for Ruby Programmers in the work place, and do you see it as primarily tied to Rails and Web related work? Do you see trends in administration or other work? Whatâ€™s the future for Ruby?</span>
  </p>
  
  <p>
    <strong>James>></strong> I would definitely say that Ruby is seeing the most use currently in the Web application world. That&#8217;s not all it can do though and some brave souls are pushing those boundaries!
  </p>
  
  <p>
    Ruby has begun to make some inroads into the sciences. <acronym title="[ National Oceanic and Atmospheric Administration ]">NOAA</acronym> used Ruby to analyze satellite images of that damage caused by Hurricane Katrina, I spoke with a genetic researcher doing some genome processing with Ruby at the LSRC, and even <acronym title="[ National Aeronautics and Space Administration ]">NASA</acronym> is using Ruby on a few projects now.
  </p>
  
  <p>
    That&#8217;s just one field. Ruby is ready for us to take it into many new fields. My hope for the future is that we take Ruby to new places and do for them what we&#8217;ve done for web development.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Do you have any other suggestions for these participants (would-be Ruby developers)?</span>
  </p>
  
  <p>
    <strong>James>></strong> Be immune to the word &#8220;can&#8217;t.&#8221; There are two kinds of people, those who say they can&#8217;t and those who aren&#8217;t afraid to try. Be one of the latter. Succeed or fail that&#8217;s all it really takes to be a hero.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Thanks James for sharing your views with the RubyLearning participants.</span>
  </p>
  
  <p class="note">
    On 7th Oct. we talk to <strong>Dr Nic Williams</strong> from Australia.
  </p>
  
  <p>
    <span style="font-size: 8pt; font-family: Arial;"><i><strong>Disclaimer:</strong></i></span><br /><span style="font-size: 8pt; font-family: Arial;"><i>The opinions expressed are those of James Edward Gray II and do not necessarily reflect those of <strong><a href="http://rubylearning.com/">www.RubyLearning.com</a></strong>.</i></span>
  </p>
  
  <p>
    <strong>The Path to Ruby Mastery Series (So Far)</strong>:
  </p>
  
  <ul>
    <li>
      #1: <a href="http://rubylearning.com/blog/2008/09/23/little-known-ways-to-ruby-mastery-by-jamie-van-dyke/">Jamie van Dyke</a>
    </li>
  </ul>
  
  <p class="alert">
    <strong><em>Post supported by Blue Box Group</em>:</strong> <a href="https://boxpanel.blueboxgrp.com/public/order/partner/43921">Blue Box Group</a> is in the business of providing affordable <a href="https://boxpanel.blueboxgrp.com/public/order/partner/43921">Ruby on Rails hosting</a> solutions! They approach web hosting, virtual servers and dedicated servers differently, treating each client as a partner and working towards the common goal of success for their business. From shared Ruby on Rails hosting to giant production clusters, they have the experience, talent and equipment to make your site a success!
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Interviews" rel="tag">Interviews</a>, <a href="http://technorati.com/tag/James+Edward+Gray+II" rel="tag">James Edward Gray II</a>, <a href="http://technorati.com/tag/Little+Known+Ways+to+Ruby+Mastery" rel="tag">Little Known Ways to Ruby Mastery</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Ruby+Beginners%26%238217%3B+Questions" rel="tag">Ruby Beginners&#8217; Questions</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>
