---
author: Satish Talim
categories:
- Interview
- Ruby
- Sinatra
- Twitter
date: 2009-04-28
description:
- RubyLearning caught up with Luke Franci and Barry Hess creators of Follow Cost,
  in this interview.
keywords:
- Follow Cost,Twitter,Luke Francl,Barry Hess,Merb,Sinatra, Ruby
layout: post
permalink: /2009/04/28/follow-cost-a-sinatra-app-for-twitter/
tags:
- Barry Hess
- Follow Cost
- Luke Francl
- Merb
- Ruby
- Sinatra
- Twitter
title: 'Follow Cost: A Sinatra app for Twitter'
---

<div>
  <p class="alert">
    RubyLearning caught up with <strong>Luke Francl</strong> and <strong>Barry Hess</strong> creators of <a href="http://followcost.com/">Follow Cost</a> &#8211; a <strong>Twitter</strong> tool to help people decide if following someone is worth it, and talked to them about Follow Cost and Sinatra in this interview.
  </p>
  
  <p>
    <img class="alignright" title="Luke Francl" src="http://www.rubylearning.com/images/luke-headshot.jpg" alt="Luke Francl" width="125" height="125" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Luke and Barry, could you tell us something about yourselves &#8211; your backgrounds, where both of you are based?</span>
  </p>
  
  <p>
    <strong>Luke>></strong> I&#8217;m a Rails developer based in Minneapolis, USA. I worked as a Java developer for a number of years before making the jump to Ruby. I&#8217;ve been doing this for about 3 years now.
  </p>
  
  <p>
    <strong>Barry>></strong> I work with Ruby and Rails from a rural area, an hour south of Minneapolis. The start of my career was in a very corporate environment, mostly working with Java. I&#8217;ve been messing with Ruby for nearly 3 years.
  </p>
  
  <p>
    <img class="alignright" title="Barry Hess" src="http://www.rubylearning.com/images/barry_hess.jpg" alt="Barry Hess" width="125" height="125" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Barry, you are the &#8220;Prime Hacker&#8221; at Iridesco. Tell us something about this.</span>
  </p>
  
  <p>
    <strong>Barry>></strong> I&#8217;ve worked with <a href="http://iridesco.com/">Iridesco</a> for over 2 years now. We&#8217;re a 4-man team: 2 founders and jacks-of-all-trade in New York City, a programmer in Transylvania, and me. So we&#8217;re rather distributed. Our primary app is <a href="http://www.getharvest.com/">Harvest</a>, a time tracking and invoicing app. To help us work as a distributed team, we built <a href="http://coopapp.com/">Co-op</a>, a sort of private, group Twitter that ties in with Harvest rather nicely.
  </p>
  
  <p>
    Titles always give me trouble. Am I a software engineer? Developer? Programmer? Without a corporate overlord to tell me I am a Programmer IV or some such, it becomes rather difficult. When Danny Wen, one of Iridesco&#8217;s co-founders, signed me up for this year&#8217;s SXSWi conference with the title Prime Hacker, well, I thought that title was better than any I had thought of!
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> What is <strong>Follow Cost</strong>?</span>
  </p>
  
  <p>
    Follow Cost is a tool to help people decide if following someone is worth it. Follow Cost will tell you how often someone tweets. Different people have different standards for how much is &#8220;too much&#8221; and Follow Cost can help you decide for yourself, but we do give a special warning for people who tweet more than Robert Scoble. 1/1000th of Scoble&#8217;s average daily output is called a &#8220;milliscoble.&#8221;
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> What was the idea behind Follow Cost ?</span>
  </p>
  
  <p>
    <strong>Luke>></strong> Barry and I and a few other Minnesota developers were on a road trip to the WindyCityRails conference in Chicago. We were complaining about how certain people just Tweet way too much, and how it would be cool if there was a tool to warn you before following. That was the genesis of Follow Cost. After I got home, I whipped up a couple mockups and asked Barry if he wanted to help build it.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Why did you decide to use Sinatra for Follow Cost ?</span>
  </p>
  
  <p>
    For such a simple app, Sinatra was a really good fit. Originally, Follow Cost did not even have a database &#8212; it queried Twitter, then page cached the results. But the main reason we wanted to use Sinatra was to try something new. (This was also our first foray into jQuery.) We&#8217;ve both been building Rails apps for years, and we wanted to try something else.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> For a person new to web development, how can Sinatra help?</span>
  </p>
  
  <p>
    <strong>Luke>></strong> I think that Sinatra brings the power of Ruby with the fast-paced development of PHP. One of the things I always liked about PHP was that you could get something running really quickly. Just upload it to the server and you were all set. With Passenger, developing in Sinatra is very much like that, except in a nice language like Ruby instead of a crufty one like PHP.
  </p>
  
  <p>
    <strong>Barry>></strong> Sinatra allows a beginner to see results quickly. Even in your local environment Sinatra gets you from code to seeing something in the browser faster than Rails. Deploying a quick Sinatra practice app to a shared host like Dreamhost, which uses Passenger, is a piece of cake compared to when we started with Rails. In our day, we also deployed up hill both ways, in the snow.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How can one go about learning Sinatra?</span>
  </p>
  
  <p>
    Well, we heard there&#8217;s this <b>RubyLearning class<sup class='footnote'><a href='#fn-1931-1' id='fnref-1931-1'>1</a></sup></b> on it&#8230;
  </p>
  
  <p>
    We went about it by following the <a href="http://www.sinatrarb.com/book.html">Sinatra book</a> and the source code. It&#8217;s nice that Sinatra&#8217;s source is so small because you can easily read it and understand it.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Do you have any suggestions for RubyLearningâ€™s &#8220;<a href="http://rubylearning.com/blog/2009/04/07/new-sinatra-course-announced/">Introduction to Sinatra</a>&#8221; course participants?</span>
  </p>
  
  <p>
    Pick something in Sinatra&#8217;s sweet spot &#8212; small applications that need to be dynamic &#8212; and have fun with it! We find Sinatra to be a perfect tool to tie into all the hot social network API&#8217;s out there. And remember, the world can always use one more app based on the Twitter API!
  </p>
  
  <p>
    <span style="color:#CC3333;"><em>Thank you Luke and Barry. In case you have any queries and/or questions, kindly post your questions here (as comments to this blog post) and they would be glad to answer.</em></span>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Follow+Cost" rel="tag">Follow Cost</a>, <a href="http://technorati.com/tag/Twitter" rel="tag">Twitter</a>, <a href="http://technorati.com/tag/Luke+Francl" rel="tag">Luke Francl</a>, <a href="http://technorati.com/tag/Barry+Hess" rel="tag">Barry Hess</a>, <a href="http://technorati.com/tag/Merb" rel="tag">Merb</a>, <a href="http://technorati.com/tag/Sinatra" rel="tag">Sinatra</a>, <a href="http://technorati.com/tag/Ruby" rel="tag"> Ruby</a>

<div class='footnotes'>
  <div class='footnotedivider'>
  </div>
  
  <ol>
    <li id='fn-1931-1'>
      <strong>Introduction to Sinatra</strong>: Here are the <a href="http://rubylearning.com/blog/2009/04/07/new-sinatra-course-announced/">course details</a>. <span class='footnotereverse'><a href='#fnref-1931-1'>&#8617;</a></span>
    </li>
  </ol>
</div>
