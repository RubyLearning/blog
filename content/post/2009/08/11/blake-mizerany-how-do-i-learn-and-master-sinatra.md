---
draft: false
title: 'Blake Mizerany: How do I learn and master Sinatra?'
date: 2009-08-11
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/rubylearning
categories:
- Beginners
- Interview
- Learn Sinatra
- Ruby
- Sinatra
layout: post
permalink: /2009/08/11/blake-mizerany-how-do-i-learn-and-master-sinatra/
tags:
- Blake Mizerany
- Learning Sinatra
- ruby programming
- Sinatra
topsy_short_url:
- http://bit.ly/1HL7HPp
---

<div>
  <p class="update">
    Welcome to the <b>last</b> installment on the <abbr title="RubyLearning">RL</abbr> blog, of a mini series &#8211; &#8220;<strong>How do I learn and master Sinatra?</strong>&#8221; &#8211; by top Rubyists using <em>Sinatra</em>. The interview series will provide insight and commentary from these notable <em>Sinatra</em> developers, with the goal of facilitating and providing answers to the questions Ruby beginners face on <em>how to learn and master Sinatra</em>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Blake Mizerany, could you tell us something about yourself &#8211; your background, where you are based?</span>
  </p>
  
  <p class="block">
    <img class="alignright" title="Blake Mizerany" src="http://www.rubylearning.com/images/blake_mizerany.jpg" alt="Blake Mizerany" /><strong>Blake Mizerany>></strong> I&#8217;m one of the many Mad-Scientiests at Heroku. I started the Sinatra project in September of &#8217;07. I create useless, and sometimes useful, things out of Ruby, Erlang, and sometimes C.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Are there any pre-requisites for a person to start learning Sinatra?</span>
  </p>
  
  <p>
    <strong>Blake>></strong> Be prepared to throw out what the big frameworks taught you and be prepared to learn what they hide from you. It&#8217;s not difficult.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Would you suggest that a beginner learns Sinatra before learning Ruby on Rails? Why?</span>
  </p>
  
  <p>
    <strong>Blake>></strong> <span style="background-color: #FFFFCC;">Absolutely. When you learn a large framework first, you&#8217;re introduced to an abundance of ideas, constraints, and magic. Worst of all, they start you with a pattern. In the case of Rails, that&#8217;s MVC. MVC doesn&#8217;t fit most web-applications from the start or at all. You&#8217;re doing yourself a disservice starting with it. Back into patterns, never start with them</span>. Don&#8217;t think you&#8217;ll win that big bet on the golf course just because you bought that $10,000 set of golf clubs. <img src="http://rubylearning.com/blog/wp-includes/images/smilies/icon_wink.gif" alt=";)" class="wp-smiley" />
  </p>
  
  <blockquote class="right">
    <p>
      Sinatra &#8211; quickly create tiny web apps and services
    </p>
  </blockquote>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Any features of Sinatra that you consider awesome?</span>
  </p>
  
  <p>
    <strong>Blake>></strong> Sinatra features that I consider awesome are:
  </p>
  
  <ol>
    <li>
      <b>The community</b>. I&#8217;ve met so many bright people on the mailing list and in IRC. Including those I work with at Heroku today. These people are fantastic and always willing to help. Drop in anytime.
    </li>
    <li>
      <b>halt and pass</b>. See the README. <img src="http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" />
    </li>
    <li>
      <b>Sinatra::Base</b>
    </li>
  </ol>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How should one start learning Sinatra?</span>
  </p>
  
  <p>
    <strong>Blake>></strong> Read the README. It has *everything* you need to start. Use Heroku to deploy.
  </p>
  
  <p>
    Then learn Rack. Understand how Rack works. Write basic apps in Rack. Write a simple peice of middleware.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Which area of Sinatra should a beginner pay particular attention to?</span>
  </p>
  
  <p>
    <strong>Blake>></strong> It&#8217;s not a MVC framework that starts you with CRUD. You can separate your concerns how you like. Don&#8217;t start using it they way you would use a MVC framework. You *can* use it like a MVC framework; but it will make you a better person to keep things simpler until you need those abstractions.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is the official documentation on Sinatra good enough for a beginner? Are there areas which need improvement or need to be re-written</span>
  </p>
  
  <p>
    <strong>Blake>></strong> Yes. The README is a fantastic place to start.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Sequel, DataMapper, ActiveRecord &#8211; which one would you recommend to use with Sinatra and why?</span>
  </p>
  
  <p>
    <strong>Blake>></strong> Any. When I do use a SQL database, which is rare these days, I use Sequel because it&#8217;s light on memory and dependencies (see <a href="http://github.com/rtomayko/sinatra-sequel/tree/master">http://github.com/rtomayko/sinatra-sequel/tree/master</a>). It just always works. I&#8217;ll use ActiveRecord (AR) when I have something CRUD&#8217;y that I know is CRUD&#8217;y; AR is awesome at that.
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/sinatralogo.jpg" alt="Sinatra Icon" title="Sinatra micro-framework" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is an understanding of Rack important while learning Sinatra? Why? Which area of Rack should one be really comfortable with?</span>
  </p>
  
  <p>
    <strong>Blake>></strong> You don&#8217;t need to know Rack to learn Sinatra. It would behoove you to understand it to ensure you get the most out of Sinatra. Rack is the foundation of Sinatra.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How should one hone one&#8217;s skills in Sinatra?</span>
  </p>
  
  <p>
    <strong>Blake>></strong> Read the source. It&#8217;s less than 1,200 LOC. Thanks to the all the great contributions, it&#8217;s a fantastic example of how to get a ton of features out of Ruby with little, clean, pretty Ruby code.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> What type of projects should a beginner work on to gain more expertise in Sinatra?</span>
  </p>
  
  <p>
    <strong>Blake>></strong> Build a JSON web service. Build a small blog. Build a url shortner. Any of those will get your feet wet. You&#8217;ll see how Sinatra gets you going quickly and how it can grow to great heights to fit most of your needs as a framework.
  </p>
  
  <p>
    <span style="color:#CC3333;"><em>Thank you Blake. In case you have any queries and/or questions, kindly post your questions here (as comments to this blog post) and Blake would be glad to answer.</em></span>
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
    <li>
      <a href="http://rubylearning.com/blog/2009/07/21/carlos-gabaldon-how-do-i-learn-and-master-sinatra/">Carlos Gabaldon</a>
    </li>
  </ul>
</div>

