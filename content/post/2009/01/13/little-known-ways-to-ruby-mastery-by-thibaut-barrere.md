---
title: Little Known Ways to Ruby Mastery by Thibaut Barrere
author: Satish Talim
date: 2009-01-13
layout: post
permalink: /2009/01/13/little-known-ways-to-ruby-mastery-by-thibaut-barrere/
keywords:
  - "ruby for beginners,ruby beginners,ruby programming,ruby on rails blog,rails blog,rails tutorials,ruby beginners' questions,little known ways to ruby mastery,ruby masters,interviews,Thibaut Barrere,ruby,the ruby programming language"
description:
  - The Path to Ruby Mastery Interview Series by Ruby Masters, provides guidance to and answers questions confronting Ruby beginners from across the globe.
categories:
  - Beginners
  - Interview
  - Ruby
  - Ruby Masters
---
<div>
  <h3>
    A weekly series from the Ruby Masters
  </h3>
  
  <p class="update">
    Welcome to the next installment of the weekly interview series on the <abbr title="RubyLearning">RL</abbr> blog &#8211; &#8220;<strong>Path to Ruby Mastery</strong>&#8221; &#8211; by top trainers and developers in the <strong>Ruby community</strong>, from across the globe. The interview series will provide insight and commentary from these notable Ruby trainers and developers, with the goal of facilitating and providing answers to the questions <strong>Ruby beginners</strong> face.
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/thibaut.jpg" alt="Thibaut Barrere, France" title="Thibaut Barrere, France" width="116" height="132" />
  </p>
  
  <p>
    <span class="drop_cap">T</span>his week, we&#8217;re happy to have <strong>Thibaut Barrere</strong> from France.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Welcome, Thibaut and thanks for taking out time to share your thoughts. For the benefit of the readers, could you tell us something about your self?</span>
  </p>
  
  <p>
    <strong>Thibaut>></strong> Hello! My name is Thibaut Barrere. I&#8217;m 31 years old, a husband and dad who loves to create useful things (either in Ruby or not). I became a freelancer in 2005, after working for software editors and consulting companies.
  </p>
  
  <p>
    I do my best to share useful thoughts and tools on the <a href="http://evolvingworker.com/">Evolving Worker</a> blog. I also write <a href="http://blog.logeek.fr/2008/3/31/data-visualization-with-ruby-and-rmagick-where-are-those-bikes">Ruby tutorials on my programming blog</a>.
  </p>
  
  <p>
    I pretty much falled in love with programming in 1984 (<a href="http://en.wikipedia.org/wiki/Oric#ric-1">this was my first machine</a>). Since then I used various languages and platforms (Pascal, C++, Java, .Net&#8230;). I discovered Ruby in 2004 as I needed to parse a large amount of logs on a .Net application to understand a bug. I was amazed by how much could be achieved without knowing much of the language. Gradually I realised that Ruby and Rake were an efficient way to create easy to maintain build scripts. I got addicted to Ruby and it&#8217;s now my everyday language for most tasks.
  </p>
  
  <p>
    I started using Rails in 2005 and it got me deeper into Ruby. Since then I&#8217;ve been using Ruby on different kinds of projects, including the <a href="http://www.villanao.co.uk/">plumbing behind a holidays rentals aggregator</a>, automation and continuous integration, logs analysis for measuring speed or business performance, CMS and blogs, <a href="http://blog.logeek.fr/2008/1/19/a-beginner-s-guide-to-datawarehouse">datawarehousing</a>, <a href="http://evolvingworker.com/2008/2/28/using-mind-mapping-data-to-drive-your-software-application">data-driven applications</a>, reporting and more regular web applications with Rails and now Merb.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Willian Molinari, Brazil>></strong> How should one go about learning the Ruby language? What material (books, eBooks, online tutorials etc.) would you recommend?</span>
  </p>
  
  <p>
    <strong>Thibaut>></strong> Here are a few things that I find useful:
  </p>
  
  <ul>
    <li>
      Fire up irb each time you wonder if Ruby does this or that &#8211; just give it a try,
    </li>
    <li>
      Learn by writing your own unit-tests against the standard library &#8211; a pretty good way to understand how things work,
    </li>
    <li>
      Read existing code (eg: <a href="http://github.com/aeden/activewarehouse/tree/master/">ACTIVEWAREHOUSE-ETL</a>, <a href="http://facets.rubyforge.org/">RUBY FACETS</a>, <a href="http://github.com/thoughtworks/cruisecontrol.rb/tree/master">CRUISECONTROL.RB</a>) to see how projects are structured and which idioms are used,
    </li>
    <li>
      Have a look at <a href="http://peepcode.com/">PEEPCODE</a> and pick a screen-cast or a pdf randomly once in a while,
    </li>
    <li>
      Finally, read <a href="http://www.amazon.com/Ruby-Programming-Language-David-Flanagan/dp/0596516177">THE RUBY PROGRAMMING LANGUAGE</a> by David Flanagan and Yukihiro Matsumoto. It&#8217;s dense yet amazing.
    </li>
  </ul>
  
  <p>
    One thing that really surprised me about Ruby is that you can use it for real without knowing much of it, since the very beginning &#8211; and learn as you go.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Keith Brady, Australia>></strong> What are the pros and cons of Ruby that are being discussed in the development community and what is your opinion on that?</span>
  </p>
  
  <p>
    <strong>Thibaut>></strong> Many discussions occur around the pros and cons of X vs. Y. Part of these discussions is related to fear &#8211; will I be blamed for making the &#8220;wrong&#8221; choice ?
  </p>
  
  <p>
    Instead of trying to compare languages or tools, I prefer to &#8220;budget&#8221; the corresponding time into trying new things out, and see what works for me or my team (eg: spend a couple of hours or one day on Silverlight, IronRuby, CouchDB, Cucumber/Webrat, Merb or Ramaze and see if it proves useful, rinse, repeat).
  </p>
  
  <p>
    That said, the cons I often meet are:
  </p>
  
  <ul>
    <li>
      difficult to read for people coming from a static background: people used to Java, C#, C++ sometimes seem to have a hard-time starting,
    </li>
    <li>
      part of the standard library has issues, like downloading files with net/http: when I was faced with these issues, I used wget/curl instead to do the job instead,
    </li>
    <li>
      Ruby is slow: for what I&#8217;ve done, it has always been fast enough, or easy to scale out / refactor if needed. As well I remember C# was considered slow in 2001; I never met an issue that could not be worked out somehow, either.
    </li>
  </ul>
  
  <p>
    The pros are:
  </p>
  
  <ul>
    <li>
      pleasure: it feels good once you start using it
    </li>
    <li>
      ability to innovate: quite often when having an idea, you try it out and it works
    </li>
    <li>
      a lot of reusable stuff already exists so you can focus on writing new, useful code
    </li>
  </ul>
  
  <p>
    <span style="color:#CC3333;"><strong>Dennis Theisen, Germany>></strong> Could you name three features of Ruby that you like the most, as compared to other languages? Why?</span>
  </p>
  
  <p>
    <strong>Thibaut>></strong> One of the things I like most is the overall simplicity of the core classes. Most people coming from Java and C# are surprised by the fact that there is only Hash and Array (and Enumerable). As a result it&#8217;s easier for newcomers to get started.
  </p>
  
  <p>
    Speaking of language features, I really like blocks. I believe they are the reason why we don&#8217;t have to build specialized containers that often in Ruby. I also like opened classes and duck typing, because these two features make testing and hacking around a lot easier.
  </p>
  
  <p>
    An interesting consequence of the simplicity and duck typing is that in Ruby &#8220;actual reuse&#8221; is quite common, whereas in Java and C# I mostly experienced &#8220;reusable components&#8221; that were quite difficult to reuse in reality.
  </p>
  
  <p>
    Finally, I love the fact that Ruby code tends to be concise and that it creates a shorter path between ideas and their implementation.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Willian Molinari, Brazil>></strong> What has been your biggest challenge while working with Ruby?</span>
  </p>
  
  <p>
    <strong>Thibaut>></strong> Sysadmin! I&#8217;m ok with it but it&#8217;s really Rails that got me into that. Each time I have the impression that I somehow surpassed myself, a bit like if you&#8217;re a child driving a car.
  </p>
  
  <p>
    It&#8217;s exciting more than frightening though <img src="http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Jerry Anning, USA>></strong> What best practices are most important for a new Ruby programmer to learn and understand?</span>
  </p>
  
  <p>
    <strong>Thibaut>></strong> I&#8217;d focus on these ones:
  </p>
  
  <ul>
    <li>
      simplicity &#8211; ask yourself if the feature or piece of code is absolutely necessary, and write it in a way a beginner could understand. Remember that no code is faster and easier to maintain than any code,
    </li>
    <li>
      source control &#8211; even if you work alone, even for a small &#8220;labs&#8221; type of applications, use SVN, Git or whatever you feel comfortable with,
    </li>
    <li>
      unit-testing &#8211; learn to use Test::Unit, RSpec, mocks &#8211; the most horrible bugs I&#8217;ve tracked down could have all been avoided with a one-line unit-test,
    </li>
    <li>
      continuous integration &#8211; because it&#8217;s like having an tireless assistant that can do a lot of repetitive stuff for you!
    </li>
  </ul>
  
  <p>
    <span style="color:#CC3333;"><strong>Victor Goff, USA>></strong> How do you see the market for Ruby Programmers in the work place, and do you see it as primarily tied to Rails and Web related work? Do you see trends in administration or other work? Whatâ€™s the future for Ruby?</span>
  </p>
  
  <p>
    <strong>Thibaut>></strong> From where I stand (I&#8217;m in France) and from what I&#8217;m doing now, the Ruby market doesn&#8217;t seem to be only tied to Rails and Web related work.
  </p>
  
  <p>
    Ruby can be used in many fashions outside the web. For instance, a lot of companies have a need to analyze and understand their data: I&#8217;m using Ruby for a lot of different things there (statistics, reporting, data exchange, ETL&#8230;). The more we go, the more websites become front-ends on top of something that is more complicated. Some of my customers said they had no issue finding purely web Rails programmers, but that it was difficult to find people who have a good understanding of data processing, back-end etc.
  </p>
  
  <p>
    On the future of Ruby: it&#8217;s very interesting to see more platforms adopting Ruby (I&#8217;m thinking about .Net and Java for instance). I really believe there is an opportunity for Rubyists here.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Dennis Theisen, Germany>></strong> Do you think Ruby is ready to be used in &#8220;Enterprise applications&#8221;? Kindly justify your answer.</span>
  </p>
  
  <p>
    <strong>Thibaut>></strong> There is as many definition of &#8220;enterprise applications&#8221; as there are companies, unfortunately. In some companies I work for, Ruby is pretty good at gluing things together, grabbing out a CSV from there, cleaning-it up, pushing it to another application (<a href="http://www.pragprog.com/titles/fr_eir/enterprise-integration-with-ruby">ENTERPRISE INTEGRATION WITH RUBY</a> is an interesting read on that topic). In others, Ruby is pretty good at creating large and reliable systems, iteratively. In a world-wide situation where we need to create more with less, I believe Ruby has a lot of value for Enterprise applications, in a pragmatic way.
  </p>
  
  <p>
    So yes, Ruby is ready to create useful things for the enterprise (and has already been for a long time).
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> What can / should job candidates (for Ruby) do to distinguish themselves from their competition?<br /><strong>Note</strong>: The candidate has done his/her homework on the company that they are interviewing with. The candidate understands what they&#8217;re looking for, and the candidate is prepared to show them that he/she fits the bill, based on the candidate&#8217;s skills and experience. What else can the candidate do, to set themselves apart from other equally well-qualified and well-prepared candidates?</span>
  </p>
  
  <p>
    <strong>Thibaut>></strong> Many coders are eager to propose solutions as soon as they&#8217;ve heard of a topic. A skill that is often missing (and I blame myself too sometimes) is listening! An efficient way to understand the user needs and a rare quality.
  </p>
  
  <p>
    I also care about finding people who are willing to reuse existing stuff instead of rolling their own, whenever possible.
  </p>
  
  <p>
    Oh yeah and people who have respect for their team-mates, too.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Do you have any other suggestions for these participants (would-be Ruby developers)?</span>
  </p>
  
  <p>
    <strong>Thibaut>></strong> My first suggestion would be to focus your energy on creating useful code and building things instead of arguing with others whether Ruby is a good choice or not.
  </p>
  
  <p>
    My second suggestion would be to pick up a simple idea you have, something that would be useful to you first and to implement it. Real artists ship!
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Thanks Thibaut for sharing your views with the RubyLearning participants.</span>
  </p>
  
  <p class="note">
    On 20th Jan. we talk to <strong>Ryan Bates</strong> from USA.
  </p>
  
  <p>
    <span style="font-size: 8pt; font-family: Arial;"><i><strong>Disclaimer:</strong></i></span><br /><span style="font-size: 8pt; font-family: Arial;"><i>The opinions expressed are those of Thibaut Barrere and do not necessarily reflect those of <strong><a href="http://rubylearning.com/">www.RubyLearning.com</a></strong>.</i></span>
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
    <li>
      #16: <a href="http://rubylearning.com/blog/2009/01/06/little-known-ways-to-ruby-mastery-by-josh-susser/">Josh Susser</a>
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Interviews" rel="tag">Interviews</a>, <a href="http://technorati.com/tag/Little+Known+Ways+to+Ruby+Mastery" rel="tag">Little Known Ways to Ruby Mastery</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Ruby+Beginners%26%238217%3B+Questions" rel="tag">Ruby Beginners&#8217; Questions</a>, <a href="http://technorati.com/tag/Thibaut+Barrere" rel="tag">Thibaut Barrere</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>
