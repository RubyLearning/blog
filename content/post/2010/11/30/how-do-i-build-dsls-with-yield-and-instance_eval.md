---
title: How do I build DSLs with yield and instance_eval?
date: 2010-11-30
author: Michael Bleigh
categories:
  - Beginners
  - Ruby
  - Ruby Masters
layout: post
permalink: /2010/11/30/how-do-i-build-dsls-with-yield-and-instance_eval/
tags:
  - DSL
  - programming
  - ruby programming
---
This guest post is by **Michael Bleigh**, a Rubyist developing web
applications and more for [Intridea](http://intridea.com/) from his
hometown of Kansas City. He is a prolific member of the open-source and
Ruby communities, releasing such projects as <!--more-->
[OmniAuth](https://github.com/intridea/omniauth) and
[Hashie](https://github.com/intridea/hashie). In addition, he has
presented at many Ruby events including RubyConf 2010, RailsConf
2009/2010 and more. While he spends much of his time writing Ruby code,
he also enjoys graphic design and user experience work.

![Michael
Bleigh](http://rubylearning.com/images/MichaelBleigh.jpg "Michael Bleigh")

## Domain Specific Language Introduction
Ruby provides some fantastic built-in features for creating **Domain
Specific Languages (DSLs)**. A Domain Specific Language is, for our
purposes today, like a miniature specialized programming language within
a programming language. It is a way to expose functionality in a simple,
readable format for other programmers (or yourself) to use. One of the
most commonly used DSLs in the Ruby world is
[Sinatra](http://www.sinatrarb.com/):

```ruby
require 'rubygems'
require 'sinatra'

get '/hello' do
  "Hello world."
end
```

Sinatra is a Domain Specific Language for building web applications. Its
syntax is built based on the [HTTP
verbs](http://en.wikipedia.org/wiki/HTTP_Verbs#Request_methods) such as
`GET`, `POST`, and `PUT`. By exposing functionality in this way, the
code is much more readable than using a more complex, programmatic API
such as something like this:

```ruby
app = NoDSL::Application.new

app.on_request(:get, :path_info => '/hello') do |response|
  response.body = "Hello world."
end
```

This is far less readable than Sinatra’s code, but in many programming
languages this would be a perfectly acceptable design for a library.
However, because Ruby has powerful facilities for
**[metaprogramming](http://en.wikipedia.org/wiki/Metaprogramming)** and
**[first-class
functions](http://en.wikipedia.org/wiki/First-class_function)**, it is
not only common practice but essentially expected for libraries to
provide clean, readable APIs and leverage DSLs when necessary to do so.

## Yield to Oncoming Code

The `yield` statement is a very important concept to understand when
building a Ruby DSL. The functionality provided by `yield` allows a
developer to pass off control temporarily to allow for configuration or
advanced functionality. Yielding is a pattern that completely pervades
the Ruby language, including the Ruby standard library (the
functionality included with the language itself). If you’ve ever used
the `Array#map` (or `Array#collect`) functionality, that’s one example
of a `yield` pattern. An example use to increment all the items in an
array would look like this:

    [1, 2, 3].map{|i| i + 1} # => [2, 3, 4]

So how would we re-implement the `map` functionality if it weren’t
provided for us? It’s actually quite simple using the `yield` statement:

```ruby
class Array
  def my_map
    result = []
    self.each do |item|
      result << yield(item)
    end
    result
  end
end

[1, 2, 3].my_map{|i| i + 1} # => [2, 3, 4]
```

The `yield` statement essentially stops the evaluation of the method and
evaluates the block passed into the method, calling it with any
arguments supplied in the `yield` statement itself. So if I had a method
that simply yielded its argument, it would look like this:

```ruby
def parrot(argument)
  yield argument
end

parrot("Polly want a cracker.") do |argument|
  puts argument
end

# Output: "Polly want a cracker."
```

### Using `yield` for DSLs

Now, using `yield`, we have the facilities to build a simple DSL. Let’s
say we want to create a Domain Specific Language for describing kitchen
recipes. We want to be able to add ingredients as well as steps, then
print out the result. Our basic class would look something like this:

```ruby
class Recipe
  attr_accessor :name, :ingredients, :instructions

  def initialize(name)
    self.name = name
    self.ingredients = []
    self.instructions = []
  end

  def to_s
    output = name
    output << "\n#{'=' * name.size}\n\n"
    output << "Ingredients: #{ingredients.join(', ')}\n\n"

    instructions.each_with_index do |instruction, index|
      output << "#{index + 1}) #{instruction}\n"
    end

    output
  end
end
```

Now we can build a recipe:

```text
mac_and_cheese = Recipe.new("Mac and Cheese")

mac_and_cheese.ingredients << "Noodles"
mac_and_cheese.ingredients << "Water"
mac_and_cheese.ingredients << "Cheese"

mac_and_cheese.instructions << "Boil water."
mac_and_cheese.instructions << "Add noodles, boil for six minutes."
mac_and_cheese.instructions << "Drain water."
mac_and_cheese.instructions << "Mix in cheese with noodles."
```

The output of ‘`puts mac_and_cheese`’ will look like this:

```text
Mac and Cheese
==============

Ingredients: Noodles, Water, Cheese

1) Heat water to boiling.
2) Add noodles, boil for six minutes.
3) Drain water.
4) Mix in cheese with noodles.
```

While this works, the code doesn’t seem to be very elegant at all! We
need a way to make it look more like you would see on a recipe card.
Let’s add some functionality using `yield`. First, we’ll rewrite the
initializer to use `yield`:

```ruby
def initialize(name)
  self.name = name
  self.ingredients = []
  self.instructions = []

  yield self
end
```

Upon initialization, the `Recipe` class will now `yield` itself, meaning
that the caller can call modify it within a block context. Next, we need
to add some friendly methods for adding ingredients and instructions to
the class:

```ruby
def ingredient(name, options = {})
  ingredient = name
  ingredient << " (#{options[:amount]})" if options[:amount]

  ingredients << ingredient
end

def step(text, options = {})
  instruction = text
  instruction << " (#{options[:for]})" if options[:for]

  instructions << instruction
end
```

This lets us create a recipe in a much more natural way:

```ruby
mac_and_cheese = Recipe.new("Mac and Cheese") do |r|
  r.ingredient "Water", :amount => "2 cups"
  r.ingredient "Noodles", :amount => "1 cup"
  r.ingredient "Cheese", :amount => "1/2 cup"

  r.step "Heat water to boiling.", :for => "5 minutes"
  r.step "Add noodles to boiling water.", :for => "6 minutes"
  r.step "Drain water."
  r.step "Mix cheese in with noodles."
end
```

Once again, if we run ‘`puts mac_and_cheese`’ we can see the results of
our handiwork:

```text
Mac and Cheese
==============

Ingredients: Water (2 cups), Noodles (1 cup), Cheese (1/2 cup)

1) Heat water to boiling. (5 minutes)
2) Add noodles to boiling water. (6 minutes)
3) Drain water.
4) Mix cheese in with noodles.
```

Great! Not only do we have more functionality (allowing the user to
specify amounts of ingredients and durations for instructions), but this
looks a lot closer to something you might see on a recipe card.

Using `yield` is a great way to provide a simple configuration DSL and
it takes almost no extra effort. However, to really take a DSL to the
next level, you may be interested in utilizing another piece of the Ruby
language called `instance_eval`.

## Kicking It Up A Notch With `instance_eval`

While almost all programming languages give an `eval` function for
evaluating a provided string as though it were source code, Ruby’s
powerful blocks allow you to do this in a much cleaner and more readable
fashion in some specific cases. For our purposes today, we’ll be using
`instance_eval`. The `instance_eval` method takes either a string or a
block and evaluates the passed block in the context of the object
calling `instance_eval`. You can do this with any object in Ruby, even a
String:

```ruby
"Hello.".instance_eval{ size } # => 6
```

This provides a distinct advantage, in some ways, over `yield` by
actually changing the evaluation context so that there’s no need to
specify the object in question for each statement (e.g. `r.ingredient`).
You can see an `instance_eval` based DSL in action if you’ve used the
[Rails 3 Router](http://guides.rubyonrails.org/routing.html). However,
the Rails 2.3 router was based on `yield` (thus `map.resources` instead
of just `resources`).

### Caveat Eval

While `instance_eval` may be a good option (and even the correct one)
for a specific DSL you are working on, it is not an universally useful
tool. Because `instance_eval` changes the evaluation context, you will
lose access to methods on the calling context (because `self` changes)
as well as expose private methods of the evaluating object that you may
not have intended to be accessible. Remember that whenever you use
`instance_eval`, the code passed in is treated as though it were being
written into a method body of the object. A simple example of this:

```ruby
def me
  "Michael Bleigh"
end

class YieldDSL
  attr_accessor :name
  def initialize
    yield self
  end
end

class EvalDSL
  attr_accessor :name
  def initialize(&block)
    instance_eval &block
  end
end

YieldDSL.new do |d|
  d.name = me
end
# => #<YieldDSL:0x101771bc0 @name="Michael">

EvalDSL.new do
  self.name = me
end
# EXCEPTION: NoMethodError
```

So it is wise to be careful when providing an `instance_eval` based DSL,
as it may not always be more beneficial for the user. A simpler syntax
comes at the cost of changing evaluation context.

### Building Recipes with `instance_eval`

In our case for building Recipes, however, there isn’t danger in
switching context. We’re mostly passing in strings and it’s unlikely
that any complex context is going to be associated. So let’s upgrade it!
All we need to do is redefine the initializer once more:

```ruby
def initialize(name, &block)
  self.name = name
  self.ingredients = []
  self.instructions = []

  instance_eval &block
end
```

Ruby has a convention that the last argument passed to a method is a
block that can be captured in the method by using an ampersand (`&`)
character with a variable name. In this way, we have direct access to
the block (whereas before with `yield` we were making an implicit call
to the block). You can also use the built-in `block_given?` method to
check whether or not a block was passed into the method you’re currently
evaluating. This should be done instead of checking for `block.nil?` or
similar.

So what can we do with our fancy new `instance_eval` DSL? We can define
a recipe with an even prettier syntax!

```
mac_and_cheese = Recipe.new("Mac and Cheese") do
  ingredient "Water", :amount => "2 cups"
  ingredient "Noodles", :amount => "1 cup"
  ingredient "Cheese", :amount => "1/2 cup"

  step "Heat water to boiling.", :for => "5 minutes"
  step "Add noodles to boiling water.", :for => "6 minutes"
  step "Drain water."
  step "Mix cheese in with noodles."
end
```

And if we run ‘`puts mac_and_cheese`’, we get the same results as
before.


## Finishing Up

So now you should have some basic idea of how to build DSLs in Ruby
using `yield` and `instance_eval`. The ability to expose functionality
in a concise, easily-readable way is a very useful weapon for your
programming arsenal. Before we wrap, let’s take a look at a couple more
things:

### Having AND Eating Cake

There’s no reason that `yield` and `instance_eval` DSLs need to be
mutually exclusive. Far from it! In Ruby we encourage options, and it’s
actually quite easy to provide a way to `yield` OR `instance_eval` based
on the block passed in:

```ruby
def initialize(&block)
  if block_given?
    if block.arity == 1
      yield self
    else
      instance_eval &block
    end
  end
end
```

What this snippet does is check the **arity** (number of arguments) of
the block that’s passed in. If it’s one (meaning that they’re asking for
something to be passed to the block) then we use the `yield` DSL
strategy. Otherwise, we use the `instance_eval` strategy. That wasn’t so
hard, was it?

### Advanced DSLs with Treetop

The DSLs covered in this article so far have been **internal DSLs**,
that is, DSLs that are executed inside the context of Ruby code.
However, it is also possible to build **external DSLs** that do not have
to contain any Ruby code at all! For example,
[Cucumber](http://cukes.info/), the integration testing framework, is an
external **Natural Language DSL**. Rather than being wrapped in Ruby
idioms, it actually defines its own language that is executed entirely
outside the context of the Ruby programming language.

The most popular library for building Natural Language DSLs in Ruby is
[Treetop](http://treetop.rubyforge.org/), which lets you create
**grammars** upon which a new Domain Specific Language can be crafted.
It’s a highly interesting library with some amazing facilities, so be
sure to check it out!

### Conclusion

I hope that this introduction to `yield` and `instance_eval` has shown
you just how easy it can be to build Domain Specific Languages in Ruby.
The next time you find yourself repeatedly building the same kind of
objects over and over, you might consider making a DSL to streamline the
process as well as improving readability.

*Feel free to ask questions and give feedback in the comments section of
this post. Thanks and Good Luck!*

