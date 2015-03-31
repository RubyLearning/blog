---
draft: false
title: Being Awesome with the MongoDB Ruby Driver
date: 2010-12-21
author: Ethan Gunderson
authorlink: http://twitter.com/ethangunderson
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
---
This guest post is by **Ethan Gunderson**, who is a software developer
living in Chicago. By day he is a developer at<!--more-->
[Obtiva](http://obtiva.com/), where he helps clients deliver projects
and be more awesome. By night, he is part of the
[gathers.us](http://gathers.us/) team, a co-organizer of
[ChicagoDB](http://chicagodb.gathers.us/), and contributes when he can
to the [MongoDB](http://www.mongodb.org/) community. You can find him at
[ethangunderson.com](http://ethangunderson.com/), or on Twitter as
[@ethangunderson](http://twitter.com/ethangunderson).

![Ethan Gunderson](http://rubylearning.com/images/avatar-small.png "Ethan Gunderson")

## Being Awesome with the MongoDB Ruby Driver

[MongoDB](http://www.mongodb.org/) is fast becoming one of the more
popular and widely used NoSQL databases, and rightfully so. Its flexible
key/value store, powerful query language and sexy scaling options is
enough to piqué any developers interest. While most Ruby developers may
jump right into the warm embrace of the Active Record replacements
Mongoid and MongoMapper, that often robs developers of a valuable
learning experience.

The [MongoDB Ruby
driver](http://www.mongodb.org/display/DOCS/Ruby+Language+Center) is not
only simple to use, but it will get you familiar with how queries look
and how they operate. Armed with this knowledge, moving into an
[ORM](http://en.wikipedia.org/wiki/Object-relational_mapping) becomes
much easier. You'll not only be able to understand what is abstracted
away, but you'll be able to spot bad and inefficient generated queries,
making performance troubleshooting a snap. To help you hit the ground
running, we'll be building up some of common queries you would find in a
common blog. Let's get started!

### Installation

Since the driver is just a gem, installation is simple:

    (sudo) gem install mongo

There is one more piece to install, bson\_ext. Essentially, this is a
collection of C extensions used to increase the speed of serialization.
While this is optional, I recommend that you install it.

    (sudo) gem install bson_ext

Now that we have everything installed that we need, lets hop into some
code and see what we can do.

### Getting Started

First things first, we need a database connection. For the sake of
simplicity, we'll be using localhost with the default port.

    require 'mongo'
    include Mongo

    db = Connection.new.db('ruby-learning')

The next thing we'll need is a place to store all of our posts. Let's go
ahead and get a post collection started.

    posts = db.collection('posts')

That's it! If you notice, there are two things we \*didn't\* do that are
kind of cool: we didn't create the database or the collection. In fact,
neither still exist at the database level, and won't until we insert
some data.

### Inserting & Updating Documents

Let's get our blog rolling with a high quality post.

    new_post = { :title => "RubyLearning.com, its awesome", :content => "This is a pretty sweet way to learn Ruby", :created_on => Time.now }
    post_id = posts.insert(new_post)

So, what did we just do? MongoDB stores its data as key/value pairs,
which maps nicely to Ruby's Hash. After creating a hash with our data,
we inserted it into the posts collection, and in return, we received the
[ObjectId](http://www.mongodb.org/display/DOCS/Object+IDs) for the post
from MongoDB. Pretty simple, right? It's just as simple to update that
document as well.

    post = Posts.find( :_id => post_id ).first
    post[:author] = "Ethan Gunderson"
    posts.update( { :_id => post_id }, post )

Using the ObjectId we got back from our insert query, we find that same
document again. After changing the data as we see fit, we issue an
update query. An update query takes two arguments, the first one is
conditions used to find the document (just the ObjectId in our case),
and the second is the data.

While this works, it's kind of silly if you think about it. We query the
database for our document, change a small amount of information, and
insert the entire document again. There's gotta be a better way!
Luckily, there is. MongoDB has the concept of [Query
Operators](http://www.mongodb.org/display/DOCS/Advanced+Queries). One of
these operators is `$set`, which allows you to, as I'm sure you can
guess, set the value of an attribute.

    posts.update( { :_id => post_id }, '$set' => { :author => 'Ethan Gunderson' } )

Here, we supply our find conditions, similarly to our previous update,
but instead of supplying the entire document, we just set the values we
wish to change. Now, instead of having to issue two queries against the
database, we can accomplish the same task in one query, and less code to
boot.

Now let's take care of the post index page next.

    posts = Posts.find

If you run this, you'll probably notice a problem. Most of the time,
blogs list their posts in descending order. Let's change our query to
account for this.

    posts.find.sort( [['_id', -1]] )

This query has a couple of interesting points. Firstly, note that we are
sorting on id. Since MongoDB's ObjectId's contain a timestamp, we can
accurately sort based on that. This effectively removes the need for a
created\_at timestamp as well! Secondly, the sort parameter must always
take an array of array, even if there is only one field you are sorting
on.

So, that wasn't so hard, but pretty naïve. What happens when we have
1,000 posts? We don't want to torture our visitors with a ridiculous
page load time, so let's trim that back.

    posts.find.sort( [['_id', -1]] ).limit(5)

Again, this was pretty simple, and by now you should be noticing a
pattern. Building up relatively complex queries is just a matter of
chaining methods together. To further this example, here's a query
showing a theoretical pagination query.

    posts.find.sort( [['_id', -1]] ).limit(5).skip(5)

### Tags

Another common element to blogs is the concept of tags. To accomplish
this in our example, we'll be adding an array of tags to our blog post.

    post = Posts.find( :_id => post_id ).first
    post[:tags] = ['mongo', 'nosql', 'awesome'] 
    posts.update( { :_id => post_id }, post )

Now lets find a post based on a specific tag.

    posts.find( :tags => 'mongo' )

It really doesn't get more simple than that, folks. Now that the basic
implementation is out-of-the-way, how do we find posts that match more
than one tag? To accomplish this, we'll be using another Query Operator
called `$all`. As you can imagine, the `$all` operator specifies that
selected documents contain all the elements in the supplied array.

    posts.find( :tags => { '$all' => ['mongo', 'awesome'] } ) 

To round out our tags feature, let's build a query that will list all
the unique tags in our system. There are a couple of ways to skin this
particular cat, since we don't need to do any aggregation, and it needs
to be performant, we'll be using `distinct`. Though, if we needed to
also produce a count of tag occurrences, Map/Reduce may be a better
option.

    posts.distinct('tags')

### Indexing

Now that our blog is starting to grow in complexity, we'll need to start
thinking about adding proper indexes. If you notice in our tags
implementation, we're now querying on an attribute that is not indexed.
Let's fix that.

    posts.create_index('tags')

And there we have it. In a relatively short amount of time, we've built
up a lot of the common queries you would see in a standard blog. While
I've only touched the surface of what you can accomplish with the
MongoDB Ruby driver, I hope that I've shown you it's power. I've
included some more learning material and references below to continue
your learning. *Of course, if you have any questions, feel free to ask
questions and give feedback in the comments section of this post.
Thanks!*

### References

-   [MongoDB Ruby Koans](https://github.com/chicagoruby/MongoDB_Koans)
-   [MongoDB Ruby
    Documentation](http://api.mongodb.org/ruby/current/_index.html)

