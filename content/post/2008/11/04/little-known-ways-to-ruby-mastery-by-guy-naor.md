---
title: Little Known Ways to Ruby Mastery by Guy Naor
author: Satish Talim
date: 2008-11-04
layout: post
permalink: /2008/11/04/little-known-ways-to-ruby-mastery-by-guy-naor/
keywords:
  - "ruby for beginners,ruby beginners,ruby programming,ruby on rails blog,rails blog,rails tutorials,ruby beginners\\\' questions,little known ways to ruby mastery,ruby masters,interviews,Guy Naor,ruby,the ruby programming language"
description:
  - The Path to Ruby Mastery Interview Series by Ruby Masters, provides guidance to and answers questions confronting Ruby beginners from across the globe.
categories:
  - Beginners
  - Interview
  - Ruby
tags:
  - Guy Naor
  - interviews
  - Little Known Ways to Ruby Mastery
  - Ruby
  - "Ruby Beginners' Questions"
  - ruby for beginners
  - Ruby Masters
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
    <img class="alignright" src="http://rubylearning.com/images/guynaor2.jpg" alt="Guy Naor, USA" title="Guy Naor, USA" width="125" height="114" />
  </p>
  
  <p>
    <span class="drop_cap">T</span>his week, we&#8217;re happy to have <strong>Guy Naor</strong> from USA.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Welcome, Guy and thanks for taking out time to share your thoughts. For the benefit of the readers, could you tell us something about your self?</span>
  </p>
  
  <p>
    <strong>Guy>></strong> I am a long time veteran of the computing world. I started as a teenager back in the early 80&#8217;s with the earliest personal computers. Since then I programmed and managed development on a huge number of operating systems, languages and frameworks. After many years writing applications on Windows in C++, I decided to switch to web development. Those were the early days of Ruby on Rails, but after a comparison with the rest of the options, and although it was new and lightly documented, I decided to start my web development career using Rails. I am very passionate about technology and it&#8217;s real life application. In my spare time I do marathon running, scuba diving and traveling with my family.
  </p>
  
  <p>
    Professionally I now serve as the CTO of <a href="http://mor.ph/">Morph Labs</a> which provides a high quality and scalable deployment system on the cloud. It allows a full production deployment in a matter of minutes, and actually crystallizes deployment experience and knowledge into a fully automated system.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Willian Molinari, Brazil>></strong> How should one go about learning the Ruby language? What material (books, eBooks, online tutorials etc.) would you recommend?</span>
  </p>
  
  <p>
    <strong>Guy>></strong> I personally like the standard &#8220;The Ruby Programming Language&#8221; augmented with &#8220;The Ruby Way&#8221; and _why&#8217;s book. It is my experience and belief that one need to know Ruby really well in order to be an exceptional programmer in anything that uses Ruby. Be it Rails, Merb or just using it for system administration tasks and glue logic.
  </p>
  
  <p>
    I would recommend getting a really good understanding of Ruby meta-programming. It&#8217;s important to note that knowing C++ or Java doesn&#8217;t really prepare you for all the Ruby meta-programming has to offer. In addition, regular expressions. It seems to be an area many people struggle with. But if you have a good command of it you can do magic with it. Just please document what you do with it, or after a month and you have no idea what&#8217;s gong on!
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Keith Brady, Australia>></strong> What are the pros and cons of Ruby that are being discussed in the development community and what is your opinion on that?</span>
  </p>
  
  <p>
    <strong>Guy>></strong> I think that the biggest complains are speed and lack of libraries/packaging standards. On the speed side, I don&#8217;t think it&#8217;s a big problem. Most tasks needed do not pose a speed issue in real life. When something is a bottleneck, writing a few functions in C and interfacing to Ruby solves the problem. As a real life example, I once needed to analyze very large CSV files. Most of it was done in Ruby, but one part was ported to C and I saw a 100x improvement. It doesn&#8217;t mean I&#8217;ll ever want to write the whole system in C. This also leads me to the need for developers to be able to work in multiple languages and environments. I&#8217;m a strong believer in each tool for its job, and that let me be a lot more productive than trying to fit all into Ruby, C or Java alone.
  </p>
  
  <p>
    As for the library problem, though gems are a great start, they are not as well standardized as CPAN on Perl for example. But this is not an inherent Ruby issue, just something the community need to improve and standardize. If we had a very standard and accepted way of documenting and packaging, we would be a long way toward easier packaging and redistribution.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Willian Molinari, Brazil>></strong> What has been your biggest challenge while working with Ruby?</span>
  </p>
  
  <p>
    <strong>Guy>></strong> Coming from years of C++ development on Windows, and doing it directly to the Windows API (no MFC, OWL, ATL), the richness of the language and the meta-programming model surprised me. I was sure I knew everything I need about object oriented programming. What a surprise was it to see what Ruby can do. I still admire it every time I use some deep OO programming on Ruby. Passing the barrier of understanding it was a big leap in my ability to work with the language.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Jerry Anning, USA>></strong> What best practices are most important for a new Ruby programmer to learn and understand?</span>
  </p>
  
  <p>
    <strong>Guy>></strong> It is important to learn what&#8217;s accepted in the community as a writing standard. For example, when to use {} as opposed to begin/end. When not to over complicate or be too terse. The best way to learn that is to read code. See what other known libraries, systems and framework use. Then try and use the same in your code. There is a tendency when first learning Ruby to make stuff too terse (one line doing 50 different actions by chaining calls). Many times we do that only because we can. But coming to it a month later, and you can&#8217;t even understand what you did. This also bring me to commenting code. Many people think that Ruby is so readable you don&#8217;t need to comment. Well, that is NOT true. Many times the reason for something isn&#8217;t clear, even if the line reads clearly. And that is especially true in case where using a lot of regular expressions. When I write code I tend to practice what I call comment driven coding &#8211; write the comments, then write the code. This way you always keep your line of thought, and you get documented code.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Jerry Anning, USA>></strong> Can you recommend things to study after learning Core Ruby, including different frameworks, gems and external libraries?</span>
  </p>
  
  <p>
    <strong>Guy>></strong> This depends on what you want to practice. If you are going into web development, Rails is an obvious framework to learn. If you want to go into system management or deployments, learning Capistrano and Puppet will be very beneficial. If you have a specific area that interest you, look for libraries that target that area. For example, interested in telephony? Try RAGI or Adhearsion. Interested in XMPP? Try xmpp4r. There are thousands of projects for almost any interest you have.
  </p>
  
  <p>
    Personally I constantly use Rails, Capistrano and a lot of Ruby as a scripting language. Almost all my system administration scripts are written in Ruby. I use bash for very basic stuff, the rest is in Ruby.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Most beginners in Ruby, would like to contribute their time, skills and expertise to a project but invariably are unaware of where and how to do so. Could you suggest some?</span>
  </p>
  
  <p>
    <strong>Guy>></strong> I don&#8217;t think there are specifics here. It be something that interest you personally, or you won&#8217;t last long. Anything you do on your free time needs to be something you enjoy or need. As for finding projects, the best bet is just look at the project that interest you on the mailing lists, RubyForge or GitHub, then contact the maintainer/developer. Most people are friendly and would love to get help. Sometimes it&#8217;s better to start with documenting as it lets you get into the code and understand it better, before actually writing. But I know that almost all projects are welcoming to help. It will be harder on large projects like Rails &#8211; mainly because of the huge number of people already involved. But even there it&#8217;s not too hard. The most important thing is follow the project for some time understanding what is the accepted way to contribute, and who are the leaders. Then join and help.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Keith Brady, Australia>></strong> What types of applications are currently being developed in Ruby and what changes do you foresee over the next year or two?</span>
  </p>
  
  <p>
    <strong>Guy>></strong> The vast majority are Web applications. It comes from the fact that Rails is written in Ruby and it is what popularized Ruby in the first place. With time it will move back to it&#8217;s roots as a system administration/glue language. I use it constantly in that role, and know of many others that do as well. Those systems are usually less public as they work the inside of the systems and networks. I do expect many systems to come into the open as time passes. Capistrano is an interesting example, as it&#8217;s used for many things outside Rails deployments. I use it extensively to manage large numbers of servers in clouds. I know that there are Capistrano recipes for a multitude of system administration tasks, and to deployments of non Rails systems. Other systems that need flexibility and speed of development that Ruby provide will sure follow. And no, I don&#8217;t expect Ruby to take control of the world. There are many needs and may tools. There is no &#8220;one true&#8221; language.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Victor Goff, USA>></strong> How do you see the market for Ruby Programmers in the work place, and do you see it as primarily tied to Rails and Web related work? Do you see trends in administration or other work? Whatâ€™s the future for Ruby?</span>
  </p>
  
  <p>
    <strong>Guy>></strong> Currently Rails takes the biggest chunk of Ruby developers. But I see a strong future in other places like system administration. I believe this will grow as more people with Ruby experience enter the workforce. Big as it is, Ruby is still a tiny part of the overall market, the more people know and feel comfortable with it, the more places we will see it going. People tend to work with what they are comfortable in. Once you are as comfortable with Ruby as you are with bash for system admin, you will move to using Ruby a lot more. I expect this trend to accelerate in the next couple of years.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> What can / should job candidates (for Ruby) do to distinguish themselves from their competition?<br /><strong>Note</strong>: The candidate has done his/her homework on the company that they are interviewing with. The candidate understands what they&#8217;re looking for, and the candidate is prepared to show them that he/she fits the bill, based on the candidate&#8217;s skills and experience. What else can the candidate do, to set themselves apart from other equally well-qualified and well-prepared candidates?</span>
  </p>
  
  <p>
    <strong>Guy>></strong> Know the language well and to depth. Get experience working with some of the Open Source projects. Write some interesting code you can share. The big advantage of participating in an Open Source project, is that it lets employers actually look at what you do. And also show them you are involved with the community and have code good enough to be accepted. The ability to look at code you actually wrote is a big plus when looking for developers. It speaks a lot louder than any resume you will write.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Do you have any other suggestions for these participants (would-be Ruby developers)?</span>
  </p>
  
  <p>
    <strong>Guy>></strong> Know more tools and languages than just Ruby. Keep yourself updated with changes and news. But don&#8217;t try to latch into every new idea coming to the market. If you are looking for employment, most companies are not at the bleeding edge of technology. You should be aware of what&#8217;s out there, and get familiar with it. But have a strong understanding and command of what is being widely used today &#8211; companies gravitate toward the proven technologies.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Thanks Guy for sharing your views with the RubyLearning participants.</span>
  </p>
  
  <p class="note">
    On 11th Nov. we talk to <strong>Jonathan Conway</strong> from UK.
  </p>
  
  <p>
    <span style="font-size: 8pt; font-family: Arial;"><i><strong>Disclaimer:</strong></i></span><br /><span style="font-size: 8pt; font-family: Arial;"><i>The opinions expressed are those of Guy Naor and do not necessarily reflect those of <strong><a href="http://rubylearning.com/">www.RubyLearning.com</a></strong>.</i></span>
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
      #5: <a href="http://rubylearning.com/blog/2008/10/28/little-known-ways-to-ruby-mastery-by-chris-osullivan/">Chris O&#8217;Sullivan</a>
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Interviews" rel="tag">Interviews</a>, <a href="http://technorati.com/tag/Little+Known+Ways+to+Ruby+Mastery" rel="tag">Little Known Ways to Ruby Mastery</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Ruby+Beginners%26%238217%3B+Questions" rel="tag">Ruby Beginners&#8217; Questions</a>, <a href="http://technorati.com/tag/Guy+Naor" rel="tag">Guy Naor</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>
