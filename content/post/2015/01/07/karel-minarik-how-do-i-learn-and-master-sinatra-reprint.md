---
title: 'Karel Minarik: How do I learn and master Sinatra? (Reprint)'
author: Satish Talim
date: 2015-01-07
layout: post
permalink: /2015/01/07/karel-minarik-how-do-i-learn-and-master-sinatra-reprint/
thesis_description:
  - In the fourth part of the mini series "How do I learn and master Sinatra?", Karel Minarik gives us his insights on mastering Sinatra.
thesis_keywords:
  - Karel Minarik,Sinatra,Ruby programming,Learning Sinatra
topsy_short_url:
  - http://bit.ly/1xQPAGA
categories:
  - Beginners
  - Interview
  - Learn Sinatra
  - Ruby
  - Ruby Masters
  - Sinatra
tags:
  - Karel Minarik
  - Learning Sinatra
  - ruby programming
  - Sinatra
---
<div>
  <p>
    <b>Note</b>: This is reprint of the blog post that appeared on 13th July 2009, as the original is not accessible.
  </p>
  
  <p class="update">
    Welcome to the <b>fourth</b> installment on the <abbr title="RubyLearning">RL</abbr> blog, of a mini series &#8211; &#8220;<strong>How do I learn and master Sinatra?</strong>&#8221; &#8211; by top Rubyists using <em>Sinatra</em>. The interview series will provide insight and commentary from these notable <em>Sinatra</em> developers, with the goal of facilitating and providing answers to the questions Ruby beginners face on <em>how to learn and master Sinatra</em>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Karel Minarik, could you tell us something about yourself &#8211; your background, where you are based?</span>
  </p>
  
  <p class="block">
    <img class="alignright" title="Karel Minarik" src="http://www.rubylearning.com/images/karmi_mugshot.jpg" alt="Karel Minarik" /><strong>Karel Minarik>></strong> I&#8217;m Karel Minarik, web designer and developer living in Prague, Czech Republic. I have graduated in Philosophy, not Computer Science, which may explain why I love Ruby a lot, and why I prefer solving &#8220;naming things&#8221; over &#8220;cache invalidation&#8221; problems. I earn my bread by designing interfaces, writing Ruby, JavaScript, HTML/CSS and giving people advice or teaching them new tricks. I blog in undecipherable intervals on <a href="http://www.restafari.org/">Restafari.org</a> and publish code regularly at <a href="http://github.com/karmi/">Github</a>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Are there any pre-requisites for a person to start learning Sinatra?</span>
  </p>
  
  <p>
    <strong>Karel>></strong> Very few: you just need to know Ruby a little bit. The rest you can and will learn along the way. In fact, <span style="background-color: #FFFFCC;">Sinatra is wonderful teaching tool to deepen your knowledge of Ruby as a general programming language, web application architectures, HTTP and REST principles, concept of middlewares, and so on</span>. As a wonderful teaching/learning tool it&#8217;s truly on par with _why&#8217;s Shoes.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How should one start learning Sinatra?</span>
  </p>
  
  <p>
    <strong>Karel>></strong> You should start with the <a href="http://github.com/sinatra/sinatra/blob/master/README.rdoc">README</a>, which contains almost everything you need to know in its 500 or so lines. Then you should definitely glance over sourcecode of some Sinatra applications &#8220;<a href="http://www.sinatrarb.com/wild.html">in the wild</a>&#8220;.
  </p>
  
  <p>
    Some of the noteworthy examples would be eg. simple website in waferbaby&#8217;s <a href="http://github.com/waferbaby/usesthis/tree/master">usesthis</a>, background processing tutorial in bmizerany&#8217;s <a href="http://github.com/bmizerany/sinatra-dj/tree/master">sinatra-dj</a>, clever use of Ruby&#8217;s blocks/closures in pjhyett&#8217;s <a href="http://github.com/pjhyett/github-services/tree/master">github-services</a> or ultra minimal apps in ichverstehe&#8217;s <a href="http://github.com/ichverstehe/gaze/blob/master/bin/gaze">gaze</a> or gnugeek&#8217;s <a href="http://github.com/gnugeek/tophat/tree/master">tophat</a>. These examples really elucidate compact and minimal nature of Sinatra.
  </p>
  
  <p>
    Then you should sketch something rather small and well defined: web frontend for some Ruby code you have, a web API for some of your services, &#8230;
  </p>
  
  <blockquote class="right">
    <p>
      Sinatra &#8211; quickly create tiny web apps and services
    </p>
  </blockquote>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Which area of Sinatra should a beginner pay particular attention to?</span>
  </p>
  
  <p>
    <strong>Karel>></strong> Beginners should pay attention to Sinatra&#8217;s DSL itself: helpers, filters, last_modified and etag support, etc, so they&#8217;re not reinventing the mic and truly make use of it&#8217;s API. More advanced programmers should focus on Rack integration, using Rack middlewares such as <b>Rack::Auth</b> or <b>Rack::Mime</b> in your Sinatra app and running Sinatra apps themselves as middlewares. This opens different possibilities of service integration &#8211; have a look on Jon Crosby&#8217;s wonderful explanation in his <a href="http://mwrc2009.confreaks.com/13-mar-2009-11-05-in-a-world-of-middleware-who-needs-monolithic-applications-jon-crosby.html">MWRC talk</a>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is the official documentation on Sinatra good enough for a beginner? Are there areas which need improvement or need to be re-written</span>
  </p>
  
  <p>
    <strong>Karel>></strong> Sinatra&#8217;s <a href="http://www.sinatrarb.com/documentation.html">documentation</a> is pretty extensive at the moment, covering everything from basics to testing your applications and writing extensions. It&#8217;s just a bit scattered at the moment, eg. deployment is covered in the <a href="http://www.sinatrarb.com/book.html#deployment">Sinatra Book</a> started by Chris Schneider. There&#8217;s still some lack of thorough documentation about Rack integration.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Sequel, DataMapper, ActiveRecord &#8211; which one would you recommend to use with Sinatra and why?</span>
  </p>
  
  <p>
    <strong>Karel>></strong> I prefer ActiveRecord for anything talking to a relational database, because of it&#8217;s clever API, stability, general knowledge and large user base. Don&#8217;t forget that Sinatra is nice playground for experiments with other ORM&#8217;s, key/value stores, etc, though!
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/sinatralogo.jpg" alt="Sinatra Icon" title="Sinatra micro-framework" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Is an understanding of Rack important while learning Sinatra? Why? Which area of Rack should one be really comfortable with?</span>
  </p>
  
  <p>
    <strong>Karel>></strong> No, you could start learning Sinatra completely oblivious of something called &#8220;Rack&#8221;.
  </p>
  
  <p>
    However, you can use plethora of various <a href="http://rack.rubyforge.org/doc/Rack.html">bundled</a> or <a href="http://github.com/rack/rack-contrib">third-party</a> Rack middlewares very easily by simple &#8216;<b>use Rack::Utils</b>&#8216; or &#8216;<b>use Rack::Locale</b>&#8216; declaration for adding some advanced functionality to your application.
  </p>
  
  <p>
    And when you plan to plug Sinatra powered app into a Rails one, for instance, or want to &#8220;mount&#8221; various separated web applications at different endpoints, you should definitely have a detailed look on Rack itself.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How should one hone one&#8217;s skills in Sinatra?</span>
  </p>
  
  <p>
    <strong>Karel>></strong> By reading huge amounts of code available on Github. That&#8217;s a sure way how to discover clever solutions and open your mind. (Be sure to include credits if you reuse some code and release your stuff, though.)
  </p>
  
  <p>
    But the most important thing is to focus on Ruby as an expressive programming language, and to _not_ think about browser first. Think first about the domain of your application and how it translates to Ruby, not about how it should &#8220;look&#8221; or behave in a browser. That&#8217;s very important, but comes next. And don&#8217;t forget it&#8217;s really easy to code test-first in Ruby and in Sinatra.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> What type of projects should a beginner work on to gain more expertise in Sinatra?</span>
  </p>
  
  <p>
    <strong>Karel>></strong> Smallish apps, where Rails would force it&#8217;s conventions on you or which are not primarily focused on database access. Something like cschneid&#8217;s <a href="http://irclogger.com/">irclogger</a>, quirkey&#8217;s <a href="http://log.quirkey.com/">columnlog</a> or entp&#8217;s <a href="http://calendaraboutnothing.com/">Calendar About Nothing</a> &#8212; all very tight, minimal and very elegant apps.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Could you suggest some web services that a Sinatra beginner could develop himself / herself?</span>
  </p>
  
  <p>
    <strong>Karel>></strong> The sweet spot for Sinatra is something along the lines of already mentioned apps. Some ideas I could throw in:
  </p>
  
  <ul>
    <li>
      An app to display metrics about your team activity in a Git repository: who commited most, who commited most lines of code, etc., leveraging power of <a href="http://github.com/mojombo/grit">Grit</a>.
    </li>
    <li>
      A web frontend for some command-line tool like &#8216;top&#8217; or &#8216;df&#8217; for your servers.
    </li>
    <li>
      Simple web hook for <a href="http://github.com/guides/post-receive-hooks">Github&#8217;s post-receive hooks</a>, notifiying your developer mailing-list, Jabber, deploying new code to staging server or playing a tune.
    </li>
    <li>
      More advanced example could be an app to show currently deployed versions of your applications, using small Sinatra apps on each host to emit various metrics like deployed revision and it&#8217;s age, system load, etc in JSON and a Sinatra app to gather the data &#8212; &#8220;emulating&#8221; services like NewRelic, Scout or FiveRun&#8217;s Dash.
    </li>
  </ul>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Anything else you would like to add?</span>
  </p>
  
  <p>
    <strong>Karel>></strong> Do come to the #sinatra IRC channel on Freenode when you get stuck. There&#8217;s usually lots of people from different timezones, so it&#8217;s very likely that we&#8217;ll get you out of trouble fast. Just please read the README first and don&#8217;t name your application file &#8220;sinatra.rb&#8221; <img src="http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" /> Have fun with Ruby and Sinatra!
  </p>
  
  <p>
    <span style="color:#CC3333;"><em>Thank you Karel. In case you have any queries and/or questions, kindly post your questions here (as comments to this blog post) and Karel would be glad to answer.</em></span>
  </p>
  
  <p>
    <b>Others in this series:</b>
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/blog/2015/01/07/corey-donohoe-how-do-i-learn-and-master-sinatra/">Corey Donohoe</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2009/07/08/jeremy-evans-how-do-i-learn-and-master-sinatra/">Jeremy Evans</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2009/07/10/graham-ashton-how-do-i-learn-and-master-sinatra/">Graham Ashton</a>
    </li>
  </ul>
  
  <p class="alert">
    <strong><em>Post supported by 1st Easy Limited</em>:</strong> UK based 1st Easy Limited offer Sinatra and Rails hosting running on a Phusion Passenger (mod_rails) and LAMP stack. If you want to try your hand at developing with Sinatra, why not let them arrange a <a href="http://www.1steasy.com/ruby-on-rails.htm#try">trial hosting account</a> for you? You&#8217;ll get to deploy your app, with full technical support from their team!
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Karel+Minarik" rel="tag">Karel Minarik</a>, <a href="http://technorati.com/tag/Sinatra" rel="tag">Sinatra</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>, <a href="http://technorati.com/tag/Learning+Sinatra" rel="tag">Learning Sinatra</a>
