---
author: Satish Talim
categories:
- Beginners
- Interview
- Learn Sinatra
- Ruby
- Sinatra
date: 2009-07-17
layout: post
permalink: /2009/07/17/nick-plante-how-do-i-learn-and-master-sinatra/
tags:
- Learning Sinatra
- Nick Plante
- ruby programming
- Sinatra
thesis_description:
- In the sixth part of the mini series "How do I learn and master Sinatra?", Nick
  Plante gives us his insights on mastering Sinatra.
thesis_keywords:
- Nick Plante,Sinatra,Ruby programming,Learning Sinatra
title: 'Nick Plante: How do I learn and master Sinatra?'
topsy_short_url:
- http://bit.ly/1xQQD9G
---

<div>
  <p class="update">
    Welcome to the <b>sixth</b> installment on the <abbr title="RubyLearning">RL</abbr> blog, of a mini series &#8211; &#8220;<strong>How do I learn and master Sinatra?</strong>&#8221; &#8211; by top Rubyists using <em>Sinatra</em>. The interview series will provide insight and commentary from these notable <em>Sinatra</em> developers, with the goal of facilitating and providing answers to the questions Ruby beginners face on <em>how to learn and master Sinatra</em>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Nick Plante, could you tell us something about yourself &#8211; your background, where you are based?</span>
  </p>
  
  <p class="block">
    <img class="alignright" title="Nick Plante" src="http://www.rubylearning.com/images/nap.jpg" alt="Nick Plante" /><strong>Nick Plante>></strong> I&#8217;m Nick Plante, a freelance web app developer living in Portsmouth, NH &#8212; USA. I&#8217;ve been doing application development professionally for quite some time, but I don&#8217;t think I really ever enjoyed it all that much until I found Ruby, which was about 3 years ago now. I do client work for startups and small businesses and we work on incubating our own projects too. I&#8217;m also involved in a bunch of community stuff such as working as an organizer for the Rails Rumble event. In my spare time, I enjoy film, comics, travel, loud droning music, racquetball and mountain biking.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Are there any pre-requisites for a person to start learning Sinatra?</span>
  </p>
  
  <p>
    <strong>Nick>></strong> A basic understanding of HTTP verbs would be useful. It would certainly help to have a firm grasp on Ruby too. But honestly, it&#8217;s not really that important. Writing a Sinatra application is a good way to learn Ruby itself, if you&#8217;re focused on web-based projects. It&#8217;s not large enough to be overly complex or unwieldy, and is easily understood. For example, <span style="background-color: #FFFFCC;">I&#8217;d recommend that a person learn Sinatra before attempting to use Rails for a project</span>, and for a lot of people, Rails is their first experience with Ruby.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How should one start learning Sinatra?</span>
  </p>
  
  <p>
    <strong>Nick>></strong> Start by looking at the Sinatra official site; the README there is well written and very brief, and will teach you most of what you need to know. Sinatra isn&#8217;t a huge framework with all sorts of esoteric methods, so it&#8217;s easy to get started. I&#8217;d next suggest that you check out the list of Sinatra applications &#8220;in the wild&#8221;; many of these are open source (including several of my own projects).
  </p>
  
  <p>
    I&#8217;m a firm believer that the best way to learn a framework is to find practical small-scope examples to look at, and there are plenty of these for Sinatra now &#8212; just check GitHub. Once you understand the basics, pick something you&#8217;re interested in that&#8217;s relatively minimalist and start coding. The docs and the community are there to help you when and if you need help.
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
    <strong>Nick>></strong> Start with the basics; Sinatra&#8217;s RESTful syntax is a joy to work with. Stay practical. Once you&#8217;ve got that down, spend some time playing around with Rack itself. Understand how it works and how you can write and use middleware.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is the official documentation on Sinatra good enough for a beginner? Are there areas which need improvement or need to be re-written</span>
  </p>
  
  <p>
    <strong>Nick>></strong> I think it&#8217;s fine. The micro-site / README is a great read and the Sinatra book is another option. <span style="background-color: #FFFFCC;">Since Sinatra is relatively unopinionated about your choice of ORM, templating language, testing framework, javascript library, etc &#8212; you&#8217;ll get to make your own choices about what you use. The documentation there will probably be worse than Sinatra&#8217;s own</span> ;-).
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Sequel, DataMapper, ActiveRecord &#8211; which one would you recommend to use with Sinatra and why?</span>
  </p>
  
  <p>
    <strong>Nick>></strong> Whichever one you personally like the best, or are most familiar with. I&#8217;m a big fan of DataMapper for several reasons, although it&#8217;s documentation (see previous question) admittedly leaves a bit to be desired. If you&#8217;ve already got a background with Rails, ActiveRecord might be a better place to start. Use what you know and learn one new thing at a time. Once you&#8217;re comfortable with Sinatra try experimenting with something different to see how it works for you.
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/sinatralogo.jpg" alt="Sinatra Icon" title="Sinatra micro-framework" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is an understanding of Rack important while learning Sinatra? Why? Which area of Rack should one be really comfortable with?</span>
  </p>
  
  <p>
    <strong>Nick>></strong> I don&#8217;t think you really need to know much of anything about Rack to start using Sinatra, other than how to write a rackup file (which is easy and well documented; you can pretty much copy and paste). However, if you do know Rack you&#8217;ve got a lot of advantages, and I&#8217;d recommend learning it. There&#8217;s some really powerful middleware out there like Rack::Cache that can save you from reinventing the wheel when you need the extras that aren&#8217;t already baked-in.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How should one hone one&#8217;s skills in Sinatra?</span>
  </p>
  
  <p>
    <strong>Nick>></strong> Practice makes perfect. Pick an idea you&#8217;re interested in and build it. You can also learn a lot by looking at other peoples&#8217; work.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> What type of projects should a beginner work on to gain more expertise in Sinatra?</span>
  </p>
  
  <p>
    <strong>Nick>></strong> Small ones that do one simple task and do it well. Focus on writing tight elegant code that leverages Sinatra&#8217;s RESTful DSL. Don&#8217;t forget to use Rack::Test to write tests for your application.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Could you suggest some web services that a Sinatra beginner could develop himself / herself?</span>
  </p>
  
  <p>
    <strong>Nick>></strong> Write a minimalist time tracker or a pastebin service or something else similarly small in scope. Sinatra is great for creating micro-apps; maybe spend some time thinking about how you could leverage the Twitter API. Also, consider building services that are entirely web APIs and don&#8217;t need a traditional HTML frontend. Sinatra really excels for that sort of thing.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Anything else you would like to add?</span>
  </p>
  
  <p>
    <strong>Nick>></strong> Whatever you do, just remember to have fun doing it. We&#8217;re all better developers when we&#8217;re working with technologies and tools that we enjoy, and creating things that we&#8217;re personally passionate about. For me, working on Sinatra-based apps is a lot of fun. It&#8217;s not the right choice for everything, and I definitely favor Rails for certain types of applications, but for creating small clean micro-apps it&#8217;s hard to beat imo.
  </p>
  
  <p>
    <span style="color:#CC3333;"><em>Thank you Nick. In case you have any queries and/or questions, kindly post your questions here (as comments to this blog post) and Nick would be glad to answer.</em></span>
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
  </ul>
  
  <p class="alert">
    <strong><em>Post supported by 1st Easy Limited</em>:</strong> UK based 1st Easy Limited offer Sinatra and Rails hosting running on a Phusion Passenger (mod_rails) and LAMP stack. If you want to try your hand at developing with Sinatra, why not let them arrange a <a href="http://www.1steasy.com/ruby-on-rails.htm#try">trial hosting account</a> for you? You&#8217;ll get to deploy your app, with full technical support from their team!
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Nick+Plante" rel="tag">Nick Plante</a>, <a href="http://technorati.com/tag/Sinatra" rel="tag">Sinatra</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>, <a href="http://technorati.com/tag/Learning+Sinatra" rel="tag">Learning Sinatra</a>
