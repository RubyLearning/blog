---
title: 'Survserv: Rails based Real Time Outbreak Detection System'
author: Satish Talim
date: 2007-09-10
layout: post
permalink: /2007/09/10/survserv-rails-based-real-time-outbreak-detection-system/
categories:
  - Interview
  - News
  - Rails
  - Ruby
---
<div style="float: right; margin-left: 10px; margin-bottom: 10px;">
  <a href="http://www.rubylearning.com/images/ab.jpg" title="Arindam Basu"><img src="http://www.rubylearning.com/images/ab.jpg" alt="Arindam Basu" /></a>
</div>

<div>
  <p>
    <em>RubyLearning caught up with <strong>Arindam Basu</strong> and requested him to brief us about <strong>Survserv</strong>, a Rails based real time outbreak detection system (still in Beta).</em>
  </p>
  
  <p>
    <strong>Hello Arindam, and welcome to RubyLearning.com. Tell us something about your background.</strong>
  </p>
  
  <p>
    I am a physician-epidemiologist-health services researcher, and I direct an International Research Training Program in environmental and occupational health related research training program in Kolkata, India, under the aegis of the University of California at Berkeley. I got interested in Ruby and Ruby on Rails about a year back while researching on disease surveillance and data analysis, and my background as an epidemiologist biostatistician helped me to use Ruby productively for my data analytical work. I also work as a consultant in data analysis, and in health-care informatics.
  </p>
  
  <p>
    <strong>What is the goal of <strong>Survserv</strong>?</strong>
  </p>
  
  <p>
    Briefly, the goal of Survserv is to develop a web-based framework where anyone with a hand-held device (like a cellphone that can access the WWW, or a device like the simputer, etc) that can access a website or can SMS, can enter some basic information about specific symptoms and complaints to a web-database. The database will connect to a statistical program (I have used R for statistical computing), then use Naive Bayesian Classification (a related concept to how your email program filters spams in your mailboxes) and classify the symptoms to a number of disease clusters.
  </p>
  
  <p>
    These disease clusters however, will be automatically mined for their spatial and temporal relationships (in other words, the database will also record the IP address or from where the request has come in addition to time stamp). Over time, a graph of the number of symptoms and signs will be built up, and the waves will be compared with regular patterns to see if an epidemic is emerging. If the system detects an emergent epidemic, it will send emails to respective authorities, and raise alerts about possible outbreaks.
  </p>
  
  <p>
    <strong>Where do you think this application can be used?</strong>
  </p>
  
  <p>
    This program will be useful in far and remote places where people can just get connected to the net and cellphones are present, but nothing much more than that is available, so that outbreak detections are typically delayed. This time lag will be cut short with this web based framework, if deployed. At present, the disease surveillance system is slow and takes about a weeks&#8217; time for the data to be compiled and presented from a health center to the district level and then they get dumped to a major city or the state health intelligence bureau. In addition, these data are rarely mined (let alone real time) for predicting epidemics. This system will create a parallel data abstraction system where epidemics will be alerted real time system wide, and enable development of an epidemic prediction engine. The concept is neither novel nor unique but one that is practical and can be easily deployed and will likely to significantly improve on current lag times for disease outbreaks.
  </p>
  
  <p>
    <strong>What&#8217;s the current status of the application?</strong>
  </p>
  
  <p>
    I have not received any sponsorship or funding for the program. It&#8217;s still funded from my own funds, and being worked on my own time as and when I can. About 40% of the work has been done though, eg, setting up the database (I am using MySQL), the front end forms, the link between R, and routing of the graphs. The program should be usable to anyone who can access web.
  </p>
  
  <p>
    <strong>Finally, anything else you would like to tell our readers?</strong>
  </p>
  
  <p>
    This work has been selected at the Open Source Developers&#8217; Conference in Brisbane, Australia (26-29 November, 2007). If anyone&#8217;s interested to learn more about the work, I&#8217;d be happy to explain.
  </p>
  
  <p>
    <em>Thanks Arindam. We wish you and Survserv all the very best. You can contact Arindam at <strong>arinbasu99 [at] yahoo.com</strong></em>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Arindam+Basu" rel="tag">Arindam Basu</a>, <a href="http://technorati.com/tag/Berkeley" rel="tag">Berkeley</a>, <a href="http://technorati.com/tag/Health" rel="tag">Health</a>, <a href="http://technorati.com/tag/Survserv" rel="tag">Survserv</a>, <a href="http://technorati.com/tag/Survserv%3A+Rails+based+Real+Time+Outbreak+Detection+System" rel="tag">Survserv: Rails based Real Time Outbreak Detection System</a>, <a href="http://technorati.com/tag/University+of+California" rel="tag">University of California</a>, <a href="http://technorati.com/tag/University+of+California+at+Berkeley" rel="tag">University of California at Berkeley</a>
