---
title: Ruby/Tk Tutorial
author: Satish Talim
date: 2007-02-12
layout: post
permalink: /2007/02/12/rubytk-tutorial/
dsq_thread_id:
  - 208368536
categories:
  - Ruby
---
<div>
  <!--adsense-->
</div>

<div>
  <h4>
    Ruby/Tk
  </h4>
  
  <p>
    Ruby/Tk provides Ruby with a graphical user interface (GUI). The <span class="sidenote" title="Tk works along a composition model - that is, you start by creating a container (such as a <strong>TkFrame</strong> or <strong>TkRoot</strong>) and then create widgets (GUI components) that populate it, such as buttons or labels. When you are ready to start the GUI, you invoke <strong>Tk.mainloop</strong>. The Tk engine then takes control of the program, displaying widgets and calling your code in response to GUI events.">Tk</span> extension works on Windows, Mac OS X and Unix systems.
  </p>
  
  <p>
    Previous versions of the Ruby One-Click Installer contained an (old) version of Tcl/Tk. Now this Ruby installer only contains the Ruby bindings to whatever version of Tcl/Tk you wish to install. It&#8217;s recommended to use <a href="http://www.activestate.com/store/freedownload.aspx?prdGuid=f0cd6399-fefb-466e-ba17-220dcd6f4078">ActiveTcl</a>. Download the file <u>ActiveTcl8.4.13.0.261555-win32-ix86-threaded.exe</u> and install it. Reboot your PC.
  </p>
  
  <h4>
    Simple Tk applications
  </h4>
  
  <p>
    Let&#8217;s understand the following program hellotk.rb
  </p>
  
  <pre>require 'tk'
hello = TkRoot.new {title "Hello World"}
Tk.mainloop</pre>
  
  <p>
    The <a href="http://www.jbrowse.com/text/rubytk_en.html" >Tk documentation</a> shows the class hierarchy. Briefly, the hierarchy is as follows:
  </p>
  
  <p>
    Object->TclTkIp->TkKernel->TkObject->TkWindow->TkRoot<br />Object->TclTkIp->TkKernel->TkObject->TkWindow->TkLabel->TkButton
  </p>
  
  <p>
    There are many modules like:<br /><strong>Tk, Tk::Wm</strong> and many others.
  </p>
  
  <p>
    <strong>TkKernel</strong> is the superclass of <strong>TkObject</strong>. The subclass redefines the class method <strong>new</strong> to take a block.<br /><strong>TkObject</strong> is the superclass of all widgets and has an included Tk module.<br /><strong>TkRoot</strong> class represents the root widget. The root widget is at the top of the Ruby/Tk widget hierarchy and has the included module <strong>Tk::Wm</strong> for communicating with a window manager. The methods introduced here are normally used as instance methods of <strong>TkRoot</strong>.
  </p>
  
  <p>
    In the program, after loading the tk extension module, we create a root-level frame using <strong>TkRoot.new</strong>. With Tk you create widgets and then bind code blocks to them. When something happens (like the user clicking a widget), Tk runs the appropriate code block. In our program, we use the <strong>title</strong> and <strong>minsize</strong> instance methods (of module <strong>Tk::Wm</strong>) in the code block to <strong>TkRoot.new</strong>. We are now ready with our GUI and we invoke <strong>Tk.mainloop</strong>
  </p>
  
  <p>
    Let us now add some widgets to the above program, namely a <strong>TkLabel</strong>. The modified program is hellotk1.rb
  </p>
  
  <pre>require 'tk'
hello = TkRoot.new do
  title "Hello World"
  # the min size of window
  minsize(400,400)
end
TkLabel.new(hello) do
  text 'Hello World'
  foreground 'red'
  pack { padx 15; pady 15; side 'left'}
end
Tk.mainloop</pre>
  
  <p>
    Here, we make a <strong>TkLabel</strong> widget (representing a label) as a child of the root frame, setting several options for the label. Finally, we pack the root frame and enter the main GUI event loop.
  </p>
  
  <p>
    We also need to be able to get information back from our widgets while our program is running by setting up callbacks (routines invoked when certain events happen) and sharing data. The next example, hellotk2.rb does that.
  </p>
  
  <pre>require 'tk'
TkButton.new do
  text "EXIT"
  command { exit }
  pack('side'=>'left', 'padx'=>10, 'pady'=>10)
end
Tk.mainloop</pre>
  
  <p>
    Callbacks are very easy to setup. The <strong>command</strong> option takes a <strong>Proc</strong> object, which will be called when the callback fires. This means that the code block passed into the command method is run when the user clicks the button, allowing you to programmatically execute the same functionality that would be invoked on an actual button press. Note that the <strong>Kernel#exit</strong> method terminates your program here.
  </p>
  
  <p>
    We shall now build a rudimentary GUI interface to our SOAP server hosted at www.puneruby.com. The program is the soapguiclient.rb
  </p>
  
  <pre>require 'soap/rpc/driver'

require 'tk'

 

class SOAPGuiClient

  def connect

    @buttonconnect.configure('text' => 'Reset')

    @buttonconnect.command { reset }

    begin

      driver = SOAP::RPC::Driver.new('http://217.160.200.122:12321/',

                                     'urn:mySoapServer')

      driver.add_method('sayhelloto', 'username')

      s = driver.sayhelloto('Satish Talim')

    rescue Exception => e

      s = "Exception occured: " + e

    ensure

      @label.configure('text' => s)

    end

  end #connect

 

  def reset

    @label.configure('text' => "")

    @buttonconnect.configure('text' => 'Connect')

    @buttonconnect.command { connect }

  end # reset

 

#---

  def initialize

    root = TkRoot.new do

      title 'SOAP Client'

      # the min size of window

      minsize(535, 100)

    end

#---

    @label = TkLabel.new(root) do

      pack

    end

#---

    @buttonconnect = TkButton.new(root)

    @buttonconnect.configure('text' => 'Connect')

    @buttonconnect.command { connect }

    @buttonconnect.pack('side'=>'bottom')

#---

    Tk.mainloop

  end #initialize

end # class

 

SOAPGuiClient.new

#---</pre>
  
  <p>
    In the above program, we reconfigure a widget while it&#8217;s running. Every widget supports the <strong>configure</strong> method, which takes a code block in the same manner as <strong>new</strong>. We have also modified the soapserver.rb program shown earlier to soapserver2.rb. We have included the <strong>Logger</strong> class.
  </p>
  
  <pre>require 'logger'

require 'soap/rpc/standaloneServer'

class MyServer &lt; SOAP::RPC::StandaloneServer

  def initialize(* args)

    super

    add_method(self, 'sayhelloto', 'username')

    @log = Logger.new("soapserver.log", 5, 10*1024)  

  end

  def sayhelloto(username)

    t = Time.now

    @log.info("#{username} logged on #{t}")

    "Hello, #{username} on #{t}."

  end

end

 

server = MyServer.new('PuneRubyServer','urn:mySoapServer','www.puneruby.com',12321)

trap('INT') {server.shutdown}

server.start</pre>
  
  <p>
    The <strong>Logger</strong> class helps write log messages to a file or stream. It supports time- or size-based rolling of log files. Messages can be assigned severities, and only those messages at or above the logger's current reporting level will be logged. Here, we log to a file called soapserver.log, which is rotated when it gets about 10K bytes and keeps up to five old files.
  </p>
</div>

<div>
  <a href="http://technorati.com/tag/Instant+Rails" rel="tag"></a><a href="http://technorati.com/tag/Quick+Ruby" rel="tag"></a><a href="http://technorati.com/tag/Instant+Rails" rel="tag"></a><a href="http://technorati.com/tag/Pune+Ruby" rel="tag"></a><a href="http://technorati.com/tag/Quick+Ruby+Guide" rel="tag"></a><a href="http://technorati.com/tag/Programming+Languages" rel="tag"></a><a href="http://technorati.com/tag/Blogs" rel="tag"></a><a href="http://technorati.com/tag/Ruby" rel="tag"></a><a href="http://technorati.com/tag/PuneRuby" rel="tag"></a><a href="http://technorati.com/tag/QuickRuby" rel="tag"></a><a href="http://technorati.com/tag/PuneBloggers" rel="tag"></a><a href="http://technorati.com/tag/India" rel="tag"></a><a href="http://technorati.com/tag/PuneBlogs" rel="tag"></a><a href="http://technorati.com/tag/Blogosphere" rel="tag"></a><a href="http://technorati.com/tag/Digg" rel="tag"></a><a href="http://technorati.com/tag/Media" rel="tag"></a><a href="http://technorati.com/tag/Tip" rel="tag"></a><a href="http://technorati.com/tag/RSS" rel="tag"></a><a href="http://technorati.com/tag/Marketing" rel="tag"></a><a href="http://technorati.com/tag/News" rel="tag"></a><a href="http://technorati.com/tag/IndianGuru" rel="tag"></a><a href="http://technorati.com/tag/Blogging" rel="tag"></a><a href="http://technorati.com/tag/Internet" rel="tag"></a><a href="http://technorati.com/tag/Blog" rel="tag"></a><a href="http://technorati.com/tag/Technical+Support" rel="tag"></a><a href="http://technorati.com/tag/Free+Software" rel="tag"></a><a href="http://technorati.com/tag/Help" rel="tag"></a><a href="http://technorati.com/tag/Pune" rel="tag"></a><a href="http://technorati.com/tag/SatishTalim" rel="tag"></a><a href="http://technorati.com/tag/Satish+Talim" rel="tag"></a><a href="http://technorati.com/tag/Weblog" rel="tag"></a><a href="http://technorati.com/tag/Weblogs" rel="tag"></a><a href="http://technorati.com/tag/Training" rel="tag"></a><a href="http://technorati.com/tag/Free+Training" rel="tag"></a><a href="http://technorati.com/tag/Tutorial" rel="tag"></a><a href="http://technorati.com/tag/Education" rel="tag"></a><a href="http://technorati.com/tag/Teacher" rel="tag"></a><a href="http://technorati.com/tag/Learning+Ruby" rel="tag"></a>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby%2FTk" rel="tag">Ruby/Tk</a>, <a href="http://technorati.com/tag/Ruby%2FTk+Tutorial" rel="tag"> Ruby/Tk Tutorial</a>
