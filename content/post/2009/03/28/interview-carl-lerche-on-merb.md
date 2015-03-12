---
author: Satish Talim
categories:
- Beginners
- Interview
- Merb
- Ruby
date: 2009-03-28
description:
- RubyLearning talks to Carl Lerche, a core Merb developer, on the eve of the online
  Merb course at RubyLearning.
keywords:
- Interviews,Carl Lerche,Merb,Merbist,Ruby,RubyLearning,The Merb Way,Merb in action
layout: post
permalink: /2009/03/28/interview-carl-lerche-on-merb/
tags:
- Carl Lerche
- interviews
- Merb
- Merb in Action
- Merbist
- Ruby
- RubyLearning
- The Merb Way
title: 'Interview: Carl Lerche on Merb'
topsy_short_url:
- http://bit.ly/cWAqMG
---

<div>
  <p class="update">
    <span class="drop_cap">R</span>ubyLearning&#8217;s 3rd batch of the &#8220;<strong>Introduction to Merb</strong>&#8221; course starts today, 28th Mar. 2009. Satish Talim of RubyLearning caught up with <strong>Carl Lerche</strong>, Merb core team member, to learn more about <strong>Merb</strong>.
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/carl.jpg" alt="Carl Lerche, USA" title="Carl Lerche, USA" width="125" height="125" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Welcome, Carl and thanks for taking out time to share your thoughts. For the benefit of the readers, could you tell us something about your self?</span>
  </p>
  
  <p>
    <strong>Carl>></strong> First off, thanks for having me. So, a little about me? Let&#8217;s see, I&#8217;ve been working with Ruby for about 4 or 5 years now. I discovered Ruby a while back working with FreeBSD. I started using Ruby on Rails back before it was released as 1.0 software and have been enjoying the Ruby world since then. I&#8217;ve been involved with a number of open source Ruby projects and am currently employed full time by Engine Yard to contribute to Ruby on Rails.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How closely have you been associated with Merb?</span>
  </p>
  
  <blockquote class="right">
    <p>
      Merb &#8211; Ruby web framework for the enterprise
    </p>
  </blockquote>
  
  <p>
    <strong>Carl>></strong> I have been actively contributing to the Merb project for about 9 months and am on the core developer team. I started investigating Merb about a year ago when I needed a Ruby framework that offered greater flexibility than Ruby on Rails. It looked quite promising, but it had a number of drawbacks, such as the router. I decided to write the missing code and contribute back to the project. Since then, I have been actively involved in Merb&#8217;s development.
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/powered-by-merb-big.png" alt="Merb" title="Merb - Ruby web framework for the enterprise" width="128" height="60" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> If someone wanted to learn and start using Merb, how does one do that? Can you talk about what all is being done for Merb in terms of documentation, books, tutorials and training?</span>
  </p>
  
  <p>
    <strong>Carl>></strong> Even though Merb adoption has been picking up, it is still a fairly new framework. As such, learning resources can be scarce. I would say that one of the best ways to learn Merb is to read the source code and the specs. We make quite a bit of effort to keep the code readable and we only spec out the public API, so everything that happens in the specs is actually something that a developer using Merb should be using. That being said, the Merb website does have a wiki that is updated and that contains good information. The Merb community is also quite helpful and there are lots of people on the IRC channel that answer questions.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> What type of projects would you use Merb for?</span>
  </p>
  
  <p>
    <strong>Carl>></strong> You can use for any web application. It is a very flexible framework that handles the VC bits of MVC in context of the web. This includes anything from large, complex, web applications to simple web services. Merb is ORM agnostic, so you can use it with ActiveRecord, DataMapper, Sequel, or any other library. However, we do recommend using DataMapper, which is why it is the default ORM when you install the full Merb stack. Personally, I have never needed to use anything besides Merb in the context of the web.
  </p>
  
  <p>
    <a href='http://www.railsware.com/'><img class="alignright" src='http://rubylearning.com/images/Railsware125x125.png' width="125" height="125" style="border: 0px none ;" alt="Sponsor: Railsware for premium-quality web applications" title="Sponsor: Railsware for premium-quality web applications" /></a>
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> With Merb and Rails merging by the end of the year, how does it benefit the developer?</span>
  </p>
  
  <p>
    <strong>Carl>></strong> The Rails/Merb merge is actually quite exciting. First, let me clear up a misconception that seems to be somewhat common. The Rails / Merb merge is not so much of a code base merge as it is a joining of forces of the developers. Anyway, coming from the Merb side of things, working on Rails 3 gives me the opportunity to revisit all the things that are already implemented in Merb and question whether they are as good as possible, such as AbstractController. As it turns out, AbstractController is not as abstract as it could be. In other words, Rails 3 will actually be a significant improvement over current Merb. Also, since Rails has a much greater reach within businesses, all developers who use Merb for their hobby projects but have to use Rails at work will be able to use Rail 3, the framework with everything that made Merb great and more.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Tell us something about deployment of Merb apps.</span>
  </p>
  
  <p>
    <strong>Carl>></strong> Deploying Merb apps is actually relatively easy. Merb has an executable that handles creating all the child processes. As of the latest version, it also monitors the processes for memory and will restart them if they start getting out of hand. Also, apache passenger works quite well with Merb. Also, something to checkout would be Engine Yard&#8217;s new Solo offering. It&#8217;s pretty slick. You can deploy a Merb app onto amazon&#8217;s AWS platform quite painlessly through an easy to use web interface. No matter which way you want to go, I would definitely recommend hitting up the IRC channel if you have any questions.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Carl, thank you for your time. Anything else you would like to add?</span>
  </p>
  
  <p>
    <strong>Carl>></strong> Well, I&#8217;ll mention a cool new feature that will be in Rails 3 and most likely Merb 1.1. That would be mountable apps. I&#8217;ve started working on this recently and it&#8217;s shaping out quite nicely. It&#8217;ll basically let any application developed with Merb or Rails 3 be reusable in any other application. So, if you develop a blog or forum application, you could just release that app as a gem and mount it in any other app and share the models and other fun stuff. I&#8217;ll be talking more about this at railsconf, so, if you are there, be sure to stop by. I&#8217;ll see you all there!
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Carl, thank you for your time.</span>
  </p>
  
  <p>
    <span style="font-size: 8pt; font-family: Arial;"><i><strong>Disclaimer:</strong></i></span><br /><span style="font-size: 8pt; font-family: Arial;"><i>The opinions expressed are those of Carl Lerche and do not necessarily reflect those of <strong><a href="http://rubylearning.com/">www.RubyLearning.com</a></strong>.</i></span>
  </p>
  
  <p class="alert">
    <strong><em>Post supported by Railsware</em>:</strong> At <a href="http://railsware.com/">Railsware</a> we chose Ruby on Rails as the core technology from the very beginning. As a product development company <a href="http://railsware.com/services">we build web applications</a> for our clients and for ourselves and have experienced the benefits of both Rails and Merb. We are looking forward to this merge of Rails and Merb for better performance and keeping the best of both frameworks, and a rigorous API which will definitely result in reliable results and lower amount of patching. As the big result, developing a web application on Rails 3 will become even faster and cheaper. We are eagerly waiting to start building and delivering more great web apps using Rails 3.
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Interviews" rel="tag">Interviews</a>, <a href="http://technorati.com/tag/Carl+Lerche" rel="tag">Carl Lerche</a>, <a href="http://technorati.com/tag/Merb" rel="tag">Merb</a>, <a href="http://technorati.com/tag/Merbist" rel="tag">Merbist</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/RubyLearning" rel="tag">RubyLearning</a>, <a href="http://technorati.com/tag/The+Merb+Way" rel="tag">The Merb Way</a>, <a href="http://technorati.com/tag/Merb+in+action" rel="tag">Merb in action</a>
