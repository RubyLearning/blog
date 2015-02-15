---
title: What are the Twelve Rules of Sinatra?
author: Satish Talim
date: 2009-07-19
layout: post
permalink: /2009/07/19/what-are-the-twelve-rules-of-sinatra/
thesis_description:
  - The blog post discusses the 12 rules of Sinatra, the micro-web framework.
thesis_keywords:
  - Jeremy Evans,Sinatra,Ruby programming,Learning Sinatra,Twelve Rules of Sinatra
topsy_short_url:
  - 
categories:
  - Beginners
  - Ruby
  - Sinatra
tags:
  - Jeremy Evans
  - Learning Sinatra
  - ruby programming
  - Sinatra
  - Twelve Rules of Sinatra
---
<div>
  <h3>
    The Twelve Rules of Sinatra
  </h3>
  
  <p class="update center">
    <strong>The Twelve Rules of Sinatra: <a href="http://rubylearning.com/data/Sinatra12Rules.pdf">Download this as a Free Report</a>.</strong>
  </p>
  
  <p>
    Recently, I was reading Scott Adams&#8217; (of Dilbert fame) blog post &#8220;<a href="http://www.dilbert.com/blog/entry/rule_of_twelve">Rule of Twelve</a>&#8221; where he stated:
  </p>
  
  <blockquote>
    <p>
      The Rule of Twelve states that if you know twelve concepts about a given topic you will look like an expert to people who only know two or three. If you learn more than twelve concepts about a topic, the value of each additional one drops off considerably. Allow me to be the first to confess that twelve is not a magic and inviolable number.
    </p>
  </blockquote>
  
  <p>
    He also wrote a follow-up post to support his statement: &#8220;<a href="http://www.dilbert.com/blog/entry/twelve_rules_of_energy_efficient_building/">Twelve Rules of Energy Efficient Building</a>&#8220;.
  </p>
  
  <p>
    This made me wonder, could we apply the same &#8220;Rule of Twelve&#8221; to <strong>Sinatra</strong>?
  </p>
  
  <p class="block">
    <img class="alignright" title="Jeremy Evans" src="http://rubylearning.com/images/jeremy-125.jpg" alt="Jeremy Evans" />Here is <strong><a href="http://code.jeremyevans.net/">Jeremy Evans&#8217;</a></strong> take on this:
  </p>
  
  <ol>
    <li>
      Just like Rails, keep your controller/actions simple, and put most of your business logic in your models. This makes testing and code reuse easier.
    </li>
    <li>
      Also like Rails, avoid excess logic in your views. Add helper methods that the views call to keep the views clean.
    </li>
    <li>
      Unlike Rails, read the Sinatra source. The main part is a single file that&#8217;s around 1000 lines of quite understandable Ruby code. Just reading it will probably make you a better programmer.
    </li>
    <li>
      If you have a problem that you think other people probably have (e.g. a Rails-like flash), look first for a Rack middleware that handles it, rather than recreating the wheel.
    </li>
    <li>
      Untested code will probably break sooner than later, so if you want the code to work in the future, write tests.
    </li>
  </ol>
  
  <p>
    <span style="color:#CC3333;"><em>Well, Jeremy has set the ball rolling. <b>What&#8217;s your take on this?</b> Kindly post your thoughts as comments to this blog post. Looking forward to some interesting read.</em></span>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Jeremy+Evans" rel="tag">Jeremy Evans</a>, <a href="http://technorati.com/tag/Sinatra" rel="tag">Sinatra</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>, <a href="http://technorati.com/tag/Learning+Sinatra" rel="tag">Learning Sinatra</a>, <a href="http://technorati.com/tag/Twelve+Rules+of+Sinatra" rel="tag">Twelve Rules of Sinatra</a>
