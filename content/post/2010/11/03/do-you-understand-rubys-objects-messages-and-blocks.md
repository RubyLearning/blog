---
draft: false
title: Do You Understand Ruby's Objects, Messages and Blocks?
date: 2010-11-03
author: Ed Howland
categories:
- beginners
- ruby
- ruby masters
layout: post
permalink: /2010/11/03/do-you-understand-rubys-objects-messages-and-blocks/
tags:
- programming
- ruby blocks
- ruby messages
- ruby objects
- ruby programming
---
This guest post is by **[Ed Howland](http://greenprogrammer.wordpress.com/)**,
an independent consultant who has worked in Ruby and RoR for more than 5 years,
since the 0.13 days of Rails. He has over 22 years in the software development
industry<!--more--> working on mainly O-O projects in C/C++, Java, Perl and
PHP. Ed is a frequent speaker at regional conferences and local Ruby/Linux user
groups.

## Introduction

![Ed
Howland](http://rubylearning.com/images/ed_howland.jpg "Ed Howland")
Ruby is a very elegant and expressive language. Consider the following
complete Ruby program (one of the first examples I was exposed to,
reconstructed from memory):

    #!/usr/bin/env ruby
    Dir[ARGV.first+'/*'].each {|f| File.rename f, f.downcase}

Running `./rename.rb .` will rename all files in the current directory
into their lowercase equivalents. Useful for importing a DOS/Windows
directory to Linux. When I showed this to my friend Mark, an IT pro, he
grokked it immediately.

But how does it work?

Actually, all that is going on here is a bunch of Ruby objects that are
talking to each other. By deconstructing Ruby’s object-message protocol,
we can analyze almost any Ruby code and discover how it works
internally.

## Objects

In Ruby, nearly everything is an object. Classically object-oriented
languages define an object as something that maintains state and
exhibits behavior. While this is true in Ruby, I think it is more
precise to say that Ruby objects contain other objects and respond to
messages. You might say that Ruby is a ‘message oriented’ language.

## Messages

    :message [payload1, ... payloadN]

A Ruby message consists of a name, usually represented by a symbol such
as :message, and an optional payload. The payload is often called the
list of arguments or parameters. The payload, if present, is a list of
other objects.

When the object receives the message, it handles it and returns some
other object. Each object has a number of message handlers corresponding
to the messages it responds to. In the Ruby program above, the fragment
`f.downcase`, the ‘f’ variable, which is a string containing the current
filename, is sent the message `:downcase`, and it returns a new string
that is converted to lowercase.

Some other messages:

    1.send :+, 2
    1.+ 2       # same thing
    1 + 2       # same thing

You can use the `send` method on any object to invoke a message handler.
Ruby gives us a lot of syntax sugar to make it easy to express messages.
We don’t need to use the `send` method, we can just use the shortcut ‘.’
(dot) operator.

Ruby also provides some other syntactic sugar. In some cases, we can
just use the message name inline, as in `1 + 2`. In another case, the
:[] message can have its payload embedded between the braces. `Dir['*']`
is the same as `Dir.[]('*')`. There is also the ‘=’ message, which can
be appended to another message name, such as an instance variable setter
and then used inline. `a.iv=(13)` is the same as `a.iv = 13`. (This is
what happens when you use the `attr_writer` to declare an instance
variable set method.)

The payload of a message can be defined as having (in this sequence)
required arguments, optional (or default) arguments, a variable number
of arguments and an implicit or explicit block. Default arguments are
specified with `arg=value`. The variable arguments are collected in
‘‘splatted’ (‘\*’) parameter. In the message handler, every actual
argument is collected in a list.

The explicit block argument is declared with a preceding ‘&’, as in
`&blk`. Default arguments are often used to emulate named parameters to
a message handler. Setting a parameter to the empty hash: `{}` lets us
pass in a (bare) hash as the last parameter:
`object.method :find=>true, :query=>'fred'`. You see that in a lot of
Rails code.

Here is a complete example:

    def message required, default={}, *variable, █

We can query an object to see if it understands a certain message, with
the :responds\_to? message.

    "AAAAA".respond_to? :downcase
     => true

How does an object handle a message? We first need to look at blocks, a
way to encapsulate Ruby code in an object. We will then expand that
concept to methods, another type of object that contains code.

## Blocks

A block is a special kind of object that contains executable code. In
fact, all Ruby code is evaluated in the context of a block. Many other
blocks can be declared and since they are just objects they can be used
like any object. Particularly, they can be passed in the payload of a
message.

There are a variety of synonyms for blocks: ‘lambdas’, ‘procs’ and
‘closures’. In most cases , , these refer to the same thing, an instance
of the `Proc` class. `Proc` objects understand a variety of messages,
the most significant of which is :call. The :call message invokes the
code in the block.

We can create a proc with any of the block keywords ‘proc’, ‘lambda’ and
‘-\>’ (the later form. ‘-\>’ is new to Ruby 1.9 and above). Another way
is to send the :new message to the `Proc` class itself. The code block
needs to be surrounded by curly braces ‘{}’ or by `do ... end`.

    p=proc {puts "in block"}
     => #<Proc:0x0000010095ca30@(irb):5>
    p.call
    in block

The :call message can have a payload like any other message. Inside the
block, these payload objects are bound to variables defined between ‘||’
in the front of the declaration. Collection iterators apply this
approach calling the passed in block once for every element in the
collection passing the element to the block. Let’s re-implement the
:join message with the :inject message.

    ["aa","bb", "cc"].inject(['','']) {|accum,v| [', ', accum[1]+accum[0]+v]}[1]
     => "aa, bb, cc"

The result of the last expression evaluated in the block is returned
from the :call invocation. You can also explicitly return an expression
with the `return` keyword at any point

Procs or lambdas are also closures. I admit, it took me a long time to
understand what that means. The most understandable closures I’ve seen
involve code that creates code based on passed in parameters. Assume we
want to make some micro-blogging formatters. We can combine some
functions to carry out a simple setup. (Remember that blocks passed in
are part of the saved context too.)

    mbmakr = proc do |&blk|
      proc {|*args| blk.call(*args)[0..139]}
    end

    tweetr = mbmakr.call {|msg| msg}
    reply = mbmakr.call {|user, msg| "@"+user+": "+msg}
    retweetr = mbmakr.call {|user, msg| 'RT '+reply.call(user, msg)}
    dmesgr= mbmakr.call {|user, msg| 'D '+user+' '+msg}

    retweetr.call "john_x", "French tomato soup is tasty! #protip"
     => "RT @john_x: French tomato soup is tasty! #protip"

Wow, code making code! C-3PO would be amazed.

The context captured by a block can be retrieved via the :binding
message. We can pass the binding object the :eval message and a string
containing some Ruby code. The code will be evaluated in the context of
the binding. This is very useful in templating systems, for example.
Passing the current binding to ERb, local variables will be interpreted
in the context of the template. Remember that the even the outermost
code is running in a block.

    require "erb"

    template=ERB.new "~ <%= a %> ~"
    a="hi there"
    template.result binding
     => "~ hi there ~"

Procs also can be queried as to their number of arguments with :arity
message. A bit out of our scope, so I refer you to the Proc class
documentation. We also will look at this a bit more when we discuss
Methods.

The last step on our journey to the actual implementation of a message
handler are ‘methods’.

## Methods

If we combine a block with a name and bind it to an owner (the *module*
to which it belongs) and a recipient (the *object* to which it belongs),
we get a message handler. These are called ‘methods’ which are objects
too. Methods objects can only exist in the context of a module. Modules
and classes are outside the scope of this article, but fortunately we
can get access to the current class with the combined message
`self.class`.

One way to create a method is to send the module object the
:define\_method message which takes a symbol for the method name and a
block containing the code to be executed when objects get that message.

    self.class.send(:define_method, :greet) {|user| puts "hello #{user}"}
     => #<Proc:0x000001008e4b48@(irb):78 (lambda)>
    greet "Fred"
    hello Fred

We can access the actual method object by sending the class the :method
message. Then we can query its attributes.

    m=self.class.method :greet
    => #<Method: Class(Object)#greet>
    puts m.name, m.owner, m.receiver
    greet
    Object
    Object

And, just like a block, we can invoke the method’s code block via its
:call message.

There is an easier way to define a method within a module: the
`def method args ... end` pattern:

    def who_am_i user
        "I am #{user}"
      end

Let’s combine all we have learned so far. Imagine we’d like a very
idiomatic Ruby way to create HTML text.

    def opt_to_s opt={}
      opt.empty? ? '' : ' ' + opt.map {|e,v| "#{e}=\"#{v}\""}.join(', ')
    end

    [:html, :body, :h1].each do |el|
      start="<#{el}"
      fin="</#{el}>"
      self.class.send(:define_method, el) {|options={}, &blk| start + opt_to_s(options) + '>' + blk.call + fin}
    end

    # Now, we can neatly nest tags and content
    html do
      body do
        h1 :class=>"bold-h1", :id=>"h1_99" do
          "header"
        end
      end
    end
     => "<html><body><h1 class=\"bold-h1\", id=\"h1_99\">header</h1></body></html>"

Inside the array’s `each` iterator. methods are created using a closure
containing the contracted start and fin tag fragments.

Ruby 1.9.2 gives you a nice way to query method object parameters.

    def x(a, b, c=3, *d, &e); end
    self.class.method(:x).parameters
     => [[:req, :a], [:req, :b], [:opt, :c], [:rest, :d], [:block, :e]]

This can also be accomplished with the ‘methopara’ gem in 1.9.1.

What happens when an object gets a message that it doesn’t understand?
Ruby will invoke the `:method_missing` message on that object. That
handler is defined in Object, but you can override it in your own
classes. Custom method\_missing handlers can lead to very dynamic code
that self adjusts to runtime conditions.

## Summary

The message-object protocol is fundamental to the way Ruby works.
Messages are sent to objects to perform some task. Within the object, a
message handler responds to the message and executes some code. Code
blocks or procs can be created and executed at any time. A method is an
enhancement of a proc that is bound to an object and named for the
message it handles. Examining this interaction between Ruby objects at
the message and block level leads to a deeper understanding of the way
Ruby works and should help you write more expressive code.

I urge you to explore the Proc, Module and Method class documentation
and experiment with creating your own blocks.

1.  As we will see when we discuss the ‘yield’ operator, inline blocks
    passed implicitly in a message call, is not really an instance of
    Proc. This is presumably a performance optimization.[↩](#fnref:1)

2.  There is also a subtle difference between the `proc` and `lambda`
    declarations. A lambda will throw an ArgumentError if the number of
    supplied arguments to :call do not match the number of required
    arguments, whereas proc will just set these to nil, or just drop any
    extra ones. Inline blocks behave more like procs than
    lambdas.[↩](#fnref:2)

*I hope you found this article valuable. Feel free to ask questions and
give feedback in the comments section of this post. Thanks!*

***Do also read* these awesome Guest Posts:**

-   [How Does One Use Design Patterns In
    Ruby?](http://rubylearning.com/blog/2010/11/02/how-does-one-use-design-patterns-in-ruby/)
-   [Do you know what’s new in Ruby
    1.9?](http://rubylearning.com/blog/2010/10/26/do-you-know-whats-new-in-ruby-1-9/)
-   [The value of a personal bug
    log](http://rubylearning.com/blog/2010/10/25/the-value-of-a-personal-bug-log/)
-   [Do You Enjoy Your Code
    Quality?](http://rubylearning.com/blog/2010/10/18/do-you-enjoy-your-code-quality/)

