---
title: Convert bytes to megabytes
author: Satish Talim
date: 2007-02-06
layout: post
permalink: /2007/02/06/convert-bytes-to-megabytes/
categories:
  - Code Snippets
  - Ruby
  - Tricks
---
<div>
  <!--adsense-->
</div>

<div>
  <p>
    In one of my projects, I need to find the file-size in megabytes again and again. This simple method helps me to convert the size of a file in bytes to megabytes. This is useful for very large files.
  </p>
  
  <pre>MEGABYTE = 1024.0 * 1024.0
def bytesToMeg bytes
  bytes /  MEGABYTE  
end

# big file
len = File.size("Dreamweaver8-en.exe")
puts len.to_s + ' bytes'  # displays 62651176 bytes
puts bytesToMeg(len).to_s + ' MB'  # displays 59.7488174438477 MB
</pre>
  
  <hr />
  One of the uses for 
  <a href="http://www.investintech.com/">PDF conversion</a> is that by going through the process of <a href="http://www.oardc.ohio-state.edu/library/word_to_pdf.html">converting PDF to Word</a> you&#8217;ll have a more easily editable document than if you didn&#8217;t do <a href="http://www.investintech.com/prod_a2d.htm">PDF conversion</a> and tried to edit a PDF file.<br /> 
  
  <hr />
  
  <p>
    The program code is pretty obvious and as you can see the method uses division. However, it is best to wrap this functionality in a method.
  </p>
</div>

<div>
  <a href="http://technorati.com/tag/Instant+Rails" rel="tag"></a><a href="http://technorati.com/tag/Quick+Ruby" rel="tag"></a><a href="http://technorati.com/tag/Instant+Rails" rel="tag"></a><a href="http://technorati.com/tag/Pune+Ruby" rel="tag"></a><a href="http://technorati.com/tag/Quick+Ruby+Guide" rel="tag"></a><a href="http://technorati.com/tag/Programming+Languages" rel="tag"></a><a href="http://technorati.com/tag/Blogs" rel="tag"></a><a href="http://technorati.com/tag/Ruby" rel="tag"></a><a href="http://technorati.com/tag/PuneRuby" rel="tag"></a><a href="http://technorati.com/tag/QuickRuby" rel="tag"></a><a href="http://technorati.com/tag/PuneBloggers" rel="tag"></a><a href="http://technorati.com/tag/PuneBlogs" rel="tag"></a><a href="http://technorati.com/tag/Blogosphere" rel="tag"></a><a href="http://technorati.com/tag/Digg" rel="tag"></a><a href="http://technorati.com/tag/Media" rel="tag"></a><a href="http://technorati.com/tag/Tip" rel="tag"></a><a href="http://technorati.com/tag/RSS" rel="tag"></a><a href="http://technorati.com/tag/Marketing" rel="tag"></a><a href="http://technorati.com/tag/News" rel="tag"></a><a href="http://technorati.com/tag/IndianGuru" rel="tag"></a><a href="http://technorati.com/tag/Blogging" rel="tag"></a><a href="http://technorati.com/tag/Internet" rel="tag"></a><a href="http://technorati.com/tag/Blog" rel="tag"></a><a href="http://technorati.com/tag/Technical+Support" rel="tag"></a><a href="http://technorati.com/tag/Free+Software" rel="tag"></a><a href="http://technorati.com/tag/Help" rel="tag"></a><a href="http://technorati.com/tag/Pune" rel="tag"></a><a href="http://technorati.com/tag/SatishTalim" rel="tag"></a><a href="http://technorati.com/tag/Satish+Talim" rel="tag"></a><a href="http://technorati.com/tag/Weblog" rel="tag"></a><a href="http://technorati.com/tag/Weblogs" rel="tag"></a><a href="http://technorati.com/tag/Training" rel="tag"></a><a href="http://technorati.com/tag/Free+Training" rel="tag"></a><a href="http://technorati.com/tag/Tutorial" rel="tag"></a><a href="http://technorati.com/tag/Education" rel="tag"></a><a href="http://technorati.com/tag/Teacher" rel="tag"></a><a href="http://technorati.com/tag/Learning+Ruby" rel="tag"></a>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Convert+bytes+to+megabytes" rel="tag">Convert bytes to megabytes</a>, <a href="http://technorati.com/tag/Ruby+tricks" rel="tag">Ruby tricks</a>
