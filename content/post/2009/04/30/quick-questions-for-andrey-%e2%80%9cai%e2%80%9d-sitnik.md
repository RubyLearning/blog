---
title: Quick Questions for Andrey 'A.I.' Sitnik
author: Satish Talim
date: 2009-04-30
layout: post
permalink: /2009/04/30/quick-questions-for-andrey-%e2%80%9cai%e2%80%9d-sitnik/
keywords:
  - Andrey Sitnik,R18n,Merb,Sinatra, Ruby
description:
  - Andrey Sitnik talks to RubyLearning about his Ruby gem R18n.
categories:
  - interview
  - rails
  - ruby
tags:
  - andrey sitnik
  - merb
  - r18n
  - ruby
  - sinatra
---
<div>
  <p class="alert">
    RubyLearning caught up with <strong>Andrey &#8220;A.I.&#8221; Sitnik</strong> developer of R18n, a tool to internationalize and localize your Merb/Sinatra/desktop Ruby application, and asked him some quick questions in this interview.
  </p>
  
  <p>
    <img class="alignright" title="Andrey Sitnik" src="http://www.rubylearning.com/images/andrey.jpg" alt="Andrey Sitnik" width="125" height="125" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Andrey, could you tell us something about yourself &#8211; your background, where you are based?</span>
  </p>
  
  <p>
    <strong>Andrey>></strong> I live in Saint Petersburg, Russia and study in Saint Petersburg State Polytechnical University.
  </p>
  
  <p>
    I believe in the ubiquity of genetic algorithms and that diversity (of culture, languages, etc) is necessary for progress.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> What is &#8220;R18n&#8221; ?</span>
  </p>
  
  <p>
    <strong>Andrey>></strong> This is the only normal name that isnâ€™t taken by any other Rails plugins <img src="http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> What was the idea behind &#8220;R18n&#8221; ?</span>
  </p>
  
  <p>
    <strong>Andrey>></strong> I18n logic is the same for any application and doesnâ€™t depend on a framework. So, I think, that i18n library must be agnostic with core gem and gems for &#8220;out of box&#8221; work with additional frameworks.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> How does your tool help to internationalize and localize a Merb / Sinatra app?</span>
  </p>
  
  <p>
    <strong>Andrey>></strong> <a href="http://r18n.rubyforge.org/">R18n</a> helps to translate interface and print dates and numbers in user traditions (for example, &#8220;27.04.2009&#8221; in Russian and &#8220;04/27/2009&#8243; in USA). To translate your data (e.g. in database) you need to write you own logic, because itâ€™s very business specific.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> For a Ruby beginner, can you illustrate the usage of your tool with an example ?</span>
  </p>
  
  <p>
    <strong>Andrey>></strong> Add R18n to your Sinatra application:<br /><code>require 'sinatra/r18n'</code>
  </p>
  
  <p>
    Now your app has i18n support and you need to add translations file in i18n/ dir. For example ./i18n/en.yml:<br /><code>post:&lt;br />
       friends: Post only for friends&lt;br />
       tags: Post tags: %1</code>
  </p>
  
  <p>
    <code>comments: !!pl&lt;br />
       0: No comments&lt;br />
       1: One comment&lt;br />
       n: %1 comments</code>
  </p>
  
  <p>
    And use these translated messages in a view:<br /><code>i18n.post.friends&lt;br />
     i18n.post.tags(@post.tags.join(', '))&lt;br />
     i18n.comments(@post.comments.size)</code>
  </p>
  
  <p>
    Also it would be good if a user reads numbers and dates in his culture formats:<br /><code>i18n.l @post.created_at, :date&lt;br />
     i18n.l 10000</code>
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Are you working on any other Ruby based project?</span>
  </p>
  
  <p>
    <strong>Andrey>></strong> I am working on my science project related to <a href="http://github.com/ai/d2na/tree/master">machine learning via genetics algorithms using Ruby</a> and plan to start a genetic algorithms Ruby library.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> What will be there in the next version of &#8220;R18n&#8221; ?</span>
  </p>
  
  <p>
    <strong>Andrey>></strong> I plan a performance optimization (compile translation files?) and a Rails plugin with compatibility with Rails I18n API.
  </p>
  
  <p>
    <span style="color:#CC3333;"><em>Thank you Andrey. In case you have any queries and/or questions, kindly post your questions here (as comments to this blog post) and Andrey would be glad to answer.</em></span>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Andrey+Sitnik" rel="tag">Andrey Sitnik</a>, <a href="http://technorati.com/tag/R18n" rel="tag">R18n</a>, <a href="http://technorati.com/tag/Merb" rel="tag">Merb</a>, <a href="http://technorati.com/tag/Sinatra" rel="tag">Sinatra</a>, <a href="http://technorati.com/tag/Ruby" rel="tag"> Ruby</a>
