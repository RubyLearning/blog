---
title: 'Jeremy Evans: How do I learn and master Sinatra?'
author: Satish Talim
date: 2009-07-08
layout: post
permalink: /2009/07/08/jeremy-evans-how-do-i-learn-and-master-sinatra/
thesis_keywords:
  - Jeremy Evans,Sinatra,Ruby programming,Learning Sinatra
thesis_description:
  - In the second part of the mini series "How do I learn and master Sinatra?", Jeremy Evans gives us his insights on mastering Sinatra.
topsy_short_url:
  - http://bit.ly/1HL5sM9
categories:
  - Beginners
  - Interview
  - Learn Sinatra
  - Ruby
  - Sinatra
tags:
  - Jeremy Evans
  - Learning Sinatra
  - ruby programming
  - Sinatra
---
<div>
  <p class="update">
    Welcome to the <b>second</b> installment on the <abbr title="RubyLearning">RL</abbr> blog, of a mini series &#8211; &#8220;<strong>How do I learn and master Sinatra?</strong>&#8221; &#8211; by top Rubyists using <em>Sinatra</em>. The interview series will provide insight and commentary from these notable <em>Sinatra</em> developers, with the goal of facilitating and providing answers to the questions Ruby beginners face on <em>how to learn and master Sinatra</em>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Jeremy Evans, could you tell us something about yourself &#8211; your background, where you are based?</span>
  </p>
  
  <p class="block">
    <img class="alignright" title="Jeremy Evans" src="http://rubylearning.com/images/jeremy-125.jpg" alt="Jeremy Evans" /><strong>Jeremy Evans>></strong> I am <a href="http://code.jeremyevans.net/">Jeremy Evans</a> and I do computer work for the government in Sacramento, CA, USA. I&#8217;ve been using Ruby since 2004.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Are there any pre-requisites for a person to start learning Sinatra?</span>
  </p>
  
  <p>
    <strong>Jeremy>></strong> I think you need a basic understanding of Ruby syntax, but once you have that you can pretty much dive right in. Sinatra is simple enough to understand that not much else should be required.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How should one start learning Sinatra?</span>
  </p>
  
  <p>
    <strong>Jeremy>></strong> I&#8217;d recommend reading the documentation on the Sinatra website, especially the README, FAQ, and the Sinatra Book.
  </p>
  
  <p>
    After that, just start coding an application, referring to those documentation sources and the RDoc API documentation.
  </p>
  
  <blockquote class="right">
    <p>
      Sinatra &#8211; quickly create tiny web apps and services
    </p>
  </blockquote>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Which area of Sinatra should a beginner pay particular attention to?</span>
  </p>
  
  <p>
    <strong>Jeremy>></strong> I&#8217;m not sure a beginner should focus on a particular aspect. The focus should depend on the application the programmer wants to create.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is the official documentation on Sinatra good enough for a beginner? Are there areas which need improvement or need to be re-written</span>
  </p>
  
  <p>
    <strong>Jeremy>></strong> This is hard for me to say, as I was already fairly experienced with Ruby when I started learning Sinatra (and there wasn&#8217;t nearly as much documentation back then), but I think the introductory documentation is good enough for a beginner.
  </p>
  
  <p>
    If there is one aspect of the documentation that could be improved, I think it&#8217;s that the RDoc API documentation could be more complete, as some methods are undocumented.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Sequel, DataMapper, ActiveRecord &#8211; which one would you recommend to use with Sinatra and why?</span>
  </p>
  
  <p>
    <strong>Jeremy>></strong> As I&#8217;m the maintainer of <a href="http://sequel.rubyforge.org/">Sequel</a>, I&#8217;m obviously biased towards Sequel, at least if you are using an SQL database. If you are using a non-SQL database and want ORM-like behavior that the native adapter doesn&#8217;t provide, DataMapper may be a good choice. If you want to use ActiveRecord, you need to make sure your application is single threaded, or use a Rack middleware to clean up the connection pool manually.
  </p>
  
  <p>
    I think Sequel and Sinatra are a good fit for each other as they both are simple and flexible. Both allow you to accomplish a lot with not much code.
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/sinatralogo.jpg" alt="Sinatra Icon" title="Sinatra micro-framework" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is an understanding of Rack important while learning Sinatra? Why? Which area of Rack should one be really comfortable with?</span>
  </p>
  
  <p>
    <strong>Jeremy>></strong> I think an understanding of Rack is helpful, but not required. Learning how Rack works, especially how you can use middleware to reuse common code between applications (even if they use different frameworks), is definitely worth the small amount of time it takes. However, if you just want to learn Sinatra basics, I wouldn&#8217;t focus on learning Rack first.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How should one hone one&#8217;s skills in Sinatra?</span>
  </p>
  
  <p>
    <strong>Jeremy>></strong> Like everything else in programming, once you have the basics, the best way to improve your skills is to practice. With Sinatra, the best way to practice is to think of a web site/application/service that you want to create, and use Sinatra to create it. As you code, you&#8217;ll probably come across situations where you know what result you want, but not how to get there. That&#8217;s when you need to do some research in the API docs or the source code. If you are still unsure after doing some research, jump on the #sinatra IRC channel and ask questions there.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> What type of projects should a beginner work on to gain more expertise in Sinatra?</span>
  </p>
  
  <p>
    <strong>Jeremy>></strong> <span style="background-color: #FFFFCC;">Start with a small project. I&#8217;d recommend a basic web site with a few pages, but the important thing is to pick something that interests you</span>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Could you suggest some web services that a Sinatra beginner could develop himself / herself?</span>
  </p>
  
  <p>
    <strong>Jeremy>></strong> A fairly simple one would be a proxy service where the user can provide a URL and the Sinatra web service could retrieve the page and return it to the user. A beginner would need to do some research on Ruby&#8217;s standard library (<b>net/http</b><sup class='footnote'><a href='#fn-2574-1' id='fnref-2574-1'>1</a></sup> or <b>open-uri</b>), but the Sinatra code for a simple proxy service should only be a few lines.
  </p>
  
  <p>
    Another web service that a beginning Sinatra user could create would be a URL shortener<sup class='footnote'><a href='#fn-2574-2' id='fnref-2574-2'>2</a></sup>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Anything else you would like to add?</span>
  </p>
  
  <p>
    <strong>Jeremy>></strong> The best way to learn is to have fun doing so, so pick projects that interest you.
  </p>
  
  <p>
    <span style="color:#CC3333;"><em>Thank you Jeremy. In case you have any queries and/or questions, kindly post your questions here (as comments to this blog post) and Jeremy would be glad to answer.</em></span>
  </p>
  
  <p>
    <b>Others in this series:</b>
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/blog/2015/01/07/corey-donohoe-how-do-i-learn-and-master-sinatra/">Corey Donohoe</a>
    </li>
  </ul>
  
  <p class="alert">
    <strong><em>Post supported by 1st Easy Limited</em>:</strong> UK based 1st Easy Limited offer Sinatra and Rails hosting running on a Phusion Passenger (mod_rails) and LAMP stack. If you want to try your hand at developing with Sinatra, why not let them arrange a <a href="http://www.1steasy.com/ruby-on-rails.htm#try">trial hosting account</a> for you? You&#8217;ll get to deploy your app, with full technical support from their team!
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Jeremy+Evans" rel="tag">Jeremy Evans</a>, <a href="http://technorati.com/tag/Sinatra" rel="tag">Sinatra</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>, <a href="http://technorati.com/tag/Learning+Sinatra" rel="tag">Learning Sinatra</a>

<div class='footnotes'>
  <div class='footnotedivider'>
  </div>
  
  <ol>
    <li id='fn-2574-1'>
      Read 14.20 A Real-World HTTP Client from the <strong>Ruby Cookbook</strong>. <span class='footnotereverse'><a href='#fnref-2574-1'>&#8617;</a></span>
    </li>
    <li id='fn-2574-2'>
      Read <a href="http://blog.saush.com/2009/04/clone-tinyurl-in-40-lines-of-ruby-code/">Clone TinyURL in 40 lines of Ruby code</a>. <span class='footnotereverse'><a href='#fnref-2574-2'>&#8617;</a></span>
    </li>
  </ol>
</div>
