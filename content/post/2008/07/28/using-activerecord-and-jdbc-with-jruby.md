---
title: Using ActiveRecord and JDBC with JRuby
author: Satish Talim
date: 2008-07-28
layout: post
permalink: /2008/07/28/using-activerecord-and-jdbc-with-jruby/
topsy_short_url:
  - http://bit.ly/dluxgS
categories:
  - JRuby
  - Ruby
tags:
  - ActiveRecord
  - JDBC
  - JRuby
---
<div>
  <h3>
    Preamble
  </h3>
  
  <p>
    The participants of the <a href="http://rubylearning.org/">FORPC101</a> series of courses have been requesting me for a small article related to JRuby; so here it is.
  </p>
  
  <p>
    In this article, we shall see how easy it is to connect to a database (MySQL) using ActiveRecord and a JDBC driver using JRuby.
  </p>
  
  <h3>
    Assumptions
  </h3>
  
  <p>
    I am assuming that you have Java 1.6, JRuby 1.1.3, MySQL installed and working.
  </p>
  
  <h3>
    Note
  </h3>
  
  <p>
    I am using a Windows XP box but these examples will work on a Mac or Linux box too.
  </p>
  
  <h3>
    JRuby
  </h3>
  
  <blockquote>
    <p>
      For Ruby Developers, JRuby offers a deployment platform that is well understood, particular in corporations. For a Java community, JRuby is important because it offers a chance to experience a powerful language and framework while still taking advantage of Javaâ€™s excellent libraries and the ability to work in both Ruby and Java &#8211; <strong>Martin Fowler</strong>
    </p>
  </blockquote>
  
  <h3>
    MySQL
  </h3>
  
  <p>
    <a href="http://www.mysql.com/">MySQL</a> is a one of the most popular open source databases around and is used by many prominent organizations from Yahoo to NASA.
  </p>
  
  <h3>
    ORM and ActiveRecord
  </h3>
  
  <p>
    <a href="http://en.wikipedia.org/wiki/Object-relational_mapping">ORM</a>, stands for object-relational mapping. ORM libraries map database tables to classes. If a database has a table called orders, our program will have a class named Order. Rows in this table correspond to objects of the class &#8211; a particular order is represented as an object of class Order. Within that object, attributes are used to get and set the individual columns. Our Order object has methods to get and set the amount, the sales tax, and so on.
  </p>
  
  <p>
    <strong>So an ORM layer maps tables to classes, rows to objects, and columns to attributes of those objects</strong>. Class methods are used to perform table-level operations, and instance methods perform operations on the individual rows. <strong>Active Record is an ORM</strong>.<br /><strong>ActiveRecord</strong> relieves us of the hassles of dealing with the underlying database, leaving us free to work on business logic. <strong>ActiveRecord</strong> relies on convention over configuration. Wherever possible, <strong>ActiveRecord</strong> guesses the correct configuration by reflecting against the data schema. When you do need a specific override, you specify the override directly in your class.
  </p>
  
  <p>
    Also, <strong>ActiveRecord</strong> assumes that:
  </p>
  
  <ul>
    <li>
      database table names, like variable names, have lowercase letters and underscores between the words
    </li>
    <li>
      table names are always plural
    </li>
    <li>
      files are named in lowercase with underscores
    </li>
  </ul>
  
  <p>
    <strong>ActiveRecord implements some of its <a href="http://www.thirdbit.net/articles/2007/08/01/10-things-you-should-know-about-method_missing/">funkiest magic</a></strong> with <strong>method_missing</strong> because <strong>ActiveRecord::Base</strong> overrides the Kernelâ€™s <strong>method_missing</strong> method.
  </p>
  
  <h3>
    RubyGems
  </h3>
  
  <p>
    JRuby comes with a fairly loaded standard library from scratch but that does not mean there arenâ€™t other things youâ€™ll need. Almost all of them are installable as Gems. RubyGems is the premier package management tool for Ruby. It works fine with JRuby and JRuby ships with it. You use it through the gem command. Now, we need to run the JRuby version of the gem command and to ensure that, we use the â€“S flag to the interpreter.<br />We shall install <strong>ActiveRecord</strong> as a freestanding gem in JRuby:
  </p>
  
  <pre><code>C:\>jruby -S gem install activerecord</code></pre>
  
  <h3>
    Adapter
  </h3>
  
  <p>
    In <strong>ActiveRecord</strong> there is this concept of an adapter. Each adapter is specific for one database, so thereâ€™s a MySQL adapter, an Oracle adapter, and so on. <em>At the moment, there are few adapters that ship with ActiveRecord</em>. <br />The <strong>activerecord-jdbc-adapter</strong> adapter is needed as it allows use of virtually any JDBC-compliant database with your JRuby application. This adapter supports:
  </p>
  
  <ul>
    <li>
      MySQL &#8211; Complete support
    </li>
    <li>
      PostgreSQL &#8211; Complete support
    </li>
    <li>
      Oracle &#8211; Complete support
    </li>
    <li>
      Microsoft SQL Server &#8211; Complete support except for change_column_default
    </li>
    <li>
      DB2 &#8211; Complete, except for the migrations: <ul>
        <li>
          change_column
        </li>
        <li>
          change_column_default
        </li>
        <li>
          remove_column
        </li>
        <li>
          rename_column
        </li>
        <li>
          add_index
        </li>
        <li>
          remove_index
        </li>
        <li>
          rename_table
        </li>
      </ul>
    </li>
    
    <li>
      FireBird &#8211; Complete, except for change_column_default and rename_column
    </li>
    <li>
      Derby &#8211; Complete, except for: <ul>
        <li>
          change_column
        </li>
        <li>
          change_column_default
        </li>
        <li>
          remove_column
        </li>
        <li>
          rename_column
        </li>
      </ul>
    </li>
    
    <li>
      HSQLDB &#8211; Complete
    </li>
    <li>
      H2 &#8211; Complete
    </li>
    <li>
      SQLite3 &#8211; work in progress
    </li>
  </ul>
  
  <p>
    We will install the <strong>activerecord-jdbcxxx-adapter</strong>, where xxx would be the database name, for example <strong>activerecord-jdbcmysql-adapter</strong> for MySQL. We are going to use the adapter for a specific database (MySQL). You can install it directly and a driver gem will be installed as well.<br />Other databases will require testing and likely a custom configuration module.<br />Ensure that your MySQL service is running.
  </p>
  
  <p>
    Open a command window and type:
  </p>
  
  <pre><code>C:\>jruby -S gem install activerecord-jdbcmysql-adapter</code></pre>
  
  <p>
    From your JRuby code, you need to specify only the name of the adapter you want to use; <strong>ActiveRecord</strong> will provide the Ruby bridge code.
  </p>
  
  <p>
    The article is continued in <a href="http://rubylearning.com/blog/2008/07/30/using-activerecord-and-jdbc-with-jruby-part-2/">Part 2</a>.
  </p>
  
  <h3>
    References
  </h3>
  
  <ol>
    <li>
      <a href="http://www.apress.com/book/view/1590598814">Practical JRuby on Rails</a>
    </li>
    <li>
      <a href="http://github.com/nicksieger/activerecord-jdbc-adapter/tree/master">activerecord-jdbcXXX-adapter</a>
    </li>
  </ol>
</div>

Technorati Tags: <a href="http://technorati.com/tag/ActiveRecord" rel="tag">ActiveRecord</a>, <a href="http://technorati.com/tag/JDBC" rel="tag">JDBC</a>, <a href="http://technorati.com/tag/JRuby" rel="tag">JRuby</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>
