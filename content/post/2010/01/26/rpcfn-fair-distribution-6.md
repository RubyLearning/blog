---
title: 'RPCFN: Fair Distribution - 6'
author: Satish Talim
date: 2010-01-26
layout: post
permalink: /2010/01/26/rpcfn-fair-distribution-6/
thesis_description:
  - The sixth Ruby Programming Challenge for Newbies by John Trupiano.
thesis_keywords:
  - Ruby,The Ruby Programming Language,Ruby Programming Challenge For Newbies,Programming,RPCFN,John Trupiano
topsy_short_url:
  - http://bit.ly/8oxWQe
categories:
  - beginners
  - rpcfn
  - ruby
tags:
  - john trupiano
  - programming
  - rpcfn
  - ruby
  - ruby programming challenge for newbies
  - the ruby programming language
---
<div>
  <h3>
    Ruby Programming Challenge For Newbies
  </h3>
  
  <h4>
    RPCFN: Fair Distribution (#6)
  </h4>
  
  <h5>
    By John Trupiano
  </h5>
  
  <h3>
    About John Trupiano
  </h3>
  
  <p class="block">
    <img class="alignleft" title="John Trupiano" src="http://rubylearning.com/images/johntrupiano.jpg" alt="John Trupiano" />John Trupiano (<a href="http://twitter.com/jtrupiano">twitter</a>) is the co-founder of <a href="http://smartlogicsolutions.com/">SmartLogic</a>, the premiere Ruby development team in Baltimore, Maryland. He is an active member in the technology and business communities in the mid-Atlantic region. He is highly involved with the local Ruby user group (<a href="http://www.meetup.com/bmore-on-rails/">Bmore on Rails</a>) and recently organized the first ever <a href="http://mdtechcrawl.com/">Maryland TechCrawl</a>, a show and tell event showcasing the exciting and innovative technologies being developed in the region. He is also very active in the open source community having authored <a href="http://github.com/jtrupiano/timecop">timecop</a> and <a href="http://github.com/jtrupiano/rack-rewrite">Rack::Rewrite</a> and contributing to a slew of projects including rails, capistrano, shoulda, factory_girl, gemcutter and multitest.
  </p>
  
  <p>
    John has this to say about the challenge:
  </p>
  
  <blockquote>
    <p>
      <em>I think the Ruby challenge is great because it instills from the very start the idea that you need to practice to become a great programmer. Even as a problem setter, I have found the exercise of defining a problem and iterating through various solutions to be extremely educational and beneficial. Satish has cultivated a fantastic program here that provides access for beginners to seasoned Ruby programmers. Furthermore, the Ruby challenge serves as a notice to the Ruby community that it is important for us to provide a welcoming and nurturing environment for newcomers.</em>
    </p>
  </blockquote>
  
  <h3>
    Our Awesome Sponsors
  </h3>
  
  <p>
    This monthly programming challenge is co-sponsored by <strong>Backup My App</strong> and <strong>Caliper</strong>.
  </p>
  
  <p>
    <a href="http://backupmyapp.com/"><img class="alignright" src="http://rubylearning.com/images/banner1.gif" width="125" height="125" style="border: 0px none ;" alt="Backup My App" title="Backup My App" /></a>
  </p>
  
  <p>
    <strong>Backup My App</strong> is an automatic backup service for Ruby on Rails applications. You simply install the plugin to your Rails application and they handle the rest of the process. They store backup history for several weeks and you can restore any of them automatically. Try out their 1 GB plan for free. <a href="http://backupmyapp.com/">Backup My App</a> has co-sponsored this challenge and is proud to make this contribution to the Ruby community.
  </p>
  
  <p>
    <a href="http://devver.net/caliper"><img class="alignright" src="http://rubylearning.com/images/caliper.png" width="125" height="125" style="border: 0px none ;" alt="Caliper" title="Caliper" /></a>
  </p>
  
  <p>
    <strong><a href="http://devver.net/caliper">Caliper</a></strong> provides free, hosted metrics for Ruby programmers. Find duplication, code smells, complex code and more! Get set up with just one click!
  </p>
  
  <h3>
    Prizes
  </h3>
  
  <ul>
    <li>
      The participant with the best Ruby solution (if there is a tie between answers, then the one who posted first will be the winner) will be awarded any <b>one</b> of PeepCode&#8217;s <a href="http://peepcode.com/screencasts/ruby-on-rails">Ruby on Rails screencasts</a> and a free 10 GB account for a year from <a href="http://backupmyapp.com/">Backup My App</a>.
    </li>
    <li>
      From the remaining working Ruby solutions, three participants would be selected randomly and each one would be awarded any <b>one</b> of Pragmatic&#8217;s <a href='http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming'>The Ruby Object Model and Metaprogramming</a> screencasts.
    </li>
    <li>
      <b>All the participants in this challenge (except the participant with the best Ruby solution) will get a free 5 GB account for 6 months from <a href="http://backupmyapp.com/">Backup My App</a></b>.
    </li>
  </ul>
  
  <p>
    The four persons who win, can&#8217;t win again in the next immediate challenge but can still participate.
  </p>
  
  <h3 style="color:#0000FF;">
    The Ruby Challenge
  </h3>
  
  <p>
    <img class="alignright" src='http://rubylearning.com/images/rubypc.jpg' style="border: 0px none ;" alt="RPCFN" title="Ruby Programming Challenge For Newbies" />
  </p>
  
  <h4>
    The Challenge
  </h4>
  
  <p>
    Imagine that you manage a t-shirt printing company. Each morning you review all orders placed the prior day and determine how long each order will take to fulfill. On any given day, only a certain number of your printing machines are operational. Your job is to schedule each printing job with one of the operational printing machines in such a manner that (a) all t-shirts are printed in the least amount of time, and (b) the distribution of work across machines is as fair as possible (i.e. the standard deviation of the time each machine spends working is minimized).
  </p>
  
  <p>
    Your objective is to write a <b>FairDistribution</b> class that satisfies the following test cases. The code in the test cases is sufficient to define the methods you must implement.
  </p>
  
  <p>
    This is an NP complete problem, and as such I have only provided very small datasets in the test cases. Test case #3 takes the longest to solve (See **Notes below about how to run the Test Case #3) and you may find it easier to comment it out early in your development phase. On a MBP Pro with a 2.4 GHz dual core processor and 4GB RAM, it took just over 3 minutes to solve. The other three test cases took only a couple of seconds.
  </p>
  
  <p>
    Note that test cases 2 and 4 define specific distributions against which you can verify. Test cases 1 and 3 have more than one acceptable distribution and as such I have not provided a specific distribution to test against.
  </p>
  
  <p>
    Note also that there is a well known algorithm that provides a much faster though not optimal solution. It will pass all tests except for test case #3. If you are only able to determine this particular solution, please still consider submitting your solution for consideration.
  </p>
  
  <p>
    <b>** Notes</b>: To accommodate the fact that Test Case #3 takes a long time to run, you can run the test normally, and TC#3 will not run. When you want the TC#3 to run, then you can run the following:
  </p>
  
  <pre>ruby test_solution_acceptance.rb full</pre>
  
  <p>
    The word &#8220;full&#8221; will signal it to run all the test cases.
  </p>
  
  <h4>
    The Test Suite
  </h4>
  
  <p>
    <a href="http://gist.github.com/286495">test_solution_acceptance.rb</a>
  </p>
  
  <h4>
    Requirements
  </h4>
  
  <p>
    The solution to the challenge has to be a pure Ruby script, using only the Ruby Standard Libraries (meaning, no external Gems). You <b>do not</b> need to build a gem for this. Pure Ruby code is all that is needed.
  </p>
  
  <h3 style="color:#0000FF;">
    How to Enter the Challenge
  </h3>
  
  <p>
    Read the <a href="http://rubylearning.com/blog/ruby-programming-challenge-faq/index.php#rpc6">Challenge Rules</a>. By participating in this challenge, you agree to be bound by these Challenge Rules. <b>It&#8217;s free and <a href="http://rubylearning.com/blog/wp-login.php?action=register">registration</a> is optional</b>. You can enter the challenge just by posting the following as a comment to this blog post:
  </p>
  
  <ol>
    <li>
      Your name:
    </li>
    <li>
      Country of Residence:
    </li>
    <li>
      <a href="http://rubylearning.com/blog/ruby-programming-challenge-faq/#rpc5">GIST URL of your Solution</a> (i.e. Ruby code) with explanation and / or test cases:
    </li>
    <li>
      Code works with Ruby 1.8 / 1.9 / Both:
    </li>
    <li>
      Email address (will not be published):
    </li>
    <li>
      Brief description of what you do (will not be published):
    </li>
  </ol>
  
  <p>
    <b>Note</b>:
  </p>
  
  <ul>
    <li>
      As soon as we receive your GIST URL, we will fork your submission. This means that your solution is frozen and accepted. Please be sure that is the solution you want, as it is now recorded in time and is the version that will be evaluated.
    </li>
    <li>
      All solutions posted would be hidden to allow participants to come up with their own solutions.
    </li>
    <li>
      <b>You should post your entries before midnight of 20th Feb. 2010 (Indian Standard Time). No new solutions will be accepted from 21st Feb. onwards.</b>
    </li>
    <li>
      On 21st Feb. 2010 all the solutions will be thrown open for everyone to see and comment upon.
    </li>
    <li>
      The winning entries will be announced on this blog before end of Feb. 2010. The winners will be sent their prizes by email.
    </li>
  </ul>
  
  <h3>
    More details on the RPCFN?
  </h3>
  
  <p>
    Please refer to the <b><a href="http://rubylearning.com/blog/ruby-programming-challenge-faq/">RPCFN FAQ</a></b> for answers to the following questions:
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/blog/ruby-programming-challenge-faq/index.php#rpc1">What Is The Ruby Programming Challenge For Newbies (RPCFN)?</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/ruby-programming-challenge-faq/index.php#rpc2">How does RPCFN benefit you?</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/ruby-programming-challenge-faq/index.php#rpc6">Challenge Rules</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/ruby-programming-challenge-faq/index.php#rpc3">Best Solution</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/ruby-programming-challenge-faq/index.php#rpc4">Can I Submit A Ruby Programming Challenge Topic?</a>
    </li>
  </ul>
  
  <h3>
    Donations
  </h3>
  
  <p>
    RPCFN is entirely financed by RubyLearning and sometimes sponsors, so if you enjoy solving Ruby problems and would like to give something back by helping with the running costs then any donations are gratefully received.
  </p>
  
  <p>
    <a href='http://www.pledgie.com/campaigns/415'><img alt='Click here to lend your support to: Support RubyLearning With Some Love and make a donation at www.pledgie.com !' src='http://www.pledgie.com/campaigns/415.png?skin_name=chrome' style='border:0px;' /></a>
  </p>
  
  <h3>
    Acknowledgements
  </h3>
  
  <p>
    Special thanks to:
  </p>
  
  <ul>
    <li>
      <a href="http://twitter.com/jtrupiano">John Trupiano</a>.
    </li>
    <li>
      Sponsors <strong>Caliper</strong> and <strong>Backup My App</strong>.
    </li>
    <li>
      <a href="http://github.com/">GitHub</a>, for giving us access to a private repository on GitHub to store all the submitted solutions.
    </li>
    <li>
      The RubyLearning team, namely Jeff Savin (Canada), Mareike Hybsier (Germany), Peter Crawford (Italy) and Satoshi Asakawa (Japan).
    </li>
  </ul>
  
  <h3>
    Questions?
  </h3>
  
  <p>
    Contact Satish Talim at <a href="mailto:satish.talim@gmail.com">satish [dot] talim [at] gmail.com</a> OR if you have any doubts / questions about the challenge (the current problem statement), please post them as comments to this post and the author will reply asap.
  </p>
  
  <h3>
    The Participants
  </h3>
  
  <p>
    There are two categories of participants. Some are vying for the prizes and some are participating for the fun of it.
  </p>
  
  <h4>
    In the competition
  </h4>
  
  <ol>
    <li>
      Rajesh Tripathi, USA
    </li>
    <li>
      Aleksey Gureiev, Australia
    </li>
    <li>
      Aldric Giacomoni, USA
    </li>
    <li>
      Adam Lum, USA
    </li>
    <li>
      Brad O&#8217;Connor, Australia
    </li>
    <li>
      Martin Linkhorst, Germany
    </li>
    <li>
      Ilya Ermolin, Russia
    </li>
    <li style="color:#0000FF;">
      Elijah Miller, USA &#8211; declared winner (randomly selected)
    </li>
    <li style="color:#0000FF;">
      <b>Guillaume Petit, France &#8211; declared winner (best solution)</b>
    </li>
    <li>
      Marc Minneman, USA
    </li>
    <li>
      Cary Swoveland, Canada
    </li>
    <li>
      Aurélien Bottazzini, France
    </li>
    <li style="color:#0000FF;">
      Benoit Daloze, Belgium &#8211; declared winner (randomly selected)
    </li>
    <li style="color:#0000FF;">
      Jacob Hodes, USA &#8211; declared winner (randomly selected)
    </li>
  </ol>
  
  <h4>
    Just for Fun
  </h4>
  
  <ol>
    <li>
      Dominik Masur, Germany
    </li>
  </ol>
  
  <h3 style="color:#0000FF;">
    The Winners
  </h3>
  
  <p>
    <img class="alignright" src='http://rubylearning.com/images/winner_icon_1.png' style="border: 0px none ;" alt="Winners" />
  </p>
  
  <p>
    Congratulations to the winners of this Ruby Challenge. They are:
  </p>
  
  <ul>
    <li>
      <b>Guillaume Petit</b> from France (his <a href="https://gist.github.com/3e3b45010e8fae7c7d9b">Ruby Challenge solution</a>) &#8211; the person with the best and most creative Ruby solution. He wins any <b>one</b> of PeepCode’s <a href="http://peepcode.com/screencasts/ruby-on-rails">Ruby on Rails screencasts</a> and a free 10 GB account for a year from <a href="http://backupmyapp.com/">Backup My App</a>.
    </li>
    <li>
      <b>Elijah Miller</b> from USA (his <a href="http://gist.github.com/297449">Ruby Challenge solution</a>), <b>Jacob Hodes</b> from USA (his <a href="https://gist.github.com/a460231c78f2a90180ab">Ruby Challenge solution</a>), and <b>Benoit Daloze</b> from Belgium (his <a href="https://gist.github.com/43c82d5127d5d05ebe2e">Ruby Challenge solution</a>) &#8211; selected randomly amongst the remaining working Ruby solutions. They win any <b>one</b> of Pragmatic’s <a href="http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming">The Ruby Object Model and Metaprogramming screencasts</a>.
    </li>
    <li>
      <b>All the participants in this challenge (except Guillaume Petit who gets a free 10 GB account for a year) will get a free 5 GB account for 6 months from <a href="http://backupmyapp.com/">Backup My App</a></b>.
    </li>
  </ul>
  
  <h3>
    Previous Challenge
  </h3>
  
  <p>
    <a href="http://rubylearning.com/blog/2009/12/27/rpcfn-mazes-5/">RPCFN: Mazes (#5)</a> by Peter Cooper.
  </p>
  
  <p>
    <b>Note</b>: All the previous challenges, sponsors and winners can be seen on the <a href="http://ruby-challenge.rubylearning.org/">Ruby Programming Challenge for Newbies</a> page.
  </p>
  
  <p>
    <img class="alignleft" src='http://rubylearning.com/images/update.jpg' style="border: 0px none ;" alt="Update" title="Update" />
  </p>
  
  <ul>
    <li>
      This challenge is now closed.
    </li>
    <li>
      The (#7) challenge by <b>James Edward Gray II, USA</b> is scheduled for 1st Mar. 2010.
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>, <a href="http://technorati.com/tag/Ruby+Programming+Challenge+For+Newbies" rel="tag">Ruby Programming Challenge For Newbies</a>, <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/RPCFN" rel="tag">RPCFN</a>, <a href="http://technorati.com/tag/John+Trupiano" rel="tag">John Trupiano</a>
