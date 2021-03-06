---
author: Satish Talim
categories:
- beginners
- interview
- ruby
- ruby masters
date: 2008-10-28
description:
- The Path to Ruby Mastery Interview Series by Ruby Masters, provides guidance to
  and answers questions confronting Ruby beginners from across the globe.
keywords:
- ruby for beginners,ruby beginners,ruby programming,ruby on rails blog,rails blog,rails
  tutorials,ruby beginners\' questions,little known ways to ruby mastery,ruby masters,interviews,Stuart
  Halloway,ruby,the ruby programming language
layout: post
permalink: /2008/10/28/little-known-ways-to-ruby-mastery-by-chris-osullivan/
tags:
- chris o'sullivan
- interviews
- little known ways to ruby mastery
- ruby
- ruby beginners' questions
- the ruby programming language
title: Little Known Ways to Ruby Mastery by Chris O'Sullivan
---

<div>
  <h3>
    A weekly series from the Ruby Masters
  </h3>
  
  <p class="update">
  Welcome to the next installment of the weekly interview series on the <abbr title="RubyLearning">RL</abbr> blog &#8211; &#8220;<strong>Path to Ruby Mastery</strong>&#8221; &#8211; by top trainers and developers in the <strong>Ruby community</strong>, from across the globe.<!--more--> The interview series will provide insight and commentary from these notable Ruby trainers and developers, with the goal of facilitating and providing answers to the questions <strong>Ruby beginners</strong> face. We welcome your suggestions for interviewees and questions. Look for a new post every Tuesday!
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/chris.jpg" alt="Chris O'Sullivan, UK" title="Chris O'Sullivan, UK" width="125" height="134" />
  </p>
  
  <p>
    <span class="drop_cap">T</span>his week, we&#8217;re happy to have <strong>Chris O&#8217;Sullivan</strong> from UK.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Welcome, Chris and thanks for taking out time to share your thoughts. For the benefit of the readers, could you tell us something about your self?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> I&#8217;m Chris O&#8217;Sullivan, an Average Joe Ruby on Rails developer working for a media agency in London, UK. I came to RoR development early last year after a long spell doing Windows development in .Net and Delphi. You can read my <a href="http://www.thechrisoshow.com/">blog</a>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Willian Molinari, Brazil>></strong> How should one go about learning the Ruby language? What material (books, eBooks, online tutorials etc.) would you recommend?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> Like a gigantic proportion of the Rails community I came to Ruby because I wanted to learn about Rails &#8211; and in my arrogance I tried to create Rails applications without first figuring out Ruby. Don&#8217;t follow my foolish example, and pick up a Ruby book first! After several false Rails starts I eventually picked up Mr Neighbourly&#8217;s humble little Ruby book from Lulu (written by Jeremy McNally) and found it to be a tremendous resource.
  </p>
  
  <p>
    I also owe a tonne to Ryan Bates&#8217;s Railscast. Every week he manages to put together a magnificent video tutorial. It&#8217;s worth watching each and every episode, even if you&#8217;re not interested in the topic, as you&#8217;ll learn a tonne about Ruby and Rails best practices.
  </p>
  
  <p>
    Another excellent reference is David Black&#8217;s Ruby for Rails. A lot of stuff in Rails just feels like voodoo magic, but David explains with blessed simplicity how Ruby enables all this magic to happen.
  </p>
  
  <p>
    The best way to learn about a language though is to make something! Get started making a simple application, and you&#8217;ll learn gabillions more than just reading books or watching screencasts.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Willian Molinari, Brazil>></strong> What has been your biggest challenge while working with Ruby? </span>
  </p>
  
  <p>
    <strong>Chris>></strong> The biggest challenge for me has been to trying to drop my statically typed habits. It&#8217;s entirely easy to program Ruby with a C# or Java style &#8211; but you miss out on all the wonderful juciness of Ruby. One of the classic examples is the Enumerable class. Coming from a statically typed language I kept finding myself write code like this:
  </p>
  
  <pre><code>for i in collection
  puts i.to_s
end</code></pre>
  
  <p>
    When you can so easily do something like:
  </p>
  
  <pre><code>collection.each {|i| puts i.to_s}</code></pre>
  
  <p>
    I&#8217;d also want to use standard inheritance to dry up my code &#8211; forgetting about the wonderous powers of mixing in modules.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Jerry Anning, USA>></strong> Can you recommend things to study after learning Core Ruby, including different frameworks, gems and external libraries?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> It&#8217;s incredibly important to be a test-a-holic. Test everything! Berate yourself if you write code that isn&#8217;t tested. Testing stuff can be real freaky hard though, but keep at it! I&#8217;m a huge fan of <a href="http://www.thoughtbot.com/projects/shoulda">shoulda</a> (although it&#8217;s quite Rails focused).
  </p>
  
  <p>
    Learn about the whys and wherefores of mocking as well, your tests will thank you for it. <a href="http://mocha.rubyforge.org/">Mocha</a> is what I use with my mocking and stubbing.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Most beginners in Ruby, would like to contribute their time, skills and expertise to a project but invariably are unaware of where and how to do so. Could you suggest some?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> There&#8217;s a gabillion open source projects to choose from, and they can all be found at github! Thanks to git (and github), contributing to a project has never been easier!
  </p>
  
  <p>
    For most beginners, the problem isn&#8217;t necessarily which project to contribute to, but &#8216;what&#8217; to contribute. A simple but affective way to contribute to a project is to write documentation. 99.99% of open source projects are severely under documented &#8211; but thanks to the beauty of rdoc, most Ruby source code has the documentation built in.
  </p>
  
  <p>
    Another way of contributing to a project is by helping out with test coverage. Run a script like rcov on a project and you&#8217;ll see which bits of code aren&#8217;t covered with tests. Believe me, it&#8217;s not a trivial thing to contribute to test coverage, and you&#8217;re also less likely to contribute damaging code if you&#8217;re worried about that sort of thing.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Victor Goff, USA>></strong> How do you see the market for Ruby Programmers in the work place, and do you see it as primarily tied to Rails and Web related work? Do you see trends in administration or other work? Whatâ€™s the future for Ruby?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> Thanks to the plethora of Virtual Machines out there I see Ruby as taking a larger role in the enterprise. With JRuby and Iron Ruby it&#8217;s already possible to contribute to large enterprise applications using the sweetest of languages. The power of Ruby also means that you end up with more maintainable code, which will lead to cost-savings across the board which I&#8217;m sure large corporations will seize upon.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> What can / should job candidates (for Ruby) do to distinguish themselves from their competition?<br /><strong>Note</strong>: The candidate has done his/her homework on the company that they are interviewing with. The candidate understands what they&#8217;re looking for, and the candidate is prepared to show them that he/she fits the bill, based on the candidate&#8217;s skills and experience. What else can the candidate do, to set themselves apart from other equally well-qualified and well-prepared candidates?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> The best way to distinguish yourself is to be a &#8216;giver&#8217; developer. What do I mean? For years and years I was a &#8216;taker&#8217; developer. Every day I&#8217;d scour the internet looking for solutions to my problems, but never contribute anything back to the community. I owe so much to random strangers all over the world! Eventually I realised that the more I gave the community, the more I got back.
  </p>
  
  <p>
    To be a &#8216;giver&#8217; developer do stuff like:
  </p>
  
  <ul>
    <li>
      write blog posts about the problems that you&#8217;ve solved &#8211; chances are that if you had the problem someone else did as well. If you don&#8217;t have a blog (or don&#8217;t want one) answer problems in forums instead.
    </li>
    <li>
      go on IRC and help newbie developers. These newbies are the future awesome developers, and one day they&#8217;ll be teaching you a thing or two!
    </li>
    <li>
      contribute to open source projects that you use a lot. The more you contribute to a project, the more you&#8217;ll learn about it.
    </li>
  </ul>
  
  <p>
    Get into the habit of being a giving developer and before you know it, you&#8217;ll find that people will be coming to YOU with job offers rather than the other way around! Future employers will be able to google your name/handle and see all the good stuff you&#8217;ve worked on.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Do you have any other suggestions for these participants (would-be Ruby developers)?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> The biggest suggestion I can offer Ruby developers is to read lots and lots of source code. Coming from a .net world where source code is typically kept under lock and key, I hadn&#8217;t developed the habit of looking at source code. Now I read as much as I can!
  </p>
  
  <p>
    A classic example is the Rails application &#8211; so many times I&#8217;ve found myself frustrated with the documentation of a given helper, but then realised that the best way to find out how a method works is to just read the source code. The more code you read, the more cool practices you&#8217;ll pick up, and the better you&#8217;ll become.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Thanks Chris for sharing your views with the RubyLearning participants.</span>
  </p>
  
  <p class="note">
    On 4th Nov. we talk to <strong>Guy Naor</strong> from USA.
  </p>
  
  <p>
    <span style="font-size: 8pt; font-family: Arial;"><i><strong>Disclaimer:</strong></i></span><br /><span style="font-size: 8pt; font-family: Arial;"><i>The opinions expressed are those of Chris O&#8217;Sullivan and do not necessarily reflect those of <strong><a href="http://rubylearning.com/">www.RubyLearning.com</a></strong>.</i></span>
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
  </ul>
  
  <p class="alert">
    <strong><em>Post supported by Blue Box Group</em>:</strong> <a href="https://boxpanel.blueboxgrp.com/public/order/partner/43921">Blue Box Group</a> is in the business of providing affordable <a href="https://boxpanel.blueboxgrp.com/public/order/partner/43921">Ruby on Rails hosting</a> solutions! They approach web hosting, virtual servers and dedicated servers differently, treating each client as a partner and working towards the common goal of success for their business. From shared Ruby on Rails hosting to giant production clusters, they have the experience, talent and equipment to make your site a success!
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Chris+O%26%238217%3BSullivan" rel="tag">Chris O&#8217;Sullivan</a>, <a href="http://technorati.com/tag/Interviews" rel="tag">Interviews</a>, <a href="http://technorati.com/tag/Little+Known+Ways+to+Ruby+Mastery" rel="tag">Little Known Ways to Ruby Mastery</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Ruby+Beginners%26%238217%3B+Questions" rel="tag">Ruby Beginners&#8217; Questions</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>
