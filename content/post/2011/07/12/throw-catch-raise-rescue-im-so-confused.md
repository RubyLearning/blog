---
title: 'Throw, Catch, Raise, Rescue&#8230; I&#8217;m so confused!'
author: Avdi Grimm
date: 2011-07-12
layout: post
permalink: /2011/07/12/throw-catch-raise-rescue-im-so-confused/
thesis_description:
  - Avdi Grimm explains the usage of Throw, Catch, Raise, Rescue in the Ruby programming language.
thesis_keywords:
  - Programming,Ruby programming, Avdi Grimm
topsy_short_url:
  - 
categories:
  - Beginners
  - Ruby
  - Ruby Masters
tags:
  - Avdi Grimm
  - programming
  - ruby programming
---
<div>
  <h3>
    Throw, Catch, Raise, Rescue&#8230; I&#8217;m so confused!
  </h3>
  
  <p class="update">
    This guest post is by <strong>Avdi Grimm</strong>, who is the author of &#8220;<strong><a href="http://exceptionalruby.com/">Exceptional Ruby</a></strong>&#8220;, an in-depth guide to exceptions and failure handling in Ruby. <em>RubyLearning readers can get a $3 discount on the book by using code <strong>RUBYLEARN</strong></em>. Avdi has been hacking Ruby code for 10 years, and is still loving it. He is chief aeronaut at <a href="http://shiprise.net/">ShipRise</a>, a consultancy specializing in sustainable software development and in helping geographically dispersed teams work more effectively. He lives in southern Pennsylvania with his wife and four children, and in his copious spare time blogs and podcasts at <a href="http://avdi.org/devblog/">Virtuous Code</a> and <a href="http://wideteams.com/">WideTeams.com</a>.
  </p>
  
  <h3>
    Old keywords, new meanings
  </h3>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/avdig.jpg" alt="Avdi Grimm" /> <span class="drop_cap">O</span>ne of the aspects of Ruby that often confuses newbies coming from other languages is the fact that it has both <code>throw</code> and <code>catch</code> and <code>raise</code> and <code>rescue</code> statements. In this article I&#8217;ll try and clear up that confusion.
  </p>
  
  <p>
    If you’re familiar with Java, C#, PHP, or C++, you are probably used to using <code>try</code>, <code>catch</code>, and <code>throw</code> for exception handling. You use <code>try</code> to delineate the block in which you expect an exception may occur. You use <code>catch</code> to specify what to do when an exception is raised. And you use <code>throw</code> to raise an exception yourself.
  </p>
  
  <p>
    You&#8217;ve probably noticed that Ruby has <code>throw</code> and <code>catch</code>&#8230; but they don&#8217;t seem to be used the way you&#8217;re used to in other languages! And there are also these &#8220;<code>begin</code>&#8220;, &#8220;<code>raise</code>&#8221; and &#8220;<code>rescue</code>&#8221; statements that seem to do the same thing. What&#8217;s going on here?
  </p>
  
  <h3>
    Getting out fast
  </h3>
  
  <p>
    If you’ve done much programming in another language like Java, you may have noticed that exceptions are sometimes used for non-error situations. &#8220;exceptions for control flow&#8221; is a technique developers sometimes turn to when they want an &#8220;early escape&#8221; from a particular path of execution.
  </p>
  
  <p>
    For instance, imagine some code that scrapes a series of web pages, looking for one that contains a particular text string.
  </p>
  
  <pre>def show_rank_for(target, query)
  rank = nil
  each_google_result_page(query, 6) do |page, page_index|
    each_google_result(page) do |result, result_index|
      if result.text.include?(target)
        rank = (page_index * 10) + result_index
      end
    end
  end
  puts "#{target} is ranked #{rank} for search '#{query}'"
end

show_rank_for("avdi.org", "nonesuch")</pre>
  
  <p>
    (For brevity, I&#8217;ve excluded the definitions of the <code>#each_google_result_page</code> and <code>#each_google_result</code> methods. You can view the full source at <a href="https://gist.github.com/1075364">https://gist.github.com/1075364</a>.)
  </p>
  
  <p>
    Fetching pages and parsing them is time-consuming. What if the target text is found on page 2? This code will keep right on going until it hits the max number of result pages (here specified as 6).
  </p>
  
  <p>
    It would be nice if we could end the search as soon as we find a matching result. We might think to use the <code>break</code> keyword, which &#8220;breaks out&#8221; of a loop&#8217;s execution. But <code>break</code> only breaks out of the immediately surrounding loop, and here we have a loop inside another loop.
  </p>
  
  <p>
    This is a situation where we might come up with the idea of using an exception to break out of the two levels of looping. But exceptions are supposed to be for unexpected failures, and finding the results we were looking for is neither unexpected, nor a failure! What to do?
  </p>
  
  <h3>
    Throwing Ruby a fast ball
  </h3>
  
  <p>
    Ruby has given us a tool for just this situation. Unlike in other languages, Ruby&#8217;s <code>throw</code> and <code>catch</code> are not used for exceptions. Instead, they provide a way to terminate execution early when no further work is needed. Their behavior is very similar to that of exceptions, but they are intended for very different situations.
  </p>
  
  <p>
    Let&#8217;s look at how we can use <code>catch</code> and <code>throw</code> to end the web search as soon as we find a result:
  </p>
  
  <pre>def show_rank_for(target, query)
  rank = catch(:rank) {
    each_google_result_page(query, 6) do |page, page_index|
      each_google_result(page) do |result, result_index|
        if result.text.include?(target)
          throw :rank, (page_index * 10) + result_index
        end
      end
    end
    "&lt;not found&gt;"
  }
  puts "#{target} is ranked #{rank} for search '#{query}'"
end</pre>
  
  <p>
    This time we&#8217;ve wrapped the whole search in a <code>catch{...}</code> block. We tell the <code>catch</code> block what symbol to catch, in this case <code>:rank</code>. When the result we are looking for is found, instead of setting a variable we throw the symbol <code>:rank</code>. We also give <code>throw</code> a second parameter, the search result <code>:rank</code>. This second parameter is the throw&#8217;s &#8220;payload&#8221;.
  </p>
  
  <p>
    The <code>throw</code> &#8220;throws&#8221; execution up to the <code>catch</code> block, breaking out of all the intervening blocks and method calls. Because we gave the <code>throw</code> and <code>catch</code> the same symbol (<code>:rank</code>), the <code>catch</code> block is matched to the <code>throw</code> and the thrown symbol is &#8220;caught&#8221;.
  </p>
  
  <p>
    The rank value that we gave as a payload to throw now becomes the return value of the <code>catch</code> block. We assign the result value to a variable, and proceed normally.
  </p>
  
  <p>
    What if the search string is never found, and <code>throw</code> is never called? In that case, the loops will finish, and the return value of the <code>catch</code> block will be the value of the last statement in the block. We provide a default value (&#8220;<not found>&#8221;) for just this possibility.
  </p>
  
  <h3>
    catch and throw in the real world
  </h3>
  
  <p>
    The <a href="http://rack.rubyforge.org/">Rack</a> and <a href="http://www.sinatrarb.com/">Sinatra</a> projects provide a great example of how <code>throw</code> and <code>catch</code> can be used to terminate execution early. Sinatra&#8217;s <code>#last_modified</code> method looks at the HTTP headers supplied by the client and, if they indicate the client already has the most recent version of the page, immediately ends the action and returns a &#8220;Not modified&#8221; code. Any expensive processing that would have been incurred by executing the full action is avoided.
  </p>
  
  <pre>get '/foo' do
  last_modified some_timestamp
  # ...expensive GET logic...
end</pre>
  
  <p>
    Here&#8217;s a simplified version of the <code>#last_modified</code> implementation. Note that it throws the <code>:halt</code> symbol. Rack catches this symbol, and uses the supplied response to immediately reply to the HTTP client. This works no matter how many levels deep in method calls the <code>throw</code> was invoked.
  </p>
  
  <pre>def last_modified(time)
  response['Last-Modified'] = time
  if request.env['HTTP_IF_MODIFIED_SINCE'] &gt; time
    throw :halt, response
  end
end</pre>
  
  <p>
    The way Rack uses <code>catch/throw</code> illustrates an important point: the <code>throw</code> call does not have to be in the same method as the <code>catch</code> block.
  </p>
  
  <h3>
    Conclusion
  </h3>
  
  <p>
    Ruby is a language that tries to anticipate your needs as a programmer. One common need is a way to terminate execution early when we find there is no further work to be done. Unlike in some languages, where we would have to either abuse the exception mechanism or use multiple loop breaks and method returns to achieve the same effect, Ruby provides us with the <code>catch</code> and <code>throw</code> mechanism to quickly and cleanly make an early escape. This leaves <code>begin/raise/rescue</code> free to be used for errors, and nothing else.
  </p>
  
  <p class="alert">
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>, <a href="http://technorati.com/tag/Avdi+Grimm" rel="tag"> Avdi Grimm</a>
