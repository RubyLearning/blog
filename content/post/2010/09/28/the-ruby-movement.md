---
author: Matt Aimonetti
categories:
- Beginners
- Ruby
- Ruby Masters
date: 2010-09-28
layout: post
permalink: /2010/09/28/the-ruby-movement/
tags:
- Matt Aimonetti
- programming
- Ruby
- ruby beginner
- Ruby for Noobs
thesis_description:
- Matt Aimonetti writes about the "Ruby movement", a parallel between art movements
  and programming and what makes Ruby special. A guest blog post on RubyLearning.
thesis_keywords:
- Ruby, Programming, Matt Aimonetti, Ruby for Noobs, Ruby beginner
thesis_title:
- The Ruby movement by Matt Aimonetti
title: The Ruby movement
topsy_short_url:
- http://bit.ly/d4jOgR
---

<div>
  <p class="update">
    This guest post is contributed by <b><a rel='author' href="http://matt.aimonetti.net/">Matt Aimonetti</a></b>, a Senior Engineer at Sony Playstation in San Diego, CA. <a href="https://plus.google.com/101114877505962271216?author" rel="author">Matt</a> has been active in the Ruby community for many years, he developed or contributed to a lot OSS libraries and frameworks, spoke at users groups and conferences in the U.S. and abroad. Working with startups, fortune 100 companies and traditional companies, he had the opportunity to be involved with really captivating Ruby, MacRuby, noSQL/lessSQL, Rails and Merb projects. Matt is currently writing a <a href="http://macruby.labs.oreilly.com/">MacRuby book for O&#8217;Reilly</a>, available for free online.
  </p>
  
  <p class="block">
    <img class="alignright" height="125" width="125" src="http://rubylearning.com/images/m_aimonetti.jpg" alt="Matt Aimonetti" /> <span class="drop_cap">A</span>n art movement is a tendency or style in art with a specific common philosophy or goal, followed by a group of artists during a restricted period of time, or, at least, with the hay-day of the movement defined within usually a number of years.<sup class='footnote'><a href='#fn-4744-1' id='fnref-4744-1'>1</a></sup>
  </p>
  
  <p>
    The programming world is much closer to the art world than you might think. Painters, sculptors, architects, singers, writers, cinematographers and photographers are recognized as artists, while programmers/coders/hackers are not there yet. One could argue that programming is more of a craft than an art, but instead of getting into semantics, let&#8217;s look at &#8220;programming movements&#8221; the same way we look at &#8220;art movements&#8221;.
  </p>
  
  <p>
    Art is about expressing and generating feelings. Various styles and techniques can be used and when artists work on a piece, they do not target the entire world but often limit their focus. Authors often try to express something personal and communicate their own world view to their audience. Keeping that in mind, let&#8217;s see how this applies to the Ruby language and its creator: <img src="http://rubylearning.com/images/japanes.jpg" alt="Matt Aimonetti" />, Matsumoto Yukihiro aka Matz.
  </p>
</div>

<div style="width:image 218 px;font-size:80%;text-align:center">
  <img src="http://rubylearning.com/images/image4.jpg" alt="Matsumoto Yukihiro" width="218" style="padding-bottom:0.5em" /><br />Matsumoto Yukihiro
</div>

<div>
  <p>
    Any good designer/artist starts by learning from exemplars. In the dead cold of a late German autumn in 1705, an impoverished young musician named J.S. Bach took a 6 month, unpaid leave from his job and walked 250 miles to study the work and ideas of maestro: Dietrich Buxtehude. Now fast forward to 2010 and take a look at well known Japanese artist <a href="http://en.wikipedia.org/wiki/Takashi_Murakami">Takashi Murakami&#8217;s</a> creations.
  </p>
</div>

<div style="width:image 240 px;font-size:80%;text-align:center">
  <img src="http://rubylearning.com/images/image1.jpg" alt="Superflat creation for Louis Vuitton - Takashi Murakami, 2003" width="240" height="240" style="padding-bottom:0.5em" /><br />Superflat creation for Louis Vuitton &#8211; Takashi Murakami, 2003
</div>

<div>
  <p>
    You can see how masters like <a href="http://en.wikipedia.org/wiki/Henri_Matisse">Henri Matisse</a> and <a href="http://en.wikipedia.org/wiki/Andy_Warhol">Andy Warhol</a> have helped him create his own style.
  </p>
</div>

<div style="width:image 240 px;font-size:80%;text-align:center">
  <img src="http://rubylearning.com/images/image0.jpg" alt="La gerbe' Henri Matisse, 1953" width="240" height="240" style="padding-bottom:0.5em" /><br />La gerbe&#8217; Henri Matisse, 1953
</div>

<div>
  <p>
    Murakami&#8217;s Superflat creation for Louis Vuitton, clearly follows Warhol&#8217;s pop-art steps with a strong influence from previous artists like Matisse, Tezuka and others. <a href="http://www.youtube.com/watch?v=yqaXxSBZTZc&NR=1">Watch one of the video clips Murakami produced</a> for LV.
  </p>
  
  <p>
    The same thing goes for programming languages. When designing his programming language: Ruby, Matz was strongly influenced by Perl, Smalltalk, Python, Eiffel, Dylan, Lisp and many more languages. But at the same time he created his own programming language with its own design values, own desiderata/objectives and own priorities.
  </p>
  
  <p>
    Programming is not a religion. And neither are art movements. When you reflect on art movements, you might like <a href="http://en.wikipedia.org/wiki/Impressionism">impressionism</a> better than <a href="http://en.wikipedia.org/wiki/Expressionism">expressionism</a> but you know they are both art movements. When you study their contexts a bit more, you understand the motivations behind each movement better. Don&#8217;t believe even for a second that Ruby is a perfect language nor that it will be the last programming language you will need to learn. Programming languages, very much like art movements, are not set in stone, they evolve and spawn new movements. But regardless of what happens, if they grow to be important enough, programming movements influence new languages and keep on living through them.
  </p>
  
  <p>
    Alright, enough armchair philosophy. Let&#8217;s look at the Ruby movement values and the problems its designer was trying to address.
  </p>
  
  <p>
    In his OSCON 2003 presentation, Matz explained what his motivations in creating Ruby were. He started by stating that languages influence human thoughts much more than we think. And that the good programming languages should help developers:
  </p>
  
  <ul>
    <li>
      program better.
    </li>
    <li>
      think smarter.
    </li>
    <li>
      finish your job faster.
    </li>
  </ul>
  
  <p>
    He defined a few principles that he felt needed to be put in place to help program better/reduce stress in programming:
  </p>
  
  <ul>
    <li>
      Principle of least surprise (the developer should not be surprised by the way an API works).
    </li>
    <li>
      Principle of succinctness (shorter code is easier to write, read and maintain).
    </li>
    <li>
      Principle of human interface (the language should be written for the developer, not the machine).
    </li>
  </ul>
  
  <p>
    This, in a way, is the Ruby manifesto. It is not uncommon for art movements to define their rules, perspective and even publish manifestos. The <a href="http://en.wikipedia.org/wiki/Futurist_Manifesto">futurists</a>, <a href="http://en.wikipedia.org/wiki/Surrealist_Manifesto">surrealists</a> and <a href="http://en.wikipedia.org/wiki/Art_manifesto#Dada_Manifesto_1916">dadaists</a> for instance had their own manifestos while others like the <a href="http://en.wikipedia.org/wiki/Cubism">cubists</a> let <a href="http://en.wikipedia.org/wiki/Louis_Vauxcelles">art critics</a> explain their movements. In his presentation, Matz clearly defined the core values that he refers to when he is thinking about making a change somewhere. Each language has its own set of values and they are sometimes in opposition from one language to the other. It&#8217;s up to you, the developer, to see how these values fit your project and your team. Unfortunately, there is not (yet) a perfect language that everyone you can use for everything.
  </p>
  
  <p>
    If you are reading this article, you are probably already part of the Ruby movement or you are looking into it. The two first things you should probably remember are:
  </p>
  
  <ul>
    <li>
      to learn and understand Ruby’s values.
    </li>
    <li>
      to be curious about what other &#8220;movements&#8221; value and how they approach challenges.
    </li>
  </ul>
  
  <p>
    f you do that, you will first understand the pros and cons of the language, and you will understand why some aspects of the language can seem odd to you. (For more info, <a href="http://merbist.com/2010/08/22/discussion-with-a-java-switcher/">read the post I wrote</a> about the discussion I had with an ex-Java developer).
  </p>
  
  <p>
    Look at other engineering movements, not only programming languages:
  </p>
  
  <ul>
    <li>
      <a href="http://en.wikipedia.org/wiki/NoSQL">NoSQL movement</a> in comparison with other Data storing approaches like <a href="http://en.wikipedia.org/wiki/RDMS">RDMS</a>.
    </li>
    <li>
      Event driven architecture movement like <a href="http://twistedmatrix.com/trac/">Twisted</a> / <a href="http://wiki.github.com/eventmachine/eventmachine/">EventMachine</a> / <a href="http://nodejs.org/">node.js</a>.
    </li>
    <li>
      Functional programming movement with <a href="http://www.haskell.org/">Haskell</a>, <a href="http://clojure.org/">Clojure</a>, <a href="http://www.erlang.org/">Erlang</a>.
    </li>
    <li>
      Look at the Lisp movement (sub functional programming movement) with <a href="http://en.wikipedia.org/wiki/Scheme_(programming_language)">Scheme</a> / <a href="http://racket-lang.org/">Racket</a> / <a href="http://en.wikipedia.org/wiki/Common_Lisp">CommonLisp</a>.
    </li>
    <li>
      Look at the <a href="http://golang.org/">Go Programming Language</a>, and see what it does differently and why
    </li>
  </ul>
  
  <p>
    Look at how architects design buildings, how musicians compose music, how NASA designs rockets. By understanding the main design goal, the list of objectives and the scope of each approach, you will be able to understand, value and criticize each movement.
  </p>
  
  <p>
    Don&#8217;t limit yourself to using idioms and pushing keys on your keyboard without understanding the &#8220;why&#8221; behind the &#8220;how&#8221;. Ruby wants you to become a better programmer, that is part of the language&#8217;s objectives. Better Ruby developers mean a stronger influence on the Ruby movement and improvement brought by the community synergy. If you find something that is not right with Ruby or its community (I have my own list), you should try to understand why it is like that and ask yourself what you can do to help. Don&#8217;t think for a second that you are not smart or expert enough. Be passionate and get involved to improve yourself and the movement as a whole. Take for example artists learning from outside their paradigms. Picasso and Matisse were friendly rivals, they shared the same interest in primitivism and <a href="http://en.wikipedia.org/wiki/African_art">African art</a> and influenced each other while being part of different movements. Directors like <a href="http://en.wikipedia.org/wiki/Quentin_Tarantino">Quentin Tarantino</a>, <a href="http://en.wikipedia.org/wiki/Martin_Scorsese">Martin Scorsese</a>, <a href="http://en.wikipedia.org/wiki/John_Woo">John Woo</a>, <a href="http://en.wikipedia.org/wiki/Steven_Soderbergh">Steven Soderbergh</a>, <a href="http://en.wikipedia.org/wiki/Brian_De_Palma">Brian De Palma</a>, <a href="http://en.wikipedia.org/wiki/Wim_Wenders">Wim Wenders</a>, <a href="http://en.wikipedia.org/wiki/Oliver_Stone">Oliver Stone</a> all have different styles but all admit to have been directly influenced by <a href="http://www.imdb.com/name/nm0000419/">Jean-Luc Godard</a> and the <em>Nouvelle</em> Vague movement. Most modern music movements love to borrow from each other to create interesting new trends.
  </p>
  
  <p>
    So when you work on your code, when you are looking at other programming language, think about art and remember that a movement always benefits from borrowing ideas from other movements. Don&#8217;t forget that one&#8217;s own little programming world is transient, metamorphic and therefore should remain fun, challenging and welcoming. Educate yourself, stay open minded and help take the Ruby movement to the next level.
  </p>
  
  <h4>
    Recommended reading (not Ruby specific):
  </h4>
  
  <p>
    <img src="http://rubylearning.com/images/image2.jpg" alt="The Design of Design" /> <a href="http://www.amazon.com/Design-Essays-Computer-Scientist/dp/0201362988">The Design of Design</a>
  </p>
  
  <p>
    <img src="http://rubylearning.com/images/image5.jpg" alt="Hackers & Painters" /> <a href="http://www.amazon.com/dp/1449389554?tag=merbist-20&camp=213381&creative=390973&linkCode=as4&creativeASIN=1449389554&adid=1DHD48KWCSEWD48FX7DM">Hackers & Painters</a>
  </p>
  
  <p>
    <img src="http://rubylearning.com/images/image3.jpg" alt="The Pragmatic Programmer" /> <a href="http://www.amazon.com/dp/020161622X?tag=merbist-20&camp=213381&creative=390973&linkCode=as4&creativeASIN=020161622X&adid=1X9WP08X4ADG7QZVSA60">The Pragmatic Programmer: From Journeyman to Master</a>
  </p>
  
  <p>
    <img src="http://rubylearning.com/images/image6.jpg" alt="The Passionate Programmer" /> <a href="http://www.amazon.com/dp/1934356344?tag=merbist-20&camp=213381&creative=390973&linkCode=as4&creativeASIN=1934356344&adid=0MM3E66D9GAYJDEFFT7F">The Passionate Programmer</a>
  </p>
  
  <p>
    <em>So &#8211; what do you think? If <b>you</b> have ideas, sites, resources, etc. that I haven&#8217;t mentioned, please post them as comments here.</em>
  </p>
  
  <p class="alert">
    <strong><em>Post supported by Sticker Mule</em>:</strong> <a href="http://www.stickermule.com/t/categories/custom-stickers">Sticker Mule</a> prints custom stickers starting at $69 for 100. They aspire to be every Ruby developer&#8217;s favorite sticker printing service. A $25 off coupon (RL01) is available for Ruby Learning readers through October 31st, 2010. Enter code RL01 during checkout.
  </p>
  
  <p>
    <b><em>Do read</em> these awesome Guest Posts:</b>
  </p>
  
  <ul>
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

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Programming" rel="tag"> Programming</a>, <a href="http://technorati.com/tag/Matt+Aimonetti" rel="tag"> Matt Aimonetti</a>

<div class='footnotes'>
  <div class='footnotedivider'>
  </div>
  
  <ol>
    <li id='fn-4744-1'>
      <a href="http://en.wikipedia.org/wiki/Art_movement">http://en.wikipedia.org/wiki/Art_movement</a>. <span class='footnotereverse'><a href='#fnref-4744-1'>&#8617;</a></span>
    </li>
  </ol>
</div>
