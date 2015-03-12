---
author: Elise Huard
categories:
- Beginners
- Ruby
- Ruby Masters
date: 2010-10-04
layout: post
permalink: /2010/10/04/ruby-forensics/
tags:
- Elise Huard
- programming
- Ruby
- Ruby Beginners
- Ruby for Noobs
- Ruby Forensics
thesis_description:
- Elise Huard introduces us to introspection - Ruby's capability to determine the
  type of an object at runtime. A guest blog post on RubyLearning.
thesis_keywords:
- Ruby, Programming, Elise Huard, Ruby for Noobs, Ruby beginners, Ruby Forensics
title: Ruby Forensics
topsy_short_url:
- http://bit.ly/b9Ohlv
---

<div>
  <h3>
    Ruby Forensics
  </h3>
  
  <p class="update">
    This guest post is contributed by <strong><a href="http://twitter.com/elise_huard">Elise Huard</a></strong>, who is based in Brussels, Belgium and is the owner of <a href="http://jabberwocky.eu/">Jabberwocky</a>, a solutions company mostly focused on Rails. She has worked with a few other technologies before falling in love with Rails and Ruby about 3 years ago and going freelance to work with Ruby full time. She contributes to open source projects as much as she can, and has given talks at a few Ruby and Rails conferences. She’s a jack of all trades, loves reading, tinkering, food, travel, learning, and people out of the ordinary.
  </p>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/pic1-125.jpg" alt="Elise Huard" width="125" height="125" /> <span class="drop_cap">S</span>ay you want to use a library, but no or very little documentation is available, and you don&#8217;t feel like diving into the code right away.
  </p>
  
  <p>
    Well, you picked the right language. Ruby is blessed with what is called <a href="http://en.wikipedia.org/wiki/Type_introspection">introspection</a>: if you ask a Ruby program/class/module politely, it will tell you almost anything about itself. This post will tell you some tricks I use on a daily basis.
  </p>
  
  <pre>module Layer
  FILLINGS = [:chocolate, :meringue, :jam, :cream, :strawberry]
  def fill(filling)
    puts "fill with #{filling}"
  end
end

class Cake
  include Layer

  attr_accessor :calories

  def ice
    @calories = @calories + 200
  end

  def eat
    puts "nom"
  end

  def self.bake
    return new
  end
end

class CheeseCake &lt; Cake; end</pre>
  
  <p>
    Say you have a class, but you&#8217;d like to know what method it defines.
  </p>
  
  <pre>Cake.public_instance_methods</pre>
  
  <p>
    Won&#8217;t be that useful, because Ruby objects (with some exceptions like <code>BasicObject</code>) have got a whole lot of methods out of the box. Rather, use:
  </p>
  
  <pre>Cake.public_instance_methods - Object.public_instance_methods
=&gt; [:calories, :calories=, :ice, :eat, :fill]</pre>
  
  <p>
    If you want one particular method, and you have an idea of which name it should have:
  </p>
  
  <pre>(Cake.public_instance_methods - Object.public_instance_methods).grep(/eat/)</pre>
  
  <p>
    Will show if your instinct was right or not.
  </p>
  
  <p>
    The same can be done for class methods, of course:
  </p>
  
  <pre>(Cake.methods - Object.methods)
=&gt; [:bake]</pre>
  
  <p>
    (<code>public_class_methods</code> also works.)
  </p>
  
  <p>
    <em>Note:</em> this won&#8217;t show you the dynamic methods, like find_by_X for ActiveRecord. The class doesn&#8217;t know it has these kind of methods in itself. They&#8217;re executed on the fly when the program hits <code>method_missing</code>. You&#8217;d have to look at the classes&#8217; <code>method_missing</code> method to find out.
  </p>
  
  <p>
    Then there&#8217;s the case where you&#8217;d like to know, exactly, where a method was defined. Ruby gives us the &#8216;<code>method</code>&#8216; method, which takes a symbol as an argument.
  </p>
  
  <pre>Cake.new.method(:fill)
 =&gt; #&lt;Method: Cake(Layer)#fill&gt;</pre>
  
  <p>
    Which tells us it was defined in the Layer module, included in the Cake class.
  </p>
  
  <pre>Cake.new.method(:eat)
 =&gt; #&lt;Method: Cake#eat&gt;</pre>
  
  <p>
    Sometimes, you want to know which other classes your class was descended from &#8211; including mixed in modules. The <code>ancestors</code> method will show you:
  </p>
  
  <pre>CheeseCake.ancestors
 =&gt; [CheeseCake, Cake, Layer, Object, Kernel, BasicObject]</pre>
  
  <p>
    Should you want to know about any constants, there&#8217;s a method for that too:
  </p>
  
  <pre>Cake.constants
 =&gt; [:FILLINGS]</pre>
  
  <p>
    All these methods have a good chance of giving you the information you want. When used in irb, together with a little experimentation, they can really help you find the code you&#8217;re looking for.
  </p>
  
  <p>
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
  
  <p>
    <b><em>Do read</em> these awesome Guest Posts:</b>
  </p>
  
  <ul>
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

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Programming" rel="tag"> Programming</a>, <a href="http://technorati.com/tag/Elise+Huard" rel="tag"> Elise Huard</a>, <a href="http://technorati.com/tag/Ruby+for+Noobs" rel="tag"> Ruby for Noobs</a>, <a href="http://technorati.com/tag/Ruby+beginners" rel="tag"> Ruby beginners</a>, <a href="http://technorati.com/tag/Ruby+Forensics" rel="tag"> Ruby Forensics</a>
