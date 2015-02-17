---
title: 'JRuby: Caffeinated Ruby'
author: Satish Talim
date: "2007-04-27"
layout: post
permalink: /2007/04/27/jruby-caffeinated-ruby/
categories:
- jruby
- rails
- ruby
---
Recently, **[JRuby](http://jruby.codehaus.org/)** has been gaining more
and more attention in the Java and Ruby communities. Java is a powerful
platform and there are millions of lines of Java code being written each
month, that the world will have to live with for a long time from now.
By leveraging Java the platform with the power of the Ruby programming
language, programmers get the best from both worlds. *You better not
ignore JRuby any more!*

**What is JRuby**?

**JRuby** is a 100% pure-Java implementation of the Ruby programming
language that runs in the JVM. JRuby’s creators, [Thomas
Enebo](http://www.bloglines.com/blog/ThomasEEnebo) and [Charles
Nutter](http://rubylearning.com/blog/2007/04/26/interview-charles-nutter/),
have been hired by [Sun](http://www.sun.com/) to work on JRuby full
time. The current JRuby release 0.9.9 is fully compatible with Ruby
1.8.5.

[Ola Bini](http://ola-bini.blogspot.com/) says that "JRuby is ready for
prime time. Application developers should try their applications on
JRuby NOW."

So, I decided to take a quick look at JRuby and found it very easy to
use.

**Download and Setup:**

-   The [JRuby distribution](http://dist.codehaus.org/jruby/) comes as a
tar.gz file, namely jruby-bin-0.9.9.tar.gz
-   Uncompress the archive; you should end up with a **jruby-0.9.9**
folder.
-   In Windows, set the system environment variable **JRUBY\_HOME** to
C:\\jruby-0.9.9 I am assuming that you have uncompressed JRuby to C:
-   Also, set the system environment variable **path** to
C:\\jruby-0.9.9\\bin;
-   The JRuby distribution’s bin directory contains the jruby.bat file
that is used to run the JRuby interpreter. Run the command **jruby
-version** from the command line to test that the JRuby is working.
On my PC, it said:\
**ruby 1.8.5 (2007-04-23 rev 3539) [x86-jruby0.9.9]**

**Where to use JRuby?:**

​a. ***JRuby allows Ruby programs to use Java classes***. This is a
powerful concept that JRuby now brings to Ruby users. My [Ruby/Tk
Tutorial](http://rubylearning.com/satishtalim/ruby_tk_tutorial.html) has
a program **p075hellotk1.rb** that uses Ruby/Tk a graphical user
interface. However, the documentation for Ruby/Tk is extremely poor and
I would be comfortable in using Java Swing instead. The code in JRuby
for the program p075hellotk1.rb can be something like this:

# javaSwingHello.rb
require 'java' # Line 2
JFrame = javax.swing.JFrame
JLabel = javax.swing.JLabel
frame  = JFrame.new
jlabel = JLabel.new("Hello World")
frame.add(jlabel)
frame.setDefaultCloseOperation(JFrame::EXIT_ON_CLOSE)
frame.pack
frame.setVisible(true)

Run the above program from the command line as follows:

**jruby javaSwingHello.rb**

Line 2: The second line of the above program enables JRuby’s Java
support and allows a Ruby program to use Java classes.

​b. ***Calling JRuby from Java***. JRuby can just as easily be called
from Java, using either the JSR 223 Scripting for Java 6 or the [Apache
Bean Scripting](http://en.wikipedia.org/wiki/Bean_Scripting_Framework)
framework. More information on this is available in the [JRuby
Wiki](http://www.headius.com/jrubywiki/index.php/Main_Page)

​c. ***Running Rails with JRuby***. The advantages are obvious. To quote
the JRuby Wiki:

-   Gives Rails the power and functionality of Java: Virtual Machine,
application servers, and libraries.
-   With future JVM and JRuby improvements, JRuby may be faster than
Matz’ Ruby Interpreter in running Rails
-   Gets Rails in the door of Java shops by making Rails apps into
Java-platform apps.

To conclude, I am surely liking JRuby and would definitely explore it
further. **Ignore JRuby at your own peril !**

**Resources:**

-   [JRuby Home Page](http://jruby.codehaus.org/)
-   [JRuby Wiki](http://www.headius.com/jrubywiki/index.php/Main_Page)
-   [Rails on
JRuby](http://www.headius.com/jrubywiki/index.php/JRuby_on_Rails)
-   [JRuby Forum](http://www.nabble.com/JRuby---User-f14107.html)
-   [JRuby and the Java
Platform](http://java.sun.com/developer/technicalArticles/scripting/jruby/)

Go on! **[Digg
It](http://rubylearning.com/blog/2007/04/27/jruby-caffeinated-ruby/)** !

Technorati Tags: [JRuby: Caffeinated
Ruby](http://technorati.com/tag/JRuby%3A+Caffeinated+Ruby),
[Java](http://technorati.com/tag/Java),
[JRuby](http://technorati.com/tag/JRuby),
[Ruby](http://technorati.com/tag/Ruby)

