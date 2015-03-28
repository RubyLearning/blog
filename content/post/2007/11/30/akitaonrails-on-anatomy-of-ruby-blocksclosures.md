---
draft: false
title: '"AkitaOnRails" On Anatomy of Ruby Blocks/Closures'
date: 2007-11-30
author: Fabio Akita
categories:
- beginners
- rails
- ruby
- training
layout: post
---

***Fabio Akita’s*** "AkitaOnRails" series at RubyLearning.com, for
would-be Ruby developers, has been quite a hit. Today in another
article, Fabio talks in depth about Ruby’s **Blocks/Closures**, This is
a rather long article but well worth the time invested in reading it.<!--more-->
The entire source code for the programs in this article is available
[here](http://tinyurl.com/2zjgjb).

![Fabio
Akita](http://www.rubylearning.com/images/akita.jpg "Fabio Akita")**Fabio
Akita** is a Brazilian Rails enthusiast, also known online as
“AkitaOnRails”. He regularly write posts on his own
[blog](http://www.akitaonrails.com/) and had published the very first
book tailored for the Brazilian audience called “Repensando a Web com
Rails”. He is now a full-time Ruby on Rails developer working as Brazil
Rails Practice Manager for the Utah company Surgeworks LLC.

**Note**: You may want to brush up on [Ruby Blocks and
Procs](http://rubylearning.com/satishtalim/ruby_blocks_and_procs.html)
before going through Fabio’s article.

**Fabio\>\>** There is no Rubyism more difficult to explain, than a
Closure. I could write an entire book about it. Instead of boring
everyone to death with academics, I’ll try to focus only on what one
really needs for day-to-day activities.

Let’s start with an example:

    # program1.rb
    for i in [1,2,3,4]
      puts i
    end

    a = 0
    b = [1,2,3,4]
    while a < b.length
      puts b[a]
      a += 1
    end

These are very simple iterators, similar to what we have in several
languages. The first one with a ‘**for**‘ construct and the second with
the familiar ‘**while**‘ statement. Nothing fancy here. But let’s see
another way of accomplishing the same thing in Ruby:

    # program2.rb
    [1,2,3,4].each { |i| puts i }

    [1,2,3,4].each do |i|
      puts i
    end

Not too shabby, simpler and elegant, but that’s where people start
gasping. The pipes notation is particularly threatening for
non-starters. Both the brackets and the do..end notations define an
enclosed piece of code that we name as ‘blocks’ or ‘closures’. What’s
between the pipes are like parameters to a method. It ‘feels’ like this
pseudo-code:

    def unnamed_method(i)
      puts i
    end

    [1,2,3,4].each(unnamed_method)

This is not valid Ruby code, of course. That’s similar to what we would
do in C\# with delegates. We have something similar in JavaScript (using
the "Prototype" [http://www.prototypejs.org/api/enumerable/each](http://www.prototypejs.org/api/enumerable/each)
library):

    [1,2,3,4].each(function(i) {
      alert(i);
    });

In Javascript functions are first-class citizens of the language and
they can be defined anonymously (without a name), and then passed as
parameters to another function. We can manipulate and move functions all
over the place.

Ruby doesn’t have methods as first-class citizens. We actually can
extract a method from an object and wrap it around a ‘**Method**‘
object, but it holds the context of its object, so it is not
independent.

    # program3.rb
    class Test
      def initialize
        @hello = "Hello!"
      end
      def say
        @hello
      end
    end

    m = Test.new.method(:say)
    puts m.call # => "Hello!"
    puts m.class # => "Method"

Here, we extracted the :say method from the instantiated Test instance.
Notice that we can now manipulate the method as a normal object.
Whenever we send the ‘**call**‘ message to the method object, it runs as
if it was being executed from the context of the original object
(Test.new.say). In the above example the second last statement would
successfully print “Hello!”, as stored in the local instance variable
@hello.

Although simple, we don’t do this very often. That’s because this method
is bound to the original object’s context and we don’t usually want
that: it would be nice to have an independent block of code. So, let’s
create one very simple block of code referenced by a variable:

    # program4.rb
    c = lambda { |i| puts i }
    c.call(1) # => 1
    c.call(2) # => 2

The ‘**lambda**‘ keyword encloses the code within brackets as an object
block, an instance of the **Proc** class. This object responds to the
‘**call**‘ method. In the last two statements we pass parameters to the
‘**call**‘ method and it goes to the ‘i’ variable defined within pipes
inside the block. So, it acts as an independent entity, detached from
any particular class. Let’s test it:

    # program5.rb
    c = lambda { |i| puts i }

    class Test
      def say(block)
        block.call(self.class)
      end
    end

    c.call(self.class) # => Object
    Test.new.say(c)    # => Test

We’re using the same block defined above in the variable ‘c’. After the
definition of the Test class, we call the block object passing
‘self.class’ and it returns **Object** as a result. Then, we call the
:say method from inside an instance of the Test class. The :say method
calls the block giving the inner ‘self.class’ as a block parameter. In
this case it prints out ‘Test’ instead of ‘**Object**‘, meaning that the
block binds itself to the enclosing scope. That’s one difference between
a block and a detached object method.

In many ways, Blocks resembles anonymous functions from Javascript,
anonymous delegates from C\#, anonymous inner classes from Java. This is
a very useful construct that was primarily created to better handle
iterators. For instance:

    # program6.rb
    [1,2,3,4].reverse_each { |i| puts i }
    # => 4 
    # => 3
    # => 2
    # => 1

Now, this is different from the Array’s ‘**each**‘ method we used
before. ‘**reverse\_each**‘ navigates backwards through the Array’s
elements. It gets each element and passes it into the ‘i’ variable, set
as a parameter for the block defined within brackets.

In languages like Java, everything has to be defined through an
interface. Enumerators are no different, and we have interfaces like
‘Iterator’. This method defines simple methods as ‘hasNext()’ and
‘next()’. But what if we actually need something as a reverse iterator?
Now we’re on our own. What if we need something more complicated like an
iterator that only walks through even elements? In Ruby we can define
such a method like this:

    # program7.rb
    class Array
      def even
        i = 0
        while i < self.size
          yield(self[i]) if i % 2 == 0
          i += 1
        end
      end
    end

    [1,2,3,4,5,6].even { |i| puts i }
    # => 1
    # => 3
    # => 5

First of all, remember that Ruby’s classes are all open, so we can
easily redefine the standard **Array** class and append new methods to
it. Now pay attention to the ‘even’ method. We implement it the usual
way with a ‘while’ loop. But the interesting bit is the ‘**yield**‘
keyword. Pretend that it works like a \*wildcard placeholder\* for
blocks. In the example, when we pass the ‘self[i]’ value as its
parameter, we’re actually passing this value to the ‘i’ parameter in the
block.

We can rewrite this method in a slightly different way but with the same
behavior:

    # program8.rb
    class Array
      def even(&code)
        i = 0
        while i < self.size
          code.call( self[i] ) if i % 2 == 0
          i += 1
        end
      end
    end

So, now we explicitly defined that the ‘even’ method expects to receive
a block, converting it to the ‘code’ parameter. Then, inside it we send
the ‘**call**‘ method to ‘code’ and pass ‘self[i]’ as its parameter. The
result is exactly the same as using the **yield** keyword.

We can still do it differently:

    # program9.rb
    class Array
      def even(block)
        i = 0
        while i < self.size
          block.call( self[i] ) if i % 2 == 0
          i += 1
        end
      end
    end

Now we’re doing it without the ampersand in the parameter. In the
previous example, the ampersand operator ‘captures’ a block into a
**Proc** instance object. In the latest example, the ‘even’ method
expects to directly receive a **Proc** object, like this:

    # program10.rb
    class Array
      def even(block)
        i = 0
        while i < self.size
          block.call( self[i] ) if i % 2 == 0
          i += 1
        end
      end
    end
    c = lambda { |i| puts i }
    [1,2,3,4,5,6].even( c )

Let’s go back to the Array’s ‘**each**‘ method as we displayed before:

    c = lambda { |i| puts i }
    [1,2,3,4].each( &c )

A little bit different, because the ‘**each**‘ method doesn’t expect a
**Proc** object as a parameter, but an actual Block. So we use the
ampersand before the **Proc** instance variable and it kind of ‘expands’
it back into a ‘raw’ code block, so that the ‘even’ method can ‘yield’
it inside, instead of executing through the ‘**call**‘ method.

This usage of a **Proc** object is not as elegant as just passing a
Block, but with this construct we are storing code within an object. We
can define a method that receives as many blocks as we need, for
instance:

    # program11.rb
    def foo(name, block1, block2)
      block1.call
      puts name
      block2.call
    end

    foo "Fabio", lambda { puts "Hello" }, lambda { puts "World" }

This example receives a normal parameter and 2 blocks instead of one. We
can pass blocks as enclosed **Proc** objects in the parameters list as
we would do with any other kind of object. We usually don’t need that
many discrete blocks inside a single method. The most usual style is:

    # program12.rb
    def foo( param1, param2 )
      # do something
      some_param = 1
      yield( some_param ) if block_given?
    end

    foo(1, 2) do |some_param|
      # do something
    end

So we define a normal method, with normal parameters. But inside it we
ask ‘**block\_given?**‘. If positive, it ‘yields’ its block passing some
parameter to it (of course, parameters are optional, and you can pass as
many parameters as you want to a block, even zero parameters).

We call the defined method as usual, passing a block at the end of the
method call. By the way, here’s another way of defining a block: using
the do .. end construct. There is no strict rule, but we reserve the
brackets notation when the block is small and we can state it in a
single line, and the do .. end notation when we have blocks with
multiple statements inside.

There’s a gotcha:

    foo a, b do |some_param|
      # do something
    end

    foo a, b { |some_param| # do something }

Both brackets and do .. end constructs define blocks, so at first glance
the 2 above statements seems to do the same thing. But the gotcha is
that in Ruby parenthesis are optional, and we’re not using them here.

In the first statement the block is assumed to be passed to the ‘foo’
method as expected, with ‘a’ and ‘b’ as normal parameters. But the
second statement guesses that ‘b’ is a method and tries to pass the
block to it. The recommendation is: if you have a method that needs both
parameters and a block, enclose the parameters within parenthesis to
avoid ambiguities.

We now understand that **Blocks are pieces of code that can be exchanged
between method calls, as parameters or returned values**. But there is
more to it:

    # program13.rb
    c = lambda { |i| puts i }
    c = Proc.new { |i| puts i }
    c = proc { |i| puts i }

The above 3 statements do the same thing: instantiate a block object.
‘proc’ is an alias for ‘**lambda**‘ and they work slightly different
than ‘**Proc.new**‘. In Ruby 1.9, ‘proc’ will probably be an alias for
‘**Proc.new**‘ instead.

**Keywords to keep in mind are**:

-   **lambda/Proc.new** – encloses a bunch of code inside a **Proc**
    instance.
-   & – ampersand, either captures a ‘raw’ code block into a **Proc**
    object or expands the **Proc** object as a ‘raw’ block.
-   {}/do..end – defines a code block.
-   || – pipes, defines the parameters of a block. If you don’t need
    any, just omit the pipes altogether.

So, some people misinterpret Blocks as a simple function pointer, or
something like Java’s anonymous inner class. That’s not the case: and
here we finally boil down to “Closures”. Ruby Blocks are Closures. The
words ‘blocks’ and ‘closures’ mean the same thing in Ruby.

Ruby Blocks can enclose not only code and it’s own inner local
variables, but it can enclose the surrounding context variables. That’s
why it is called a ‘closure’. Let’s see an example:

    # program14.rb
    def greetings_factory(prefix)
      Proc.new { |name| "#{prefix}, #{name} !"}
    end

    birthday = greetings_factory("Happy Birthday")
    xmas = greetings_factory("Merry XMas")

    puts birthday.call("David") # => "Happy Birthday, David !"
    puts xmas.call("Matz")      # => "Merry XMas, Matz !"

The first thing is a method definition for ‘greetings\_factory’. It gets
a prefix as a parameter and returns a **Proc** object, whose inner
parameter is a name. So far so good.

The second part defines 2 **Proc** instances, one for birthday and
another for christmas. Notice that we pass 2 different prefixes into the
‘greetings\_factory’ method. The different values are ‘closed’ within
Block. So, when we later call them, we see how differently they behave:
they actually stored the latest state within itself. So each block
stored the ‘prefix’ variable passed before, while still accepting the
‘name’ parameter within the Block.

Keep in mind that every Ruby Block is a Closure, that’s why this
construct actually works:

    # program15.rb
    list = []
    [1,2,3,4].each do |i| 
      list << i * 2 
    end
    puts list.inspect # => [2, 4, 6, 8]

So, we defined a ‘list’ array \*before\* we create the iterator block.
Then, inside the block we refer to the external ‘list’ array and
populate it. In Java, this would’ve been a final variable, but in Ruby
there is no such limitation.

You’d want to be very careful about the surroundings of your block: do
not define variables that’s going to be used inside the blocks too early
in the code. Try to keep dependencies nearby, like in the above example
where the ‘list’ Array is defined right before the iterator itself.

Iterators get a big boost because we’re not limited to a hard Interface.
We can add whatever methods we need, like ‘each’, ‘reverse\_each’,
‘collect’, ‘select’ and so on. Each one of them can receive a block and
pass one element at a time to the user-defined block.

Another very important usage is to enclose widely used code patterns.
For example, Rails has the following construct to use database
transactions:

    User.transaction do 
      u = User.new(:login => 'admin')
      u.save!
    end

‘User’ would be the **ActiveRecord** instance. One example of the
structure for the model’s ‘transaction’ class method would resemble this
structure:

    class ActiveRecord::Base
      def self.transaction
        begin
          ActiveRecord::Base.establish_connection
          yield if block_given?
        rescue => e
          RAILS_DEFAULT_LOGGER.error e
        ensure
          ActiveRecord::Base.remove_connection 
        end
      end
    end

This means: open the database then try to ‘yield’ the block if provided.
If anything wrong happens, get the error message and log it. Finally
ensure that the connection is dropped after all this.

**ActiveRecord** doesn’t open and close connections this often, but you
get the idea. But this is an overall big picture of one way to avoid
repetition and the extraction of common code patterns. So it’s clever to
encapsulate common functionality and place in a placeholder for
user-defined code in-between.

The **File.open** method does the same thing: it takes responsibility of
properly opening files, yielding the user block and ensuring that the
file is closed without the user having to manually do this kind of house
cleaning.

The most important
“concept”:[http://martinfowler.com/bliki/Closure.html](http://martinfowler.com/bliki/Closure.html)
is that Blocks helps hiding implementation details. We don’t want to
know the inner details of a list iterator, or how a transaction works.
We just need to focus on the business logic itself, trapped within a
Block.

We described here a lot of stuff, and I think it covers the basics.
Enough to actually read some of the Rails source-code and get acquainted
for closure’s modus operandi. Hope you enjoyed this article!

*Thank you Fabio for showing us a different perspective on Ruby Blocks.
In case you have any queries, questions on this article, kindly post
your questions here and Fabio would be glad to answer.*

