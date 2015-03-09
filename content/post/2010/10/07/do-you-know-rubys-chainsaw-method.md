---
title: Do YOU know Ruby's "Chainsaw" method?
author: Paolo Perrotta
date: 2010-10-07
layout: post
permalink: /2010/10/07/do-you-know-rubys-chainsaw-method/
thesis_description:
  - "Paolo Perrotta loves Ruby's 'Chainsaw' method - method_missing(). Paolo shows you why, in this guest blog post on RubyLearning."
thesis_keywords:
  - Ruby, Programming, Paolo Perrotta, Ruby for Noobs, Ruby beginners, method_missing
topsy_short_url:
  - http://bit.ly/ceoL1Z
categories:
  - beginners
  - popular
  - ruby
  - ruby masters
tags:
  - method_missing
  - paolo perrotta
  - programming
  - ruby
  - ruby beginners
  - ruby for noobs
---
<div>
  <h3>
    Do YOU know Ruby&#8217;s &#8216;Chainsaw&#8217; method?
  </h3>
  
  <p class="update">
    This guest post is contributed by <strong><a href="http://rubylearning.com/blog/2009/07/01/interview-author-paolo-perrotta/">Paolo Perrotta</a></strong>, a freelance geek, currently coaching agile teams for a large phone company. He also wrote the <a href="http://www.pragprog.com/titles/ppmetr/metaprogramming-ruby">Metaprogramming Ruby book</a> for the Prags. He lives in Northern Italy with his girlfriend and a cat. He loves Ruby.
  </p>
  
  <p>
    <span class="drop_cap">T</span>he <code>method_missing()</code> method is a wonderful tool for every Ruby programmer. I love it. There, I said it!
  </p>
</div>

<div style="width:image 560 px; font-size:80%; text-align:center;">
  <img src="http://rubylearning.com/images/method_missing.jpg" alt="method_missing" width="560" style="padding-bottom:0.5em;" /><br />method_missing()
</div>

<div>
  <p>
    Some Rubyists <a href="http://jakescruggs.blogspot.com/2010/08/ruby-kaigi-2010-day-2.html">are surprised</a> when I declare my love for <code>method_missing()</code>. They do have a point. As far as tools go, <code>method_missing()</code> is a chainsaw: it&#8217;s powerful, but it&#8217;s also potentially dangerous.
  </p>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/PaoloPerrotta.jpg" alt="Paolo Perrotta" width="125" height="125" title="Paolo Perrotta" /> In case you don&#8217;t know about <code>method_missing()</code>, here is how it works. Imagine that you&#8217;re calling a method on a Ruby object. For example, you call <code>duck.sing("Quacking in the Rain")</code>. Usually, at this point one of two things happens: if <code>duck</code> has a <code>sing()</code> method that takes one argument, then Ruby executes the method; if <code>duck</code> doesn&#8217;t have that method, then Ruby raises an error. But wait: there is a third possibility. If <code>duck</code>doesn&#8217;t have a method named <code>sing()</code>, but it does have a method named <code>method_missing()</code>, then Ruby executes <code>method_missing()</code> instead. Ruby also tells to <code>method_missing()</code> which method you originally called, with arguments and all. Here is an example:
  </p>
  
  <p>
  </p>
  
  <p>
    You can say that <code>duck.sing()</code> and <code>duck.dance()</code> are <a href="http://gist.github.com/534776">Ghost Methods</a>: they aren&#8217;t defined anywhere, but you can call them anyway.
  </p>
  
  <p>
    That&#8217;s what <code>method_missing() </code>does. The difficult part is deciding when and how to use it. Let&#8217;s see an example of Ghost Methods in action.
  </p>
  
  <p>
    Imagine that you have an <code>InformationDesk</code> object with many complex methods that provide some kind of tourist information or service:
  </p>
  
  <p>
  </p>
  
  <p>
    To give a break to people working at the <code>InformationDesk</code>, you can wrap the <code>InformationDesk</code> in a <code>DoNotDisturb</code> object:
  </p>
  
  <p>
  </p>
  
  <p>
    <code>DoNotDisturb</code> forwards method calls to the wrapped <code>InformationDesk</code>, unless it&#8217;s lunchtime. During lunch breaks, <code>DoNotDisturb</code> responds to calls by raising an exception &#8211; unless you&#8217;re calling <code>emergency()</code>, that works at any hour. (If you think that two hours are too much for a lunch, then you&#8217;ve probably never lived in Italy!)
  </p>
  
  <p>
    The problem with the above code is that <code>DoNotDisturb</code> contains a lot of look-alike methods. This is a form of duplication, and duplication sucks. If a programmer adds methods to <code>InformationDesk</code>, she also needs to remember to add matching methods to <code>DoNotDisturb</code>, most likely by copy-pasting the existing look-alike methods and then modifying them. One misstep in this procedure, and you have a brand new bug.
  </p>
  
  <p>
    When I work with Java or C#, I accept this kind of code duplication as a fact of life. In Ruby, I can be more aggressive and replace all the calls with a single <code>method_missing()</code>:
  </p>
  
  <p>
  </p>
  
  <p>
    <code>DoNotDisturb</code> is now a <a href="http://gist.github.com/535077">Dynamic Proxy</a>: it forwards each method call to its inner <code>InformationDesk</code>, and it also wraps additional logic around each call. If you add methods to <code>InformationDesk</code>, you needn&#8217;t worry about <code>DoNotDisturb</code>: it will work for the new methods without any change.
  </p>
  
  <p>
    This kind of trickery is useful, but it does have a dark side. If you abuse <code>method_missing()</code>, you can end up with code that&#8217;s difficult to read and maintain. I&#8217;m still intimidated by some of <a href="http://github.com/rails/rails/blob/277c799d58be4b3e0e885d7b3fd6d954facc111b/activerecord/lib/active_record/base.rb">the wildest examples of <code>method_missing()</code></a> that abound the Ruby ecosystem. Even if you take care to keep your <code>method_missing()</code>small and maintainable, Ghost Methods are still inherently less explicit than regular methods. You can easily discover the regular methods in a class by looking at the auto-generated documentation, but you have to look at the source code (or the author&#8217;s documentation) to spot Ghost Methods.
  </p>
  
  <p>
    Also, if you&#8217;re not careful around <code>method_missing()</code>, sneaky bugs can creep into your code. For example, an overly tolerant <code>method_missing()</code> might accept a mistyped method call without flinching. Chainsaws are meant to be handled with care!
  </p>
  
  <p>
    So, what kind of tree should you use the<code> method_missing()</code> chainsaw on? Here are my simple rules of thumb:
  </p>
  
  <ol>
    <li>
      I <b>use <code>method_missing()</code>to remove duplication</b>. A well placed <code>method_missing()</code> allows me to remove duplicated code at a level that wouldn&#8217;t otherwise be possible.
    </li>
    <li>
      On the other hand, I usually <b>think twice about using <code>method_missing()</code> for cosmetic reasons</b>, like getting cool method names such as <code>find_by_name_and_address()</code>.
    </li>
    <li>
      I always try to <b>evaluate whether <code>method_missing()</code> is worth the extra reading effort</b>. I dislike duplicated code because it&#8217;s hard to read and modify. If I replace that code with a <code>method_missing()</code> that&#8217;s even harder to read and modify, then I&#8217;ve defeated <code>method_missing()</code>&#8216;s purpose.
    </li>
  </ol>
  
  <p>
    It&#8217;s a balancing act: with some experience you can strike the sweet spot between shortness and clarity in your Ruby code. To do that, you&#8217;ll likely use the <code>method_missing()</code> chainsaw to cut out unnecessary branches from your forest of methods.
  </p>
  
  <p>
    There are many more neat tricks, caveats and interesting details around <code>method_missing()</code>.&nbsp;In <a href="http://www.amazon.com/Metaprogramming-Ruby-Program-Like-Pros/dp/1934356476/ref=sr_1_1?ie=UTF8&s=books&qid=1284392039&sr=8-1">Metaprogramming Ruby</a>, I devoted most of the Methods chapter to it (you can check the first few pages from that chapter <a href="http://media.pragprog.com/titles/ppmetr/methods.pdf">here</a>). You can also find a lot of information on <code>method_missing()</code> on the Web, including some <a href="http://yehudakatz.com/2010/01/02/the-craziest-fing-bug-ive-ever-seen/">pretty crazy bug reports</a>. With this information, and some experience, you&#8217;ll be able to make up your own mind about the pros and cons of <code>method_missing()</code>.
  </p>
  
  <p>
    Me, I already made up my mind. Yes, I use <code>method_missing()</code> sparingly. Yes, I keep it as short as I can. Yeah, I triple-check it for bugs&#8230; But when the duplication begins to sting, I put on my evil grin and grab my faithful chainsaw.
  </p>
  
  <p>
    <em>Have <b>you</b> used <code>method_missing()</code> before? Why don&#8217;t you share your experiences with us? Let us know in the comments section of this post. Thanks!</em>
  </p>
  
  <p class="alert">
    <strong><em>Post supported by <a href="http://tupalo.com/">Tupalo.com</a></em>:</strong> Tupalo.com is a privately-held internet startup located in Vienna, Austria. Their social yellow-pages app is developed using Ruby on Rails and also uses many of the other exciting tools like Cucumber, RSpec, Capistrano and Puppet, Ruby developers came to appreciate.
  </p>
  
  <p>
    <b><em>Do read</em> these awesome Guest Posts:</b>
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/06/gem-sawyer-modern-day-ruby-warrior/">Gem Sawyer, Modern Day Ruby Warrior</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/05/outside-in-development/">An Introduction to Outside-in Development</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/04/ruby-forensics/">Ruby Forensics</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/01/an-introduction-to-eventmachine-and-how-to-avoid-callback-spaghetti/">An introduction to eventmachine, and how to avoid callback spaghetti</a>
    </li>
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

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Programming" rel="tag"> Programming</a>, <a href="http://technorati.com/tag/Paolo+Perrotta" rel="tag"> Paolo Perrotta</a>, <a href="http://technorati.com/tag/Ruby+for+Noobs" rel="tag"> Ruby for Noobs</a>, <a href="http://technorati.com/tag/Ruby+beginners" rel="tag"> Ruby beginners</a>, <a href="http://technorati.com/tag/method_missing" rel="tag"> method_missing</a>
