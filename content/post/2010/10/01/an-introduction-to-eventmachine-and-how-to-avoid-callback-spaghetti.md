---
draft: false
title: An introduction to eventmachine, and how to avoid callback spaghetti
date: 2010-10-01
author: Martyn Loughran
categories:
- Beginners
- Popular
- Ruby
- Ruby Masters
layout: post
permalink: /2010/10/01/an-introduction-to-eventmachine-and-how-to-avoid-callback-spaghetti/
tags:
- eventmachine
- Martyn Loughran
- programming
- Ruby
- Ruby Beginners
- Ruby eventmachine
- Ruby for Noobs
---
This guest post is contributed by **[Martyn
Loughran](http://mloughran.com/)**, who works at [New
Bamboo](http://new-bamboo.co.uk/) in London where he builds some very
cool apps like<!--more--> [Pusher](http://pusherapp.com/). Pusher is a web service
which finally makes web push easy using the brand new WebSocket
protocol. When he's not hacking away at the next great thing, he's most
likely to be found behind a cello; hacking in this context is less
desirable. Alternatively find him on twitter as
[@mloughran](http://twitter.com/mloughran) where he tweets, reluctantly.

![Martyn Loughran](http://rubylearning.com/images/martyn.jpg)

## An introduction to eventmachine, and how to avoid callback spaghetti

Evented programming has become cool lately, largely due to the very elegant
[node.js](http://nodejs.org/) project. However, we've been evented in the Ruby
world for many years thanks to eventmachine, which adds evented IO to Ruby.
Writing evented code is often viewed as 'hard' or 'back to front', but it can
actually be very elegant. You just need a few tricks up your sleeve.

One of the big challenges is understanding how to create clean
abstractions. Since the structure of the code is so different to what
you're probably used to, you can quickly find yourself tied up in
callback spaghetti. In this blog post I will explain some common
patterns you can use while we combine the Twitter streaming API,
Google's language API, and a WebSocket server. No spaghetti is required,
promise!

After getting started with eventmachine, we'll discuss two common
abstractions. Firstly deferrable objects which are like method calls
which return asynchrnously. Secondly, how to abstract code that can
trigger multiple events. Finally, we'll add a WebSocket server into the
same process to show off doing IO concurrently.

## Getting started with eventmachine {#getting_started_with_eventmachine}

Let's start by installing eventmachine and checking that the basics
work:

    gem install eventmachine

You can run this `ruby test1.rb` as you normally would, but you'll need
to kill it when you've had enough.

    # test1.rb

    require 'rubygems'
    require 'eventmachine'

    EventMachine.run {
      EventMachine.add_periodic_timer(1) {
        puts "Hello world"
      }
    }

With a bit of luck you should get a cheery message every second.

So how does this work? After requiring eventmachine, we call
`EventMachine.run`, passing a block. The best advice for now is to
completely ignore this and just focus on what's inside the block,
eventmachine can't work without it. (If you're curious, read up on the
[reactor pattern](http://en.wikipedia.org/wiki/Reactor_pattern).) Inside
the `EventMachine.run` block we call `add_periodic_timer`, passing
another block. This tells eventmachine to fire an event every 1s, at
which point it should call the block. This is the first of many
interesting blocks. It's known a callback.

You're probably thinking you could have done this much easier with
`loop { puts 'hi'; sleep 1 }`, and you'd be right! It's gets better, I
promise.

## Using eventmachine for network IO {#using_eventmachine_for_network_io}

Efficient IO is the whole point of eventmachine, but you need to
understand one thing. When you're doing any kind of network IO with
eventmachine, you *must* use eventmachine, or a library which uses
eventmachine under the hood (you can usually spot them on github because
they start with `em-`). You therefore need to be very careful when for
example picking gems which talk to databases, apis, etc.

If you don't do this you'll block the reactor, which basically means
that eventmachine will not be able to trigger any more events until the
IO operation completes. So for example, if you used `Net::HTTP` from the
standard library to request a URL which took 10s to return, the periodic
timer you added earlier wouldn't fire till it finished. You've thrown
concurrency out of the window!

So let's talk about the HTTP client. Although eventmachine actually
comes with two different HTTP clients, both have issues, and it's
generally recommended to ignore them and install the very capable
[em-http-request]() instead

    gem install em-http-request

Let's make a quick http request to check that it works (note that EM is
an alias for EventMachine, and by corollary I dislike typing):

    require 'rubygems'
    require 'eventmachine'

    EM.run {
      require 'em-http'

      EM::HttpRequest.new('http://json-time.appspot.com/time.json').get.callback { |http|
        puts http.response
      }
    }

Again we're attaching a callback which is called once the request has
completed. We're attaching it in a slightly different way to the timer
above, which we'll discuss next.

## Abstracting code that has a success or failure case {#abstracting_code_that_has_a_success_or_failure_case}

When designing APIs it's extremely common to need to differentiate
between successful and failure responses. In Ruby, two common ways to do
this are to return `nil`, or to raise an exception
(`ActiveRecord::NotFound` for example). Eventmachine provides quite an
elegant abstraction for this: the deferrable.

A deferrable is an object to which you may attach a success and a
failure callback, slightly confusingly named `callback` and `errback`
respectively. If you're so inclined you might like to look at the
[code](http://github.com/eventmachine/eventmachine/blob/master/lib/em/deferrable.rb),
since there is not much to it.

The call to `HttpRequest#get` we looked at earlier actually returns a
deferrable (in fact it returns an instance of `EM::HttpClient` which
mixes in the `EM::Deferrable` module). It is also quite common to make
use of the `EM::DefaultDeferrable` which you can use standalone.

As an excuse to use a deferrable ourselves I've decided that it would be
a jolly marvelous idea to look up the language of tweets as they arrive
from the twitter streaming API.

Handily, the [Google AJAX Language
API](http://code.google.com/apis/ajaxlanguage/documentation/) allows you
to get the language of any piece of text. It's designed to be used from
the browser, but we won't let a small matter like that stop us for now
(although you should if it's a real application).

When I'm trying out a new API I generally start with HTTParty
(`gem install httparty`) since it's just so quick and easy to use.
Warning: you can't use HTTParty with eventmachine since it uses
`Net::HTTP` under the covers -- this is just for testing!

    require 'rubygems'
    require 'httparty'
    require 'json'

    response = HTTParty.get("http://www.google.com/uds/GlangDetect", :query => {
      :v => '1.0',
      :q => "Sgwn i os yw google yn deall Cymraeg?"
    })

    p JSON.parse(response.body)["responseData"]

    # => {"isReliable"=>true, "confidence"=>0.5834181, "language"=>"cy"}

Cool, Google understands Welsh!

Before we convert this to use em-http-request (HTTParty uses Net::HTTP
under the covers), let's wrap it up in a class so we can compare it to
the eventmachine version we'll write in a minute. I decided to return
`nil` if the language could not be reliably determined.

    require 'rubygems'
    require 'httparty'
    require 'json'

    class LanguageDetector
      URL = "http://www.google.com/uds/GlangDetect"

      def initialize(text)
        @text = text
      end

      # Returns the language if it can be detected, otherwise nil
      def language
        response = HTTParty.get(URL, :query => {:v => '1.0', :q => @text})

        return nil unless response.code == 200

        info = JSON.parse(response.body)["responseData"]

        return info['isReliable'] ? info['language'] : nil
      end
    end

    puts LanguageDetector.new("Sgwn i os yw google yn deall Cymraeg?").language

We can now convert this code to use em-http-request:

    require 'rubygems'
    require 'em-http'
    require 'json'

    class LanguageDetector
      URL = "http://www.google.com/uds/GlangDetect"

      include EM::Deferrable

      def initialize(text)
        request = EM::HttpRequest.new(URL).get({
          :query => {:v => "1.0", :q => text}
        })

        # This is called if the request completes successfully (whatever the code)
        request.callback {
          if request.response_header.status == 200
            info = JSON.parse(request.response)["responseData"]
            if info['isReliable']
              self.succeed(info['language'])
            else
              self.fail("Language could not be reliably determined")
            end
          else
            self.fail("Call to fetch language failed")
          end
        }

        # This is called if the request totally failed
        request.errback {
          self.fail("Error making API call")
        }
      end
    end

    EM.run {
      detector = LanguageDetector.new("Sgwn i os yw google yn deall Cymraeg?")
      detector.callback { |lang| puts "The language was #{lang}" }
      detector.errback { |error| puts "Error: #{error}" }
    }

This returns:

    The language was cy

This looks pretty different. The important thing is that in all cases
we've either called `succeed` or `fail`, which we can do since we
included `EM::Deferrable`. Depending on which one we call, either the
`callback` or `errback` block will be executed.

As an exercise you could try to extend this class to retry the api call
up to 3 times on failure. You should be able to maintain exactly the
same external interface, which means that we've successfully wrapped up
this complexity in an object and can now forget how it works!

## Abstracting code that returns multiple events multiple times {#abstracting_code_that_returns_multiple_events_multiple_times}

Now we arrive at territory where eventmachine really shines.

We'll build a client that connects to Twitter's streaming api, and emits
events every time a tweet arrives.

To use Twitter's [streaming
API](http://dev.twitter.com/pages/streaming_api) you just need to open a
long lived HTTP connection to `stream.twitter.com`, and wait for the
deluge to arrive. Again we'll use em-http-request.

Connecting to the API, and listening to all tweets that mention
newtwitter is as easy as doing:

    http = EventMachine::HttpRequest.new('http://stream.twitter.com/1/statuses/filter.json').post({
      :head => { 'Authorization' => [username, password] },
      :query => { "track" => "newtwitter" }
    })

Although this returns a deferrable (which remember triggers its callback
when the request completes), it's actually got another trick up it's
sleeve. We can also register to be notified every time new data is
received:

    http.stream do |chunk|
      # This chunk may contain one or more tweets separated by \r\n
    end

Let's put this together and listen for some tweets:

    require 'rubygems'
    require 'em-http'
    require 'json'

    EM.run {
      username = 'yourtwitterusername'
      password = 'password'
      term = 'newtwitter'
      buffer = ""

      http = EventMachine::HttpRequest.new('http://stream.twitter.com/1/statuses/filter.json').post({
        :head => { 'Authorization' => [ username, password ] },
        :query => { "track" => term }
      })

      http.callback {
        unless http.response_header.status == 200
          puts "Call failed with response code #{http.response_header.status}"
        end
      }

      http.stream do |chunk|
        buffer += chunk
        while line = buffer.slice!(/.+\r\n/)
          tweet = JSON.parse(line)
          puts tweet['text']
        end
      end
    }

This should return something like:

    Hey @Twitter. When shall I be getting the #NewTwitter?
    #NewTwitter #Perfect
    WHAHOO WTF? #NewTwitter is weird!
    Buenos dÃ­as a todos! =) Estoy sola en la office, leyendo Le Monde y probando el #NewTwitter desde FireFox, que funciona de 10!
    Curiosity and boredom got the better of me...I'm trying the #newtwitter

It works! Now say we wanted to lookup the language of each tweet using
the class we built earlier. We could do this by adding further to our
stream method, however this is the road to callback hell (and just
imagine what it would be like if we hadn't abstracted the language
detection!).

    http.stream do |chunk|
      buffer += chunk
      while line = buffer.slice!(/.+\r\n/)
        tweet = JSON.parse(line)
        text = tweet['text']
        detector = LanguageDetector.new(text)
        detector.callback { |lang|
          puts "Language: #{lang}, tweet: #{text}"
        }
        detector.errback { |error|
          puts "Language could not be determined for tweet: #{text}"
        }
      end
    end

Let's rewrite what we just did nicely.

Earlier we used a deferrable to abstract code that either succeeded or
failed asynchronously. Another common technique in a lot of eventmachine
code is to provide an `onevent` callback system. For example, it would
be great if we could have an interface like this:

    stream = TweetStream.new(username, password, term)
    stream.ontweet { |tweet| puts tweet }

As if by magic here is the code!

    require 'rubygems'
    require 'em-http'
    require 'json'

    class TwitterStream
      URL = 'http://stream.twitter.com/1/statuses/filter.json'

      def initialize(username, password, term)
        @username, @password = username, password
        @term = term
        @callbacks = []
        @buffer = ""
        listen
      end

      def ontweet(█)
        @callbacks << block
      end

      private

      def listen
        http = EventMachine::HttpRequest.new(URL).post({
          :head => { 'Authorization' => [ @username, @password ] },
          :query => { "track" => @term }
        })

        http.stream do |chunk|
          @buffer += chunk
          process_buffer
        end
      end

      def process_buffer
        while line = @buffer.slice!(/.+\r\n/)
          tweet = JSON.parse(line)

          @callbacks.each { |c| c.call(tweet['text']) }
        end
      end
    end

So now we can write a nice bit of code like this.

    EM.run {
      stream = TwitterStream.new('yourtwitterusername', 'pass', 'newtwitter')
      stream.ontweet { |tweet|
        LanguageDetector.new(tweet).callback { |lang|
          puts "New tweet in #{lang}: #{tweet}"
        }
      }
    }

## Mixing different kinds of IO in the same process {#mixing_different_kinds_of_io_in_the_same_process}

One of the great things about using eventmachine is that because none of
the IO operations block, it's possible and really easy to mix and match
different types of IO in the same process.

So for example we could use WebSockets to push tweets to a browser in
realtime and get something like this:

Fortunately there's already a WebSocket server built using eventmachine,
[em-websocket](http://github.com/igrigorik/em-websocket) (which I'm
pretty familiar with since we use it in [Pusher](http://pusherapp.com)).
Install it with `gem install em-websocket`.

Once we've started a websocket server (which is trivial), it's as easy
as:

    stream.ontweet { |tweet|
      LanguageDetector.new(tweet).callback { |lang|
        puts "New tweet in #{lang}: #{tweet}"

        websocket_connections.each do |socket|
          socket.send(JSON.generate({
            :lang => lang,
            :tweet => tweet
          }))
        end
      }
    }

See, no spaghetti!

All the code is contained in [this gist](http://gist.github.com/604404),
including the extremely basic HTML page which connects to the WebSocket.
Please fork it and add the funky canvas visualisation I ran out of time
to write!

## Going further {#going_further}

If you'd like to learn more I recommend:

-   The [wiki](http://github.com/eventmachine/eventmachine/wiki).
-   Aman Gupta's
    [slides](http://timetobleed.com/eventmachine-scalable-non-blocking-io-in-ruby/)
    (he knows what he's talking about since he maintains eventmachine).
-   Joining the [google
    group](http://groups.google.com/group/eventmachine).
-   Reading the [code](http://github.com/eventmachine/eventmachine).
-   Asking on the irc channel (\#eventmachine).
-   Try node.js as well, it's pretty cool and the same concepts apply.

Have fun!

*I hope you found this article valuable and that it gives you an insight
into the eventmachine. Feel free to ask questions and give feedback in
the comments section of this post. Thanks!*

***Do read* these awesome Guest Posts:**

-   [The Testing
    Mindset](http://rubylearning.com/blog/2010/09/30/the-testing-mindset/)
-   [An Introduction to Desktop Apps with
    Ruby](http://rubylearning.com/blog/2010/09/29/an-introduction-to-desktop-apps-with-ruby/)
-   [The Ruby
    movement](http://rubylearning.com/blog/2010/09/28/the-ruby-movement/)
-   [Almost everything is an object (and everything is almost an
    object!)](http://rubylearning.com/blog/2010/09/27/almost-everything-is-an-object-and-everything-is-almost-an-object/)
-   [So... you're new to
    Ruby!](http://rubylearning.com/blog/2010/09/24/so-youre-new-to-ruby/)
-   [Incorporating Web APIs to spark computer programming
    exercises](http://rubylearning.com/blog/2010/09/23/incorporating-web-apis-to-spark-computer-programming-exercises/)
-   [14 Ways To Have Fun Coding
    Ruby](http://rubylearning.com/blog/2010/09/22/14-ways-to-have-fun-coding-ruby/)
-   [Writing modular web applications with
    Rack](http://rubylearning.com/blog/2010/09/21/writing-modular-web-applications-with-rack/)
-   [How to Learn Ruby (or any programming
    language)](http://rubylearning.com/blog/2010/09/20/how-to-learn-ruby-or-any-programming-language/)

