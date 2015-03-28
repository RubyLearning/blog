---
draft: false
title: Do you know how to write an internal DSL in Ruby?
date: 2011-10-02
Hide OgTags:
- 0
Hide SexyBookmarks:
- 0
author: Satish Talim
authorlink: http://satishtalim.com
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/satishtalim/about
categories:
- Beginners
- Metaprogramming
- Popular
- Ruby
layout: post
permalink: /2011/10/02/do-you-know-how-to-write-an-internal-dsl-in-ruby/
tags:
- programming
- Ruby
- Ruby DSL
- ruby programming
topsy_short_url:
- http://bit.ly/rsrPHC
---

<div>
  <p class="alert">
    Almost all Ruby programming newbies would love to get their hands wet writing a Ruby DSL. This article explains how you can write a simple Ruby DSL.
  </p>
  
  <h3>
    Introduction
  </h3>
  
  <p>
    A <b>Domain-Specific Language (DSL)</b> is a (usually small) programming or description language designed for a fairly narrow purpose. DSLs are targeted at end users or domain specialists who are not expert programmers. <a href="http://www.infoq.com/presentations/domain-specific-languages">Martin Fowler</a> classifies DSLs into two styles &#8211; external and internal. An external DSL is a language that is different from the main programming language for an application, but that is interpreted by or translated into a program in the main language. An internal DSL transforms the main programming language itself into the DSL (our simple DSL is tied to the Ruby programming language).
  </p>
  
  <h4>
    Ruby code blocks
  </h4>
  
  <p>
    Ruby&#8217;s <em>support for blocks</em> (i.e., closures) is useful in defining internal DSLs.
  </p>
  
  <p>
    Ruby code blocks (called closures in other languages) are chunks of code between braces or between do- end that you can associate with method invocations, almost as if they were parameters. A Ruby block is a way of grouping statements, and may appear only in the source next to a method call; the block is written starting on the same line as the method call&#8217;s last parameter (or the closing parenthesis of the parameter list). The code in the block is not executed at the time it is encountered. Instead, Ruby remembers the context in which the block appears (the local variables, the current object, and so on) and then enters the method. Matz says that any method can be called with a block as an implicit argument. Inside the method, you can call the block using the <code>yield</code> keyword with a value. Blocks are not objects, but they can be converted into objects of class <code>Proc</code>. One way a block can be converted to a <code>Proc</code> object is by passing a block to a method whose last parameter is prefixed with an ampersand. That parameter will receive the block as a <code>Proc</code> object:
  </p>
  
  <pre>def my_method(p1, &#038;block)
  ...
end
</pre>
  
  <h4>
    instance_eval
  </h4>
  
  <p>
    The class <code>Object</code> has an <code>instance_eval</code> public method which can be called from a specific object. It provides access to the instance variables of that object. It can be called either with a block or with a string:
  </p>
  
  <pre>class Rubyist
  def initialize
    @geek = "Matz"
  end
end
obj = Rubyist.new
# instance_eval can access obj's private methods
# and instance variables
obj.instance_eval do
  puts self  # => #&lt;Rubyist:0x2ef83d0&gt;
  puts @geek # => Matz
end
</pre>
  
  <p>
    The block that you pass to <code>instance_eval</code> helps you dip inside an object to do something in there. You can wreak havoc on encapsulation! No data is private data anymore.
  </p>
  
  <p>
    <code>instance_eval</code> can also be used to add class methods as shown below:
  </p>
  
  <pre>class Rubyist
end
Rubyist.instance_eval do
  def who
    "Geek"
  end
end
puts Rubyist.who # => Geek
</pre>
  
  <h3>
    Deciding on a simple DSL
  </h3>
  
  <p>
    You are an expert Ruby programmer and your friends Victor, Michael and Satoshi (all 3 are novice chess players) have requested you to write a Ruby program for them, that could help them with a listing of the best black opening chess moves.
  </p>
  
  <p>
    You tell your chess friends that if they need help they should individually send you a text file containing the white&#8217;s first move, as follows:
  </p>
  
  <pre>
h4
a3
e4
</pre>
  
  <p>
    h4, a3, e4 would be Ruby methods in your DSL program. Once we get the DSL to follow valid Ruby syntax, Ruby does all the work to parse the file and hold the data in a way that we can operate on it.
  </p>
  
  <p>
    Victor is playing the black pieces and his opponent plays the opening white piece (say h4). Victor would like to know what&#8217;s the best strategy to counter white&#8217;s opening move of h4. He also would like to know, what if his opponent would have played a3.
  </p>
  
  <p>
    Victor decides to send a <a href="https://github.com/SatishTalim/ChessOpeningMoves/blob/master/chess_opener_test.txt">text file</a> to you.
  </p>
  
  <h3>
    The DSL program &#8211; chess_opener.rb
  </h3>
  
  <p>
    Being a Ruby expert, you dish out your first version of the DSL program &#8211; <a href="https://github.com/SatishTalim/ChessOpeningMoves/blob/master/chess_opener.rb">chess_opener.rb</a>:
  </p>
  
  <pre>class ChessOpener
  def initialize
    @data = {}
    load_data
  end
  
  def self.load(filename)
    dsl = new
    dsl.instance_eval(File.read(filename))
  end
  
  def h4
    puts "=========="
    puts @data.assoc("h4")
    puts "=========="    
  end

  def a3
    puts "=========="
    puts @data.assoc("a3")
    puts "=========="    
  end

  def method_missing(method_name, *args, &#038;block)
    msg = "You tried to call the method #{method_name}. There is no such method."
    raise msg
  end

  private
  def load_data
    @data = {"a3" => ["Anderssen's Opening Polish Gambit: 1. a3 a5 2. b4",
                      "Anderssen's Opening Creepy Crawly Formation: 1. a3 e5 2. h3 d5",
                      "Anderssen's Opening Andersspike: 1. a3 g6 2. g4"],
             "h4" => ["Koola-Koola continues 1.h4 a5",
                      "Wulumulu continues 1.h4 e5 2. d4",
                      "Crab Variation continues 1.h4 any 2. a4",
                      "Borg Gambit continues 1.h4 g5.",
                      "Symmetric Variation continues 1.h4 h5"]}
  end
  
end
</pre>
  
  <h4>
    Some explanation of code
  </h4>
  
  <p>
    The <code>initialize</code> method of your class <code>ChessOpener</code> creates a <code>Hash</code> object <code>@data</code> and populates it by calling the <code>private</code> method <code>load_data</code>. You have referred to the online <a href="http://en.wikipedia.org/wiki/List_of_chess_openings">list of chess openings</a> to create the hash <code>@data</code>. The current program has the openings only for a3 and h4 moves, but you plan to add the other moves soon.
  </p>
  
  <p>
    You want a simple and straightforward way to parse the <a href="https://github.com/SatishTalim/ChessOpeningMoves/blob/master/chess_opener_test.txt">DSL file</a>. Something like:
  </p>
  
  <pre>my_dsl = ChessOpener.load(filename)
</pre>
  
  <p>
    Also, you would like to accept the DSL file from the command line, something like:
  </p>
  
  <pre>my_dsl = ChessOpener.load(ARGV[0])
</pre>
  
  <p>
    You write a <em>class method</em> <code>load</code>:
  </p>
  
  <pre>def self.load(filename)
  dsl = new
  dsl.instance_eval(File.read(filename))
end
</pre>
  
  <p>
    The class method <code>load</code> creates a <code>ChessOpener</code> object and calls <code>instance_eval</code> on the DSL file (chess_opener_test.txt above). If you feed <code>instance_eval</code> a string, <code>instance_eval</code> will evaluate the string as Ruby code. In fact, this Ruby code is nothing but calls to the methods h4 and a3 which are respectively called. The methods h4 and a3 make use of Ruby Hash&#8217;s <code>assoc</code> method to extract the information about the particular (say h4) move.
  </p>
  
  <p>
    The program also provides a <a href="http://rubylearning.com/satishtalim/ruby_method_missing.html">method_missing</a> method, in case the program fails to find a method say h5 (assuming Victor has typed that by mistake in the file chess_opener_test.txt.)
  </p>
  
  <h3>
    Running the DSL program
  </h3>
  
  <p>
    You next write the program &#8211; <a href="https://github.com/SatishTalim/ChessOpeningMoves/blob/master/chess_opener_test.rb">chess_opener_test.rb</a>, ensuring that the files chess_opener.rb, chess_opener_test.rb and chess_opener_test.txt are in the same folder on your computer.
  </p>
  
  <p>
    You now run your Ruby code as follows:
  </p>
  
  <pre>ruby chess_opener_test.rb chess_opener_test.txt
</pre>
  
  <p>
    Here&#8217;s the sample output:
  </p>
  
  <pre>==========
h4
Koola-Koola continues 1.h4 a5
Wulumulu continues 1.h4 e5 2. d4
Crab Variation continues 1.h4 any 2. a4
Borg Gambit continues 1.h4 g5.
Symmetric Variation continues 1.h4 h5
==========
==========
a3
Anderssen's Opening Polish Gambit: 1. a3 a5 2. b4
Anderssen's Opening Creepy Crawly Formation: 1. a3 e5 2. h3 d5
Anderssen's Opening Andersspike: 1. a3 g6 2. g4
==========
</pre>
  
  <p>
    In fact, in the next version of your DSL program, you plan to write the output to a file and send the same to Victor. Why don&#8217;t you <a href="https://github.com/SatishTalim/ChessOpeningMoves">fork this project</a> and add-on some more functionality?
  </p>
  
  <p>
    That&#8217;s it!
  </p>
  
  <p class="alert">
    <em>Feel free to ask questions and give feedback in the comments section of this post.</em> Fellow Rubyists, if you would like to write a guest blog post for RubyLearning email me at <b>satish [at] rubylearning.org</b>
  </p>
</div>

