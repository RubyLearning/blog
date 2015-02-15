---
title: Connect JRuby to MySQL using JDBC
author: Satish Talim
date: 2007-05-05
layout: post
permalink: /2007/05/05/connect-jruby-to-mysql-using-jdbc/
topsy_short_url:
  - http://bit.ly/RpYUwO
thesis_thumb_width:
  - 66
thesis_thumb_height:
  - 66
categories:
  - JRuby
  - Rails
  - Ruby
---
<div>
  <p>
    <strong>JRuby</strong> is a 100% pure-Java implementation of the Ruby programming language that runs in the JVM. <strong>MySQL</strong> is a one of the most popular open source databases around and is used by many prominent organizations from Yahoo to NASA.
  </p>
  
  <p>
    This brief tutorial demonstrates how to <i>install and configure JRuby to connect to the MySQL database</i>. The tutorial is written for beginners who are familiar with Java code and JDBC. Exposure to Ruby will make the syntax easier to follow. You don&#8217;t need any specific integrated development environment (IDE) or tool knowledge. Familiarity with a text editor and setting environment variables is required.
  </p>
  
  <p>
    The tutorial assumes that your Java, <a href="http://rubylearning.com/blog/2007/04/27/jruby-caffeinated-ruby/" >JRuby</a> and MySQL 4.1+ environment is successfully installed and configured.
  </p>
  
  <h4>
    Creating a Database and User
  </h4>
  
  <p>
    Again, I am assuming that you have MySQL running and are familiar with the basics. Run the mysql client program from the command line (as shown below) so that we can execute some administration commands.
  </p>
  
  <pre><code>&lt;span style="color:blue">C:/mysql/bin> mysql --user=root mysql&lt;/span></code></pre>
  
  <p>
    First create a database called &#8220;ruby&#8221; within MySQL and the user is root.
  </p>
  
  <pre><code>&lt;span style="color:blue">mysql> CREATE DATABASE ruby;
Query OK, 1 row affected (0.02 sec)&lt;/span></code></pre>
  
  <p>
    and check that it has been created using
  </p>
  
  <pre><code>&lt;span style="color:blue">mysql> SHOW DATABASES;
+------------+
| Database   |
+------------+
| ruby       |
| mysql      |
| test       |
+------------+
3 rows in set (0.01 sec)&lt;/span></code></pre>
  
  <p>
    Let&#8217;s create a table in our database ruby
  </p>
  
  <pre><code>&lt;span style="color:blue">use ruby;
create table student (id VARCHAR(2), name VARCHAR(20), rank VARCHAR(2));&lt;/span></code></pre>
  
  <p>
    To check whether the table has been created, type:
  </p>
  
  <pre><code>&lt;span style="color:blue">show tables;
+---------------------+
| Tables_in_ruby      |
+---------------------+
| student             |
+---------------------+
1 row in set (0.00 sec)&lt;/span></code></pre>
  
  <p>
    To verify your table, type:
  </p>
  
  <pre><code>&lt;span style="color:blue">mysql> describe student;
+--------+----------------+------+------+-----------+--------+
| Field  | Type           | Null | Key  | Default   | Extra  |
+--------+----------------+------+------+-----------+--------+
| id     | char(2)        | YES  |      | NULL      |        |
| name   | varchar(20)    | YES  |      | NULL      |        |
| rank   | char(2)        | YES  |      | NULL      |        |
+--------+----------------+------+------+-----------+--------+
3 rows in set (0.04 sec)&lt;/span></code></pre>
  
  <p>
    Now let us insert 3 records into student table:
  </p>
  
  <pre><code>&lt;span style="color:blue">mysql> insert into student values ('01', 'Peter', '10');
Query OK, 1 row affected (0.06 sec)

mysql> insert into student values ('02', 'Bruce', '08');
Query OK, 1 row affected (0.01 sec)

mysql> insert into student values ('03', 'Pat', '06');
Query OK, 1 row affected (0.00 sec)&lt;/span></code></pre>
  
  <h4>
    Download type 4 pure JDBC driver
  </h4>
  
  <p>
    <a href = "http://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-3.1.10.zip/from/pick" >Download</a> mySQL Connector/J Ver 3.1.10 or later open source JDBC driver for the above database. Unzip and Install the pure JDBC driver to C:/default folder ie. C:/mysql-connector-java-3.1.8<br />Next, copy the file mysql-connector-java-3.1.10-bin.jar to the lib folder of your Java installation and then add this .jar file location to your system environment variable classpath.
  </p>
  
  <h4>
    Connect to MySQL
  </h4>
  
  <p>
    Now that you&#8217;ve created a database and populated it with some data, your next task is to connect to that database using JRuby. To do so, create a new file named jrubyjdbc.rb. Open this file in a text editor, and enter the lines shown below:
  </p>
  
  <pre><code>&lt;span style="color:blue">require 'java'

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
end&lt;/span></code></pre>
  
  <p>
    The code should work and you should get the output as:
  </p>
  
  <pre><code>&lt;span style="color:blue">C:/rubyprograms>jruby jrubyjdbc.rb
Peter
Bruce
Pat&lt;/span></code></pre>
  
  <h4>
    Some code explanation
  </h4>
  
  <ul>
    <li>
      Create a Ruby module into which you put all the classes in java.sql. Because you&#8217;re using numerous classes from the java.sql package, it<br /> makes sense to include the whole package. Keep in mind that including the package slows your script. This use of a module is a convenient way to access all of these classes.
    </li>
    <li>
      There can be name clashes between Java class names and Ruby class names. Class is an example of this; Java has java.lang.Class and Ruby also has Class. To resolve this name clash, define a Ruby module that includes the Java class definition.
    </li>
    <li>
      There&#8217;s no need to declare the type of the variable named connection. Ruby is a dynamically typed language; therefore types aren&#8217;t required for variable declarations.
    </li>
    <li>
      Class.forName and DriverManager.getConnection both throw checked exceptions. In Java code, the equivalent code won&#8217;t compile until you do something with those exceptions. Ruby doesn&#8217;t have checked exceptions, so you aren&#8217;t forced to handle them. However, when writing an application, you generally want to do something with exceptions if you can. Two checked exceptions could arise from your code: ClassNotFoundException and SQLException. Exceptions in Ruby are handled similarly to the Java approach. You have a block starting with begin instead of try and ending with end instead of }. Instead of catch, you use rescue.
    </li>
  </ul>
  
  <p>
    Go on! <strong><a href="http://digg.com/programming/Connect_JRuby_to_MySQL_using_JDBC" >Digg It</a></strong> !
  </p>
</div>

<div>
  <a href="http://technorati.com/tag/Instant+Rails" rel="tag"></a><a href="http://technorati.com/tag/Quick+Ruby" rel="tag"></a><a href="http://technorati.com/tag/Instant+Rails" rel="tag"></a><a href="http://technorati.com/tag/Pune+Ruby" rel="tag"></a><a href="http://technorati.com/tag/Quick+Ruby+Guide" rel="tag"></a><a href="http://technorati.com/tag/Programming+Languages" rel="tag"></a><a href="http://technorati.com/tag/Blogs" rel="tag"></a><a href="http://technorati.com/tag/Ruby" rel="tag"></a><a href="http://technorati.com/tag/PuneRuby" rel="tag"></a><a href="http://technorati.com/tag/QuickRuby" rel="tag"></a><a href="http://technorati.com/tag/PuneBloggers" rel="tag"></a><a href="http://technorati.com/tag/PuneBlogs" rel="tag"></a><a href="http://technorati.com/tag/Blogosphere" rel="tag"></a><a href="http://technorati.com/tag/Digg" rel="tag"></a><a href="http://technorati.com/tag/Media" rel="tag"></a><a href="http://technorati.com/tag/Tip" rel="tag"></a><a href="http://technorati.com/tag/RSS" rel="tag"></a><a href="http://technorati.com/tag/Marketing" rel="tag"></a><a href="http://technorati.com/tag/News" rel="tag"></a><a href="http://technorati.com/tag/IndianGuru" rel="tag"></a><a href="http://technorati.com/tag/Blogging" rel="tag"></a><a href="http://technorati.com/tag/Internet" rel="tag"></a><a href="http://technorati.com/tag/Blog" rel="tag"></a><a href="http://technorati.com/tag/Technical+Support" rel="tag"></a><a href="http://technorati.com/tag/Free+Software" rel="tag"></a><a href="http://technorati.com/tag/Help" rel="tag"></a><a href="http://technorati.com/tag/Pune" rel="tag"></a><a href="http://technorati.com/tag/SatishTalim" rel="tag"></a><a href="http://technorati.com/tag/Satish+Talim" rel="tag"></a><a href="http://technorati.com/tag/Weblog" rel="tag"></a><a href="http://technorati.com/tag/Weblogs" rel="tag"></a><a href="http://technorati.com/tag/Training" rel="tag"></a><a href="http://technorati.com/tag/Free+Training" rel="tag"></a><a href="http://technorati.com/tag/Tutorial" rel="tag"></a><a href="http://technorati.com/tag/Education" rel="tag"></a><a href="http://technorati.com/tag/Teacher" rel="tag"></a><a href="http://technorati.com/tag/Learning+Ruby" rel="tag"></a>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Connect+JRuby+to+MySQL+using+JDBC" rel="tag">Connect JRuby to MySQL using JDBC</a>, <a href="http://technorati.com/tag/Java" rel="tag">Java</a>, <a href="http://technorati.com/tag/JDBC" rel="tag">JDBC</a>, <a href="http://technorati.com/tag/JRuby" rel="tag">JRuby</a>, <a href="http://technorati.com/tag/MySQL" rel="tag">MySQL</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>
