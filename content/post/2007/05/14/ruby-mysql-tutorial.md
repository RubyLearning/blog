---
title: Ruby MySQL Tutorial
author: Satish Talim
date: 2007-05-14
layout: post
permalink: /2007/05/14/ruby-mysql-tutorial/
categories:
  - Code Snippets
  - Ruby
---
<div>
  <p>
    This brief <strong>Ruby MySQL Tutorial</strong> shows you how you can connect to MySQL in Ruby. MySQL support in Ruby was made possible by Tomita Masahiro. He has developed a pure Ruby binding called Ruby/MySQL. We need to install the same on our PC and the installation (you need to be connected to the internet and it takes some time) is as shown below:
  </p>
  
  <pre><code>C:\>gem install mysql
Bulk updating Gem source index for: http://gems.rubyforge.org
Select which gem to install for your platform (i386-mswin32)

 1. mysql 2.7.1 (mswin32)

 2. mysql 2.7 (ruby)

 3. mysql 2.6 (ruby)

 4. mysql 2.5.1 (ruby)

 5. Cancel installation

> 1
Successfully installed mysql-2.7.1-mswin32
Installing ri documentation for mysql-2.7.1-mswin32...
Installing RDoc documentation for mysql-2.7.1-mswin32...
C:\></code></pre>
  
  <p>
    This installs mysql-2.7.1-mswin32 driver which is faster and supports MySQL 4.1 and later. The documentation for this driver is <a href="http://tmtm.org/en/mysql/ruby/" >here</a>.
  </p>
  
  <p>
    I will assume that you&#8217;ve already installed mySQL 4.1 or above on your PC and that you have it running and are familiar with the basics.
  </p>
  
  <p>
    Now, run the mysql client program from the command line, as:
  </p>
  
  <pre><code>C:\>mysql</code></pre>
  
  <p>
    You should get the mysql prompt. Next, create a database ruby as:
  </p>
  
  <pre><code>mysql> create database ruby;
Query OK, 1 row affected (0.02 sec)</code></pre>
  
  <p>
    Next, create a table student in the database ruby as:
  </p>
  
  <pre><code>mysql> use ruby;
create table student (id VARCHAR(2), name VARCHAR(20), rank VARCHAR(2));</code></pre>
  
  <p>
    As a first exercise we try to connect to the MySQL server and print all the names in the table student. Program <strong>p078rubymysql.rb</strong>
  </p>
  
  <pre><code>require 'mysql'

#my = Mysql.new(hostname, username, password, databasename)
con = Mysql.new('localhost', '', '', 'student')
rs = con.query('select * from student')
rs.each_hash { |h| puts h['name']}
con.close
</code></pre>
  
  <p>
    It is as simple as that. You can explore this api further.
  </p>
</div>

<div>
  <a href="http://technorati.com/tag/Instant+Rails" rel="tag"></a><a href="http://technorati.com/tag/Quick+Ruby" rel="tag"></a><a href="http://technorati.com/tag/Instant+Rails" rel="tag"></a><a href="http://technorati.com/tag/Pune+Ruby" rel="tag"></a><a href="http://technorati.com/tag/Quick+Ruby+Guide" rel="tag"></a><a href="http://technorati.com/tag/Programming+Languages" rel="tag"></a><a href="http://technorati.com/tag/Blogs" rel="tag"></a><a href="http://technorati.com/tag/Ruby" rel="tag"></a><a href="http://technorati.com/tag/PuneRuby" rel="tag"></a><a href="http://technorati.com/tag/QuickRuby" rel="tag"></a><a href="http://technorati.com/tag/PuneBloggers" rel="tag"></a><a href="http://technorati.com/tag/PuneBlogs" rel="tag"></a><a href="http://technorati.com/tag/Blogosphere" rel="tag"></a><a href="http://technorati.com/tag/Digg" rel="tag"></a><a href="http://technorati.com/tag/Media" rel="tag"></a><a href="http://technorati.com/tag/Tip" rel="tag"></a><a href="http://technorati.com/tag/RSS" rel="tag"></a><a href="http://technorati.com/tag/Marketing" rel="tag"></a><a href="http://technorati.com/tag/News" rel="tag"></a><a href="http://technorati.com/tag/IndianGuru" rel="tag"></a><a href="http://technorati.com/tag/Blogging" rel="tag"></a><a href="http://technorati.com/tag/Internet" rel="tag"></a><a href="http://technorati.com/tag/Blog" rel="tag"></a><a href="http://technorati.com/tag/Technical+Support" rel="tag"></a><a href="http://technorati.com/tag/Free+Software" rel="tag"></a><a href="http://technorati.com/tag/Help" rel="tag"></a><a href="http://technorati.com/tag/Pune" rel="tag"></a><a href="http://technorati.com/tag/SatishTalim" rel="tag"></a><a href="http://technorati.com/tag/Satish+Talim" rel="tag"></a><a href="http://technorati.com/tag/Weblog" rel="tag"></a><a href="http://technorati.com/tag/Weblogs" rel="tag"></a><a href="http://technorati.com/tag/Training" rel="tag"></a><a href="http://technorati.com/tag/Free+Training" rel="tag"></a><a href="http://technorati.com/tag/Tutorial" rel="tag"></a><a href="http://technorati.com/tag/Education" rel="tag"></a><a href="http://technorati.com/tag/Teacher" rel="tag"></a><a href="http://technorati.com/tag/Learning+Ruby" rel="tag"></a>
</div>

Technorati Tags: <a href="http://technorati.com/tag/MySQL" rel="tag">MySQL</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Ruby+MySQL+Tutorial" rel="tag">Ruby MySQL Tutorial</a>
