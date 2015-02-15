---
title: 'JRuby: Caffeinated Ruby'
author: Satish Talim
date: 2007-04-27
layout: post
permalink: /2007/04/27/jruby-caffeinated-ruby/
categories:
  - JRuby
  - Rails
  - Ruby
---
<div>
  <p>
    Recently, <strong><a href="http://jruby.codehaus.org/" >JRuby</a></strong> has been gaining more and more attention in the Java and Ruby communities. Java is a powerful platform and there are millions of lines of Java code being written each month, that the world will have to live with for a long time from now. By leveraging Java the platform with the power of the Ruby programming language, programmers get the best from both worlds. <i>You better not ignore JRuby any more!</i>
  </p>
  
  <p>
    <strong>What is JRuby</strong>?
  </p>
  
  <p>
    <strong>JRuby</strong> is a 100% pure-Java implementation of the Ruby programming language that runs in the JVM. JRuby&#8217;s creators, <a href="http://www.bloglines.com/blog/ThomasEEnebo" >Thomas Enebo</a> and <a href="http://rubylearning.com/blog/2007/04/26/interview-charles-nutter/" >Charles Nutter</a>, have been hired by <a href="http://www.sun.com/" >Sun</a> to work on JRuby full time. The current JRuby release 0.9.9 is fully compatible with Ruby 1.8.5.
  </p>
  
  <p>
    <a href="http://ola-bini.blogspot.com/" >Ola Bini</a> says that &#8220;JRuby is ready for prime time. Application developers should try their applications on JRuby NOW.â€
  </p>
  
  <p>
    So, I decided to take a quick look at JRuby and found it very easy to use.
  </p>
  
  <p>
    <strong>Download and Setup:</strong>
  </p>
  
  <ul>
    <li>
      The <a href="http://dist.codehaus.org/jruby/" >JRuby distribution</a> comes as a tar.gz file, namely jruby-bin-0.9.9.tar.gz
    </li>
    <li>
      Uncompress the archive; you should end up with a <strong>jruby-0.9.9</strong> folder.
    </li>
    <li>
      In Windows, set the system environment variable <strong>JRUBY_HOME</strong> to C:\jruby-0.9.9 I am assuming that you have uncompressed JRuby to C:
    </li>
    <li>
      Also, set the system environment variable <strong>path</strong> to C:\jruby-0.9.9\bin;
    </li>
    <li>
      The JRuby distribution&#8217;s bin directory contains the jruby.bat file that is used to run the JRuby interpreter. Run the command <strong>jruby -version</strong> from the command line to test that the JRuby is working. On my PC, it said:<br /><strong>ruby 1.8.5 (2007-04-23 rev 3539) [x86-jruby0.9.9]</strong>
    </li>
  </ul>
  
  <p>
    <strong>Where to use JRuby?:</strong>
  </p>
  
  <p>
    a. <strong><i>JRuby allows Ruby programs to use Java classes</i></strong>. This is a powerful concept that JRuby now brings to Ruby users. My <a href="http://rubylearning.com/satishtalim/ruby_tk_tutorial.html" >Ruby/Tk Tutorial</a> has a program <strong>p075hellotk1.rb</strong> that uses Ruby/Tk a graphical user interface. However, the documentation for Ruby/Tk is extremely poor and I would be comfortable in using Java Swing instead. The code in JRuby for the program p075hellotk1.rb can be something like this:
  </p>
  
  <pre># javaSwingHello.rb
require 'java' # Line 2
JFrame = javax.swing.JFrame
JLabel = javax.swing.JLabel
frame  = JFrame.new
jlabel = JLabel.new("Hello World")
frame.add(jlabel)
frame.setDefaultCloseOperation(JFrame::EXIT_ON_CLOSE)
frame.pack
frame.setVisible(true)
</pre>
  
  <p>
    Run the above program from the command line as follows:
  </p>
  
  <p>
    <strong>jruby javaSwingHello.rb</strong>
  </p>
  
  <p>
    Line 2: The second line of the above program enables JRuby&#8217;s Java support and allows a Ruby program to use Java classes.
  </p>
  
  <p>
    b. <strong><i>Calling JRuby from Java</i></strong>. JRuby can just as easily be called from Java, using either the JSR 223 Scripting for Java 6 or the <a href="http://en.wikipedia.org/wiki/Bean_Scripting_Framework" >Apache Bean Scripting</a> framework. More information on this is available in the <a href="http://www.headius.com/jrubywiki/index.php/Main_Page" >JRuby Wiki</a>
  </p>
  
  <p>
    c. <strong><i>Running Rails with JRuby</i></strong>. The advantages are obvious. To quote the JRuby Wiki:
  </p>
  
  <ul>
    <li>
      Gives Rails the power and functionality of Java: Virtual Machine, application servers, and libraries.
    </li>
    <li>
      With future JVM and JRuby improvements, JRuby may be faster than Matz&#8217; Ruby Interpreter in running Rails
    </li>
    <li>
      Gets Rails in the door of Java shops by making Rails apps into Java-platform apps.
    </li>
  </ul>
  
  <p>
    To conclude, I am surely liking JRuby and would definitely explore it further. <strong>Ignore JRuby at your own peril !</strong>
  </p>
  
  <p>
    <strong>Resources:</strong>
  </p>
  
  <ul>
    <li>
      <a href="http://jruby.codehaus.org/" >JRuby Home Page</a>
    </li>
    <li>
      <a href="http://www.headius.com/jrubywiki/index.php/Main_Page" >JRuby Wiki</a>
    </li>
    <li>
      <a href="http://www.headius.com/jrubywiki/index.php/JRuby_on_Rails" >Rails on JRuby</a>
    </li>
    <li>
      <a href="http://www.nabble.com/JRuby---User-f14107.html" >JRuby Forum</a>
    </li>
    <li>
      <a href="http://java.sun.com/developer/technicalArticles/scripting/jruby/" >JRuby and the Java Platform</a>
    </li>
  </ul>
  
  <p>
    Go on! <strong><a href="http://rubylearning.com/blog/2007/04/27/jruby-caffeinated-ruby/" >Digg It</a></strong> !
  </p>
</div>

<div>
  <a href="http://technorati.com/tag/Instant+Rails" rel="tag"></a><a href="http://technorati.com/tag/Quick+Ruby" rel="tag"></a><a href="http://technorati.com/tag/Instant+Rails" rel="tag"></a><a href="http://technorati.com/tag/Pune+Ruby" rel="tag"></a><a href="http://technorati.com/tag/Quick+Ruby+Guide" rel="tag"></a><a href="http://technorati.com/tag/Programming+Languages" rel="tag"></a><a href="http://technorati.com/tag/Blogs" rel="tag"></a><a href="http://technorati.com/tag/Ruby" rel="tag"></a><a href="http://technorati.com/tag/PuneRuby" rel="tag"></a><a href="http://technorati.com/tag/QuickRuby" rel="tag"></a><a href="http://technorati.com/tag/PuneBloggers" rel="tag"></a><a href="http://technorati.com/tag/PuneBlogs" rel="tag"></a><a href="http://technorati.com/tag/Blogosphere" rel="tag"></a><a href="http://technorati.com/tag/Digg" rel="tag"></a><a href="http://technorati.com/tag/Media" rel="tag"></a><a href="http://technorati.com/tag/Tip" rel="tag"></a><a href="http://technorati.com/tag/RSS" rel="tag"></a><a href="http://technorati.com/tag/Marketing" rel="tag"></a><a href="http://technorati.com/tag/News" rel="tag"></a><a href="http://technorati.com/tag/IndianGuru" rel="tag"></a><a href="http://technorati.com/tag/Blogging" rel="tag"></a><a href="http://technorati.com/tag/Internet" rel="tag"></a><a href="http://technorati.com/tag/Blog" rel="tag"></a><a href="http://technorati.com/tag/Technical+Support" rel="tag"></a><a href="http://technorati.com/tag/Free+Software" rel="tag"></a><a href="http://technorati.com/tag/Help" rel="tag"></a><a href="http://technorati.com/tag/Pune" rel="tag"></a><a href="http://technorati.com/tag/SatishTalim" rel="tag"></a><a href="http://technorati.com/tag/Satish+Talim" rel="tag"></a><a href="http://technorati.com/tag/Weblog" rel="tag"></a><a href="http://technorati.com/tag/Weblogs" rel="tag"></a><a href="http://technorati.com/tag/Training" rel="tag"></a><a href="http://technorati.com/tag/Free+Training" rel="tag"></a><a href="http://technorati.com/tag/Tutorial" rel="tag"></a><a href="http://technorati.com/tag/Education" rel="tag"></a><a href="http://technorati.com/tag/Teacher" rel="tag"></a><a href="http://technorati.com/tag/Learning+Ruby" rel="tag"></a>
</div>

Technorati Tags: <a href="http://technorati.com/tag/JRuby%3A+Caffeinated+Ruby" rel="tag">JRuby: Caffeinated Ruby</a>, <a href="http://technorati.com/tag/Java" rel="tag">Java</a>, <a href="http://technorati.com/tag/JRuby" rel="tag">JRuby</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>
