---
author: Michael Bleigh
categories:
- Beginners
- Ruby
- Ruby Masters
date: 2010-11-30
layout: post
permalink: /2010/11/30/how-do-i-build-dsls-with-yield-and-instance_eval/
tags:
- DSL
- programming
- ruby programming
thesis_description:
- Learn how to make your code friendlier and more readable by creating APIs utilizing
  blocks, yielding values, and instance evaluation.
thesis_keywords:
- DSL,Programming,Ruby programming
title: How do I build DSLs with yield and instance_eval?
topsy_short_url:
- http://bit.ly/fOGlvW
---

<div>
  <h3 id="how_do_i_build_dsls_with_yield_and_instance_eval">
    How do I build DSLs with <code>yield</code> and <code>instance_eval</code>?
  </h3>
  
  <p class="update">
    This guest post is by <strong>Michael Bleigh</strong>, a Rubyist developing web applications and more for <a href="http://intridea.com/">Intridea</a> from his hometown of Kansas City. He is a prolific member of the open-source and Ruby communities, releasing such projects as <a href="https://github.com/intridea/omniauth">OmniAuth</a> and <a href="https://github.com/intridea/hashie">Hashie</a>. In addition, he has presented at many Ruby events including RubyConf 2010, RailsConf 2009/2010 and more. While he spends much of his time writing Ruby code, he also enjoys graphic design and user experience work.
  </p>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/MichaelBleigh.jpg" alt="Michael Bleigh" title="Michael Bleigh" /> <span class="drop_cap">R</span>uby provides some fantastic built-in features for creating <strong>Domain Specific Languages (DSLs)</strong>. A Domain Specific Language is, for our purposes today, like a miniature specialized programming language within a programming language. It is a way to expose functionality in a simple, readable format for other programmers (or yourself) to use. One of the most commonly used DSLs in the Ruby world is <a href="http://www.sinatrarb.com/">Sinatra</a>:
  </p>
  
  <pre>require 'rubygems'
require 'sinatra'

get '/hello' do
  "Hello world."
end
</pre>
  
  <p>
    Sinatra is a Domain Specific Language for building web applications. Its syntax is built based on the <a href="http://en.wikipedia.org/wiki/HTTP_Verbs#Request_methods">HTTP verbs</a> such as <code>GET</code>, <code>POST</code>, and <code>PUT</code>. By exposing functionality in this way, the code is much more readable than using a more complex, programmatic API such as something like this:
  </p>
  
  <pre>app = NoDSL::Application.new

app.on_request(:get, :path_info =&gt; '/hello') do |response|
  response.body = "Hello world."
end
</pre>
  
  <p>
    This is far less readable than Sinatra&#8217;s code, but in many programming languages this would be a perfectly acceptable design for a library. However, because Ruby has powerful facilities for <strong><a href="http://en.wikipedia.org/wiki/Metaprogramming">metaprogramming</a></strong> and <strong><a href="http://en.wikipedia.org/wiki/First-class_function">first-class functions</a></strong>, it is not only common practice but essentially expected for libraries to provide clean, readable APIs and leverage DSLs when necessary to do so.
  </p>
  
  <h3 id="yield_to_oncoming_code">
    Yield to Oncoming Code
  </h3>
  
  <p>
    The <code>yield</code> statement is a very important concept to understand when building a Ruby DSL. The functionality provided by <code>yield</code> allows a developer to pass off control temporarily to allow for configuration or advanced functionality. Yielding is a pattern that completely pervades the Ruby language, including the Ruby standard library (the functionality included with the language itself). If you&#8217;ve ever used the <code>Array#map</code> (or <code>Array#collect</code>) functionality, that&#8217;s one example of a <code>yield</code> pattern. An example use to increment all the items in an array would look like this:
  </p>
  
  <pre>[1, 2, 3].map{|i| i + 1} # =&gt; [2, 3, 4]
</pre>
  
  <p>
    So how would we re-implement the <code>map</code> functionality if it weren&#8217;t provided for us? It&#8217;s actually quite simple using the <code>yield</code> statement:
  </p>
  
  <pre>class Array
  def my_map
    result = []
    self.each do |item|
      result &lt;&lt; yield(item)
    end
    result
  end
end

[1, 2, 3].my_map{|i| i + 1} # =&gt; [2, 3, 4]
</pre>
  
  <p>
    The <code>yield</code> statement essentially stops the evaluation of the method and evaluates the block passed into the method, calling it with any arguments supplied in the <code>yield</code> statement itself. So if I had a method that simply yielded its argument, it would look like this:
  </p>
  
  <pre>def parrot(argument)
  yield argument
end

parrot("Polly want a cracker.") do |argument|
  puts argument
end

# Output: "Polly want a cracker."
</pre>
  
  <h4 id="using_yield_for_dsls">
    Using <code>yield</code> for DSLs
  </h4>
  
  <p>
    Now, using <code>yield</code>, we have the facilities to build a simple DSL. Let&#8217;s say we want to create a Domain Specific Language for describing kitchen recipes. We want to be able to add ingredients as well as steps, then print out the result. Our basic class would look something like this:
  </p>
  
  <pre>class Recipe
  attr_accessor :name, :ingredients, :instructions

  def initialize(name)
    self.name = name
    self.ingredients = []
    self.instructions = []
  end

  def to_s
    output = name
    output &lt;&lt; "\n#{'=' * name.size}\n\n"
    output &lt;&lt; "Ingredients: #{ingredients.join(', ')}\n\n"

    instructions.each_with_index do |instruction, index|
      output &lt;&lt; "#{index + 1}) #{instruction}\n"
    end

    output
  end
end
</pre>
  
  <p>
    Now we can build a recipe:
  </p>
  
  <pre>mac_and_cheese = Recipe.new("Mac and Cheese")

mac_and_cheese.ingredients &lt;&lt; "Noodles"
mac_and_cheese.ingredients &lt;&lt; "Water"
mac_and_cheese.ingredients &lt;&lt; "Cheese"

mac_and_cheese.instructions &lt;&lt; "Boil water."
mac_and_cheese.instructions &lt;&lt; "Add noodles, boil for six minutes."
mac_and_cheese.instructions &lt;&lt; "Drain water."
mac_and_cheese.instructions &lt;&lt; "Mix in cheese with noodles."
</pre>
  
  <p>
    The output of &#8216;<code>puts mac_and_cheese</code>&#8217; will look like this:
  </p>
  
  <pre>Mac and Cheese
==============

Ingredients: Noodles, Water, Cheese

1) Heat water to boiling.
2) Add noodles, boil for six minutes.
3) Drain water.
4) Mix in cheese with noodles.
</pre>
  
  <p>
    While this works, the code doesn&#8217;t seem to be very elegant at all! We need a way to make it look more like you would see on a recipe card. Let&#8217;s add some functionality using <code>yield</code>. First, we&#8217;ll rewrite the initializer to use <code>yield</code>:
  </p>
  
  <pre>def initialize(name)
  self.name = name
  self.ingredients = []
  self.instructions = []

  yield self
end
</pre>
  
  <p>
    Upon initialization, the <code>Recipe</code> class will now <code>yield</code> itself, meaning that the caller can call modify it within a block context. Next, we need to add some friendly methods for adding ingredients and instructions to the class:
  </p>
  
  <pre>def ingredient(name, options = {})
  ingredient = name
  ingredient &lt;&lt; " (#{options[:amount]})" if options[:amount]

  ingredients &lt;&lt; ingredient
end

def step(text, options = {})
  instruction = text
  instruction &lt;&lt; " (#{options[:for]})" if options[:for]

  instructions &lt;&lt; instruction
end
</pre>
  
  <p>
    This lets us create a recipe in a much more natural way:
  </p>
  
  <pre>mac_and_cheese = Recipe.new("Mac and Cheese") do |r|
  r.ingredient "Water", :amount =&gt; "2 cups"
  r.ingredient "Noodles", :amount =&gt; "1 cup"
  r.ingredient "Cheese", :amount =&gt; "1/2 cup"

  r.step "Heat water to boiling.", :for =&gt; "5 minutes"
  r.step "Add noodles to boiling water.", :for =&gt; "6 minutes"
  r.step "Drain water."
  r.step "Mix cheese in with noodles."
end
</pre>
  
  <p>
    Once again, if we run &#8216;<code>puts mac_and_cheese</code>&#8217; we can see the results of our handiwork:
  </p>
  
  <pre>Mac and Cheese
==============

Ingredients: Water (2 cups), Noodles (1 cup), Cheese (1/2 cup)

1) Heat water to boiling. (5 minutes)
2) Add noodles to boiling water. (6 minutes)
3) Drain water.
4) Mix cheese in with noodles.
</pre>
  
  <p>
    Great! Not only do we have more functionality (allowing the user to specify amounts of ingredients and durations for instructions), but this looks a lot closer to something you might see on a recipe card.
  </p>
  
  <p>
    Using <code>yield</code> is a great way to provide a simple configuration DSL and it takes almost no extra effort. However, to really take a DSL to the next level, you may be interested in utilizing another piece of the Ruby language called <code>instance_eval</code>.
  </p>
  
  <h3 id="kicking_it_up_a_notch_with_instance_eval">
    Kicking It Up A Notch With <code>instance_eval</code>
  </h3>
  
  <p>
    While almost all programming languages give an <code>eval</code> function for evaluating a provided string as though it were source code, Ruby&#8217;s powerful blocks allow you to do this in a much cleaner and more readable fashion in some specific cases. For our purposes today, we&#8217;ll be using <code>instance_eval</code>. The <code>instance_eval</code> method takes either a string or a block and evaluates the passed block in the context of the object calling <code>instance_eval</code>. You can do this with any object in Ruby, even a String:
  </p>
  
  <pre>"Hello.".instance_eval{ size } # =&gt; 6
</pre>
  
  <p>
    This provides a distinct advantage, in some ways, over <code>yield</code> by actually changing the evaluation context so that there&#8217;s no need to specify the object in question for each statement (e.g. <code>r.ingredient</code>). You can see an <code>instance_eval</code> based DSL in action if you&#8217;ve used the <a href="http://guides.rubyonrails.org/routing.html">Rails 3 Router</a>. However, the Rails 2.3 router was based on <code>yield</code> (thus <code>map.resources</code> instead of just <code>resources</code>).
  </p>
  
  <h4 id="caveat_eval">
    Caveat Eval
  </h4>
  
  <p>
    While <code>instance_eval</code> may be a good option (and even the correct one) for a specific DSL you are working on, it is not an universally useful tool. Because <code>instance_eval</code> changes the evaluation context, you will lose access to methods on the calling context (because <code>self</code> changes) as well as expose private methods of the evaluating object that you may not have intended to be accessible. Remember that whenever you use <code>instance_eval</code>, the code passed in is treated as though it were being written into a method body of the object. A simple example of this:
  </p>
  
  <pre>def me
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
# =&gt; #&lt;YieldDSL:0x101771bc0 @name="Michael"&gt;

EvalDSL.new do
  self.name = me
end
# EXCEPTION: NoMethodError
</pre>
  
  <p>
    So it is wise to be careful when providing an <code>instance_eval</code> based DSL, as it may not always be more beneficial for the user. A simpler syntax comes at the cost of changing evaluation context.
  </p>
  
  <h4 id="building_recipes_with_instance_eval">
    Building Recipes with <code>instance_eval</code>
  </h4>
  
  <p>
    In our case for building Recipes, however, there isn&#8217;t danger in switching context. We&#8217;re mostly passing in strings and it&#8217;s unlikely that any complex context is going to be associated. So let&#8217;s upgrade it! All we need to do is redefine the initializer once more:
  </p>
  
  <pre>def initialize(name, &block)
  self.name = name
  self.ingredients = []
  self.instructions = []

  instance_eval &block
end
</pre>
  
  <p>
    Ruby has a convention that the last argument passed to a method is a block that can be captured in the method by using an ampersand (<code>&</code>) character with a variable name. In this way, we have direct access to the block (whereas before with <code>yield</code> we were making an implicit call to the block). You can also use the built-in <code>block_given?</code> method to check whether or not a block was passed into the method you&#8217;re currently evaluating. This should be done instead of checking for <code>block.nil?</code> or similar.
  </p>
  
  <p>
    So what can we do with our fancy new <code>instance_eval</code> DSL? We can define a recipe with an even prettier syntax!
  </p>
  
  <pre>mac_and_cheese = Recipe.new("Mac and Cheese") do
  ingredient "Water", :amount =&gt; "2 cups"
  ingredient "Noodles", :amount =&gt; "1 cup"
  ingredient "Cheese", :amount =&gt; "1/2 cup"

  step "Heat water to boiling.", :for =&gt; "5 minutes"
  step "Add noodles to boiling water.", :for =&gt; "6 minutes"
  step "Drain water."
  step "Mix cheese in with noodles."
end
</pre>
  
  <p>
    And if we run &#8216;<code>puts mac_and_cheese</code>&#8217;, we get the same results as before.
  </p>
  
  <h3 id="finishing_up">
    Finishing Up
  </h3>
  
  <p>
    So now you should have some basic idea of how to build DSLs in Ruby using <code>yield</code> and <code>instance_eval</code>. The ability to expose functionality in a concise, easily-readable way is a very useful weapon for your programming arsenal. Before we wrap, let&#8217;s take a look at a couple more things:
  </p>
  
  <h4 id="having_and_eating_cake">
    Having AND Eating Cake
  </h4>
  
  <p>
    There&#8217;s no reason that <code>yield</code> and <code>instance_eval</code> DSLs need to be mutually exclusive. Far from it! In Ruby we encourage options, and it&#8217;s actually quite easy to provide a way to <code>yield</code> OR <code>instance_eval</code> based on the block passed in:
  </p>
  
  <pre>def initialize(&block)
  if block_given?
    if block.arity == 1
      yield self
    else
      instance_eval &block
    end
  end
end
</pre>
  
  <p>
    What this snippet does is check the <strong>arity</strong> (number of arguments) of the block that&#8217;s passed in. If it&#8217;s one (meaning that they&#8217;re asking for something to be passed to the block) then we use the <code>yield</code> DSL strategy. Otherwise, we use the <code>instance_eval</code> strategy. That wasn&#8217;t so hard, was it?
  </p>
  
  <h4 id="advanced_dsls_with_treetop">
    Advanced DSLs with Treetop
  </h4>
  
  <p>
    The DSLs covered in this article so far have been <strong>internal DSLs</strong>, that is, DSLs that are executed inside the context of Ruby code. However, it is also possible to build <strong>external DSLs</strong> that do not have to contain any Ruby code at all! For example, <a href="http://cukes.info/">Cucumber</a>, the integration testing framework, is an external <strong>Natural Language DSL</strong>. Rather than being wrapped in Ruby idioms, it actually defines its own language that is executed entirely outside the context of the Ruby programming language.
  </p>
  
  <p>
    The most popular library for building Natural Language DSLs in Ruby is <a href="http://treetop.rubyforge.org/">Treetop</a>, which lets you create <strong>grammars</strong> upon which a new Domain Specific Language can be crafted. It&#8217;s a highly interesting library with some amazing facilities, so be sure to check it out!
  </p>
  
  <h4 id="conclusion">
    Conclusion
  </h4>
  
  <p>
    I hope that this introduction to <code>yield</code> and <code>instance_eval</code> has shown you just how easy it can be to build Domain Specific Languages in Ruby. The next time you find yourself repeatedly building the same kind of objects over and over, you might consider making a DSL to streamline the process as well as improving readability.
  </p>
  
  <p>
    <em>Feel free to ask questions and give feedback in the comments section of this post. Thanks and Good Luck!</em>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/DSL" rel="tag">DSL</a>, <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>
