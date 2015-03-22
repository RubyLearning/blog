---
draft: false
title: 'Clojure: A Chat with Andrew Boekhoff'
date: 2010-07-29
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: https://www.facebook.com/satishtalim/about
categories:
- Clojure
- Interview
layout: post
permalink: /2010/07/29/clojure-a-chat-with-andrew-boekhoff/
tags:
- Andrew Boekhoff
- Clojure
- congomongo
- MongoDB
---
In this brief interview, Satish Talim of RubyLearning talks to **Andrew
Boekhoff**, author of
[CongoMongo](http://github.com/somnium/congomongo), a toolkit for using
MongoDB with Clojure.

**Satish\>\>** Welcome Andrew and thanks for taking out time to share
your thoughts. What programming languages have you used seriously?

**Andrew\>\>** Seriously: Ruby and Clojure. Less Seriously: C, C++, Java
and now: Haskell, Scheme.

**Satish\>\>** Why and when did you decide to start working on Clojure?

**Andrew\>\>** I’ve been using Clojure for a little over a year. I had
read Paul Graham’s essays, so I wanted to try a lisp dialect. I also
wanted to learn what functional programming was all about. Then I
watched Rich Hickey’s presentations on Clojure and by that point I was
pretty much sold.

**Satish\>\>** Could you name three features of Clojure that you like
the most, as compared to other languages? Why?

**Andrew\>\>**

1.  **Immutability**: Using immutable locals and data structures as the
    default eliminates a huge class of potential errors. I’ve never
    written as much code that worked on the first try in any other
    language. Concurrency is often mentioned as a great benefit from
    pervasive immutability — and it certainly is — but for me, the net
    reduction in complexity is what I love most.
2.  **It’s a Lisp: It has Macros**: Whether its for shearing off boiler
    plate, or embedding a parser for an internal DSL, the ability to
    easily extend the syntax of the language is a uniquely expressive
    trait of the lisp family.
3.  **The immense practicality of the JVM**: By being hosted on the JVM,
    Clojure comes with batteries-included and can be deployed anywhere
    that Java can (almost anywhere).

**Satish\>\>** You have written a Clojure wrapper (congomongo) for the
mongo-db java api. Can you tell us more about this wrapper? Also, why
did you target MongoDB?

**Andrew\>\>** I really like working with MongoDB. The combination of
schema-less document storage and ad-hoc queries is fantastic. The JSON
format fits Clojure’s data structures well, and the mongo-java-driver is
high quality and maintained. Congomongo is fairly light-weight — its
main goal is to make interacting with the database from Clojure
convenient and idiomatic.

*Thank you Andrew. In case you have any queries and/or questions, kindly
post your questions here (as comments to this blog post) and Andrew
would be glad to answer.*
