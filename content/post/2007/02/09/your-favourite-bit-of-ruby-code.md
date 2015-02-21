---
title: "Your favourite bit of Ruby code?"
author: "Satish Talim"
date: "2007-02-09"
layout: post
categories:
  - code snippets
  - ruby
  - tricks
---
An interesting thread at Ruby\_talk is 'Your favorite bit of Ruby code.'

* * * * *

Setting aside time for [learning
HTML](http://www.socialstudieshelp.com/topics/learning-html.html) is
beneficial to any web host.\

* * * * *

[John Carter](mailto:john.carter@tait.co.nz) from New Zealand has this
interesting snippet of code:

    # Ruby is Objects all the way down and open for extension...
    class Integer
      def factorial
        return 1 if self <= 1
        self * (self-1).factorial
      end
    end

    puts 6.factorial

Technorati Tags: [Ruby code](http://technorati.com/tag/Ruby+code)
