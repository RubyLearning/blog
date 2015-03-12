---
author: Satish Talim
categories:
- Beginners
- Interview
- Learn Sinatra
- Ruby
- Sinatra
date: 2009-07-21
layout: post
permalink: /2009/07/21/carlos-gabaldon-how-do-i-learn-and-master-sinatra/
tags:
- Carlos Gabaldon
- Learning Sinatra
- ruby programming
- Sinatra
thesis_description:
- In the eight part of the mini series "How do I learn and master Sinatra?", Carlos
  Gabaldon gives us his insights on mastering Sinatra.
thesis_keywords:
- Carlos Gabaldon,Sinatra,Ruby programming,Learning Sinatra
title: 'Carlos Gabaldon: How do I learn and master Sinatra?'
topsy_short_url:
- http://bit.ly/1xQQZgp
---

<div>
  <p class="update">
    Welcome to the <b>eight</b> installment on the <abbr title="RubyLearning">RL</abbr> blog, of a mini series &#8211; &#8220;<strong>How do I learn and master Sinatra?</strong>&#8221; &#8211; by top Rubyists using <em>Sinatra</em>. The interview series will provide insight and commentary from these notable <em>Sinatra</em> developers, with the goal of facilitating and providing answers to the questions Ruby beginners face on <em>how to learn and master Sinatra</em>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Carlos Gabaldon, could you tell us something about yourself &#8211; your background, where you are based?</span>
  </p>
  
  <p class="block">
    <img class="alignright" title="Carlos Gabaldon" src="http://www.rubylearning.com/images/Carlos_Gabaldon_125.jpg" alt="Carlos Gabaldon" /><strong>Carlos Gabaldon>></strong> I’m <a href="http://carlosgabaldon.com/">Carlos Gabaldon</a>. I have been in software development for over 10 years. I am currently working as a software architect for the Apollo Group, Inc. I am based in Chandler, AZ. I have experience in multiple languages and platforms: C, C++, C#, Java, Small Talk, Lisp, Erlang, Ruby, Objective-C, Python, and PHP on Linux, FreeBSD, and Windows.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Are there any pre-requisites for a person to start learning Sinatra?</span>
  </p>
  
  <p>
    <strong>Carlos>></strong> A basic understanding of Ruby and HTTP are very helpful. Since Sinatra is essentially a DSL on top of Rack, which is just an abstraction layer for dealing with HTTP, understanding Ruby&#8217;s implementation of blocks, closures, and hashes will make working with Sinatra a little more straight forward.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How should one start learning Sinatra?</span>
  </p>
  
  <p>
    <strong>Carlos>></strong> The best way to learn is to download the latest version of <a href="http://www.sinatrarb.com/">Sinatra</a> and read the documentation to get your first app running. The docs are great way to start learning. After you have gone through all the examples, I suggest building your sample application, that will allow you to explore all the various aspects of Sinatra. By building a blog or some type of social web app it will force you to learn how to do things like authentication, authorization, session management, and database interaction. Also, spelunking the <a href="http://github.com/sinatra/sinatra/tree/master">source code</a> on GitHub is a great way to learn the internals.
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
    <strong>Carlos>></strong> For a beginner I would suggest focusing on understanding Routes, Handlers, Views, Helpers, Authentication, and Models. These are the core things required to build most basic web applications.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is the official documentation on Sinatra good enough for a beginner? Are there areas which need improvement or need to be re-written</span>
  </p>
  
  <p>
    <strong>Carlos>></strong> The official docs are great for a beginner to learn Sinatra. The <a href="http://www.sinatrarb.com/book.html">Sinatra book</a> looks very promising once it is complete, it just needs more people like myself contributing to the completion.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Sequel, DataMapper, ActiveRecord &#8211; which one would you recommend to use with Sinatra and why?</span>
  </p>
  
  <p>
    <strong>Carlos>></strong> It depends on your background. If you are coming to Sinatra from the Rails community you will most likely be more comfortable with ActiveRecord; like wise if you are coming from Merb you will be more familiar with DataMapper, since it is used pretty heavily in that community. For basic little web applications I think any of the above ORM&#8217;s are great. I personally really like Sequel and DataMapper since they give you much more control over your table and object mappings as well as your custom SQL. ActiveRecord abstracts to much of the SQL for my tastes which makes optimization of SQL queries very difficult. If someone plans to build a high performance web site using Sinatra or any other web framework I would recommend against using any ORM &#8211; you want to have a lot of control over your SQL, you do not want the join queries being generated by an ORM.
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/sinatralogo.jpg" alt="Sinatra Icon" title="Sinatra micro-framework" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is an understanding of Rack important while learning Sinatra? Why? Which area of Rack should one be really comfortable with?</span>
  </p>
  
  <p>
    <strong>Carlos>></strong> I do not feel an understanding of Rack is important for someone learning Sinatra. Once you have a solid understanding of Sinatra, then learning Rack will help one with building middleware.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How should one hone one&#8217;s skills in Sinatra?</span>
  </p>
  
  <p>
    <strong>Carlos>></strong> Build a lot of different types of web apps, learn Ruby, study Sinatra&#8217;s source code, and read great sites like yours.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> What type of projects should a beginner work on to gain more expertise in Sinatra?</span>
  </p>
  
  <p>
    <strong>Carlos>></strong> Blogs, Community Sites, really anything.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Could you suggest some web services that a Sinatra beginner could develop himself / herself?</span>
  </p>
  
  <p>
    <strong>Carlos>></strong> I would suggest building social integration type services on top of the Twitter or Facebook api&#8217;s. There is a lot of great open web service api&#8217;s out there to some great communities, building services that can integrate various communities is always cool.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Anything else you would like to add?</span>
  </p>
  
  <p>
    <strong>Carlos>></strong> Sinatra is a great Ruby DSL which makes it a lot of fun to build cool web applications. But this is possible, because Ruby is a great language for building DSL&#8217;s and Rack makes it easy to build web frameworks. I suggest that mastering Ruby and learning more about Rack are the next steps after getting comfortable with Sinatra.
  </p>
  
  <p>
    <span style="color:#CC3333;"><em>Thank you Carlos. In case you have any queries and/or questions, kindly post your questions here (as comments to this blog post) and Carlos would be glad to answer.</em></span>
  </p>
  
  <p>
    <b>Others in this series:</b>
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/blog/2015/01/07/corey-donohoe-how-do-i-learn-and-master-sinatra/">Corey Donohoe</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2009/07/08/jeremy-evans-how-do-i-learn-and-master-sinatra/">Jeremy Evans</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2009/07/10/graham-ashton-how-do-i-learn-and-master-sinatra/">Graham Ashton</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2015/01/07/karel-minarik-how-do-i-learn-and-master-sinatra-reprint/">Karel Minarik</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2009/07/15/chris-strom-how-do-i-learn-and-master-sinatra/">Chris Strom</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2009/07/17/nick-plante-how-do-i-learn-and-master-sinatra/">Nick Plante</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2009/07/20/julio-javier-cicchelli-how-do-i-learn-and-master-sinatra/">Julio Javier Cicchelli</a>
    </li>
  </ul>
  
  <p class="alert">
    <strong><em>Post supported by 1st Easy Limited</em>:</strong> UK based 1st Easy Limited offer Sinatra and Rails hosting running on a Phusion Passenger (mod_rails) and LAMP stack. If you want to try your hand at developing with Sinatra, why not let them arrange a <a href="http://www.1steasy.com/ruby-on-rails.htm#try">trial hosting account</a> for you? You&#8217;ll get to deploy your app, with full technical support from their team!
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Carlos+Gabaldon" rel="tag">Carlos Gabaldon</a>, <a href="http://technorati.com/tag/Sinatra" rel="tag">Sinatra</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>, <a href="http://technorati.com/tag/Learning+Sinatra" rel="tag">Learning Sinatra</a>
