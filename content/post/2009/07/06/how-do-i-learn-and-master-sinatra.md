---
author: Satish Talim
categories:
- Beginners
- Interview
- Learn Sinatra
- Ruby
- Sinatra
date: 2009-07-06
layout: post
permalink: /2009/07/06/how-do-i-learn-and-master-sinatra/
tags:
- Corey Donohoe
- Learning Sinatra
- ruby programming
- Sinatra
thesis_description:
- In the first part of a mini series "How do I learn and master Sinatra", Corey Donohoe
  gives us his insights on mastering Sinatra.
thesis_keywords:
- Corey Donohoe,Sinatra,Ruby programming,Learning Sinatra
title: How do I learn and master Sinatra?
---

<div>
  <p class="update">
    Welcome to the <b>first</b> installment on the <abbr title="RubyLearning">RL</abbr> blog, of a mini series &#8211; &#8220;<strong>How do I learn and master Sinatra?</strong>&#8221; &#8211; by top Rubyists using <em>Sinatra</em>. The interview series will provide insight and commentary from these notable <em>Sinatra</em> developers, with the goal of facilitating and providing answers to the questions Ruby beginners face on <em>how to learn and master Sinatra</em>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Corey Donohoe, could you tell us something about yourself &#8211; your background, where you are based?</span>
  </p>
  
  <p class="block">
    <img class="alignright" title="Corey Donohoe" src="http://rubylearning.com/images/CoreyDonohoe.jpg" alt="Corey Donohoe" /><strong>Corey Donohoe>></strong> I&#8217;m <a href="http://atmos.org/">Corey Donohoe</a>. I&#8217;m based out of Boulder, Colorado &#8211; USA. My background is in computer science and system administration though I prefer hacking to either of those labels. I&#8217;m a pretty normal dude, I enjoy cycling, music, coffee, micro brews, and all the other awesomeness that my home state has to offer. I&#8217;ve been working for <a href="http://www.engineyard.com/">Engine Yard</a> since March of &#8217;07 doing everything from app support to internal development. I&#8217;m currently 1/2 of our internal integrations team.
  </p>
  
  <blockquote class="right">
    <p>
      Sinatra&#8217;s greatest strength is its flexibility
    </p>
  </blockquote>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Are there any pre-requisites for a person to start learning Sinatra</span>
  </p>
  
  <p>
    <strong>Corey>></strong> There aren&#8217;t any hardcore prerequisites per se; Ruby and experience in a Ruby web framework is a plus. HTTP verbs play a huge role in Sinatra, as well as things like query and post params. If you get those concepts you can hit the ground running.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How should one start learning Sinatra?</span>
  </p>
  
  <p>
    <strong>Corey>></strong> Learn Sinatra incrementally. If you have new business requirements try to think about things like &#8220;how would i implement this in Sinatra?&#8221; Take the time to figure that requirement out in Sinatra then throw the solution out! When the time comes to use Sinatra for something you&#8217;ll have a much more broad understanding of the framework and you&#8217;ll hit fewer blockers.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Which area of Sinatra should a beginner pay particular attention to?</span>
  </p>
  
  <p>
    <strong>Corey>></strong> Understanding the difference between <b>Sinatra::Base</b> and <b>Sinatra::Default</b> is definitely something a Sinatra beginner should focus on early. <b>Sinatra::Base</b> is for writing Rack middleware, and <b>Sinatra::Default</b> is normally for writing Rack applications. Learning the modular style app development is really useful as well as using the register method to include pieces of functionality. Getting a handle on those concepts will expose you to the rest of Sinatra, which is relatively intuitive.
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/sinatralogo.jpg" alt="Sinatra Icon" title="Sinatra micro-framework" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is the official documentation on Sinatra good enough for a beginner? Are there areas which need improvement or need to be re-written</span>
  </p>
  
  <p>
    <strong>Corey>></strong> The Sinatra documentation is well done and I can generally find answers to my questions just by referencing the docs. There&#8217;s always #sinatra on freenode or the Sinatra book on github if you need additional help too. There&#8217;s plenty of pretty well tested examples on github using Sinatra, hancock and integrity come to mind.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Sequel, DataMapper, ActiveRecord &#8211; which one would you recommend to use with Sinatra and why?</span>
  </p>
  
  <p>
    <strong>Corey>></strong> I use DataMapper exclusively. It was a bumpy ride a year ago but these days it&#8217;s acceptable for production use. We interface with more than just relational databases and the ability to keep a consistent model syntax across various data sources is really attractive to us. Realistically I feel like I spend less time fighting my framework when I&#8217;m using DataMapper so it&#8217;s the clear choice. The one place I wouldn&#8217;t use dm in would be a join heavy relational environment; ActiveRecord is way better at that.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is an understanding of Rack important while learning Sinatra? Why? Which area of Rack should one be really comfortable with?</span>
  </p>
  
  <p>
    <strong>Corey>></strong> You don&#8217;t need a solid understanding of Rack to get a Sinatra up and running, but you&#8217;ll be missing out on a lot of the power. It&#8217;s extremely beneficial to take the time to learn how the <b>Rack::Builder</b> works as well as the usage of the <b>use/map/run</b> commands in that context. The modularity of Rack really becomes apparent and you&#8217;ll find yourself using Sinatra more effectively.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How should one hone one&#8217;s skills in Sinatra?</span>
  </p>
  
  <p>
    <strong>Corey>></strong> Read code, write test code, write code. All of the awesome testing frameworks available for Ruby are available to Sinatra. If you don&#8217;t write tests it might be a good way to familiarize yourself with testing best practices without the overheard of a larger framework.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> What type of projects should a beginner work on to gain more expertise in Sinatra?</span>
  </p>
  
  <p>
    <strong>Corey>></strong> <span style="background-color: #FFFFCC;">A beginner would benefit from writing something completely API driven as a first project</span>. So many people couple databases with dynamic web applications but it&#8217;s kind of liberating to just be an intermediary service. Twitter apps are pretty trivial to implement and can teach you a lot. They also expose you to a pretty large userbase to solicit feedback.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Could you suggest some web services that a Sinatra beginner could develop himself / herself?</span>
  </p>
  
  <p>
    <strong>Corey>></strong> <span style="background-color: #FFFFCC;">Web services are great targets for introducing Sinatra into your workplace</span>. Identify a pain point in your organization and put a small app in front of it. It doesn&#8217;t have to replace something overnight but it&#8217;s a great way to sneak functionality in at work. Once you have a few of these built you start to reap the benefits of microapps and web services.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Anything else you would like to add?</span>
  </p>
  
  <p>
    <strong>Corey>></strong> <span style="background-color: #FFFFCC;">Learning Sinatra is the best thing you can do while we all wait for Rails 3 to land</span>. The middleware you write will be able to be dropped right into your Rails 3 applications so it&#8217;s not like you&#8217;re wasting time. We&#8217;re starting to build really modular systems using Sinatra by building APIs into those systems. I think a lot of people would benefit from breaking their monolith apps down into microapps and Sinatra is a great way to do it.
  </p>
  
  <p>
    People looking for a template might want to investigate the singem gem. It has basic templates for twitter apps or regular webservices. All of them are bootstrapped for testing with cucumber+rspec.
  </p>
  
  <p>
    <span style="color:#CC3333;"><em>Thank you Corey. In case you have any queries and/or questions, kindly post your questions here (as comments to this blog post) and Corey would be glad to answer.</em></span>
  </p>
  
  <p class="alert">
    <strong><em>Post supported by 1st Easy Limited</em>:</strong> UK based 1st Easy Limited offer Sinatra and Rails hosting running on a Phusion Passenger (mod_rails) and LAMP stack. If you want to try your hand at developing with Sinatra, why not let them arrange a <a href="http://www.1steasy.com/ruby-on-rails.htm#try">trial hosting account</a> for you? You&#8217;ll get to deploy your app, with full technical support from their team!
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Corey+Donohoe" rel="tag">Corey Donohoe</a>, <a href="http://technorati.com/tag/Sinatra" rel="tag">Sinatra</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>, <a href="http://technorati.com/tag/Learning+Sinatra" rel="tag">Learning Sinatra</a>
