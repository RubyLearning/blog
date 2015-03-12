---
author: Satish Talim
categories:
- Interview
- Ruby
- Ruby Masters
date: 2008-11-18
description:
- The Path to Ruby Mastery Interview Series by Ruby Masters, provides guidance to
  and answers questions confronting Ruby beginners from across the globe.
keywords:
- ruby for beginners,ruby beginners,ruby programming,ruby on rails blog,rails blog,rails
  tutorials,ruby beginners\' questions,little known ways to ruby mastery,ruby masters,interviews,Ian
  Dees,ruby,the ruby programming language
layout: post
permalink: /2008/11/18/little-known-ways-to-ruby-mastery-by-ian-dees/
tags:
- Ian Dees
- interviews
- Little Known Ways to Ruby Mastery
- Ruby
- Ruby Beginners' Questions
- The Ruby Programming Language
title: Little Known Ways to Ruby Mastery by Ian Dees
---

<div>
  <h3>
    A weekly series from the Ruby Masters
  </h3>
  
  <p class="update">
    Welcome to the next installment of the weekly interview series on the <abbr title="RubyLearning">RL</abbr> blog &#8211; &#8220;<strong>Path to Ruby Mastery</strong>&#8221; &#8211; by top trainers and developers in the <strong>Ruby community</strong>, from across the globe. The interview series will provide insight and commentary from these notable Ruby trainers and developers, with the goal of facilitating and providing answers to the questions <strong>Ruby beginners</strong> face. We welcome your suggestions for interviewees and questions. Look for a new post every Tuesday!
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/iandees.jpg" alt="Ian Dees, USA" title="Ian Dees, USA" width="123" height="142" />
  </p>
  
  <p>
    <span class="drop_cap">T</span>his week, we&#8217;re happy to have <strong>Ian Dees</strong> from USA.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Welcome, Ian and thanks for taking out time to share your thoughts. For the benefit of the readers, could you tell us something about your self?</span>
  </p>
  
  <p>
    <strong>Ian>></strong> Hi. I&#8217;m a software developer working for a test equipment company near Portland, Oregon, USA. I started programming for fun in 1986, and for pay in 1996. Projects have ranged from assembly code running on bare metal, through embedded systems and desktop software, all the way up to high-level test code and Web applications. Outside the office, my obsessions include my beautifully chaotic family, bicycles, guitars, books, coffee, and cooking. I&#8217;ve written a book, &#8220;<a href="http://www.pragprog.com/titles/idgtr/scripted-gui-testing-with-ruby">Scripted GUI Testing with Ruby</a>,&#8221; published by the Pragmatic Programmers.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Willian Molinari, Brazil>></strong> How should one go about learning the Ruby language? What material (books, eBooks, online tutorials etc.) would you recommend?</span>
  </p>
  
  <p>
    <strong>Ian>></strong> The best way to learn Ruby is to write it. My first Ruby program was an entry in a programming contest. That code turned out clumsy, verbose, and non-idiomatic, but writing it taught me a lot of the quirks of the language.
  </p>
  
  <p>
    So I&#8217;d say work your way through a <a href="http://tryruby.hobix.com/">tutorial</a> or two, then look for a programming challenge to have fun with. Here are a few code challenge sites (some are focused on other languages, but there&#8217;s no reason you couldn&#8217;t solve them in Ruby as an exercise):
  </p>
  
  <ul>
    <li>
      <a href="http://perl.plover.com/qotw/">http://perl.plover.com/qotw/</a>
    </li>
    <li>
      <a href="http://codekata.pragprog.com/">http://codekata.pragprog.com/</a>
    </li>
    <li>
      <a href="http://www.devx.com/DevX/Door/17707">http://www.devx.com/DevX/Door/17707</a>
    </li>
  </ul>
  
  <p>
    As for reading material, _why&#8217;s <a href="http://poignantguide.net/ruby/">Poignant Guide to Ruby</a> is a great way to soak up the Ruby atmosphere. That plus the official <a href="http://www.ruby-doc.org/">Ruby reference docs</a> should get you off to a good start.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Jerry Anning, USA>></strong> Can you recommend things to study after learning Core Ruby, including different frameworks, gems and external libraries?</span>
  </p>
  
  <p>
    <strong>Ian>></strong> Tempted as I am to give a &#8220;Great Moments in Ruby History&#8221; spiel, I&#8217;d recommend seeing what libraries you end up depending on most in your own apps, and peeking behind the curtain to see how they tick.
  </p>
  
  <p>
    For example, we use the Camping library at work to drive a couple of status pages on our build server. I ended up cracking open the <a href="http://code.whytheluckystiff.net/svn/camping/trunk/lib/camping-unabridged.rb">unabridged version of the source</a> to diagnose a problem, and was rewarded with a crisp, thoroughly documented treat of metaprogramming.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Most beginners in Ruby, would like to contribute their time, skills and expertise to a project but invariably are unaware of where and how to do so. Could you suggest some?</span>
  </p>
  
  <p>
    <strong>Ian>></strong> Ruby has a way of leading people on a natural path to becoming contributors. First, you happen to use a library for a while, and maybe ask a question on the mailing list. Then, you notice a bug and submit a ticket. In the meantime, you find a way to fix the problem on your own machine. You submit a patch. Next thing you know, you have commit access, are listed as a core contributor, and are answering mailing list traffic daily on three different projects.
  </p>
  
  <p>
    The best part is that this all seems to happen on its own, just as a byproduct of using and loving Ruby. That said, if you&#8217;re looking for something specific, the <a href="http://rubini.us/contribute">Rubinius project</a> is actively seeking contributors of varying skill levels.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Keith Brady, Australia>></strong> What are the pros and cons of Ruby that are being discussed in the development community and what is your opinion on that?</span>
  </p>
  
  <p>
    <strong>Ian>></strong> Matz has said that his goal in creating Ruby was to optimize for programmer happiness. The language&#8217;s advantages and disadvantages stem from that decision. Ruby has an Algol-like syntax for familiarity, dynamic typing for &#8220;sketchability,&#8221; a little bit of Lisp&#8217;s and Smalltalk&#8217;s power so that enterprising coders can extend the language, and a few of Perl&#8217;s shortcuts.
  </p>
  
  <p>
    On the downside, optimizing for the programmer has meant that interpreter implementors have traditionally had to make performance sacrifices (though see the obsessive effort that has gone into making Ruby 1.9 and JRuby faster). And Ruby doesn&#8217;t support quite the level of on-the-fly modification of programs that, say, Smalltalk and Lisp do.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Willian Molinari, Brazil>></strong> What has been your biggest challenge while working with Ruby?</span>
  </p>
  
  <p>
    <strong>Ian>></strong> Limits, both mine and Ruby&#8217;s. For me, meta-programming &#8212; programs writing programs &#8212; introduces tons of new things to keep track of. When you&#8217;re handing off code that&#8217;s not going to run until much later on, in a completely different part of your program (or someone else&#8217;s program!), will it have everything it needs to execute? I&#8217;m less than a week away from going back to grad school to learn theory of computation, so I can keep some of this stuff straight.
  </p>
  
  <p>
    As for Ruby&#8217;s limits&#8230; it seems like it&#8217;s human nature to run straight to the end of what any particular language feature (e.g., blocks) can do, and almost immediately bump our heads against the edge cases. There are a lot of coding shortcuts we could take more safely if we had something like Lisp&#8217;s macros. Keep an eye on the work <a href="http://rewrite.rubyforge.org/">Reg Braithwaite</a> has been doing on this subject.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> What can / should job candidates (for Ruby) do to distinguish themselves from their competition?<br /><strong>Note</strong>: The candidate has done his/her homework on the company that they are interviewing with. The candidate understands what they&#8217;re looking for, and the candidate is prepared to show them that he/she fits the bill, based on the candidate&#8217;s skills and experience. What else can the candidate do, to set themselves apart from other equally well-qualified and well-prepared candidates?</span>
  </p>
  
  <p>
    <strong>Ian>></strong> My current job wasn&#8217;t specifically a Ruby job when I interviewed for it, but here&#8217;s a principle that transcends languages:
  </p>
  
  <p>
    Have a portfolio. Work on some open-source projects, and show your prospective employers the contributions you&#8217;ve made. (Hopefully, you&#8217;ve found a project that&#8217;s meaningful to you, speaks to your passions, and isn&#8217;t just resume filler.) If that isn&#8217;t an option, sketch out screen mockups of the closed-source apps you&#8217;ve built. For each one, talk about how it challenged you and what it taught you.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Do you have any other suggestions for these participants (would-be Ruby developers)?</span>
  </p>
  
  <p>
    <strong>Ian>></strong> Aim for MINASWAN (Matz Is Nice And So We Are Nice).
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Thanks Ian for sharing your views with the RubyLearning participants.</span>
  </p>
  
  <p class="note">
    On 25th Nov. we talk to <strong>Bruce Tate</strong> from USA.
  </p>
  
  <p>
    <span style="font-size: 8pt; font-family: Arial;"><i><strong>Disclaimer:</strong></i></span><br /><span style="font-size: 8pt; font-family: Arial;"><i>The opinions expressed are those of Ian Dees and do not necessarily reflect those of <strong><a href="http://rubylearning.com/">www.RubyLearning.com</a></strong>.</i></span>
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
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Interviews" rel="tag">Interviews</a>, <a href="http://technorati.com/tag/Little+Known+Ways+to+Ruby+Mastery" rel="tag">Little Known Ways to Ruby Mastery</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Ruby+Beginners%26%238217%3B+Questions" rel="tag">Ruby Beginners&#8217; Questions</a>, <a href="http://technorati.com/tag/Ian+Dees" rel="tag">Ian Dees</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>
