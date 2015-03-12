---
author: Satish Talim
categories:
- Ruby
date: 2008-12-23
description:
- The Path to Ruby Mastery Interview Series by Ruby Masters, provides guidance to
  and answers questions confronting Ruby beginners from across the globe.
keywords:
- ruby for beginners,ruby beginners,ruby programming,ruby on rails blog,rails blog,rails
  tutorials,ruby beginners' questions,little known ways to ruby mastery,ruby masters,interviews,Yehuda
  Katz,ruby,the ruby programming language
layout: post
permalink: /2008/12/23/little-known-ways-to-ruby-mastery-by-yehuda-katz/
tags:
- interviews
- Little Known Ways to Ruby Mastery
- Merb
- Ruby
- Ruby Beginners' Questions
- The Ruby Programming Language
- Yehuda Katz
title: Little Known Ways to Ruby Mastery by Yehuda Katz
---

<div>
  <h3>
    A weekly series from the Ruby Masters
  </h3>
  
  <p class="update">
    Welcome to the next installment of the weekly interview series on the <abbr title="RubyLearning">RL</abbr> blog &#8211; &#8220;<strong>Path to Ruby Mastery</strong>&#8221; &#8211; by top trainers and developers in the <strong>Ruby community</strong>, from across the globe. The interview series will provide insight and commentary from these notable Ruby trainers and developers, with the goal of facilitating and providing answers to the questions <strong>Ruby beginners</strong> face. We welcome your suggestions for interviewees and questions. Look for a new post every Tuesday!
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/YehudaKatz.jpg" alt="Yehuda Katz, USA" title="Yehuda Katz, USA" width="125" height="107" />
  </p>
  
  <p>
    <span class="drop_cap">T</span>his week, we&#8217;re happy to have <strong>Yehuda Katz</strong> from USA.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Welcome, Yehuda and thanks for taking out time to share your thoughts. For the benefit of the readers, could you tell us something about your self?</span>
  </p>
  
  <p>
    <strong>Yehuda>></strong> I&#8217;m the current maintainer of the Merb project, and also work on the jQuery and DataMapper projects. Together, Merb, DataMapper, and jQuery are a killer stack that really ramps up productivity. I was an Accounting major in college, and got involved with Ruby in 2005, in the pre-1.0 days of Ruby on Rails. I love Ruby and the community around it, and believe that the future is bright for the language. I currently work for Engine Yard on the Merb project.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Keith Brady, Australia>></strong> What are the pros and cons of Ruby that are being discussed in the development community and what is your opinion on that?</span>
  </p>
  
  <p>
    <strong>Yehuda>></strong> A lot of people have talked about Ruby as too slow to really be viable. I debunked that in my keynote at MerbCamp. Because Rubyists are so industrious, most of the critical path of Ruby applications have been optimized in C (with servers like Thin and Ebb and bindings to XML libraries like LibXML). People are also concerned about the development process of the Standard Ruby. On the bright side, the RubySpec project has created a runnable test suite for what Ruby is, and the alternative implementations (Rubinius and JRuby) are pushing the language forward.
  </p>
  
  <p>
    What&#8217;s great about Ruby is how quickly it exposes new developers to advanced programming techniques, like lambdas. You can&#8217;t get past simple iterations in Ruby before being exposed to lambdas, and many methods in common frameworks accept blocks (one of Ruby&#8217;s lambdas). Additionally, Ruby&#8217;s mutability makes it very easy to implement ceremony-less extensions to the language that make building frameworks like Rails or Merb simple and easy to use. Compare Rails or Merb with CakePHP or Struts if you want to see what I mean.
  </p>
  
  <p>
    Finally, something that isn&#8217;t really related to the language itself is Rails&#8217; strong emphasis on the 80/20 rule and convention over configuration. While Merb tries to go even further by making it possible to opt out of the conventions more granularly, the basic idea is fairly permeated in the Ruby community. It&#8217;s very difficult to make a Ruby library popular if it requires out-of-the-box configuration and does not attempt to provide a certain amount of common defaults.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Willian Molinari, Brazil>></strong> What has been your biggest challenge while working with Ruby?</span>
  </p>
  
  <p>
    <strong>Yehuda>></strong> I&#8217;d say the biggest challenge of working with Ruby is how dynamic the language is. While it makes it possible to create really powerful, simple language extensions (and thus makes Rails or Merb possible), those same features allow Ruby libraries to hide complexity and changes that aren&#8217;t easy to track down. The popular alias_method_chain feature, for instance, combined with metaprogramming creates methods that run in your application but that you can&#8217;t easily look at in source. In fact, it can sometimes be nearly impossible to figure out where all the pieces even come from.
  </p>
  
  <p>
    That&#8217;s the reason for the Merb rule against alias_method_chain, but you can&#8217;t really solve this problem without making Ruby significantly less powerful. It&#8217;s important for Ruby programmers to define clear APIs for libraries that they release, and try to avoid opaque magic where possible. Where not possible, library developers should clearly document exactly what they&#8217;re doing, so people trying to debug those libraries can understand the underlying codebase.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Most beginners in Ruby, would like to contribute their time, skills and expertise to a project but invariably are unaware of where and how to do so. Could you suggest some?</span>
  </p>
  
  <p>
    <strong>Yehuda>></strong> <strong>Merb</strong> of course! While I may be biased, the Merb project has a simple enough codebase (at around 6,000 lines for the core framework) to take a look at some outstanding tickets and dive in quickly. It&#8217;s also a relatively popular framework, so contributions you make could start helping developers very quickly. You can get information on <a href="http://wiki.merbivore.com/contribute/start">how to get started contributing to Merb</a>. You might also dive into other edgy projects like DataMapper or YARD. Both could use some love, but have the potential to really be game-changers to the Ruby ecosystem, so getting involved now could be a great way to get in on the ground floor. The only thing I&#8217;d add is that when getting involved in a project, make sure to understand the culture and goals of the project. Be humble while learning the rules and idiosyncrasies of the project and its team.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Keith Brady, Australia>></strong> What types of applications are currently being developed in Ruby and what changes do you foresee over the next year or two?</span>
  </p>
  
  <p>
    <strong>Yehuda>></strong> The biggest changes have to do with old Ruby infrastructure that&#8217;s being pushed to the breaking point. Rubygems, rake, and rdoc were all fantastic pieces of software during the earliest days of Ruby in the US, but the community is putting so much pressure on the projects that significant changes are afoot. Rubygems, for instance, really needs support for &#8220;packages&#8221;, a simple change that could dramatically improve the way large Ruby projects package their applications. I&#8217;d look for modifications or wholesale replacement of core pieces of Ruby infrastructure over the next year.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Michael Uplawski, Germany>></strong> According to you, what is a comfortable size of a Ruby/Rails-project? Why?</span>
  </p>
  
  <p>
    <strong>Yehuda>></strong> Once a Ruby projects gets larger than about 5-10,000 lines of code, I like to start breaking it up into modules. When I say modules, I mean defined sub-projects with their own external APIs that other modules connect to. This prevents the sort of intertwined Ruby projects that are extremely difficult to refactor because of how connected everything is to everything else. In a Merb project, I&#8217;d strongly recommend using slices for this purpose. Merb itself uses rubygems to separate out the core framework (around 6,000 LOC) and additional modules, which all use the same plugin API that we expect users to use in general.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Dennis Theisen, Germany>></strong> Do you think Ruby is ready to be used in &#8220;Enterprise applications&#8221;? Kindly justify your answer.</span>
  </p>
  
  <p>
    <strong>Yehuda>></strong> Absolutely. The productivity benefits alone justify using Ruby in the Enterprise. While certain parts of Ruby might still be rough (SOAP support is a good example), the language itself, and the frameworks surrounding it are so productive that it&#8217;s worth having to deal with the oddities of SOAP4R, for instance. Ruby is also fundamentally changing the way Enterprises should think about software. While it&#8217;s simple to think that you&#8217;re building a piece of software from the ground up with very little common infrastructure, the fact is that proprietary applications built inside enterprises are constantly reinventing the same wheels over and over and over. Since Ruby and its supporting infrastructure is open source, large companies can leverage the power of the work others are doing to avoid having to reinvent the wheel.
  </p>
  
  <p>
    Additionally, as more and more large companies, like Yellow Pages, begin to use Ruby, the feedback loop becomes more powerful as more and more large companies feed back into the community. Engine Yard, the company I work for, has been on the forefront of encouraging contributions, and the ecosystem around Rails and Merb is growing every day (Gartner found that 1,000,000 developers are already using Ruby, and that number is expected to grow to 4,000,000 in just a few years).
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Do you have any other suggestions for these participants (would-be Ruby developers)?</span>
  </p>
  
  <p>
    <strong>Yehuda>></strong> Don&#8217;t be seduced by the power of the dark side. But seriously, Ruby is an extremely powerful language, but you should still define clear, consistent APIs to use both internally and in libraries. When testing, test those interfaces. Avoid mocking out large pieces of the interfaces that prevent you from determining whether the full application or library works. A clear API, with only a few public parts exposed, is worth its weight in pixie dust.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Thanks Yehuda for sharing your views with the RubyLearning participants.</span>
  </p>
  
  <p class="note">
    On 30th Dec. we talk to <strong>Ilya Grigorik</strong> from Canada.
  </p>
  
  <p>
    <span style="font-size: 8pt; font-family: Arial;"><i><strong>Disclaimer:</strong></i></span><br /><span style="font-size: 8pt; font-family: Arial;"><i>The opinions expressed are those of Yehuda Katz and do not necessarily reflect those of <strong><a href="http://rubylearning.com/">www.RubyLearning.com</a></strong>.</i></span>
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
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Interviews" rel="tag">Interviews</a>, <a href="http://technorati.com/tag/Little+Known+Ways+to+Ruby+Mastery" rel="tag">Little Known Ways to Ruby Mastery</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Ruby+Beginners%26%238217%3B+Questions" rel="tag">Ruby Beginners&#8217; Questions</a>, <a href="http://technorati.com/tag/Yehuda+Katz" rel="tag">Yehuda Katz</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>
