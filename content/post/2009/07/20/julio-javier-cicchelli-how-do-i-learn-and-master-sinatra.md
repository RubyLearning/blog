---
author: Satish Talim
categories:
- Beginners
- Interview
- Learn Sinatra
- Ruby
- Sinatra
date: 2009-07-20
layout: post
permalink: /2009/07/20/julio-javier-cicchelli-how-do-i-learn-and-master-sinatra/
tags:
- Julio Javier Cicchelli
- Learning Sinatra
- ruby programming
- Sinatra
thesis_description:
- In the seventh part of the mini series "How do I learn and master Sinatra?", Julio
  Javier Cicchelli gives us his insights on mastering Sinatra.
thesis_keywords:
- Julio Javier Cicchelli,Sinatra,Ruby programming,Learning Sinatra
title: 'Julio Javier Cicchelli: How do I learn and master Sinatra?'
topsy_short_url:
- http://bit.ly/1HL76NG
---

<div>
  <p class="update">
    Welcome to the <b>seventh</b> installment on the <abbr title="RubyLearning">RL</abbr> blog, of a mini series &#8211; &#8220;<strong>How do I learn and master Sinatra?</strong>&#8221; &#8211; by top Rubyists using <em>Sinatra</em>. The interview series will provide insight and commentary from these notable <em>Sinatra</em> developers, with the goal of facilitating and providing answers to the questions Ruby beginners face on <em>how to learn and master Sinatra</em>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Julio Javier Cicchelli, could you tell us something about yourself &#8211; your background, where you are based?</span>
  </p>
  
  <p class="block">
    <img class="alignright" title="Julio Javier Cicchelli" src="http://www.rubylearning.com/images/jjcicchelli.jpg" alt="Julio Javier Cicchelli" /><strong>Julio Javier Cicchelli>></strong> Hey everybody! I am Julio Javier Cicchelli and I have currently set an anchor in the (in)famous Red Light District in Amsterdam, the Netherlands. I was born in Buenos Aires and I spent the formative years of my life there. Six years ago, I decided to set sail for Europe. I first reached France. Two years ago I decided to head for the Netherlands.
  </p>
  
  <p>
    Initially I planned to become an architect as this is the profession that runs in the family. Yet I was meant for other things. One day, I discovered the incredible <a href="http://en.wikipedia.org/wiki/Commodore_64">Commodore C64K</a>. This proved to mark a watershed in my life. As a result of my academic and personal pursuits, I have become a devoted Software Engineer, who is passionate about the Software development process. I have also developed &#8220;unholy&#8221; love for Information Systems and Software. My interest in music and arts propelled me to seek for the parallels between these disciplines and Software Engineering. As a result, I consider Software to be yet another form of expression. Indeed, because of the uniqueness of each piece of software developed, I equate the process of software creation to a modern form of craftsmanship. This unorthodox attitude towards the way of truly experiencing the Software Development lies at the very core of my newly-founded Software company <a href="http://rock-n-code.com/">Rock & Code</a>.
  </p>
  
  <p>
    Even though my life seems to be deeply rooted in the domain of computers and source code, I also love those simple joys that make our lives worthwhile. I am always eager to meet interesting people, to discover new fascinating cultures, and to visit new places. I am also a music junkie, a wannabe musician and artist, a passionate concertgoer, a party person, an incurable dreamer, and a vocal social activist. At the end, all I want is to live my life to the fullest.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Are there any pre-requisites for a person to start learning Sinatra?</span>
  </p>
  
  <p>
    <strong>Julio>></strong> I do not think there are any pre-requisite for all those who are keen on learning Sinatra. Fortunately, the Sinatra DSL has been designed in such a way that it is almost intuitive and easy to grasp and follow, by developers of different ranks. Nevertheless, a basic knowledge of Ruby and Rack could save you lots of time. It will also save you some undesirable headaches. Yet, all those who are new to the programming language and its evil ways should be able to catch up simultaneously with both Ruby and Sinatra.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How should one start learning Sinatra?</span>
  </p>
  
  <p>
    <strong>Julio>></strong> If you are an absolute beginner, do not panic. I strongly recommend that you read the core Sinatra documentation. You must pay special attention to the <a href="http://www.sinatrarb.com/intro.html">README</a> and the <a href="http://www.sinatrarb.com/faq.html">FAQ</a>. The <a href="http://www.sinatrarb.com/book.html">book</a> is another must read. If you want to expand your knowledge of the framework even further, you can review the screencasts and the presentations available on the website. Finally you can browse through the <a href="http://www.rubyinside.com/sinatra-29-links-and-resources-for-a-quicker-easier-way-to-build-webapps-1371.html">resources</a>. Be bold and do not be afraid to try out the example code that you will encounter while reading!
  </p>
  
  <p>
    If you are a developer of some experience, I’d also recommend that you read the <a href="http://github.com/sinatra/sinatra/tree/master">source code</a>. Since this framework is basically a very well written DSL of about 2000 lines, the code should pose no problems. It is easy to read and understand. The benefits of reading it are plenty. First and foremost, studying this code would give you a more profound insight of how this framework works intimately with Rack. In the mean time, it will teach you how to write a DSL properly. In addition, you can find plenty of real-life applications and their respective source code on the <a href="http://www.sinatrarb.com/wild.html">In the Wild</a> and <a href="http://www.sinatrarb.com/extensions-wild.html">Extensions in the Wild</a> sections of the documentation page. They are also posted on <a href="https://github.com/">Github</a>. So, if you are looking for more realistic examples, this is your haven!
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
    <strong>Julio>></strong> Since Sinatra is very straight-forward, a newbie does not have to devote extra attention to any particular areas. What really matters is that a developer should grasp its concepts and be aware of the possibilities that this framework can offer. From there on, every developer can make a singular use of it. How he or she is going to do it depends on external factors such as the kind of software problem that has to be solved, his or her vision, preferences, methodologies and practices of writing Software.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is the official documentation on Sinatra good enough for a beginner? Are there areas which need improvement or need to be re-written</span>
  </p>
  
  <p>
    <strong>Julio>></strong> As I have already stated, the official documentation is the pivotal gateway that guarantees the right of passage to the Sinatra world. I believe it can fully satiate the initial hunger for knowledge of any starter. When I was a novice, I studied the documentation very carefully. This allowed me to eventually master it. In addition, I consider this documentation to be exemplary because it is simple, pithy, and full of useful examples for all the dilettantes. Certainly, there is plenty of room for improvement. There are certain parts that are either incomplete or still unwritten and probably unexplored. One of its drawbacks is that it is only available in English. This could prove to be a nuisance for all the developers who are still not comfortable with English. Hopefully, those weaknesses and insufficiencies will be addressed in the near future.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Sequel, DataMapper, ActiveRecord &#8211; which one would you recommend to use with Sinatra and why?</span>
  </p>
  
  <p>
    <strong>Julio>></strong> I highly recommend that developers use <a href="http://datamapper.org/doku.php">DataMapper</a> when they are working on projects that involve some sort of a data base (not only relational databases). This ORM has certain characteristics such as eager loading, laziness, performance, and Ruby-like syntax that I particularly favor. It is also very simple to use. Please be aware that I am somehow biased. Although I have used ActiveRecord, I have never used or explored the approach proposed by Sequel.
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/sinatralogo.jpg" alt="Sinatra Icon" title="Sinatra micro-framework" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is an understanding of Rack important while learning Sinatra? Why? Which area of Rack should one be really comfortable with?</span>
  </p>
  
  <p>
    <strong>Julio>></strong> A basic knowledge of <a href="http://rack.rubyforge.org/">Rack</a> could be extremely useful during the process of learning Sinatra because it allows you to consider the vast project possibilities this framework has to offer. Moreover, exploring the intimate relationship between these two technologies enables you to write simple, modular and powerful applications. Taking into account that Rack has become the backbone of any Web framework written in Ruby, Rack-compatible applications are guaranteed to work with any Rack-supported framework. It only takes one Rack to rule them all!
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How should one hone one&#8217;s skills in Sinatra?</span>
  </p>
  
  <p>
    <strong>Julio>></strong> There is nothing more exciting than pushing the limits of your knowledge even further. In order to succeed in doing this, you have to be intrepid. Do not be afraid of transforming your ideas into neat (or not so neat) lines of code. Even if your task appears to be daunting, do not give up! Carry on until you complete your projects. Study carefully the concepts and the approach to write applications proposed by Sinatra. Then go with the flow and start coding. In cases of a writer’s block, do not despair. Never forget the reason why Internet has become such a popular tool. It abounds with documentation, interactive examples, and of course, billions of blogs, forums, and chats, where kind people are genuinely willing to help you out with your development quest. So go ahead, write some applications and have lots of fun at the same time.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> What type of projects should a beginner work on to gain more expertise in Sinatra?</span>
  </p>
  
  <p>
    <strong>Julio>></strong> It is entirely up to the beginners to decide. There are plenty of applications that they can actually write. My sole piece of advice to all the explorers out there is to be self-centered for just a moment and ask themselves the following question: &#8220;What is the application I actually need?&#8221;. Certainly the answers to that question will vary from a personal website, to a blog system or an application that allows you to manage your finances, your record or DVD collection, etc. In conclusion, just do what you really want but remember to write it as a Sinatra application. If you are proud of what you have developed, brag about it by showing it to other developers around the world!
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Could you suggest some web services that a Sinatra beginner could develop himself / herself?</span>
  </p>
  
  <p>
    <strong>Julio>></strong> Let the starters play again! They are numerous services that they can implement. Consider this to be a gradual process. If you have just created you first Sinatra application, congratulations, you are in. Now, in order to make it even more attractive, try to modify it by adding a RESTful APl if you have not done so already! Make your application respond to any delivery format you like and&#8230; there was light! Now your application can provide information as a web service in XML, JSON, HTML or ever CSV to any client. Of course you will have to develop the client that will consume the API as well. The cool part is that the client can be almost any kind of Software you can possibly imagine: it could be a mysterious command-line application, a typical web admin user interface, a web application, a desktop application, a smart phone application etc. The choice is yours!
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Anything else you would like to add?</span>
  </p>
  
  <p>
    <strong>Julio>></strong> <span style="background-color: #FFFFCC;">It is incredible how much you can accomplish with so little. Arm yourselves with personal motivation, incessant curiosity, and an avid desire to explore this tiny Ruby framework. You will be surprised by the plethora of possibilities that it can offer. Do not waste this chance girls and boys! You will learn lots of interesting stuff if you go this way. I cannot promise you instant fame and fortune but I assure you, it is a whole lot of fun!</span>
  </p>
  
  <p>
    <span style="color:#CC3333;"><em>Thank you Julio. In case you have any queries and/or questions, kindly post your questions here (as comments to this blog post) and Julio would be glad to answer.</em></span>
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
  </ul>
  
  <p class="alert">
    <strong><em>Post supported by 1st Easy Limited</em>:</strong> UK based 1st Easy Limited offer Sinatra and Rails hosting running on a Phusion Passenger (mod_rails) and LAMP stack. If you want to try your hand at developing with Sinatra, why not let them arrange a <a href="http://www.1steasy.com/ruby-on-rails.htm#try">trial hosting account</a> for you? You&#8217;ll get to deploy your app, with full technical support from their team!
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Julio+Javier+Cicchelli" rel="tag">Julio Javier Cicchelli</a>, <a href="http://technorati.com/tag/Sinatra" rel="tag">Sinatra</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>, <a href="http://technorati.com/tag/Learning+Sinatra" rel="tag">Learning Sinatra</a>
