---
author: Satish Talim
categories:
- Beginners
- Interview
- Ruby
date: 2008-07-29
layout: post
permalink: /2008/07/29/david-flanagan-talks-to-rubylearning/
tags:
- book
- David Flanagan
- O'Reilly
- Ruby
- The Ruby Programming Language
title: David Flanagan talks to RubyLearning
---

<div>
  <p class="note">
    <strong>O&#8217;Reilly Media, Inc.</strong> is a strong supporter of <strong><a href="http://rubylearning.org/">RubyLearning.org</a></strong> and recently announced a 50% discount, for the participants of the <a href="http://rubylearning.org/">FORPC101</a> course, on their book &#8220;<a href="http://oreilly.com/catalog/9780596516178/">The Ruby Programming Language</a>&#8221; by David Flanagan, Yukihiro Matsumoto. Satish Talim of RubyLearning recently caught up with <strong><span style="color:blue;">David Flanagan</span></strong> who was kind enough to spare time answering questions posed by RubyLearning.
  </p>
  
  <p>
    <strong><span style="color:blue;">Satish Talim>></span></strong> David, a warm welcome to you. For the benefit of the readers, could you tell us something about your self?
  </p>
  
  <p>
    <strong><span style="color:blue;">David Flanagan>></span></strong> Hmm. Although I spend most of my time these days writing about programming, my training and my original career was as a programmer. I studied at MIT, and after graduation continued to work there, writing client-side applications for the X Window System (which was new at the time) and the Motif GUI toolkit. This was in C. HTTP hadn&#8217;t been invented yet, so we all had to make do with FTP. The internet wasn&#8217;t particularly new, but there were still more .edu sites than .com sites.
  </p>
  
  <p>
    I broke into the writing business in the early 1990&#8217;s when O&#8217;Reilly hired me to write a book as part of their series on the X Window System.
  </p>
  
  <p>
    <strong><span style="color:blue;">Satish Talim>></span></strong> David, you are one of O&#8217;Reilly&#8217;s most prolific authors, specializing in Java and JavaScript. How did you discover Ruby?
  </p>
  
  <p>
    <strong><span style="color:blue;">David Flanagan>></span></strong> I first heard about Ruby the same way most people did: because of all the excitement about Rails. I didn&#8217;t pay much attention at the time, however, and didn&#8217;t really investigate the language.
  </p>
  
  <p>
    Because of my success at documenting Java and JavaScript, my editor at O&#8217;Reilly thought I&#8217;d be a good person to write a book about Ruby.
  </p>
  
  <p>
    <strong><span style="color:blue;">Satish Talim>></span></strong> How is your book different than Pickaxe?
  </p>
  
  <p>
    <strong><span style="color:blue;">David Flanagan>></span></strong> My book is really focused on the core language and documents it in detail. The Pickaxe covers the language in less detail, but also covers the libraries and tools that surround the language.
  </p>
  
  <p>
    My book has an extended tutorial that introduces the core classes and their API, but does not have a reference section like the Pickaxe.
  </p>
  
  <p>
    You can learn Ruby from the Pickaxe, but I don&#8217;t think you can master it with that book alone. <em>My book was written to be a definitive book on the language, and is intended for those who want to learn and master the language</em>.
  </p>
  
  <p>
    <strong><span style="color:blue;">Satish Talim>></span></strong> What role does Ruby play in your day to day work?
  </p>
  
  <p>
    <strong><span style="color:blue;">David Flanagan>></span></strong> Surprisingly little, actually. Right now I&#8217;m writing some documentation for freebase.com, and that has involved some Python programming, but not Ruby. Ruby has become my scripting language of choice when I need to write a utility program of some sort. (Usually to process my documentation text files in some way.)
  </p>
  
  <p>
    <strong><span style="color:blue;">Satish Talim>></span></strong> What did you learn from writing &#8220;The Ruby Programming Language&#8221;?
  </p>
  
  <p>
    <strong><span style="color:blue;">David Flanagan>></span></strong> After being exposed to Ruby&#8217;s blocks, I came to really appreciate the power of tightly integrating closures with language syntax. The debate about adding closures to Java got underway while I was working on my Ruby book, and it is my experience with Ruby that makes me a proponent of the BGGA proposal.
  </p>
  
  <p>
    <strong><span style="color:blue;">Satish Talim>></span></strong> For a Ruby newbie what&#8217;s the most important thing he/she should focus on, in Ruby 1.9?
  </p>
  
  <p>
    <strong><span style="color:blue;">David Flanagan>></span></strong> <strong>Unicode support</strong> is the largest change, and will be the most important for anyone who works with anything other than ASCII. For the rest, the <strong>performance improvements in 1.9</strong> will probably be the most important thing about 1.9.
  </p>
  
  <p>
    I feel that most of the other new features of Ruby 1.9 are just conveniences. For example, I really like the new hash syntax that allows me to write {a:1} instead of {:a => 1}.
  </p>
  
  <p>
    The fact that iterator methods return Enumerators when invoked with no block is somewhat confusing but very powerful and introduces a new way of thinking about iterations. Here is an example: a program that prints itself, with line numbers:
  </p>
  
  <pre><code>File.open(__FILE__) do |f|
  f.each_line.with_index { |line, number|
    print "#{number+1}: #{line}"
  }
end</code></pre>
  
  <p>
    <strong><span style="color:blue;">Satish Talim>></span></strong> Any words of advice for a Ruby newbie?
  </p>
  
  <p>
    <strong><span style="color:blue;">David Flanagan>></span></strong> Ruby is a different language than any that you already know, and it can take some time to get the feel of it. Like any language, it has some quirks that you may not care for. But once you get past those, the language really grows on you.
  </p>
  
  <p>
    Learn Ruby for Ruby&#8217;s sake, and try to master the language. Don&#8217;t just learn enough Ruby to be able to write Rails programs. If you do that you&#8217;re in danger of doing cut-and-paste programming without really understanding what you&#8217;re doing.
  </p>
  
  <p>
    <strong><span style="color:blue;">Satish Talim>></span></strong> What&#8217;s next for you?
  </p>
  
  <p>
    <strong><span style="color:blue;">David Flanagan>></span></strong> I&#8217;m monitoring the development of Javascript 2 (aka ECMAScript 4) and will document it when it is ready. That looks like a very exciting new language.
  </p>
  
  <p>
    <strong><span style="color:blue;">Satish Talim>></span></strong> Thanks David for sharing your views with the RubyLearning participants.
  </p>
  
  <p class="note">
    <em><strong>Note</strong>: This interview is one of my ways of saying thank you to O&#8217;Reilly and not directly influenced or specified by the sponsors.</em>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/David+Flanagan" rel="tag">David Flanagan</a>, <a href="http://technorati.com/tag/Interviews" rel="tag"> Interviews</a>, <a href="http://technorati.com/tag/O%26%238217%3BReilly" rel="tag"> O&#8217;Reilly</a>, <a href="http://technorati.com/tag/Ruby" rel="tag"> Ruby</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag"> The Ruby Programming Language</a>
