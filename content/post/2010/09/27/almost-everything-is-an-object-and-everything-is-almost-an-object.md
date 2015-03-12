---
author: David Black
categories:
- Beginners
- Ruby
- Ruby Masters
date: 2010-09-27
layout: post
permalink: /2010/09/27/almost-everything-is-an-object-and-everything-is-almost-an-object/
tags:
- David A. Black
- programming
- Ruby
- ruby beginner
- Ruby for Noobs
thesis_description:
- David A. Black explains to Ruby Noobs why almost everything in Ruby is an object.
  A guest blog post on RubyLearning.
thesis_keywords:
- Ruby, Programming, David A. Black, Ruby beginner, Ruby for Noobs
title: Almost everything is an object (and everything is almost an object!)
topsy_short_url:
- http://bit.ly/cpn3BG
---

<div>
  <h3>
    Almost everything is an object
  </h3>
  
  <h4>
    (and everything is almost an object!)
  </h4>
  
  <p class="update">
    This guest post is contributed by <b>David A. Black</b>, a Senior Developer with <a href="http://www.cyrusinnovation.com">Cyrus Innovation, Inc.</a> David has been programming in Ruby for ten years, and is the author of <a href="http://www.manning.com/black2">The Well-Grounded Rubyist</a> (Manning, 2009). He&#8217;s one of the founding directors of <a href="http://www.rubycentral.org">Ruby Central, Inc.</a>, the parent organization of the <a href="http://www.rubyconf.org">International Ruby Conference</a> (RubyConf). David is also one of the most experienced Ruby and Rails trainers in the the business. One of his current projects is <a href="http://www.compleatrubyist.com">The Compleat Rubyist</a>, a training event taught by David, Gregory Brown, and Jeremy McAnally. David is a frequent invited speaker and keynoter at Ruby and Rails conferences, as well as users groups, in the U.S. and abroad.
  </p>
  
  <p class="block">
    <img class="alignright" height="125" width="125" src="http://www.rubylearning.com/images/dblack.jpg" title="David A. Black" alt="David A. Black" /> <span class="drop_cap">Y</span>ou&#8217;ll sometimes hear the statement that <em>Everything is an object in Ruby.</em> But is that true?
  </p>
  
  <p>
    It&#8217;s almost true, but not quite. No, this doesn&#8217;t mean we&#8217;ve caught Ruby doing something wrong! It&#8217;s just an opportunity to look more closely at how objects operate.
  </p>
  
  <p>
    Here&#8217;s an example of something that isn&#8217;t an object: an argument list. Consider a method call like this:
  </p>
  
  <pre>
create_person("David", "Black", "New Jersey")
</pre>
  
  <p>
    Three strings are serving as method arguments, and those strings are objects. But the argument list <em>itself</em> is not an object. There&#8217;s no ArgumentList class. Moreover, it would be hard to imagine one. Consider this code:
  </p>
  
  <pre>
arglist = ArgumentList.new  # no such thing; a thought experiment!
arglist &lt;&lt; "David"
arglist &lt;&lt; "Black"
arglist &lt;&lt; "New Jersey"
</pre>
  
  <p>
    Already there&#8217;s a problem. The <code>&lt;&lt;</code> &#8220;operator&#8221; is actually a method. That means that the code we&#8217;ve got is equivalent to this:
  </p>
  
  <pre>
arglist = ArgumentList.new
arglist.&lt;&lt;("David")
# etc.
</pre>
  
  <p>
    So in order to use an ArgumentList object, we need to be able to construct&#8230; an argument list.
  </p>
  
  <p>
    The way out of this circularity is to include something in the language that isn&#8217;t an object. Argument lists are part of the syntax of the language. They&#8217;re not objects.
  </p>
  
  <p>
    In addition to syntactic constructs like argument lists, Ruby also includes non-objects in the form of keywords like <code>if</code>, <code>class</code>, <code>alias</code>, and <code>begin</code>, <code>end</code>, <code>rescue</code>. Some of these keywords provide control flow techniques; some, like <code>alias</code>, let you conduct business with the interpreter that affects the world in which your objects live. Non-object keywords help to create the framework inside of which your objects can come into being and do everything they have to do.
  </p>
  
  <p>
    So not everything is Ruby is an object, and for good reason. But there&#8217;s a corollary to this point, and an important one: even though not everything is an object, <em>everything does evaluate to an object</em>.
  </p>
  
  <hr />
  
  <p>
    New to Ruby? Join our online Core Ruby course. Read details <a href="http://rubylearning.com/blog/2010/09/06/new-course-ruby-programming-101/">here</a>.
  </p>
  
  <hr />
  
  <h3>
    Everything (really, everything!) evaluates to an object
  </h3>
  
  <p>
    Every Ruby statement or expression evaluates to a single object. This is true not only of variables, object literals, and method calls, but of control-flow structures, keyword-based statements, class and method definitions, and everything else. The object a statement evaluates to may be <code>nil</code>, but it will always be something. Understanding this principle can help you make sense of things that happen in your code, and also provides some techniques you can take advantage of.
  </p>
  
  <p>
    You can get lots of information about how statements evaluate to objects by using irb. irb is very literal-minded, and will always print out the value of the statement you type in. Sometimes the value is obvious; sometimes what irb shows you is instructive. Let&#8217;s start with an irb classic: <code>puts</code>.
  </p>
  
  <pre>
>> puts "Hi"
Hi
=> nil
</pre>
  
  <p>
    Note the <code>nil</code> at the end: that&#8217;s the return value from <code>puts</code>. After all, <code>puts</code> is a method, so it has to return something. As it happens, it always returns <code>nil</code>. The printing out of the string is a side-effect.
  </p>
  
  <p>
    Knowing that <code>puts</code> returns <code>nil</code> will help you predict the result of evaluating this code:
  </p>
  
  <pre>
["one", "two", "three"].map {|n| puts n.upcase }
</pre>
  
  <p>
    It&#8217;s a common learner mistake to expect the result to be <code>["ONE", "TWO", "THREE"]</code>. In fact, it&#8217;s <code>[nil, nil, nil]</code>. Each time through the block, the block evaluates to the return value of <code>puts</code>&mdash;namely, <code>nil</code>.
  </p>
  
  <p>
    If every statement reduces to a single object, then the principle must apply to things you probably don&#8217;t usually think of in this way, such as class definitions. Sure enough:
  </p>
  
  <pre>
>> class MyClass; end
=> nil
</pre>
  
  <p>
    An empty class definition body evaluates to <code>nil</code>. A non-empty class definition body evaluates to the last expression evaluated inside it:
  </p>
  
  <pre>
>> class AnotherClass
>>   2 + 3
>> end
=> 5
</pre>
  
  <p>
    You can, if you want to, assign this value to a variable:
  </p>
  
  <pre>
>> x = class C; "Hi!"; end
=> "Hi!"
>> puts x
Hi!
=> nil
</pre>
  
  <p>
    It&#8217;s kind of silly to do that, usually. But there&#8217;s one very common idiom that uses this technique. Remember that inside a class body, <code>self</code> is the class object itself:
  </p>
  
  <pre>
>> class Thing
>>   self
>> end
=> Thing
</pre>
  
  <p>
    You&#8217;ll often see this fact used for the purpose of grabbing hold, in a variable, of an object&#8217;s singleton class:
  </p>
  
  <pre>
>> t = Thing.new
=> #&lt;Thing:0x18cf18>
>> singleton_class_of_t = class &lt;&lt; t; self; end
=> #&lt;Class:#&lt;Thing:0x18cf18>>
</pre>
  
  <p>
    We go into the singleton class using the <code>class &lt;&lt; t</code> construct, evaluate <code>self</code>, and exit the class body. The result of this fishing expedition is that we&#8217;ve landed the singleton class itself and saved it to a variable. Now it&#8217;s possible to do things with the class that you can&#8217;t do as long as it remains anonymous, such as calling <code>class_eval</code> on it.
  </p>
  
  <p>
    (Note that in Ruby 1.9.2 there&#8217;s a singleton_class method, so the above technique is probably going to start disappearing as more people move to 1.9.2 and higher versions.)
  </p>
  
  <p>
    Most class bodies evaluate to <code>nil</code> because, typically, class definitions end with a method definition&mdash;and method definitions always evaluate to <code>nil</code>:
  </p>
  
  <pre>
>> def my_method
>>   "Doesn't matter what I put here"
>> end
=> nil
</pre>
  
  <p>
    Of course, when you call the method it returns a string:
  </p>
  
  <pre>
>> my_method
=> "Doesn't matter what I put here"
</pre>
  
  <p>
    But the method definition <em>itself</em> evaluates to <code>nil</code>.
  </p>
  
  <p>
    Conditionals, including if statements and case statements, also always evaluate to an object. This isn&#8217;t exactly an obscure point; after all, the ultimate value of a conditional is often put to use.
  </p>
  
  <pre>
>> action = "stop"
=> "stop"
>> message = if action == "stop" then "Bye!" else "Continue!" end
=> "Bye!"
</pre>
  
  <p>
    There&#8217;s an interesting general rule, though: If no condition is true, or no case matched, then an if statement or case statement always evaluates to nil.
  </p>
  
  <pre>
>> if 3 &gt; 5
>>   "Universe is in trouble!"
>> end
=> nil

>> case 1 + 1
>> when 3
>>   "My world is upside-down!"
>> end
=> nil
</pre>
  
  <p>
    One place you&#8217;ll see this put to use is in templating situations where someone wants to include something conditionally. Consider this erb fragment:
  </p>
  
  <pre>
&lt;%= "#{first} #{"#{middle} " if middle}#{last}" %&gt;
</pre>
  
  <p>
    The expression <code>"#{middle }" if middle</code> will evaluate to <code>nil</code> if <code>middle</code> is <code>nil</code>. Interpolating <code>nil</code> into a string is the same as interpolating an empty string, so that whole part of the larger string will simply be an empty string. If <code>middle</code> isn&#8217;t <code>nil</code>, then <code>middle</code> plus a space will be interpolated into the larger string. Mind you, if you actually use this technique, people might accuse you of having overly clever or &#8220;cute&#8221; code&mdash;and they may be right! But even if you don&#8217;t use it in real code, it&#8217;s an instructive example.
  </p>
  
  <p>
    So even though not everything is an object in Ruby, an object is never very far away. Every statement eventually reduces to a single object. You might say that almost everything is an object&mdash;and everything is almost an object. Much of the time, the objects produced by control flow statements, class and method definitions, and keyword statements are ignored. But when you want or need them, they&#8217;re available. And exploring what statements evaluate to can teach you a lot about what Ruby is &#8220;thinking&#8221;.
  </p>
  
  <p class="alert">
    <strong><em>Post supported by <a href="http://zencoder.com/">Zencoder Inc.</a></em>:</strong> Zencoder does <a href="http://zencoder.com/">video encoding</a>, as a service, in the cloud. Hook up to their API, and within minutes, you&#8217;ll be ready to process video, whether it&#8217;s 10,000 videos or just 10. Zencoder is highly optimized for speed, uses the best compression technology around, and handles hundreds of video/audio formats (including obscure and corrupt files). Also check out their open-source <a href="http://videojs.com/">HTML5 video player</a> &#8211; <a href="http://videojs.com/">VideoJS</a>.
  </p>
  
  <p>
    <b><em>Do read</em> these awesome Guest Posts:</b>
  </p>
  
  <ul>
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

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Programming" rel="tag"> Programming</a>, <a href="http://technorati.com/tag/David+A.+Black" rel="tag"> David A. Black</a>, <a href="http://technorati.com/tag/Ruby+beginner" rel="tag"> Ruby beginner</a>, <a href="http://technorati.com/tag/Ruby+for+Noobs" rel="tag"> Ruby for Noobs</a>
