---
title: "Do you know what's new in Ruby 1.9?"
author: Carlo Pecchia
date: 2010-10-26
layout: post
permalink: /2010/10/26/do-you-know-whats-new-in-ruby-1-9/
thesis_description:
  - "Carlo Pecchia walks us thro' the changes in Ruby 1.9 in this guest post on RubyLearning."
thesis_keywords:
  - Programming, Ruby 1.9,Ruby programming
topsy_short_url:
  - http://bit.ly/9TeJ4R
categories:
  - beginners
  - ruby
  - ruby masters
tags:
  - programming
  - ruby 1.9
  - ruby programming
---
<div>
  <h3>
    Do you know what&#8217;s new in Ruby 1.9?
  </h3>
  
  <p class="update">
    This guest post is by <strong><a href="http://carlopecchia.eu/">Carlo Pecchia</a></strong>, who is an IT engineer mainly interested on agile methodologies and &#8220;good practices&#8221; for developing large and complex systems. He is also interested in web architectures and emerging programming languages.
  </p>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/carlopecchia.jpg" alt="Carlo Pecchia" title="Carlo Pecchia" width="125" height="125" /> <span class="drop_cap">W</span>ith major version 1.9 the Ruby language took a series of improvements devoted to rationalizing and better organizing the internal structure of the language itself.
  </p>
  
  <p>
    The language &#8220;core&#8221; sized from around 3 MB in version 1.0 to 30 in version 1.9: we see that both internal and external (some interfaces) refactoring was needed. Let me show you the main improvements introduced.
  </p>
  
  <h3>
    Smart things
  </h3>
  
  <p>
    A list of a general &#8211; smart &#8211; improvements: <tt>Rubygems</tt> in now officially a part of Ruby, and so is <tt>Rake</tt>. Some poorly used libraries were removed from the core &#8211; but always available as gems: soap, jruby, etc.
  </p>
  
  <h3>
    Objects hieararchy
  </h3>
  
  <p>
    A new root in the class hierarchy was introduced <tt>BasicObject</tt>:
  </p>
  
  <pre>1.8 =&gt; [Class, Module, Object, Kernel]
1.9 =&gt; [Class, Module, Object, Kernel, BasicObject]

BasicObject.instance_methods
# =&gt; [:==, :equal?, :!, :!=, :instance_eval, :instance_exec, :__send__]
</pre>
  
  <p>
    This serves to better organize things internally. This class is so &#8220;basic&#8221; that it doesn&#8217;t give even the <tt>object_id</tt>, in fact the last statement will generate an error (&#8216;undefined method&#8230;&#8217;):
  </p>
  
  <pre>foo = BasicObject.new
foo.object_id
</pre>
  
  <h3>
    Loving chain methods
  </h3>
  
  <p>
    More often in Ruby than in other languages, the chain methods style is used. In order to improve this &#8220;technique&#8221; the new method <tt>tap</tt> has been released (and backported into 1.8 too):
  </p>
  
  <pre>>puts "Hello".reverse
            .tap{ |o| puts "reversed: #{o}" }
            .upcase

# =&gt; reversed: olleH
# =&gt; OLLEH
</pre>
  
  <p>
    Basically, we can now also &#8220;do something else too&#8221; with the object in the chain.
  </p>
  
  <h3>
    Main changes
  </h3>
  
  <p>
    Let us now see the main areas where changes were introduced: symbols, arrays, hashes and blocks. And finally, an interesting improvement toward parallelism: the fibers.
  </p>
  
  <h3>
    Symbols
  </h3>
  
  <p>
    Symbols are now interpreted as string wrt regular expressions:
  </p>
  
  <pre>>a = [:windows, :mac, :amiga]
puts a.grep(/ac/)

# 1.8 =&gt; []
# 1.9 =&gt; mac
</pre>
  
  <p>
    We can also get a Proc from a symbol:
  </p>
  
  <pre>u = :upcase.to_proc
u.call('lorem ipsum...')
</pre>
  
  <h3>
    Arrays
  </h3>
  
  <p>
    Arrays, a fundamental store in any modern language, have been deeply revisited:
  </p>
  
  <ul>
    <li>
      the method <tt>to_a</tt> doesn&#8217;t belong to the <tt>Object</tt> class.
    </li>
    <li>
      arrays can be easily created with the homonym class (eg: <code>a = Array('apple', 'bananas')</code>) for an improved code readability.
    </li>
    <li>
      in such a creation the implicit separator &#8211; default is &#8220;\n&#8221; &#8211; is not considered.
    </li>
    <li>
      the splat operator (<code>*a = some_array_here</code>) has a more consistent behaviour.
    </li>
  </ul>
  
  <h3>
    Hashes
  </h3>
  
  <p>
    Now hashes (finally!) are stable data structures: elements keep order insertion. Even a Hash is not &#8211; by definition &#8211; such a kind of data abstraction, that feature can be very handy.
  </p>
  
  <p>
    It&#8217;s now possible to declare hashes differently (use name: value pairs to create a hash if the keys are symbols):
  </p>
  
  <pre>data = { jan: 201234, feb: 234234, mar: 234345 }
</pre>
  
  <p>
    And that, obviously, make obsolete some other forms: if-then-else with colon and splat hashes definition (eg: <code>h = {"jan", 201234, "feb", 234234, "mar", 234345}</code>).
  </p>
  
  <p>
    <b>Easy access within a string</b>:
  </p>
  
  <pre>puts "First two months of this year was: %{jan} and %{feb}" % data
</pre>
  
  <p>
    Finally, to make things more consistently, we have two major differences:
  </p>
  
  <ul>
    <li>
      <tt>select</tt> method on hash &#8211; that aim to act like a &#8220;filter&#8221; &#8211; return a hash (in 1.8 it returns an array of arrays&#8230;)
    </li>
    <li>
      <tt>to_s</tt> method return and internal representation of the hash, rather than join together keys and values.
    </li>
  </ul>
  
  <h3>
    Blocks
  </h3>
  
  <p>
    Still considering the mantra word &#8220;rationalization&#8221;, blocks and methods share the same syntax for parameters:
  </p>
  
  <pre>def my_method(foo, bar=10, *baz)
  ...
end

lambda {|foo, bar=10, *baz| ...}
</pre>
  
  <p>
    An interesting &#8220;correction&#8221; was made on block parameters: now they are local variables and don&#8217;t collide with external references:
  </p>
  
  <pre>foo = 'this is an external variable'
bar = 23

10.times do |foo|
  bar = foo + 1
  # foo here is unrelated from the external name
end
</pre>
  
  <p>
    <b>This was a major issue in language version 1.8.</b>
  </p>
  
  <p>
    Of course, if <tt>within</tt> a block (outside parameters list) we reference an external variable, that one will be modified. With 1.9 we can &#8220;protect&#8221; such variables declaring an internal homonym:
  </p>
  
  <pre>foo = 'this is an external variable'
bar = 23

10.times do |i;foo|
  bar = bar + 1
  foo = bar % 2
end

# foo untouched, but bar modified
</pre>
  
  <h3>
    Fibers
  </h3>
  
  <p>
    We will see an increasing usage of parallelism techniques in programming, and the spread of (really interesting) languages like Clojure and Erlang is a clear sign. Ruby too &#8211; with 1.9 &#8211; offers a nice tool for programmers: fibers.
  </p>
  
  <p>
    They are a lightweight processes &#8211; memory footprint is only 4Kbytes &#8211; conceived for a cooperative concurrence. Basically we can think of them like Procs that maintain status over calls:
  </p>
  
  <pre>fb = Fiber.new do |val|
  Fiber.yield "That's all... (#{val})"
  Fiber.yield "folks! (#{val})"
end

puts fb.resume 10
...
puts fb.resume 20
</pre>
  
  <h3>
    A final note
  </h3>
  
  <p>
    The transition &#8211; fairly smooth in my opinion &#8211; towards version 1.9 is still in progress. I hope this post helps you to understand the major differences and to act accordingly when coding, both by your own and on someone elses code.
  </p>
  
  <p class="attn">
    <img class="alignleft" height="48" width="48" alt="Alert!" src="http://rubylearning.com/images/icon_warning.png" title="Alert!" /><strong>A final tip:</strong> pay attention when using a gem &#8211; the interesting project <a href="http://isitruby19.com/">http://isitruby19.com/</a> can help you see if a gem is already ported on Ruby 1.9.
  </p>
  
  <p>
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
  
  <p>
    <strong><em>Do read</em> these awesome Guest Posts:</strong>
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/25/the-value-of-a-personal-bug-log/">The value of a personal bug log</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/18/do-you-enjoy-your-code-quality/">Do You Enjoy Your Code Quality?</a>
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/Ruby+1.9" rel="tag"> Ruby 1.9</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>
