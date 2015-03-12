---
author: Satish Talim
categories:
- Beginners
- Interview
- Ruby
- Ruby Masters
date: 2008-11-25
description:
- The Path to Ruby Mastery Interview Series by Ruby Masters, provides guidance to
  and answers questions confronting Ruby beginners from across the globe.
keywords:
- ruby for beginners,ruby beginners,ruby programming,ruby on rails blog,rails blog,rails
  tutorials,ruby beginners\' questions,little known ways to ruby mastery,ruby masters,interviews,Bruce
  Tate,ruby,the ruby programming language
layout: post
permalink: /2008/11/25/little-known-ways-to-ruby-mastery-by-bruce-tate/
tags:
- Bruce Tate
- interviews
- Little Known Ways to Ruby Mastery
- Ruby
- Ruby Beginners' Questions
- The Ruby Programming Language
title: Little Known Ways to Ruby Mastery by Bruce Tate
topsy_short_url:
- http://bit.ly/9KgAiX
---

<div>
  <h3>
    A weekly series from the Ruby Masters
  </h3>
  
  <p class="update">
    Welcome to the next installment of the weekly interview series on the <abbr title="RubyLearning">RL</abbr> blog &#8211; &#8220;<strong>Path to Ruby Mastery</strong>&#8221; &#8211; by top trainers and developers in the <strong>Ruby community</strong>, from across the globe. The interview series will provide insight and commentary from these notable Ruby trainers and developers, with the goal of facilitating and providing answers to the questions <strong>Ruby beginners</strong> face. We welcome your suggestions for interviewees and questions. Look for a new post every Tuesday!
  </p>
  
  <p>
    <span class="drop_cap">T</span>his week, we&#8217;re happy to have <strong>Bruce Tate</strong> from USA.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Welcome, Bruce and thanks for taking out time to share your thoughts. For the benefit of the readers, could you tell us something about your self?</span>
  </p>
  
  <p>
    <strong>Bruce>></strong> I am a kayaker, mountain biker, and father of two beautiful girls in Austin, Texas. I work as the CTO of WellGood, LLC, a company that specializes in building software that can make money and solve a social problem, like getting supplies to teachers or letting people give a donation to their favorite charity as a gift. I was a prolific author and speaker in the Java space. I moved to Ruby around four years ago, and haven&#8217;t looked back since.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Willian Molinari, Brazil>></strong> How should one go about learning the Ruby language? What material (books, eBooks, online tutorials etc.) would you recommend?</span>
  </p>
  
  <p>
    <strong>Bruce>></strong> The best way to learn Ruby is to use it. Pick a problem that&#8217;s easy enough for a first problem, but hard enough to put the language through it&#8217;s paces. If you can find a way to use it at work, that&#8217;s even better. I have my favorite set of books. The PickAxe book by Dave Thomas is a great book, and the new book by Matz called the Ruby Programming Language is brilliant. Several smaller resources are available too. I like Why&#8217;s Poignant Guide to Ruby, a quirky cartoon that walks through an exercise about an hour or two long. And through the first year of your development, you should work through a few Ruby Quiz problems. Some are easier and some are tougher, but the Pragmatic Press has them in book form and every problem is instructive.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong> Keith Brady, Australia>></strong> What are the pros and cons of Ruby that are being discussed in the development community and what is your opinion on that?</span>
  </p>
  
  <p>
    <strong>Bruce>></strong> Ruby is my language of choice because the syntax doesn&#8217;t get in my way, and the object model is pure. Since Ruby is highly dynamic, it&#8217;s easy for advanced developers to build their own languages to solve critical problems, and beginners get the benefits of using those programs. That means that there&#8217;s less to type, understand, and debug. For example, a programmer can open up a number class and add methods to convert to hours, minutes, days, and weeks. In code, you might see something like 10.days, which is much more readable than some unwieldy constant.
  </p>
  
  <p>
    There&#8217;s a down side to all of that freedom, too. Ruby is like a sharp knife. You can carve something beautiful with it quickly. You can cut your thumb off, too.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Dennis Theisen, Germany>></strong> Could you name three features of Ruby that you like the most, as compared to other languages? Why?</span>
  </p>
  
  <p>
    <strong>Bruce>></strong>
  </p>
  
  <ol>
    <li>
      I love the way that Ruby handles collections. As a coder, I deal with arrays and hashes. All of the abstractions for things like lists, queues, sets, bags, and the like are built into those two. That means I don&#8217;t spend much time thinking about precisely which collection I want to use, and I don&#8217;t box myself in once I pick a collection. If the collection needs a key, it&#8217;s a hash. If it doesn&#8217;t, it&#8217;s an array.
    </li>
    <li>
      I love code blocks. The whole implementation is easy. I can write a quick one-line code block or a multi-line block with friendly syntax for each. Code blocks are everywhere in Ruby. Whether it&#8217;s a quick hitting one liner ( 3.times {do_something_tedious} ) or managing transactions, for example: <pre><code>Bank.transaction do 
  my_account.debit(amount)
  your_account.credit(amount)
end</code></pre>
      
      <p>
        you can use code blocks anywhere that you need to pass code into a code.</li> 
        
        <li>
          I love the way new languages roll off your fingertips. When I&#8217;m using ActiveRecord, in an Employee class, I can say &#8220;belongs_to :department&#8221; and I&#8217;m done. I don&#8217;t need to break away from this code to build a mapping, and the mapping reads like a sentence. By making my code read like a sentence, I can reduce my total coding effort and maintenance time.
        </li></ol> 
        
        <p>
          <span style="color:#CC3333;"><strong>Jerry Anning, USA>></strong> What best practices are most important for a new Ruby programmer to learn and understand? </span>
        </p>
        
        <p>
          <strong>Bruce>></strong> Test, test, test. Very early on, learn a testing framework. Measure your code coverage, and learn to write your tests first. It will save you more time than you can possibly understand right now.
        </p>
        
        <p>
          <span style="color:#CC3333;"><strong>Jerry Anning, USA>></strong> Can you recommend things to study after learning Core Ruby, including different frameworks, gems and external libraries?</span>
        </p>
        
        <p>
          <strong>Bruce>></strong> Get to know rcov for coverage, and pick a testing framework that works for you. Get a good editor that you&#8217;re comfortable with. I use TextMate, but it&#8217;s infinitely better on OS x. If you&#8217;re on Windows, you will need something else. And after that, let your problems dictate where to go. Start with a problem, and then move on to which frameworks and gems you need. It&#8217;s not like PhP or Java where you&#8217;ll need 50 classic frameworks to start. Often, the core or Rails will take you a long way.
        </p>
        
        <p>
          <span style="color:#CC3333;"><strong>Satish Talim>></strong> Most beginners in Ruby, would like to contribute their time, skills and expertise to a project but invariably are unaware of where and how to do so. Could you suggest some?</span>
        </p>
        
        <p>
          <strong>Bruce>></strong> You can always find a project that needs better code coverage and start from there. It&#8217;s fairly easy to install rcov. That will point you to uncovered lines of code. You can then write some tests to cover those cases and submit them. Again, let your problem dictate the tools you want to test.
        </p>
        
        <p>
          <span style="color:#CC3333;"><strong>Keith Brady, Australia>></strong> What types of applications are currently being developed in Ruby and what changes do you foresee over the next year or two?</span>
        </p>
        
        <p>
          <strong>Bruce>></strong> I am a boring Rails developer. It works for me. I do see a huge jump in scalability over the next two years for a variety of reasons, including the emergence of solid virtual machines, great work on making things thread safe, and the excellent JRuby package which will let Ruby work on established Java platforms. Also, internationalization will enable better support for applications that span languages.
        </p>
        
        <p>
          <span style="color:#CC3333;"><strong>Victor Goff, USA>></strong> How do you see the market for Ruby Programmers in the work place, and do you see it as primarily tied to Rails and Web related work? Do you see trends in administration or other work? What&#8217;s the future for Ruby?</span>
        </p>
        
        <p>
          <strong>Bruce>></strong> It&#8217;s expanding rapidly. I&#8217;m not in the market, but there&#8217;s no shortage of consulting offers.
        </p>
        
        <p>
          <span style="color:#CC3333;"><strong>Michael Uplawski, Germany>></strong> According to you, what is a comfortable size of a Ruby/Rails-project? Why?</span</p> 
          
          <p>
            <strong>Bruce>></strong> You can do amazing things with very small teams. Rails gives you so much more leverage. My current projects use teams of 1-3 developers and 1 designer. I also work with a very good analyst, and that helps. But I try to work with very small teams of very good programmers. I find that&#8217;s about like a team of six to twelve Java programmers using the technologies I was using four years ago. (It&#8217;s probably better now, because Java is not standing still.)
          </p>
          
          <p>
            <span style="color:#CC3333;"><strong>Michael Uplawski, Germany>></strong> Having spent some years in the I.T. industry and coming to Ruby from a different background, how do I recognize Ruby&#8217;s limitations so as to suggest a different language in such cases?</span>
          </p>
          
          <p>
            <strong>Bruce>></strong> This is a great question. It&#8217;s easy to pick up a golden hammer and see every new problem as a nail. I tend to use Ruby on very complicated problems, because the language lets me express ideas with less clutter. I use Java for simpler problems that absolutely must scale beyond where I&#8217;m willing to take Ruby. I also use non-traditional approaches, like SQL scripts, simple spreadsheets, and editor macros for quick hitting problems where I might have written code before.
          </p>
          
          <p>
            <span style="color:#CC3333;"><strong>Dennis Theisen, Germany>></strong> Do you think Ruby is ready to be used in &#8220;Enterprise applications&#8221;? Kindly justify your answer.</span>
          </p>
          
          <p>
            <strong>Bruce>></strong> I&#8217;m a CTO. We&#8217;ve bet on Ruby. It&#8217;s been incredible for us in terms of productivity. We&#8217;ve never had a scaling problem we couldn&#8217;t solve, but we&#8217;re not E-bay yet, either.
          </p>
          
          <p>
            <span style="color:#CC3333;"><strong>Satish Talim>></strong> What can / should job candidates (for Ruby) do to distinguish themselves from their competition?<br /><strong>Note</strong>: The candidate has done his/her homework on the company that they are interviewing with. The candidate understands what they&#8217;re looking for, and the candidate is prepared to show them that he/she fits the bill, based on the candidate&#8217;s skills and experience. What else can the candidate do, to set themselves apart from other equally well-qualified and well-prepared candidates?</span>
          </p>
          
          <p>
            <strong>Bruce>></strong> Code with good people. Open Source is a good way to do that. There&#8217;s no substitute for coding in a productive environment.
          </p>
          
          <p>
            <span style="color:#CC3333;"><strong>Satish Talim>></strong> Do you have any other suggestions for these participants (would-be Ruby developers)?</span>
          </p>
          
          <p>
            <strong>Bruce>></strong> I can&#8217;t think of any.
          </p>
          
          <p>
            <span style="color:#CC3333;"><strong>Satish Talim>></strong> Thanks Bruce for sharing your views with the RubyLearning participants.</span>
          </p>
          
          <p class="note">
            On 2nd Dec. we talk to <strong>Ezra Zygmuntowicz</strong> from USA.
          </p>
          
          <p>
            <span style="font-size: 8pt; font-family: Arial;"><i><strong>Disclaimer:</strong></i></span><br /><span style="font-size: 8pt; font-family: Arial;"><i>The opinions expressed are those of Bruce Tate and do not necessarily reflect those of <strong><a href="http://rubylearning.com/">www.RubyLearning.com</a></strong>.</i></span>
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
          </ul></div> 
          
          <p>
            Technorati Tags: <a href="http://technorati.com/tag/Interviews" rel="tag">Interviews</a>, <a href="http://technorati.com/tag/Little+Known+Ways+to+Ruby+Mastery" rel="tag">Little Known Ways to Ruby Mastery</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Ruby+Beginners%26%238217%3B+Questions" rel="tag">Ruby Beginners&#8217; Questions</a>, <a href="http://technorati.com/tag/Bruce+Tate" rel="tag">Bruce Tate</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>
          </p>
