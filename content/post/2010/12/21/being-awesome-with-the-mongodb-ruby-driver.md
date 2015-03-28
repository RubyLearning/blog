---
draft: false
title: Being Awesome with the MongoDB Ruby Driver
date: 2010-12-21
author: Ethan Gunderson
categories:
- Beginners
- Ruby
- Ruby Masters
layout: post
permalink: /2010/12/21/being-awesome-with-the-mongodb-ruby-driver/
tags:
- MongoDB
- MongoDB Ruby Driver
- programming
- ruby programming
topsy_short_url:
- null
---

<div>
  <h3>
    Being Awesome with the MongoDB Ruby Driver
  </h3>
  
  <p class="update">
    This guest post is by <strong>Ethan Gunderson</strong>, who is a software developer living in Chicago. By day he is a developer at <a href="http://obtiva.com/">Obtiva</a>, where he helps clients deliver projects and be more awesome. By night, he is part of the <a href="http://gathers.us/">gathers.us</a> team, a co-organizer of <a href="http://chicagodb.gathers.us/">ChicagoDB</a>, and contributes when he can to the <a href="http://www.mongodb.org/">MongoDB</a> community. You can find him at <a href="http://ethangunderson.com/">ethangunderson.com</a>, or on Twitter as <a href="http://twitter.com/ethangunderson">@ethangunderson</a>.
  </p>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/avatar-small.png" alt="Ethan Gunderson" title="Ethan Gunderson" /> <a href="http://www.mongodb.org/">MongoDB</a> is fast becoming one of the more popular and widely used NoSQL databases, and rightfully so. Its flexible key/value store, powerful query language and sexy scaling options is enough to piqué any developers interest. While most Ruby developers may jump right into the warm embrace of the Active Record replacements Mongoid and MongoMapper, that often robs developers of a valuable learning experience.
  </p>
  
  <p>
    The <a href="http://www.mongodb.org/display/DOCS/Ruby+Language+Center">MongoDB Ruby driver</a> is not only simple to use, but it will get you familiar with how queries look and how they operate. Armed with this knowledge, moving into an <a href="http://en.wikipedia.org/wiki/Object-relational_mapping">ORM</a> becomes much easier. You&#8217;ll not only be able to understand what is abstracted away, but you&#8217;ll be able to spot bad and inefficient generated queries, making performance troubleshooting a snap. To help you hit the ground running, we&#8217;ll be building up some of common queries you would find in a common blog. Let&#8217;s get started!
  </p>
  
  <h4>
    Installation
  </h4>
  
  <p>
    Since the driver is just a gem, installation is simple:
  </p>
  
  <pre>(sudo) gem install mongo
</pre>
  
  <p>
    There is one more piece to install, bson_ext. Essentially, this is a collection of C extensions used to increase the speed of serialization. While this is optional, I recommend that you install it.
  </p>
  
  <pre>(sudo) gem install bson_ext
</pre>
  
  <p>
    Now that we have everything installed that we need, lets hop into some code and see what we can do.
  </p>
  
  <h4>
    Getting Started
  </h4>
  
  <p>
    First things first, we need a database connection. For the sake of simplicity, we&#8217;ll be using localhost with the default port.
  </p>
  
  <pre>require 'mongo'
include Mongo

db = Connection.new.db('ruby-learning')
</pre>
  
  <p>
    The next thing we&#8217;ll need is a place to store all of our posts. Let&#8217;s go ahead and get a post collection started.
  </p>
  
  <pre>posts = db.collection('posts')
</pre>
  
  <p>
    That&#8217;s it! If you notice, there are two things we *didn&#8217;t* do that are kind of cool: we didn&#8217;t create the database or the collection. In fact, neither still exist at the database level, and won&#8217;t until we insert some data.
  </p>
  
  <h4>
    Inserting & Updating Documents
  </h4>
  
  <p>
    Let&#8217;s get our blog rolling with a high quality post.
  </p>
  
  <pre>new_post = { :title => "RubyLearning.com, its awesome", :content => "This is a pretty sweet way to learn Ruby", :created_on => Time.now }
post_id = posts.insert(new_post)
</pre>
  
  <p>
    So, what did we just do? MongoDB stores its data as key/value pairs, which maps nicely to Ruby&#8217;s Hash. After creating a hash with our data, we inserted it into the posts collection, and in return, we received the <a href="http://www.mongodb.org/display/DOCS/Object+IDs">ObjectId</a> for the post from MongoDB. Pretty simple, right? It&#8217;s just as simple to update that document as well.
  </p>
  
  <pre>post = Posts.find( :_id => post_id ).first
post[:author] = "Ethan Gunderson"
posts.update( { :_id => post_id }, post )
</pre>
  
  <p>
    Using the ObjectId we got back from our insert query, we find that same document again. After changing the data as we see fit, we issue an update query. An update query takes two arguments, the first one is conditions used to find the document (just the ObjectId in our case), and the second is the data.
  </p>
  
  <p>
    While this works, it&#8217;s kind of silly if you think about it. We query the database for our document, change a small amount of information, and insert the entire document again. There&#8217;s gotta be a better way! Luckily, there is. MongoDB has the concept of <a href="http://www.mongodb.org/display/DOCS/Advanced+Queries">Query Operators</a>. One of these operators is <code>$set</code>, which allows you to, as I&#8217;m sure you can guess, set the value of an attribute.
  </p>
  
  <pre>posts.update( { :_id => post_id }, '$set' => { :author => 'Ethan Gunderson' } )
</pre>
  
  <p>
    Here, we supply our find conditions, similarly to our previous update, but instead of supplying the entire document, we just set the values we wish to change. Now, instead of having to issue two queries against the database, we can accomplish the same task in one query, and less code to boot.
  </p>
  
  <p>
    Now let&#8217;s take care of the post index page next.
  </p>
  
  <pre>posts = Posts.find
</pre>
  
  <p>
    If you run this, you&#8217;ll probably notice a problem. Most of the time, blogs list their posts in descending order. Let&#8217;s change our query to account for this.
  </p>
  
  <pre>posts.find.sort( [['_id', -1]] )
</pre>
  
  <p>
    This query has a couple of interesting points. Firstly, note that we are sorting on id. Since MongoDB&#8217;s ObjectId&#8217;s contain a timestamp, we can accurately sort based on that. This effectively removes the need for a created_at timestamp as well! Secondly, the sort parameter must always take an array of array, even if there is only one field you are sorting on.
  </p>
  
  <p>
    So, that wasn&#8217;t so hard, but pretty naïve. What happens when we have 1,000 posts? We don&#8217;t want to torture our visitors with a ridiculous page load time, so let&#8217;s trim that back.
  </p>
  
  <pre>posts.find.sort( [['_id', -1]] ).limit(5)
</pre>
  
  <p>
    Again, this was pretty simple, and by now you should be noticing a pattern. Building up relatively complex queries is just a matter of chaining methods together. To further this example, here&#8217;s a query showing a theoretical pagination query.
  </p>
  
  <pre>posts.find.sort( [['_id', -1]] ).limit(5).skip(5)
</pre>
  
  <h4>
    Tags
  </h4>
  
  <p>
    Another common element to blogs is the concept of tags. To accomplish this in our example, we&#8217;ll be adding an array of tags to our blog post.
  </p>
  
  <pre>post = Posts.find( :_id => post_id ).first
post[:tags] = ['mongo', 'nosql', 'awesome'] 
posts.update( { :_id => post_id }, post )
</pre>
  
  <p>
    Now lets find a post based on a specific tag.
  </p>
  
  <pre>posts.find( :tags => 'mongo' )
</pre>
  
  <p>
    It really doesn&#8217;t get more simple than that, folks. Now that the basic implementation is out-of-the-way, how do we find posts that match more than one tag? To accomplish this, we&#8217;ll be using another Query Operator called <code>$all</code>. As you can imagine, the <code>$all</code> operator specifies that selected documents contain all the elements in the supplied array.
  </p>
  
  <pre>posts.find( :tags => { '$all' => ['mongo', 'awesome'] } ) 
</pre>
  
  <p>
    To round out our tags feature, let&#8217;s build a query that will list all the unique tags in our system. There are a couple of ways to skin this particular cat, since we don&#8217;t need to do any aggregation, and it needs to be performant, we&#8217;ll be using <code>distinct</code>. Though, if we needed to also produce a count of tag occurrences, Map/Reduce may be a better option.
  </p>
  
  <pre>posts.distinct('tags')
</pre>
  
  <h4>
    Indexing
  </h4>
  
  <p>
    Now that our blog is starting to grow in complexity, we&#8217;ll need to start thinking about adding proper indexes. If you notice in our tags implementation, we&#8217;re now querying on an attribute that is not indexed. Let&#8217;s fix that.
  </p>
  
  <pre>posts.create_index('tags')
</pre>
  
  <p>
    And there we have it. In a relatively short amount of time, we&#8217;ve built up a lot of the common queries you would see in a standard blog. While I&#8217;ve only touched the surface of what you can accomplish with the MongoDB Ruby driver, I hope that I&#8217;ve shown you it&#8217;s power. I&#8217;ve included some more learning material and references below to continue your learning. <em>Of course, if you have any questions, feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
  
  <h4>
    References
  </h4>
  
  <ul>
    <li>
      <a href="https://github.com/chicagoruby/MongoDB_Koans">MongoDB Ruby Koans</a>
    </li>
    <li>
      <a href="http://api.mongodb.org/ruby/current/_index.html">MongoDB Ruby Documentation</a>
    </li>
  </ul>
</div>

