---
title: "RPCFN: Average Arrival Time For A Flight - 2 Reprint"
author: Satish Talim
date: 2015-01-26
layout: post
permalink: /2015/01/26/rpcfn-average-arrival-time-for-a-flight-2-reprint/
categories:
  - beginners
  - popular
  - rpcfn
  - ruby
tags:
  - chris strom
  - programming
  - rpcfn
  - ruby
  - ruby programming challenge for newbies
  - the ruby programming language
---
<div>
  <p>
    <b>Note</b>: This article first appeared on 8th Oct. 2009 but the original is not accessible; hence the reprint.
  </p>
  
  <h3>
    Ruby Programming Challenge For Newbies
  </h3>
  
  <h4>
    RPCFN: Average Arrival Time For A Flight (#2)
  </h4>
  
  <h5>
    By Chris Strom
  </h5>
  
  <p class="update">
    Thank you for the very encouraging response to the <a href="http://rubylearning.com/blog/2015/01/26/felipe-elias-philipp-winner-rpcfn-1-reprint/">first-ever</a> &#8220;<strong>Ruby Programming Challenge For Newbies (RPCFN)</strong>&#8220;. The second Ruby challenge is from Chris Strom.
  </p>
  
  <h3>
    About Chris Strom
  </h3>
  
  <p class="block">
    <img class="alignleft" title="Chris Strom" src="http://rubylearning.com/images/chris_strom.jpg" alt="Chris Strom" />Chris Strom (<a href="http://twitter.com/eee_c">twitter</a> / <a href="http://japhr.blogspot.com/">blog</a>) in his day job, is the Director of Software Engineering for mdlogix, a small company in Baltimore, Maryland. They develop software that manages clinical research trials and associated data. They primarily code with Ruby on Rails. His background is in web development, mostly in Perl until ~2005 when he made the switch to Ruby.
  </p>
  
  <p>
    Chris has this to say about the challenge:
  </p>
  
  <blockquote>
    <p>
      <em>RPCFN is a good idea as reading books and documentation can only take you so far when learning a new language. To really learn, you need to use the language. RPCFN provides a fabulous forum for using Ruby in the form of regular, engaging (but not arcanely difficult) challenges. Better yet, it provides feedback on how to use Ruby well, as each fortnight the best solution to a challenge is chosen. RPCFN is a wonderful introduction to the Ruby language and to the Ruby community. Welcome newbies!</em>
    </p>
  </blockquote>
  
  <h3>
    Sponsor
  </h3>
  
  <p>
    <a href='http://www.railsware.com/'><img class="alignright" src='http://rubylearning.com/images/Railsware125x125.png' width="125" height="125" style="border: 0px none ;" alt="Railsware for premium-quality web applications" title="Railsware for premium-quality web applications" /></a>
  </p>
  
  <p>
    This fortnights programming challenge is sponsored by <strong><a href="http://www.railsware.com/">Railsware</a></strong>. Railsware is glad to support the Ruby Programming Challenge and help the Ruby community grow and get stronger.
  </p>
  
  <p>
    Railsware is a product development company specializing in Ruby on Rails and UI design creating premium-quality web applications. The company works with startups and established businesses looking to build ecommerce, social networking, specialized business applications and many other products.
  </p>
  
  <h3>
    Prizes
  </h3>
  
  <ul>
    <li>
      The person with the best Ruby solution (if there is a tie between answers, then the one who posted first will be the winner) will be awarded any <b>one</b> of PeepCode&#8217;s <a href="http://peepcode.com/screencasts/ruby-on-rails">Ruby on Rails screencasts</a>.
    </li>
    <li>
      The other prize, selected randomly amongst the remaining working Ruby solutions, will be awarded any <b>one</b> of BDDCasts&#8217; <a href='http://bddcasts.com/'>screencasts</a>.
    </li>
  </ul>
  
  <p>
    The two persons who win, can&#8217;t win again in the next immediate challenge but can still participate.
  </p>
  
  <h3 style="color:#0000FF;">
    The Ruby Challenge
  </h3>
  
  <p>
    <img class="alignright" src='http://rubylearning.com/images/rubypc.jpg' style="border: 0px none ;" alt="RPCFN" title="Ruby Programming Challenge For Newbies" />
  </p>
  
  <p>
    You owe a big favor and have agreed to pick up a friend at the airport every Friday night. The airline on which your friend flies is cheap, but terrible with reporting delays and departure/arrival times. You soon realize that the 10pm flight is never on time and is usually late by more than an hour. If the plane has arrived at 11:15pm, 12:03am, 11:30pm, 11:23pm and 11:48pm, what is the average arrival time?
  </p>
  
  <p>
    Does the solution still work if your friend changes to a flight arriving 6 hours later? What about 12 hours later?
  </p>
  
  <h4>
    Program Output
  </h4>
  
  <p>
    The output should look something like this when run from the console:
  </p>
  
  <pre>>> average_time_of_day(["11:51pm", "11:56pm", "12:01am", "12:06am", "12:11am"])
=> "12:01am"

>> average_time_of_day(["6:41am", "6:51am", "7:01am"])
=> "6:51am"
</pre>
  
  <h4>
    Hint
  </h4>
  
  <ul>
    <li>
      Your digital ways will not help you, time of day is cyclical.
    </li>
    <li>
      You may need to use the <b>Math</b> and <b>Time</b> classes.
    </li>
  </ul>
  
  <p>
    <b>Requirements</b>: This has to be a pure Ruby script, using only the Ruby Standard Libraries (meaning, no external Gems). You <b>do not</b> need to build a gem for this. Pure Ruby code is all that is needed.
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
      Email address (will not be published):
    </li>
    <li>
      Brief description of what you do (will not be published):
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
      <b>You should post your entries before midnight of 18th Oct. 2009 (Indian Standard Time). No new solutions will be accepted from 19th to 22nd Oct. 2009.</b>
    </li>
    <li>
      On Monday, 19th Oct. 2009 all the solutions will be thrown open for everyone to see and comment upon.
    </li>
    <li>
      The winning entries will be announced on this blog on 22nd Oct. The winners will be sent their prizes by email.
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
  
  <h3>
    Acknowledgements
  </h3>
  
  <p>
    Special thanks to:
  </p>
  
  <ul>
    <li>
      <a href="http://japhr.blogspot.com/">Chris Strom</a>.
    </li>
    <li>
      Sponsor <a href="http://www.railsware.com/">Railsware</a>.
    </li>
    <li>
      Jeff Schoolcraft of <a href="http://bddcasts.com/">BDDCasts</a>.
    </li>
    <li>
      The RubyLearning team, namely Dave Lilley (New Zealand), Jeff Savin (Canada), <a href="http://citizen428.net/">Michael Kohl</a> (Austria), Peter Crawford (Italy), Satoshi Asakawa (Japan) and Victor Goff (USA).
    </li>
    <li>
      <a href="http://giordano.scalzo.biz/2009/10/10/entering-rpcfn-2/">Giordano Scalzo</a>
    </li>
    <li>
      <a href="http://jonathanjulian.com/2009/10/i-just-entered-rpcfn-2/">Jonathan Julian</a>
    </li>
    <li>
      <a href="http://www.loicpaillotin.com/2009/10/getting-back-in-shape.html">Loïc Paillotin</a>
    </li>
  </ul>
  
  <h3>
    Questions?
  </h3>
  
  <p>
    Contact Satish Talim at <a href="mailto:satish.talim@gmail.com">satish.talim@gmail.com</a> OR if you have any doubts / questions about the challenge (the current problem statement), please post them as comments to this post and the author will reply asap.
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
    <li style="color:#0000FF;">
      Othmane Benkirane, Morocco &#8211; declared winner
    </li>
    <li>
      Tisho Georgiev, Bulgaria
    </li>
    <li>
      Pete Campbell, USA
    </li>
    <li>
      Jonathan Julian, USA
    </li>
    <li>
      Antonio, Canada
    </li>
    <li>
      Robison WR Santos, Brazil
    </li>
    <li>
      Ricardo Duarte, Brazil
    </li>
    <li>
      Paul Barry, USA
    </li>
    <li>
      Haris Amin, USA
    </li>
    <li style="color:#0000FF;">
      <a href="http://rubylearning.com/blog/2009/10/22/charles-feduke-winner-rpcfn-2/">Charles Feduke</a>, USA &#8211; declared winner
    </li>
    <li>
      Oliver, UK
    </li>
    <li>
      Bryan Liles, USA
    </li>
    <li>
      Gunther Diemant, Germany
    </li>
    <li>
      Valério Farias, Brazil
    </li>
    <li>
      Vikas Maskeri, India
    </li>
    <li>
      Jiren Patel, India
    </li>
    <li>
      Stefan, Germany
    </li>
    <li>
      Ahmed Al Hafoudh, Slovakia
    </li>
    <li>
      Tom Voltz, USA
    </li>
    <li>
      David Jenkins, USA
    </li>
    <li>
      Michael Lang, USA
    </li>
    <li>
      Thiago Fernandes Massa, Brazil
    </li>
    <li>
      Tim Rand, USA
    </li>
    <li>
      Milan Dobrota, Serbia
    </li>
    <li>
      Mike Hodgson, Canada
    </li>
    <li>
      Brad O&#8217;Connor, Australia
    </li>
    <li>
      Giordano Scalzo, Italy
    </li>
    <li>
      Rainer Thiel, New Zealand
    </li>
    <li>
      Todd Huss, USA
    </li>
    <li>
      Pankaj Sisodiya, India
    </li>
    <li>
      Loïc Paillotin, USA
    </li>
    <li>
      Chuck Ha, USA
    </li>
    <li>
      Josh Baxley, USA
    </li>
    <li>
      Javier Blanco Gutiérrez, Spain
    </li>
    <li>
      Sogo Ohta, Japan
    </li>
    <li>
      Daniel Wanek, USA
    </li>
    <li>
      Himansu Desai, USA
    </li>
    <li>
      John McDonald, USA
    </li>
    <li>
      Ben Miller, UK
    </li>
    <li>
      Sriram Varahan, India
    </li>
    <li>
      Conner Peirce, USA
    </li>
    <li>
      Ben Marini, USA
    </li>
  </ol>
  
  <h4>
    Just for Fun
  </h4>
  
  <ol>
    <li>
      Michael Kohl, Austria
    </li>
    <li>
      <a href="http://rubyinside.com/">Peter Cooper, UK</a>
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
      <b>Charles Feduke</b> from USA (his <a href="https://gist.github.com/5b371226faf83af50d7e">Ruby Challenge solution</a>) &#8211; the person with the best Ruby solution. He wins any <b>one</b> of PeepCode&#8217;s <a href="http://peepcode.com/screencasts/ruby-on-rails">Ruby on Rails screencasts</a>.
    </li>
    <li>
      <b>Othmane Benkirane</b> from Morocco (his <a href="http://gist.github.com/205002">Ruby Challenge solution</a>) &#8211; selected randomly amongst the remaining working Ruby solutions. He wins any <b>one</b> of BDDCasts’ <a href='http://bddcasts.com/'>screencasts</a>.
    </li>
  </ul>
  
  <h3>
    Previous Challenge
  </h3>
  
  <p>
    <a href="http://rubylearning.com/blog/2015/01/25/rpcfn-shift-subtitle-1-reprint/">RPCFN: Shift Subtitle (#1)</a> by Fabio Akita.
  </p>
  
  <h3>
    Next Challenge
  </h3>
  
  <p>
    <a href="http://rubylearning.com/blog/2009/10/30/rpcfn-short-circuit-3/">RPCFN: Short Circuit (#3)</a> by Gautam Rege.
  </p>
  
  <p>
    <img class="alignleft" src='http://rubylearning.com/images/update.jpg' style="border: 0px none ;" alt="Update" title="Update" />
  </p>
  
  <ul>
    <li>
      <b>This Challenge is now closed</b>. <b>Chris Strom</b> has a <a href="https://gist.github.com/4f6807eef49064027a3c">working solution to this problem</a>. This is not a &#8220;perfect&#8221; or the sole &#8220;correct&#8221; solution, but just one way of doing it.
    </li>
    <li>
      Chris Strom has written a blog post that talks about the <a href="http://japhr.blogspot.com/2009/10/newbie-feedback.html">most common &#8220;issues&#8221; faced by Ruby beginners</a>.
    </li>
    <li>
      The (#3) challenge by <b>Gautam Rege, India</b> is scheduled for 1st Nov. 2009.
    </li>
    <li>
      The (#4) challenge by <b>Michael Kohl, Austria</b> is scheduled for 1st Dec. 2009.
    </li>
    <li>
      The (#5) challenge by <b><a href="http://rubyinside.com/">Peter Cooper</a>, UK</b> is scheduled for 1st Jan. 2010.
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>, <a href="http://technorati.com/tag/Ruby+Programming+Challenge+For+Newbies" rel="tag">Ruby Programming Challenge For Newbies</a>, <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/RPCFN" rel="tag">RPCFN</a>, <a href="http://technorati.com/tag/Chris+Strom" rel="tag">Chris Strom</a>
