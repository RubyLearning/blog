---
author: Satish Talim
categories:
- beginners
- code snippets
- ruby
- training
- tricks
date: 2007-11-26
layout: post
title: '"AkitaOnRails" On Ruby Symbols'
---

*RubyLearning recently caught with **Fabio Akita** from Brazil and got
his viewpoint on one of the vexing areas for beginners in Ruby –
**Symbols**.*<!--more-->

![Fabio
Akita](http://www.rubylearning.com/images/akita.jpg "Fabio Akita")**Fabio
Akita** is a Brazilian Rails enthusiast, also known online as
“AkitaOnRails”. He regularly write posts on his own
[blog](http://www.akitaonrails.com/) and had published the very first
book tailored for the Brazilian audience called “Repensando a Web com
Rails”. He is now a full-time Ruby on Rails developer working as Brazil
Rails Practice Manager for the Utah company Surgeworks LLC.

Ruby is very similar to many other object oriented languages. You can
find similar constructs from non-dynamic languages as Java or C\#. On
the other hand, to start grasping all the possibilities of Ruby one has
to invest some time learning what we call ‘Rubyisms’. One example is
something called a \*symbol\*.

This is more obvious when you start learning Ruby through Rails. Much of
Rails power comes from the fact that it uses a lot of rubyisms. Let’s
see one example: (**Note**: You may want to brush up on
[Symbols](http://rubylearning.com/satishtalim/ruby_symbols.html) and
[ActiveRecord](http://rubylearning.com/satishtalim/ruby_activerecord_and_mysql.html)
before going through the examples that follow.)

    <span style="color:blue">class Transact < ActiveRecord::Base
      validates_presence_of :when
      validates_presence_of :category, :account
      validates_presence_of :value
      validates_numericality_of :value

      belongs_to :category
      belongs_to :account
    end</span>

‘class’ we understand, after all, the mainstream languages are
‘object-oriented’. But what are all those colons doing through all the
code? Those denote Symbols. More important, the colons represent
initializers of the class **Symbol**.

This can be quite confusing considering that the normal way of
initializing an object is:

    <span style="color:blue">Symbol.new</span>

The ‘**new**‘ call asks for the standard ‘**initialize**‘ method defined
within the class. Turns out that this method is private, the idea being
that all symbols should be instantiated with the colon notation.

Symbols are used as identifiers. Some other languages could simply use
Strings instead of Symbols. In Ruby, it would become something like
this:

    <span style="color:blue">class Transact < ActiveRecord::Base
      validates_presence_of "when"
      validates_presence_of "category", "account"
      validates_presence_of "value"
      validates_numericality_of "value"

      belongs_to "category"
      belongs_to "account"
    end</span>

Not so visually different: we got rid of the colons and went back to the
comfortable quotation marks. They look the same but behave differently.
Like Symbols in Ruby, Strings also have a special constructor. Instead
of doing:

    <span style="color:blue">String.new("category")</span>

We just do:

    <span style="color:blue">"category"</span>

One could call these kind of shortcuts as “eye-candy”, but the languages
would be pretty harsh without them. We use Strings all the time, and it
would be extremely painful to instantiate new Strings without this
special constructor: simply writing it between quotation marks.

The problem is, as Strings are easy to write, we overuse them more often
than not. There is an important side-effect: each new construct
instantiates a brand new object in memory, even though they have the
same content. For instance:

    <span style="color:blue">>> "category".object_id
    => 2953810

    >> "category".object_id
    => 2951340</span>

Here, we instantiate two strings with the same content. Each object in
memory has a unique ID so each string created above uses a separate
memory slot and have separate IDs. Now imagine that the same string
shows up in hundreds of different places throughout your project. You’re
definitely using more memory than necessary.

But, this is not a new problem. For that, we have another construct in
most languages called ‘constants’, Ruby included. We have to
conscientiously plan and pre-define several constants beforehand. So,
that’s how our previous example would be using memory efficient
constants:

    <span style="color:blue">class Transact < ActiveRecord::Base
      ACCOUNT = "account"
      CATEGORY = "category"
      VALUE = "value"
      WHEN = "when"

      validates_presence_of WHEN
      validates_presence_of CATEGORY, ACCOUNT
      validates_presence_of VALUE
      validates_numericality_of VALUE

      belongs_to CATEGORY
      belongs_to ACCOUNT
    end</span>

This works, but this is not nearly as nice. First of all, you have to
pre-define everything beforehand, either in the same class or a
separated module just for constants. Second, the code is less elegant,
less readable, thus, less maintainable.

So, we get back to the purpose of Symbols: being as memory efficient as
constants but as easy to the eyes as full fledged strings. Quotation
mark notation is already taken for Strings, capitalized words for
constants, dollar sign for global variables and so on. So, colon was a
good candidate.

Let’s see what it all means:

    <span style="color:blue">>> "string".object_id
    => 3001850
    >> "string".object_id
    => 2999540

    >> :string.object_id
    => 69618
    >> :string.object_id
    => 69618</span>

As we explained before, the first two strings have the same content and
look similar, but they do occupy different memory slots, allowing for
unnecessary duplication.

The last two symbols both are exactly the same thing. So I can call
identifiers as symbols through all my code without worrying about
duplication in memory. They are easy to initialize and easy to manage.

We can also transform a String into a Symbol and vice-versa:

    <span style="color:blue">>> "string".to_sym
    => :string
    >> :symbol.to_s
    => "symbol"</span>

One good place where this is put to good use is within Rails’
**ActiveSupport**. This package was made to extend the Ruby language,
and one such extension was made to the ubiquitous **Hash** class. Let’s
see an example:

    <span style="color:blue">>> params = { "id" => 1, "action" => "show" }
    => {"action"=>"show", "id"=>1}

    >> params["id"]
    => 1

    >> params.symbolize_keys!
    => {:id=>1, :action=>"show"}

    >> params[:id]
    => 1</span>

The first statement instantiates and populates a **Hash** (yet another
special initialization notation). The second statement asks for the
value identified by the key “id”, which is a string.

Instead of doing it this way, we can call the **symbolize\_keys!** to
transform all string keys into symbol keys. Now in the last statement we
can use the more usual Rails notation as symbol keys within a Hash. When
Rails receives a HTML Form post request, it only gets strings, so it is
its job to convert everything into meaningful Rails objects. If you’ve
been in the Rails world, you already saw this usage with controllers.

So, this is all to be said about Symbols: very simple constructs that
makes code more readable and more efficient at the same time, which is
compatible with the Ruby Way.

*Thank you Fabio for showing us a different perspective on Symbols. In
case you have any queries, questions on this article, kindly post your
questions here and Fabio would be glad to answer.*

Technorati Tags: [Brazil](http://technorati.com/tag/Brazil), [Fabio
Akita](http://technorati.com/tag/Fabio+Akita), [Ruby
Programming](http://technorati.com/tag/Ruby+Programming), [Ruby
Symbols](http://technorati.com/tag/Ruby+Symbols)
