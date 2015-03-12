---
author: Satish Talim
categories:
- code snippets
- ruby
- tricks
date: 2007-02-06
layout: post
title: Convert bytes to megabytes
---

In one of my projects, I need to find the file-size in megabytes again
and again. This simple method helps me to convert the size of a file in
bytes to megabytes. This is useful for very large files.

    MEGABYTE = 1024.0 * 1024.0
    def bytesToMeg bytes
      bytes /  MEGABYTE
    end

    # big file
    len = File.size("Dreamweaver8-en.exe")
    puts len.to_s + ' bytes'  # displays 62651176 bytes
    puts bytesToMeg(len).to_s + ' MB'  # displays 59.7488174438477 MB

* * * * *

One of the uses for [PDF conversion](http://www.investintech.com/) is
that by going through the process of [converting PDF to
Word](http://www.oardc.ohio-state.edu/library/word_to_pdf.html) you’ll
have a more easily editable document than if you didn’t do [PDF
conversion](http://www.investintech.com/prod_a2d.htm) and tried to edit
a PDF file.\

* * * * *

The program code is pretty obvious and as you can see the method uses
division. However, it is best to wrap this functionality in a method.

Technorati Tags: [Convert bytes to
megabytes](http://technorati.com/tag/Convert+bytes+to+megabytes), [Ruby
tricks](http://technorati.com/tag/Ruby+tricks)
