---
title: Little Known Ways to Ruby Mastery by Ryan Bates
author: Satish Talim
date: 2009-01-20
layout: post
permalink: /2009/01/20/little-known-ways-to-ruby-mastery-by-ryan-bates/
tinucleatus@gmail.com:
  - tinucleatus
keywords:
  - "ruby for beginners,ruby beginners,ruby programming,ruby on rails blog,rails blog,rails tutorials,ruby beginners' questions,little known ways to ruby mastery,ruby masters,interviews,Ryan Bates,ruby,the ruby programming language"
description:
  - The Path to Ruby Mastery Interview Series by Ruby Masters, provides guidance to and answers questions confronting Ruby beginners from across the globe.
categories:
  - Beginners
  - Interview
  - Ruby
  - Ruby Masters
tags:
  - interviews
  - Little Known Ways to Ruby Mastery
  - Ruby
  - "Ruby Beginners' Questions"
  - Ryan Bates
  - The Ruby Programming Language
---
<div>
  <h3>
    A weekly series from the Ruby Masters
  </h3>
  
  <p class="update">
    Welcome to the <b>last</b> installment of the weekly interview series on the <abbr title="RubyLearning">RL</abbr> blog &#8211; &#8220;<strong>Path to Ruby Mastery</strong>&#8221; &#8211; by top trainers and developers in the <strong>Ruby community</strong>, from across the globe. The interview series will provide insight and commentary from these notable Ruby trainers and developers, with the goal of facilitating and providing answers to the questions <strong>Ruby beginners</strong> face.
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/ryan_bates.jpg" alt="Ryan Bates, USA" title="Ryan Bates, USA" width="125" height="142" />
  </p>
  
  <p>
    <span class="drop_cap">T</span>his week, we&#8217;re happy to have <strong>Ryan Bates</strong> from USA.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Welcome, Ryan and thanks for taking out time to share your thoughts. For the benefit of the readers, could you tell us something about your self?</span>
  </p>
  
  <p>
    <strong>Ryan>></strong> I started toying around with static HTML around 1996. A few years later I created a website for my father&#8217;s company using this little-known scripting language called WebDNA. As the site grew, I ported it over to PHP, and then later to Rails. Needless to say, Rails has been by far the most pleasant to work with.
  </p>
  
  <p>
    I enjoy teaching, partly because I get to learn along with whoever I&#8217;m helping by researching topics I might not have otherwise. While beginning with Rails, I started answering questions on <a href="http://railsforum.com/">railsforum.com</a>. Later I started <a href="http://railscasts.com/">Railscasts</a>, the free Ruby on Rails screencast series. I&#8217;m also working with the <a href="http://www.pragprog.com/">Pragmatic Programmers</a> on a couple screencast series: <a href="http://www.pragprog.com/screencasts/v-rbar/everyday-active-record">Everyday Active Record</a> and <a href="">Mastering Rails Forms</a>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Willian Molinari, Brazil>></strong> How should one go about learning the Ruby language? What material (books, eBooks, online tutorials etc.) would you recommend?</span>
  </p>
  
  <p>
    <strong>Ryan>></strong> It depends on what your past experience is. If you are very new to programming, I recommend reading <a href="http://www.amazon.com/Learn-Program-Pragmatic-Programmers-Chris/dp/0976694042/">Learn to Program</a>. Next up the tier is <a href="http://www.amazon.com/Beginning-Ruby-Novice-Professional/dp/1590597664/">Beginning Ruby: From Novice to Professional</a>. And then there&#8217;s the classic <a href="http://www.amazon.com/Programming-Ruby-Pragmatic-Programmers-Second/dp/0974514055/">Programming Ruby</a> (also known as the Pickaxe book).
  </p>
  
  <p>
    You may also want to <a href="http://tryruby.hobix.com/">Try Ruby!</a>, where you can run Ruby commands interactively in your browser. If you enjoy problem solving, check out <a href="http://rubyquiz.com/">Ruby Quiz</a> and a recent project of mine called <a href="http://github.com/ryanb/ruby-warrior/tree/master">Ruby Warrior</a> (still in early development).
  </p>
  
  <p>
    Finally, don&#8217;t only read books and work through examples. Find a real world problem, and use Ruby to solve it. Ask questions to the community if you can&#8217;t find the solution on your own.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Dennis Theisen, Germany>></strong> Could you name three features of Ruby that you like the most, as compared to other languages? Why?</span>
  </p>
  
  <p>
    <strong>Ryan>></strong> Ruby has spoiled me. Since learning it, I&#8217;ve found it much harder to work in other languages. These are the primary culprits.
  </p>
  
  <ul>
    <li>
      Blocks. They make iterations a breeze and so much more!
    </li>
    <li>
      Everything&#8217;s an object. Being able to call methods directly on integers, strings, arrays, etc. greatly simplifies the method interfaces.
    </li>
    <li>
      Metaprogramming. Injecting behavior at runtime opens up so many possibilities.
    </li>
  </ul>
  
  <p>
    <span style="color:#CC3333;"><strong>Jerry Anning, USA>></strong> Can you recommend things to study after learning Core Ruby, including different frameworks, gems and external libraries?</span>
  </p>
  
  <p>
    <strong>Ryan>></strong> There&#8217;s obviously Rails which I recommend every Ruby programmer try, even if you aren&#8217;t into web development. It handles Ruby in a different way (both good and bad) than what you see in many other projects. Also, go through the various methods in Active Support and <a href="http://github.com/sam/extlib/tree/master">extlib</a>. Doing so will make reading other projects that use these easier, and may improve the code you write.
  </p>
  
  <p>
    Also, if you haven&#8217;t already, I highly recommend signing up to <a href="http://github.com/">GitHub</a>. It has made a huge impact on improving myself as a programmer. Get involved with other programmers, read their code, and share your own code.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Jerry Anning, USA>></strong> What best practices are most important for a new Ruby programmer to learn and understand?</span>
  </p>
  
  <p>
    <strong>Ryan>></strong> There are three best practices which have made a world of difference for me: testing, refactoring, and naming.
  </p>
  
  <p>
    It took me a long time to grasp automated testing. The best advice I can give is: don&#8217;t give up on it too soon. Start with a project that is easy to test (maybe the models in a simple Rails app). Once you establish a testing rhythm it gets easier, and the payoff is well worth it.
  </p>
  
  <p>
    One of my favorite things about Ruby is how natural it feels to refactor. If you don&#8217;t know what refactoring is, I recommend reading <a href="http://www.amazon.com/Refactoring-Improving-Existing-Addison-Wesley-Technology/dp/0201485672/">Martin Fowler&#8217;s book</a> on the subject. It&#8217;s not in Ruby, but the concepts he teaches still apply. Also keep an eye out for the <a href="http://www.amazon.com/Refactoring-Ruby-Addison-Wesley-Professional/dp/0321603508/">Ruby edition</a> of this book.
  </p>
  
  <p>
    Finally, learning how to give proper names to variables, methods, and classes will help make your code much more readable. Find concise yet descriptive names and stay consistent with them across your application. This does wonders towards improving the readability of the code.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Victor Goff, USA>></strong> How do you see the market for Ruby Programmers in the work place, and do you see it as primarily tied to Rails and Web related work? Do you see trends in administration or other work? What&#8217;s the future for Ruby? </span>
  </p>
  
  <p>
    <strong>Ryan>></strong> I think web applications play a very significant role in the future, not only in Ruby, but also in our society. Every day it seems we are moving away from the desktop and more into the cloud. But the buck doesn&#8217;t stop at Rails. I suspect Ruby will far outlive Rails in the web development world as we see other innovative Ruby frameworks come into play. Overall, I think Ruby has a very bright future in the work place.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Michael Uplawski, Germany>></strong> According to you, what is a comfortable size of a Ruby/Rails-project? Why?</span>
  </p>
  
  <p>
    <strong>Ryan>></strong> I find Rails scales very well for a wide range of project sizes. I&#8217;ve worked with apps ranging from 3 models to 100 models and it has handled both great. The most comfortable size is probably somewhere around 10-40 models.
  </p>
  
  <p>
    Where Rails is not as applicable are the two extremes. If you&#8217;re app is very small (only a few pages, or mostly static content), there are other languages and frameworks which are lighter weight and easier to deploy. I don&#8217;t have much experience with gigantic enterprise apps, but I imagine there&#8217;s a limit you could reach where Rails isn&#8217;t as practical in how it organizes things. As Rails improves (especially with Rails 3), it will become more and more applicable to these other types of projects.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Thanks Ryan for sharing your views with the RubyLearning participants.</span>
  </p>
  
  <p>
    <span style="font-size: 8pt; font-family: Arial;"><i><strong>Disclaimer:</strong></i></span><br /><span style="font-size: 8pt; font-family: Arial;"><i>The opinions expressed are those of Ryan Bates and do not necessarily reflect those of <strong><a href="http://rubylearning.com/">www.RubyLearning.com</a></strong>.</i></span>
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
    <li>
      #17: <a href="http://rubylearning.com/blog/2009/01/13/little-known-ways-to-ruby-mastery-by-thibaut-barrere/">Thibaut Barrere</a>
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Interviews" rel="tag">Interviews</a>, <a href="http://technorati.com/tag/Little+Known+Ways+to+Ruby+Mastery" rel="tag">Little Known Ways to Ruby Mastery</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Ruby+Beginners%26%238217%3B+Questions" rel="tag">Ruby Beginners&#8217; Questions</a>, <a href="http://technorati.com/tag/Ryan+Bates" rel="tag">Ryan Bates</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>
