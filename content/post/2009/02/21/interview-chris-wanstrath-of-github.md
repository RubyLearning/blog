---
title: 'Interview: Chris Wanstrath of GitHub'
author: Satish Talim
date: 2009-02-21
layout: post
permalink: /2009/02/21/interview-chris-wanstrath-of-github/
keywords:
  - Chris Wanstrath,Git, GitHub,Interviews,Ruby,The Ruby Programming Language
description:
  - On the eve of the first ever free, online course on "Git and GitHub", Chris Wanstrath founder of GitHub talks to RubyLearning.
ashbbb@gmail.com:
  - ashbb
jccalistro@gmail.com:
  - joaocalistro
andre.java@gmail.com:
  - andrefaria
categories:
  - Beginners
  - Interview
  - Ruby
  - Training
tags:
  - Chris Wanstrath
  - Git
  - GitHub
  - interviews
  - Ruby
  - The Ruby Programming Language
---
<div>
  <p class="alert">
    On the eve of the first ever free, online course on &#8220;Git and GitHub&#8221;, Satish Talim of RubyLearning caught up with <strong>Chris Wanstrath</strong> and talked to him, in this short interview.
  </p>
  
  <p>
    <img class="alignright" src="http://rubylearning.com/images/ChrisWanstrath.jpg" alt="Chris Wanstrath, USA" title="Chris Wanstrath, USA" width="95" height="125" />
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish Talim>></strong> Welcome, Chris and thanks for taking out time to share your thoughts. For the benefit of the readers, could you tell us something about your self?</span>
  </p>
  
  <p>
    <strong>Chris Wanstrath>></strong> I&#8217;m a Ruby and JavaScript programmer living in San Francisco, CA. <em>I was one of the guys who started <strong>GitHub</strong></em>. When I&#8217;m not working on the site, I can be found playing guitar or drinking bourbon. Sometimes at the same time!
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Why according to you, is it important for a new Ruby developer to know and use Git and GitHub?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> I learned how to program by reading other people&#8217;s code and contributing to open source projects. Submitting a patch and seeing how the maintainer rewrites it is invaluable: it&#8217;s like getting free, personalized programming lessons from someone with more experience than you.
  </p>
  
  <p>
    GitHub is important because it&#8217;s one of the best places to participate in active open source development. The barrier to entry is extremely low, and with casual forking it&#8217;s basically designed for the &#8220;make small changes to a foreign project and see what happens&#8221; workflow.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Why GitHub? Why not SourceForge?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> SourceForge is about publishing projects, GitHub is about collaborating on code. SourceForge is helpful when exploring or working on projects, but this is really where GitHub shines.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> What were the challenges of putting GitHub together?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> We&#8217;re still facing them today. We not only have to worry about the database when growing, but also Git repositories on disk &#8211; we essentially have two different data stores, one of which has never been used at this scale before. We&#8217;re constantly doing lots of very cool caching things under the hood to try and make everything faster.
  </p>
  
  <p>
    Big database tables and high IO are our biggest issues. I think the key is to recognize problems early on and not be afraid of throwing out existing code in order to implement a better solution. It&#8217;s okay to do things the simple way early on &#8211; probably better, really &#8211; but you need to understand that they&#8217;re only going to take you so far before you need to spend more time coming up with a smarter solution that works for higher load.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Do you have any suggestions for RubyLearning&#8217;s Git & GitHub course participants?</span>
  </p>
  
  <p>
    <strong>Chris>></strong> Create and share open source &#8211; whether on GitHub or elsewhere! It&#8217;s very rewarding, a great way to meet people, and the best way to improve your skills.
  </p>
  
  <p>
    <span style="color:#CC3333;"><strong>Satish>></strong> Thanks Chris for sharing your views with the RubyLearning GitHub course participants.</span>
  </p>
  
  <p>
    <span style="font-size: 8pt; font-family: Arial;"><i><strong>Disclaimer:</strong></i></span><br /><span style="font-size: 8pt; font-family: Arial;"><i>The opinions expressed are those of Chris Wanstrath and do not necessarily reflect those of <strong><a href="http://rubylearning.com/">www.RubyLearning.com</a></strong>.</i></span>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Chris+Wanstrath" rel="tag">Chris Wanstrath</a>, <a href="http://technorati.com/tag/Git" rel="tag">Git</a>, <a href="http://technorati.com/tag/GitHub" rel="tag"> GitHub</a>, <a href="http://technorati.com/tag/Interviews" rel="tag">Interviews</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>
