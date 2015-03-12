---
author: Satish Talim
categories:
- Interview
- Rails
- Ruby
- Ruby Masters
- Ruby on Rails
date: 2011-02-18
layout: post
permalink: /2011/02/18/interview-michael-hartl-author-of-the-ruby-on-rails-tutorial-railstutorial-org/
tags:
- Michael Hartl
- Ruby on Rails
- ruby programming
thesis_description:
- RubyLearning participants talk to Michael Hartl the author of the Ruby on Rails
  Tutorial.
thesis_keywords:
- Michael Hartl,Ruby on Rails,Ruby programming
title: 'Interview: Michael Hartl, author of the Ruby on Rails Tutorial (railstutorial.org)'
topsy_short_url:
- http://bit.ly/eZqMC4
---

<div>
  <p class="alert">
    RubyLearning participants talk to Michael Hartl the author of the Ruby on Rails Tutorial (<a href="http://ruby.railstutorial.org/">railstutorial.org</a>).
  </p>
  
  <p>
    <img class="alignright" title="Michael Hartl" src="http://rubylearning.com/images/headshot_smaller.jpg" alt="Michael Hartl" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Welcome Michael and thanks for taking out time for RubyLearning. For the benefit of the readers of this blog could you please introduce yourself and tell us what you do for a living?</span>
  </p>
  
  <p>
    <strong>Michael>></strong> Happy to be here. I&#8217;m a programmer, educator, and entrepreneur. Recently, I&#8217;ve been focused on making educational products and selling them online. I&#8217;ve been doing web development since around 2001 and Rails development since 2005. I also have a background in academic teaching and research, principally in theoretical and computational physics.
  </p>
  
  <p>
    My current products are the Ruby on Rails Tutorial book and the Ruby on Rails Tutorial screencasts. The <a href="http://railstutorial.org/ruby-on-rails-tutorial-book">book is available for free online</a>, for <a href="http://railstutorial.org/">buy as a PDF</a>, and as a <a href="http://amzn.to/RTbook">print edition</a>. The <a href="http://railstutorial.org/">screencasts are available for purchase</a> from the Rails Tutorial website or (if you have a subscription) from Safari Books Online. I especially recommend the <a href="http://railstutorial.org/">Rails Tutorial PDF/screencast bundle</a>.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Ricardo Astorquia, Spain>></strong> How do you get the right balance for teaching in a book for those folks that may have different backgrounds, where more details are necessary while another reader may need just a little more guidance than just a reference book?</span>
  </p>
  
  <p>
    <strong>Michael>></strong> It&#8217;s important to realize that advanced readers rarely mind a little basic material, especially if including it is a core part of your style, and that basic material helps bring the newbies up to speed. One inspiration is The Economist magazine&#8217;s house style, which usually includes some information about a company or person, no matter how famous; for example, they might write &#8220;General Electric, an American conglomerate&#8221; or &#8220;Steve Jobs, boss of Apple&#8221;. I try always to include enough detail that even a beginner has a place to start if they need further information.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Vince Vincent, USA>></strong> Do you intend to create a sequel as new Rails versions are released? If not, what is the speediest way for a Rails developer to progress from here (aside from reading the API which many suggest)?</span>
  </p>
  
  <p>
    <strong>Michael>></strong> I plan to keep the <a href="http://railstutorial.org/">Ruby on Rails Tutorial</a> up-to-date. The book is easy to edit, but the screencasts are trickier, so for a while I might only supplement the screencasts. Eventually, though, I anticipate having to re-cut the entire series once Rails has changed enough to justify the effort.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Imhotep Albasiel, USA>></strong> Would you be writing about Rails development on Windows in the future?</span>
  </p>
  
  <p>
    <strong>Michael>></strong> I am hoping to cover Rails development on Windows in future editions. Part of the issue has been the lack of a standard Windows installation method, but the new <a href="http://railsinstaller.org/">Rails Installer</a> aims to change that, so I&#8217;m optimistic that Rails development will start to take off on Windows.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Samnang Chhun, Cambodia>></strong> Is it important to understand Rack when learning Rails?</span>
  </p>
  
  <p>
    <strong>Michael>></strong> Rack is a Ruby library that provides a standard interface between web frameworks and web servers. Most Ruby web frameworks, including Rails and Sinatra, use Rack, and it is certainly important in some contexts, but I think that Rack can be skipped when first learning Rails. It&#8217;s really more of an intermediate-to-advanced topic.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Samnang Chhun, Cambodia>></strong> What should I do next to become a Rails guru?</span>
  </p>
  
  <p>
    <strong>Michael>></strong> There are lots of great Rails resources out there, and I particularly recommend <a href="http://railscasts.com/">Railscasts</a> by Ryan Bates. Of course, there&#8217;s no substitute for writing your own application, so I suggest picking a problem that interests you and plunging ahead.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Victor Goff, USA>></strong> On January 25th, you were notified that your RailsTutorial was banned by a certain country. Have you cashed in on the notoriety yet!?</span>
  </p>
  
  <p>
    <strong>Michael>></strong> I&#8217;m not sure being blocked by the Great Firewall of China is a big enough story to earn me much notoriety. It is weird, though, and disappointing. I guess it means I&#8217;ve made the big time?
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Victor Goff, USA>></strong> How do you manage having a publication that can be broken by updates in the gems that you use, either in the production directly, or in testing?</span>
  </p>
  
  <p>
    <strong>Michael>></strong> This is a big lesson I learned from my first Rails book, called RailsSpace. In that book, my coauthor and I made the mistake of not using specific version numbers for the gems, but the Ruby on Rails 3 Tutorial book avoids this error. Every one of the gems in the book is tied to a particular version number, so the tutorial is (virtually) guaranteed to work as advertised. Of course, I do occasionally update the book with new gem versions, but I always test the new gems to make sure they work. (The sample application&#8217;s test suite proves invaluable in this context.)
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Robin Gowin, USA>></strong> Where do you see Rails going, and what do you think of the Rails &#8211; Merb merger?</span>
  </p>
  
  <p>
    <strong>Michael>></strong> I think Rails is off to the races now, especially with the release of Rails 3. The Rails core team and the Merb developers deserve immense credit for setting aside their differences and joining forces to make Rails 3 happen. Given how modular the core of Rails is now, I expect all kinds of great innovation in the next few years.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Mohnish Jadwani, India>></strong> If developers want to migrate from an application built on Rails 2 to an application built on Rails 3, what are the challenges one would face for this migration (I understand this would be an app specific question, I only want to know in generic terms). How best can this be dealt?</span>
  </p>
  
  <p>
    <strong>Michael>></strong> Since the Rails Tutorial is aimed mainly at beginners, I didn&#8217;t feel that covering the upgrade from Rails 2 to Rails 3 fit with the core philosophy of the book. Moreover, there are already lots of resources to help make the Rails 2.x to 3.x upgrade, including an e-book dedicated to this subject (Jeremy McAnally&#8217;s &#8220;<a href="http://www.railsupgradehandbook.com/">Rails 3 Upgrade Handbook</a>&#8220;).
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Zachary S. Scott, USA>></strong> Do you have plans for any other Ruby (non-Rails related) project?</span>
  </p>
  
  <p>
    <strong>Michael>></strong> I am contemplating making a Ruby tutorial at some point, but no promises! I&#8217;m also planning to open-source PolyTeXnic, the Ruby program I use to make the HTML and PDF versions of the book.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Zachary S. Scott, USA>></strong> What do you think of Sinatra?</span>
  </p>
  
  <p>
    <strong>Michael>></strong> I&#8217;ve only dabbled with Sinatra, but I&#8217;d like to know it better. It seems very clean and elegant.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Anything else you would like to add?</span>
  </p>
  
  <p>
    <strong>Michael>></strong> Web development is hard, so don&#8217;t get discouraged if you run into difficulties. All web developers run into difficulties all the time. With practice, you&#8217;ll get better at powering through the problems &mdash and you&#8217;ll also learn that sometimes you have to give up and hack around them. <img src="http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif" alt=":-)" class="wp-smiley" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><em>Thank you Michael. In case you have any queries and/or questions, please post your questions here (as comments to this blog post) and Michael would be glad to answer.</em></span>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Michael+Hartl" rel="tag">Michael Hartl</a>, <a href="http://technorati.com/tag/Ruby+on+Rails" rel="tag">Ruby on Rails</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>
