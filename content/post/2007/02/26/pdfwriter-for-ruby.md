---
author: Satish Talim
categories:
- ruby
date: 2007-02-26
layout: post
title: PDF::Writer for Ruby
---

This brief blog post is in response to the many emails you wrote to me,
to blog a bit about **PDF::Writer for Ruby**.<!--more-->

**PDF::Writer for Ruby** by Austin Ziegler, provides the ability to
create PDF documents using only native Ruby libraries. Many web
applications may want to offer PDF as one possible download format.

* * * * *

If you need to [convert PDF to Word](http://www.investintech.com/) in
order to more easily edit your [PDF
files](http://www.oardc.ohio-state.edu/library/word_to_pdf.html) then a
specialized piece of [PDF
converter](http://www.investintech.com/prod_a2d.htm) software is
probably better than free online ones.

* * * * *

On your Windows, load the pdf-writer gem and write a PDF. If you don’t
already have pdf-writer on your system, just run the following command:

    gem install pdf-writer

Now you can use the gem mechanism to load pdf-writer and create a PDF
document, as shown in the following example:

    require 'rubygems'
    require_gem 'pdf-writer'

    pdf = PDF::Writer.new
    pdf.select_font "Times-Roman"
    pdf.text "Hello, Ruby." , :font_size => 72, :justification => :center
    pdf.save_as("hello.pdf" )

The call to require ‘rubygems’ loads the gem mechanism, and then the
call require\_gem ‘pdf-writer’ loads the pdf-writer gem.

The above example is adapted from the tutorial/article on how to publish
printable documents at
[artima.com](http://www.artima.com/rubycs/articles/pdf_writer.html). In
this article, Austin Ziegler introduces the creation of a variety of
types of documents with PDF::Writer for Ruby. This introduction covers
basic creation, partial document generation and customization, and
Rails-generated documents.

[](http://technorati.com/tag/Instant+Rails)[](http://technorati.com/tag/Quick+Ruby)[](http://technorati.com/tag/Instant+Rails)[](http://technorati.com/tag/Pune+Ruby)[](http://technorati.com/tag/Quick+Ruby+Guide)[](http://technorati.com/tag/Programming+Languages)[](http://technorati.com/tag/Blogs)[](http://technorati.com/tag/Ruby)[](http://technorati.com/tag/PuneRuby)[](http://technorati.com/tag/QuickRuby)[](http://technorati.com/tag/PuneBloggers)[](http://technorati.com/tag/PuneBlogs)[](http://technorati.com/tag/Blogosphere)[](http://technorati.com/tag/Digg)[](http://technorati.com/tag/Media)[](http://technorati.com/tag/Tip)[](http://technorati.com/tag/RSS)[](http://technorati.com/tag/Marketing)[](http://technorati.com/tag/News)[](http://technorati.com/tag/IndianGuru)[](http://technorati.com/tag/Blogging)[](http://technorati.com/tag/Internet)[](http://technorati.com/tag/Blog)[](http://technorati.com/tag/Technical+Support)[](http://technorati.com/tag/Free+Software)[](http://technorati.com/tag/Help)[](http://technorati.com/tag/Pune)[](http://technorati.com/tag/SatishTalim)[](http://technorati.com/tag/Satish+Talim)[](http://technorati.com/tag/Weblog)[](http://technorati.com/tag/Weblogs)[](http://technorati.com/tag/Training)[](http://technorati.com/tag/Free+Training)[](http://technorati.com/tag/Tutorial)[](http://technorati.com/tag/Education)[](http://technorati.com/tag/Teacher)[](http://technorati.com/tag/Learning+Ruby)

Technorati Tags: [Austin
Ziegler](http://technorati.com/tag/Austin+Ziegler), [PDF::Writer for
Ruby](http://technorati.com/tag/PDF%3A%3AWriter+for+Ruby)
