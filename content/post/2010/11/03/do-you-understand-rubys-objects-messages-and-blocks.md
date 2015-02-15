---
title: 'Do You Understand Ruby&#8217;s Objects, Messages and Blocks?'
author: Ed Howland
date: 2010-11-03
layout: post
permalink: /2010/11/03/do-you-understand-rubys-objects-messages-and-blocks/
thesis_description:
  - "Ed Howland de-constructs Ruby's message protocol and looks into what is really going on behind the scenes. A guest blog post on RubyLearning."
thesis_keywords:
  - Ruby Objects, Ruby Messages,Ruby Blocks,Programming,Ruby programming
topsy_short_url:
  - http://bit.ly/admgNf
categories:
  - Beginners
  - Ruby
  - Ruby Masters
tags:
  - programming
  - Ruby Blocks
  - Ruby Messages
  - Ruby Objects
  - ruby programming
---
<div>
  <h3 id="objects-messages-and-blocks">
    Do You Understand Ruby&#8217;s Objects, Messages and Blocks?
  </h3>
  
  <p class="update">
    This guest post is by <strong><a href="http://greenprogrammer.wordpress.com/">Ed Howland</a></strong>, an independent consultant who has worked in Ruby and RoR for more than 5 years, since the 0.13 days of Rails. He has over 22 years in the software development industry working on mainly O-O projects in C/C++, Java, Perl and PHP. Ed is a frequent speaker at regional conferences and local Ruby/Linux user groups.
  </p>
  
  <h3 id="introduction">
    Introduction
  </h3>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/ed_howland.jpg" alt="Ed Howland" title="Ed Howland" width="125" height="125" /> <span class="drop_cap">R</span>uby is a very elegant and expressive language. Consider the following complete Ruby program (one of the first examples I was exposed to, reconstructed from memory):
  </p>
  
  <pre>#!/usr/bin/env ruby
Dir[ARGV.first+'/*'].each {|f| File.rename f, f.downcase}
</pre>
  
  <p>
    Running <code>./rename.rb .</code> will rename all files in the current directory into their lowercase equivalents. Useful for importing a DOS/Windows directory to Linux. When I showed this to my friend Mark, an IT pro, he grokked it immediately.
  </p>
  
  <p>
    But how does it work?
  </p>
  
  <p>
    Actually, all that is going on here is a bunch of Ruby objects that are talking to each other. By deconstructing Ruby&#8217;s object-message protocol, we can analyze almost any Ruby code and discover how it works internally.
  </p>
  
  <h3 id="objects">
    Objects
  </h3>
  
  <p>
    In Ruby, nearly everything is an object. Classically object-oriented languages define an object as something that maintains state and exhibits behavior. While this is true in Ruby, I think it is more precise to say that Ruby objects contain other objects and respond to messages. You might say that Ruby is a &#8216;message oriented&#8217; language.
  </p>
  
  <h3 id="messages">
    Messages
  </h3>
  
  <pre>:message [payload1, ... payloadN]
</pre>
  
  <p>
    A Ruby message consists of a name, usually represented by a symbol such as :message, and an optional payload. The payload is often called the list of arguments or parameters. The payload, if present, is a list of other objects.
  </p>
  
  <p>
    When the object receives the message, it handles it and returns some other object. Each object has a number of message handlers corresponding to the messages it responds to. In the Ruby program above, the fragment <code>f.downcase</code>, the &#8216;f&#8217; variable, which is a string containing the current filename, is sent the message <code>:downcase</code>, and it returns a new string that is converted to lowercase.
  </p>
  
  <p>
    Some other messages:
  </p>
  
  <pre>1.send :+, 2
1.+ 2       # same thing
1 + 2       # same thing
</pre>
  
  <p>
    You can use the <code>send</code> method on any object to invoke a message handler. Ruby gives us a lot of syntax sugar to make it easy to express messages. We don&#8217;t need to use the <code>send</code> method, we can just use the shortcut ‘.’ (dot) operator.
  </p>
  
  <p>
    Ruby also provides some other syntactic sugar. In some cases, we can just use the message name inline, as in <code>1 + 2</code>. In another case, the :[] message can have its payload embedded between the braces. <code>Dir['*']</code> is the same as <code>Dir.[]('*')</code>. There is also the &#8216;=&#8217; message, which can be appended to another message name, such as an instance variable setter and then used inline. <code>a.iv=(13)</code> is the same as <code>a.iv = 13</code>. (This is what happens when you use the <code>attr_writer</code> to declare an instance variable set method.)
  </p>
  
  <p>
    The payload of a message can be defined as having (in this sequence) required arguments, optional (or default) arguments, a variable number of arguments and an implicit or explicit block. Default arguments are specified with <code>arg=value</code>. The variable arguments are collected in &#8216;‘splatted&#8217; (&#8216;*&#8217;) parameter. In the message handler, every actual argument is collected in a list.
  </p>
  
  <p>
    The explicit block argument is declared with a preceding &#8216;&&#8217;, as in <code>&blk</code>. Default arguments are often used to emulate named parameters to a message handler. Setting a parameter to the empty hash: <code>{}</code> lets us pass in a (bare) hash as the last parameter: <code>object.method :find=&gt;true, :query=&gt;'fred'</code>. You see that in a lot of Rails code.
  </p>
  
  <p>
    Here is a complete example:
  </p>
  
  <pre>def message required, default={}, *variable, &block</pre>
  
  <p>
    We can query an object to see if it understands a certain message, with the :responds_to? message.
  </p>
  
  <pre>"AAAAA".respond_to? :downcase
 =&gt; true
</pre>
  
  <p>
    How does an object handle a message? We first need to look at blocks, a way to encapsulate Ruby code in an object. We will then expand that concept to methods, another type of object that contains code.
  </p>
  
  <h3 id="blocks">
    Blocks
  </h3>
  
  <p>
    A block is a special kind of object that contains executable code. In fact, all Ruby code is evaluated in the context of a block. Many other blocks can be declared and since they are just objects they can be used like any object. Particularly, they can be passed in the payload of a message.
  </p>
  
  <p>
    There are a variety of synonyms for blocks: &#8216;lambdas&#8217;, &#8216;procs&#8217; and &#8216;closures&#8217;. In most cases <fnref target="1" />, <fnref target="2" />, these refer to the same thing, an instance of the <code>Proc</code> class. <code>Proc</code> objects understand a variety of messages, the most significant of which is :call. The :call message invokes the code in the block.
  </p>
  
  <p>
    We can create a proc with any of the block keywords &#8216;proc&#8217;, &#8216;lambda&#8217; and &#8216;->&#8217; (the later form. &#8216;->&#8217; is new to Ruby 1.9 and above). Another way is to send the :new message to the <code>Proc</code> class itself. The code block needs to be surrounded by curly braces &#8216;{}&#8217; or by <code>do ... end</code>.
  </p>
  
  <pre>p=proc {puts "in block"}
 =&gt; #&lt;Proc:0x0000010095ca30@(irb):5&gt;
p.call
in block
</pre>
  
  <p>
    The :call message can have a payload like any other message. Inside the block, these payload objects are bound to variables defined between &#8216;||&#8217; in the front of the declaration. Collection iterators apply this approach calling the passed in block once for every element in the collection passing the element to the block. Let&#8217;s re-implement the :join message with the :inject message.
  </p>
  
  <pre>["aa","bb", "cc"].inject(['','']) {|accum,v| [', ', accum[1]+accum[0]+v]}[1]
 =&gt; "aa, bb, cc"
</pre>
  
  <p>
    The result of the last expression evaluated in the block is returned from the :call invocation. You can also explicitly return an expression with the <code>return</code> keyword at any point
  </p>
  
  <p>
    Procs or lambdas are also closures. I admit, it took me a long time to understand what that means. The most understandable closures I&#8217;ve seen involve code that creates code based on passed in parameters. Assume we want to make some micro-blogging formatters. We can combine some functions to carry out a simple setup. (Remember that blocks passed in are part of the saved context too.)
  </p>
  
  <pre>mbmakr = proc do |&blk|
  proc {|*args| blk.call(*args)[0..139]}
end

tweetr = mbmakr.call {|msg| msg}
reply = mbmakr.call {|user, msg| "@"+user+": "+msg}
retweetr = mbmakr.call {|user, msg| 'RT '+reply.call(user, msg)}
dmesgr= mbmakr.call {|user, msg| 'D '+user+' '+msg}

retweetr.call "john_x", "French tomato soup is tasty! #protip"
 =&gt; "RT @john_x: French tomato soup is tasty! #protip"
</pre>
  
  <p>
    Wow, code making code! C-3PO would be amazed.
  </p>
  
  <p>
    The context captured by a block can be retrieved via the :binding message. We can pass the binding object the :eval message and a string containing some Ruby code. The code will be evaluated in the context of the binding. This is very useful in templating systems, for example. Passing the current binding to ERb, local variables will be interpreted in the context of the template. Remember that the even the outermost code is running in a block.
  </p>
  
  <pre>require "erb"

template=ERB.new "~ &lt;%= a %&gt; ~"
a="hi there"
template.result binding
 =&gt; "~ hi there ~"
</pre>
  
  <p>
    Procs also can be queried as to their number of arguments with :arity message. A bit out of our scope, so I refer you to the Proc class documentation. We also will look at this a bit more when we discuss Methods.
  </p>
  
  <p>
    The last step on our journey to the actual implementation of a message handler are &#8216;methods&#8217;.
  </p>
  
  <h3 id="methods">
    Methods
  </h3>
  
  <p>
    If we combine a block with a name and bind it to an owner (the <em>module</em> to which it belongs) and a recipient (the <em>object</em> to which it belongs), we get a message handler. These are called &#8216;methods&#8217; which are objects too. Methods objects can only exist in the context of a module. Modules and classes are outside the scope of this article, but fortunately we can get access to the current class with the combined message <code>self.class</code>.
  </p>
  
  <p>
    One way to create a method is to send the module object the :define_method message which takes a symbol for the method name and a block containing the code to be executed when objects get that message.
  </p>
  
  <pre>self.class.send(:define_method, :greet) {|user| puts "hello #{user}"}
 =&gt; #&lt;Proc:0x000001008e4b48@(irb):78 (lambda)&gt;
greet "Fred"
hello Fred
</pre>
  
  <p>
    We can access the actual method object by sending the class the :method message. Then we can query its attributes.
  </p>
  
  <pre>m=self.class.method :greet
=&gt; #&lt;Method: Class(Object)#greet&gt;
puts m.name, m.owner, m.receiver
greet
Object
Object
</pre>
  
  <p>
    And, just like a block, we can invoke the method&#8217;s code block via its :call message.
  </p>
  
  <p>
    There is an easier way to define a method within a module: the <code>def method args ... end</code> pattern:
  </p>
  
  <pre>def who_am_i user
    "I am #{user}"
  end
</pre>
  
  <p>
    Let&#8217;s combine all we have learned so far. Imagine we&#8217;d like a very idiomatic Ruby way to create HTML text.
  </p>
  
  <pre>def opt_to_s opt={}
  opt.empty? ? '' : ' ' + opt.map {|e,v| "#{e}=\"#{v}\""}.join(', ')
end

[:html, :body, :h1].each do |el|
  start="&lt;#{el}"
  fin="&lt;/#{el}&gt;"
  self.class.send(:define_method, el) {|options={}, &blk| start + opt_to_s(options) + '&gt;' + blk.call + fin}
end

# Now, we can neatly nest tags and content
html do
  body do
    h1 :class=&gt;"bold-h1", :id=&gt;"h1_99" do
      "header"
    end
  end
end
 =&gt; "&lt;html&gt;&lt;body&gt;&lt;h1 class=\"bold-h1\", id=\"h1_99\"&gt;header&lt;/h1&gt;&lt;/body&gt;&lt;/html&gt;"
</pre>
  
  <p>
    Inside the array&#8217;s <code>each</code> iterator. methods are created using a closure containing the contracted start and fin tag fragments.
  </p>
  
  <p>
    Ruby 1.9.2 gives you a nice way to query method object parameters.
  </p>
  
  <pre>def x(a, b, c=3, *d, &e); end
self.class.method(:x).parameters
 =&gt; [[:req, :a], [:req, :b], [:opt, :c], [:rest, :d], [:block, :e]]
</pre>
  
  <p>
    This can also be accomplished with the &#8216;methopara&#8217; gem in 1.9.1.
  </p>
  
  <p>
    What happens when an object gets a message that it doesn&#8217;t understand? Ruby will invoke the <code>:method_missing</code> message on that object. That handler is defined in Object, but you can override it in your own classes. Custom method_missing handlers can lead to very dynamic code that self adjusts to runtime conditions.
  </p>
  
  <h3 id="summary">
    Summary
  </h3>
  
  <p>
    The message-object protocol is fundamental to the way Ruby works. Messages are sent to objects to perform some task. Within the object, a message handler responds to the message and executes some code. Code blocks or procs can be created and executed at any time. A method is an enhancement of a proc that is bound to an object and named for the message it handles. Examining this interaction between Ruby objects at the message and block level leads to a deeper understanding of the way Ruby works and should help you write more expressive code.
  </p>
  
  <p>
    I urge you to explore the Proc, Module and Method class documentation and experiment with creating your own blocks.
  </p>
  
  <div class="footnotes">
    <ol>
      <li id="fn:1">
        <p>
          As we will see when we discuss the &#8216;yield&#8217; operator, inline blocks passed implicitly in a message call, is not really an instance of Proc. This is presumably a performance optimization.<a href="#fnref:1" rev="footnote">&#8617;</a>
        </p>
      </li>
      
      <li id="fn:2">
        <p>
          There is also a subtle difference between the <code>proc</code> and <code>lambda</code> declarations. A lambda will throw an ArgumentError if the number of supplied arguments to :call do not match the number of required arguments, whereas proc will just set these to nil, or just drop any extra ones. Inline blocks behave more like procs than lambdas.<a href="#fnref:2" rev="footnote">&#8617;</a>
        </p>
      </li>
    </ol>
  </div>
  
  <p>
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
  
  <p>
    <strong><em>Do also read</em> these awesome Guest Posts:</strong>
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/blog/2010/11/02/how-does-one-use-design-patterns-in-ruby/">How Does One Use Design Patterns In Ruby?</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/26/do-you-know-whats-new-in-ruby-1-9/">Do you know what’s new in Ruby 1.9?</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/25/the-value-of-a-personal-bug-log/">The value of a personal bug log</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/18/do-you-enjoy-your-code-quality/">Do You Enjoy Your Code Quality?</a>
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby+Objects" rel="tag">Ruby Objects</a>, <a href="http://technorati.com/tag/Ruby+Messages" rel="tag"> Ruby Messages</a>, <a href="http://technorati.com/tag/Ruby+Blocks" rel="tag">Ruby Blocks</a>, <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>
