---
draft: false
title: Quick Questions for Andrey 'A.I.' Sitnik
date: 2009-04-30
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/rubylearning
categories:
- interview
- rails
- ruby
description:
- Andrey Sitnik talks to RubyLearning about his Ruby gem R18n.
keywords:
- Andrey Sitnik,R18n,Merb,Sinatra, Ruby
layout: post
permalink: /2009/04/30/quick-questions-for-andrey-%e2%80%9cai%e2%80%9d-sitnik/
tags:
- andrey sitnik
- merb
- r18n
- ruby
- sinatra
---
RubyLearning caught up with **Andrey “A.I.” Sitnik** developer of R18n,
a tool to internationalize and localize your Merb/Sinatra/desktop Ruby
application, and asked him some quick questions in this interview.<!--more-->

![Andrey
Sitnik](http://www.rubylearning.com/images/andrey.jpg "Andrey Sitnik")

**Satish Talim\>\>** Andrey, could you tell us something about yourself
– your background, where you are based?

**Andrey\>\>** I live in Saint Petersburg, Russia and study in Saint
Petersburg State Polytechnical University.

I believe in the ubiquity of genetic algorithms and that diversity (of
culture, languages, etc) is necessary for progress.

**Satish\>\>** What is “R18n” ?

**Andrey\>\>** This is the only normal name that isnâ€™t taken by any
other Rails plugins
![:)](http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif)

**Satish\>\>** What was the idea behind “R18n” ?

**Andrey\>\>** I18n logic is the same for any application and doesnâ€™t
depend on a framework. So, I think, that i18n library must be agnostic
with core gem and gems for “out of box” work with additional frameworks.

**Satish\>\>** How does your tool help to internationalize and localize
a Merb / Sinatra app?

**Andrey\>\>** [R18n](http://r18n.rubyforge.org/) helps to translate
interface and print dates and numbers in user traditions (for example,
“27.04.2009” in Russian and “04/27/2009″ in USA). To translate your data
(e.g. in database) you need to write you own logic, because itâ€™s very
business specific.

**Satish\>\>** For a Ruby beginner, can you illustrate the usage of your
tool with an example ?

**Andrey\>\>** Add R18n to your Sinatra application:\
`require 'sinatra/r18n'`

Now your app has i18n support and you need to add translations file in
i18n/ dir. For example ./i18n/en.yml:\
`post:<br />        friends: Post only for friends<br />        tags: Post tags: %1`

`comments: !!pl<br />        0: No comments<br />        1: One comment<br />        n: %1 comments`

And use these translated messages in a view:\
`i18n.post.friends<br />      i18n.post.tags(@post.tags.join(', '))<br />      i18n.comments(@post.comments.size)`

Also it would be good if a user reads numbers and dates in his culture
formats:\
`i18n.l @post.created_at, :date<br />      i18n.l 10000`

**Satish\>\>** Are you working on any other Ruby based project?

**Andrey\>\>** I am working on my science project related to [machine
learning via genetics algorithms using
Ruby](http://github.com/ai/d2na/tree/master) and plan to start a genetic
algorithms Ruby library.

**Satish\>\>** What will be there in the next version of “R18n” ?

**Andrey\>\>** I plan a performance optimization (compile translation
files?) and a Rails plugin with compatibility with Rails I18n API.

*Thank you Andrey. In case you have any queries and/or questions, kindly
post your questions here (as comments to this blog post) and Andrey
would be glad to answer.*

