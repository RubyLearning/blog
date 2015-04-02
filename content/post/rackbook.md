+++
draft = false
title = "What's Rack"
date = "2013-04-02T02:03:43-04:00"
publishdate = "2015-04-04"
author = "Satish Talim"
authorfacebook = "http://www.facebook.com/satishtalim/about"
authorgoogleplus = "https://plus.google.com/+SatishTalim/about"
authorlink = "http://satishtalim.com"
authorlinkedin = "https://www.linkedin.com/in/satishtalim"
authortwitter = "http://twitter.com/IndianGuru"
categories = ['ebook', 'rack']
nocomment = false
socialsharing = true
tags = ["Satish Talim", "rack", 'ebook']
totop = true

+++
**A Quick Introduction to Rack**

-- SATISH TALIM

Copyright 2013 Satish Talim

## What’s Rack?

In the words of the author of Rack – **Christian Neukirchen**: Rack aims
to provide a minimal API for connecting web servers supporting Ruby
(like WEBrick, Mongrel etc.) and Ruby web frameworks (like Rails,
Sinatra etc.).

Web frameworks such as Sinatra are built on top of Rack or have a Rack
interface for allowing web application servers to connect to them.

The premise of Rack is simple – it just allows you to easily deal with
HTTP requests.

HTTP is a simple protocol: it basically describes the activity of a
client sending a HTTP request to a server and the server returning a
HTTP response. Both HTTP request and HTTP response in turn have very
similar structures. A HTTP request is a triplet consisting of a method
and resource pair, a set of headers and an optional body while a HTTP
response is in triplet consisting of a response code, a set of headers
and an optional body.

Rack maps closely to this. A Rack application is a Ruby object that has
a call method, which has a single argument, the *environment*,
(corresponding to a HTTP request) and returns an array of 3 elements,
*status*, *headers* and *body* (corresponding to a HTTP response).

Rack includes *handlers* that connect Rack to all these web application
servers (WEBrick, Mongrel etc.).

Rack includes *adapters* that connect Rack to various web frameworks
(Sinatra, Rails etc.).


Between the server and the framework, Rack can be customized to your
applications needs using *middleware*. The fundamental idea behind Rack
middleware is – come between the calling client and the server, process
the HTTP request before sending it to the server, and processing the
HTTP response before returning it to the client.


![](data:image/jpeg;base64,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)

A Rack App

## Documentation

Read the full documentation of Rack at –
[http://rack.rubyforge.org/doc/](http://rack.rubyforge.org/doc/)

## Installing Rack

Note that I have Ruby 1.9+ installed on a Windows box and all the
programs in this article have been tested using that.

Let’s check if we already have rack with us. Open a command window and
type:

    irb --simple-prompt
    >> require 'rack'
    => true
    >>

Yes, rack’s already there on your machine. If rack’s not there you will
get an error like:

    LoadError: no such file to load -- rack

You can install rack by opening a new command window and typing:

    $ gem install rack

## A quick visit to Ruby’s proc object

Remember the [proc object from
Ruby](http://rubylearning.com/satishtalim/ruby_procs.html)? Blocks are
not objects, but they can be converted into objects of class Proc. This
can be done by calling the lambda method included in the Object class. A
block created with lambda acts like a Ruby method. The class Proc has a
method call that invokes the block.


In irb type:


    >> my_rack_proc = lambda { puts 'Rack Intro' }
    => #<Proc:0x1fc9038@(irb):2(lambda)>
    >> # method call invokes the block
    ?> my_rack_proc.call

Rack Intro

    => nil
    >>

## A simple Rack App – `my_rack_proc`

As mentioned earlier, our simple Rack application is a Ruby object (not
a class) that responds to call and takes exactly one argument, the
*environment*. The *environment* must be a true instance of Hash. The
app should return an Array of exactly three values: the *status* code
(it must be greater than or equal to 100), the *headers* (must be a
hash), and the *body* (the body commonly is an Array of Strings, the
application instance itself, or a File-like object. The body must
respond to method each and must only yield String values.) Let us create
our new Proc object. Type:

    >> my_rack_proc = lambda { |env| [200, {}, ["Hello. The time is #{Time.now}"]] }
    => #<Proc:0x1f4c358@(irb):5(lambda)>
    >>

Now we can call the Proc object my_rack_proc with the call method.
Type:

    >> my_rack_proc.call({})
    => [200, {}, ["Hello. The time is 2011-10-24 09:18:56 +0530"]]
    >>

`my_rack_proc` is our single line Rack application.

In the above example, we have used an empty hash for headers. Instead,
let’s have something in the header as follows:

    >> **my_rack_proc = lambda { |env| [200, {"Content-Type" => "text/plain"}, ["Hello. The time is #{Time.now}"]] }
    => #<Proc:0x1f4c358@(irb):5(lambda)>
    >>

Now we can call the Proc object `my_rack_proc` with the call method.
Type:


    >> my_rack_proc.call({})
    => [200, {"Content-Type" => "text/plain"}, ["Hello. The time is 2011-10-24 09:18:56 +0530"]]
    >>

We can run our Rack application (my_rack_proc) with any of the Rack
handlers.

To look at the Rack handlers available, in irb type:

    >> Rack::Handler.constants
    => [:CGI, :FastCGI, :Mongrel, :EventedMongrel, :SwiftipliedMongrel, :WEBrick, :LSWS, :SCGI, :Thin]
    >>

To get a handler for say WEBrick (the default WEBrick, web application
server, that comes along with Ruby), type:

    >> Rack::Handler::WEBrick
    => Rack::Handler::WEBrick
    >>

All of these handlers have a common method called `run` to run all the
Rack based applications.

    >> Rack::Handler::WEBrick.run my_rack_proc
    [2011-10-24 10:00:45] INFO WEBrick 1.3.1
    [2011-10-24 10:00:45] INFO ruby 1.9.2 (2011-07-09) [i386-mingw32]
    [2011-10-24 10:00:45] INFO WEBrick::HTTPServer#start: pid=1788 port=80

Open a browser window and type the url: `http://localhost/`

In your browser window, you should see a string, something like this:

    Hello. The time is 2011-10-24 10:02:20 +0530

**Note**: If you already have something running at port 80, you can run
this app at a different port, say 9876. Type:


    >> Rack::Handler::WEBrick.run my_rack_proc, :Port => 9876
    [2011-10-24 11:32:21] INFO WEBrick 1.3.1
    [2011-10-24 11:32:21] INFO ruby 1.9.2 (2011-07-09) [i386-mingw32]
    [2011-10-24 11:32:21] INFO WEBrick::HTTPServer#start: pid=480 port=9876

Open a browser window and type the url: <http://localhost:9876/>

In your browser window, you should see a string, something like this:

    Hello. The time is 2011-10-24 10:02:20 +0530

## Another Rack app – my_method

A Rack app need not be a lambda; it could be a method. Type:

    >> def my_method env
    >> [200, {}, ["method called"]]
    >> end
    => nil

We declare a method my_method that takes an argument env. The method
returns three values.

Next type:

    >> Rack::Handler::WEBrick.run method(:my_method)
    [2011-10-24 14:32:05] INFO WEBrick 1.3.1
    [2011-10-24 14:32:05] INFO ruby 1.9.2 (2011-07-09) [i386-mingw32]
    [2011-10-24 14:32:05] INFO WEBrick::HTTPServer#start: pid=1644 port=80

Open a browser window and type the url: `http://localhost/`

In your browser window, you should see something like this:

    method called

Method bjects are created by Object#method. They are associated with a
particular object (not just with a class). They may be used to invoke
the method within the object. The Method.call method invokes the method
with the specified arguments, returning the method’s return value.

Press `Ctrl-C` in irb to stop the `WEBrick` server.

## Using rackup

The rack gem comes with a bunch of useful stuff to make life easier for
a rack application developer. rackup is one of them.

rackup is a useful tool for running Rack applications. rackup
automatically figures out the environment it is run in, and runs your
application as FastCGI, CGI, or standalone with Mongrel or WEBrick – all
from the same configuration.

To use rackup, you’ll need to supply it with a rackup config file. By
convention, you should use .ru extension for a rackup config file.
Supply it a run RackObject and you’re ready to go:

    $ rackup config.ru

By default, rackup will start a server on port 9292.

To view rackup help, open a command window and type:

    $ rackup --help

Let us create a `config.ru` file that contains the following:

    run lambda { |env| [200, {"Content-Type" => "text/plain"}, ["Hello. The time is #{Time.now}"]] }

This file contains run, which can be called on anything that responds to
a `.call`.

To run our rack app, in the same folder that contains config.ru, type:

    $ rackup config.ru
    [2011-10-24 15:18:03] INFO WEBrick 1.3.1
    [2011-10-24 15:18:03] INFO ruby 1.9.2 (2011-07-09) [i386-mingw32]
    [2011-10-24 15:18:03] INFO WEBrick::HTTPServer#start: pid=3304 port=9292

Open a browser window and type the url: <http://localhost:9292/>

In your browser window, you should see something like this:

    Hello. The time is 2011-10-24 15:18:10 +0530

Press `Ctrl-C` to stop the `WEBrick` server.

Now let’s move our application from the config.ru file to `my_app.rb`
file as follows:

    # my_app.rb
    class MyApp
      def call env
        [200, {"Content-Type" => "text/html"}, ["Hello Rack Participants"]]
      end
    end

Also, our `config.ru` will change to:

    require './my_app'
    run MyApp.new

To run our rack app, in the same folder that contains config.ru, type:

    $ rackup config.ru
    [2011-10-25 06:18:16] INFO WEBrick 1.3.1
    [2011-10-25 06:18:16] INFO ruby 1.9.2 (2011-07-09) [i386-mingw32]
    [2011-10-25 06:18:16] INFO WEBrick::HTTPServer#start: pid=2224
    port=9292

Open a browser window and type the url: <http://localhost:9292/>

In your browser window, you should see something like this:

    Hello Rack Participants

Press `Ctrl-C` to stop the `WEBrick` server.

## Deploying Pure Rack Apps to Heroku

We shall now download and install Git. The precompiled packages are
available here: [http://git.or.cz/](http://git.or.cz/)

Select the relevant package for your operating system.

Please ensure that you are connected to the internet and then create an
account on Heroku (obviously do this only once) if you don’t have one –
[http://heroku.com/signup](http://heroku.com/signup).

Now install the Heroku Toolbelt:

Use the URL – [http://toolbelt.heroku.com](http://toolbelt.heroku.com/)

This ensures that you have access to the Heroku command-line client,
Foreman which is used to run applications locally, and the Git revision
control system that is used to deploy sites to Heroku.

Next, create a new folder, say rackheroku. Now assuming that you have
Git installed, open a Bash shell in that folder. You now need to
identify yourself to Git (you need to do this only once). With the bash
shell still open type in the following:

    $ git config --global user.name "Your name here"
    $ git config --global user.email "Your email id"

Git does not allow accented characters in user name. This will set the
info stored when you commit to a Git repository. Git has now been set
up.

If you don't already use SSH, you'll need to create a public/private key
pair to deploy code to Heroku. This keypair is used for the strong
cryptography and that uniquely identifies you as a developer when
pushing code changes.

You can use DSA keys if you prefer, using the -t dsa option. Heroku can
use either type of key. To generate a public key type:

    $ ssh-keygen -t rsa
    Generating public/private rsa key pair.
    Enter file in which to save the key (/Users/adam/.ssh/id_rsa):
    Enter passphrase (empty for no passphrase):
    Enter same passphrase again:
    Your identification has been saved in /Users/adam/.ssh/id_rsa.
    Your public key has been saved in /Users/adam/.ssh/id_rsa.pub.
    The key fingerprint is:
    a6:88:0a:0b:74:90:c6:e9:d5:49:d6:e3:04:d5:6c:3e adam@workstation

Next, add your key to Heroku, type:

    $ heroku keys:add

Having already installed the Heroku Toolbelt, you now have access to the
heroku command from within the command window. First of all, try logging
in using the same details as when you signed up for Heroku. Type:


    $ heroku login

Enter your Heroku credentials.

    Email: satish@rubylearning.org
    Password:
    Authentication successful.
    $

You'll be prompted for your username and password the first time you run
a heroku command; they'll be saved on `~/.heroku/credentials` so you
won't be prompted on future runs. It will also upload your public key to
allow you to push and pull code.


In order for Heroku to know what to do with your Rack app, create a
`config.ru` (ru stands for Rack up) in the rackheroku folder. The
contents are:

    require './my_app'
    run MyApp.new

Also, copy the `my_app.rb` file to the rackheroku folder. It’s
contents are:


    # my_app.rb
    class MyApp
      def call env
        [200, {"Content-Type" => "text/html"}, ["Hello Rack Participants"]]
      end
    end

Next we install bundler. Open a command window and type:

    $ gem install bundler

Close the command window. Next, we will install the required gems (if
any) via bundler. In the already open Git Bash shell for folder
rackheroku type:



    $ bundle init

Writing new Gemfile to c:/rackheroku/Gemfile

Edit the created Gemfile with your preferred text editor to let it look
like this:

    source "http://rubygems.org"
    gem 'rack'

Now we need to tell Bundler to check if we’re missing the gems our
application depends on, if so, tell it to install them. In your open
Bash shell type:

    $ bundle check

The Gemfile's dependencies are satisfied

Finally in the open Bash shell, type:

    $ **bundle install**

This will ensure all gems specified on Gemfile, together with their
dependencies, are available for your application. Running “bundle
install” will also generate a “Gemfile.lock” file. The Gemfile.lock
ensures that your deployed versions of gems on Heroku match the version
installed locally on your development machine.

Next we set up our local app to use Git. Type:

    $ **git init**
    $ **git add .**
    $ **git commit -m "Rack app first commit"**

Let’s create our Rack app on Heroku (we are calling the app –
rachonheroku). Type:

    $ **heroku create rackonheroku**
    Creating rackonheroku... done, stack is cedar

    http://rackonheroku.herokuapp.com/ | git@heroku.com:rackonheroku.git
    Git remote heroku added

The app has been created and two URLs are provided. One is for the web
face of your new app i.e.
[http://rackonheroku.herokuapp.com/](http://rackonheroku.herokuapp.com/)
If you visit that URL now, you’ll see a standard welcome page, until you
push your application up. The other one is for the Git repository that
you will push your code to. Normally you would need to add this as a git
remote; the “heroku create” command has done this for you automatically.
Do note that the output from the create command will be different for
each one of you.

Now let us deploy our code to Heroku. Type:

    $ **git push heroku master**

Run the deployed app in your browser by opening a new browser window and
typing:

[http://rackonheroku.herokuapp.com/](http://rackonheroku.herokuapp.com/)

In the browser window, you should see:

    Hello Rack Participants from across the globe

## Using Rack middleware

We mentioned earlier that between the server and the framework, Rack can
be customized to your applications needs using middleware. The
fundamental idea behind Rack middleware is – come between the calling
client and the server, process the HTTP request before sending it to the
server, and processing the HTTP response before returning it to the
client.

[Rackup](http://rack.rubyforge.org/doc/classes/Rack/Builder.html) also
has a use method that accepts a middleware. Let us use one of Rack’s
built-in middleware.

You must have observed that every time we make a change to our config.ru
or my_app.rb files, we need to restart the WEBrick server. To avoid
this, let’s use one of Rack’s built-in middleware – Rack::Reloader. Edit
`config.ru` to have:

    require './my\_app'
    use Rack::Reloader
    run MyApp.new

In the same folder, we have the `my_app.rb` file. Its contents are:

    # my_app.rb
    class MyApp
      def call env
        [200, {"Content-Type" =\> "text/html"}, ["Hello Rack Participants from across the globe"]]
      end
    end

To run our rack app, in the same folder that contains config.ru, type:

    $ rackup config.ru

Open a browser window and type the url: <http://localhost:9292/>.

In your browser window, you should see something like this:

    Hello Rack Participants from across the globe

Modify my_app.rb and instead of “Hello Rack Participants from across
the globe” type “Hello Rack Participants from across the world!

Refresh the browser window and you should see:

    Hello Rack Participants from across the world!

There was no need to re-start the WEBrick server.

You can now press `Ctrl-C` to stop the `WEBrick` server.

## Writing our own Middleware

For all practical purposes, a middleware is a rack application that
wraps up an inner application.

Our middleware is going to do something very simple. We will append some
text to the body being sent by our inner application. Let us write our
own middleware. We will create a middleware class called
MyRackMiddleware. Here’s the skeleton program:

    class MyRackMiddleware
      def initialize(appl)
        @appl = appl
      end
      def call(env)
      end
    end

In the code above, to get the original body, we initialize the class
MyRackMiddleware by passing in the inner application (appl).

Next we need to call this appl:

    def call(env)
      status, headers, body = @appl.call(env) # we now call the inner application
    end

In the above code, we now have access to the original body, which we can
now modify. Rack does not guarantee you that the body would be a string.
It could be an object too. However, we are guaranteed that if we call
`.each` on the body, everything it returns will be a string. Let us use
this in our call method:

    def call(env)
      status, headers, body = @appl.call(env)
      append\_s = "... greetings from RubyLearning!!"
      new_body = ""
      body.each { |string| new_body << " " << string }
      new_body << " " << append_s
      [status, headers, [new_body]]
    end

Here’s our completed middleware class:

    class MyRackMiddleware
      def initialize(appl)
        @appl = appl
      end
      def call(env)
        status, headers, body = @appl.call(env)
        append_s = "... greetings from RubyLearning!!"
        new_body = ""
        body.each { |string| new_body << " " << string }
        new_body << " " << append_s
        [status, headers, [new_body]]
      end
    end

Our my_app.rb file remains the same. Its contents are:


    # my_app.rb
    class MyApp
      def call(env)
        [200, {"Content-Type" =\> "text/html"}, ["Hello Rack Participants from across the globe"]]
      end
    end

Edit config.ru to have:

    require './my\_app'
    require './myrackmiddleware'
    use Rack::Reloader
    use MyRackMiddleware
    run MyApp.new

To run our rack app, in the same folder that contains config.ru, type:

    $ rackup config.ru

Open a browser window and type the url: `http://localhost:9292/`.

In your browser window, you should see something like this:

    Hello Rack Participants from across the globe... greetings from RubyLearning!!

## Rack and Sinatra

Let us see how to use Rack with a Sinatra app. Create a folder
racksinatra. Next, let us install Sinatra:

    gem install Sinatra

Here’s a trivial Sinatra program `my_sinatra.rb` in the folder
`racksinatra`:

    require 'sinatra'
    get '/' do
      'Welcome to all'
    End

Sinatra can use Rack middleware. Our trivial middleware class will
intercept the request from the user, calculate and display the response
time on the console and pass on the unaltered request to the Sinatra
app. In the folder racksinatra write the middleware class namely
rackmiddleware.rb.

    class RackMiddleware
      def initialize(appl)
        @appl = appl
      end
      def call(env)
        start = Time.now
        status, headers, body = @appl.call(env) \# call our Sinatra app
        stop = Time.now
        puts "Response Time: \#{stop-start}" \# display on console
        [status, headers, body]
      end
    end

In order for Heroku to know what to do with our Sinatra app, create a
config.ru in the folder racksinatra:

    require "./my_sinatra"
    run Sinatra::Application

Modify the Sinatra app to use our middleware:

    # my_sinatra.rb
    require 'sinatra'
    require './rackmiddleware'
    use RackMiddleware
    get '/' do
      'Welcome to all'
    end

Now open a Git Bash shell for folder racksinatra and type:

    $ bundle init

Edit the created Gemfile with your preferred text editor to let it look
like this:

    source "http://rubygems.org"
    gem 'sinatra'

In your open Bash shell type:


    $ bundle check

Finally in the open Bash shell, type:


    $ bundle install

Set up your local app to use Git. Type:

    $ git init
    $ git add .
    $ git commit -m "SinatraRack app"

Create the app on Heroku. In the open bash shell, type:

    $ heroku create racksinatra

Finally, let us push our app to Heroku:

    $ git push heroku master

The app is now running on Heroku. You can take a look at it, in your
browser type:

    http://racksinatra.herokuapp.com

To check whether the *** Response Time ***: has been displayed on
the Heroku console, type:

    $ heroku logs -s app -n 5

where `-s app` shows the output from your app and `-n 5` retrieves 5 log
lines.

For me it showed:

    [36m2011-10-26T05:40:06+00:00 app[web.1]: Response Time : 0.000297385

That’s it. I hope you liked this introductory article on Rack. Happy
Racking!!

### Other eBooks by the Author

The following eBooks from Satish Talim are available on Amazon.

[The Ultimate Guide to Ruby Programming [Kindle
Edition]](http://www.amazon.com/gp/product/B0062X2I68/ref=as_li_tf_tl?ie=UTF8&amp;camp=1789&amp;creative=9325&creativeASIN=B0062X2I68&linkCode=as2&tag=satishtalimsw-20)

[Programming the Web with Ruby [Kindle
Edition]](http://www.amazon.com/gp/product/B00B7VN8IC/ref=as_li_tf_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B00B7VN8IC&linkCode=as2&tag=satishtalimsw-20)

[How Do I Create And Publish My First Ruby
Gem?](http://www.amazon.com/gp/product/B00BECCKYM/ref=as_li_tf_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B00BECCKYM&linkCode=as2&tag=satishtalimsw-20)

