---
title: "Ruby MySQL Tutorial"
author: "Satish Talim"
date: "2007-05-14"
layout: post
categories:
  - code snippets
  - ruby
---
This brief **Ruby MySQL Tutorial** shows you how you can connect to
MySQL in Ruby. MySQL support in Ruby was made possible by Tomita
Masahiro. He has developed a pure Ruby binding called Ruby/MySQL. We
need to install the same on our PC and the installation (you need to be
connected to the internet and it takes some time) is as shown below:

    C:\>gem install mysql
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
    C:\>

This installs mysql-2.7.1-mswin32 driver which is faster and supports
MySQL 4.1 and later. The documentation for this driver is
[here](http://tmtm.org/en/mysql/ruby/).

I will assume that you’ve already installed mySQL 4.1 or above on your
PC and that you have it running and are familiar with the basics.

Now, run the mysql client program from the command line, as:

    C:\>mysql

You should get the mysql prompt. Next, create a database ruby as:

    mysql> create database ruby;
    Query OK, 1 row affected (0.02 sec)

Next, create a table student in the database ruby as:

    mysql> use ruby;
    create table student (id VARCHAR(2), name VARCHAR(20), rank VARCHAR(2));

As a first exercise we try to connect to the MySQL server and print all
the names in the table student. Program **p078rubymysql.rb**

    require 'mysql'

    #my = Mysql.new(hostname, username, password, databasename)
    con = Mysql.new('localhost', '', '', 'student')
    rs = con.query('select * from student')
    rs.each_hash { |h| puts h['name']}
    con.close

It is as simple as that. You can explore this api further.

Technorati Tags: [MySQL](http://technorati.com/tag/MySQL),
[Ruby](http://technorati.com/tag/Ruby), [Ruby MySQL
Tutorial](http://technorati.com/tag/Ruby+MySQL+Tutorial)
