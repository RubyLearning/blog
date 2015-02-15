---
title: '&#8220;AkitaOnRails&#8221; On Anatomy of Ruby Blocks/Closures'
author: Fabio Akita
date: 2007-11-30
layout: post
permalink: /2007/11/30/akitaonrails-on-anatomy-of-ruby-blocksclosures/
topsy_short_url:
  - http://bit.ly/97Jc8R
categories:
  - Beginners
  - Rails
  - Ruby
  - Training
---
<div>
  <p>
    <em><strong>Fabio Akita&#8217;s</strong> &#8220;AkitaOnRails&#8221; series at RubyLearning.com, for would-be Ruby developers, has been quite a hit. Today in another article, Fabio talks in depth about Ruby&#8217;s <strong>Blocks/Closures</strong>, This is a rather long article but well worth the time invested in reading it. The entire source code for the programs in this article is available <a href="http://tinyurl.com/2zjgjb">here</a>.</em>
  </p>
  
  <p class="block">
    <img class="alignleft" title="Fabio Akita" src="http://www.rubylearning.com/images/akita.jpg" alt="Fabio Akita" /><strong>Fabio Akita</strong> is a Brazilian Rails enthusiast, also known online as &#8220;AkitaOnRails&#8221;. He regularly write posts on his own <a href="http://www.akitaonrails.com/">blog</a> and had published the very first book tailored for the Brazilian audience called &#8220;Repensando a Web com Rails&#8221;. He is now a full-time Ruby on Rails developer working as Brazil Rails Practice Manager for the Utah company Surgeworks LLC.
  </p>
  
  <p>
    <strong>Note</strong>: You may want to brush up on <a href="http://rubylearning.com/satishtalim/ruby_blocks_and_procs.html">Ruby Blocks and Procs</a> before going through Fabio&#8217;s article.
  </p>
  
  <p>
    <strong>Fabio>></strong> There is no Rubyism more difficult to explain, than a Closure. I could write an entire book about it. Instead of boring everyone to death with academics, I&#8217;ll try to focus only on what one really needs for day-to-day activities.
  </p>
  
  <p>
    Let&#8217;s start with an example:
  </p>
  
  <pre><code>&lt;span style="color:blue"># program1.rb
for i in [1,2,3,4]
  puts i
end

a = 0
b = [1,2,3,4]
while a &lt; b.length
  puts b[a]
  a += 1
end&lt;/span></code></pre>
  
  <p>
    These are very simple iterators, similar to what we have in several languages. The first one with a &#8216;<strong>for</strong>&#8216; construct and the second with the familiar &#8216;<strong>while</strong>&#8216; statement. Nothing fancy here. But let&#8217;s see another way of accomplishing the same thing in Ruby:
  </p>
  
  <pre><code>&lt;span style="color:blue"># program2.rb
[1,2,3,4].each { |i| puts i }

[1,2,3,4].each do |i|
  puts i
end&lt;/span></code></pre>
  
  <p>
    Not too shabby, simpler and elegant, but that&#8217;s where people start gasping. The pipes notation is particularly threatening for non-starters. Both the brackets and the do..end notations define an enclosed piece of code that we name as &#8216;blocks&#8217; or &#8216;closures&#8217;. What&#8217;s between the pipes are like parameters to a method. It &#8216;feels&#8217; like this pseudo-code:
  </p>
  
  <pre><code>&lt;span style="color:blue">def unnamed_method(i)
  puts i
end

[1,2,3,4].each(unnamed_method)&lt;/span></code></pre>
  
  <p>
    This is not valid Ruby code, of course. That&#8217;s similar to what we would do in C# with delegates. We have something similar in JavaScript (using the &#8220;Prototype&#8221;:<a href="http://www.prototypejs.org/api/enumerable/each">http://www.prototypejs.org/api/enumerable/each</a> library):
  </p>
  
  <pre><code>&lt;span style="color:blue">[1,2,3,4].each(function(i) {
  alert(i);
});&lt;/span></code></pre>
  
  <p>
    In Javascript functions are first-class citizens of the language and they can be defined anonymously (without a name), and then passed as parameters to another function. We can manipulate and move functions all over the place.
  </p>
  
  <p>
    Ruby doesn&#8217;t have methods as first-class citizens. We actually can extract a method from an object and wrap it around a &#8216;<strong>Method</strong>&#8216; object, but it holds the context of its object, so it is not independent.
  </p>
  
  <pre><code>&lt;span style="color:blue"># program3.rb
class Test
  def initialize
    @hello = "Hello!"
  end
  def say
    @hello
  end
end

m = Test.new.method(:say)
puts m.call # => "Hello!"
puts m.class # => "Method"&lt;/span></code></pre>
  
  <p>
    Here, we extracted the :say method from the instantiated Test instance. Notice that we can now manipulate the method as a normal object. Whenever we send the &#8216;<strong>call</strong>&#8216; message to the method object, it runs as if it was being executed from the context of the original object (Test.new.say). In the above example the second last statement would successfully print &#8220;Hello!&#8221;, as stored in the local instance variable @hello.
  </p>
  
  <p>
    Although simple, we don&#8217;t do this very often. That&#8217;s because this method is bound to the original object&#8217;s context and we don&#8217;t usually want that: it would be nice to have an independent block of code. So, let&#8217;s create one very simple block of code referenced by a variable:
  </p>
  
  <pre><code>&lt;span style="color:blue"># program4.rb
c = lambda { |i| puts i }
c.call(1) # => 1
c.call(2) # => 2&lt;/span></code></pre>
  
  <p>
    The &#8216;<strong>lambda</strong>&#8216; keyword encloses the code within brackets as an object block, an instance of the <strong>Proc</strong> class. This object responds to the &#8216;<strong>call</strong>&#8216; method. In the last two statements we pass parameters to the &#8216;<strong>call</strong>&#8216; method and it goes to the &#8216;i&#8217; variable defined within pipes inside the block. So, it acts as an independent entity, detached from any particular class. Let&#8217;s test it:
  </p>
  
  <pre><code>&lt;span style="color:blue"># program5.rb
c = lambda { |i| puts i }

class Test
  def say(block)
    block.call(self.class)
  end
end

c.call(self.class) # => Object
Test.new.say(c)    # => Test&lt;/span></code></pre>
  
  <p>
    We&#8217;re using the same block defined above in the variable &#8216;c&#8217;. After the definition of the Test class, we call the block object passing &#8216;self.class&#8217; and it returns <strong>Object</strong> as a result. Then, we call the :say method from inside an instance of the Test class. The :say method calls the block giving the inner &#8216;self.class&#8217; as a block parameter. In this case it prints out &#8216;Test&#8217; instead of &#8216;<strong>Object</strong>&#8216;, meaning that the block binds itself to the enclosing scope. That&#8217;s one difference between a block and a detached object method.
  </p>
  
  <p>
    In many ways, Blocks resembles anonymous functions from Javascript, anonymous delegates from C#, anonymous inner classes from Java. This is a very useful construct that was primarily created to better handle iterators. For instance:
  </p>
  
  <pre><code>&lt;span style="color:blue"># program6.rb
[1,2,3,4].reverse_each { |i| puts i }
# => 4 
# => 3
# => 2
# => 1&lt;/span></code></pre>
  
  <p>
    Now, this is different from the Array&#8217;s &#8216;<strong>each</strong>&#8216; method we used before. &#8216;<strong>reverse_each</strong>&#8216; navigates backwards through the Array&#8217;s elements. It gets each element and passes it into the &#8216;i&#8217; variable, set as a parameter for the block defined within brackets.
  </p>
  
  <p>
    In languages like Java, everything has to be defined through an interface. Enumerators are no different, and we have interfaces like &#8216;Iterator&#8217;. This method defines simple methods as &#8216;hasNext()&#8217; and &#8216;next()&#8217;. But what if we actually need something as a reverse iterator? Now we&#8217;re on our own. What if we need something more complicated like an iterator that only walks through even elements? In Ruby we can define such a method like this:
  </p>
  
  <pre><code>&lt;span style="color:blue"># program7.rb
class Array
  def even
    i = 0
    while i &lt; self.size
      yield(self[i]) if i % 2 == 0
      i += 1
    end
  end
end

[1,2,3,4,5,6].even { |i| puts i }
# => 1
# => 3
# => 5&lt;/span></code></pre>
  
  <p>
    First of all, remember that Ruby&#8217;s classes are all open, so we can easily redefine the standard <strong>Array</strong> class and append new methods to it. Now pay attention to the &#8216;even&#8217; method. We implement it the usual way with a &#8216;while&#8217; loop. But the interesting bit is the &#8216;<strong>yield</strong>&#8216; keyword. Pretend that it works like a *wildcard placeholder* for blocks. In the example, when we pass the &#8216;self[i]&#8217; value as its parameter, we&#8217;re actually passing this value to the &#8216;i&#8217; parameter in the block.
  </p>
  
  <p>
    We can rewrite this method in a slightly different way but with the same behavior:
  </p>
  
  <pre><code>&lt;span style="color:blue"># program8.rb
class Array
  def even(&#038;code)
    i = 0
    while i &lt; self.size
      code.call( self[i] ) if i % 2 == 0
      i += 1
    end
  end
end&lt;/span></code></pre>
  
  <p>
    So, now we explicitly defined that the &#8216;even&#8217; method expects to receive a block, converting it to the &#8216;code&#8217; parameter. Then, inside it we send the &#8216;<strong>call</strong>&#8216; method to &#8216;code&#8217; and pass &#8216;self[i]&#8217; as its parameter. The result is exactly the same as using the <strong>yield</strong> keyword.
  </p>
  
  <p>
    We can still do it differently:
  </p>
  
  <pre><code>&lt;span style="color:blue"># program9.rb
class Array
  def even(block)
    i = 0
    while i &lt; self.size
      block.call( self[i] ) if i % 2 == 0
      i += 1
    end
  end
end&lt;/span></code></pre>
  
  <p>
    Now we&#8217;re doing it without the ampersand in the parameter. In the previous example, the ampersand operator &#8216;captures&#8217; a block into a <strong>Proc</strong> instance object. In the latest example, the &#8216;even&#8217; method expects to directly receive a <strong>Proc</strong> object, like this:
  </p>
  
  <pre><code>&lt;span style="color:blue"># program10.rb
class Array
  def even(block)
    i = 0
    while i &lt; self.size
      block.call( self[i] ) if i % 2 == 0
      i += 1
    end
  end
end
c = lambda { |i| puts i }
[1,2,3,4,5,6].even( c )&lt;/span></code></pre>
  
  <p>
    Let&#8217;s go back to the Array&#8217;s &#8216;<strong>each</strong>&#8216; method as we displayed before:
  </p>
  
  <pre><code>&lt;span style="color:blue">c = lambda { |i| puts i }
[1,2,3,4].each( &#038;c )&lt;/span></code></pre>
  
  <p>
    A little bit different, because the &#8216;<strong>each</strong>&#8216; method doesn&#8217;t expect a <strong>Proc</strong> object as a parameter, but an actual Block. So we use the ampersand before the <strong>Proc</strong> instance variable and it kind of &#8216;expands&#8217; it back into a &#8216;raw&#8217; code block, so that the &#8216;even&#8217; method can &#8216;yield&#8217; it inside, instead of executing through the &#8216;<strong>call</strong>&#8216; method.
  </p>
  
  <p>
    This usage of a <strong>Proc</strong> object is not as elegant as just passing a Block, but with this construct we are storing code within an object. We can define a method that receives as many blocks as we need, for instance:
  </p>
  
  <pre><code>&lt;span style="color:blue"># program11.rb
def foo(name, block1, block2)
  block1.call
  puts name
  block2.call
end

foo "Fabio", lambda { puts "Hello" }, lambda { puts "World" }&lt;/span></code></pre>
  
  <p>
    This example receives a normal parameter and 2 blocks instead of one. We can pass blocks as enclosed <strong>Proc</strong> objects in the parameters list as we would do with any other kind of object. We usually don&#8217;t need that many discrete blocks inside a single method. The most usual style is:
  </p>
  
  <pre><code>&lt;span style="color:blue"># program12.rb
def foo( param1, param2 )
  # do something
  some_param = 1
  yield( some_param ) if block_given?
end

foo(1, 2) do |some_param|
  # do something
end&lt;/span></code></pre>
  
  <p>
    So we define a normal method, with normal parameters. But inside it we ask &#8216;<strong>block_given?</strong>&#8216;. If positive, it &#8216;yields&#8217; its block passing some parameter to it (of course, parameters are optional, and you can pass as many parameters as you want to a block, even zero parameters).
  </p>
  
  <p>
    We call the defined method as usual, passing a block at the end of the method call. By the way, here&#8217;s another way of defining a block: using the do .. end construct. There is no strict rule, but we reserve the brackets notation when the block is small and we can state it in a single line, and the do .. end notation when we have blocks with multiple statements inside.
  </p>
  
  <p>
    There&#8217;s a gotcha:
  </p>
  
  <pre><code>&lt;span style="color:blue">foo a, b do |some_param|
  # do something
end

foo a, b { |some_param| # do something }&lt;/span></code></pre>
  
  <p>
    Both brackets and do .. end constructs define blocks, so at first glance the 2 above statements seems to do the same thing. But the gotcha is that in Ruby parenthesis are optional, and we&#8217;re not using them here.
  </p>
  
  <p>
    In the first statement the block is assumed to be passed to the &#8216;foo&#8217; method as expected, with &#8216;a&#8217; and &#8216;b&#8217; as normal parameters. But the second statement guesses that &#8216;b&#8217; is a method and tries to pass the block to it. The recommendation is: if you have a method that needs both parameters and a block, enclose the parameters within parenthesis to avoid ambiguities.
  </p>
  
  <p>
    We now understand that <strong>Blocks are pieces of code that can be exchanged between method calls, as parameters or returned values</strong>. But there is more to it:
  </p>
  
  <pre><code>&lt;span style="color:blue"># program13.rb
c = lambda { |i| puts i }
c = Proc.new { |i| puts i }
c = proc { |i| puts i }&lt;/span></code></pre>
  
  <p>
    The above 3 statements do the same thing: instantiate a block object. &#8216;proc&#8217; is an alias for &#8216;<strong>lambda</strong>&#8216; and they work slightly different than &#8216;<strong>Proc.new</strong>&#8216;. In Ruby 1.9, &#8216;proc&#8217; will probably be an alias for &#8216;<strong>Proc.new</strong>&#8216; instead.
  </p>
  
  <p>
    <strong>Keywords to keep in mind are</strong>:
  </p>
  
  <ul>
    <li>
      <strong>lambda/Proc.new</strong> &#8211; encloses a bunch of code inside a <strong>Proc</strong> instance.
    </li>
    <li>
      & &#8211; ampersand, either captures a &#8216;raw&#8217; code block into a <strong>Proc</strong> object or expands the <strong>Proc</strong> object as a &#8216;raw&#8217; block.
    </li>
    <li>
      {}/do..end &#8211; defines a code block.
    </li>
    <li>
      || &#8211; pipes, defines the parameters of a block. If you don&#8217;t need any, just omit the pipes altogether.
    </li>
  </ul>
  
  <p>
    So, some people misinterpret Blocks as a simple function pointer, or something like Java&#8217;s anonymous inner class. That&#8217;s not the case: and here we finally boil down to &#8220;Closures&#8221;. Ruby Blocks are Closures. The words &#8216;blocks&#8217; and &#8216;closures&#8217; mean the same thing in Ruby.
  </p>
  
  <p>
    Ruby Blocks can enclose not only code and it&#8217;s own inner local variables, but it can enclose the surrounding context variables. That&#8217;s why it is called a &#8216;closure&#8217;. Let&#8217;s see an example:
  </p>
  
  <pre><code>&lt;span style="color:blue"># program14.rb
def greetings_factory(prefix)
  Proc.new { |name| "#{prefix}, #{name} !"}
end

birthday = greetings_factory("Happy Birthday")
xmas = greetings_factory("Merry XMas")

puts birthday.call("David") # => "Happy Birthday, David !"
puts xmas.call("Matz")      # => "Merry XMas, Matz !"&lt;/span></code></pre>
  
  <p>
    The first thing is a method definition for &#8216;greetings_factory&#8217;. It gets a prefix as a parameter and returns a <strong>Proc</strong> object, whose inner parameter is a name. So far so good.
  </p>
  
  <p>
    The second part defines 2 <strong>Proc</strong> instances, one for birthday and another for christmas. Notice that we pass 2 different prefixes into the &#8216;greetings_factory&#8217; method. The different values are &#8216;closed&#8217; within Block. So, when we later call them, we see how differently they behave: they actually stored the latest state within itself. So each block stored the &#8216;prefix&#8217; variable passed before, while still accepting the &#8216;name&#8217; parameter within the Block.
  </p>
  
  <p>
    Keep in mind that every Ruby Block is a Closure, that&#8217;s why this construct actually works:
  </p>
  
  <pre><code>&lt;span style="color:blue"># program15.rb
list = []
[1,2,3,4].each do |i| 
  list &lt;&lt; i * 2 
end
puts list.inspect # => [2, 4, 6, 8]&lt;/span></code></pre>
  
  <p>
    So, we defined a &#8216;list&#8217; array *before* we create the iterator block. Then, inside the block we refer to the external &#8216;list&#8217; array and populate it. In Java, this would&#8217;ve been a final variable, but in Ruby there is no such limitation.
  </p>
  
  <p>
    You&#8217;d want to be very careful about the surroundings of your block: do not define variables that&#8217;s going to be used inside the blocks too early in the code. Try to keep dependencies nearby, like in the above example where the &#8216;list&#8217; Array is defined right before the iterator itself.
  </p>
  
  <p>
    Iterators get a big boost because we&#8217;re not limited to a hard Interface. We can add whatever methods we need, like &#8216;each&#8217;, &#8216;reverse_each&#8217;, &#8216;collect&#8217;, &#8216;select&#8217; and so on. Each one of them can receive a block and pass one element at a time to the user-defined block.
  </p>
  
  <p>
    Another very important usage is to enclose widely used code patterns. For example, Rails has the following construct to use database transactions:
  </p>
  
  <pre><code>&lt;span style="color:blue">User.transaction do 
  u = User.new(:login => 'admin')
  u.save!
end&lt;/span></code></pre>
  
  <p>
    &#8216;User&#8217; would be the <strong>ActiveRecord</strong> instance. One example of the structure for the model&#8217;s &#8216;transaction&#8217; class method would resemble this structure:
  </p>
  
  <pre><code>&lt;span style="color:blue">class ActiveRecord::Base
  def self.transaction
    begin
      ActiveRecord::Base.establish_connection
      yield if block_given?
    rescue => e
      RAILS_DEFAULT_LOGGER.error e
    ensure
      ActiveRecord::Base.remove_connection 
    end
  end
end&lt;/span></code></pre>
  
  <p>
    This means: open the database then try to &#8216;yield&#8217; the block if provided. If anything wrong happens, get the error message and log it. Finally ensure that the connection is dropped after all this.
  </p>
  
  <p>
    <strong>ActiveRecord</strong> doesn&#8217;t open and close connections this often, but you get the idea. But this is an overall big picture of one way to avoid repetition and the extraction of common code patterns. So it&#8217;s clever to encapsulate common functionality and place in a placeholder for user-defined code in-between.
  </p>
  
  <p>
    The <strong>File.open</strong> method does the same thing: it takes responsibility of properly opening files, yielding the user block and ensuring that the file is closed without the user having to manually do this kind of house cleaning.
  </p>
  
  <p>
    The most important &#8220;concept&#8221;:<a href="http://martinfowler.com/bliki/Closure.html">http://martinfowler.com/bliki/Closure.html</a> is that Blocks helps hiding implementation details. We don&#8217;t want to know the inner details of a list iterator, or how a transaction works. We just need to focus on the business logic itself, trapped within a Block.
  </p>
  
  <p>
    We described here a lot of stuff, and I think it covers the basics. Enough to actually read some of the Rails source-code and get acquainted for closure&#8217;s modus operandi. Hope you enjoyed this article!
  </p>
  
  <p>
    <em>Thank you Fabio for showing us a different perspective on Ruby Blocks. In case you have any queries, questions on this article, kindly post your questions here and Fabio would be glad to answer.</em>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Brazil" rel="tag">Brazil</a>, <a href="http://technorati.com/tag/Fabio+Akita" rel="tag">Fabio Akita</a>, <a href="http://technorati.com/tag/Rails" rel="tag">Rails</a>, <a href="http://technorati.com/tag/Ruby+Blocks" rel="tag">Ruby Blocks</a>, <a href="http://technorati.com/tag/Ruby+Programming" rel="tag">Ruby Programming</a>
