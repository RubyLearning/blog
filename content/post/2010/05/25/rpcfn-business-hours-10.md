---
title: 'RPCFN: Business Hours - 10'
author: Satish Talim
date: 2010-05-25
layout: post
permalink: /2010/05/25/rpcfn-business-hours-10/
thesis_description:
  - The 10th Ruby Challenge for Newbies is by Ryan Bates on RubyLearning.org
thesis_keywords:
  - ruby, the ruby programming language, ruby programming challenge for newbies, programming, rpcfn, ryan bates
topsy_short_url:
  - http://bit.ly/dxYc67
categories:
  - Beginners
  - RPCFN
  - Ruby
tags:
  - programming
  - RPCFN
  - Ruby
  - Ruby Programming Challenge For Newbies
  - Ryan Bates
  - The Ruby Programming Language
---
<div>
  <h3>
    Ruby Programming Challenge For Newbies
  </h3>
  
  <h4>
    RPCFN: Business Hours (#10)
  </h4>
  
  <h5>
    By Ryan Bates
  </h5>
  
  <h3>
    About Ryan Bates
  </h3>
  
  <p class="block">
    <img class="alignright" title="Ryan Bates" src="http://rubylearning.com/images/ryan_bates.jpg" alt="Ryan Bates" /><b>Ryan Bates</b> has been involved in web development since 1998. In 2005 he started working professionally with Ruby and Rails and is now best known for his work on <a href="http://railscasts.com/">Railscasts</a>, the free Ruby on Rails screencast series.
  </p>
  
  <p>
    Ryan has this to say about the challenge:
  </p>
  
  <blockquote>
    <p>
      <em>Sometimes when working in a structured framework environment such as Rails it is easy to forget about the fundamentals of Ruby and how to organize code. The majority of this challenge could be done in one large method, but I encourage you to focus on readability through refactoring. This challenge also exercises working with times and iterations.</em>
    </p>
  </blockquote>
  
  <h3>
    Our Awesome Sponsor
  </h3>
  
  <p>
    This monthly programming challenge is sponsored by <strong>Backup My App</strong>.
  </p>
  
  <p>
    <a href="http://backupmyapp.com/"><img class="alignright" src="http://rubylearning.com/images/banner1.gif" width="125" height="125" style="border: 0px none ;" alt="Backup My App" title="Backup My App" /></a>
  </p>
  
  <p>
    <strong>Backup My App</strong> is an automatic backup service for Ruby on Rails applications. You simply install the plugin to your Rails application and they handle the rest of the process. They store backup history for several weeks and you can restore any of them automatically. Try out their 1 GB plan for free. <a href="http://backupmyapp.com/">Backup My App</a> has sponsored this challenge and is proud to make this contribution to the Ruby community.
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
    Chunky Bacon Begone is a dry-cleaning company known for its speedy service. It guarantees to dry-clean anything within two business hours or less. The problem is, when the customer drops off the clothes, he needs to know what time they are guaranteed to be done.
  </p>
  
  <p>
    It is your job to write a Ruby script which will determine the guaranteed time given a business hour schedule. You must create a class called <b>BusinessHours</b> which allows one to define the opening and closing time for each day. It should provide the following interface:
  </p>
  
  <pre>
hours = BusinessHours.new("9:00 AM", "3:00 PM")
hours.update :fri, "10:00 AM", "5:00 PM"
hours.update "Dec 24, 2010", "8:00 AM", "1:00 PM"
hours.closed :sun, :wed, "Dec 25, 2010"
</pre>
  
  <p>
    The <b>update</b> method should change the opening and closing time for a given day. The <b>closed</b> method should specify which days the shop is not open. Notice days can either be a symbol for week days or a string for specific dates. Any given day can only have one opening time and one closing time &#8212; there are no off-hours in the middle of the day.
  </p>
  
  <p>
    A method called <b>calculate_deadline</b> should determine the resulting business time given a time interval (in seconds) along with a starting time (as a string). The returned object should be an instance of <b>Time</b>. Here are some examples:
  </p>
  
  <pre>
hours.calculate_deadline(2*60*60, "Jun 7, 2010 9:10 AM") # => Mon Jun 07 11:10:00 2010
hours.calculate_deadline(15*60, "Jun 8, 2010 2:48 PM") # => Thu Jun 10 09:03:00 2010
hours.calculate_deadline(7*60*60, "Dec 24, 2010 6:45 AM") # => Mon Dec 27 11:00:00 2010
</pre>
  
  <p>
    In the first example the time interval is 2 hours (7,200 seconds). Since the 2 hours fall within business hours the day does not change and the interval is simply added to the starting time.
  </p>
  
  <p>
    In the second line an interval of 15 minutes (900 seconds) is used. The starting time is 12 minutes before closing time which leaves 3 minutes remaining to be added to the next business day. The next day is Wednesday and therefore closed, so the resulting time is 3 minutes after opening on the following day.
  </p>
  
  <p>
    The last example is 7 hours (25200 seconds) which starts before opening on Dec 24th. There are only 5 business hours on Dec 24th which leaves 2 hours remaining for the next business day. The next two days are closed (Dec 25th and Sunday) therefore the deadline is not until 2 hours after opening on Dec 27th.
  </p>
  
  <p>
    <b>Tip</b>: Use <b>Time.parse</b> to generate a Time from a string. You may need to <b>require &#8220;time&#8221;</b> in order to do this.
  </p>
  
  <p>
    <b>Requirements</b>: This has to be a pure Ruby script, using only the Ruby Standard Libraries (meaning, no external Gems, libraries). You do not need to build a gem for this. Pure Ruby code is all that is needed. Ryan will mostly be judging by the beauty of your code as long as it satisfies his test case.
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
      <b>You should post your entries before midnight of 27th June 2010 (Indian Standard Time). No new solutions will be accepted from 28th June onwards.</b>
    </li>
    <li>
      On 28th June 2010 all the solutions will be thrown open for everyone to see and comment upon.
    </li>
    <li>
      The winning entries will be announced on this blog before 30th June 2010. The winners will be sent their prizes by email.
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
      <a href="http://railscasts.com/">Ryan Bates</a>.
    </li>
    <li>
      Sponsors <strong>Backup My App</strong>.
    </li>
    <li>
      <a href="http://github.com/">GitHub</a>, for giving us access to a private repository on GitHub to store all the submitted solutions.
    </li>
    <li>
      The RubyLearning team.
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
      Simon Menke, Belgium
    </li>
    <li>
      Colin Casey, Canada
    </li>
    <li>
      Stephane Tang, France
    </li>
    <li>
      Juan Villanelo, Chile
    </li>
    <li>
      Vasko Zdravevski, USA
    </li>
    <li>
      Sebastián Rabuini, Argentina
    </li>
    <li>
      Dmitry Lipovoi, Russia
    </li>
    <li>
      Andy Vanasse, USA
    </li>
    <li>
      Cary Swoveland, Canada
    </li>
    <li>
      Jeremy Peterson, USA
    </li>
    <li>
      Paul Mucur, UK
    </li>
    <li>
      Delbert Mitten, USA
    </li>
    <li>
      Theo Mills, USA
    </li>
    <li>
      Rémy Coutable, France
    </li>
    <li>
      James Silberbauer, South Africa
    </li>
    <li>
      Michael Cramm, Canada
    </li>
    <li>
      Christopher Fortenberry, USA
    </li>
    <li>
      Tanzeeb Khalili, Canada
    </li>
  </ol>
  
  <h4>
    Just for Fun
  </h4>
  
  <ol>
    <li>
      James Edward Gray II, USA
    </li>
    <li>
      Eric Hutzelman, USA
    </li>
    <li>
      Benoit Daloze, Belgium
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
      <b>Dmitry Lipovoi</b> from Russia (his <a href="https://gist.github.com/e9c0da1a6e92dd12cbc7">Ruby Challenge solution</a>) &#8211; the person with the best and most creative Ruby solution. He wins any <b>one</b> of PeepCode’s <a href="http://peepcode.com/screencasts/ruby-on-rails">Ruby on Rails screencasts</a> and a free 10 GB account for a year from <a href="http://backupmyapp.com/">Backup My App</a>.
    </li>
    <li>
      <b>Michael Cramm</b> from Canada, <b>Cary Swoveland</b> from Canada and <b>Jeremy Peterson</b> from USA win any <b>one</b> of Pragmatic’s <a href="http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming">The Ruby Object Model and Metaprogramming screencasts</a>.
    </li>
    <li>
      <b>All the participants in this challenge (except Dmitry Lipovoi who gets a free 10 GB account for a year) will get a free 5 GB account for 6 months from <a href="http://backupmyapp.com/">Backup My App</a></b>.
    </li>
  </ul>
  
  <h3>
    Previous Challenge
  </h3>
  
  <p>
    <a href="http://rubylearning.com/blog/2010/04/29/rpcfn-interactive-fiction-9/">RPCFN: Interactive Fiction (#9)</a> by Avdi Grimm.
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
      All the solutions have been tested and the results are available <a href="http://github.com/IndianGuru/RPCFN10">here</a>.
    </li>
    <li>
      The (#11) challenge by <b>Elise Huard, Belgium</b> is scheduled for 1st July 2010.
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>, <a href="http://technorati.com/tag/Ruby+Programming+Challenge+For+Newbies" rel="tag">Ruby Programming Challenge For Newbies</a>, <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/RPCFN" rel="tag">RPCFN</a>, <a href="http://technorati.com/tag/Ryan+Bates" rel="tag">Ryan Bates</a>
