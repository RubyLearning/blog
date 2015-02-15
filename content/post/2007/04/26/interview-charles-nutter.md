---
title: 'Interview: Charles Nutter'
author: Satish Talim
date: 2007-04-26
layout: post
permalink: /2007/04/26/interview-charles-nutter/
categories:
  - Rails
  - Ruby
---
<div style="float: right; margin-left: 10px; margin-bottom: 10px;">
  <a href="http://rubylearning.com/images/nutter.jpg" title="Charles Nutter"><img src="http://rubylearning.com/images/nutter.jpg" alt="Charles Nutter" /></a>
</div>

<div>
  <p>
    <span style="color:blue;">(This interview appeared before on 30th Aug. 2006 on the PuneRuby blog).</span>
  </p>
  
  <p>
    Today&#8217;s talk with Ruby Guru, <b><span style="color:blue;">Charles Nutter</span></b> would be of interest to all of you who have a Java background.
  </p>
  
  <p>
    <b>Satish Talim>></b> Hello Charles, and welcome to PuneRuby. Could you tell us something about yourself &#8211; your background; where you are based&#8230;?
  </p>
  
  <p>
    <b>Charles Nutter>></b> I&#8217;ve been programming computers since I was in grade school. Since 1996 I&#8217;ve been a fulltime Java developer, primarily working on web-based applications using Java EE technologies. My most recent job has me as application architect for a number of large Java EE applications, making technology decisions and setting project direction. However for the past year my true love has been JRuby, a Ruby implementation for the JVM. I have devoted much of my free time to making JRuby compatible with Ruby, so Java developers might be able to take advantage of the beauty and power of Ruby.
  </p>
  
  <p>
    I am based in the Minneapolis area in the state of Minnesota in the United States.
  </p>
  
  <hr />
  You can 
  <a href="http://edu.ericae.net/learn-html.htm">learn HTML</a> as a first step into web programming.<br /> 
  
  <hr />
  
  <p>
    <b>Satish Talim>></b> Given the choices out there, why did you select Ruby?
  </p>
  
  <p>
    <b>Charles Nutter>></b> I came to Ruby via a recommendation from a friend. Before I&#8217;d ever written a line of code, I found that RubyConf 2004 would be held within a few miles of my employer&#8217;s home office. I arranged to attend, and was amazed by the level of energy, the enthusiasm of the attendees, and especially the ingenuity and simplicity of the applications and libraries being presented. I began to believe I might have finally found a scripting/dynamic language I could really love. While at the conference, I wondered if there might be a Java implementation of Ruby. That led me to JRuby, and I&#8217;ve been a Rubyist and JRubyist ever since.
  </p>
  
  <p>
    <b>Satish Talim>></b> How did you learn Ruby and when?
  </p>
  
  <p>
    <b>Charles Nutter>></b> I&#8217;ve learned Ruby a bit differently than most folks; namely, from the inside out. In the process of helping to redesign and reengineer JRuby, I&#8217;ve had to learn the language, obviously, but I&#8217;ve also had to learn how JRuby and the stock Ruby interpreter work internally. That&#8217;s taught me more about the language than any other source, since I&#8217;ve had to develop a deeper understanding of features most books and documents only cover from a Ruby point of view. I&#8217;m hoping to take my knowledge of Ruby to organizations interested in advancing the language and advancing JRuby, so that the Java world I know and love can benefit from Ruby as well.
  </p>
  
  <p>
    <b>Satish Talim>></b> Which features of Ruby do you like the most?
  </p>
  
  <p>
    <b>Charles Nutter>></b> Closures are certainly the most visible and compelling feature of Ruby&#8230;so compelling that most other platforms and languages are compared to Ruby simply by how easily they can implement or present closures. I also like that the language is very terse but very readable, and that whitespace is not syntactically important. Though there are perlisms, most code I&#8217;ve had the pleasure to read is still very clear in its intent. I believe Ruby has been carefully evolved not to fulfill some higher vision of what a language ought to do, or to show off crazy language feature X, but to really help people get work done. As has been said many times before, Ruby makes simple problems easy and difficult problems possible. That&#8217;s exactly what we need in the Java world, since so many problems we solve again and again with too much code are really very simple at their core.
  </p>
  
  <p>
    <b>Satish Talim>></b> Do you think Ruby has the potential to be a mainstream programming language?
  </p>
  
  <p>
    <b>Charles Nutter>></b> Absolutely, and I think it&#8217;s already on its way. The mainstream press has started to realize that the Ruby Way is gathering a lot of momentum, and now major software companies are starting to investigate and fund research in the Ruby world. I believe that Ruby is the best scripting/dynamic language currently available, and I am not at all surprised that its popularity has exploded recently. I have introduced friends and family to Ruby and in every case they have told me &#8220;if only I had learned Ruby first, I might have [finished my degree|continued in school|understood programming&#8230;]&#8221;. It&#8217;s simply awe-inspiring how easily people can become productive with Ruby. It has the potential to change the world.
  </p>
  
  <p>
    <b>Satish Talim>></b> What applications, utilities have you developed in Ruby and what platform are you running these applications on?
  </p>
  
  <p>
    <b>Charles Nutter>></b> I have been working almost exclusively on JRuby, a Ruby implementation in Java originally written in 2001. During the two years I&#8217;ve been on the project, we&#8217;ve worked furiously to improve compatibility with Ruby 1.8, fixing bug after bug after bug and adding as many tests as possible. Over the past nine months, I&#8217;ve led efforts to get more complicated applications working like IRB, RubyGems, and Ruby on Rails, to the point that most pure Ruby applications now &#8220;just work&#8221; under JRuby. I&#8217;m very excited that I and other Java developers will now be able to use Ruby alongside our Java code and libraries, within our Java application servers, and in concert with our existing Java infrastructure. The potential for JRuby is enormous, and we&#8217;re only seeing the tip of the iceberg right now.
  </p>
  
  <p>
    JRuby has taken most of my free time, but I have many other projects on which I plan to spend more time. I&#8217;d like to make Rake into a full-fledged replacement for Ant. I&#8217;d like to wire in JRuby&#8217;s extension mechanism to allow transparent installation of Gems that have native code components. I want to continue to help efforts to get Mongrel running under JRuby. I want to help build out the RubySpec Wiki, an effort to document in a tighter specification format the functioning of Ruby and its libraries. I want to build out tool support for Ruby in the NetBeans IDE. I want to help efforts to build code refactoring capabilities for Ruby. I want to help bring disparate test frameworks and libraries together into a comprehensive suite of RubyTests. I want to make as many existing Ruby apps run well under JRuby as possible. I want to bring the world of Ruby to the world of Java, and help both worlds gain maximum benefit from each other. They&#8217;re big goals, but I know they&#8217;re all possible&#8230;and I think they&#8217;re inevitable.
  </p>
  
  <p>
    <b>Satish Talim>></b> Anything else you would like to share with the PuneRuby members?
  </p>
  
  <p>
    <b>Charles Nutter>></b> Have a look at JRuby, especially if you have Java libraries, legacy Java code, or existing Java servers and infrastructure you&#8217;d like to Rubify. JRuby has become a viable Ruby interpreter in its own right, but it&#8217;s even more compelling as a way to write Java Platform-based applications in a simple, beautiful language. Think of Ruby on the JVM like Ruby under UNIX: Java and C are excellent, powerful languages for writing core components, libraries, and frameworks, and Ruby helps programmers tie the power of those components, libraries, and frameworks together into applications with a minimum of effort. JRuby is hosted on <b><a href="http://jruby.codehaus.org/" >Codehaus</a></b>, and we welcome code contributions and mailing list discussions from anyone interested. Stop by and let us help you decide if JRuby might be the Ruby for you.
  </p>
  
  <p>
    <b>Satish Talim>></b> Thanks Charles for sharing your views with the PuneRuby members.
  </p>
  
  <p>
    You can keep in touch with Charles Nutter via his <b><a href="http://headius.blogspot.com/">blog</a></b>.
  </p>
</div>

<div>
  <a href="http://technorati.com/tag/Instant+Rails" rel="tag"></a><a href="http://technorati.com/tag/Quick+Ruby" rel="tag"></a><a href="http://technorati.com/tag/Instant+Rails" rel="tag"></a><a href="http://technorati.com/tag/Pune+Ruby" rel="tag"></a><a href="http://technorati.com/tag/Quick+Ruby+Guide" rel="tag"></a><a href="http://technorati.com/tag/Programming+Languages" rel="tag"></a><a href="http://technorati.com/tag/Blogs" rel="tag"></a><a href="http://technorati.com/tag/Ruby" rel="tag"></a><a href="http://technorati.com/tag/PuneRuby" rel="tag"></a><a href="http://technorati.com/tag/QuickRuby" rel="tag"></a><a href="http://technorati.com/tag/PuneBloggers" rel="tag"></a><a href="http://technorati.com/tag/PuneBlogs" rel="tag"></a><a href="http://technorati.com/tag/Blogosphere" rel="tag"></a><a href="http://technorati.com/tag/Digg" rel="tag"></a><a href="http://technorati.com/tag/Media" rel="tag"></a><a href="http://technorati.com/tag/Tip" rel="tag"></a><a href="http://technorati.com/tag/RSS" rel="tag"></a><a href="http://technorati.com/tag/Marketing" rel="tag"></a><a href="http://technorati.com/tag/News" rel="tag"></a><a href="http://technorati.com/tag/IndianGuru" rel="tag"></a><a href="http://technorati.com/tag/Blogging" rel="tag"></a><a href="http://technorati.com/tag/Internet" rel="tag"></a><a href="http://technorati.com/tag/Blog" rel="tag"></a><a href="http://technorati.com/tag/Technical+Support" rel="tag"></a><a href="http://technorati.com/tag/Free+Software" rel="tag"></a><a href="http://technorati.com/tag/Help" rel="tag"></a><a href="http://technorati.com/tag/Pune" rel="tag"></a><a href="http://technorati.com/tag/SatishTalim" rel="tag"></a><a href="http://technorati.com/tag/Satish+Talim" rel="tag"></a><a href="http://technorati.com/tag/Weblog" rel="tag"></a><a href="http://technorati.com/tag/Weblogs" rel="tag"></a><a href="http://technorati.com/tag/Training" rel="tag"></a><a href="http://technorati.com/tag/Free+Training" rel="tag"></a><a href="http://technorati.com/tag/Tutorial" rel="tag"></a><a href="http://technorati.com/tag/Education" rel="tag"></a><a href="http://technorati.com/tag/Teacher" rel="tag"></a><a href="http://technorati.com/tag/Learning+Ruby" rel="tag"></a>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Charles+Nutter" rel="tag">Charles Nutter</a>, <a href="http://technorati.com/tag/Interviews" rel="tag"> Interviews</a>, <a href="http://technorati.com/tag/Interview%3A+Charles+Nutter" rel="tag"> Interview: Charles Nutter</a>, <a href="http://technorati.com/tag/Java" rel="tag"> Java</a>, <a href="http://technorati.com/tag/JRuby" rel="tag"> JRuby</a>, <a href="http://technorati.com/tag/Ruby+Interviews" rel="tag"> Ruby Interviews</a>
