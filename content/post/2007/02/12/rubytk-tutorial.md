---
author: Satish Talim
categories:
- ruby
date: 2007-02-12
layout: post
title: Ruby/Tk Tutorial
---

#### Ruby/Tk

Ruby/Tk provides Ruby with a graphical user interface (GUI). The Tk
extension works on Windows, Mac OS X and Unix systems.

Previous versions of the Ruby One-Click Installer contained an (old)
version of Tcl/Tk. Now this Ruby installer only contains the Ruby
bindings to whatever version of Tcl/Tk you wish to install. It’s
recommended to use
[ActiveTcl](http://www.activestate.com/store/freedownload.aspx?prdGuid=f0cd6399-fefb-466e-ba17-220dcd6f4078).
Download the file `ActiveTcl8.4.13.0.261555-win32-ix86-threaded.exe` and
install it. Reboot your PC.

#### Simple Tk applications

Let’s understand the following program `hellotk.rb`:

    require 'tk'
    hello = TkRoot.new {title "Hello World"}
    Tk.mainloop

The [Tk documentation](http://www.jbrowse.com/text/rubytk_en.html) shows
the class hierarchy. Briefly, the hierarchy is as follows:

Object-\>TclTkIp-\>TkKernel-\>TkObject-\>TkWindow-\>TkRoot\
Object-\>TclTkIp-\>TkKernel-\>TkObject-\>TkWindow-\>TkLabel-\>TkButton

There are many modules like:

* `Tk`
* `Tk::Wm`

and many others.

`TkKernel` is the superclass of `TkObject`. The subclass redefines
the class method `new` to take a block.\
`TkObject` is the superclass of all widgets and has an included Tk
module.\
`TkRoot` class represents the root widget. The root widget is at the
top of the Ruby/Tk widget hierarchy and has the included module
`Tk::Wm` for communicating with a window manager. The methods
introduced here are normally used as instance methods of `TkRoot`.

In the program, after loading the tk extension module, we create a
root-level frame using `TkRoot.new`. With Tk you create widgets and
then bind code blocks to them. When something happens (like the user
clicking a widget), Tk runs the appropriate code block. In our program,
we use the `title` and `minsize` instance methods (of module
`Tk::Wm`) in the code block to `TkRoot.new`. We are now ready with
our GUI and we invoke `Tk.mainloop`

Let us now add some widgets to the above program, namely a `TkLabel`.
The modified program is hellotk1.rb

    require 'tk'
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
    Tk.mainloop

Here, we make a `TkLabel` widget (representing a label) as a child of
the root frame, setting several options for the label. Finally, we pack
the root frame and enter the main GUI event loop.

We also need to be able to get information back from our widgets while
our program is running by setting up callbacks (routines invoked when
certain events happen) and sharing data. The next example, hellotk2.rb
does that.

    require 'tk'
    TkButton.new do
      text "EXIT"
      command { exit }
      pack('side'=>'left', 'padx'=>10, 'pady'=>10)
    end
    Tk.mainloop

Callbacks are very easy to setup. The `command` option takes a
`Proc` object, which will be called when the callback fires. This
means that the code block passed into the command method is run when the
user clicks the button, allowing you to programmatically execute the
same functionality that would be invoked on an actual button press. Note
that the `Kernel\#exit` method terminates your program here.

We shall now build a rudimentary GUI interface to our SOAP server hosted
at www.puneruby.com. The program is the soapguiclient.rb

    require 'soap/rpc/driver'
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
    #---

In the above program, we reconfigure a widget while it’s running. Every
widget supports the `configure` method, which takes a code block in
the same manner as `new`. We have also modified the soapserver.rb
program shown earlier to soapserver2.rb. We have included the `Logger`
class.

    require 'logger'
    require 'soap/rpc/standaloneServer'

    class MyServer < SOAP::RPC::StandaloneServer
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

    server = MyServer.new('PuneRubyServer', 'urn:mySoapServer', 'www.puneruby.com', 12321)
    trap('INT') {server.shutdown}
    server.start

The `Logger` class helps write log messages to a file or stream. It
supports time- or size-based rolling of log files. Messages can be
assigned severities, and only those messages at or above the logger's
current reporting level will be logged. Here, we log to a file called
soapserver.log, which is rotated when it gets about 10K bytes and keeps
up to five old files.

Technorati Tags: [Ruby/Tk](http://technorati.com/tag/Ruby%2FTk),
[Ruby/Tk Tutorial](http://technorati.com/tag/Ruby%2FTk+Tutorial)
