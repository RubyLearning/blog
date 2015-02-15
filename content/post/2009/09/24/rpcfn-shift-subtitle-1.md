---
title: 'RPCFN: Shift Subtitle (#1)'
author: Satish Talim
date: 2009-09-24
layout: post
permalink: /2009/09/24/rpcfn-shift-subtitle-1/
thesis_keywords:
  - Ruby,The Ruby Programming Language,Ruby Programming Challenge For Newbies,Programming,RPCFN
thesis_description:
  - The first-ever Ruby Programming Challenge for Newbies.
topsy_short_url:
  - http://bit.ly/8D4krn
categories:
  - Beginners
  - RPCFN
  - Ruby
tags:
  - fabio akita
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
    RPCFN: Shift Subtitle (#1)
  </h4>
  
  <h5>
    By Fabio Akita
  </h5>
  
  <p class="update">
    After a <a href="http://rubylearning.com/blog/2009/09/13/poll-ruby-problems-for-beginners-and-prizes/">very encouraging response to our poll</a> from YOU, the readers of the <abbr title="RubyLearning">RL</abbr> blog, RL is happy to announce the first-ever <b>fortnightly</b> ( bi-weekly / every 14 days) &#8220;<strong>Ruby Programming Challenge For Newbies (RPCFN)</strong>&#8221; in Ruby. Thanks to YOU, the Ruby community, people like Fabio Akita and companies like Locaweb who make all of this possible.
  </p>
  
  <h3>
    About Fabio Akita
  </h3>
  
  <p class="block">
    <img class="alignleft" title="Fabio Akita" src="http://www.rubylearning.com/images/akita.jpg" alt="Fabio Akita" /><strong>Fabio Akita</strong> is a Brazilian Rails enthusiast, also known online as &#8220;AkitaOnRails&#8221;. He regularly write posts on his own <a href="http://www.akitaonrails.com/">blog</a> and had published the very first book tailored for the Brazilian audience called &#8220;Repensando a Web com Rails&#8221;.
  </p>
  
  <p>
    He is now a full-time Ruby on Rails developer working as Project Manager at <a href="http://www.locaweb.com/default.html?utm_campaign=Rails&utm_source=rubylearning&utm_medium=quadrado">Locaweb</a>, Brazil. He&#8217;s also the creator of the &#8220;<a href="http://www.railssummit.com.br/">Rails Summit Latin America</a>&#8220;, the largest international Rails event in South America.
  </p>
  
  <p>
    Fabio has this to say about the challenge:
  </p>
  
  <blockquote>
    <p>
      <em>If you&#8217;re learning a new language such as Ruby, it is important that you practice it. And the best way to start is by scratching your own itch. Anything goes. It&#8217;s not unusual to start by writing simple command line scripts to help out your everyday routine. That&#8217;s why I thought of a very trivial exercise in the first challenge. It should demand that you know the basics for a variety of Ruby subjects such as regular expressions, file manipulation, time calculation and so on. The only way to achieve mastery is by practice. So let&#8217;s get started!</em>
    </p>
  </blockquote>
  
  <h3>
    Sponsor
  </h3>
  
  <p>
    <a href='http://www.1steasy.com/ruby-on-rails.htm'><img class="alignright" src='http://rubylearning.com/images/rubylearning125.gif' width="125" height="125" style="border: 0px none ;" alt="UK based Passenger Hosting" title="UK based Passenger Hosting" /></a>
  </p>
  
  <p>
    <strong><a href="http://www.1steasy.com/">1st Easy Limited</a></strong> are delighted to have been given the opportunity to support the work of Satish Talim and his team at RubyLearning.
  </p>
  
  <p>
    Taking part in the Ruby Programming Challenge? You’re welcome to take advantage of the free <a href="http://www.1steasy.com/ruby-on-rails.htm">Ruby on Rails hosting trials</a> that 1st Easy offer: simply register your details, and a full-featured account is yours to do with as you please for one month. Once the trial is over, you can transfer your work to a paid account, or walk away with no questions asked!
  </p>
  
  <h3>
    Prizes
  </h3>
  
  <ul>
    <li>
      The person with the best Ruby solution (if there is a tie between answers, then the one who posted first will be the winner) will be awarded any <b>one</b> of PeepCode&#8217;s <a href="http://peepcode.com/screencasts/ruby-on-rails">Ruby on Rails screencasts</a>.
    </li>
    <li>
      The other prize, selected randomly amongst the remaining working Ruby solutions, will be awarded any <b>one</b> of Pragmatic&#8217;s <a href='http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming'>The Ruby Object Model and Metaprogramming</a> screencasts.
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
    <b>Difficulty</b>: Ruby beginner.
  </p>
  
  <p>
    <b>Goals</b>: Basic control over Ruby elements, specially command line scripting.
  </p>
  
  <p>
    <b>Description</b>: There are several ways to subtitle a movie nowadays, and one of the most well known format is the SubRip format (<a href="http://en.wikipedia.org/wiki/SubRip">http://en.wikipedia.org/wiki/SubRip</a>). It has entries like these:
  </p>
  
  <pre>645
01:31:51,210 --> 01:31:54,893
the government is implementing a new policy...

646
01:31:54,928 --> 01:31:57,664
In connection with a dramatic increase
in crime in certain neighbourhoods,
</pre>
  
  <p>
    Each line has an increasing integer identification, then comes the time range (start and end time) in the format &#8220;hours:minutes:seconds,milliseconds&#8221;. The decimal separator used is the comma. Finally there are the subtitles themselves and a line break marks the end of an entry.
  </p>
  
  <p>
    Sometimes the timing is shifted for a small amount, 2 or 3 seconds. Then comes the trouble when you need to shift everything a few seconds back or ahead.
  </p>
  
  <p>
    The goal is to create a small command line script in Ruby that will read an SRT file, and output another one with the new calculated times.
  </p>
  
  <p>
    So, for example, if I want to shift everything 2,500 (2 seconds and 500 milliseconds) ahead, I would start with this:
  </p>
  
  <pre>01:32:04,283 --> 01:32:07,769
</pre>
  
  <p>
    and end up with:
  </p>
  
  <pre>01:32:06,783 --> 01:32:10,269
</pre>
  
  <p>
    The command line should accept arguments such as:
  </p>
  
  <pre>shift_subtitle --operation add --time 02,110 input_file output_file
</pre>
  
  <p>
    This means &#8220;&#45;&#45;operation&#8221; can accept either &#8216;add&#8217; or &#8216;sub&#8217; to add or subtract times. The &#8220;&#45;&#45;time&#8221; will accept the amount of time to shift in the format 11,222 where &#8220;11&#8221; is the amount of seconds and &#8220;222&#8221; the amount of milliseconds.
  </p>
  
  <p>
    <b>Requirements</b>: This has to be a pure Ruby script, using only the Ruby Standard Libraries (meaning, no external Gems).
  </p>
  
  <p>
    It has to implement &#8220;optparse&#8221; to parse the command line arguments.
  </p>
  
  <p>
    As an observation, bear in mind that the first thing that you might attempt will look like this:
  </p>
  
  <pre>a = Time.at(04,283)
b = a + 2.500
puts b.usec
=> 500283
</pre>
  
  <p>
    This is wrong, the proper result should&#8217;ve been &#8220;783&#8221; (as in the example in the previous section). So it means that you will have to find another way out.
  </p>
  
  <p>
    <b>Extras (Optional)</b>: If you want:
  </p>
  
  <ul>
    <li>
      It would be interesting to exercise the process of a Gem creation. So you would have to package your script.
    </li>
    <li>
      Another thing that would be good is to have RSpec unit tests covering your code, to exercise software development best practices.
    </li>
  </ul>
  
  <p>
    <b>(Note that the above two points are optional and not a requirement).</b>
  </p>
  
  <h3 style="color:#0000FF;">
    How to Enter the Challenge
  </h3>
  
  <p>
    <b>It&#8217;s free and registration is not required</b>. You can enter the challenge just by posting the following as a comment to this blog post:
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
      Your Solution (i.e. Ruby code): Prefix your code with <pre> tag and suffix it with </pre> tag.
    </li>
    <li>
      Code works with Ruby 1.8 / 1.9 / Both:
    </li>
    <li>
      Explanation (if any):
    </li>
    <li>
      Test cases (if any):
    </li>
  </ol>
  
  <p>
    <b>Note</b>:
  </p>
  
  <ul>
    <li>
      You may provide the URL of your source code, in case it is hosted on GitHub.
    </li>
    <li>
      All solutions posted would be hidden to allow users to come up with their own solutions.
    </li>
    <li>
      <b>You should post your entries before midnight of 4th Oct. 2009 (Indian Standard Time). No new solutions will be accepted from 5th to 8th Oct. 2009.</b>
    </li>
    <li>
      On Monday, 5th Oct. 2009 all the solutions will be thrown open for everyone to see and comment upon.
    </li>
    <li>
      The winning entries will be announced on this blog. The winners will be sent their prizes by email.
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
      <a href="http://www.akitaonrails.com/">Fabio Akita</a>.
    </li>
    <li>
      Sponsor <a href="http://www.1steasy.com/">1st Easy Limited</a>, U.K.
    </li>
    <li>
      The RubyLearning team, namely <a href="http://citizen428.net/">Michael Kohl</a> (Austria), Peter Crawford (Italy), Satoshi Asakawa (Japan) and Victor Goff (USA).
    </li>
    <li>
      <a href="http://www.rubyinside.com.br/participe-do-desafio-do-ruby-learning-e-concorra-a-premios-2227">Ruby Inside, Brazil</a>.
    </li>
    <li>
      <a href="http://ruby.about.com/b/2009/10/02/have-you-tried-the-ruby-programming-challenge-for-newbies-yet.htm">Amanda and Michael&#8217;s Ruby Blog</a>
    </li>
    <li>
      <a href="http://redshinythings.blogspot.com/2009/10/ruby-challenge.html">Adrian</a>
    </li>
    <li>
      <a href="http://www.deploymentzone.com/2009/09/29/temp-files-and-ruby-1-8-6-on-windows/">Charles Feduke</a>
    </li>
    <li>
      <a href="http://blog.kreusch.com.br/post/199158389/my-ruby-programming-challenge-for-newbies-1-entry">Fabio Kreusch</a>
    </li>
    <li>
      <a href="http://www.fernandoquadro.com.br/html/2009/09/25/desafio-ruby-learning-participe-e-concorra-a-premios/">Fernando Quadro</a>
    </li>
    <li>
      <a href="http://charpcfn.wordpress.com/2009/10/06/shift-subtitle-results/">It&#8217;s so shiny</a>
    </li>
    <li>
      <a href="http://blog.foxxtrot.net/2009/09/ruby-programming-challenge-for-newbies.html">Jeff Craig</a>
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
    There are two categories of participants. Some are vying for the prize and some are participating for the fun of it. The participants were:
  </p>
  
  <h4>
    In the competition
  </h4>
  
  <ol>
    <li>
      Felipe Giotto, Brazil
    </li>
    <li>
      Eduardo, Brazil
    </li>
    <li style="color:#0000FF;">
      Kalle Lindström, Sweden &#8211; declared winner
    </li>
    <li>
      Robison WR Santos, Brazil
    </li>
    <li>
      Aldric, USA
    </li>
    <li>
      Akshay Gupta, India
    </li>
    <li>
      Fabio Kreusch, Brazil
    </li>
    <li>
      Chris Jones, USA
    </li>
    <li>
      Chuck Ha, USA
    </li>
    <li>
      Milan Dobrota, Serbia
    </li>
    <li>
      Parag Shah, India
    </li>
    <li>
      Hugo Figueiredo, Brazil
    </li>
    <li>
      John McDonald, USA
    </li>
    <li style="color:#0000FF;">
      <a href="http://rubylearning.com/blog/2009/10/08/felipe-elias-philipp-winner-rpcfn-1/">Felipe Elias Philipp</a>, Brazil &#8211; declared winner
    </li>
    <li>
      Charles Feduke, USA
    </li>
    <li>
      Hari Rajagopal, USA
    </li>
    <li>
      Brad O&#8217;Connor, Australia
    </li>
    <li>
      Oliver, UK
    </li>
    <li>
      Jacob Lichner, USA
    </li>
    <li>
      Todd Huss, USA
    </li>
    <li>
      Antonio, Canada
    </li>
    <li>
      Sriram Varahan, India
    </li>
    <li>
      Giordano Scalzo, Italy
    </li>
    <li>
      Phil Kates, USA
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
      Rodrigo Rosenfeld Rosas, Brazil
    </li>
    <li>
      Dominik Honnef, Germany
    </li>
    <li>
      Mike Hodgson, Canada
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
      <b>Felipe Elias Philipp</b> from Brazil (his <a href="http://github.com/felipeelias/shift_subtitle">Ruby Challenge solution</a>) &#8211; the person with the best Ruby solution. He wins any <b>one</b> of PeepCode&#8217;s <a href="http://peepcode.com/screencasts/ruby-on-rails">Ruby on Rails screencasts</a>.
    </li>
    <li>
      <b>Kalle Lindström</b> from Sweden (his <a href="https://gist.github.com/fa3ec5afe7b19d22c44a">Ruby Challenge solution</a>) &#8211; selected randomly amongst the remaining working Ruby solutions. He wins any <b>one</b> of Pragmatic&#8217;s <a href='http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming'>The Ruby Object Model and Metaprogramming</a> screencasts.
    </li>
  </ul>
  
  <h3>
    Next Challenge
  </h3>
  
  <p>
    <a href="http://rubylearning.com/blog/2009/10/08/rpcfn-average-arrival-time-for-a-flight-2/">RPCFN: Average Arrival Time For A Flight (#2)</a> by Chris Strom.
  </p>
  
  <p>
    <img class="alignleft" src='http://rubylearning.com/images/update.jpg' style="border: 0px none ;" alt="Update" title="Update" />
  </p>
  
  <ul>
    <li>
      <b>The Challenge is now closed</b>. <b>Fabio Akita</b> has a <a href="http://github.com/akitaonrails/Shift-Subtitle">working solution to this problem</a>. This is not a &#8220;perfect&#8221; or the sole &#8220;correct&#8221; solution, but just one way of doing it. Fabio is thankful to <b>Satoshi Asakawa</b> for using one of his ideas in this implementation.
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>, <a href="http://technorati.com/tag/Ruby+Programming+Challenge+For+Newbies" rel="tag">Ruby Programming Challenge For Newbies</a>, <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/RPCFN" rel="tag">RPCFN</a>, <a href="http://technorati.com/tag/Fabio+Akita" rel="tag">Fabio Akita</a>
