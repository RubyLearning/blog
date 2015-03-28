---
draft: false
title: 'Sinatra: Some Questions from Ruby Newbies'
date: 2013-08-14
author: Satish Talim
authorlink: http://satishtalim.com
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/satishtalim/about
categories:
- Beginners
- Learn Sinatra
- Ruby
- Sinatra
layout: post
permalink: /2013/08/14/sinatra-some-questions-from-ruby-newbies/
tags:
- Andy Lindeman
- Carlo Pecchia
- Dan Mayer
- Darren Jones
- Learning Sinatra
- Nathan Esquenazi
- Sinatra
- Sudarshan Shubakar
topsy_short_url:
- http://bit.ly/149Igli
---

<div>
  <p>
    Darren Jones in his excellent book <a href="http://www.amazon.com/gp/product/0987332147/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=0987332147&linkCode=as2&tag=satishtalimsw-20">Jump Start Sinatra</a> says &#8220;<em>Since its release in 2007, Sinatra has quickly gained in popularity in the Ruby web community due to its elegant simplicity and classy syntax. Everybody who uses it falls in love with its elegant simplicity and classy syntax</em>.&#8221;
  </p>
  
  <p>
    RubyLearning will be conducting a &#8220;free&#8221; (i.e. pay if you like) <a href="http://rubylearning.com/blog/2013/08/14/a-free-online-course-on-sinatra/">online course on Sinatra</a> from 7th Sept. 2013 and many of the would-be participants (mostly Ruby newbies) would have a plethora of questions related to Sinatra.
  </p>
  
  <p>
    <strong>Satish Talim</strong> of RubyLearning.org talked to Ruby Gurus Andy Lindeman, Carlo Pecchia, Dan Mayer, Darren Jones, Nathan Esquenazi and Sudarshan Shubakar to answer some of the would-be participant&#8217;s questions.
  </p>
  
  <hr align="center" width="70%" />
  
  <p>
    <span style="color:#0060C0;"><b>Satish</b>>> A warm welcome to you all. For the benefit of the would-be Sinatra course participants, could each one of you tell us something about your self?</span>
  </p>
  
  <p class="block">
    <img class="alignleft" title="Andy Lindeman" src="http://rubylearning.com/images/andylindeman.jpg" alt="Andy Lindeman" /><b>Andy</b>>> I am a software generalist focused on web and mobile. I like open source and work primarily on RSpec. I work at Big Nerd Ranch, primarily writing web application backends in Ruby and Rails. I dabble a good bit: currently Objective C/iOS, Clojure, Erlang, and client-side JavaScript frameworks are on my radar. I like working on open source and meeting new folks in the community.
  </p>
  
  <p class="block">
    <img class="alignright" title="Carlo Pecchia" src="http://rubylearning.com/images/carlopecchia.jpg" alt="Carlo Pecchia" /><b>Carlo</b>>> <a href="http://carlopecchia.eu/">I am</a> an IT engineer mainly interested on agile methodologies and &#8220;good practices&#8221; for developing large and complex systems. I am also interested in web architectures and emerging programming languages.
  </p>
  
  <p class="block">
    <img class="alignleft" title="Dan Mayer" src="http://www.rubylearning.com/images/danmayer.jpg" alt="Dan Mayer" /><b>Dan</b>>> I am a tech lead on the LivingSocial consumer web team. I have been developing Ruby applications since 2007 and often work with both Rails and Sinatra. I believe in trying to keep code small, and breaking applications up into logical components and services. My thoughts on development can be found on <a href="http://mayerdan.com/">http://mayerdan.com</a>. I am on twitter as <a href="https://twitter.com/danmayer">@danmayer</a>
  </p>
  
  <p class="block">
    <img class="alignright" title="Darren Jones" src="http://www.rubylearning.com/images/darrenjones.jpg" alt="Darren Jones" /><b>Darren</b>>> <a href="http://daz4126.com/">I am</a> the author of <a href="http://www.amazon.com/gp/product/0987332147/ref=as_li_ss_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=0987332147&linkCode=as2&tag=satishtalimsw-20">Jump Start Sinatra</a>, a short book that helps you to get up to speed with Sinatra over a weekend, published by Sitepoint. I have been using Sinatra since 2009 and used it to build the <a href="http://cardsinthecloud.com/">Cards in the Cloud</a> website. I live in Manchester in the UK where I teach Mathematics and enjoy playing water polo.
  </p>
  
  <p class="block">
    <img class="alignleft" title="Nathan Esquenazi" src="http://www.rubylearning.com/images/nathanesquenazi.jpg" alt="Nathan Esquenazi" /><b>Nathan</b>>> I am one of the creators of the <a href="http://www.padrinorb.com/">Padrino framework</a>, enabling powerful extensions to the Sinatra core and the co-founder of <a href="http://thecodepath.com/">CodePath</a>, providing practical training to engineers interested in learning mobile development.
  </p>
  
  <p class="block">
    <img class="alignright" title="Sudarshan Shubakar" src="http://www.rubylearning.com/images/sudarshanshubakar.jpg" alt="Sudarshan Shubakar" width="115" height="115" /><b>Sudarshan</b>>> I am a software developer based out of Pune, India. I enjoy working with design principles and patterns, learning new programming languages and a bit of open source development. I am majorly a Java developer for the past 11 years and have recently started working on Ruby out of interest.
  </p>
  
  <p>
    <span style="color:#0060C0;"><b>Satish</b>>> What is Sinatra best suited for?</span>
  </p>
  
  <p class="block">
    <b>Andy</b>>> Simple web apps, especially those that are mostly APIs or only have a few views.
  </p>
  
  <p class="block">
    <b>Carlo</b>>> Sinatra is an &#8220;essential&#8221; framework for Ruby based web application. Talking about &#8220;web app&#8221; the point of reference is &#8211; without any doubt &#8211; RubyOnRails (RoR): Sinatra is lightweight compared to it. You have less features, but also less stuff to digest to start with. Personally I&#8217;ve used Sinatra (and I was really satisfied by it) for apps where data complexity and user interactions are not critical points (in my case: internal enterprise app).
  </p>
  
  <p class="block">
    <b>Dan</b>>> Sinatra is great for smaller applications and apis. Sinatra fits really well when there is a limited front end which uses a lot less of the standard view layer helpers and other features common in Rails. I have personally found that Sinatra is best for APIs and micro sites. If an application with a significant front end is going to be developed, it is often best to start with rails as you will start to home grow and try to replace many common features of rails with your own bad implementations. Finally people often forget how much rails helps in terms of basic security precautions, making it harder to make common mistakes. There is a well known Ruby community quote that I can&#8217;t find attribution for, &#8220;every Ruby web framework eventually becomes a horrible bad and buggy implementation of rails&#8221;.
  </p>
  
  <p class="block">
    <b>Darren</b>>> Putting your Ruby code onto the web! At its heart Sinatra is essentially just a wrapper for making it easy to deal with HTTP requests and responses by providing some very nice helper methods. This means that it is suited for anything that you can write in Ruby. It can handle small projects brilliantly but is also great for larger projects too.
  </p>
  
  <p class="block">
    <b>Nathan</b>>> Sinatra is incredibly well-suited for building REST APIs for mobile clients as well as web back-end services that are paired with modern javascript frameworks like Backbone, AngularJS, Ember, et al.
  </p>
  
  <p class="block">
    <b>Sudarshan</b>>> The Sinatra book <a href="http://sinatra-book.gittr.com/#introduction">introduction</a> says it best by these statements:<br />* In Sinatra, you can write short ad hoc applications or mature, larger application with the same easiness.<br />* Sinatra really shines when used for experiments and application mock-ups or for creating a quick interface for your code.<br />My take on this is that Sinatra gets you started quickly on whatever problem you are trying to solve (with a web/URL based solution) quickly. There is hardly a learning curve and you can have a meaningful implementation of your solution within no time.
  </p>
  
  <p>
    Another point where Sinatra is most useful is when you would like finer control over how your application is organized. This <a href="http://stackoverflow.com/questions/3068114/what-is-the-limit-of-sinatra">discussion on stackoverflow.com</a> provides some good inputs on how Sinatra compares to Rails. As one person says in this discussion, there is no limit to what you can do with it.
  </p>
  
  <p>
    <span style="color:#0060C0;"><b>Satish</b>>> I am a Ruby newbie and if I learn Sinatra, does that help me with Ruby on Rails?</span>
  </p>
  
  <p class="block">
    <b>Andy</b>>> I think it depends on exactly how much you know.
  </p>
  
  <p>
    For folks with little background on programming or web application development at all, I think it&#8217;s a great fit. There&#8217;s not very much &#8220;magic&#8221; and it&#8217;s easy to get up and running quickly.
  </p>
  
  <p class="block">
    <b>Carlo</b>>> Sure! Learning Sinatra gives you all the details about how HTTP protocol is handled; how routing works; how to manage your models; how to talk with a Data Base (noSQL are welcome too); how a template system has to be used; and so on. My suggestion is: start with Sinatra, and *then* consider RoR for &#8220;not small&#8221; projects.
  </p>
  
  <p class="block">
    <b>Dan</b>>> Learning Sinatra is a great way to begin to learn Rails. It will definitely help you learn Rails as it helps you learn Ruby basics as well as common Ruby web development practices. In many ways it is a smaller and simpler way to learn to work with a web framework, which is excellent. I find while this is great for learning, it leads to a less natural project structure and uncommon patterns for larger applications. Actually learning some of the basic web development concepts first in Sinatra would help one to understand why these concepts exist and why they are bit more complicated in Rails.
  </p>
  
  <p class="block">
    <b>Darren</b>>> A little, but it is more useful for improving your Ruby. I think that it would help you understand some of the &#8216;magic&#8217; that Rails does in the background as you have a lot more control with Sinatra.
  </p>
  
  <p class="block">
    <b>Nathan</b>>> Sinatra is an excellent introduction to the Ruby language and to web development. Sinatra has a remarkably short learning curve and as such allows for new developers to tinkering with web apps of all sorts with minimal overhead or confusion. The distinct advantage of learning Sinatra while you are developing your Ruby acumen is that Sinatra is very explicit and simple allowing the expressiveness of Ruby itself to shine through.
  </p>
  
  <p class="block">
    <b>Sudarshan</b>>> Hmm, will Sinatra help one learn Ruby on Rails&#8230; probably not in an obvious manner. However my understanding is that if one tries to build a well-structured MVC application with Sinatra, one would find it easier to appreciate what Rails offers out of the box and why it mandates what it does.
  </p>
  
  <p>
    With Sinatra there is almost no mandate apart from the dsl syntax itself. So you are free to organize your application any way you like.
  </p>
  
  <p>
    If you are trying to learn Rails while you are developing your pet application, my understanding is that you may find it slightly difficult because you may need to deviate from your problem domain to understand the framework. This probably isn&#8217;t true if you are just trying to learn Rails with just a mock application.
  </p>
  
  <p>
    With Sinatra, like I&#8217;ve already mentioned, there is hardly a learning curve and you stay focused on your problem domain.
  </p>
  
  <p>
    <span style="color:#0060C0;"><b>Satish</b>>> How much Ruby do I have to cover in order to start learning Sinatra?</span>
  </p>
  
  <p class="block">
    <b>Andy</b>>> I think it again depends on what an individual developer&#8217;s background is.
  </p>
  
  <p>
    Developers who are new to Ruby but know other object-oriented languages will likely pick up enough Ruby to be proficient very quickly.
  </p>
  
  <p>
    Other developers may need more basics about the structure and basic syntax and semantics of programming languages first.
  </p>
  
  <p>
    That said, I think you could pair a lot of the learning: while introducing a Sinatra concept, also introduce some Ruby concepts.
  </p>
  
  <p class="block">
    <b>Carlo</b>>> At the very beginning &#8220;not too much&#8221;, but if and when you want to code seriously you have to dirty your hands. There is no escape! <img src="http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif" alt=":-)" class="wp-smiley" />
  </p>
  
  <p class="block">
    <b>Dan</b>>> I would make sure to cover some Ruby basics firsts:
  </p>
  
  <p>
    * Running a ruby script<br />* variables<br />* method calls<br />* basic data structures (array, hashes, strings, and numericals)
  </p>
  
  <p>
    After making sure those basics are understood, I think you could get into Sinatra specifics. It would also likely help to have a basic knowledge of html, CSS, and possibly JSON, if you are planning to cover api endpoints.
  </p>
  
  <p class="block">
    <b>Darren</b>>> Not much at all to get started. But the more Ruby you know, the better your Sinatra applications will be. As I mentioned in my answer to question 1, Sinatra apps are basically just Ruby apps put on the web, so the standard of your Sinatra app will be directly linked to how much Ruby you know. The Sinatra source code is written in Ruby and a great exercise is to read through it (it&#8217;s only around 2000 lines and very well commented). This will help to improve your Ruby skills and help you to understand how Sinatra works.
  </p>
  
  <p class="block">
    <b>Nathan</b>>> Sinatra is entirely built using idiomatic ruby constructs and patterns. That said you can start tinkering with Sinatra well before you have a strong grasp on Ruby. I would recommend taking the time to first familiarize yourself with the basic ruby constructs and then you can quickly dive in and learn by doing.
  </p>
  
  <p class="block">
    <b>Sudarshan</b>>> Have you seen <a href="http://www.sinatrarb.com/">http://www.sinatrarb.com/</a> !!:)
  </p>
  
  <p>
    I needed a beginner&#8217;s level knowledge of Ruby to start using Sinatra.
  </p>
  
  <p>
    However, when you are learning a new language like Ruby and using something like Sinatra to do so, it is important to understand where the domain of the framework starts blurring and your problem domain begins to shine.
  </p>
  
  <p>
    So you may need to understand Ruby much deeper to efficiently solve the actual problem that you are working on.
  </p>
  
  <p>
    <span style="color:#0060C0;"><b>Satish</b>>> How important is it for me to know Rack while learning Sinatra?</span>
  </p>
  
  <p class="block">
    <b>Andy</b>>> I think Rack is pretty simple for experienced developers to understand, but understanding why it&#8217;s needed and how it fits is a bit more abstract and difficult. I don&#8217;t think new developers need to understand Rack while learning Sinatra.
  </p>
  
  <p class="block">
    <b>Carlo</b>>> Rack is a very basic and important component, don&#8217;t be afraid by it. I strongly encourage you to take half a day to study it: it&#8217;s time well invested.
  </p>
  
  <p class="block">
    <b>Dan</b>>> While Rack is great, I think it could likely be skipped over at the beginning to allow new users to just think in terms of a Sinatra request and response cycle. It might be a good thing to cover a bit further into the lessons, but to help users get to the first goal to dynamically add information to a page, I don&#8217;t believe knowledge of Rack is really necessary.
  </p>
  
  <p class="block">
    <b>Darren</b>>> I don&#8217;t think you need to know much about Rack, except that Sinatra (and most other Ruby frameworks) uses it extensively in the background. Once you get more confident with Sinatra then you can start to dig a bit deeper into how Rack runs the show in the background, but it isn&#8217;t essential when you first start.
  </p>
  
  <p class="block">
    <b>Nathan</b>>> Rack is the web-server interface that underlies web development in Ruby. Learning about Rack and Rack middleware development will give the developer an insightful look under the hood at how the request/response model of the web interacts in ruby-based web libraries.
  </p>
  
  <p class="block">
    <b>Sudarshan</b>>> It is possible to write simple Sinatra apps in the classic style without using Rack. However as your app begins to gather a bit of complexity, you will want to shift to the Modular style. Here&#8217;s where Rack will help you organize your app better. This is of course apart from the benefit of web server abstraction Rack inherently provides.
  </p>
  
  <p>
    <span style="color:#0060C0;"><b>Satish</b>>> While developing Sinatra apps which style (Modular or Classic) should I use?</span>
  </p>
  
  <p class="block">
    <b>Andy</b>>> If the audience is beginners, I&#8217;d start with classic because you have to keep very little context in your head. As the audience becomes more experienced, move toward a more modular approach.
  </p>
  
  <p class="block">
    <b>Carlo</b>>> It depends roughly on your application &#8220;size&#8221;. Modular style gives you more maintainable and readable code. Anyway start with Classic and then when your app grows up, consider switching to Modular style.
  </p>
  
  <p class="block">
    <b>Dan</b>>> I think for teaching beginners, the Classic style is simpler to understand and would be quicker to get students to the learn / reward cycle. Sinatra apps that grow large, is where the modular approach has many advantages. For larger apis, the modular approach is definitely the way to go, but often I find when you are really utilizing that approach it would make sense to just have a full Rails app. I haven&#8217;t ended up building out to many very large Sinatra applications so there might be other advice on this point.
  </p>
  
  <p class="block">
    <b>Darren</b>>> It doesn&#8217;t matter at all. I really like the fact that the Classic style allows you to get started really quickly and build apps with all the code in just a single file. The modular style makes it easier to organize large applications and is a good approach if you are working in teams as each module can be developed independently of the other. Modular apps also make it easier to reuse and share code in other projects.
  </p>
  
  <p class="block">
    <b>Nathan</b>>> While tinkering around learning Sinatra or for extremely simple apps, use classic. For writing middle-wares and production applications, I recommend using Modular. Modular is more explicit and I prefer having my Sinatra apps contained within an explicit class of my choosing. I don&#8217;t see many benefits to using the classic style.
  </p>
  
  <p class="block">
    <b>Sudarshan</b>>> When you are starting to learn Sinatra, I would recommend using the classic style to get a feel of how things work. If you are building a meaningful application of even moderate complexity, the Modular style will help you keep your code organized. Once you are familiar with the Modular style of organizing your Sinatra app, you may be able to work with the Modular style with ease from the word go.
  </p>
  
  <p class="alert">
    <em>Well, we have set the ball rolling. <b>What&#8217;s your take on this?</b> Kindly post your thoughts as comments to this blog post. Looking forward to some interesting read.</em>
  </p>
</div>

