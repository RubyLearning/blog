---
title: '20+ Rubyists are using Sinatra &#8211; Do you? (Reprint)'
author: Satish Talim
date: 2015-01-07
layout: post
permalink: /2015/01/07/20-rubyists-are-using-sinatra-do-you-reprint/
thesis_description:
  - '20+ Rubyists are using Sinatra - Do you?'
thesis_keywords:
  - Rubyists Using Sinatra,Ruby Programming,Rubyists,Sinatra
topsy_short_url:
  - http://bit.ly/1HLdtAP
categories:
  - Beginners
  - Ruby
  - Sinatra
tags:
  - ruby programming
  - Rubyists
  - Rubyists Using Sinatra
  - Sinatra
---
<div>
  <p>
    <b>Note</b>: This first appeared on 29th June 2009 and is being reprinted as the original is not accessible.
  </p>
  
  <h3>
    20+ Rubyists are using Sinatra &#8211; Do you?
  </h3>
  
  <p class="update">
    With <strong>Sinatra</strong> you can quickly create your own tiny web-applications in Ruby and write lots of small services. RubyLearning caught up with some Rubyists working with Sinatra and asked them as to why, how and where they use <em>Sinatra</em>.
  </p>
  
  <p class="block">
    <img class="alignright" title="Aaron Quint" src="http://rubylearning.com/images/AaronQuint.jpg" alt="Aaron Quint" /><strong><a href="http://twitter.com/aq">Aaron Quint</a>>></strong> I&#8217;ve been using Sinatra all over the place. With <a href="http://code.quirkey.com/vegas/">Vegas</a> I&#8217;ve been using it as a way to provide simple web interfaces to existing code. I&#8217;ve also been using it to prototype new application ideas. When not using Sinatra, I&#8217;ve been using some of the same basic ideas in JavaScript with <a href="http://code.quirkey.com/sammy/">Sammy.js</a>. <span style="background-color: #FFFFCC;">In general, Sinatra is just fun to use as it provides the most direct and clean route to get an idea or a piece of code on the web</span>. <a href="http://rubylearning.com/blog/2009/03/20/interview-aaron-quint-on-sinatra/">Read Aaron&#8217;s interview on Sinatra</a>.
  </p>
  
  <p class="block">
    <img class="alignleft" title="Adam Keys" src="http://rubylearning.com/images/AdamKeys.jpg" alt="Adam Keys" /><strong><a href="http://twitter.com/therealadam">Adam Keys</a>>></strong> I’m using Sinatra for two things. For personal stuff, <span style="background-color: #FFFFCC;">I always reach for Sinatra when I want to prototype an idea. It’s easy to get something in place so I can iterate on the idea quickly. Sinatra is great for deploying prototypes too!</span>
  </p>
  
  <p>
    At FiveRuns, we use Sinatra as the API endpoint for Dash. We’ve got hundreds of clients in our public beta sending custom metrics to Dash once a minute. Sinatra has handled this load with aplomb. Further, because our API is just a few URL endpoints, <span style="background-color: #FFFFCC;">Sinatra’s minimal API is a perfect match for our needs.</span> <a href="http://rubylearning.com/blog/2009/03/03/interview-adam-keys-on-sinatra/">Read Adam&#8217;s interview on Sinatra</a>.
  </p>
  
  <p class="block">
    <img class="alignright" title="Andrew Neil" src="http://rubylearning.com/images/nelstrom-125.jpg" alt="Andrew Neil" /><strong><a href="http://twitter.com/nelstrom">Andrew Neil</a>>></strong> <a href="http://all-sorts.org/">All Sorts</a> searches Twitter every minute for the <a href="http://search.twitter.com/search?q=%23collectivenouns">#collectivenouns</a> hashtag, then parses matching tweets to identify collective nouns. The requirements were very simple &#8211; no user log in, no CRUD, only a handful of models and routes &#8211; so Sinatra was the perfect choice for this project. I took Nick Plante&#8217;s <a href="http://github.com/zapnap/retweet/tree/master">retweet</a> source as a starting point, which proved to be an excellent introduction to Sinatra and DataMapper. Part of the appeal, of course, was to dabble with new technologies. The live site runs on passenger, with Rack::Cache taking care of the caching.
  </p>
  
  <p class="block">
    <img class="alignleft" title="Bruno Miranda" src="http://rubylearning.com/images/bruno.jpg" alt="Bruno Miranda" /><strong><a href="http://twitter.com/brupm">Bruno Miranda</a>>></strong> I am using Sinatra on a url shortner app that I wrote at <a href="http://s.bopia.com/">s.bopia.com</a> as well as a proxy app that processes beanstalkd queue items for <a href="http://mx.msn.cyloop.com/">mx.msn.cyloop.com</a>. <span style="background-color: #FFFFCC;">Sinatra is a great tool to accomplish small tasks as a minimal layer on top of http protocol.</span>
  </p>
  
  <p class="block">
    <img class="alignright" title="Chris Strom" src="http://rubylearning.com/images/chris_strom.jpg" alt="Chris Strom" /><strong><a href="http://twitter.com/eee_c">Chris Strom</a>>></strong> I am using Sinatra most prominently to serve up my family&#8217;s cookbook, backed by a CouchDB store. Excruciating details on how I do this are contained in a series of blog posts starting with: <a href="http://japhr.blogspot.com/2009/03/my-chain.html">http://japhr.blogspot.com/2009/03/my-chain.htm</a>.
  </p>
  
  <p>
    I chose Sinatra because it felt close to the metal &#8212; especially important because I did not want anything interfering with CouchDB. I continue to use Sinatra because it complements my BDD workflow exceedingly well. <span style="background-color: #FFFFCC;">Sinatra&#8217;s lean DSL encourages me to produce similarly beautiful code. Sinatra never gets in my way. Sinatra goes out of its way to make my life simple.</span>
  </p>
  
  <p class="block">
    <img class="alignleft" title="Corey Donohoe" src="http://rubylearning.com/images/CoreyDonohoe.jpg" alt="Corey Donohoe" /><strong><a href="http://twitter.com/atmos">Corey Donohoe</a>>></strong> <span style="background-color: #FFFFCC;">Sinatra is great for building non-trivial rack middleware.</span> <a href="http://www.engineyard.com/">We&#8217;re mainly using Sinatra</a> for integration applications between existing pieces of software. Instead of working on a monolithic app we&#8217;re writing a fleet of microapps to handle arising business needs. We feel that Sinatra gets in the way less frequently than most other frameworks. With cucumber and good development practices we&#8217;re using the same top notch testing tools the Rails guys are using. In my <a href="http://atmos.org/index.php/about/">personal hacking</a> I&#8217;ve been using it as the basis for twitter microapps leveraging twitter&#8217;s oauth API.
  </p>
  
  <p class="block">
    <img class="alignright" title="Doug Sparling" src="http://www.rubylearning.com/images/doug_sparling.jpg" alt="Doug Sparling" /><strong><a href="http://twitter.com/scriptrunner">Doug Sparling</a>>></strong> In my former company, we had started using <em>Sinatra for web services</em> and in one instance, a small app used for mobile advertising that doesn&#8217;t use the database.
  </p>
  
  <p>
    1) <b>Why?</b> &#8211; <span style="background-color: #FFFFCC;">We don&#8217;t always need the full Rails stack, particularly with web services and anything that doesn&#8217;t require the database. It&#8217;s also useful for use with legacy databases, which we have to deal with. I can use Datamapper, which is thread safe (though I haven&#8217;t seen any performance issues with Rails, which we usually cache anyway).</span><br />2) <b>How?</b> &#8211; We use Mongrel clusters for our Rails web sites, but with the Sinatra apps we&#8217;re using Passenger. For our Sinatra web services, I use Datamapper ORM. I have one internal web service in Rails 2.3.2, but I&#8217;m looking at moving it to Sinatra as well.<br />3) <b>Where?</b> &#8211; Mostly internal web services at the moment, but I&#8217;m sure we&#8217;ll look at it for external services as well.
  </p>
  
  <p class="block">
    <img class="alignleft" title="Jeremy Evans" src="http://rubylearning.com/images/jeremy-125.jpg" alt="Jeremy Evans" /><strong><a href="http://code.jeremyevans.net/">Jeremy Evans</a>>></strong> I use Sinatra on quite a few projects, mostly for small applications. At work, we use it to handle the dynamic portion of our mostly static public website, and for some internal applications. Personally, I use it in <a href="http://github.com/jeremyevans/giftsmas/tree/master">Giftsmas</a>, my open source gift-tracking application, and in a couple of other sites I maintain.
  </p>
  
  <p>
    <span style="background-color: #FFFFCC;">I use Sinatra because it is simple and flexible. It doesn&#8217;t require boilerplate code, and lets you focus on the needs of your application.</span>
  </p>
  
  <p class="block">
    <img class="alignright" title="Graham Ashton" src="http://www.rubylearning.com/images/graham-ashton.jpeg" alt="Graham Ashton" /><strong><a href="http://grahamashton.net/">Graham Ashton</a>>></strong> I first tried Sinatra during an in house &#8220;hack week&#8221; at <a href="http://www.wordtracker.com/">Wordtracker</a> (one of my main Rails clients). We used Sinatra to great effect to throw up a user interface for a new keyword research tool that we&#8217;d come up with during hack week. <span style="background-color: #FFFFCC;">Sinatra was very accessible &#8211; the docs are well written and the mailing list is friendly. I quickly gained a lot of confidence in the framework by reading the code, which is succinct and easy to follow</span> (I wish more projects would follow the advice of the Linux kernel coding style and wrap their code at 80 columns &#8211; it encourages legibility).
  </p>
  
  <p>
    After that experience Sinatra was an obvious choice for Nesta, my <a href="http://effectif.com/nesta">file based CMS</a>. It&#8217;s a simple app and Sinatra is a perfect fit for it. I had the application up and running in a matter of days, and I really enjoyed writing it. The goal of Nesta was to build a CMS that people could easily modify to suit their own web sites, and Sinatra makes it very easy for people to do that. There&#8217;s not a lot of ceremony.
  </p>
  
  <p>
    I still use Rails for larger apps, but I&#8217;m now turning to Sinatra first whenever I want to try something out, or if I&#8217;m not sure where a new application is going. It&#8217;s more fun.
  </p>
  
  <p class="block">
    <img class="alignleft" title="Hasham Malik" src="http://rubylearning.com/images/hasham_small.jpg" alt="Hasham Malik" /><strong><a href="http://twitter.com/hasham2">Hasham Malik</a>>></strong> I have recently started development with the Sinatra micro framework while working at <a href="http://www.cambridgedocs.com/">CambridgeDocs</a>. Earlier we have used PHP / Ruby on Rails for server-side back ends of native iphone applications that we have been developing. <span style="background-color: #FFFFCC;">Sinatra lets you create REST based services with minimalistic approach which is ideal of mobile back ends. Sinatra is also lean and fast and at the same time it gives you the liberty to use whichever ORM / templating system you want.</span> Sinatra has this positive vibe among Rubyists these days with 1.0 nearing its release its great time to learn this new framework.
  </p>
  
  <p class="block">
    <img class="alignright" title="James Edward Gray II" src="http://grayproductions.net/images/james_headshot_square.jpg" alt="James Edward Gray II" /><strong><a href="http://twitter.com/JEG2">James Edward Gray II</a>>></strong> At <a href="http://highgroove.com/">Highgroove Studios</a>, Sinatra is a vital part of the architecture of our monitoring application, <a href="http://scoutapp.com/">Scout</a>. We provide the API the agents use to check-in with data via the micro framework. This is nice because it separates the two functions of the application, allowing us to do things like deploy an application update without interrupting the API service. Still <span style="background-color: #FFFFCC;">Sinatra gives us a touch more abstraction than something like Rails Metal would and that makes working on the API a little easier.</span>
  </p>
  
  <p class="block">
    <img class="alignleft" title="Jeremy Raines" src="http://rubylearning.com/images/face_small2.jpg" alt="Jeremy Raines" /><strong><a href="http://twitter.com/jraines">Jeremy Raines</a>>></strong> I&#8217;m a web developer in Park City, Utah. I got started using Sinatra because I was interested in REST and <span style="background-color: #FFFFCC;">I like the way Sinatra maps controller actions to HTTP verbs. I also love its lightweight simplicity. It&#8217;s great for doing small API based webapps and mashups.</span> Most of my Sinatra apps use Ruby scripts fired by cron jobs to pull data from other webservices into a SQLite database, and serve content with Sinatra. I&#8217;ll be using it more in my work with Purple Raincloud, a new social media consultancy here in Utah. I&#8217;m @jraines on Twitter, and my homepage is at <a href="http://jeremyraines.com/">jeremyraines.com</a>.
  </p>
  
  <p class="block">
    <img class="alignright" title="Julio Javier Cicchelli" src="http://www.rubylearning.com/images/jjcicchelli.jpg" alt="Julio Javier Cicchelli" /><strong><a href="http://twitter.com/monsieur_rock">Julio Javier Cicchelli</a>>></strong> First of all, I like the idea to write about Sinatra and, especially, to show its practical uses to the masses. There are a whole lot of Rails developers but nobody seems to be taking Sinatra quite seriously (at least, this is what I&#8217;ve been noticing in websites such as <a href="http://jobs.rubynow.com/">jobs.rubynow.com</a>).
  </p>
  
  <p>
    I&#8217;ve just founded a company called &#8220;<a href="http://rock-n-code.com/">Rock & Code</a>&#8221; in Amsterdam, The Netherlands that offers solutions developed on Sinatra (instead of Rails or even Merb) to my partners. Why you would ask? <span style="background-color: #FFFFCC;">Sinatra have definitely broken the MVC paradigm (widely implemented by frameworks such as Rails, Merb, Django, Spring, etc.) and decided to give total control back to the developer by allowing him to build almost any kind of web-based solution (no matter the complexity) in a very simple manner on top of the abstracted HTTP layer it implements from Rack. Furthermore, Sinatra applications can make use of the existing gem library instead of consuming plug-ins specifically-designed for a particular framework.</span> How my company is using Sinatra? I&#8217;m currently developing RESTful web services that uses CouchDB and communicates with clients written in both MacRuby and iPhone (in the near future) using JSON but I&#8217;ve planned to use Sinatra in web development and also server interfacing. Where can it be applied? I believe that Sinatra suits perfectly for prototyping, client-server applications, SOA applications and interfacing servers, for starters.
  </p>
  
  <p class="block">
    <img class="alignleft" title="Karel Minarík" src="http://www.rubylearning.com/images/karmi_mugshot.jpg" alt="Karel Minarík" /><strong><a href="http://twitter.com/karmiq">Karel Minarík</a>>></strong> <span style="background-color: #FFFFCC;">Sinatra</span> powers <a href="http://www.restafari.org/">my blog</a>, deployment automation, internal apps and <span style="background-color: #FFFFCC;">is generally the tool of choice whenever I need to build a web app without overhead. Sinatra excels when doing &#8220;freestyle coding&#8221; &#8212; it&#8217;s a sort of a blank canvas: you&#8217;re bound only by HTTP and your Ruby knowledge. Sinatra doesn&#8217;t force anything on you, which can lead to awesome or evil code, in equal measures &#8212; and that&#8217;s part of its charm to me. Sinatra exposes you to Rack intensely, though, which brings rather different mindset for building web applications then the prevailing &#8220;monolithic&#8221; style.</span> See eg. <a href="http://github.com/rack/rack-contrib/tree/master">www.github.com/rack/rack-contrib</a> for inspiration.
  </p>
  
  <p class="block">
    <strong><a href="http://twitter.com/cypher">Markus Prinz</a>>></strong> I use Sinatra because it concentrates on one area, and does that very well, leaving the rest up to me. So <span style="background-color: #FFFFCC;">whenever I have some idea that requires a web app, I can try it out very quickly with Sinatra with a minimum of fuss.</span> And since Sinatra is not a one-size-fits-all solution, but instead essentially a library, I have a great deal of flexibility in using it. That means I can try out new approaches to things like data storage, and use something like Tokyo Cabinet/Tokyo Tyrant or CouchDB instead of a relational database. But <span style="background-color: #FFFFCC;">I can also use Sinatra as a component in a larger application to offer a web interface, without interfering with the rest of the application.</span>
  </p>
  
  <p class="block">
    <img class="alignright" title="Matt Todd" src="http://highgroove.com/images/about/mtodd.jpg" alt="Matt Todd" /><strong><a href="http://twitter.com/mtodd">Matt Todd</a>>></strong> We at @highgroove (<a href="http://highgroove.com/">Highgroove Studios</a>) <span style="background-color: #FFFFCC;">use Sinatra in a lot of different projects for memory-efficient web services.</span> One of our products, <a href="http://scoutapp.com/">Scout</a> (@scoutapp) uses it to consume thousands of reports constantly. We are able to fine tune our stack with Sinatra to keep it minimal, responsive, and powerful.
  </p>
  
  <p>
    Highgroove Studios is Charles Brian Quinn (@seebq), Derek Haynes (@dhaynes23), Andre Lewis (@alewis), James Edward Gray II (@JEG2), and myself, Matt Todd (@mtodd).
  </p>
  
  <p class="block">
    <img class="alignleft" title="Nick Plante" src="http://www.rubylearning.com/images/nap.jpg" alt="Nick Plante" /><strong><a href="http://twitter.com/zapnap">Nick Plante</a>>></strong> We&#8217;re using Sinatra for a variety of small web sites and services. Why? Because <span style="background-color: #FFFFCC;">Sinatra is small, RESTful, fast, and intuitive. It&#8217;s perfect for lightweight apps and APIs.</span>
  </p>
  
  <p>
    One of our sites, <a href="http://rdoc.info/">rdoc.info</a>, uses it to generate and host documentation for a variety of Ruby libraries, integrating with GitHub web hooks to automatically regenerate docs whenever projects are updated. We could have used Rails, but the additional overhead, helpers, and other extras that come pre-packaged with it just weren&#8217;t necessary. In fact, they would have probably gotten in our way.
  </p>
  
  <p>
    <a href="http://tweetdreams.org/">Tweetdreams</a> is another small Sinatra-based project that we launched earlier this year. It&#8217;s a Twitter dream journal. There really isn&#8217;t much to it, which is sort of the beauty of it. The source is available on GitHub as &#8220;<a href="http://github.com/zapnap/retweet/tree/master">retweet</a>&#8221; and it&#8217;s been used as the basis for a number of other Twitter-oriented projects including the <a href="http://all-sorts.org/">http://all-sorts.org</a> linguistic experiment created by Andrew Neil.
  </p>
  
  <p>
    I should note that both of these projects use DataMapper and Haml, too. <span style="background-color: #FFFFCC;">Sinatra is ORM and templating language agnostic, which can be another bonus if you already have a predefined set of tools that you&#8217;re familiar with and want to use.</span>
  </p>
  
  <p class="block">
    <img class="alignright" title="Peter Cooper" src="http://www.rubylearning.com/images/petercooper.jpg" alt="Peter Cooper" /><strong><a href="http://twitter.com/peterc">Peter Cooper</a>>></strong> As I don&#8217;t work on big projects, I&#8217;m using Sinatra for everything now, where I would have used Rails before. It&#8217;s nearly all local or private stuff for now but I&#8217;d like to be able to release more community projects using it in due course. <span style="background-color: #FFFFCC;">I love Sinatra because it&#8217;s less opinionated and more Ruby-like than Rails. It might take me a little longer to achieve certain results but I can &#8220;plug and play&#8221; code, libraries, and frameworks wherever I like with it, rather than have to work around tightly coupled &#8220;conventions.&#8221;</span>
  </p>
  
  <p class="block">
    <img class="alignleft" title="Piyush Gupta" src="http://www.rubylearning.com/images/PiyushGupta.jpg" alt="Piyush Gupta" /><strong><a href="http://twitter.com/mba_piyush">Piyush Gupta</a>>></strong> When your application is small, Sinatra helps us to develop applications quickly and easily. <span style="background-color: #FFFFCC;">Sinatra is easy to understand and follow.</span> We have recently used it for a twitter mashup called MillionTwitter Follower which is not yet live. Expecting it to be live soon.
  </p>
  
  <p class="block">
    <img class="alignright" title="Sam Goebert" src="http://www.rubylearning.com/images/sam.jpg" alt="Sam Goebert" /><strong><a href="http://twitter.com/bigcurl">Sam Goebert</a>>></strong> <a href="http://www.bigcurl.de/">Bigcurl</a> uses Sinatra to power its <a href="http://www.httpush.com/">HTTPush API</a>, which is a hosted gateway to the Apple Push Notification Service. Our complete api frontend is implemented using Sinatra. This gave us a tremendous boost during development of the API specification. We were able to experiment more as the code has very few lines. Second reason we went with Sinatra was memory consumption, since we span lot of instances over the course of a day this was crucial to get the maximum out of a machine but maintaining the beauty in code.
  </p>
  
  <p class="block">
    <img class="alignleft" title="Sau Sheong Chang" src="http://www.rubylearning.com/images/sau.jpg" alt="Sau Sheong Chang" /><strong><a href="http://twitter.com/sausheong">Sau Sheong Chang</a>>></strong> I picked up Sinatra first when I was writing my <a href="http://blog.saush.com/2009/03/write-an-internet-search-engine-with-200-lines-of-ruby-code/">search engine</a> and I was looking for a simple way to write my search engine interface. The simplicity of Sinatra blew me away and I was soon knee-deep into writing more apps on Sinatra. After a few more applications, I was convinced that <span style="background-color: #FFFFCC;">Sinatra is the way to write web applications as it is meant to be.</span> Today I use it to write quick and simple web applications, often in combination with DataMapper, that serve as front-end interfaces for larger systems.
  </p>
  
  <p class="block">
    <img class="alignright" title="Saurabh Purnaye" src="http://www.rubylearning.com/images/saurabhpurnaye.jpg" alt="Saurabh Purnaye" /><strong><a href="http://twitter.com/saurabhp">Saurabh Purnaye</a>>></strong> I work for Synechron, Pune. The applications we create are mostly UI based (html/css/jquery and flex), and I need web services to respond to the calls from UI &#8211; that&#8217;s where I use Sinatra. <span style="background-color: #FFFFCC;">Sinatra is really fast and easy for providing RESTful web service solutions.</span> There are many options while working with Sinatra &#8211; for example Database: ORM (datamapper/active record), Templating: (erb/haml/builder), http caching, filters, helpers and error handling. One of it&#8217;s best features is it comes with Rack middleware. For the last 6 months I am using Sinatra and I feel very happy to work with it.
  </p>
  
  <h3>
    Do YOU use Sinatra?
  </h3>
  
  <p>
    <a href="http://ad.ly/refer/2014322399"><img class="alignright" src='http://ad.ly/static/images/referral/square.gif' alt="Twitter" /></a>
  </p>
  
  <p>
    If you are a Rubyist using Sinatra, <em>we would like to know as to why, how and where you are using Sinatra</em>. Post this as a blog comment. Thanks.
  </p>
  
  <p class="alert">
    <strong><em>Post supported by 1st Easy Limited</em>:</strong> UK based 1st Easy Limited offer Sinatra and Rails hosting running on a Phusion Passenger (mod_rails) and LAMP stack. If you want to get to know them first, or simply want to try out your Sinatra or Rails skills, <a href="http://www.1steasy.com/ruby-on-rails.htm#try">let them arrange a free trial hosting account</a> for you &#8211; full technical support from their team is included!
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Rubyists+Using+Sinatra" rel="tag">Rubyists Using Sinatra</a>, <a href="http://technorati.com/tag/Ruby+Programming" rel="tag">Ruby Programming</a>, <a href="http://technorati.com/tag/Rubyists" rel="tag">Rubyists</a>, <a href="http://technorati.com/tag/Sinatra" rel="tag">Sinatra</a>
