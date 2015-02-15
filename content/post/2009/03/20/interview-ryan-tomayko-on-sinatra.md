---
title: 'Interview: Ryan Tomayko on Sinatra'
author: Satish Talim
date: 2009-03-20
layout: post
permalink: /2009/03/20/interview-ryan-tomayko-on-sinatra/
keywords:
  - Ryan Tomayko,Interviews,Ruby,Sinatra,The Ruby Programming Language
description:
  - Ryan Tomayko key developer for Sinatra talks to RubyLearning on Sinatra micro web-framework.
topsy_short_url:
  - http://bit.ly/9BJIZX
categories:
  - Heroku
  - Interview
  - Ruby
  - Sinatra
tags:
  - interviews
  - Ruby
  - Ryan Tomayko
  - Sinatra
  - The Ruby Programming Language
---
<div>
  <p class="alert">
    On the eve of the first ever online &#8220;<strong>Introduction to Sinatra</strong>&#8221; course, Satish Talim of RubyLearning caught up with <strong>Ryan Tomayko</strong> and talked to him on <strong>Sinatra</strong>, in this interview.
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/RyanTomayko.jpg" alt="Ryan Tomayko, USA" title="Ryan Tomayko, USA" width="125" height="125" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Welcome, Ryan and thanks for taking out time to share your thoughts. For the benefit of the readers, could you tell us something about your self?</span>
  </p>
  
  <p>
    <strong>Ryan Tomayko>></strong> My background is in systems design and general web architecture &#8212; HTTP, REST, and &#8220;web services&#8221; primarily. I&#8217;ve been involved in the Ruby web development community for a little over three years and have contributed to Rails, Rack, Sinatra, and a bunch of other tools and libraries. I live, work, and play in San Francisco, am happily married, and have two crazy kids with totally awesome websites (<a href="http://lydia.tomayko.com/">http://lydia.tomayko.com/</a> and <a href="http://elijah.tomayko.com/">http://elijah.tomayko.com/</a>).
  </p>
  
  <p>
    You can follow me on Twitter (<a href="http://twitter.com/rtomayko">http://twitter.com/rtomayko</a>) and find out more about me at my blog (<a href="http://tomayko.com/about">http://tomayko.com/about</a>).
  </p>
  
  <blockquote class="right">
    <p>
      Sinatra&#8217;s greatest strength is its flexibility
    </p>
  </blockquote>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> You are one of the lead developers of Sinatra and work at Heroku. How come you got involved with Sinatra? Tell us more about this.</span>
  </p>
  
  <p>
    <strong>Ryan>></strong> I&#8217;ve been an advocate for standards based web development for quite some time, with a particular focus on server-side web frameworks. In 2005, I wrote an article titled &#8220;On HTTP Abuse&#8221; (<a href="http://tomayko.com/writings/on-http-abuse">http://tomayko.com/writings/on-http-abuse</a>) to make the case that the tools we were using to build web applications were basically&#8230; horrible. I also outlined some of the traits I felt would be present in a good web framework. We&#8217;ve made a lot of progress since then (Rails, for instance, has fully embraced REST and HTTP), but when I saw what Blake Mizerany had put together in Sinatra, I was blown away by how closely it resembled the framework I had imagined in my head when I was writing that article in 2005.
  </p>
  
  <p>
    I was hooked and have been fairly active in the project ever since.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> What&#8217;s your role at Heroku?</span>
  </p>
  
  <p>
    <strong>Ryan>></strong> I&#8217;ve been going under the working title of &#8220;Product Designer / Architect&#8221; but we like to think of ourselves as curators of technology more than anything. My job is to understand where the Ruby community is going, to play with the tools and technologies people are using to get there, and then to make it an order of magnitude easier for them to be used on Heroku than anywhere else <img src="http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> So many Ruby-based web frameworks &#8211; is this good for Ruby?</span>
  </p>
  
  <p>
    <strong>Ryan>></strong> I can&#8217;t think of a better situation than the one we have now, to be honest. Rails is the premier general purpose web development platform &#8211; perfectly suited to a wide range of applications. It&#8217;s taken many of the best practices established by not only the Ruby community but the web development community in general and made them accessible to everyone. It&#8217;s maturing rapidly, is well documented, and has a large (but not too large!) community. Rails has become a &#8220;safe bet&#8221;.
  </p>
  
  <p>
    The web is very young, though. There&#8217;s still a lot of stuff we&#8217;ve yet to figure out. Frameworks like Merb, Ramaze, Camping, Waves, etc. have a bit more freedom to experiment with alternative designs and philosophies or to focus more narrowly on achieving specific goals that might be off the radar for Rails. There&#8217;s very little downside to competition here (the talk about Rails vs. Merb &#8220;tearing the community apart&#8221; was mostly overblown in my estimation). Without this diversity, web development in Ruby might stagnate a bit.
  </p>
  
  <p>
    Sinatra is unique in many ways. In my opinion, Rails and Sinatra aren&#8217;t really competitors in any kind of head-to-head sense. Once you&#8217;ve become familiar with both environments, I think you&#8217;ll find that each has a clear sweet spot and that choosing one over the other is all about using the best tool for the job. It&#8217;s hammer vs. saw as opposed to Craftsmen vs. Stanley. Using Sinatra to build a traditional CRUD app with 10-15 models and a mostly-HTML-with-some-Ajax front-end is going to feel a bit wonky compared to Rails. Conversely, using Rails as the server component in a collaborative, browser-based map/reduce system (<a href="http://www.igvita.com/2009/03/03/collaborative-map-reduce-in-the-browser/">http://www.igvita.com/2009/03/03/collaborative-map-reduce-in-the-browser/</a>) is going to feel like overkill. Look at some of the apps in the wild that were built with Sinatra (<a href="http://www.sinatrarb.com/wild.html">http://www.sinatrarb.com/wild.html</a>) and imagine what they might look like if they had been implemented in Rails. I think the distinction is clear and the benefits of having multiple specialized frameworks obvious.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> For a person new to web development, how can one go about learning Sinatra? </span>
  </p>
  
  <p>
    <strong>Ryan>></strong> For a person just starting out with web development in general, I&#8217;d suggest something extremely simple and well-understood &#8211; a blog or TODO list, maybe. Choose something that has a lot of prior art so you can reference how the different resources are linked together and how the browser and server interact. One thing that sets Sinatra apart from most web frameworks is that it does not try to hide the web&#8217;s basic concepts and protocols from the developer. We believe that a strong understanding of HTTP, URLs, and the various media types/formats (HTML, CSS, JSON/JavaScript, RSS, etc) that make the web work is required to build good web applications. The more you get comfortable with those concepts, the more Sinatra will make sense to you.
  </p>
  
  <p>
    Once you know what you want to build, the only thing to do is to start writing code &#8211; one line at a time. The Sinatra website has a good introduction (<a href="http://www.sinatrarb.com/intro.html">http://www.sinatrarb.com/intro.html</a>) that covers most of the basic features supported by framework at a high level. From there, you might move on to some of the more detailed documentation (<a href="http://www.sinatrarb.com/documentation.html">http://www.sinatrarb.com/documentation.html</a>) or watch the &#8220;Classy Web Development with Sinatra&#8221; screencasts (<a href="http://www.pragprog.com/screencasts/v-aksinatra/classy-web-development-with-sinatra">http://www.pragprog.com/screencasts/v-aksinatra/classy-web-development-with-sinatra</a>).
  </p>
  
  <p>
    This part is important. Eventually, you&#8217;re going to run into a problem that you don&#8217;t know how to solve or something that doesn&#8217;t make any sense at all. When that happens, be sure to either send something to the Sinatra mailing list (<a href="http://groups.google.com/group/sinatrarb">http://groups.google.com/group/sinatrarb</a>) or drop by #sinatra on irc.freenode.net. There&#8217;s a large group of insanely smart developers that are more than happy to help out. It doesn&#8217;t matter how &#8220;stupid&#8221; the problem is &#8211; just ask. This is actually a very real way of contributing to the project. Those discussions are archived and searchable via Google so, by asking, you make it easier for the next person to find their way when they have a problem.
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/sinatralogo.jpg" alt="Sinatra Icon" title="Sinatra micro-framework" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Where all can Sinatra be used? What kind of projects should a person learning Sinatra work on?</span>
  </p>
  
  <p>
    <strong>Ryan>></strong> Sinatra is a perfect fit for smaller apps/services, APIs, and sites that are mostly static but with some light server interactions. There&#8217;s a big list of Sinatra apps on the website (<a href="http://www.sinatrarb.com/wild.html">http://www.sinatrarb.com/wild.html</a>), most of which have source code available on the GitHub.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Any plans on writing a book on Sinatra?</span>
  </p>
  
  <p>
    <strong>Ryan>></strong> Book?! We&#8217;re still working on the README! <img src="http://rubylearning.com/blog/wp-includes/images/smilies/icon_wink.gif" alt=";)" class="wp-smiley" />
  </p>
  
  <p>
    There&#8217;s a community effort underway to produce a free, online book that&#8217;s coming along quite nicely: <a href="http://www.sinatrarb.com/book.html">http://www.sinatrarb.com/book.html</a>.
  </p>
  
  <p>
    As for me personally, I don&#8217;t own a single tech book so it would seem unusual for me to produce one. I wouldn&#8217;t be surprised if someone else put a book together at some point in the near future, though.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Since you are closely involved with both Sinatra and Heroku and most of the course participants have no Rails background, could you tell us in simple terms how one can deploy a simple Sinatra CRUD app on Heroku?</span>
  </p>
  
  <p>
    <strong>Ryan>></strong> How about a quick and dirty wiki?
  </p>
  
  <ol>
    <li>
      Sign up for a Heroku account at: <a href="http://heroku.com/">http://heroku.com/</a>
    </li>
    <li>
      Install the heroku gem on your local machine (this will also install the Sinatra, Sequel, and Sqlite3-ruby gems as dependencies):<br /><code>$ sudo gem install heroku</code>
    </li>
    <li>
      Create a directory for the wiki app and initialize a git repository:<br /><code>$ mkdir wiki&lt;br />$ cd wiki&lt;br />$ git init&lt;br />Initialized empty Git repository in .git/</code>
    </li>
    <li>
      Create a new heroku application. You will be prompted for your heroku email address and password (this is required the first time you create an app only):<br /><code>$ heroku create&lt;br />Enter your Heroku credentials&lt;br />Email: joe@example.com&lt;br />Password:&lt;br />Uploading ssh public key /Users/joe/.ssh/id_rsa.pub</code> <p>
        The final bit of output from the create command will be something like this:<br /><code>Created http://quiet-snow-81.heroku.com/ | git@heroku.com:quiet-snow-81.git&lt;br />Git remote heroku added</code>
      </p>
      
      <p>
        The app has been created and two URLs are provided: one for the web face of your new app, and one for the remote git repository. A git remote named &#8220;heroku&#8221; is added for you automatically &#8212; we&#8217;ll push to this remote when it&#8217;s time to deploy in step #7.</li> 
        
        <li>
          Create wiki.rb and config.ru files based on the following examples:<br /><a href="https://gist.github.com/8ff54cdfd44e1a6485e2">https://gist.github.com/8ff54cdfd44e1a6485e2</a> <p>
            You can start a development server to test locally. The site is available at <a href="http://localhost:4567/">http://localhost:4567/</a>
          </p>
          
          <p>
            <code>$ ruby wiki.rb&lt;br />== Sinatra/0.9.1.1 has taken the stage on 4567 for development</code></li> 
            
            <li>
              Commit the wiki.rb and config.ru files to the git repository:<br /><code>$ git add wiki.rb config.ru&lt;br />$ git commit -m 'initial commit of simple sinatra wiki'</code>
            </li>
            <li>
              Deploy the application to Heroku and open a browser:<br /><code>$ git push heroku master&lt;br />$ heroku open</code>
            </li>
            <li>
              Lather, rinse, repeat <img src="http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" /> Be sure to see the Heroku documentation (<a href="http://heroku.com/docs/">http://heroku.com/docs/</a>) for more information.
            </li></ol> 
            
            <p>
              <span style="color:#CC3333;"><strong>Satish>></strong> Do you have any suggestions for RubyLearningâ€™s &#8220;Introduction to Sinatra&#8221; course participants?</span>
            </p>
            
            <p>
              <strong>Ryan>></strong> Have fun!
            </p>
            
            <p>
              <span style="color:#CC3333;"><strong>Satish>></strong> Thanks Ryan for sharing your views with the <strong>Introduction to Sinatra<sup class='footnote'><a href='#fn-1739-1' id='fnref-1739-1'>1</a></sup></strong> &#8221; and &#8221; <strong>Introduction to Merb<sup class='footnote'><a href='#fn-1739-2' id='fnref-1739-2'>2</a></sup></strong> &#8221; course participants.</span>
            </p>
            
            <p>
              <span style="font-size: 8pt; font-family: Arial;"><i><strong>Disclaimer:</strong></i></span><br /><span style="font-size: 8pt; font-family: Arial;"><i>The opinions expressed are those of Ryan Tomayko and do not necessarily reflect those of <strong><a href="http://rubylearning.org/">RubyLearning.org</a></strong>.</i></span>
            </p></div> 
            
            <p>
              Technorati Tags: <a href="http://technorati.com/tag/Ryan+Tomayko" rel="tag">Ryan Tomayko</a>, <a href="http://technorati.com/tag/Interviews" rel="tag">Interviews</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Sinatra" rel="tag">Sinatra</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>
            </p>
            
            <div class='footnotes'>
              <div class='footnotedivider'>
              </div>
              
              <ol>
                <li id='fn-1739-1'>
                  <strong>Introduction to Sinatra</strong>: Here are the <a href="http://rubylearning.com/blog/2009/02/25/introduction-to-sinatra-a-new-course/">course details</a>. <span class='footnotereverse'><a href='#fnref-1739-1'>&#8617;</a></span>
                </li>
                <li id='fn-1739-2'>
                  <strong>Introduction to Merb</strong>: Here are the <a href="http://rubylearning.com/blog/2009/03/02/introduction-to-merb-3rd-batch/">course details</a>. <span class='footnotereverse'><a href='#fnref-1739-2'>&#8617;</a></span>
                </li>
              </ol>
            </div>
