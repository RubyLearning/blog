---
title: 'RPCFN: XML Transformer - 8'
author: Satish Talim
date: 2010-04-07
layout: post
permalink: /2010/04/07/rpcfn-xml-transformer-8/
thesis_description:
  - Jamie van Dyke throws a new Ruby Challenge for Ruby Newbies at RubyLearning.
thesis_keywords:
  - Ruby,The Ruby Programming Language,Ruby Programming Challenge For Newbies,Programming,RPCFN,Jamie van Dyke
topsy_short_url:
  - http://bit.ly/aNaIaD
categories:
  - beginners
  - rpcfn
  - ruby
tags:
  - jamie van dyke
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
    RPCFN: XML Transformer (#8)
  </h4>
  
  <h5>
    By Jamie van Dyke
  </h5>
  
  <h3>
    About Jamie van Dyke
  </h3>
  
  <p class="block">
    <img class="alignleft" title="Jamie van Dyke" src="http://rubylearning.com/images/jamiedyke.jpg" alt="Jamie van Dyke" />Jamie van Dyke has been using Ruby and Rails since the beginning of 2005, has contributed significantly to the Rails documentation and code base, as well as running his own Rails business and being responsible for building Engine Yard&#8217;s European support team. Jamie is now the CTO over at <a href="http://www.boxedup.com/">Boxedup</a>.
  </p>
  
  <p>
    Jamie has this to say about the challenge:
  </p>
  
  <blockquote>
    <p>
      <em>This challenge is ideal for both beginner and advanced users. You can solve it in multiple ways and with differing levels of complexity, each level giving more flexibility. I hope you enjoy trying to solve the challenge and I look forward to seeing the results.</em>
    </p>
  </blockquote>
  
  <h3>
    Our Awesome Sponsors
  </h3>
  
  <p>
    This monthly programming challenge is co-sponsored by <strong>Eden Development</strong> and <strong>Backup My App</strong>.
  </p>
  
  <p>
    <a href="http://edendevelopment.co.uk/"><img class="alignright" src='http://rubylearning.com/images/eden-new-logo-leaf-square.png' width="125" height="125" style="border: 0px none ;" alt="A leading software development firm based in Winchester, UK" title="A leading software development firm based in Winchester, UK" /></a>
  </p>
  
  <p>
    <strong><a href="http://edendevelopment.co.uk/">Eden Development</a></strong> is a leading software development firm based in Winchester, UK, specialising in Ruby applications. They craft dependable, flexible and beautifully made software which meets real business needs. They stand for quality, integrity, real craftsmanship and peace of mind for their customers. They also teach basic Ruby to Agile/XP courses: they love learning themselves and are delighted to support the RubyLearning initiative.
  </p>
  
  <p>
    <a href="http://backupmyapp.com/"><img class="alignright" src="http://rubylearning.com/images/banner1.gif" width="125" height="125" style="border: 0px none ;" alt="Backup My App" title="Backup My App" /></a>
  </p>
  
  <p>
    <strong>Backup My App</strong> is an automatic backup service for Ruby on Rails applications. You simply install the plugin to your Rails application and they handle the rest of the process. They store backup history for several weeks and you can restore any of them automatically. Try out their 1 GB plan for free. <a href="http://backupmyapp.com/">Backup My App</a> has co-sponsored this challenge and is proud to make this contribution to the Ruby community.
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
  
  <h5>
    Introduction
  </h5>
  
  <p>
    I love a good challenge and find it helps you discover different aspects of a language, and also different methods to achieve the same goal. Seeing how others completed a quiz also helps you to expand your knowledge and experience which will give you more insight in the future.
  </p>
  
  <p>
    The best tests are always ones based on real world examples. I&#8217;ve tried to simplify this one so it&#8217;s accessible to all that want to take a stab, while at the same time allowing those that one to be more advanced the opportunity to show off a little. You could complete this with a simple solution, or spend more time and give an elegant, more ruby-ish answer. You choose.
  </p>
  
  <p>
    A library I recently wrote had to import data on a regular basis. I needed to normalise the data before I could import it because the data was from different XML feeds, but in unknown formats. So, your challenge is to build an XML transformer that can take any (within reason) XML file and change it into an expected XML format.
  </p>
  
  <h5>
    Specifics
  </h5>
  
  <p>
    You can <a href="http://rubylearning.com/data/xmlfiles.zip">download 3 source XML files</a> as examples. You need to work out how to convert each of these files in to the expected output, bearing in mind that these are merely examples and therefore you should make your transformer as flexible as possible to handle other source inputs.
  </p>
  
  <p>
    You will need to employ the use of an XML library, personally I use the <b>nokogiri rubygem</b>, but feel free to choose your own. Once you&#8217;ve decided on XML parser it&#8217;s up to you how you go about solving this quiz. I&#8217;ve designed this quiz to give you the freedom to solve this however you see fit, the only stipulation is that you stick to Ruby!
  </p>
  
  <h5>
    Additional Information
  </h5>
  
  <p>
    <b>Qs.</b> Do we have to use an XML parser?
  </p>
  
  <p>
    <b>Ans.</b> Well, no, but it will probably be easier if you do.
  </p>
  
  <p>
    <b>Qs.</b> Is it okay to assume that the source file has only first names and last names? It has no other data, e.g. ages, sexes, &#8230; ?
  </p>
  
  <p>
    <b>Ans.</b> In this example there are only 2 fields that you need to worry about. Bonus points go to the results that can handle multiple formats with multiple fields. Of course, any file that has 3 fields in the source, should be outputting 3 fields in the result.
  </p>
  
  <p>
    <b>Qs.</b> Is it necessary to indent output data (result xml)?
  </p>
  
  <p>
    <b>Ans.</b> The results may ignore whitespace outside of elements but not inside.
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
      <b>You should post your entries before midnight of 26th Apr. 2010 (Indian Standard Time). No new solutions will be accepted from 27th Apr. onwards.</b>
    </li>
    <li>
      On 27th Apr. 2010 all the solutions will be thrown open for everyone to see and comment upon.
    </li>
    <li>
      The winning entries will be announced on this blog before 30th Apr. 2010. The winners will be sent their prizes by email.
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
      <a href="http://www.boxedup.com/">Jamie van Dyke</a>.
    </li>
    <li>
      Sponsors <strong>Eden Development</strong> and <strong>Backup My App</strong>.
    </li>
    <li>
      <a href="http://github.com/">GitHub</a>, for giving us access to a private repository on GitHub to store all the submitted solutions.
    </li>
    <li>
      The RubyLearning team, namely Satoshi Asakawa (Japan) and Victor Goff III (USA).
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
      Richard Colley, Australia
    </li>
    <li style="color:#0000FF;">
      <b>Paul Barry, USA &#8211; declared winner (best solution)</b>
    </li>
    <li style="color:#0000FF;">
      John Prince, USA &#8211; declared winner (randomly selected)
    </li>
    <li style="color:#0000FF;">
      Tanzeeb Khalili, Canada &#8211; declared winner (randomly selected)
    </li>
    <li>
      Rémy Coutable, France
    </li>
    <li style="color:#0000FF;">
      Adam Lum, USA &#8211; declared winner (randomly selected)
    </li>
    <li>
      Vijay Thiruvallur, India
    </li>
    <li>
      Benoit Daloze, Belgium
    </li>
  </ol>
  
  <h4>
    Just for Fun
  </h4>
  
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
      <b>Paul Barry</b> from USA (his <a href="https://gist.github.com/9575443f97f8f09bf104">Ruby Challenge solution</a>) &#8211; the person with the best and most creative Ruby solution. He wins any <b>one</b> of PeepCode’s <a href="http://peepcode.com/screencasts/ruby-on-rails">Ruby on Rails screencasts</a> and a free 10 GB account for a year from <a href="http://backupmyapp.com/">Backup My App</a>.
    </li>
    <li>
      <b>Adam Lum</b> from USA, <b>John Prince</b> from USA and <b>Tanzeeb Khalili</b> from Canada win any <b>one</b> of Pragmatic’s <a href="http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming">The Ruby Object Model and Metaprogramming screencasts</a>.
    </li>
    <li>
      <b>All the participants in this challenge (except Paul Barry who gets a free 10 GB account for a year) will get a free 5 GB account for 6 months from <a href="http://backupmyapp.com/">Backup My App</a></b>.
    </li>
  </ul>
  
  <h3>
    Previous Challenge
  </h3>
  
  <p>
    <a href="http://rubylearning.com/blog/2010/02/23/rpcfn-broadsides-7/">RPCFN: Broadsides (#7)</a> by James Edward Gray II.
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
      The (#9) challenge by <b>Avdi Grimm, USA</b> is scheduled for 1st May 2010.
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>, <a href="http://technorati.com/tag/Ruby+Programming+Challenge+For+Newbies" rel="tag">Ruby Programming Challenge For Newbies</a>, <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/RPCFN" rel="tag">RPCFN</a>, <a href="http://technorati.com/tag/Jamie+van+Dyke" rel="tag">Jamie van Dyke</a>
