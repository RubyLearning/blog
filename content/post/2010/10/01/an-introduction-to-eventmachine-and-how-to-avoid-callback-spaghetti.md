---
title: An introduction to eventmachine, and how to avoid callback spaghetti
author: Martyn Loughran
date: 2010-10-01
layout: post
permalink: /2010/10/01/an-introduction-to-eventmachine-and-how-to-avoid-callback-spaghetti/
thesis_description:
  - Martyn Loughran gives an introduction to eventmachine, and how to avoid callback spaghetti in this guest post on RubyLearning.
thesis_keywords:
  - Ruby eventmachine,Ruby, Programming, Martyn Loughran, Ruby for Noobs, Ruby beginners, eventmachine
topsy_short_url:
  - http://bit.ly/alZZI4
categories:
  - Beginners
  - Popular
  - Ruby
  - Ruby Masters
tags:
  - eventmachine
  - Martyn Loughran
  - programming
  - Ruby
  - Ruby Beginners
  - Ruby eventmachine
  - Ruby for Noobs
---
<div>
  <h3 id="an_introduction_to_eventmachine_and_how_to_avoid_callback_spaghetti">
    An introduction to eventmachine, and how to avoid callback spaghetti
  </h3>
  
  <p class="update">
    This guest post is contributed by <strong><a href="http://mloughran.com/">Martyn Loughran</a></strong>, who works at <a href="http://new-bamboo.co.uk/">New Bamboo</a> in London where he builds some very cool apps like <a href="http://pusherapp.com/">Pusher</a>. Pusher is a web service which finally makes web push easy using the brand new WebSocket protocol. When he&#8217;s not hacking away at the next great thing, he&#8217;s most likely to be found behind a cello; hacking in this context is less desirable. Alternatively find him on twitter as <a href="http://twitter.com/mloughran">@mloughran</a> where he tweets, reluctantly.
  </p>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/martyn.jpg" alt="Martyn Loughran" width="125" height="125" /> <span class="drop_cap">E</span>vented programming has become cool lately, largely due to the very elegant <a href="http://nodejs.org/">node.js</a> project. However, we&#8217;ve been evented in the Ruby world for many years thanks to eventmachine, which adds evented IO to Ruby. Writing evented code is often viewed as &#8216;hard&#8217; or &#8216;back to front&#8217;, but it can actually be very elegant. You just need a few tricks up your sleeve.
  </p>
  
  <p>
    One of the big challenges is understanding how to create clean abstractions. Since the structure of the code is so different to what you&#8217;re probably used to, you can quickly find yourself tied up in callback spaghetti. In this blog post I will explain some common patterns you can use while we combine the Twitter streaming API, Google&#8217;s language API, and a WebSocket server. No spaghetti is required, promise!
  </p>
  
  <p>
    After getting started with eventmachine, we&#8217;ll discuss two common abstractions. Firstly deferrable objects which are like method calls which return asynchrnously. Secondly, how to abstract code that can trigger multiple events. Finally, we&#8217;ll add a WebSocket server into the same process to show off doing IO concurrently.
  </p>
  
  <h3 id="getting_started_with_eventmachine">
    Getting started with eventmachine
  </h3>
  
  <p>
    Let&#8217;s start by installing eventmachine and checking that the basics work:
  </p>
  
  <pre>gem install eventmachine
</pre>
  
  <p>
    You can run this <code>ruby test1.rb</code> as you normally would, but you&#8217;ll need to kill it when you&#8217;ve had enough.
  </p>
  
  <pre># test1.rb

require 'rubygems'
require 'eventmachine'

EventMachine.run {
  EventMachine.add_periodic_timer(1) {
    puts "Hello world"
  }
}
</pre>
  
  <p>
    With a bit of luck you should get a cheery message every second.
  </p>
  
  <p>
    So how does this work? After requiring eventmachine, we call <code>EventMachine.run</code>, passing a block. The best advice for now is to completely ignore this and just focus on what&#8217;s inside the block, eventmachine can&#8217;t work without it. (If you&#8217;re curious, read up on the <a href="http://en.wikipedia.org/wiki/Reactor_pattern">reactor pattern</a>.) Inside the <code>EventMachine.run</code> block we call <code>add_periodic_timer</code>, passing another block. This tells eventmachine to fire an event every 1s, at which point it should call the block. This is the first of many interesting blocks. It&#8217;s known a callback.
  </p>
  
  <p>
    You&#8217;re probably thinking you could have done this much easier with <code>loop { puts 'hi'; sleep 1 }</code>, and you&#8217;d be right! It&#8217;s gets better, I promise.
  </p>
  
  <h3 id="using_eventmachine_for_network_io">
    Using eventmachine for network IO
  </h3>
  
  <p>
    Efficient IO is the whole point of eventmachine, but you need to understand one thing. When you&#8217;re doing any kind of network IO with eventmachine, you <em>must</em> use eventmachine, or a library which uses eventmachine under the hood (you can usually spot them on github because they start with <code>em-</code>). You therefore need to be very careful when for example picking gems which talk to databases, apis, etc.
  </p>
  
  <p>
    If you don&#8217;t do this you&#8217;ll block the reactor, which basically means that eventmachine will not be able to trigger any more events until the IO operation completes. So for example, if you used <code>Net::HTTP</code> from the standard library to request a URL which took 10s to return, the periodic timer you added earlier wouldn&#8217;t fire till it finished. You&#8217;ve thrown concurrency out of the window!
  </p>
  
  <p>
    So let&#8217;s talk about the HTTP client. Although eventmachine actually comes with two different HTTP clients, both have issues, and it&#8217;s generally recommended to ignore them and install the very capable <a href="">em-http-request</a> instead
  </p>
  
  <pre>gem install em-http-request
</pre>
  
  <p>
    Let&#8217;s make a quick http request to check that it works (note that EM is an alias for EventMachine, and by corollary I dislike typing):
  </p>
  
  <pre>require 'rubygems'
require 'eventmachine'

EM.run {
  require 'em-http'

  EM::HttpRequest.new('http://json-time.appspot.com/time.json').get.callback { |http|
    puts http.response
  }
}
</pre>
  
  <p>
    Again we&#8217;re attaching a callback which is called once the request has completed. We&#8217;re attaching it in a slightly different way to the timer above, which we&#8217;ll discuss next.
  </p>
  
  <h3 id="abstracting_code_that_has_a_success_or_failure_case">
    Abstracting code that has a success or failure case
  </h3>
  
  <p>
    When designing APIs it&#8217;s extremely common to need to differentiate between successful and failure responses. In Ruby, two common ways to do this are to return <code>nil</code>, or to raise an exception (<code>ActiveRecord::NotFound</code> for example). Eventmachine provides quite an elegant abstraction for this: the deferrable.
  </p>
  
  <p>
    A deferrable is an object to which you may attach a success and a failure callback, slightly confusingly named <code>callback</code> and <code>errback</code> respectively. If you&#8217;re so inclined you might like to look at the <a href="http://github.com/eventmachine/eventmachine/blob/master/lib/em/deferrable.rb">code</a>, since there is not much to it.
  </p>
  
  <p>
    The call to <code>HttpRequest#get</code> we looked at earlier actually returns a deferrable (in fact it returns an instance of <code>EM::HttpClient</code> which mixes in the <code>EM::Deferrable</code> module). It is also quite common to make use of the <code>EM::DefaultDeferrable</code> which you can use standalone.
  </p>
  
  <p>
    As an excuse to use a deferrable ourselves I&#8217;ve decided that it would be a jolly marvelous idea to look up the language of tweets as they arrive from the twitter streaming API.
  </p>
  
  <p>
    Handily, the <a href="http://code.google.com/apis/ajaxlanguage/documentation/">Google AJAX Language API</a> allows you to get the language of any piece of text. It&#8217;s designed to be used from the browser, but we won&#8217;t let a small matter like that stop us for now (although you should if it&#8217;s a real application).
  </p>
  
  <p>
    When I&#8217;m trying out a new API I generally start with HTTParty (<code>gem install httparty</code>) since it&#8217;s just so quick and easy to use. Warning: you can&#8217;t use HTTParty with eventmachine since it uses <code>Net::HTTP</code> under the covers &#8211; this is just for testing!
  </p>
  
  <pre>require 'rubygems'
require 'httparty'
require 'json'

response = HTTParty.get("http://www.google.com/uds/GlangDetect", :query =&gt; {
  :v =&gt; '1.0',
  :q =&gt; "Sgwn i os yw google yn deall Cymraeg?"
})

p JSON.parse(response.body)["responseData"]

# =&gt; {"isReliable"=&gt;true, "confidence"=&gt;0.5834181, "language"=&gt;"cy"}
</pre>
  
  <p>
    Cool, Google understands Welsh!
  </p>
  
  <p>
    Before we convert this to use em-http-request (HTTParty uses Net::HTTP under the covers), let&#8217;s wrap it up in a class so we can compare it to the eventmachine version we&#8217;ll write in a minute. I decided to return <code>nil</code> if the language could not be reliably determined.
  </p>
  
  <pre>require 'rubygems'
require 'httparty'
require 'json'

class LanguageDetector
  URL = "http://www.google.com/uds/GlangDetect"

  def initialize(<span class="hiddenGrammarError" pre="">text)
    @text</span> = text
  end

  # Returns the language if it can be detected, otherwise nil
  def language
    response = HTTParty.get(URL, :query =&gt; {:v =&gt; '1.0', :q =&gt; @text})

    return nil unless response.code == 200

    info = JSON.parse(response.body)["responseData"]

    return info['isReliable'] ? info['language'] : nil
  end
end

puts LanguageDetector.new("Sgwn i os yw google yn deall Cymraeg?").language
</pre>
  
  <p>
    We can now convert this code to use em-http-request:
  </p>
  
  <pre>require 'rubygems'
require 'em-http'
require 'json'

class LanguageDetector
  URL = "http://www.google.com/uds/GlangDetect"

  include EM::Deferrable

  def initialize(text)
    request = EM::HttpRequest.new(URL).get({
      :query =&gt; {:v =&gt; "1.0", :q =&gt; text}
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
</pre>
  
  <p>
    This returns:
  </p>
  
  <pre>The language was cy
</pre>
  
  <p>
    This looks pretty different. The important thing is that in all cases we&#8217;ve either called <code>succeed</code> or <code>fail</code>, which we can do since we included <code>EM::Deferrable</code>. Depending on which one we call, either the <code>callback</code> or <code>errback</code> block will be executed.
  </p>
  
  <p>
    As an exercise you could try to extend this class to retry the api call up to 3 times on failure. You should be able to maintain exactly the same external interface, which means that we&#8217;ve successfully wrapped up this complexity in an object and can now forget how it works!
  </p>
  
  <h3 id="abstracting_code_that_returns_multiple_events_multiple_times">
    Abstracting code that returns multiple events multiple times
  </h3>
  
  <p>
    Now we arrive at territory where eventmachine really shines.
  </p>
  
  <p>
    We&#8217;ll build a client that connects to Twitter&#8217;s streaming api, and emits events every time a tweet arrives.
  </p>
  
  <p>
    To use Twitter&#8217;s <a href="http://dev.twitter.com/pages/streaming_api">streaming API</a> you just need to open a long lived HTTP connection to <code>stream.twitter.com</code>, and wait for the deluge to arrive. Again we&#8217;ll use em-http-request.
  </p>
  
  <p>
    Connecting to the API, and listening to all tweets that mention newtwitter is as easy as doing:
  </p>
  
  <pre>http = EventMachine::HttpRequest.new('http://stream.twitter.com/1/statuses/filter.json').post({
  :head =&gt; { 'Authorization' =&gt; [username, password] },
  :query =&gt; { "track" =&gt; "newtwitter" }
})
</pre>
  
  <p>
    Although this returns a deferrable (which remember triggers its callback when the request completes), it&#8217;s actually got another trick up it&#8217;s sleeve. We can also register to be notified every time new data is received:
  </p>
  
  <pre>http.stream do |chunk|
  # This chunk may contain one or more tweets separated by \r\n
end
</pre>
  
  <p>
    Let&#8217;s put this together and listen for some tweets:
  </p>
  
  <pre>require 'rubygems'
require 'em-http'
require 'json'

EM.run {
  username = 'yourtwitterusername'
  password = 'password'
  term = 'newtwitter'
  buffer = ""

  http = EventMachine::HttpRequest.new('http://stream.twitter.com/1/statuses/filter.json').post({
    :head =&gt; { 'Authorization' =&gt; [ username, password ] },
    :query =&gt; { "track" =&gt; term }
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
</pre>
  
  <p>
    This should return something like:
  </p>
  
  <pre>Hey @Twitter. When shall I be getting the #NewTwitter?
#NewTwitter #Perfect
WHAHOO WTF? #NewTwitter is weird!
Buenos dÃ­as a todos! =) Estoy sola en la office, leyendo Le Monde y probando el #NewTwitter desde FireFox, que funciona de 10!
Curiosity and boredom got the better of me...I'm trying the #newtwitter
</pre>
  
  <p>
    It works! Now say we wanted to lookup the language of each tweet using the class we built earlier. We could do this by adding further to our stream method, however this is the road to callback hell (and just imagine what it would be like if we hadn&#8217;t abstracted the language detection!).
  </p>
  
  <pre>http.stream do |chunk|
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
</pre>
  
  <p>
    Let&#8217;s rewrite what we just did nicely.
  </p>
  
  <p>
    Earlier we used a deferrable to abstract code that either succeeded or failed asynchronously. Another common technique in a lot of eventmachine code is to provide an <code>onevent</code> callback system. For example, it would be great if we could have an interface like this:
  </p>
  
  <pre>stream = TweetStream.new(username, password, term)
stream.ontweet { |tweet| puts tweet }
</pre>
  
  <p>
    As if by magic here is the code!
  </p>
  
  <pre>require 'rubygems'
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

  def ontweet(&block)
    @callbacks &lt;&lt; block
  end

  private

  def listen
    http = EventMachine::HttpRequest.new(URL).post({
      :head =&gt; { 'Authorization' =&gt; [ @username, @password ] },
      :query =&gt; { "track" =&gt; @term }
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
</pre>
  
  <p>
    So now we can write a nice bit of code like this.
  </p>
  
  <pre>EM.run {
  stream = TwitterStream.new('yourtwitterusername', 'pass', 'newtwitter')
  stream.ontweet { |tweet|
    LanguageDetector.new(tweet).callback { |lang|
      puts "New tweet in #{lang}: #{tweet}"
    }
  }
}
</pre>
  
  <h3 id="mixing_different_kinds_of_io_in_the_same_process">
    Mixing different kinds of IO in the same process
  </h3>
  
  <p>
    One of the great things about using eventmachine is that because none of the IO operations block, it&#8217;s possible and really easy to mix and match different types of IO in the same process.
  </p>
  
  <p>
    So for example we could use WebSockets to push tweets to a browser in realtime and get something like this:
  </p>
  
  <p>
  </p>
  
  <p>
    Fortunately there&#8217;s already a WebSocket server built using eventmachine, <a href="http://github.com/igrigorik/em-websocket">em-websocket</a> (which I&#8217;m pretty familiar with since we use it in <a href="http://pusherapp.com">Pusher</a>). Install it with <code>gem install em-websocket</code>.
  </p>
  
  <p>
    Once we&#8217;ve started a websocket server (which is trivial), it&#8217;s as easy as:
  </p>
  
  <pre>stream.ontweet { |tweet|
  LanguageDetector.new(tweet).callback { |lang|
    puts "New tweet in #{lang}: #{tweet}"

    websocket_connections.each do |socket|
      socket.send(JSON.generate({
        :lang =&gt; lang,
        :tweet =&gt; tweet
      }))
    end
  }
}
</pre>
  
  <p>
    See, no spaghetti!
  </p>
  
  <p>
    All the code is contained in <a href="http://gist.github.com/604404">this gist</a>, including the extremely basic HTML page which connects to the WebSocket. Please fork it and add the funky canvas visualisation I ran out of time to write!
  </p>
  
  <h3 id="going_further">
    Going further
  </h3>
  
  <p>
    If you&#8217;d like to learn more I recommend:
  </p>
  
  <ul>
    <li>
      The <a href="http://github.com/eventmachine/eventmachine/wiki">wiki</a>.
    </li>
    <li>
      Aman Gupta&#8217;s <a href="http://timetobleed.com/eventmachine-scalable-non-blocking-io-in-ruby/">slides</a> (he knows what he&#8217;s talking about since he maintains eventmachine).
    </li>
    <li>
      Joining the <a href="http://groups.google.com/group/eventmachine">google group</a>.
    </li>
    <li>
      Reading the <a href="http://github.com/eventmachine/eventmachine">code</a>.
    </li>
    <li>
      Asking on the irc channel (#eventmachine).
    </li>
    <li>
      Try node.js as well, it&#8217;s pretty cool and the same concepts apply.
    </li>
  </ul>
  
  <p>
    Have fun!
  </p>
  
  <p>
    <em>I hope you found this article valuable and that it gives you an insight into the eventmachine. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
  
  <p>
    <b><em>Do read</em> these awesome Guest Posts:</b>
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/30/the-testing-mindset/">The Testing Mindset</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/29/an-introduction-to-desktop-apps-with-ruby/">An Introduction to Desktop Apps with Ruby</a>
    </li>
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

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Programming" rel="tag"> Programming</a>, <a href="http://technorati.com/tag/Martyn+Loughran" rel="tag"> Martyn Loughran</a>, <a href="http://technorati.com/tag/Ruby+for+Noobs" rel="tag"> Ruby for Noobs</a>, <a href="http://technorati.com/tag/Ruby+beginners" rel="tag"> Ruby beginners</a>, <a href="http://technorati.com/tag/eventmachine" rel="tag"> eventmachine</a>
