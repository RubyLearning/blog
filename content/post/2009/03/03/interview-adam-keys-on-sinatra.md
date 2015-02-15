---
title: 'Interview: Adam Keys on Sinatra'
author: Satish Talim
date: 2009-03-03
layout: post
permalink: /2009/03/03/interview-adam-keys-on-sinatra/
keywords:
  - Adam Keys,Interviews,Ruby,Sinatra,The Ruby Programming Language,web framework
description:
  - |
    Adam Keys talks to RubyLearning's "Introduction to Sinatra" course participants on Sinatra micro web framework.
topsy_short_url:
  - http://bit.ly/bD5kFq
categories:
  - Interview
  - Ruby
  - Sinatra
tags:
  - Adam Keys
  - interviews
  - Ruby
  - Sinatra
  - The Ruby Programming Language
  - web framework
---
<div>
  <p class="alert">
    On the eve of the first ever online &#8220;<strong>Introduction to Sinatra</strong>&#8221; course, Satish Talim of RubyLearning caught up with <strong>Adam Keys</strong> and talked to him on <strong>Sinatra</strong>, in this interview.
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/AdamKeys.jpg" alt="Adam Keys, USA" title="Adam Keys, USA" width="125" height="125" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Welcome, Adam and thanks for taking out time to share your thoughts. For the benefit of the readers, could you tell us something about your self?</span>
  </p>
  
  <p>
    <strong>Adam Keys>></strong> I enjoy exploring all sorts of topics that are coincidental with Ruby: information design, functional languages, linguistics, architecture and other sorts of semi-boring topics. Entertaining people makes me happy. I live with my wife, three dogs and two cats in Dallas, TX. My website is <a href="http://therealadam.com/">http://therealadam.com/</a> and I&#8217;m <a href="http://twitter.com/therealadam">therealadam</a> on Twitter.
  </p>
  
  <blockquote class="right">
    <p>
      Sinatra &#8211; quickly create tiny web apps and services
    </p>
  </blockquote>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> What&#8217;s Sinatra and how did you get involved with it?</span>
  </p>
  
  <p>
    <strong>Adam>></strong> Sinatra is a tiny little library for writing web applications. I like to say it&#8217;s the smallest possible DSL for describing HTTP interactions. <span style="background-color: #FFFFCC;">It&#8217;s great for building small to medium-size web apps and also for building web APIs, REST services, and web hooks</span>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> For a person new to web development, how can Sinatra help?</span>
  </p>
  
  <p>
    <strong>Adam>></strong> Sinatra is very close to how HTTP works, so it&#8217;s a great introduction to the workings of the protocol and how it&#8217;s used to make REST-structured apps. Further, Sinatra doesn&#8217;t put much overhead in your way. You get right down to writing the interesting part of your app or figuring out how to extract infrastructure to make writing the interesting part of your app easier.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How can one go about learning Sinatra?</span>
  </p>
  
  <p>
    <strong>Adam>></strong> Check out my screencast, &#8220;<a href="http://www.pragprog.com/screencasts/v-aksinatra/classy-web-development-with-sinatra">Classy Web Development with Sinatra</a>&#8220;!
  </p>
  
  <p>
    If you&#8217;re experienced with Ruby, just give the Sinatra sources a read. It&#8217;s less than two thousand lines and pretty straight-forward to understand.
  </p>
  
  <p>
    If you&#8217;re less experienced, I recommend just searching for Sinatra applications and add-ons on GitHub and reading their code. I learned a lot of great things this way.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Where all can Sinatra be used?</span>
  </p>
  
  <p>
    <strong>Adam>></strong> It&#8217;s great for building mashups. My friend and co-worker Bruce Williams used Twitter data to build Front Row to History when he went to Obama&#8217;s election-day rally. Sinatra&#8217;s small footprint, both resource-wise and conceptually, made it easy to build this application in less than twenty-four hours.
  </p>
  
  <p>
    There are lots of interesting little <a href="http://github.com/sr/git-wiki/tree/master">wikis</a> and <a href="http://github.com/rtomayko/wink/tree/master">weblogs</a> written in Sinatra. There&#8217;s also a neat gem documentation server. Sinatra is fun for building these apps because it you can mix and match the libraries you are interested in experimenting with.
  </p>
  
  <p>
    Sinatra&#8217;s ideal for building services. It&#8217;s quite easy to sketch out the resources a REST services presents and then write it directly in Sinatra.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Who all have been using Sinatra and in what way?</span>
  </p>
  
  <p>
    <strong>Adam>></strong> A couple of the guys at <a href="http://heroku.com/">Heroku</a> work on Sinatra. I believe they are using it to compose their service out of many smaller apps.
  </p>
  
  <p>
    <a href="http://github.com/">GitHub<sup class='footnote'><a href='#fn-1508-1' id='fnref-1508-1'>1</a></sup></a> released sample apps for their web hooks API as Sinatra apps. Lots of people forked those apps to make new apps that integrate with the services their interested in.
  </p>
  
  <p>
    At FiveRuns, we use Sinatra in our metrics collection API for <a href="http://dash.fiveruns.com/">Dash</a>. Every number in the system is uploaded to a Sinatra app before it proceeds through our processing queues.
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/sinatralogo.jpg" alt="Sinatra Icon" title="Sinatra microframework" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is deploying a Sinatra app easy? What would your recommend?</span>
  </p>
  
  <p>
    <strong>Adam>></strong> Since Sinatra is built on top of Rack, you&#8217;ve got options. You can use Phusion Passenger to deploy with Apache. If your needs are more sophisticated, you can use Mongrel, Thin, Swiftiply or any other Rack-compliant server. And it&#8217;s all just files, so you can use all your favorite tools: Capistrano or Vlad, Subversion or Git.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Do you have any suggestions for RubyLearning&#8217;s &#8221; <strong>Introduction to Sinatra<sup class='footnote'><a href='#fn-1508-2' id='fnref-1508-2'>2</a></sup></strong> &#8221; course participants?</span>
  </p>
  
  <p>
    <strong>Adam>></strong> Using Sinatra is a great opportunity to learn about what you miss from other, larger frameworks. Once you&#8217;ve decided you need some feature, write it yourself. I&#8217;ve found this is a fantastic way to learn about web frameworks.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Thanks Adam<sup class='footnote'><a href='#fn-1508-3' id='fnref-1508-3'>3</a></sup> for sharing your views with the RubyLearning Sinatra course participants.</span>
  </p>
  
  <p>
    <span style="font-size: 8pt; font-family: Arial;"><i><strong>Disclaimer:</strong></i></span><br /><span style="font-size: 8pt; font-family: Arial;"><i>The opinions expressed are those of Adam Keys and do not necessarily reflect those of <strong><a href="http://rubylearning.org/">RubyLearning.org</a></strong>.</i></span>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Adam+Keys" rel="tag">Adam Keys</a>, <a href="http://technorati.com/tag/Interviews" rel="tag">Interviews</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Sinatra" rel="tag">Sinatra</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>

<div class='footnotes'>
  <div class='footnotedivider'>
  </div>
  
  <ol>
    <li id='fn-1508-1'>
      <strong>Introduction to Git & GitHub</strong>: Here are the <a href="http://rubylearning.com/blog/2009/02/10/git-and-github-a-free-course/">course details</a>. <span class='footnotereverse'><a href='#fnref-1508-1'>&#8617;</a></span>
    </li>
    <li id='fn-1508-2'>
      <strong>Introduction to Sinatra</strong>: Here are the <a href="http://rubylearning.com/blog/2009/02/25/introduction-to-sinatra-a-new-course/">course details</a>. <span class='footnotereverse'><a href='#fnref-1508-2'>&#8617;</a></span>
    </li>
    <li id='fn-1508-3'>
      An <a href="http://rubylearning.com/blog/2008/04/22/ruby-interview-adam-keys-of-fiveruns/">earlier interview</a> of Adam by RubyLearning. <span class='footnotereverse'><a href='#fnref-1508-3'>&#8617;</a></span>
    </li>
  </ol>
</div>
