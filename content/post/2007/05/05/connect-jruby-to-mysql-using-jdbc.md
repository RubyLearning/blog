---
title: "Connect JRuby to MySQL using JDBC"
author: "Satish Talim"
date: "2007-05-05"
layout: post
categories:
  - jruby
  - rails
  - ruby
---
**JRuby** is a 100% pure-Java implementation of the Ruby programming
language that runs in the JVM. **MySQL** is a one of the most popular
open source databases around and is used by many prominent organizations
from Yahoo to NASA.<!--more-->

This brief tutorial demonstrates how to *install and configure JRuby to
connect to the MySQL database*. The tutorial is written for beginners
who are familiar with Java code and JDBC. Exposure to Ruby will make the
syntax easier to follow. You don’t need any specific integrated
development environment (IDE) or tool knowledge. Familiarity with a text
editor and setting environment variables is required.

The tutorial assumes that your Java,
[JRuby](http://rubylearning.com/blog/2007/04/27/jruby-caffeinated-ruby/)
and MySQL 4.1+ environment is successfully installed and configured.

#### Creating a Database and User

Again, I am assuming that you have MySQL running and are familiar with
the basics. Run the mysql client program from the command line (as shown
below) so that we can execute some administration commands.

    C:/mysql/bin> mysql --user=root mysql

First create a database called “ruby” within MySQL and the user is root.

    mysql> CREATE DATABASE ruby;
    Query OK, 1 row affected (0.02 sec)

and check that it has been created using

    mysql> SHOW DATABASES;
    +------------+
    | Database   |
    +------------+
    | ruby       |
    | mysql      |
    | test       |
    +------------+
    3 rows in set (0.01 sec)

Let’s create a table in our database ruby

    use ruby;
    create table student (id VARCHAR(2), name VARCHAR(20), rank VARCHAR(2));

To check whether the table has been created, type:

    show tables;
    +---------------------+
    | Tables_in_ruby      |
    +---------------------+
    | student             |
    +---------------------+
    1 row in set (0.00 sec)

To verify your table, type:

    mysql> describe student;
    +--------+----------------+------+------+-----------+--------+
    | Field  | Type           | Null | Key  | Default   | Extra  |
    +--------+----------------+------+------+-----------+--------+
    | id     | char(2)        | YES  |      | NULL      |        |
    | name   | varchar(20)    | YES  |      | NULL      |        |
    | rank   | char(2)        | YES  |      | NULL      |        |
    +--------+----------------+------+------+-----------+--------+
    3 rows in set (0.04 sec)

Now let us insert 3 records into student table:

    mysql> insert into student values ('01', 'Peter', '10');
    Query OK, 1 row affected (0.06 sec)

    mysql> insert into student values ('02', 'Bruce', '08');
    Query OK, 1 row affected (0.01 sec)

    mysql> insert into student values ('03', 'Pat', '06');
    Query OK, 1 row affected (0.00 sec)

#### Download type 4 pure JDBC driver

[Download](http://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-3.1.10.zip/from/pick)
mySQL Connector/J Ver 3.1.10 or later open source JDBC driver for the
above database. Unzip and Install the pure JDBC driver to C:/default
folder ie. C:/mysql-connector-java-3.1.8\
Next, copy the file mysql-connector-java-3.1.10-bin.jar to the lib
folder of your Java installation and then add this .jar file location to
your system environment variable classpath.

#### Connect to MySQL

Now that you’ve created a database and populated it with some data, your
next task is to connect to that database using JRuby. To do so, create a
new file named jrubyjdbc.rb. Open this file in a text editor, and enter
the lines shown below:

    require 'java'

    module JavaLang
      include_package "java.lang"
    end

    module JavaSql
      include_package 'java.sql'
    end

    begin
      JavaLang::Class.forName("com.mysql.jdbc.Driver").newInstance
      conn = JavaSql::DriverManager.getConnection("jdbc:mysql://127.0.0.1:3306/ruby?user=root");
      stmt = conn.createStatement
      rs = stmt.executeQuery("select name from student")
      while (rs.next) do
        puts rs.getString("name")
      end
      rs.close
      stmt.close
      conn.close()
    rescue JavaLang::ClassNotFoundException
      puts "ClassNotFoundException"
    rescue JavaSql::SQLException
      puts "SQLException"
    end

The code should work and you should get the output as:

    C:/rubyprograms>jruby jrubyjdbc.rb
    Peter
    Bruce
    Pat

#### Some code explanation

-   Create a Ruby module into which you put all the classes in java.sql.
    Because you’re using numerous classes from the java.sql package, it\
     makes sense to include the whole package. Keep in mind that
    including the package slows your script. This use of a module is a
    convenient way to access all of these classes.
-   There can be name clashes between Java class names and Ruby class
    names. Class is an example of this; Java has java.lang.Class and
    Ruby also has Class. To resolve this name clash, define a Ruby
    module that includes the Java class definition.
-   There’s no need to declare the type of the variable named
    connection. Ruby is a dynamically typed language; therefore types
    aren’t required for variable declarations.
-   Class.forName and DriverManager.getConnection both throw checked
    exceptions. In Java code, the equivalent code won’t compile until
    you do something with those exceptions. Ruby doesn’t have checked
    exceptions, so you aren’t forced to handle them. However, when
    writing an application, you generally want to do something with
    exceptions if you can. Two checked exceptions could arise from your
    code: ClassNotFoundException and SQLException. Exceptions in Ruby
    are handled similarly to the Java approach. You have a block
    starting with begin instead of try and ending with end instead of }.
    Instead of catch, you use rescue.

Go on! **[Digg
It](http://digg.com/programming/Connect_JRuby_to_MySQL_using_JDBC)** !

Technorati Tags: [Connect JRuby to MySQL using
JDBC](http://technorati.com/tag/Connect+JRuby+to+MySQL+using+JDBC),
[Java](http://technorati.com/tag/Java),
[JDBC](http://technorati.com/tag/JDBC),
[JRuby](http://technorati.com/tag/JRuby),
[MySQL](http://technorati.com/tag/MySQL),
[Ruby](http://technorati.com/tag/Ruby)
