---
title: Little Known Ways to Ruby Mastery by Chris Matthieu
author: Satish Talim
date: 2008-12-09
layout: post
permalink: /2008/12/09/little-known-ways-to-ruby-mastery-by-chris-matthieu/
keywords:
  - "ruby for beginners,ruby beginners,ruby programming,ruby on rails blog,rails blog,rails tutorials,ruby beginners\\\' questions,little known ways to ruby mastery,ruby masters,interviews,ruby,the ruby programming language,Chris Matthieu"
description:
  - The Path to Ruby Mastery Interview Series by Ruby Masters, provides guidance to and answers questions confronting Ruby beginners from across the globe.
categories:
  - Beginners
  - Interview
  - Ruby
  - Ruby Masters
tags:
  - Chris Matthieu
  - interviews
  - Little Known Ways to Ruby Mastery
  - Ruby
  - "Ruby Beginners' Questions"
  - The Ruby Programming Language
---
<div>
  <h3>
    A weekly series from the Ruby Masters
  </h3>
  
  <p class="update">
    Welcome to the next installment of the weekly interview series on the <abbr title="RubyLearning">RL</abbr> blog &#8211; &#8220;<strong>Path to Ruby Mastery</strong>&#8221; &#8211; by top trainers and developers in the <strong>Ruby community</strong>, from across the globe. The interview series will provide insight and commentary from these notable Ruby trainers and developers, with the goal of facilitating and providing answers to the questions <strong>Ruby beginners</strong> face. We welcome your suggestions for interviewees and questions. Look for a new post every Tuesday!
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/chris_clouds.jpg" alt="Chris Matthieu, USA" title="Chris Matthieu, USA" width="125" height="168" />
  </p>
  
  <p>
    <span class="drop_cap">T</span>his week, we&#8217;re happy to have <strong>Chris Matthieu</strong> from USA.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Welcome, Chris and thanks for taking out time to share your thoughts. For the benefit of the readers, could you tell us something about your self?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> Hello, my name is Chris Matthieu and I&#8217;m the host of <a href="http://www.rubyology.com/">Rubyology</a>. I have been Microsoft-free since I tried Ruby on Rails in 2006. My first Rails site was <a href="http://chugd.com/">Chug&#8217;d</a>, a social network for beer lovers. Since then I have designed and developed 10 additional full-featured Rails applications including a Ruby-based web server called <a href="http://wuby.org/">Wuby</a>, which has been open sourced on GitHub. You can learn more about my projects at <a href="http://chrismatthieu.com/">http://ChrisMatthieu.com/</a>
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Willian Molinari, Brazil>></strong> How should one go about learning the Ruby language? What material (books, eBooks, online tutorials etc.) would you recommend?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> Of course I would recommend listening to Rubyology to learn more about Ruby and other frameworks including Rails. Other podcasts that I recommend include RailsCasts and RailsEnvy. Books such as the RubyWay and RailsWay and the &#8220;Pickaxe&#8221; book are also great resources as well. These podcasts and books are great to familiarize yourself with the language and framework but nothing makes you learn like jumping into a project with both feet! You should also seek out your local Ruby or Rails user groups in your home town and get involved.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Keith Brady, Australia>></strong> What are the pros and cons of Ruby that are being discussed in the development community and what is your opinion on that?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> The biggest negative that you will hear about Rails is that it can&#8217;t scale. This is simply not true. If your application is not designed to handle traffic from the start it will not scale regardless of the language or framework that it is developed in. All high-volume sites need to be designed to run in a load balanced environment with state management or stateless pages. Caching and database tuning are critical. The biggest positive to me about Ruby and Rails are the community of innovators, flexibility of the language, and rapid development of the latest Web 2.0 features including RESTful APIs, tagging, and AJAX. Rails makes modern site development fun and simple.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Willian Molinari, Brazil>></strong> What has been your biggest challenge while working with Ruby?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> My biggest challenge with working with Ruby is getting it into the enterprise. Most developers still need to work on legacy applications in Java or .NET at work and can only develop personal inspirations at home in Rails. Only the lucky few seem to be able to use Rails full time in their jobs. I believe that JRuby will probably be the first to succeed in the enterprise due to its stealthiness Java environment and library access.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Jerry Anning, USA>></strong> What best practices are most important for a new Ruby programmer to learn and understand?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> New Rails developers need to follow the common practices of convention over configuration. Use RESTful scaffolding to start with so your application has RESTful APIs throughout. Pay attention to developing skinny controllers with most of your business logic in the models (fat models). Learn active resource caching techniques to reduce database IOs. Leverage plug-ins and gems as much as possible to reduce testing and support.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Most beginners in Ruby, would like to contribute their time, skills and expertise to a project but invariably are unaware of where and how to do so. Could you suggest some?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> You must check out <a href="http://github.com/">GitHub</a>. It&#8217;s a source code repository and a social network for developers. Most frameworks (including Rails) and gems and plug-ins exist at github and your can download them and/or contribute on them by simply forking repositories. Watch this video on how to contribute to Jay Philips&#8217; <a href="http://blip.tv/file/1249560/">Adhearsion project</a>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Keith Brady, Australia>></strong> What types of applications are currently being developed in Ruby and what changes do you foresee over the next year or two?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> Ruby is predominately being used today to develop Web applications using Rails as the framework. I am seeing new mediums moving to Ruby as the core development language because of its ease of use an power including: telephony and low-res game development as well as thick client desktop applications. Before web development became big with Ruby on Rails, Ruby was used by many network/system administrators for scripting purposes.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> What can / should job candidates (for Ruby) do to distinguish themselves from their competition?<br /><strong>Note</strong>: The candidate has done his/her homework on the company that they are interviewing with. The candidate understands what they&#8217;re looking for, and the candidate is prepared to show them that he/she fits the bill, based on the candidate&#8217;s skills and experience. What else can the candidate do, to set themselves apart from other equally well-qualified and well-prepared candidates?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> Get involved in the community. Either introduce game-changing ideas to the community or participate in open source development on GitHub projects. Signup for the Google, Yahoo, and Facebook Rails user groups and help answer questions. Get your name out there and earn respect from the community. If you think that you are ready for an interview on Rubyology send me an email at chris [at] rubyology.com. I can help get your name and cool project exposed to over 2,000 listeners in 15 minutes.
  </p>
  
  <p>
    Hope this helps!
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Thanks Chris for sharing your views with the RubyLearning participants.</span>
  </p>
  
  <p class="note">
    On 16th Dec. we talk to <strong>Peter Cooper</strong> from UK.
  </p>
  
  <p>
    <span style="font-size: 8pt; font-family: Arial;"><i><strong>Disclaimer:</strong></i></span><br /><span style="font-size: 8pt; font-family: Arial;"><i>The opinions expressed are those of Chris Matthieu and do not necessarily reflect those of <strong><a href="http://rubylearning.com/">www.RubyLearning.com</a></strong>.</i></span>
  </p>
  
  <p>
    <strong>The Path to Ruby Mastery Series (So Far)</strong>:
  </p>
  
  <ul>
    <li>
      #1: <a href="http://rubylearning.com/blog/2008/09/23/little-known-ways-to-ruby-mastery-by-jamie-van-dyke/">Jamie van Dyke</a>
    </li>
    <li>
      #2: <a href="http://rubylearning.com/blog/2008/09/30/little-known-ways-to-ruby-mastery-by-james-edward-gray-ii/">James Edward Gray II</a>
    </li>
    <li>
      #3: <a href="http://rubylearning.com/blog/2008/10/07/little-known-ways-to-ruby-mastery-by-dr-nic-williams/">Dr Nic Williams</a>
    </li>
    <li>
      #4: <a href="http://rubylearning.com/blog/2008/10/14/little-known-ways-to-ruby-mastery-by-stuart-halloway/">Stuart Halloway</a>
    </li>
    <li>
      #5: <a href="http://rubylearning.com/blog/2008/10/21/little-known-ways-to-ruby-mastery-by-jay-fields/">Jay Fields</a>
    </li>
    <li>
      #6: <a href="http://rubylearning.com/blog/2008/10/28/little-known-ways-to-ruby-mastery-by-chris-osullivan/">Chris O&#8217;Sullivan</a>
    </li>
    <li>
      #7: <a href="http://rubylearning.com/blog/2008/11/04/little-known-ways-to-ruby-mastery-by-guy-naor/">Guy Naor</a>
    </li>
    <li>
      #8: <a href="http://rubylearning.com/blog/2008/11/11/little-known-ways-to-ruby-mastery-by-jonathan-conway/">Jonathan Conway</a>
    </li>
    <li>
      #9: <a href="http://rubylearning.com/blog/2008/11/18/little-known-ways-to-ruby-mastery-by-ian-dees/">Ian Dees</a>
    </li>
    <li>
      #10: <a href="http://rubylearning.com/blog/2008/11/25/little-known-ways-to-ruby-mastery-by-bruce-tate/">Bruce Tate</a>
    </li>
    <li>
      #11: <a href="http://rubylearning.com/blog/2008/12/02/little-known-ways-to-ruby-mastery-by-ezra-zygmuntowicz/">Ezra Zygmuntowicz</a>
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Interviews" rel="tag">Interviews</a>, <a href="http://technorati.com/tag/Little+Known+Ways+to+Ruby+Mastery" rel="tag">Little Known Ways to Ruby Mastery</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Ruby+Beginners%26%238217%3B+Questions" rel="tag">Ruby Beginners&#8217; Questions</a>, <a href="http://technorati.com/tag/Chris+Matthieu" rel="tag">Chris Matthieu</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>
