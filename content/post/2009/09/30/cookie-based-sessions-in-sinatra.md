---
draft: false
title: Cookie-based Sessions in Sinatra
date: 2009-09-30
author: Julio Javier Cicchelli
authorlink: http://twitter.com/monsieur_rock
categories:
- Code Snippets
- Learn Sinatra
- Ruby
- Sinatra
layout: post
permalink: /2009/09/30/cookie-based-sessions-in-sinatra/
tags:
- Cookies
- Julio Javier Cicchelli
- Ruby
- Sinatra
---
![Julio Javier
Cicchelli](http://www.rubylearning.com/images/jjcicchelli.jpg "Julio Javier Cicchelli")
This is a guest post from **[Julio Javier
Cicchelli](http://rubylearning.com/blog/2009/07/20/julio-javier-cicchelli-how-do-i-learn-and-master-sinatra/)**.<!--more-->

## Cookie-based Sessions in Sinatra

Hi there everybody! My name is [Javier
Cicchelli](http://twitter.com/monsieur_rock) and I am the Software
Engineer of the technological pride and joy of the Red Light District in
Amsterdam, the Netherlands: [Rock & Code](http://rock-n-code.com). I
have been vested with the distinct authority to shed some light on the
concept of *Cookie*. The purpose of this article is to teach you how to
concoct the explosive digital mixture that would enable you to use
cookies for sessions within your [Sinatra](http://www.sinatrarb.com/)
applications. Piece of cake, right? Before I move to the nitty-gritty of
cookies in Sinatra, I want to cover the mandatory theoretical basics.
So, I invite you to sit back and enjoy this slow and easy software ride.
By the end of that piece, you will be asking for cookies at the nearest
bakery!

## What are Cookies?

According to the Computer Science definition, a *cookie*, which is also
known as an *HTTP cookie*, a *tracking cookie*, or a *browser cookie*,
is a piece of text, no bigger than 4 kilobytes, which is stored on the
user's computer by a web server via a web browser. It is a key-value
pair structure, which is designed to retain specific information such as
user preferences, user authentication, shopping carts, demographics,
sessions, or any other data used by a website. This mechanism, which was
developed by [Netscape](http://netscape.aol.com/) in the distant 1994,
provides a way to receive information from a web server and to send it
back from the web browser absolutely unchanged. This system complements
the stateless nature of the HTTP protocol as it provides enough memory
to store pieces of information during HTTP transactions.

When you try to access a web site, your web browser connects to a web
server and it sends a request for the respective page. Then the web
server replies by sending the requested content and it simultaneously
stores a new cookie on your computer. Every time the web browser
requests web pages from the web server, it always sends the respective
cookies back to the web server. The process takes place as described, if
the web browser supports cookies and the user allows their usage. Only
the web server can modify one or more of the cookie values. Then it
sends them to the web browser upon replying to a specific request.

According to the [RFC2965
specification](http://rfc.dotsrc.org/rfc/rfc2965.html), cookies are case
insensitive. A set of defined properties is inherent to the cookie
structure. Those properties include an expiration date, a path and a
domain. The first attribute requires a date defined in *Wdy, DD-Mon-YYYY
HH:MM:SS GMT* format. The rest of the cookie characteristics require a
path and/or a domain defined as a string. Let's take a look at this
example:

    Cookie: key0=value0; ...; keyX=valueX; expires=Wed, 23-Sep-2009 23:59:59 GMT; path=/; domain=.yoursite.com

When the expiration date is defined, your cookie will be "persistent" as
it will reoccur in different sessions until the set expiration date has
been reached. If the expiration date has not been defined in the cookie,
it will occur until the end of your current session or when you close
your web browser. If the path and/or the domain attributes have been
defined in your cookie, then the web server limits the scope of the
cookie to that specific domain, sub-domain or path.

## Cookies and Sinatra

Having clarified the basics, we can proceed to the next level. Prepare
to learn how to implement cookie-based sessions in the Sinatra web
framework. You do not have to install any extra Ruby gem.

Get ready to rumble! First and foremost, you have to decide on the
session strategy your Sinatra application will use in order to send to
the web browser only those relevant pieces of information that your
application requires. As I have already explained, this information
depends on the kind of application you want to develop and on the
functionalities you want to offer to your users. Then you have to enable
the cookie based session function in Sinatra. Finally, after enabling
the cookie-based support, you have to implement the designed session
strategy in your application. Regardless of how you want to develop your
application, you must always test your code in order to verify that it
works as expected and validate that it satisfies all the given
requirements. Throughout the remainder of this article, I will look at
the existing methods that provides Sinatra for using sessions based on
cookies.

## A Simple Example

Let's take it slow and easy. I will commence with a very simple example.
I will write a cookie version of the famous "Hello World" example. Here
I will use the cookie functions included in the Sinatra framework in
order to demonstrate how to use them. In the following example, I will
explain how to enable the session support in your Sinatra application
and I will show you how to create a key-value pair inside the session.
So, let's rock & code!

    require 'rubygems'
    require 'sinatra'

    enable :sessions

    get '/' do
      session["value"] ||= "Hello world!"
      "The cookie you've created contains the value: #{session["value"]}"
    end

## A Slightly Bigger Example

Now that you have a basic idea of how cookies work in Sinatra, you are
ready to move to the next level. I will write a more complex example,
which will consist of a tiny web application, which will ask the user to
identify. In this example, I will use the session support provided by
Sinatra in order to implement non-persistent cookies. Note that I am
using the technique I resorted to in the previous example. I simply
tuned it to the logic of this application.

    require 'rubygems'
    require 'sinatra'
    require 'haml'

    enable :sessions

    get '/' do
      session["user"] ||= nil
      haml :index
    end

    get '/introduction' do
      haml :introduction
    end

    post '/introduction' do
      session["user"] = params[:name]
      redirect '/'
    end

    get '/bye' do
      session["user"] = nil
      haml :bye
    end

## A Final Example

The last example will demonstrate how to directly manage cookies through
the *request* and *response* singletons provided by Sinatra. You will
see in the following example that the previously described process
involving the use cookies is clearly implemented. This technique is
recommended when your application requires to use persistent and/or
scoped cookies. In this example, the application uses two persistent
cookies, which expire at the same time, in order to store and manage
different configuration data. Unfortunately, due to a bug on the cookie
management that I still have to investigate, I cannot test how the
application responds to the scope of the different cookies it has
created.

    require 'rubygems'
    require 'sinatra'
    require 'haml'

    get '/' do
      @@expiration_date = Time.now + (60 * 2) \
      unless request.cookies.key?('some_options') && request.cookies.key?('other_options')
      haml :index
    end

    get '/some_options' do
      @some_cookie = request.cookies["some_options"]
      haml :some_options
    end

    post '/some_options' do  
      response.set_cookie('some_options', :value => cookie_values(params), :expires => @@expiration_date)
      redirect '/'
    end

    get '/other_options' do
      @other_cookie = request.cookies["other_options"]
      haml :other_options
    end

    post '/other_options' do
      response.set_cookie('other_options', :value => cookie_values(params),:expires => @@expiration_date)
      redirect '/'
    end

    helpers do
      def cookie_values(parameters)
        values = {}
        parameters.each do |key, value|
          case key
          when 'options'
            values[value] = true
          else
            values[key] = true
          end
        end
        values
      end
    end

I would like to stress that Sinatra does allow developers to use
directly [Rack](http://rack.rubyforge.org/) to manage cookie through the
*Rack::Session::Cookie* middleware. Yet, I desisted from discussing this
method because of its complexity. Furthermore, I have not elaborated on
the existence of other alternatives to this storage mechanism. After
all, I have to leave some room for upcoming articles I can present you
with. Do not allow my deliberate slips to limit your curiosity! Be
inquisitive! You can see the source code on
[Github](http://gist.github.com/205962), of all the relevant examples.
So go ahead and rock & code!
