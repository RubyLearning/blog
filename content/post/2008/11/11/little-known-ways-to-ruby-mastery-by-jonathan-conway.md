---
title: Little Known Ways to Ruby Mastery by Jonathan Conway
author: Satish Talim
date: 2008-11-11
layout: post
permalink: /2008/11/11/little-known-ways-to-ruby-mastery-by-jonathan-conway/
keywords:
  - "ruby for beginners,ruby beginners,ruby programming,ruby on rails blog,rails blog,rails tutorials,ruby beginners\\\' questions,little known ways to ruby mastery,ruby masters,interviews,Jonathan Conway,ruby,the ruby programming language"
description:
  - The Path to Ruby Mastery Interview Series by Ruby Masters, provides guidance to and answers questions confronting Ruby beginners from across the globe.
categories:
  - Beginners
  - Interview
  - Ruby
  - Ruby Masters
tags:
  - interviews
  - Jonathan Conway
  - Little Known Ways to Ruby Mastery
  - Ruby
  - "Ruby Beginners' Questions"
  - The Ruby Programming Language
---
<div>
  <h3>
    A weekly series from the Ruby Masters
  </h3>
  
  <p class="update">
    Welcome to the next installment of the weekly interview series on the <abbr title="RubyLearning">RL</abbr> blog &#8211; &#8220;<strong>Path to Ruby Mastery</strong>&#8221; &#8211; by top trainers and developers in the <strong>Ruby community</strong>, from across the globe. The interview series will provide insight and commentary from these notable Ruby trainers and developers, with the goal of facilitating and providing answers to the questions <strong>Ruby beginners</strong> face. We welcome your suggestions for interviewees and questions. Look for a new post every Tuesday!
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/jonathan_conway.jpg" alt="Jonathan Conway, UK" title="Jonathan Conway, UK" width="125" height="130" />
  </p>
  
  <p>
    <span class="drop_cap">T</span>his week, we&#8217;re happy to have <strong>Jonathan Conway</strong> from UK.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Welcome, Jonathan and thanks for taking out time to share your thoughts. For the benefit of the readers, could you tell us something about your self?</span>
  </p>
  
  <p>
    <strong>Jonathan>></strong> It all started when I was bitten by a radioactive Commodore Vic 20 at the age of six. Apart from suddenly having the ability to keep still for long periods of time while staring at a screen. I found that I had a sudden love of power for the ability to control this Ê»micro<br /> computerÊ¼ with programming.
  </p>
  
  <p>
    I first started programming commercially as a freelancer in the mid 90Ê¼s doing BBS intros in Assembler and some applications in C before going on to University. At some point while I was there I learned Java which is what I did for the most part for several years. IÊ¼d done everything from large dot com e-commerce sites on the web to real-time financial trading applications on J2ME enabled devices, but deep down I wasnÊ¼t happy. It all seemed like so much work for so little return.
  </p>
  
  <p>
    Being young it didnÊ¼t seem to matter so much as time was something I had plenty of until I got married and had my first child. Around this time I was working as a technical architect for a company in the City, we had a small team and I was adamant that there was a better way to deliver software in shorter time scales beyond just Agile methods. During late 2004 IÊ¼d already been using Ruby for server administration. DHH presentation at some university was making the rounds and I realized that I could use Ruby for more than server administration.
  </p>
  
  <p>
    Anyway to cut a long story short I re-signed from my job and setup the UKÊ¼s first Ruby on Rails consultancy called Agile Evolved (yeh, I know cheesy name), grew the company with some very talented employees before merging with New Bamboo in early 2007. I stayed as the technical director for a bit before getting snapped up by a start up where I currently work called vzaar Yep thatÊ¼s a small Ê»vÊ¼, weÊ¼re that 2.0;).
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Keith Brady, Australia>></strong> What are the pros and cons of Ruby that are being discussed in the development community and what is your opinion on that?</span>
  </p>
  
  <p>
    <strong>Jonathan>></strong> For proÊ¼s for the Ruby language I think the first thing people notice is the amount of flexibility and power it gives you. This can be quite scary/dangerous for some people as theyÊ¼re so used to languages like Java/C# constraining them and Ê»keeping them safeÊ¼. But for a talented developer this can be incredibly liberating. Another pro of Ruby would have to be Ruby gems. After spending too long in languages where I had to physically go off, hunt down and install a library in my path, having the use of Ruby gems was a instant win for productivity for me.
  </p>
  
  <p>
    For conÊ¼s of the language? Well to be honest unless youÊ¼re trying to use Ruby like a golden hammer I canÊ¼t think of any that come to mind. I always encourage all developers to be skilled at more than one language and embrace other paradigms found in them. ItÊ¼s always about using the right tool for the job.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Jerry Anning, USA>></strong> What best practices are most important for a new Ruby programmer to learn and understand?</span>
  </p>
  
  <p>
    <strong>Jonathan>></strong> With regards to best practices in Ruby the first thing would be to embrace the languages flexibility and dynamicness and forget what they thought was OO. When I first came to Ruby I brought with me all kinds of stupid Java baggage such as trying to create Abstract classes etc.
  </p>
  
  <p>
    Unless youÊ¼re coming from another language such as Smalltalk then chances are that your previous staple language wasnÊ¼t as pure from an OO stand point as Ruby is. And I know IÊ¼m gonna start a flame war and sound elitist with some people but seeing PHP developers call their PHP 5 code Object Orientated just makes me chuckle. ItÊ¼s not their fault most of the time as theyÊ¼re just doing the best they can with the object model theyÊ¼ve been given. But seeing quite a few ex PHP devÊ¼s creating Frankensteins of pseudo OO Ruby code makes me realize how important that new beginners have a clear foundation of the fundamentals of good Object Orientated design.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Jerry Anning, USA>></strong> Can you recommend things to study after learning Core Ruby, including different frameworks, gems and external libraries?</span>
  </p>
  
  <p>
    <strong>Jonathan>></strong> My personal favorite libraries to look at for clever yet clean and understandable code would be the following:
  </p>
  
  <ol>
    <li>
      Thinking Sphinx by Pat Allan. ItÊ¼s very well written and easy to jump into if you need to change it for your own purposes.
    </li>
    <li>
      Datamapper by Sam Smoot. A very nicely abstracted ORM that gives you great flexibility.
    </li>
    <li>
      Ramaze by lots of very smart people. Although I use Merb for my everyday tasks I have to tip my hat to Ramaze. Very thorough test suite, advanced use of Ruby yet very easy to understand.
    </li>
  </ol>
  
  <p>
    <span style="color:#CC3333;"><strong>Victor Goff, USA>></strong> How do you see the market for Ruby Programmers in the work place, and do you see it as primarily tied to Rails and Web related work? Do you see trends in administration or other work? Whatâ€™s the future for Ruby?</span>
  </p>
  
  <p>
    <strong>Jonathan>></strong> The market for Ruby programmers I feel will only get stronger. However one of the common traits of a Ruby developer is that they prefer to work freelance. This has made it considerably harder for companies to hire full time people. Not only that but IÊ¼ve come across quite a few freelancers who have difficulty with the concepts of basic OO let alone good Ruby practices and yet have no qualms with charging the market rates for top end developers. I feel something will inevitably has to change in the future so as not to tarnish the reputation of Ruby developers and keep a healthy ecosystem of Ruby jobs alive.
  </p>
  
  <p>
    Another thing is that hiring companies need to be smarter and go beyond the usual academic/paper skills when seeking out new talent. IÊ¼ve been lucky to snap up incredibly talented people in the past who have been turned down by other larger companies. This is because unfortunately a lot of companies interviewing processes are either amateurish or outdated at best.
  </p>
  
  <p>
    My personal interviewing technique is based upon psychology and technical ability designed to make the interviewee as relaxed as possible so that I can see their true abilities/potential and more importantly how theyÊ¼ll interact with others at work in a social environment. Remember a good team dynamic is crucial to successful delivery of projects.
  </p>
  
  <p>
    Seeing what Jamie Van Dyke is doing at Parfa.it with regards to recruiting for clients I think is definitely going in the right direction to solve some of the problems IÊ¼ve outlined above.
  </p>
  
  <p>
    Woah, I kind of side tracked there but to keep on target I definitely see inroads into server/cloud administration with Ruby. The languages readability coupled with libraries like Puppet, Capistrano/Vlad, Thor, Vertebra and others make Ruby an Ops guys dream come true.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> What can / should job candidates (for Ruby) do to distinguish themselves from their competition?<br /><strong>Note</strong>: The candidate has done his/her homework on the company that they are interviewing with. The candidate understands what they&#8217;re looking for, and the candidate is prepared to show them that he/she fits the bill, based on the candidate&#8217;s skills and experience. What else can the candidate do, to set themselves apart from other equally well-qualified and well-prepared candidates?</span>
  </p>
  
  <p>
    <strong>Jonathan>></strong> I think the number one thing that everyone will tell you makes potential candidates stand out is contributions to Open Source. Preferably one with a good test suite, but thatÊ¼s my personal bias.
  </p>
  
  <p>
    The other thing is to spend time on personal projects. Even if theyÊ¼re not Open Source, the ability to demonstrate your skills across a wide range of areas from the front to the back end in a web development context is priceless. If youÊ¼re going for an OpÊ¼s job then writing a library for administering a cloud should increase your chances by a magnitude. Hopefully if the person interviewing you is smart and not doing the outdated cookie cutter style interviewing technique then youÊ¼ll definitely be in their top ten.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Thanks Jonathan for sharing your views with the RubyLearning participants.</span>
  </p>
  
  <p class="note">
    On 18th Nov. we talk to <strong>Ian Dees</strong> from USA.
  </p>
  
  <p>
    <span style="font-size: 8pt; font-family: Arial;"><i><strong>Disclaimer:</strong></i></span><br /><span style="font-size: 8pt; font-family: Arial;"><i>The opinions expressed are those of Jonathan Conway and do not necessarily reflect those of <strong><a href="http://rubylearning.com/">www.RubyLearning.com</a></strong>.</i></span>
  </p>
  
  <p>
    <strong>The Path to Ruby Mastery Series (So Far)</strong>:
  </p>
  
  <ul>
    <li>
      #1: <a href="http://rubylearning.com/blog/2008/09/23/little-known-ways-to-ruby-mastery-by-jamie-van-dyke/">Jamie van Dyke</a>
    </li>
    <li>
      #2: <a href="http://rubylearning.com/blog/2008/09/30/little-known-ways-to-ruby-mastery-by-james-edward-gray-ii/">James Edward Gray II</a>
    </li>
    <li>
      #3: <a href="http://rubylearning.com/blog/2008/10/07/little-known-ways-to-ruby-mastery-by-dr-nic-williams/">Dr Nic Williams</a>
    </li>
    <li>
      #4: <a href="http://rubylearning.com/blog/2008/10/14/little-known-ways-to-ruby-mastery-by-stuart-halloway/">Stuart Halloway</a>
    </li>
    <li>
      #5: <a href="http://rubylearning.com/blog/2008/10/21/little-known-ways-to-ruby-mastery-by-jay-fields/">Jay Fields</a>
    </li>
    <li>
      #6: <a href="http://rubylearning.com/blog/2008/10/28/little-known-ways-to-ruby-mastery-by-chris-osullivan/">Chris O&#8217;Sullivan</a>
    </li>
    <li>
      #7: <a href="http://rubylearning.com/blog/2008/11/04/little-known-ways-to-ruby-mastery-by-guy-naor/">Guy Naor</a>
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Interviews" rel="tag">Interviews</a>, <a href="http://technorati.com/tag/Jonathan+Conway" rel="tag">Jonathan Conway</a>, <a href="http://technorati.com/tag/Little+Known+Ways+to+Ruby+Mastery" rel="tag">Little Known Ways to Ruby Mastery</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Ruby+Beginners%26%238217%3B+Questions" rel="tag">Ruby Beginners&#8217; Questions</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>
