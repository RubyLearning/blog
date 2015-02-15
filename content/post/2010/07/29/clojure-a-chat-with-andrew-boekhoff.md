---
title: 'Clojure: A Chat with Andrew Boekhoff'
author: Satish Talim
date: 2010-07-29
layout: post
permalink: /2010/07/29/clojure-a-chat-with-andrew-boekhoff/
thesis_description:
  - A Chat with Andrew Boekhoff, author of CongoMongo, a toolkit for using MongoDB with Clojure.
thesis_keywords:
  - Andrew Boekhoff,Clojure,MongoDB,congomongo
topsy_short_url:
  - http://bit.ly/bh4v19
categories:
  - Clojure
  - Interview
tags:
  - Andrew Boekhoff
  - Clojure
  - congomongo
  - MongoDB
---
<div>
  <p class="alert">
    In this brief interview, Satish Talim of RubyLearning talks to <b>Andrew Boekhoff</b>, author of <a href="http://github.com/somnium/congomongo">CongoMongo</a>, a toolkit for using MongoDB with Clojure.
  </p>
  
  <p>
    <span style="color:#0000FF;"><strong>Satish>></strong> Welcome Andrew and thanks for taking out time to share your thoughts. What programming languages have you used seriously?</span>
  </p>
  
  <p>
    <strong>Andrew>></strong> Seriously: Ruby and Clojure. Less Seriously: C, C++, Java and now: Haskell, Scheme.
  </p>
  
  <p>
    <span style="color:#0000FF;"><strong>Satish>></strong> Why and when did you decide to start working on Clojure?</span>
  </p>
  
  <p>
    <strong>Andrew>></strong> I&#8217;ve been using Clojure for a little over a year. I had read Paul Graham&#8217;s essays, so I wanted to try a lisp dialect. I also wanted to learn what functional programming was all about. Then I watched Rich Hickey&#8217;s presentations on Clojure and by that point I was pretty much sold.
  </p>
  
  <p>
    <span style="color:#0000FF;"><strong>Satish>></strong> Could you name three features of Clojure that you like the most, as compared to other languages? Why?</span>
  </p>
  
  <p>
    <strong>Andrew>></strong>
  </p>
  
  <ol>
    <li>
      <b>Immutability</b>: Using immutable locals and data structures as the default eliminates a huge class of potential errors. I&#8217;ve never written as much code that worked on the first try in any other language. Concurrency is often mentioned as a great benefit from pervasive immutability &#8212; and it certainly is &#8212; but for me, the net reduction in complexity is what I love most.
    </li>
    <li>
      <b>It&#8217;s a Lisp: It has Macros</b>: Whether its for shearing off boiler plate, or embedding a parser for an internal DSL, the ability to easily extend the syntax of the language is a uniquely expressive trait of the lisp family.
    </li>
    <li>
      <b>The immense practicality of the JVM</b>: By being hosted on the JVM, Clojure comes with batteries-included and can be deployed anywhere that Java can (almost anywhere).
    </li>
  </ol>
  
  <p>
    <span style="color:#0000FF;"><strong>Satish>></strong> You have written a Clojure wrapper (congomongo) for the mongo-db java api. Can you tell us more about this wrapper? Also, why did you target MongoDB?</span>
  </p>
  
  <p>
    <strong>Andrew>></strong> I really like working with MongoDB. The combination of schema-less document storage and ad-hoc queries is fantastic. The JSON format fits Clojure&#8217;s data structures well, and the mongo-java-driver is high quality and maintained. Congomongo is fairly light-weight &#8212; its main goal is to make interacting with the database from Clojure convenient and idiomatic.
  </p>
  
  <p>
    <span style="color:#0000FF;"><em>Thank you Andrew. In case you have any queries and/or questions, kindly post your questions here (as comments to this blog post) and Andrew would be glad to answer.</em></span>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Andrew+Boekhoff" rel="tag">Andrew Boekhoff</a>, <a href="http://technorati.com/tag/Clojure" rel="tag">Clojure</a>, <a href="http://technorati.com/tag/MongoDB" rel="tag">MongoDB</a>, <a href="http://technorati.com/tag/congomongo" rel="tag">congomongo</a>
