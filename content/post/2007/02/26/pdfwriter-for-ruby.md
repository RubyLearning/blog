---
title: "PDF::Writer for Ruby"
author: Satish Talim
date: "2007-02-26"
layout: post
permalink: /2007/02/26/pdfwriter-for-ruby/
categories:
  - ruby
---
<div>
  <!--adsense-->
</div>

<div>
  <p>
    This brief blog post is in response to the many emails you wrote to me, to blog a bit about <strong>PDF::Writer for Ruby</strong>.
  </p>
  
  <p>
    <strong>PDF::Writer for Ruby</strong> by Austin Ziegler, provides the ability to create PDF documents using only native Ruby libraries. Many web applications may want to offer PDF as one possible download format.
  </p>
  
  <hr />
  
  <p>
    If you need to <a href="http://www.investintech.com/">convert PDF to Word</a> in order to more easily edit your <a href="http://www.oardc.ohio-state.edu/library/word_to_pdf.html" >PDF files</a> then a specialized piece of <a href="http://www.investintech.com/prod_a2d.htm">PDF converter</a> software is probably better than free online ones.
  </p>
  
  <hr />
  
  <p>
    On your Windows, load the pdf-writer gem and write a PDF. If you don&#8217;t already have pdf-writer on your system, just run the following command:
  </p>
  
  <pre>gem install pdf-writer</pre>
  
  <p>
    Now you can use the gem mechanism to load pdf-writer and create a PDF document, as shown in the following example:
  </p>
  
  <pre>require 'rubygems'
require_gem 'pdf-writer'

pdf = PDF::Writer.new
pdf.select_font "Times-Roman"
pdf.text "Hello, Ruby." , :font_size => 72, :justification => :center
pdf.save_as("hello.pdf" )</pre>
  
  <p>
    The call to require &#8216;rubygems&#8217; loads the gem mechanism, and then the call require_gem &#8216;pdf-writer&#8217; loads the pdf-writer gem.
  </p>
  
  <p>
    The above example is adapted from the tutorial/article on how to publish printable documents at <a href="http://www.artima.com/rubycs/articles/pdf_writer.html" >artima.com</a>. In this article, Austin Ziegler introduces the creation of a variety of types of documents with PDF::Writer for Ruby. This introduction covers basic creation, partial document generation and customization, and Rails-generated documents.
  </p>
</div>

<div>
  <a href="http://technorati.com/tag/Instant+Rails" rel="tag"></a><a href="http://technorati.com/tag/Quick+Ruby" rel="tag"></a><a href="http://technorati.com/tag/Instant+Rails" rel="tag"></a><a href="http://technorati.com/tag/Pune+Ruby" rel="tag"></a><a href="http://technorati.com/tag/Quick+Ruby+Guide" rel="tag"></a><a href="http://technorati.com/tag/Programming+Languages" rel="tag"></a><a href="http://technorati.com/tag/Blogs" rel="tag"></a><a href="http://technorati.com/tag/Ruby" rel="tag"></a><a href="http://technorati.com/tag/PuneRuby" rel="tag"></a><a href="http://technorati.com/tag/QuickRuby" rel="tag"></a><a href="http://technorati.com/tag/PuneBloggers" rel="tag"></a><a href="http://technorati.com/tag/PuneBlogs" rel="tag"></a><a href="http://technorati.com/tag/Blogosphere" rel="tag"></a><a href="http://technorati.com/tag/Digg" rel="tag"></a><a href="http://technorati.com/tag/Media" rel="tag"></a><a href="http://technorati.com/tag/Tip" rel="tag"></a><a href="http://technorati.com/tag/RSS" rel="tag"></a><a href="http://technorati.com/tag/Marketing" rel="tag"></a><a href="http://technorati.com/tag/News" rel="tag"></a><a href="http://technorati.com/tag/IndianGuru" rel="tag"></a><a href="http://technorati.com/tag/Blogging" rel="tag"></a><a href="http://technorati.com/tag/Internet" rel="tag"></a><a href="http://technorati.com/tag/Blog" rel="tag"></a><a href="http://technorati.com/tag/Technical+Support" rel="tag"></a><a href="http://technorati.com/tag/Free+Software" rel="tag"></a><a href="http://technorati.com/tag/Help" rel="tag"></a><a href="http://technorati.com/tag/Pune" rel="tag"></a><a href="http://technorati.com/tag/SatishTalim" rel="tag"></a><a href="http://technorati.com/tag/Satish+Talim" rel="tag"></a><a href="http://technorati.com/tag/Weblog" rel="tag"></a><a href="http://technorati.com/tag/Weblogs" rel="tag"></a><a href="http://technorati.com/tag/Training" rel="tag"></a><a href="http://technorati.com/tag/Free+Training" rel="tag"></a><a href="http://technorati.com/tag/Tutorial" rel="tag"></a><a href="http://technorati.com/tag/Education" rel="tag"></a><a href="http://technorati.com/tag/Teacher" rel="tag"></a><a href="http://technorati.com/tag/Learning+Ruby" rel="tag"></a>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Austin+Ziegler" rel="tag">Austin Ziegler</a>, <a href="http://technorati.com/tag/PDF%3A%3AWriter+for+Ruby" rel="tag">PDF::Writer for Ruby</a>
