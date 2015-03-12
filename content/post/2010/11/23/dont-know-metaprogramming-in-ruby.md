---
author: Gavin Morrice
categories:
- beginners
- metaprogramming
- popular
- ruby
- ruby masters
date: 2010-11-23
dsq_thread_id:
- 208370854
layout: post
permalink: /2010/11/23/dont-know-metaprogramming-in-ruby/
tags:
- programming
- ruby metaprogramming
- ruby programming
thesis_description:
- Gavin Morrice introduces you to the beauty of metaprogramming in Ruby. A guest post
  on RubyLearning.
thesis_keywords:
- Ruby Metaprogramming,Programming,Ruby programming
title: Don't Know Metaprogramming In Ruby?
topsy_short_url:
- http://bit.ly/hAs5o8
---

<div>
  <h3>
    Don&#8217;t Know Metaprogramming In Ruby?
  </h3>
  
  <p class="update">
    This guest post is by <strong>Gavin Morrice</strong>, Managing Director of <a href="http://katanacode.com">Katana Code Ltd.</a>, a software boutique based in Edinburgh, Scotland. He likes sharing Rails tips on <a href="http://gavinmorrice.com/">his site</a>. When he&#8217;s not writing code he&#8217;s usually weightlifting, reading or writing
  </p>
  
  <h3 id="introduction">
    Introduction
  </h3>
  
  <p class="block">
    <img class="alignright" title="Gavin Morrice" src="http://rubylearning.com/images/GavinMorrice.jpg" alt="Gavin Morrice" /> <span class="drop_cap">O</span>ne of the most impressive aspects of Ruby is its metaprogramming capabilities. As a dynamic language, Ruby gives you the freedom to define methods and even classes during runtime. Metaprogramming with Ruby, one can do in a few minutes what other languages may take hours to do. By cleverly planning your code and applying the techniques mentioned here, you&#8217;ll be able to write code that is DRYer, lighter, more intuitive and more scalable.<br /> This tutorial assumes you are already familiar with the following concepts:
  </p>
  
  <ul>
    <li>
      Ruby Classes and class inheritance
    </li>
    <li>
      Instance methods and instance variables
    </li>
    <li>
      Raising exceptions
    </li>
  </ul>
  
  <p>
    and standard Ruby notations:
  </p>
  
  <pre>MyClass#method_name to show that method_name is a method in MyClass
# =&gt; to show the return value of a method
</pre>
  
  <h3>
    What is Metaprogramming?
  </h3>
  
  <p>
    According to Wikipedia:
  </p>
  
  <blockquote>
    <p>
      Metaprogramming is the writing of computer programs that write or manipulate other programs (or themselves) as their data, or that do part of the work at compile time that would otherwise be done at runtime. In many cases, this allows programmers to get more done in the same amount of time as they would take to write all the code manually, or it gives programs greater flexibility to efficiently handle new situations without recompilation. Or, more simply put: Metaprogramming is writing <strong>code that writes code</strong> during runtime to make your life easier.
    </p>
  </blockquote>
  
  <h3 id="object_context">
    Adding methods in the context of an object
  </h3>
  
  <p>
    In Ruby, <em>everything</em> is an object. The base class in Ruby is called <tt>Object</tt> (or <tt>BasicObject</tt> in Ruby 1.9) and all other classes inherit properties from it. Every object in Ruby has its own methods, and instance variables which can be added, edited or removed during runtime. Here is a simple example:
  </p>
  
  <pre># Example 1: create a new instance of class Object
my_object = Object.new

# define a method on my_object to set the instance variable @my_instance_variable
def my_object.set_my_variable=(var)
  @my_instance_variable = var
end

# define a method on my_object to return value of instance variable @my_instance_variable
def my_object.get_my_variable
  @my_instance_variable
end

my_object.set_my_variable = "Hello"
my_object.get_my_variable # =&gt; Hello
</pre>
  
  <p>
    In this example, we have created a new instance of the <tt>Object</tt> class and defined two methods on that instance for writing and reading (setting and getting). The two new methods that we&#8217;ve defined are only available to our object &#8220;my_object&#8221; and will not be present on any other instance of the <tt>Object</tt> class. We can prove this by extending our example like so:
  </p>
  
  <pre># Example 2: create a new instance of class Object
my_object = Object.new

# create a second instance of class Object
my_other_object = Object.new

# define a method on my_object to set the instance variable @my_instance_variable
def my_object.set_my_variable=(var)
  @my_instance_variable = var
end

# define a method on my_object to return value of instance variable @my_instance_variable
def my_object.get_my_variable
  @my_instance_variable
end

my_object.set_my_variable = "Hello"
my_object.get_my_variable # =&gt; Hello

my_other_object.get_my_variable = "Hello" # =&gt; NoMethodError
</pre>
  
  <p>
    When we try to call get_my_variable() on our second object &#8220;my_other_object&#8221; the interpreter raises a NoMethodError to tell us that &#8220;my_other_object&#8221; doesn&#8217;t recognise the method get_my_variable().
  </p>
  
  <p>
    To see where this feature of Ruby might be useful, let&#8217;s look at a more common example: writing class methods.
  </p>
  
  <h4>
    Writing Class Methods
  </h4>
  
  <p>
    You&#8217;ll probably already be aware of this common syntax for writing methods to your Ruby classes:
  </p>
  
  <pre># Example 3
class MyClass
  def self.capitalize_name
    name.upcase
  end
end
print MyClass.capitalize_name # =&gt; MYCLASS
</pre>
  
  <p>
    Within our class definition we&#8217;re defining a method on one particular object just like we did in Example 1. Only, this time the object is <em>self</em> (in this case MyClass). And as we saw in Example 2, the capitalize_name() method is only available to this particular object MyClass and no other class (yet). This is just one example of how to write a class method. To refer back to Example 3 again, here are three different approaches to defining the same class methods:
  </p>
  
  <pre># Example 4
# approach 1
class MyClass
  # defining a class method within the class definition
  def MyClass.capitalize_name
    name.upcase
  end
end

# approach 2
class MyClass;end
# defining a class method out with the class definition
def MyClass.capitalize_name
  name.upcase
end

# approach 3
# define a new class named MyClass
MyClass = Class.new
# add the capitalize_name to MyClass
def MyClass.capitalize_name
  name.upcase
end
</pre>
  
  <p>
    See how similar approach 3 here is to Example 1? You will hopefully have realised that when you write a class method in Ruby, it&#8217;s just the same as creating an instance of any class and adding methods only to that instance, only this time its an instance of the class &#8220;Class&#8221;.
  </p>
  
  <h3 id="writing_code_that_writes_code">
    Writing Code That Writes Code
  </h3>
  
  <p>
    An important philosophy in programming is DRY (Don&#8217;t Repeat Yourself). Writing code that is the same (or similar) several times is not only an inefficient waste of time, it can become a nightmare when you need to make changes in future. In many cases, it&#8217;s possible to remove this duplication of effort by writing code that writes the code for you. Here&#8217;s an example&#8230;<br /> Consider an application for a car manufacturer to store and access data on each of it&#8217;s models. Within the application we have a class called CarModel:
  </p>
  
  <pre># Example 5
class CarModel
  def engine_info=(info)
    @engine_info = info
  end

  def engine_info
    @engine_info
  end

  def engine_price=(price)
    @engine_price = price
  end

  def engine_price
    @engine_price
  end

  def wheel_info=(info)
    @wheel_info = info
  end

  def wheel_info
    @wheel_info
  end

  def wheel_price=(price)
    @wheel_price = price
  end

  def wheel_price
    @wheel_price
  end

  def airbag_info=(info)
    @airbag_info = info
  end

  def airbag_info
    @airbag_info
  end

  def airbag_price=(price)
    @airbag_price = price
  end

  def airbag_price
    @airbag_price
  end

  def alarm_info=(info)
    @alarm_info = info
  end

  def alarm_info
    @alarm_info
  end

  def alarm_price=(price)
    @alarm_price = price
  end

  def alarm_price
    @alarm_price
  end

  def stereo_info=(info)
    @stereo_info = info
  end

  def stereo_info
    @stereo_info
  end

  def stereo_price=(price)
    @stereo_price = price
  end

  def stereo_price
    @stereo_price
  end
end
</pre>
  
  <p>
    Each car model comes with various features such as &#8220;stereo&#8221;, &#8220;alarm&#8221; etc. We have a method to get and set the values of each feature of the car. Each feature has information and price so for every new feature we add to the CarModel class, we need to define two new methods: <em>feature</em>_info and <em>feature</em>_price.<br /> Since each of these methods are similar, we can do the following to simplify this code:
  </p>
  
  <pre># Example 6
class CarModel
  FEATURES = ["engine", "wheel", "airbag", "alarm", "stereo"]

  FEATURES.each do |feature|
    define_method("#{feature}_info=") do |info|
      instance_variable_set("@#{feature}_info", info)
    end

    define_method("#{feature}_info") do
      instance_variable_get("@#{feature}_info")
    end

    define_method "feature_price=" do |price|
      instance_variable_set("@#{feature}_price", price)
    end

    define_method("#{feature}_price") do
      instance_variable_get("@#{feature}_price")
    end
  end
end
</pre>
  
  <p>
    In this example, we start by defining an array called FEATURES which includes all the features we wish to add methods for. Then, for each feature, we use Ruby&#8217;s <a href="http://www.ruby-doc.org/core/classes/Module.html#M001654">Module#define_method</a> to define four methods for each feature. Just like in Example 5, the four methods are getter and setter methods for the feature&#8217;s price and info. The only difference is, they have been written dynamically when the class is defined and not by us. We use <a href="http://www.ruby-doc.org/core/classes/Object.html#M000368">Object#instance_variable_set()</a> to set the value of instance variables for each feature and <a href="http://www.ruby-doc.org/core/classes/Object.html#M000378">Object#instance_variable_get</a> to return the values for each.
  </p>
  
  <p>
    The need to define getter and setter methods like this is quite common in Ruby so it&#8217;s not surprising that Ruby already has methods that do just that. <tt>Module#attr_accessor</tt> can be used to do the same thing as in Example 6 with just a single line of code.
  </p>
  
  <pre># Example 7
class CarModel
  attr_accessor :engine_info, :engine_price, :wheel_info, :wheel_price, :airbag_info, :airbag_price, :alarm_info, :alarm_price, :stereo_info, :stereo_price
end
</pre>
  
  <p>
    Great! But this still isn&#8217;t ideal. For each feature, we still need to define two attributes (<em>feature</em>_info and <em>feature</em>_price). Ideally we should be able to call a method that can do the same as in Example 7 but by only listing each feature once.
  </p>
  
  <pre># Example 8
class CarModel
  # define a class macro for setting features
  def self.features(*args)
    args.each do |feature|
      attr_accessor "#{feature}_price", "#{feature}_info"
    end
  end

  # set _info and _price methods for each of these features
  features :engine, :wheel, :airbag, :alarm, :stereo
end
</pre>
  
  <p>
    In this example, we take each of the arguments for CarModel#features and pass them to <tt>attr_accessor</tt> with &#8220;_price&#8221; and &#8220;_info&#8221; extensions. Although this approach is slightly more involved than the one in Example 7, it ensures that each feature is treated the same and means that adding more attributes in future will be simpler.
  </p>
  
  <h3 id="ruby_object_model">
    A Brief Explanation of the Ruby Object Model
  </h3>
  
  <p>
    Before going any further, it&#8217;s important that we understand the basics of Ruby&#8217;s Object Model and how Ruby deals with method calls.<br /> Whenever you call a method on an object, the interpreter first looks through the object&#8217;s instance methods to see if it can find that method. If the interpreter can find the method, it will execute it as expected but if not, it will pass the request up the chain to the object&#8217;s class. If it can&#8217;t find the method there it will continue to look in that class&#8217;s parent class, then the parent&#8217;s parent etc. up to the <tt>Object</tt> class itself.<br /> But it doesn&#8217;t stop there&#8230;<br /> If the interpreter can&#8217;t find the method anywhere up the object&#8217;s chain of inheritance, it will go back to the object and call another method called <a href="http://www.ruby-doc.org/core/classes/Kernel.src/M005925.html">method_missing()</a>. Just like with our first method, the interpreter looks for <a href="http://www.ruby-doc.org/core/classes/Kernel.src/M005925.html">method_missing()</a> in the object&#8217;s methods, then the object&#8217;s class&#8217;s instance methods etc. until reaches the <tt>Object</tt> class where <a href="http://www.ruby-doc.org/core/classes/Kernel.src/M005925.html">method_missing()</a> <strong>is</strong> defined and will raise a NoMethodError error. This is when metaprogramming really starts getting fun!
  </p>
  
  <p>
    By defining <a href="http://www.ruby-doc.org/core/classes/Kernel.src/M005925.html">method_missing()</a> yourself within a class, it&#8217;s possible to change this default behaviour for some pretty useful effects. <a href="http://www.ruby-doc.org/core/classes/Kernel.src/M005925.html">method_missing()</a> is passed two arguments; the name of the missing method (as a symbol) and array of its arguments. Let&#8217;s look at an example:
  </p>
  
  <pre># Example 9
class MyGhostClass
  def method_missing(name, *args)
    puts "#{name} was called with arguments: #{args.join(',')}"
  end
end

m = MyGhostClass.new
m.awesome_method("one", "two") # =&gt; awesome_method was called with arguments: one,two
m.another_method("three", "four") # =&gt; another_method was called with arguments: three,four
</pre>
  
  <p>
    There&#8217;s no method named awesome_method() or another_method() within our class yet when we try calling it, we don&#8217;t see the usual NoMethodError. Instead, we see the name of the methods and their arguments, just like we defined in method_missing().
  </p>
  
  <p>
    We can expand this idea a little more by adding conditions to this method. Let&#8217;s say, for example, that all methods containing the word &#8220;awesome&#8221; should be printed out just like in Example 9. All other methods should raise the default NoMethodError.
  </p>
  
  <pre># Example 10
class MyGhostClass
  def method_missing(name, *args)
    if name.to_s =~ /awesome/
      puts "#{name} was called with arguments: #{args.join(',')}"
    else
      super
    end
  end
end

m = MyGhostClass.new
m.awesome_method("one", "two") # =&gt;  awesome_method was called with arguments: one,two
m.another_method("three", "four") # =&gt;  NoMethodError
</pre>
  
  <p>
    This time, calling awesome_method behaves just like in Example 9, but another_method doesn&#8217;t contain the word &#8220;awesome&#8221; so we pass this up the chain of inheritance so the default behaviour is not broken.
  </p>
  
  <h3 id="ghost_methods">
    Ghost Methods
  </h3>
  
  <p>
    Strictly speaking, MyGhostClass#awesome_method is not really a method. If we create an instance of MyGhostClass and look scan it&#8217;s methods any with &#8220;awesome&#8221; in the name we won&#8217;t find any.
  </p>
  
  <pre># Example 11
@m = MyGhostClass.new
@m.methods.grep(/awesome/) # =&gt; nil
</pre>
  
  <p>
    Instead, we call this a ghost method. Ghost methods come with pros and cons. The major pro is the ability to write code that responds to methods when you have no way of knowing the names of those methods in advance. The major con is that changing Ruby&#8217;s default behaviour like this may cause unexpected bugs if you&#8217;re not careful with your method names.<br /> With that in mind, let&#8217;s go back to our CarModel example and see if we can extend the functionality a little further.
  </p>
  
  <pre># Example 12
class CarModel
  def method_missing(name, *args)
    name = name.to_s
    super unless name =~ /(_info|_price)=?$/
    if name =~ (/=$/)
      instance_variable_set("@#{name.chop}", args.first)
    else
      instance_variable_get("@#{name}")
    end
  end
end
</pre>
  
  <p>
    This example may look a little complex but is really quite simple. First, we take the name argument and convert it from a symbol to a string. Next, we say &#8220;send this method up the inheritance chain unless the name ends with &#8216;_price&#8217;, &#8216;_price=&#8217;, &#8216;_info&#8217; or &#8216;_info='&#8221;. If the name ends in an equals sign then we know this is a setter method so we set an instance variable with the same name as our method (minus the &#8220;=&#8221;). If there&#8217;s no equals sign then we know this is a getter method and so we return the instance variable with the same name.
  </p>
  
  <p>
    Now, we don&#8217;t have to specify the features each car model has in advance. We can simply get and set values on any _price or _info attribute during runtime:
  </p>
  
  <pre># Example 13
@car_model = CarModel.new

@car_model.stereo_info    = "CD/MP3 Player"
@car_model.stereo_price   = "£79.99"

@car_model.stereo_info  # =&gt; "CD/MP3 Player"
@car_model.stereo_price # =&gt; "£79.99"
</pre>
  
  <h3 id="conclusion">
    Conclusion
  </h3>
  
  <p>
    This tutorial has only scratched the surface of Ruby&#8217;s metaprogramming capabilities but hopefully it&#8217;s enough to spark your curiosity and will urge you to learn more about metaprogramming. The <a href="http://ruby-doc.org/core/">Ruby API</a> covers all the methods I&#8217;ve talked about here plus more. For further reading, check out:
  </p>
  
  <ul>
    <li>
      <a href="http://ruby-doc.org/core/classes/Module.html#M001660">Module#included</a>
    </li>
    <li>
      <a href="http://ruby-doc.org/core/classes/Module.html#M001650">Module#class_eval</a>
    </li>
    <li>
      <a href="http://ruby-doc.org/core/classes/Object.html#M000334">Object#instance_eval</a>
    </li>
    <li>
      <a href="http://ruby-doc.org/core/classes/Struct.html">Struct</a>
    </li>
  </ul>
  
  <p>
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
  
  <p>
    <strong><em>Do also read</em> these awesome Guest Posts:</strong>
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/blog/2010/11/17/does-ruby-have-too-many-equality-tests/">Does Ruby Have Too Many Equality Tests?</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/11/16/why-use-single-sign-in-solutions-in-rails/">Why Use Single Sign-in Solutions in Rails?</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/11/08/how-does-your-code-smell/">How does your code smell?</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/11/08/do-you-know-resque/">Do YOU know Resque?</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/11/03/do-you-understand-rubys-objects-messages-and-blocks/">Do You Understand Ruby’s Objects, Messages and Blocks?</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/11/02/how-does-one-use-design-patterns-in-ruby/">How Does One Use Design Patterns In Ruby?</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/26/do-you-know-whats-new-in-ruby-1-9/">Do you know what’s new in Ruby 1.9?</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/25/the-value-of-a-personal-bug-log/">The value of a personal bug log</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/18/do-you-enjoy-your-code-quality/">Do You Enjoy Your Code Quality?</a>
    </li>
  </ul>
  
  <p class="note">
    If you want to learn <strong>Ruby Metaprogramming</strong> in-depth, join our online course that starts 4th Dec. 2010. For details <a href="http://rubylearning.com/blog/2010/11/06/ruby-metaprogramming-course-6th-batch-learn-to-think-in-ruby/">click here</a>.
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby+Metaprogramming" rel="tag">Ruby Metaprogramming</a>, <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>
