---
author: Satish Talim
categories:
- jruby
- ruby
date: 2008-07-30
layout: post
permalink: /2008/07/30/using-activerecord-and-jdbc-with-jruby-part-2/
tags:
- activerecord
- jdbc
- jruby
- mysql
- ruby
title: Using ActiveRecord and JDBC with JRuby - Part 2
topsy_short_url:
- http://bit.ly/aYNfE9
---

<div>
  <h3>
    Part 2
  </h3>
  
  <p>
  Continuing from where we left off in Part 1<!--more--> of the article &#8211; <strong><a href="http://rubylearning.com/blog/2008/07/28/using-activerecord-and-jdbc-with-jruby/">Using ActiveRecord and JDBC with JRuby</a></strong>, let us now create a database called <strong>students</strong> and a table called <strong>rubyists</strong> (this holds say, the names and cities of all those who have downloaded my <a href="http://jruby.rubylearning.org/">JRuby eBook</a>). To do this, open a command window and type:
  </p>
  
  <pre><code>mysql -u root</code></pre>
  
  <p>
    You should now get a mysql prompt. Next at the mysql prompt, type as follows:
  </p>
  
  <pre><code>mysql>create database students;</code></pre>
  
  <p>
    It will respond with:
  </p>
  
  <pre><code>Query OK, 1 row affected (0.00 sec)</code></pre>
  
  <p>
    Next, on the mysql prompt, type:
  </p>
  
  <pre><code>mysql>grant all on students.* to 'root'@'localhost';</code></pre>
  
  <p>
    Next let us create our table called <strong>rubyists</strong> by typing the following on the mysql prompt:
  </p>
  
  <pre><code>mysql>use students;
drop table if exists rubyists;  
create table rubyists (  
   id int not null auto_increment,  
   name varchar(100) not null,  
   city text not null,  
   primary key (id)  
);</code></pre>
  
  <p>
    We are through with the database creation. Now type:
  </p>
  
  <pre><code>mysql>exit</code></pre>
  
  <blockquote>
    <p>
      Generally speaking, managing changes to a database schema has been one of the most odious tasks for a team of developers. Most have relied on storing DDL in revision control, ever vigilant to ensure that our database creation scripts are updated and consistent with each rollout. That solution can be very clumsy in an Extreme Programming project. And because Rails encourages iterative development, it would be very easy to imagine the constant schema changes turning into nightmares. Fortunately, Migrations allows a developer to manage rollout, and rollback, of database schema changes in a controlled and consistent manner, and one that happens to feel very natural to a Rails programmer. However, Migrations is beyond the scope of this article. You can refer to these URLs for further information â€“<br /> <a href="http://api.rubyonrails.org/classes/ActiveRecord/Migration.html">http://api.rubyonrails.org/classes/ActiveRecord/Migration.html</a><br /> <a href="http://weblog.jamisbuck.org/2005/9/27/getting-started-with-activerecord-migrations">http://weblog.jamisbuck.org/2005/9/27/getting-started-with-activerecord-migrations</a><br /> <a href="http://glu.ttono.us/articles/2005/10/27/the-joy-of-migrations">http://glu.ttono.us/articles/2005/10/27/the-joy-of-migrations</a>
    </p>
  </blockquote>
  
  <p>
    <strong>ActiveRecord</strong> assumes that every table it handles has as its primary key an integer column called id internally, <strong>ActiveRecord</strong> uses the value in this column to keep track of the data it has loaded from the database and to link between data in different tables.<br />Now let us start writing the program <strong>jruby01.rb</strong>
  </p>
  
  <pre><code># jruby01.rb
require 'rubygems'
require 'active_record'

ActiveRecord::Base.establish_connection(
:adapter=> "jdbcmysql",
:host => "localhost",
:database=> "students",
:username => "root",
:password => ""
)

class Rubyist &lt; ActiveRecord::Base
end</code></pre>
  
  <p>
    So far, in the above code we are:
  </p>
  
  <ul>
    <li>
      Using the <strong>ActiveRecord</strong> library, available as the <strong>active_record</strong> gem
    </li>
    <li>
      Using the <strong>ActiveRecord</strong> adapter namely <strong>jdbcmysql</strong>
    </li>
    <li>
      Establishing a connection to the database students Please note if you have set a password say xyz for your database then make <strong>:password => &#8220;xyz&#8221;</strong>
    </li>
    <li>
      Creating a class called <strong>Rubyist</strong> When you create a subclass of <strong>ActiveRecord::Base</strong>, you&#8217;re creating something that wraps a database table. By default, <strong>ActiveRecord</strong> assumes that the name of the table is the plural form of the name of the class.
    </li>
  </ul>
  
  <p>
    Next we create entries in the table without writing any SQL. If you refer the <strong>ActiveRecord</strong> documentation, we can use the <strong>create</strong> method of <strong>ActiveRecord::Base</strong> (this method creates an object, and instantly saves it as a record) to do the same:
  </p>
  
  <pre><code>Rubyist.create(:name => 'Luc Juggery', :city => "Nashville, Tenessee")  
Rubyist.create(:name => 'Sunil Kelkar', :city => "Pune, India")  
Rubyist.create(:name => 'Adam Smith', :city => "San Fransisco, USA")</code></pre>
  
  <p>
    You can now query the table using <strong>find</strong> of <strong>ActiveRecord::Base</strong>
  </p>
  
  <pre><code>participant = Rubyist.find(:first) # returns the first object fetched by SELECT * FROM rubyists  
puts %{#{participant.name} stays in #{participant.city}}</code></pre>
  
  <p>
    You will observe <strong>ActiveRecord</strong> examines the database tables themselves to find out which columns are available. This is how we were able to use accessor methods for <strong>participant.name</strong> without explicitly defining them: we defined them in the database, and <strong>ActiveRecord</strong> picked them up.<br /> If you want to delete an item from the database, you can use the <strong>destroy</strong> (Deletes the record in the database) method of <strong>ActiveRecord::Base</strong> as shown:
  </p>
  
  <pre><code>Rubyist.find(:first).destroy</code></pre>
  
  <p>
    The complete program is:
  </p>
  
  <pre><code># jruby01.rb
require 'rubygems'
require 'active_record'

ActiveRecord::Base.establish_connection(
:adapter=> "jdbcmysql",
:host => "localhost",
:database=> "students",
:username => "root",
:password => ""
)

class Rubyist &lt; ActiveRecord::Base
end

Rubyist.create(:name => 'Mitali Talim', :city => "Nashville, Tenessee")
Rubyist.create(:name => 'Sunil Kelkar', :city => "Pune, India")
Rubyist.create(:name => 'Adam Smith', :city => "San Fransisco, USA")

participant = Rubyist.find(:first)
puts %{#{participant.name} stays in #{participant.city}}

Rubyist.find(:first).destroy</code></pre>
  
  <p>
    Run the program from the command prompt:
  </p>
  
  <pre><code>C:\jrubyprograms>jruby jruby01.rb</code></pre>
  
  <p>
    The output is:
  </p>
  
  <pre><code>Mitali Talim stays in Nashville, Tenessee</code></pre>
  
  <h3>
    References
  </h3>
  
  <ol>
    <li>
      <a href="http://rubylearning.com/blog/2008/07/21/charles-nutter-talks-to-rubylearning-participants/">Charles Nutter</a> Charles is an amazing guy! He eats, drinks and dreams JRuby &#8211; always available to help you out. No wonder JRuby is going places.
    </li>
    <li>
      <a href="http://caboo.se/doc/classes/ActiveRecord/Base.html">ActiveRecord::Base</a>
    </li>
  </ol>
</div>

Technorati Tags: <a href="http://technorati.com/tag/ActiveRecord" rel="tag">ActiveRecord</a>, <a href="http://technorati.com/tag/JDBC" rel="tag">JDBC</a>, <a href="http://technorati.com/tag/JRuby" rel="tag">JRuby</a>, <a href="http://technorati.com/tag/MySQL" rel="tag">MySQL</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>
