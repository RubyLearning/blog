---
title: 'David Black Interview: Talking to RubyLearning.com'
author: Satish Talim
date: "2007-08-18"
layout: post
permalink: /2007/08/18/david-black-interview-talking-to-rubylearningcom/
categories:
  - beginners
  - interview
  - rails
  - ruby
  - training
---
<div style="float: right; margin-left: 10px; margin-bottom: 10px;">
  <a href="http://www.rubylearning.com/images/david.jpg" title="David Black"><img src="http://www.rubylearning.com/images/david.jpg" alt="David Black" /></a>
</div>

<div>
  <p>
    <em>Today, I had the good fortune to talk to David Black the author of the very popular book &#8220;<a href="http://www.manning.com/black/">Ruby for Rails</a>&#8220;, on behalf of all the <a href="http://rubylearning.com/">RubyLearning.com</a> members. I have been recommending his book to one and all and if you have not read it yet, do buy yourself a copy.</em>
  </p>
  
  <p>
    <strong>Hello David, and welcome to RubyLearning.com. Why don&#8217;t we start with a little bit of your background?</strong>
  </p>
  
  <p>
    I&#8217;m a self-taught computer programmer, currently specializing in Ruby and Rails. My education includes an undergraduate double-major in German and History of Art, and a Ph.D. in Cinema Studies. I&#8217;m also a professionally-trained cellist.
  </p>
  
  <p>
    For thirteen years, I taught in the Department of Communication at Seton Hall University in New Jersey, USA. My curriculum was mainly media history and research. At the same time, I was getting more and more into computer programming, something that had been an interest of mine literally for decades.
  </p>
  
  <p>
    In the Fall of 2005, I was scheduled to start a one-year sabbatical from the university. By that time, I was deeply involved in all sorts of Ruby and Rails activities &#8211; including writing my first Ruby book, &#8220;Ruby for Rails&#8221;. I decided that instead of taking the research leave, I would resign from the university and pursue computer programming, writing, and training full-time. That&#8217;s what I&#8217;ve been doing for the past two years.
  </p>
  
  <p>
    I started using Ruby in 2000, right when the first edition of &#8220;Programming Ruby&#8221; (the Pickaxe book) came out. I&#8217;ve written two Ruby and/or Rails books (&#8220;Ruby for Rails&#8221; and &#8220;Rails Routing&#8221;), and I have my own consultancy, <a href="http://www.rubypal.com/">Ruby Power and Light, LLC</a>. I&#8217;m also one of the founding directors of <a href="http://www.rubycentral.org">Ruby Central, Inc.</a>, the parent organization of the annual International Ruby Conference (&#8220;RubyConf&#8221;) and the International Rails Conference and RailsConf Europe.
  </p>
  
  <p>
    <strong>What according to you is the best approach to learn the Ruby programming language?</strong>
  </p>
  
  <p>
    Same as with any language: write lots of code! I strongly recommend that people make heavy use of IRB, the interactive Ruby console. It&#8217;s great for learning how Ruby works. Of course, if you&#8217;re trying out something that&#8217;s more than a few lines long, you&#8217;ll probably want to put it in a file and run it.
  </p>
  
  <p>
    Once you&#8217;ve bootstrapped yourself into some understanding of the Ruby language, a good next step is to familiarize yourself with the unit testing framework, TestUnit. (I don&#8217;t talk about testing in &#8220;Ruby for Rails&#8221;, but as I explain in the preface, that&#8217;s because I wanted the book to explore certain things in depth, not because testing is a bad idea!)
  </p>
  
  <p>
    I&#8217;ve also learned a ton about Ruby by answering people&#8217;s questions on mailing lists and IRC channels. If I see a question and I don&#8217;t know the answer, I generally feel that as a Ruby programmer, I *should* know the answer &#8211; so I go figure it out, and then answer the question. And of course someone else might come back with a better answer, and then I learn even more.
  </p>
  
  <p>
    I also recommend letting Ruby talk to you. Don&#8217;t project your expectations onto Ruby. A great deal of the trouble I see people having with Ruby comes about because they can&#8217;t believe it&#8217;s as simple as it is. For example, there&#8217;s a simple rule that every time you see an instance variable (such as @var), that instance variable belongs to &#8220;self&#8221; (the default object) &#8211; whatever self may happen to be at that point. There are no exceptions to this. So the answer to the question, &#8220;What is this instance variable? Who can access it?&#8221; is always exactly the same: it belongs to <strong>self</strong>. Just figure out what self is, and you know what object governs that particular @var.
  </p>
  
  <p>
    <strong>Which areas in Ruby should a would-be Ruby programmer concentrate on?</strong>
  </p>
  
  <p>
    Speaking of &#8220;self&#8221;: I recommend looking very closely at self. Understanding self will help you understand a lot of what&#8217;s going on. Ruby is like a novel with a different narrator for each chapter: the role of self, or &#8220;I&#8221;, keeps changing, but there&#8217;s always an &#8220;I&#8221;. You should try to develop a feel for how the role of self gets handed around during execution.
  </p>
  
  <p>
    Much too much fuss is made over the complexity of Ruby&#8217;s class model, which is actually quite simple. It&#8217;s worth spending some time getting a grasp on it, so that you can understand how objects resolve method calls by searching through the classes and modules in their look-up paths.
  </p>
  
  <p>
    Iterators, blocks, and procs can be tricky (and some of their syntax and semantics is in flux as between Ruby 1.8 and Ruby 1.9/2.0), but they&#8217;re important and powerful and just plain cool! I&#8217;d recommend becoming as familiar as possible with how they work. When you see that there are at least four ways to create a Proc object, don&#8217;t despair: it doesn&#8217;t go on forever, and if you wonder whether it&#8217;s all a bit murky, you&#8217;re not the first. But you&#8217;ll soon pinpoint the key concepts: closures, iteration, capturing blocks in methods, etc.
  </p>
  
  <p>
    <strong>What do you think are the most exciting developments going on in Ruby right now?</strong>
  </p>
  
  <p>
    The new implementations (JRuby, IronRuby, Rubinius) are very exciting. As a long-time Ruby conference organizer (I co-organized RubyConf 2001, the first one), I&#8217;m also thrilled to see that regional conferences are flourishing. These events are really well produced and full of interesting content. It&#8217;s also very gratifying to go into bookstores and see an entire Ruby shelf. That&#8217;s something very new, from my archaic perspective!
  </p>
  
  <p>
    <strong>According to you, how important is it for a would-be Ruby programmer to know JRuby and / or IronRuby?</strong>
  </p>
  
  <p>
    Both of those implementations aim for compatibility with the standard Ruby distribution, so if you know Ruby, you presumably know JRuby and IronRuby. Of course each of them has a particular focus, in terms of interoperability and programming context. So interest will be guided by those concerns too.
  </p>
  
  <p>
    <strong>When do you think is the right time to start learning Rails?</strong>
  </p>
  
  <p>
    If you&#8217;re a Ruby programmer already, then any time you develop an interest in it. If you&#8217;re not, then I would recommend learning at least some Ruby first, or learning them together. That&#8217;s really why I wrote &#8220;Ruby for Rails&#8221;: to give support to people whose main goal is learning Rails, but who want to do it right. You can&#8217;t do Rails right without some Ruby expertise, but you don&#8217;t have to postpone learning Rails forever. After all, Rails applications are Ruby programs.
  </p>
  
  <p>
    <strong>On a final note: What do you perceive as the future of Ruby?</strong>
  </p>
  
  <p>
    I&#8217;m not clairvoyant &#8211; I don&#8217;t perceive the future <img src="http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif" alt=":-)" class="wp-smiley" /> The present is awfully exciting, with lots going on and a lot to do. It will certainly be exciting to see what the next &#8220;big thing&#8221; in Ruby turns out to be. Meanwhile I&#8217;m enjoying my work with Rails, and I hope both Ruby and Rails continue to flourish.
  </p>
  
  <p>
    <em>Thanks David for sharing your views with the RubyLearning.com members. I am confident that your insights would help all the would-be Ruby programmers.</em>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/David+Black" rel="tag">David Black</a>, <a href="http://technorati.com/tag/David+Black+Interview%3A+Talking+to+RubyLearning.com" rel="tag">David Black Interview: Talking to RubyLearning.com</a>, <a href="http://technorati.com/tag/Interviews" rel="tag">Interviews</a>, <a href="http://technorati.com/tag/IronRuby" rel="tag">IronRuby</a>, <a href="http://technorati.com/tag/JRuby" rel="tag">JRuby</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Ruby+on+Rails" rel="tag">Ruby on Rails</a>, <a href="http://technorati.com/tag/Ruby+Interviews" rel="tag">Ruby Interviews</a>, <a href="http://technorati.com/tag/Ruby+Training" rel="tag">Ruby Training</a>
