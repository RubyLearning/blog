---
title: 'Interview with Ola Bini &#8211; JRuby Core Developer'
author: Satish Talim
date: 2007-08-30
layout: post
permalink: /2007/08/30/interview-with-ola-bini-jruby-core-developer/
categories:
  - Interview
  - JRuby
  - Rails
  - Ruby
---
<div style="float: right; margin-left: 10px; margin-bottom: 10px;">
  <a href="http://www.rubylearning.com/images/ola.jpg" title="Ola Bini"><img src="http://www.rubylearning.com/images/ola.jpg" alt="Ola Bini" /></a>
</div>

<div>
  <p>
    <em>RubyLearning caught up with <strong><a href="http://ola-bini.blogspot.com/">Ola Bini</a></strong> at Bangalore, India and talked to him about JRuby. Ola provides some insights for easy adoption of JRuby by the large pool of Java and Ruby developers in India.</em>
  </p>
  
  <p>
    <strong>Hello Ola, and welcome to RubyLearning.com. Tell us something about your background and how you came to JRuby.</strong>
  </p>
  
  <p>
    Well, I&#8217;m a programming language geek and have looked at many languages for a long time. I&#8217;ve used LISP since before I can remember, but Java have always been the language that is economically viable to use. But I&#8217;m not that fond of the Java language &#8211; the platform is very good, but the language&#8230; well. So I looked around for something better. I&#8217;ve known Ruby for a few years; it&#8217;s got some very nice similarities to LISP, Smalltalk and other very nice languages. Finally I found the JRuby project, realized that it would hit my sweet spot perfectly and decided to start helping out on it.
  </p>
  
  <p>
    <strong>Could you tell us some reasons on why a Ruby developer should start looking into JRuby?</strong>
  </p>
  
  <p>
    There are several good reasons: most of the problems of Ruby 1.8 are actually resolved by JRuby in one way or the other. You get better threading semantics, native unicode, active development, easier extensions, very good garbage collection &#8211; and superb integration with Java libraries. All of these are very nice things for a Ruby developer since they fix deficiencies in the current MRI 1.8.
  </p>
  
  <p>
    <strong>How should a person working on Ruby approach JRuby?</strong>
  </p>
  
  <p>
    The first step is just to try your application out on it. If it&#8217;s a regular Ruby application that doesn&#8217;t use native extensions, the chance is very good that it will just run on JRuby. The next step &#8211; after the application runs &#8211; is to get ready to integrate some of the Java specific libraries and start using them instead. For example, theres a backend to REXML that uses Java libraries instead; this makes REXML much faster and also safer. It will also add new capabilities to REXML, like validation and so on. And this is with the exact same interface as regular REXML, so you get all this for free, just by moving. The same thing applies for running JRuby on Rails, and using JDBC as a back end connector.
  </p>
  
  <p>
    <strong>With a stable release now in hand what is your current focus and roadmap for JRuby?</strong>
  </p>
  
  <p>
    Well, the current focus is on completing the compiler and also working on performance. We are not making huge changes in the functionality right now &#8211; instead looking at external libraries that enhance the value of JRuby.
  </p>
  
  <p>
    <strong>Can you give some examples where JRuby is being persistently used?</strong>
  </p>
  
  <p>
    Well, ThoughtWorks sells Mingle, which runs on JRuby on Rails. Sun has some JRuby projects. Oracle is working on JRuby projects. And there are many, many smaller projects being developed all around the world.
  </p>
  
  <p>
    <strong>Can you tell us one area of JRuby wherein you feel there needs to be an improvement?</strong>
  </p>
  
  <p>
    Well, the 1.0-release was focused on compatibility. The performance was pretty good, but now we really want to surpass MRI in performance. So that&#8217;s what we&#8217;re working on right now. Aside from that, documentation is sorely needed too. (My book, that comes out Sept. 24th, will probably help some with that.)
  </p>
  
  <p>
    <strong>Is there a plan to have a developers tool for JRuby?</strong>
  </p>
  
  <p>
    Well, right now there is a lack of development tools for Ruby itself &#8211; many companies are working on it though. These tools will work for JRuby too. I know that NetBeans are planning to add some JRuby specific things to their Ruby tool later on.
  </p>
  
  <p>
    <strong>Can you highlight on some good mechanisms for deploying JRuby based applications?</strong>
  </p>
  
  <p>
    That&#8217;s kinda hard. If you&#8217;re talking about Rails applications, using WAR based deployment to a Java application server is generally the best solution.
  </p>
  
  <p>
    <strong>How is the performance and scalability aspect of JRuby?</strong>
  </p>
  
  <p>
    I addressed performance above. Scalability is another thing. Generally JRuby takes more memory than MRI, but usually scales better due to better threading.
  </p>
  
  <p>
    <strong>Finally, how easy it is to pickup JRuby? Any pointers?</strong>
  </p>
  
  <p>
    It&#8217;s as easy as picking up Ruby. It&#8217;s really easy to get started, and if you google for the JRuby wiki, you will find lots of good information for getting started. Once again, my book will help here&#8230; <img src="http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" />
  </p>
  
  <p>
    <em>Thanks Ola for sharing your views with the RubyLearning.com members.</em>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Interview+with+Ola+Bini+%26%238211%3B+JRuby+Core+Developer" rel="tag">Interview with Ola Bini &#8211; JRuby Core Developer</a>, <a href="http://technorati.com/tag/Interviews" rel="tag">Interviews</a>, <a href="http://technorati.com/tag/JRuby" rel="tag">JRuby</a>, <a href="http://technorati.com/tag/Ola+Bini" rel="tag">Ola Bini</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Ruby+on+Rails" rel="tag">Ruby on Rails</a>, <a href="http://technorati.com/tag/Ruby+Interviews" rel="tag">Ruby Interviews</a>
