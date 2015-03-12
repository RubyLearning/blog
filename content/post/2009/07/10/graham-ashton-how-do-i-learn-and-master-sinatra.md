---
author: Satish Talim
categories:
- Beginners
- Learn Sinatra
- Ruby
- Sinatra
date: 2009-07-10
layout: post
permalink: /2009/07/10/graham-ashton-how-do-i-learn-and-master-sinatra/
tags:
- Graham Ashton
- Learning Sinatra
- ruby programming
- Sinatra
thesis_description:
- In the third part of the mini series "How do I learn and master Sinatra?", Graham
  Ashton gives us his insights on mastering Sinatra.
thesis_keywords:
- Graham Ashton,Sinatra,Ruby programming,Learning Sinatra
title: 'Graham Ashton: How do I learn and master Sinatra?'
topsy_short_url:
- http://bit.ly/1xQQ6V0
---

<div>
  <p class="update">
    Welcome to the <b>third</b> installment on the <abbr title="RubyLearning">RL</abbr> blog, of a mini series &#8211; &#8220;<strong>How do I learn and master Sinatra?</strong>&#8221; &#8211; by top Rubyists using <em>Sinatra</em>. The interview series will provide insight and commentary from these notable <em>Sinatra</em> developers, with the goal of facilitating and providing answers to the questions Ruby beginners face on <em>how to learn and master Sinatra</em>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Graham Ashton, could you tell us something about yourself &#8211; your background, where you are based?</span>
  </p>
  
  <p class="block">
    <img class="alignright" title="Graham Ashton" src="http://www.rubylearning.com/images/graham-ashton.jpeg" alt="Graham Ashton" /><strong>Graham Ashton>></strong> I&#8217;m <a href="http://grahamashton.net/">Graham Ashton</a>. When I first got involved in web development I taught myself Perl. It served me well for five years, but I felt there had to be a better way. I picked up Python and loved it, and set about finding a full time Python job. Another five years later I found my way to Ruby, Rails and eventually Sinatra. I&#8217;m now working in London developing web applications as a freelancer. I&#8217;m mainly using Ruby at the moment, but I&#8217;m still keeping my eye in with Python.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Are there any pre-requisites for a person to start learning Sinatra?</span>
  </p>
  
  <p>
    <strong>Graham>></strong> I think it&#8217;s well worth having a basic grasp of the programming language before you pick up a framework. The first time I tried Rails I didn&#8217;t know any Ruby and couldn&#8217;t tell the Rails magic apart from the Ruby magic. I found it much easier to learn Rails after spending a day or two getting familiar with the Ruby syntax. Sinatra doesn&#8217;t really do magic (which is great, and appeals to the Python fan within me), but I still think it&#8217;s well worth having a good grasp of Ruby.
  </p>
  
  <p>
    Otherwise, the only thing I&#8217;d recommend is a good understanding of the basics of HTTP (GET, POST, etc.). Sinatra feels like a pretty thin layer on top of HTTP.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How should one start learning Sinatra?</span>
  </p>
  
  <p>
    <strong>Graham>></strong> It may be a cliche, but I&#8217;d start with the <a href="http://www.sinatrarb.com/intro.html">README</a>. It&#8217;s a fairly succinct summary of what you can do with Sinatra, and will bring you up to speed on what&#8217;s possible. You can refer back to the README or the <a href="http://www.sinatrarb.com/book.html">Sinatra book</a> for more details later. I hear the book is still a work in progress, but I found it very useful when I was starting out.
  </p>
  
  <p>
    Once you&#8217;ve skim read some docs just get stuck in and start trying to make stuff. Don&#8217;t skimp on the <a href="http://www.sinatrarb.com/testing.html">testing</a>; it&#8217;s pretty easy to do and is just as important to learn as the main Sinatra API.
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
    <strong>Graham>></strong> That&#8217;s a tricky question. Sinatra is so simple that no part stands out as being worthy of attention. Just make sure you write tests and you&#8217;ll be fine.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is the official documentation on Sinatra good enough for a beginner? Are there areas which need improvement or need to be re-written</span>
  </p>
  
  <p>
    <strong>Graham>></strong> I think it&#8217;s good enough, yes. That&#8217;s how I learnt Sinatra and I managed to write a complete app without resorting to digging into the code. I hear that the book will be getting some work done on it in future, but I&#8217;m not really up to speed on it&#8217;s deficencies.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Sequel, DataMapper, ActiveRecord &#8211; which one would you recommend to use with Sinatra and why?</span>
  </p>
  
  <p>
    <strong>Graham>></strong> I&#8217;d say you should use whichever is most suitable to your task, that you&#8217;re familiar with, or interested in learning. Sinatra doesn&#8217;t have a preference.
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/sinatralogo.jpg" alt="Sinatra Icon" title="Sinatra micro-framework" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is an understanding of Rack important while learning Sinatra? Why? Which area of Rack should one be really comfortable with?</span>
  </p>
  
  <p>
    <strong>Graham>></strong> Understanding Rack certainly isn&#8217;t a pre-requisite. To deploy a Sinatra application you typically need to write yourself a Rack config file, but there are plenty of examples online that you could download if you wanted to.
  </p>
  
  <p>
    Having said all that, Rack is pretty simple, very cool, and well worth reading up on. Check out how to chain various Rack components together using the <b>Rack::Builder</b> DSL (there&#8217;s an example in the RDoc).
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How should one hone one&#8217;s skills in Sinatra?</span>
  </p>
  
  <p>
    <strong>Graham>></strong> Make stuff. Deploy it. Repeat.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> What type of projects should a beginner work on to gain more expertise in Sinatra?</span>
  </p>
  
  <p>
    <strong>Graham>></strong> When I&#8217;m learning a new technology I find that I progress faster if I&#8217;m really motivated to release whatever it is I&#8217;m working on. <span style="background-color: #FFFFCC;">So make stuff that interests you or excites you</span>. Development is a creative process, and should be fun.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Could you suggest some web services that a Sinatra beginner could develop himself / herself?</span>
  </p>
  
  <p>
    <strong>Graham>></strong> If you&#8217;ve got an existing site that you&#8217;ve already implemented with another technology, consider porting it to Sinatra (it&#8217;s a great way to compare and contrast different approaches). <span style="background-color: #FFFFCC;">Have you got a personal web page or blog? They&#8217;re easy to make in Sinatra, and once you&#8217;ve got total control of your site using something as simple as Sinatra you really can do anything you like with it</span>.
  </p>
  
  <p>
    That&#8217;s exactly what I did when I built <a href="http://effectif.com/nesta">Nesta</a> (I had previously been running Mephisto). You could just use Nesta but you&#8217;ll learn more if you write your own site from scratch. There are plenty of alternatives to Nesta out there, such as <a href="http://github.com/karmi/marley/tree/master">Marley</a> (which inspired me to make Nesta) or the code for <a href="http://github.com/toolmantim/toolmantim/tree/master">toolmantim.com</a>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Anything else you would like to add?</span>
  </p>
  
  <p>
    <strong>Graham>></strong> <span style="background-color: #FFFFCC;">Take half an hour out to learn HAML and SASS. The syntax is so simple, it&#8217;ll be well worth the investment</span>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><em>Thank you Graham. In case you have any queries and/or questions, kindly post your questions here (as comments to this blog post) and Graham would be glad to answer.</em></span>
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
  </ul>
  
  <p class="alert">
    <strong><em>Post supported by 1st Easy Limited</em>:</strong> UK based 1st Easy Limited offer Sinatra and Rails hosting running on a Phusion Passenger (mod_rails) and LAMP stack. If you want to try your hand at developing with Sinatra, why not let them arrange a <a href="http://www.1steasy.com/ruby-on-rails.htm#try">trial hosting account</a> for you? You&#8217;ll get to deploy your app, with full technical support from their team!
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Graham+Ashton" rel="tag">Graham Ashton</a>, <a href="http://technorati.com/tag/Sinatra" rel="tag">Sinatra</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>, <a href="http://technorati.com/tag/Learning+Sinatra" rel="tag">Learning Sinatra</a>
