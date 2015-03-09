---
title: 'Happynerds - Programming Links for Kids'
author: Satish Talim
date: 2009-12-21
layout: post
permalink: /2009/12/21/happynerds-programming-links-for-kids/
thesis_description:
  - Michael Kohl talks about how he created Happynerds, an online resource of programming tools for kids.
thesis_keywords:
  - Ruby,The Ruby Programming Language,Happynerds,Michael Kohl
categories:
  - heroku
  - ruby
  - sinatra
tags:
  - happynerds
  - michael kohl
  - ruby
  - the ruby programming language
---
<div>
  <h3>
    Happynerds &#8211; Programming Links for Kids
  </h3>
  
  <p>
    <b>A guest post by <a href="http://citizen428.net">Michael Kohl</a></b>.
  </p>
  
  <p class="block">
    <img class="alignright" title="Michael Kohl" src="http://rubylearning.com/images/michael_kohl.jpg" alt="Michael Kohl" />For quite some time I was planning to create an online resource of programming tools for kids, because I think developing software is a beautiful and rewarding experience which is a perfect fit for children&#8217;s natural curiosity. Alas time is always short, so up until recently all I did was to collect links on <a href="http://delicious.com">delicious</a> and wait.
  </p>
  
  <p>
    Then two weeks ago I went through my personal todo list and realized that this idea has been sitting around for way too long, so I decided to finally do something about it. Thanks to the wonderful tools the Ruby community provides us with, all it took was this initial spark of motivation and an afternoon of free time to finally create <strong><a href="http://www.happynerds.net">Happy Nerds</a></strong>.
  </p>
  
  <p>
    Happy Nerds is a very small and simple site, so it seemed like a perfect match for the wonderfully elegant <strong><a href="http://www.sinatrarb.com/">Sinatra</a></strong> DSL for web applications. I&#8217;m constantly amazed by how productive and <em>fun</em> development with Sinatra can be, especially when used together with the right tools like <strong><a href="http://github.com/rtomayko/shotgun">Shotgun</a></strong> and <strong><a href="http://haml-lang.com/">Haml</a></strong>.
  </p>
  
  <p>
    Before starting to code I obviously also had to decide where to host the site once it&#8217;s finally done, and <strong><a href="http://heroku.com/">Heroku</a></strong> just seemed like the most natural choice, due to its excellent support for everything related to Ruby web frameworks (Need gems? <a href="http://docs.heroku.com/gems">No problem!</a>), a very streamlined <a href="http://git-scm.com/">git</a>-based workflow and excellent command line tools. I also wrote a patch to add the &#8211;heroku option to <a href="http://github.com/quirkey/sinatra-gen">sinatra-gen</a> a while back, so I was literally up and running within seconds.
  </p>
  
  <p>
    Now all that was left to decide was the data store. <strong><a href="http://www.mongodb.org/">MongoDB</a></strong> had been on my radar for a long time and I got myself an invite to <a href="http://www.mongohq.com/">MongoHQ</a>&#8216;s beta program some weeks back, so this seemed like a good opportunity to finally give both of them a try. As it turned out, they are as fun to work with all the other projects mentioned so far!
  </p>
  
  <p>
    Once I decided which exact tools to use, creating the actual application was almost too easy. I started by writing a small Ruby script which fetched the appropriately tagged bookmarks from delicious (where I stored name, URL and description) and fed them into MongoDB. After that all it took was a couple of very simple Sinatra &#8220;controllers&#8221; and the actual views, which thanks to Haml also were breeze to create.
  </p>
  
  <p>
    So even as somebody who usually doesn&#8217;t do web application development, I had a first functioning version within an afternoon and a finished site within two. Granted, <a href="http://www.happynerds.net">Happy Nerds</a> is very simple at the moment, but I just wanted to finally get the idea out into the open. I do have a couple of ideas for the future though and thanks to the used technologies I feel confident that implementing them will be easy and fun once I get around to do it!
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>, <a href="http://technorati.com/tag/Happynerds" rel="tag">Happynerds</a>, <a href="http://technorati.com/tag/Michael+Kohl" rel="tag">Michael Kohl</a>
