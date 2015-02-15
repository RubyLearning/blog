---
title: 'Chris Strom: How do I learn and master Sinatra?'
author: Satish Talim
date: 2009-07-15
layout: post
permalink: /2009/07/15/chris-strom-how-do-i-learn-and-master-sinatra/
thesis_description:
  - In the fifth part of the mini series "How do I learn and master Sinatra?", Chris Strom gives us his insights on mastering Sinatra.
thesis_keywords:
  - Chris Strom,Sinatra,Ruby programming,Learning Sinatra
topsy_short_url:
  - http://bit.ly/1HL6qI9
categories:
  - Beginners
  - Interview
  - Learn Sinatra
  - Ruby
  - Sinatra
tags:
  - Chris Strom
  - Learning Sinatra
  - ruby programming
  - Sinatra
---
<div>
  <p class="update">
    Welcome to the <b>fifth</b> installment on the <abbr title="RubyLearning">RL</abbr> blog, of a mini series &#8211; &#8220;<strong>How do I learn and master Sinatra?</strong>&#8221; &#8211; by top Rubyists using <em>Sinatra</em>. The interview series will provide insight and commentary from these notable <em>Sinatra</em> developers, with the goal of facilitating and providing answers to the questions Ruby beginners face on <em>how to learn and master Sinatra</em>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Chris Strom, could you tell us something about yourself &#8211; your background, where you are based?</span>
  </p>
  
  <p class="block">
    <img class="alignright" title="Chris Strom" src="http://rubylearning.com/images/chris_strom.jpg" alt="Chris Strom" /><strong>Chris Strom>></strong> My name is Chris Strom. In my day job, I am the Director of Software Engineering for mdlogix, a small company in Baltimore, Maryland. We develop software that manages clinical research trials and associated data. We primarily code with Ruby on Rails.
  </p>
  
  <p>
    My background is in web development, mostly in Perl until ~2005 when I made the switch to Ruby.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Are there any pre-requisites for a person to start learning Sinatra?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> There are no prerequisites to getting started with Sinatra. A basic understanding of Ruby and HTTP will serve you well, especially as applications become more complicated.
  </p>
  
  <p>
    <span style="background-color: #FFFFCC;">Sinatra is pretty unique in my experience in that it can handle extremely basic web applications, but is more than capable of handling a decent amount of complexity. It is good for the beginner, but capable enough for the pro. It is good for prototyping simple applications, but can support complexity as well</span>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How should one start learning Sinatra?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> Learn Sinatra by playing!
  </p>
  
  <p>
    Imagine small apps (data aggregation, simple API proxies, silly games) and then implement them. Sinatra makes it easy. Go on&#8230; do it!
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
    <strong>Chris>></strong> Beginners should pay attention to the HTTP verbs at the start of action blocks (i.e. the &#8220;get&#8221; in &#8220;get &#8216;/foo&#8217; do &#8230;&#8221;). Simple applications will be all GETs, but as you become more proficient you will need to use POST and others.
  </p>
  
  <p>
    Don&#8217;t overlook helpers and templating. Neither are required but their effective use can significantly cut down on the amount of code in your Sinatra actions. This will make the application easier to read and easier to maintain.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is the official documentation on Sinatra good enough for a beginner? Are there areas which need improvement or need to be re-written</span>
  </p>
  
  <p>
    <strong>Chris>></strong> The official documentation is excellent.
  </p>
  
  <p>
    Any time I find myself wondering, &#8220;how would you go about accomplishing that in Sinatra?&#8221;, the documentation has a nice, concise answer, with links to further reading as necessary.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Sequel, DataMapper, ActiveRecord &#8211; which one would you recommend to use with Sinatra and why?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> I do not believe that I have ever used a full blown ORM with Sinatra. If I find myself thinking in ORM terms, I generally use Rails. If I am using a data store at all, it is usually one or two tables, which sqlite handles nicely. For more complex data structures, I use CouchDB, for which CouchRest works quite well.
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/sinatralogo.jpg" alt="Sinatra Icon" title="Sinatra micro-framework" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is an understanding of Rack important while learning Sinatra? Why? Which area of Rack should one be really comfortable with?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> No. Sinatra does an exceptional job of hiding Rack from the developer. It is there as your skill and need evolves, but developers can accomplish 95% of what they need to do without any understanding of Rack.
  </p>
  
  <p>
    The only area of Rack with which you need to be really comfortable is<br /> the one that you need in order to get you current work done.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How should one hone one&#8217;s skills in Sinatra?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> Developing applications. Sinatra makes it easy! Look for small things that can be collected / reported on.
  </p>
  
  <p>
    Blog about it. It is amazing how many things you think that you understand that blogging about it will tell you that you don&#8217;t.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> What type of projects should a beginner work on to gain more expertise in Sinatra?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> Beginners should work with projects with as few requirements as possible. The closer to pure Sinatra you can get, the better. Once you have your bearings, then you can introduce things like templating or ORM layers.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Could you suggest some web services that a Sinatra beginner could develop himself / herself?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> I would recommend starting with non-DB applications. Building something on top of an existing service with well established APIs, such as Twitter / Flickr would be a nice place to start.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Anything else you would like to add?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> Do not underestimate the importance of testing. The temptation with something as seemingly simple as Sinatra is to forgo testing and just dive straight into the code. This might be OK on very simple applications, but anything of moderate complexity requires testing to prevent silly mistakes from compounding into huge ones.
  </p>
  
  <p>
    Sinatra makes testing easy. Sinatra wants you to test. Don&#8217;t disappoint Sinatra.
  </p>
  
  <p>
    As always, if you write your tests before your code, your code will be be cleaner, more robust and easier to maintain.
  </p>
  
  <p>
    My last bit of advice is to not program by coincidence. <span style="background-color: #FFFFCC;">Sinatra is very powerful &#8212; so much so that, at times, you will find that things just seem to work. Always take some time to understand why things work like they do in Sinatra &#8212; Sinatra rewards curiosity</span>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><em>Thank you Chris. In case you have any queries and/or questions, kindly post your questions here (as comments to this blog post) and Chris would be glad to answer.</em></span>
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
  </ul>
  
  <p class="alert">
    <strong><em>Post supported by 1st Easy Limited</em>:</strong> UK based 1st Easy Limited offer Sinatra and Rails hosting running on a Phusion Passenger (mod_rails) and LAMP stack. If you want to try your hand at developing with Sinatra, why not let them arrange a <a href="http://www.1steasy.com/ruby-on-rails.htm#try">trial hosting account</a> for you? You&#8217;ll get to deploy your app, with full technical support from their team!
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Chris+Strom" rel="tag">Chris Strom</a>, <a href="http://technorati.com/tag/Sinatra" rel="tag">Sinatra</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>, <a href="http://technorati.com/tag/Learning+Sinatra" rel="tag">Learning Sinatra</a>
