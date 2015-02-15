---
title: Little Known Ways to Ruby Mastery by Josh Susser
author: Satish Talim
date: 2009-01-06
layout: post
permalink: /2009/01/06/little-known-ways-to-ruby-mastery-by-josh-susser/
apostlion@gmail.com:
  - apostlion
categories:
  - Beginners
  - Interview
  - Ruby
  - Ruby Masters
tags:
  - interviews
  - Josh Susser
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
    <img class="alignright" src="http://rubylearning.com/images/josh.jpg" alt="Josh Susser, USA" title="Josh Susser, USA" width="125" height="125" />
  </p>
  
  <p>
    <span class="drop_cap">T</span>his week, we&#8217;re happy to have <strong>Josh Susser</strong> from USA.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Welcome, Josh and thanks for taking out time to share your thoughts. For the benefit of the readers, could you tell us something about your self?</span>
  </p>
  
  <p>
    <strong>Josh>></strong> I&#8217;ve been doing object-oriented programming since the mid-80s, back when hardly anyone had heard the term let alone understood what it was. I&#8217;ve worked on a wide range of object technologies, from Smalltalk applications and virtual machine code to distributed component systems to defining Sun&#8217;s JavaCard virtual machine. Now I&#8217;m a senior developer at <a href="http://pivotallabs.com/">Pivotal Labs</a>, one of the premiere Rails consulting shops and a seriously awesome place to work. I&#8217;m probably best known in the Ruby community for my blog, <a href="http://blog.hasmanythrough.com/">has_many :through</a> and the occasional conference presentation.
  </p>
  
  <p>
    I almost started using Ruby in 2002, but I couldn&#8217;t find much documentation for it on short notice so I ended up doing the project with a combination of Perl and PHP instead. It took until 2005 for me, to really discover Ruby and what it was about. Like so many, I finally came to Ruby because of Rails, and then kicked myself I hadn&#8217;t started using it earlier. I found Ruby very easy to pick up; I had done Smalltalk development for years and some functional stuff here and there, so the basics of the language felt very familiar. But don&#8217;t worry if you don&#8217;t have that kind of background; Ruby is a very accessible language for anyone willing to make the effort.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Dennis Theisen, Germany>></strong> Could you name three features of Ruby that you like the most, as compared to other languages? Why?</span>
  </p>
  
  <p>
    <strong>Josh>></strong> First off, Ruby is fully object-oriented, as opposed to Java, C++ and Objective-C which are hybrid languages. In hybrid languages programs can create data values that aren&#8217;t objects but are some other kind of primitive data type. But in Ruby, every data value you can name is a first-class object. This makes programs more consistent and gives you smaller code since you can use polymorphism everywhere.
  </p>
  
  <p>
    Next, Ruby is dynamically typed, also known as &#8220;duck typed&#8221;, as opposed to being statically typed. This doesn&#8217;t mean Ruby is not strongly typed. It just means that types are enforced at runtime dynamically (via dynamic binding and method lookup) rather than by the compiler. Java on the other hand is statically typed, which is great if you want to be able to prove your programs are correct, but nearly useless in most real-world programming. It just means you spend a lot of time making the compiler happy instead of getting your features working.
  </p>
  
  <p>
    Finally, Ruby has a rich set of control structures and exception handling. The designers of Smalltalk decided that all control structures must be expressed as message sends. This made for very ugly if-then-else (actually ifTrue:ifFalse:) chains, and no one has ever managed to create a useful case statement. Matz rejected this ideological extremism to include special syntax for a number of control structures. As a result the code is smaller and much easier to understand. This is a big part of why I like Ruby better than Smalltalk.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Willian Molinari, Brazil>></strong> What has been your biggest challenge while working with Ruby?</span>
  </p>
  
  <p>
    <strong>Josh>></strong> As much as I like TextMate, I&#8217;m frustrated by the lack of a really good IDE for Ruby. There have been some decent attempts to integrate Ruby into products like IntelliJ and NetBeans, but so far nothing has even reached the point where Smalltalk was 20 years ago. Some of that is due to the extreme dynamism of the Ruby language, and how meta-programmable it is. But whatever the cause, I think we should be able to do better.
  </p>
  
  <p>
    The other challenging thing about Ruby is that it doesn&#8217;t have a major corporate sponsor. Engine Yard, bless their hacker hearts, are doing as much as they can to support Ruby and its ecosystem. But languages like PHP and Python didn&#8217;t really become successful until they got a corporate sponsor who could afford to support development of the language and system libraries. It&#8217;s a testament to Ruby that it&#8217;s come so far without a Yahoo or Google to throw a lot of money and people at it. But that still leaves Ruby with some rough spots that are going to need to be smoothed over before it can live up to its potential.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Jerry Anning, USA>></strong> What best practices are most important for a new Ruby programmer to learn and understand?</span>
  </p>
  
  <p>
    <strong>Josh>></strong> I&#8217;m a big fan of XP so I&#8217;d generally encourage developers to adopt those practices. But specifically, TDD (Test Driven Development) is important for Ruby development. Ruby is a dynamically typed language, which means you don&#8217;t have a compiler to help you find type errors. In practice, type errors aren&#8217;t all that common, but if you want to be able to have confidence that your code is doing what you expect, TDD is the best way to get there. One of the great things about Ruby development is the ease of doing TDD. There are a number of mature and well-supported test frameworks to choose among, and good integration with the popular IDEs and code editors.
  </p>
  
  <p>
    Pair programming is also a good practice to adopt, especially when learning a new language. If you can find a mentor to pair with that&#8217;s great, but pairing with someone who is also learning Ruby is a good way to go too.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Jerry Anning, USA>></strong> Can you recommend things to study after learning Core Ruby, including different frameworks, gems and external libraries?</span>
  </p>
  
  <p>
    <strong>Josh>></strong> This question seems to be based on the assumption that you can go off and learn the Ruby language, then some add-ons, then do something with it. I think that&#8217;s the backwards way to go at things. I&#8217;d suggest finding a project that interests you and figuring out how to use Ruby to do that project. That should naturally suggest other technologies, libraries, frameworks, etc. You can even jump in on an existing open-source project, and that way you won&#8217;t have to think to hard about making those initial technology choices. My point is that learning in a vacuum is the worst way to learn. Learning by doing is more effective and also more satisfying.
  </p>
  
  <p>
    That said, there are probably some good foundation libraries you&#8217;ll want to be familiar with. Learn the three major testing frameworks: test/unit, RSpec and Shoulda. Also get familiar with mocking libraries like RR and Mocha. Beyond that, most of what you&#8217;ll care about is going to be domain-specific, so there isn&#8217;t much point in answering such a generic question with likely irrelevant recommendations.
  </p>
  
  <p>
    As for Ruby itself, there is a lot worth mastering in the Core and Standard Libraries (stdlib). The most high-leverage classes to learn about are String, Array and Hash, as well as the Enumerable mixin. File and IO are pretty useful too. Study and understand those classes and you&#8217;ll be well on your way to Ruby mastery.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Most beginners in Ruby, would like to contribute their time, skills and expertise to a project but invariably are unaware of where and how to do so. Could you suggest some?</span>
  </p>
  
  <p>
    <strong>Josh>></strong> First off, get an account on <a href="http://github.com/">GitHub</a>. (If you haven&#8217;t learned git yet, get going on that too &#8211; it&#8217;s the future for open source SCM.) Then do some exploring around the various projects and see where you think you can jump in and contribute something. Pick a project that is currently under development and has an active community. You&#8217;ll have enough going on that you don&#8217;t want to be championing a project just yet.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Victor Goff, USA>></strong> How do you see the market for Ruby Programmers in the work place, and do you see it as primarily tied to Rails and Web related work? Do you see trends in administration or other work? Whatâ€™s the future for Ruby?</span>
  </p>
  
  <p>
    <strong>Josh>></strong> From what I&#8217;ve seen over the past year, it&#8217;s a very good market for Ruby developers. Most of the Ruby jobs are about building Rails applications or web-related things, but not entirely. I know quite a few developers building all sorts of things in Ruby that aren&#8217;t web apps. But for the moment Ruby is best suited for web development, and that&#8217;s probably going to be true for another year or two. Once we see a faster VM and better library coverage, I think you&#8217;ll see Ruby being used in a wide variety of applications. And if you want to build desktop applications, you should watch out for MacRuby.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> What can / should job candidates (for Ruby) do to distinguish themselves from their competition?<br /><strong>Note</strong>: The candidate has done his/her homework on the company that they are interviewing with. The candidate understands what they&#8217;re looking for, and the candidate is prepared to show them that he/she fits the bill, based on the candidate&#8217;s skills and experience. What else can the candidate do, to set themselves apart from other equally well-qualified and well-prepared candidates?</span>
  </p>
  
  <p>
    <strong>Josh>></strong> This is getting to be a cliche, but contributing to open source projects is one of the best ways to show your stuff. You can demonstrate your technical proficiency, as well as your ability to work in a team, make decisions as a group, resolve conflicts, and deal with rejection (a big part of open source work!).
  </p>
  
  <p>
    The other thing I&#8217;d suggest is to keep a technical blog. Contributing code to a project is great, but that doesn&#8217;t show the whole picture of you. If you keep a blog you can use it to discuss your contributions, document issues, and sound off about things you care about. This is a great way to let employers learn about you, and also demonstrates your communication skills (an essential requirement for almost any job).
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Do you have any other suggestions for these participants (would-be Ruby developers)?</span>
  </p>
  
  <p>
    <strong>Josh>></strong> Ruby is a superb language. It is fully object-oriented, has functional language features like lambdas and higher-order functions, is very easy to meta-program, and has an accessible syntax and flexible structure. But Matz didn&#8217;t invent all those things himself. In fact Ruby is a synthesis of some of the most powerful ideas in computer science. If you want to really appreciate Ruby, you should take some time to study up on the systems from which it is derived. I would start with Smalltalk (Squeak is a free, open source implementation), then read up on Scheme or some other flavor of Lisp. If you haven&#8217;t used Perl, take a look at it just to see how much nicer Ruby&#8217;s syntax is.
  </p>
  
  <p>
    And finally, get out and meet other Rubyists. A big part of what makes Ruby awesome is the community of people who use and contribute to it. Go to a local meetup or a conference and get connected to the community.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Thanks Josh for sharing your views with the RubyLearning participants.</span>
  </p>
  
  <p class="note">
    On 13th Jan. we talk to <strong>Thibaut Barrere</strong> from France.
  </p>
  
  <p>
    <span style="font-size: 8pt; font-family: Arial;"><i><strong>Disclaimer:</strong></i></span><br /><span style="font-size: 8pt; font-family: Arial;"><i>The opinions expressed are those of Josh Susser and do not necessarily reflect those of <strong><a href="http://rubylearning.com/">www.RubyLearning.com</a></strong>.</i></span>
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
    <li>
      #8: <a href="http://rubylearning.com/blog/2008/11/11/little-known-ways-to-ruby-mastery-by-jonathan-conway/">Jonathan Conway</a>
    </li>
    <li>
      #9: <a href="http://rubylearning.com/blog/2008/11/18/little-known-ways-to-ruby-mastery-by-ian-dees/">Ian Dees</a>
    </li>
    <li>
      #10: <a href="http://rubylearning.com/blog/2008/11/25/little-known-ways-to-ruby-mastery-by-bruce-tate/">Bruce Tate</a>
    </li>
    <li>
      #11: <a href="http://rubylearning.com/blog/2008/12/02/little-known-ways-to-ruby-mastery-by-ezra-zygmuntowicz/">Ezra Zygmuntowicz</a>
    </li>
    <li>
      #12: <a href="http://rubylearning.com/blog/2008/12/09/little-known-ways-to-ruby-mastery-by-chris-matthieu/">Chris Matthieu</a>
    </li>
    <li>
      #13: <a href="http://rubylearning.com/blog/2008/12/16/little-known-ways-to-ruby-mastery-by-peter-cooper/">Peter Cooper</a>
    </li>
    <li>
      #14: <a href="http://rubylearning.com/blog/2008/12/23/little-known-ways-to-ruby-mastery-by-yehuda-katz/">Yehuda Katz</a>
    </li>
    <li>
      #15: <a href="http://rubylearning.com/blog/2008/12/30/little-known-ways-to-ruby-mastery-by-ilya-grigorik/">Ilya Grigorik</a>
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Interviews" rel="tag">Interviews</a>, <a href="http://technorati.com/tag/Little+Known+Ways+to+Ruby+Mastery" rel="tag">Little Known Ways to Ruby Mastery</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Ruby+Beginners%26%238217%3B+Questions" rel="tag">Ruby Beginners&#8217; Questions</a>, <a href="http://technorati.com/tag/Josh+Susser" rel="tag">Josh Susser</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>
