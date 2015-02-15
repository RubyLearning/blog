---
title: An Introduction to Desktop Apps with Ruby
author: Martin Sadler
date: 2010-09-29
layout: post
permalink: /2010/09/29/an-introduction-to-desktop-apps-with-ruby/
thesis_keywords:
  - Ruby, Programming, Martin Sadler, JRuby, Ruby for Noobs, Ruby beginners
thesis_description:
  - Martin Sadler gives you an insight into the world of possibilities with JRuby and desktop applications. A guest blog post on RubyLearning.
topsy_short_url:
  - http://bit.ly/b13GbN
categories:
  - Beginners
  - Ruby
  - Ruby Masters
tags:
  - JRuby
  - Martin Sadler
  - programming
  - Ruby
  - Ruby Beginners
  - Ruby for Noobs
---
<div>
  <h3>
    An Introduction to Desktop Apps with Ruby
  </h3>
  
  <p class="update">
    This guest post is contributed by <b><a href="http://beyondthetype.com/">Martin Sadler</a></b>, who has over 10 years experience in the web development industry working with a range of successful high profile businesses, public sector organisations, and individuals. He is best known in the Ruby community as the creator of <a href="http://workingwithrails.com">Working With Rails</a> and is a keen advocate of the Ruby on Rails Framework.
  </p>
  
  <h3>
    Introduction
  </h3>
  
  <p class="block">
    <img class="alignright" height="125" width="125" src="http://rubylearning.com/images/msadler125x125.jpg" title="Martin Sadler" alt="Martin Sadler" /> <span class="drop_cap">I</span>n this article I&rsquo;m going to show you how easy it is to create a nifty little cross-platform system tray/menu bar application using <a href="http://jruby.org/">JRuby</a>.
  </p>
  
  <p>
    The application enables a user to take a screenshot of their desktop and then do something interesting with it!
  </p>
  
  <p>
    <img src="http://beyondthetype.com/assets/13/trayapp.png" alt="&quot;Screenshot Tray Application&quot;" />
  </p>
  
  <h3>
    What&rsquo;s covered in this article
  </h3>
  
  <p>
    Some of the key areas covered include:
  </p>
  
  <ul>
    <li>
      Using Java Classes within Ruby
    </li>
    <li>
      Refactoring
    </li>
    <li>
      Blocks
    </li>
  </ul>
  
  <p>
    <b>Note</b>: This tutorial assumes no prior Java knowledge and covers basic Ruby concepts only.
  </p>
  
  <h3>
    What is JRuby?
  </h3>
  
  <p>
    <a href="http://jruby.org/">JRuby</a> is a version of Ruby that runs on top of the <a href="http://en.wikipedia.org/wiki/Java_Virtual_Machine">JVM</a>. It runs just the same as regular <a href="http://en.wikipedia.org/wiki/Ruby_MRI">MRI Ruby</a> except it&rsquo;s about twice as fast and you get access to existing Java libraries.
  </p>
  
  <h3>
    Getting started with JRuby
  </h3>
  
  <p>
    It&rsquo;s never been easier to try <a href="http://jruby.org/">JRuby</a> out. <a href="http://rvm.beginrescueend.com/">RVM</a> is your friend here. Assuming you have <a href="http://rvm.beginrescueend.com/">RVM</a> already installed it&rsquo;s simply a case of doing the following inside your terminal session:
  </p>
  
  <pre><code>rvm install jruby
</code></pre>
  
  <p>
    and then (where x.y.z is the version of JRuby)
  </p>
  
  <pre><code>rvm use jruby-x.y.z
</code></pre>
  
  <p>
    From this point all your normal ruby commands will be using JRuby in the current terminal. Sweet.
  </p>
  
  <h4>
    Part 1: Taking a screenshot
  </h4>
  
  <p>
    <img src="http://farm3.static.flickr.com/2079/2212063279_05ab378426_m.jpg" alt="Robot" style="float: left; padding: 5px; " />
  </p>
  
  <p>
    <a href="http://download-llnw.oracle.com/javase/6/docs/api/java/awt/Robot.html">Robot</a> does for the Desktop what <a href="http://seleniumhq.org/">Selenium</a> and other automation tools do for the browser. The main difference is that you have far more access to a users machine. You can move the mouse around, control keystrokes, manipulate other programs, and most usefully take a screenshot.
  </p>
  
  <p>
    What is <a href="http://download-llnw.oracle.com/javase/6/docs/api/java/awt/Robot.html">Robot</a>? It&rsquo;s a Java class and we going to make good use of it in our first script.
  </p>
  
  <h4>
    Our first JRuby script
  </h4>
  
  <p style="text-align: right; font-style:italic">
    example1.rb
  </p>
  
  <pre><code>#----------------------------------------------------------------
# Summary: Takes a screenshot of the desktop and saves to disk
#----------------------------------------------------------------

# this gives us direct access to Java classes in Ruby
include Java

# here we are importing Java classes, just like you might require 'yaml' or 'date'
import java.awt.Robot
import java.awt.Toolkit
import java.awt.Rectangle
import javax.imageio.ImageIO

# Taking the screenshot
# 1) Create a new instance of the Robot class
# 2) Use the Toolkit class to get the size of the screen
# 3) and pass those dimensions to the Robot instance for capture
robot     = Robot.new
toolkit   = Toolkit.get_default_toolkit
dim       = toolkit.get_screen_size
rectangle = Rectangle.new(0, 0, dim.get_width, dim.get_height)
image     = robot.create_screen_capture(rectangle)

# Save the file to disk
file = java::io::File.new('test.png')
ImageIO::write(image, "png", file)
</code></pre>
  
  <p>
    Running the above script is a simple case of:
  </p>
  
  <pre><code>ruby example1.rb
</code></pre>
  
  <p>
    The resulting screenshot gets saved to the same directory you are in as &lsquo;test.png&rsquo;. Result.
  </p>
  
  <p style="padding-left: 14px; border-left: 8px green solid; margin-left: 14px;  margin-bottom: 50px">
    <strong>Tip:</strong> One question you might be asking by this point is how do you know what classes are available when you include Java? <a href="http://download-llnw.oracle.com/javase/6/docs/api/">Java API docs</a> have the answer.<br />Now, although helpful, it&#8217;s still pure Java so you&#8217;ll need to do a bit of translating to the equivalent JRuby calls. The tree view makes it easier to see how all the classes fit together.
  </p>
  
  <p>
    So we&rsquo;ve got a script to take a screenshot, it does the job, but we can make it better.
  </p>
  
  <h4>
    Refactoring into a re-usable Ruby Class
  </h4>
  
  <p style="text-align: right; font-style:italic">
    screenshot.rb
  </p>
  
  <pre><code>class Screenshot
  include Java

  import java.awt.Robot
  import java.awt.Toolkit
  import java.awt.Rectangle
  import javax.imageio.ImageIO

  def self.capture(filename = 'screenshot.png')
    robot     = Robot.new
    toolkit   = Toolkit.get_default_toolkit
    dim       = toolkit.get_screen_size
    rectangle = Rectangle.new(0, 0, dim.get_width, dim.get_height)
    image     = robot.create_screen_capture(rectangle)
    file  = java::io::File.new(filename)
    ImageIO::write(image, "png", file)
  end

end
</code></pre>
  
  <p>
    now fire up a copy of irb and enter the following:
  </p>
  
  <pre><code>require 'screenshot'
Screenshot.capture('screenshot1.png')
</code></pre>
  
  <p>
    By moving the code into a class method it&rsquo;s much tidier and easier to use for the next part of the application.
  </p>
  
  <p style="padding-left: 14px; border-left: 8px orange solid; margin-left: 14px; margin-bottom: 50px">
    <strong>Gotcha:</strong> File naming is really important here. The Ruby class defined in the file must be the CamelCase version of the filename for the require to work otherwise you&#8217;ll get errors like :<br />LoadError: use &#8216;java_import&#8217; to load normal Java classes<br />Note, this is only the case in JRuby not regular MRI Ruby
  </p>
  
  <h3>
    Part 2: Creating the system tray application
  </h3>
  
  <p>
    Now we have a class for taking a screenshot lets create the system tray application:
  </p>
  
  <p style="text-align: right; font-style:italic">
    example2.rb
  </p>
  
  <pre><code>#-----------------------------------------------------------------------------
# Summary: Runs a system tray application with ability to take a screenshot
#-----------------------------------------------------------------------------

require 'screenshot'

# Import the Java class libraries we wish to use
include Java
import java.awt.TrayIcon
import java.awt.Toolkit

# Setup our menu items
exititem        = java.awt.MenuItem.new("Exit")
screenshotitem  = java.awt.MenuItem.new("Take Screenshot...")
aboutitem       = java.awt.MenuItem.new("About")

# Event handling
exititem.add_action_listener {java.lang.System::exit(0)}
screenshotitem.add_action_listener {Screenshot.capture}

#&nbsp;Add the items to the popup menu itself
popup = java.awt.PopupMenu.new
popup.add(aboutitem)
popup.add(screenshotitem)
popup.add(exititem)

# Give the tray an icon and attach the popup menu to it
image    = java.awt.Toolkit::default_toolkit.get_image("screenshot.gif")
tray_icon = TrayIcon.new(image, "Screenshot!", popup)
tray_icon.image_auto_size = true

# Finally add the tray icon to the tray
tray = java.awt.SystemTray::system_tray
tray.add(tray_icon)
</code></pre>
  
  <p>
    Before you run this script make sure you have an icon named screenshot.gif in the same directory. Short of creating one you can use <a href="http://images.google.com/images?q=system+tray&hl=en&biw=1440&bih=684&gbv=2&tbs=isch:1,isz:i">Google to find an icon</a>.
  </p>
  
  <p>
    On running the application you&rsquo;ll see the menu appear in your system tray. Click the screenshot menu item and the screenshot gets saved to disk!
  </p>
  
  <p>
    <img src="http://beyondthetype.com/assets/13/trayapp.png" alt="&quot;Screenshot Tray Application&quot;" />
  </p>
  
  <h4>
    Refactor
  </h4>
  
  <p>
    The application is neat but it feels quite bulky, lets condense it down in to a much tighter API:
  </p>
  
  <p style="text-align: right; font-style:italic">
    example3.rb
  </p>
  
  <pre><code>require 'tray_application'; require 'screenshot';
app = TrayApplication.new("Deskshot")
app.icon_filename = 'screenshot.png'
app.item('Take Screenshot')  {Screenshot.capture}
app.item('Exit')              {java.lang.System::exit(0)}
app.run
</code></pre>
  
  <p>
    Not bad for an application of 6 lines! Where did all that code go?
  </p>
  
  <p style="text-align: right; font-style:italic">
    tray_application.rb
  </p>
  
  <pre><code>class TrayApplication

  include Java
  import java.awt.TrayIcon
  import java.awt.Toolkit

  attr_accessor :icon_filename
  attr_accessor :menu_items

  def initialize(name = 'Tray Application')
    @menu_items = []
    @name       = name
  end

  def item(label, &block)
    item = java.awt.MenuItem.new(label)
    item.add_action_listener(block)
    @menu_items &lt;&lt; item
  end

  def run
    popup = java.awt.PopupMenu.new
    @menu_items.each{|i| popup.add(i)}

    # Give the tray an icon and attach the popup menu to it
    image    = java.awt.Toolkit::default_toolkit.get_image(@icon_filename)
    tray_icon = TrayIcon.new(image, @name, popup)
    tray_icon.image_auto_size = true

    # Finally add the tray icon to the tray
    tray = java.awt.SystemTray::system_tray
    tray.add(tray_icon)
  end

end
</code></pre>
  
  <p>
    A similar pattern of refactoring was carried out here as per the Screenshot class.
  </p>
  
  <p>
    Probably the most interesting point is the way you can use Ruby to capture a block of code. In the case of the Screenshot application there are certain actions we only want to be executed when the user clicks a menu item. You can see these as code surrounded by curly braces. Alternatively they could have been written as follows:
  </p>
  
  <pre><code>app.item('Take Screenshot') do
  Screenshot.capture
end
</code></pre>
  
  <p>
    Which does more or less the same job. Usually the do/end format is preferred for multi-line code blocks.
  </p>
  
  <p>
    What is handy for us is that we can capture these code blocks using the &block parameter in the method definition. This makes the block available as a local variable inside the method and it can be simply pushed onto an array (@menu_items) for later recall.
  </p>
  
  <p>
    Curious as to how a block is executed once stored? Here is a simple example:
  </p>
  
  <pre><code>def hello(&block)
  block.call # execute the contents of the hello block using call
end

hello do
  p "hello there"
end
</code></pre>
  
  <p style="padding-left: 14px; border-left: 8px green solid; margin-left: 14px;  margin-bottom: 50px">
    <strong>Tip:</strong> Always try to keep your code tidy as you go along. Look for patterns and bake them into classes if need be. Think about how the end product will look like and work out how to get there. See also: <a href="http://tom.preston-werner.com/2010/08/23/readme-driven-development.html">Readme Driven Development</a>.
  </p>
  
  <h3>
    Part 4: One further improvement
  </h3>
  
  <p>
    So now we have a tray application that takes a screenshot and saves to disk. How about we get it to open in an image browser too. No problem.
  </p>
  
  <p>
    Lets make a small addition by making use of the <a href="http://download-llnw.oracle.com/javase/6/docs/api/java/awt/Desktop.html">Desktop Java Class</a>.
  </p>
  
  <p style="text-align: right; font-style:italic">
    screenshot.rb (revisited)
  </p>
  
  <pre><code>class Screenshot
  include Java

  import java.awt.Desktop # added Desktop to import
  import java.awt.Robot
  import java.awt.Toolkit
  import java.awt.Rectangle
  import javax.imageio.ImageIO

  def self.capture(filename = 'screenshot.png')
    robot     = Robot.new
    toolkit   = Toolkit.get_default_toolkit
    dim       = toolkit.get_screen_size
    rectangle = Rectangle.new(0, 0, dim.get_width, dim.get_height)
    image     = robot.create_screen_capture(rectangle)

    file  = java::io::File.new(filename)
    ImageIO::write(image, "png", file)

    # Open the file in the users default application for the given file type
    desktop = Desktop.get_desktop
    desktop.open(file)
   end
  end

end
</code></pre>
  
  <p>
    So now when you click &lsquo;Take Screenshot..&rsquo; up pops Preview (on Mac) with your Desktop image.
  </p>
  
  <h3>
    Beyond the screenshot
  </h3>
  
  <p>
    So we have put together the foundations of a screenshot tray application and in the process built a skeleton GUI <a href="http://jruby.org/">JRuby</a> framework. So where could we go from here?
  </p>
  
  <ul>
    <li>
      <p>
        Send the screenshot to a web service
      </p>
      
      <p>
        This would make for a handy utility for a <a href="http://lighthouseapp.com/">support web app</a>. Take the file and post it via http to your app for processing.
      </p>
    </li>
    
    <li>
      <p>
        Add an About Box
      </p>
      
      <p>
        Sadly the amount of code to show this here would have detracted from the main article. However it is still pretty straight forward. JFrame is your friend.
      </p>
    </li>
    
    <li>
      <p>
        HotKey for taking the screenshot
      </p>
    </li>
    
    <li>
      <p>
        Package! <a href="http://rawr.rubyforge.org/">Rawr</a>. Distribute
      </p>
      
      <p>
        So currently you&rsquo;ll need JRuby in order to run this application. One of the main benefits of JRuby is it compiles down to <a href="http://en.wikipedia.org/wiki/Java_bytecode">Java bytecode</a> and will run on any Java enabled platform. Mac, Windows, and Unix support in one go!
      </p>
    </li>
    
    <li>
      <p>
        Variations on the theme
      </p>
      
      <p>
        Why stop at screenshots? Here are few more ideas:
      </p>
      
      <ul>
        <li>
          Drag and drop copy and upload of files to a web service
        </li>
        <li>
          A notification service e.g. new support messages, tweets
        </li>
        <li>
          System analytics tool
        </li>
        <li>
          Copy and Paste share bin
        </li>
      </ul>
    </li>
  </ul>
  
  <h3>
    Reference
  </h3>
  
  <ul>
    <li>
      <a href="http://jruby.org/">JRuby Homepage</a>
    </li>
    <li>
      <a href="http://download-llnw.oracle.com/javase/6/docs/api/java/awt/package-tree.html">Java API AWT docs</a>
    </li>
    <li>
      <a href="http://kenai.com/projects/jruby/pages/GUIFrameworks">JRuby GUI Frameworks</a>
    </li>
  </ul>
  
  <h3>
    Attribution
  </h3>
  
  <ul>
    <li>
      Robot Image: <a href="http://www.flickr.com/photos/loresjoberg/2212063279">http://www.flickr.com/photos/loresjoberg/2212063279</a>
    </li>
  </ul>
  
  <h3>
    In Summary
  </h3>
  
  <p>
    <em>I hope you found this article valuable and that it gives you an insight into the world of possibilities with JRuby and desktop applications. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
  
  <p>
    <b><em>Do read</em> these awesome Guest Posts:</b>
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/28/the-ruby-movement/">The Ruby movement</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/27/almost-everything-is-an-object-and-everything-is-almost-an-object/">Almost everything is an object (and everything is almost an object!)</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/24/so-youre-new-to-ruby/">So… you’re new to Ruby!</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/23/incorporating-web-apis-to-spark-computer-programming-exercises/">Incorporating Web APIs to spark computer programming exercises</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/22/14-ways-to-have-fun-coding-ruby/">14 Ways To Have Fun Coding Ruby</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/21/writing-modular-web-applications-with-rack/">Writing modular web applications with Rack</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/20/how-to-learn-ruby-or-any-programming-language/">How to Learn Ruby (or any programming language)</a>
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Programming" rel="tag"> Programming</a>, <a href="http://technorati.com/tag/Martin+Sadler" rel="tag"> Martin Sadler</a>, <a href="http://technorati.com/tag/JRuby" rel="tag"> JRuby</a>, <a href="http://technorati.com/tag/Ruby+for+Noobs" rel="tag"> Ruby for Noobs</a>, <a href="http://technorati.com/tag/Ruby+beginners" rel="tag"> Ruby beginners</a>
