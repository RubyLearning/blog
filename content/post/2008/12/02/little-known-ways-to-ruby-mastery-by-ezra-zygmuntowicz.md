---
author: Satish Talim
categories:
- Beginners
- Interview
- Ruby
- Ruby Masters
date: 2008-12-02
description:
- The Path to Ruby Mastery Interview Series by Ruby Masters, provides guidance to
  and answers questions confronting Ruby beginners from across the globe.
keywords:
- ruby for beginners,ruby beginners,ruby programming,ruby on rails blog,rails blog,rails
  tutorials,ruby beginners\' questions,little known ways to ruby mastery,ruby masters,interviews,ruby,the
  ruby programming language,Ezra Zygmuntowicz,merb
layout: post
permalink: /2008/12/02/little-known-ways-to-ruby-mastery-by-ezra-zygmuntowicz/
tags:
- Ezra Zygmuntowicz
- interviews
- Little Known Ways to Ruby Mastery
- Merb
- Ruby
- Ruby Beginners' Questions
- The Ruby Programming Language
title: Little Known Ways to Ruby Mastery by Ezra Zygmuntowicz
topsy_short_url:
- http://bit.ly/cEXQnv
willian.molinari@gmail.com:
- pothix
---

<div>
  <h3>
    A weekly series from the Ruby Masters
  </h3>
  
  <p class="update">
    Welcome to the next installment of the weekly interview series on the <abbr title="RubyLearning">RL</abbr> blog &#8211; &#8220;<strong>Path to Ruby Mastery</strong>&#8221; &#8211; by top trainers and developers in the <strong>Ruby community</strong>, from across the globe. The interview series will provide insight and commentary from these notable Ruby trainers and developers, with the goal of facilitating and providing answers to the questions <strong>Ruby beginners</strong> face. We welcome your suggestions for interviewees and questions. Look for a new post every Tuesday!
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/zyg.jpg" alt="Ezra Zygmuntowicz, USA" title="Ezra Zygmuntowicz, USA" width="100" height="118" />
  </p>
  
  <p>
    <span class="drop_cap">T</span>his week, we&#8217;re happy to have <strong>Ezra Zygmuntowicz</strong> from USA.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Welcome, Ezra and thanks for taking out time to share your thoughts. For the benefit of the readers, could you tell us something about your self?</span>
  </p>
  
  <p>
    <strong>Ezra>></strong> My name is Ezra Zygmuntowicz. I&#8217;ve been using Ruby for 5 years or so and Rails since it&#8217;s first public release in 2004. I am the founder of EngineYard.com, a fully managed Ruby application hosting service. I have a number of open source projects including <a href="http://www.merbivore.com/"><strong>Merb</strong></a><sup class='footnote'><a href='#fn-910-1' id='fnref-910-1'>1</a></sup>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Willian Molinari, Brazil>></strong> How should one go about learning the Ruby language? What material (books, eBooks, online tutorials etc.) would you recommend?</span>
  </p>
  
  <p>
    <strong>Ezra>></strong> I think the best way to learn any language is to come up with a small project that will be useful to you and go ahead and start building it. You will learn much quicker working on something you need then you would working on standard examples form books and other online material. Research your problem along the way and go ask questions on irc and ruby-talk, you will find ruby folks are most helpful.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Keith Brady, Australia>></strong> What are the pros and cons of Ruby that are being discussed in the development community and what is your opinion on that?</span>
  </p>
  
  <p>
    <strong>Ezra>></strong> The pros of Ruby are the super fast development cycle. You can truly build bigger software faster with a smaller team then other languages. Ruby is also a very fun and elegant language to use, you will find yourself directly expressing your thoughts with Ruby code before too long.
  </p>
  
  <p>
    The cons of Ruby are with the current implementation of the interpreter. It is not the fastest language around and has a very conservative garbage collector which means Ruby tends to use a lot of memory if you aren&#8217;t careful. We are working on fixing these issues with our <strong>Rubinius</strong> project.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Jerry Anning, USA>></strong> Can you recommend things to study after learning Core Ruby, including different frameworks, gems and external libraries?</span>
  </p>
  
  <p>
    <strong>Ezra>></strong> I find that the best way to write code or libraries in Ruby is to write out the end user code exactly how you want the API/DSL to look and then use that as a test case and go implement the backend that can run that code. This makes for very fluent interfaces and is a very nice way to develop ruby code.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Most beginners in Ruby, would like to contribute their time, skills and expertise to a project but invariably are unaware of where and how to do so. Could you suggest some?</span>
  </p>
  
  <p>
    <strong>Ezra>></strong> Get yourself a github account and start forking a few projects and poking around. Find one you are interested in and contribute some tests or docs to help yourself get up to speed with the project. Before you know it, you will be fluent in many libraries and techniques.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Keith Brady, Australia>></strong> What types of applications are currently being developed in Ruby and what changes do you foresee over the next year or two?</span>
  </p>
  
  <p>
    <strong>Ezra>></strong> Of course there are tons of Rails and Merb web applications being built these days. But I see Ruby being used for many other things as well. Folks have come for the Rails and stayed for the Ruby. I see folks using Ruby to build all kinds of backends and automation systems.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Victor Goff, USA>></strong> How do you see the market for Ruby Programmers in the work place, and do you see it as primarily tied to Rails and Web related work? Do you see trends in administration or other work? Whatâ€™s the future for Ruby?</span>
  </p>
  
  <p>
    <strong>Ezra>></strong> <em>I see a huge demand for Ruby programmers and not near enough supply of good developers</em>. Of course folks are always hiring for Rails web developers but I also see lots of jobs for Ruby that are not web related. Ruby is being used more and more as enterprise glue language and I think it really shins in that space.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> What can / should job candidates (for Ruby) do to distinguish themselves from their competition?<br /><strong>Note</strong>: The candidate has done his/her homework on the company that they are interviewing with. The candidate understands what they&#8217;re looking for, and the candidate is prepared to show them that he/she fits the bill, based on the candidate&#8217;s skills and experience. What else can the candidate do, to set themselves apart from other equally well-qualified and well-prepared candidates?</span>
  </p>
  
  <p>
    <strong>Ezra>></strong> Have a blog with technical posts on it. Have some open source projects or code you have contributed to an open source project you can send as example code. Nothing is a better indicator of someone&#8217;s worthiness than having open source code out there that I can see and play with, to get a feel for how someone thinks.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Do you have any other suggestions for these participants (would-be Ruby developers)?</span>
  </p>
  
  <p>
    <strong>Ezra>></strong> Spend the time to really learn the Ruby language and not just libraries like Rails. It will pay large dividends.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Thanks Ezra for sharing your views with the RubyLearning participants.</span>
  </p>
  
  <p class="note">
    On 9th Dec. we talk to <strong>Chris Matthieu</strong> from USA.
  </p>
  
  <p>
    <span style="font-size: 8pt; font-family: Arial;"><i><strong>Disclaimer:</strong></i></span><br /><span style="font-size: 8pt; font-family: Arial;"><i>The opinions expressed are those of Ezra Zygmuntowicz and do not necessarily reflect those of <strong><a href="http://rubylearning.com/">www.RubyLearning.com</a></strong>.</i></span>
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
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Interviews" rel="tag">Interviews</a>, <a href="http://technorati.com/tag/Little+Known+Ways+to+Ruby+Mastery" rel="tag">Little Known Ways to Ruby Mastery</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Ruby+Beginners%26%238217%3B+Questions" rel="tag">Ruby Beginners&#8217; Questions</a>, <a href="http://technorati.com/tag/Ezra+Zygmuntowicz" rel="tag">Ezra Zygmuntowicz</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>

<div class='footnotes'>
  <div class='footnotedivider'>
  </div>
  
  <ol>
    <li id='fn-910-1'>
      RubyLearning&#8217;s new course &#8220;<strong>Introduction to Merb</strong>&#8221; will be available to all, this month. Watch this blog for an announcement. <span class='footnotereverse'><a href='#fnref-910-1'>&#8617;</a></span>
    </li>
  </ol>
</div>
