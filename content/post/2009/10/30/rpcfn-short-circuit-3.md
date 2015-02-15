---
title: 'RPCFN: Short Circuit (#3)'
author: Satish Talim
date: 2009-10-30
layout: post
permalink: /2009/10/30/rpcfn-short-circuit-3/
thesis_description:
  - The third Ruby Programming Challenge for Newbies by Gautam Rege at RubyLearning.
thesis_keywords:
  - Ruby,The Ruby Programming Language,Ruby Programming Challenge For Newbies,Programming,RPCFN,Gautam Rege
topsy_short_url:
  - http://bit.ly/8Cb47L
categories:
  - Beginners
  - RPCFN
  - Ruby
tags:
  - Gautam Rege
  - programming
  - RPCFN
  - Ruby
  - Ruby Programming Challenge For Newbies
  - The Ruby Programming Language
---
<div>
  <h3>
    Ruby Programming Challenge For Newbies
  </h3>
  
  <h4>
    RPCFN: Short Circuit (#3)
  </h4>
  
  <h5>
    By Gautam Rege
  </h5>
  
  <h3>
    About Gautam Rege
  </h3>
  
  <p class="block">
    <img class="alignleft" title="Gautam Rege" src="http://rubylearning.com/images/gautamrege.png" alt="Gautam Rege" />Gautam Rege (<a href="http://twitter.com/gautamrege">twitter</a> / <a href="http://gautamrege.wordpress.com/">blog</a>) is based in Pune, one of the busiest IT hubs in India. He has done his computer engineering from Pune Institute of Computer Technology (PICT) and passed out in the year 2000. After working for a few services based companies like Zensar and Cybage he got exposure to product companies like Veritas (now Symantec). It was always his aim to be self-employed and when he found the right partner in his friend <b>Sethupathi Asokan</b>, they both started <b><a href="http://blog.joshsoftware.com/">Josh Software Pvt. Ltd.</a></b>.
  </p>
  
  <p>
    Gautam has this to say about the challenge:
  </p>
  
  <blockquote>
    <p>
      <em>RPCFN is a unique idea on RubyLearning &#8211; and I wish I had some such help when I was starting to learn Ruby. This is learning and fun! Now that everyone seems to have got onto the challenger track, I think its time to raise the bar &#8212; very slightly <img src="http://rubylearning.com/blog/wp-includes/images/smilies/icon_wink.gif" alt=";)" class="wp-smiley" /> Short-circuit has a twist in the tail &#8211; its not just learning Ruby but also seeing how easy it is to implement well-known algorithms quickly and efficiently. Welcome newbies to this 3rd Challenge &#8211; all the best!</em>
    </p>
  </blockquote>
  
  <h3>
    Sponsor
  </h3>
  
  <p>
    <a href='http://blog.joshsoftware.com/'><img class="alignright" src='http://rubylearning.com/images/joshbannerad.jpg' width="125" height="125" style="border: 0px none ;" alt="Josh Software Pvt. Ltd." title="Josh Software Pvt. Ltd." /></a>
  </p>
  
  <p>
    This monthly programming challenge is sponsored by <strong><a href="http://joshsoftware.com/index.html">Josh Software Pvt. Ltd.</a></strong> Josh Software is an upcoming Rails start-up in Pune, India. &#8216;Josh&#8217; in Hindi (an Indian language), means &#8216;enthusiasm&#8217;. The Josh team builds state-of-the-art web based applications for various clients in various industry verticals with all the &#8216;josh&#8217;. The work culture at Josh involves fun at work, sincerity in coding and quality deliverables.
  </p>
  
  <h3>
    Prizes
  </h3>
  
  <ul>
    <li>
      The person with the best Ruby solution (if there is a tie between answers, then the one who posted first will be the winner) will be awarded any <b>one</b> of PeepCode&#8217;s <a href="http://peepcode.com/screencasts/ruby-on-rails">Ruby on Rails screencasts</a>.
    </li>
    <li>
      The other two prizes, selected randomly amongst the remaining working Ruby solutions, would be any <b>one</b> of: <ul>
        <li>
          BDDCasts&#8217; <a href='http://bddcasts.com/'>screencasts</a> and any <b>one</b> of,
        </li>
        <li>
          Pragmatic&#8217;s <a href='http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming'>The Ruby Object Model and Metaprogramming</a> screencasts.
        </li>
      </ul>
    </li>
  </ul>
  
  <p>
    The three persons who win, can&#8217;t win again in the next immediate challenge but can still participate.
  </p>
  
  <h3 style="color:#0000FF;">
    The Ruby Challenge
  </h3>
  
  <p>
    <img class="alignright" src='http://rubylearning.com/images/rubypc.jpg' style="border: 0px none ;" alt="RPCFN" title="Ruby Programming Challenge For Newbies" />
  </p>
  
  <p>
    Given a closed electrical circuit, we need to identify the redundant elements. For the sake of simplicity, we shall assume only resistors between various points. <b>Electricity will flow through the path of least resistance!</b> Source of electricity is A and the end-point is G.
  </p>
  
  <p>
    The idea of the program is to find the redundant resistors.
  </p>
  
  <p>
    <img class="aligncenter" src='http://rubylearning.com/images/short_circuit.jpg' style="border: 0px none ;" alt="Short Circuit" />
  </p>
  
  <p>
    As shown in the diagram we can &#8216;translate&#8217; load between points into any simple data structures. For example:
  </p>
  
  <pre>[
   [ A, B, 50],
   [ A, D, 150],
   [ B, C, 250],
   [ B, E, 250],
   [ C, E, 350],
   [ C, D, 50],
   [ C, F, 100],
   [ D, F, 400],
   [ E, G, 200],
   [ F, G, 100],
]
</pre>
  
  <p>
    Feel free to use ANY other data structure as long as assumptions are simple and understandable. The source and the end-point may be hard-coded in the script or can be taken as command line parameters, whichever you feel is convenient.
  </p>
  
  <p>
    In the above example, the output expected MUST be the following array of arrays:
  </p>
  
  <pre>[
  [ 'A', 'B', 50 ],
  [ 'B', 'C', 250],
  [ 'B', 'E', 250],
  [ 'C', 'E', 350],
  [ 'D', 'F', 400],
  [ 'E', 'G', 200],
]
</pre>
  
  <h4>
    Hint
  </h4>
  
  <ul>
    <li>
      &#8216;Short Circuit&#8217; is a cryptic clue to the solution for this challenge.
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
      <b>You should post your entries before midnight of 20th Nov. 2009 (Indian Standard Time). No new solutions will be accepted from 21st Nov. onwards.</b>
    </li>
    <li>
      On 21st Nov. 2009 all the solutions will be thrown open for everyone to see and comment upon.
    </li>
    <li>
      The winning entries will be announced on this blog before end of Nov. The winners will be sent their prizes by email.
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
      <a href="http://gautamrege.wordpress.com/">Gautam Rege</a>.
    </li>
    <li>
      Sponsor <a href="http://joshsoftware.com/index.html">Josh Software Pvt. Ltd.</a>.
    </li>
    <li>
      The RubyLearning team, namely Dave Lilley (New Zealand), Jeff Savin (Canada), <a href="http://citizen428.net/">Michael Kohl</a> (Austria), Peter Crawford (Italy), Satoshi Asakawa (Japan) and Victor Goff (USA).
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
      James Daniels, USA
    </li>
    <li>
      Harshad R Wankhede, India
    </li>
    <li>
      Ben Marini, USA
    </li>
    <li>
      Robison WR Santos, Brazil
    </li>
    <li>
      Mark, USA
    </li>
    <li>
      Valério Farias, Brazil
    </li>
    <li>
      Prakash Sejwani, India
    </li>
    <li>
      Paul Smith, England
    </li>
    <li>
      Himansu Desai, USA
    </li>
    <li>
      Rohit Sasikumar, India
    </li>
    <li>
      Pat Harty, USA
    </li>
    <li style="color:#0000FF;">
      Todd Huss, USA &#8211; declared winner (best solution)
    </li>
    <li style="color:#0000FF;">
      Tom, France &#8211; declared winner (randomly selected)
    </li>
    <li>
      Javier Blanco Gutiérrez, Spain
    </li>
    <li>
      Sogo Ohta, Japan
    </li>
    <li>
      Rainer Thiel, New Zealand
    </li>
    <li>
      Andy Newport, New Zealand
    </li>
    <li>
      Antonio, Canada
    </li>
    <li>
      Glenn Goodrich, USA
    </li>
    <li style="color:#0000FF;">
      Sam Johnson, Canada &#8211; declared winner (randomly selected)
    </li>
  </ol>
  
  <h4>
    Just for Fun
  </h4>
  
  <ol>
    <li>
      Aldric Giacomoni, USA
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
      <b>Todd Huss</b> from USA (his <a href="http://gist.github.com/228577">Ruby Challenge solution</a>) &#8211; the person with the best Ruby solution. He wins any <b>one</b> of PeepCode&#8217;s <a href="http://peepcode.com/screencasts/ruby-on-rails">Ruby on Rails screencasts</a>.
    </li>
    <li>
      <b>Tom</b> from France (his <a href="https://gist.github.com/8a70b216514ab5edab5d">Ruby Challenge solution</a>) &#8211; selected randomly amongst the remaining working Ruby solutions. He wins any <b>one</b> of BDDCasts’ <a href='http://bddcasts.com/'>screencasts</a>.
    </li>
    <li>
      <b>Sam Johnson</b> from Canada (his <a href="https://gist.github.com/5ed31a447fb4c03a40fc">Ruby Challenge solution</a>) &#8211; selected randomly amongst the remaining working Ruby solutions. He wins any <b>one</b> of Pragmatic’s <a href="http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming">The Ruby Object Model and Metaprogramming screencasts</a>.
    </li>
  </ul>
  
  <h3>
    Previous Challenge
  </h3>
  
  <p>
    <a href="http://rubylearning.com/blog/2009/10/08/rpcfn-average-arrival-time-for-a-flight-2/">RPCFN: Average Arrival Time For A Flight (#2)</a> by Chris Strom.
  </p>
  
  <p>
    <img class="alignleft" src='http://rubylearning.com/images/update.jpg' style="border: 0px none ;" alt="Update" title="Update" />
  </p>
  
  <p>
    <b>This challenge is now closed.</b> Gautam Rege has posted on his blog <a href="http://gautamrege.wordpress.com/2009/11/20/rpcfn3-short-circuit/">his observations on the code submitted</a> for this challenge. Do have a look.
  </p>
  
  <ul>
    <li>
      The (#4) challenge by <b>Michael Kohl, Austria</b> is scheduled for 1st Dec. 2009.
    </li>
    <li>
      The (#5) challenge by <b><a href="http://rubyinside.com/">Peter Cooper</a>, UK</b> is scheduled for 1st Jan. 2010.
    </li>
    <li>
      The (#6) challenge by John Trupiano, USA</b> is scheduled for 1st Feb. 2010.
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>, <a href="http://technorati.com/tag/Ruby+Programming+Challenge+For+Newbies" rel="tag">Ruby Programming Challenge For Newbies</a>, <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/RPCFN" rel="tag">RPCFN</a>, <a href="http://technorati.com/tag/Gautam+Rege" rel="tag">Gautam Rege</a>
