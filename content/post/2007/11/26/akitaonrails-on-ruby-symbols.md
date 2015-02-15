---
title: '&#8220;AkitaOnRails&#8221; On Ruby Symbols'
author: Satish Talim
date: 2007-11-26
layout: post
permalink: /2007/11/26/akitaonrails-on-ruby-symbols/
categories:
  - Beginners
  - Code Snippets
  - Ruby
  - Training
  - Tricks
---
<div>
  <p>
    <em>RubyLearning recently caught with <strong>Fabio Akita</strong> from Brazil and got his viewpoint on one of the vexing areas for beginners in Ruby &#8211; <strong>Symbols</strong>.</em>
  </p>
  
  <p class="block">
    <img class="alignleft" title="Fabio Akita" src="http://www.rubylearning.com/images/akita.jpg" alt="Fabio Akita" /><strong>Fabio Akita</strong> is a Brazilian Rails enthusiast, also known online as &#8220;AkitaOnRails&#8221;. He regularly write posts on his own <a href="http://www.akitaonrails.com/">blog</a> and had published the very first book tailored for the Brazilian audience called &#8220;Repensando a Web com Rails&#8221;. He is now a full-time Ruby on Rails developer working as Brazil Rails Practice Manager for the Utah company Surgeworks LLC.
  </p>
  
  <p>
    Ruby is very similar to many other object oriented languages. You can find similar constructs from non-dynamic languages as Java or C#. On the other hand, to start grasping all the possibilities of Ruby one has to invest some time learning what we call &#8216;Rubyisms&#8217;. One example is something called a *symbol*.
  </p>
  
  <p>
    This is more obvious when you start learning Ruby through Rails. Much of Rails power comes from the fact that it uses a lot of rubyisms. Let&#8217;s see one example: (<strong>Note</strong>: You may want to brush up on <a href="http://rubylearning.com/satishtalim/ruby_symbols.html">Symbols</a> and <a href="http://rubylearning.com/satishtalim/ruby_activerecord_and_mysql.html">ActiveRecord</a> before going through the examples that follow.)
  </p>
  
  <pre><code>&lt;span style="color:blue">class Transact &lt; ActiveRecord::Base
  validates_presence_of :when
  validates_presence_of :category, :account
  validates_presence_of :value
  validates_numericality_of :value

  belongs_to :category
  belongs_to :account
end&lt;/span></code></pre>
  
  <p>
    &#8216;class&#8217; we understand, after all, the mainstream languages are &#8216;object-oriented&#8217;. But what are all those colons doing through all the code? Those denote Symbols. More important, the colons represent initializers of the class <strong>Symbol</strong>.
  </p>
  
  <p>
    This can be quite confusing considering that the normal way of initializing an object is:
  </p>
  
  <pre><code>&lt;span style="color:blue">Symbol.new&lt;/span></code></pre>
  
  <p>
    The &#8216;<strong>new</strong>&#8216; call asks for the standard &#8216;<strong>initialize</strong>&#8216; method defined within the class. Turns out that this method is private, the idea being that all symbols should be instantiated with the colon notation.
  </p>
  
  <p>
    Symbols are used as identifiers. Some other languages could simply use Strings instead of Symbols. In Ruby, it would become something like this:
  </p>
  
  <pre><code>&lt;span style="color:blue">class Transact &lt; ActiveRecord::Base
  validates_presence_of "when"
  validates_presence_of "category", "account"
  validates_presence_of "value"
  validates_numericality_of "value"

  belongs_to "category"
  belongs_to "account"
end&lt;/span></code></pre>
  
  <p>
    Not so visually different: we got rid of the colons and went back to the comfortable quotation marks. They look the same but behave differently. Like Symbols in Ruby, Strings also have a special constructor. Instead of doing:
  </p>
  
  <pre><code>&lt;span style="color:blue">String.new("category")&lt;/span></code></pre>
  
  <p>
    We just do:
  </p>
  
  <pre><code>&lt;span style="color:blue">"category"&lt;/span></code></pre>
  
  <p>
    One could call these kind of shortcuts as &#8220;eye-candy&#8221;, but the languages would be pretty harsh without them. We use Strings all the time, and it would be extremely painful to instantiate new Strings without this special constructor: simply writing it between quotation marks.
  </p>
  
  <p>
    The problem is, as Strings are easy to write, we overuse them more often than not. There is an important side-effect: each new construct instantiates a brand new object in memory, even though they have the same content. For instance:
  </p>
  
  <pre><code>&lt;span style="color:blue">>> "category".object_id
=> 2953810

>> "category".object_id
=> 2951340&lt;/span></code></pre>
  
  <p>
    Here, we instantiate two strings with the same content. Each object in memory has a unique ID so each string created above uses a separate memory slot and have separate IDs. Now imagine that the same string shows up in hundreds of different places throughout your project. You&#8217;re definitely using more memory than necessary.
  </p>
  
  <p>
    But, this is not a new problem. For that, we have another construct in most languages called &#8216;constants&#8217;, Ruby included. We have to conscientiously plan and pre-define several constants beforehand. So, that&#8217;s how our previous example would be using memory efficient constants:
  </p>
  
  <pre><code>&lt;span style="color:blue">class Transact &lt; ActiveRecord::Base
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
end&lt;/span></code></pre>
  
  <p>
    This works, but this is not nearly as nice. First of all, you have to pre-define everything beforehand, either in the same class or a separated module just for constants. Second, the code is less elegant, less readable, thus, less maintainable.
  </p>
  
  <p>
    So, we get back to the purpose of Symbols: being as memory efficient as constants but as easy to the eyes as full fledged strings. Quotation mark notation is already taken for Strings, capitalized words for constants, dollar sign for global variables and so on. So, colon was a good candidate.
  </p>
  
  <p>
    Let&#8217;s see what it all means:
  </p>
  
  <pre><code>&lt;span style="color:blue">>> "string".object_id
=> 3001850
>> "string".object_id
=> 2999540

>> :string.object_id
=> 69618
>> :string.object_id
=> 69618&lt;/span></code></pre>
  
  <p>
    As we explained before, the first two strings have the same content and look similar, but they do occupy different memory slots, allowing for unnecessary duplication.
  </p>
  
  <p>
    The last two symbols both are exactly the same thing. So I can call identifiers as symbols through all my code without worrying about duplication in memory. They are easy to initialize and easy to manage.
  </p>
  
  <p>
    We can also transform a String into a Symbol and vice-versa:
  </p>
  
  <pre><code>&lt;span style="color:blue">>> "string".to_sym
=> :string
>> :symbol.to_s
=> "symbol"&lt;/span></code></pre>
  
  <p>
    One good place where this is put to good use is within Rails&#8217; <strong>ActiveSupport</strong>. This package was made to extend the Ruby language, and one such extension was made to the ubiquitous <strong>Hash</strong> class. Let&#8217;s see an example:
  </p>
  
  <pre><code>&lt;span style="color:blue">>> params = { "id" => 1, "action" => "show" }
=> {"action"=>"show", "id"=>1}

>> params["id"]
=> 1

>> params.symbolize_keys!
=> {:id=>1, :action=>"show"}

>> params[:id]
=> 1&lt;/span></code></pre>
  
  <p>
    The first statement instantiates and populates a <strong>Hash</strong> (yet another special initialization notation). The second statement asks for the value identified by the key &#8220;id&#8221;, which is a string.
  </p>
  
  <p>
    Instead of doing it this way, we can call the <strong>symbolize_keys!</strong> to transform all string keys into symbol keys. Now in the last statement we can use the more usual Rails notation as symbol keys within a Hash. When Rails receives a HTML Form post request, it only gets strings, so it is its job to convert everything into meaningful Rails objects. If you&#8217;ve been in the Rails world, you already saw this usage with controllers.
  </p>
  
  <p>
    So, this is all to be said about Symbols: very simple constructs that makes code more readable and more efficient at the same time, which is compatible with the Ruby Way.
  </p>
  
  <p>
    <em>Thank you Fabio for showing us a different perspective on Symbols. In case you have any queries, questions on this article, kindly post your questions here and Fabio would be glad to answer.</em>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Brazil" rel="tag">Brazil</a>, <a href="http://technorati.com/tag/Fabio+Akita" rel="tag">Fabio Akita</a>, <a href="http://technorati.com/tag/Ruby+Programming" rel="tag">Ruby Programming</a>, <a href="http://technorati.com/tag/Ruby+Symbols" rel="tag">Ruby Symbols</a>
