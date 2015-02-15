---
title: Ruby and Twitter
author: Satish Talim
date: 2008-03-24
layout: post
permalink: /2008/03/24/ruby-and-twitter/
categories:
  - Code Snippets
  - Ruby
  - Training
---
<div>
  <p>
    <strong><a href="http://twitter.com/home">Twitter</a></strong> is a service for friends, family, and coâ€“workers to communicate and stay connected through the exchange of quick, frequent answers to one simple question: What are you doing?
  </p>
  
  <p>
    They say that Twitter is on its way to becoming the next killer app.
  </p>
  
  <p>
    <a href="http://rubyforge.org/projects/twitter/">RubyForge</a> has a command line interface and <a href="http://twitter.rubyforge.org/twitter/">Ruby api wrapper</a> for twitter.
  </p>
  
  <p>
    I got hooked on to Twitter just today, when I came across this api. The documentation is not all that complete, given the fact that only John Nunemaker is working on this project. Nevertheless, let us see how this works.
  </p>
  
  <p>
    To get started:
  </p>
  
  <ul>
    <li>
      First install the twitter gem by typing the following at the command prompt: <strong>gem install twitter</strong>
    </li>
    <li>
      The sample program mytwitter.rb below, is self explanatory
    </li>
  </ul>
  
  <pre><code># mytwitter.rb
require 'twitter'

twitter = Twitter::Base.new('your_username', 'your_password')

# to make a post
twitter.post('Posting this message from a Ruby program!')

# returns an array of users who are in your friends list
puts '', "Your Friends", "=" * 50
twitter.friends.each do |u|
  puts u.name, u.status.text
  puts
end

</code></pre>
  
  <p>
    Have fun!
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Twitter" rel="tag"> Twitter</a>
