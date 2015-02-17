---
title: "Ruby Quirks"
author: Satish Talim
date: "2007-04-11"
layout: post
permalink: /2007/04/11/ruby-quirks/
categories:
  - code snippets
  - ruby
  - tricks
---
<div>
  <!--adsense-->
</div>

**Ruby Quirks** – peculiarity of behavior? I know this topic is debatable and remember "one man's meat is another man's poison!"

I plan to write down here (in no particular order), some of the little Ruby quirks that I've picked up and which, I now use comfortably.

**1**. Peter Cooper, the author of the book &#8216;Beginning Ruby' introduced me to Real-Time chat using an IRC client. On the #ruby channel at irc://irc.freenode.net/ I heard of this quirk:

<pre>class MotorCycle
  def initialize(make, color)
    @make, @color = make, color
  end
end

m = MotorCycle.new('Honda', 'blue')
m.instance_variable_set(:@make, 'Kawasaki')
m.instance_variable_set(:@gears, 4)
puts m.inspect</pre>

Check the output of the above program. In the code above:

<pre>m.instance_variable_set(:@gears, 4)</pre>

sets the instance variable names by *symbol* to object, thereby frustrating the efforts of the class's author to attempt to provide proper encapsulation. The variable did not have to exist prior to this call.  
**<span style="color:red;">Update:</span>** Hal Fulton in his excellent book &#8216;The Ruby Way' has this to say about instance\_variable\_set:

> It's true these methods are powerful and potentially dangerous. They should be used cautiously, not casually. But it's impossible to say whether encapsulation is violated without looking at *how these tools are used*. If they are used intentionally as part of a good design, then all is well. If they are used to violate the design, or to circumvent a bad design, then all is not well.

**2**. This one is not really a quirk but appears to be one, especially for people coming from a Java background. Last year, [Shashank Date][1] gave the [PuneRuby][2] members a presentation on &#8216;Why Ruby Shines' and three points stood out – &#8216;Expressions everywhere', &#8216;Active Class Definitions' and &#8216;Everything is an Object'.

***<small>Expressions everywhere</small>*** – In Ruby, everything returns some value. Therefore a class definition is an expression and one can say something like:

<pre>c = class C
end</pre>

The value of c is nil.

***<small>Active Class Definitions</small>*** – Look at the following program:

<pre>class C
  puts 'In class C'
end</pre>

When this class is read the first time, it executes puts and the output is – &#8216;In class C'.

***<small>Everything is an Object</small>*** – After being with Java since 1995, the concept that classes in Ruby are first-class objects, is hard to digest at first – each is an instance of class Class. When a new class is defined (typically using class Name &#8230; end), an object of type Class is created and assigned to a constant (Name. in this case). Hal Fulton's suggests a *mantra* to be recited everyday – &#8220;Class *is an object*, and Object *is a class*.&#8221;

**3**. If I want to swap two variables, I would normally use an additional temporary variable. In Ruby, this is not necessary:

<pre>x, y = y, x</pre>

will interchange the values of x and y.

**4**. Jaaron, a reader of this Learning Ruby Blog has this quirk for us. This one is well known and is the cause of much frustration.

<pre>x = 7
[1,2,3].each do |x|
end</pre>

If the name of a block parameter conflicts with the name of a local variable, the behavior is to assign the local variable to the argument. In this case, the local variable x gets assigned the value 1, then the value 2, then the value 3. The value 7 is lost.  
**<span style="color:red;">Update (13th April):</span>** Matt Chen, Matthew King and Ara Vartanian have commented on this behavior. If you refer to Programming Ruby Second Edition eBook (page 100) it says:

> The whole issue with variable scope and blocks is one that generates considerable discussion in the Ruby community. The current scheme has definite problems (particularly when variables are unexpectedly aliased inside blocks), but at the same time no one has managed to come up with something thatâ€™s both better and acceptable to the wider community. Matz is promising changes in Ruby 2.0.

**5**. Are instance variables inherited by a sub-class? David Black the author of Ruby for Rails has this to say: Instance variables are per-object, not per-class, and <span class="underline">they're not inherited</span>. But if a method uses one, and that method is available to subclasses, then it will still use the variable &#8212; but &#8220;the variable&#8221; in the sense of one per object. See the following program:

<pre>class C
  def initialize
    @n = 100
  end

  def increase_n
    @n *= 20
  end
end

class D &lt; C
  def show_n
    puts "n is #{@n}"
  end
end

d = D.new
d.increase_n
d.show_n</pre>

The output is:

<pre>>ruby p049instvarinherit.rb
n is 2000
>Exit code: 0</pre>

**6**. Morgan Schweers, a reader of this blog has this quirk for us. Imagine for a moment, that you want to be able to set a variable, but if it's not set, you default to a known value. You'd rather do it on a single line.

One of my co-workers tried this:

<pre>expand = defined?( expand ) ? expand : true</pre>

but &#8216;expand' is \*defined\* by being on the left hand side, BEFORE the RHS is evaluated, so defined? returns true, but because expand hasn't got a value yet, it returns nil.

I tried:

<pre>expand = true unless defined?(expand)</pre>

and it doesn't help either, which really shocked me. I always believed that the postfix-conditional was evaluated before even beginning to evaluate the operation, but I was distinctly disabused of this notion by testing.

Note that &#8216;expand?'' operator returns nil if its argument (which can be an arbitrary expression) is not defined; otherwise it returns a description of that argument.

I don't understand the reason for the behavior, and I think it's a bug, but I'd love to know a good language reason for it.

I am sure that you would have noticed many other **Ruby Quirks**. I'd definitely like to hear and add them here.

* * *

**Information**

Ruby is an open source thorough language of utmost balance with combination of Perl, Smalltalk, Lisp, Ada and Eiffel. With the recent developments in this language, most developers use this language in the middle tier. Today is the era of developing online business applications, [mobile software][3] and its applications. Most developers deploy their online applications after getting [business web hosting][4] and then they market for these projects through [affiliate marketing][5] campaigns or if they do not want to sell their project they can use [ppc advertising][6] for earning some revenue or can offer [ppc management][7] programs. When they are in the process of development usually they [register domain][8] and use [domain parking][9] facility, so that once their project is ready they can instantly put it on the internet.

* * *

Technorati Tags: <a href="http://technorati.com/tag/Ruby+Quirks" rel="tag">Ruby Quirks</a>

 [1]: http://rubylearning.com/blog/2007/04/11/interview-shashank-date/
 [2]: http://tech.groups.yahoo.com/group/puneruby/
 [3]: http://www.mysoftwarehubs.com
 [4]: http://www.envisionwebhosting.com
 [5]: http://www.getaffiliates.net
 [6]: http://www.qualifytraffic.com/Advertising-Info/PPC-Advertising.html
 [7]: http://www.performanceppc.com
 [8]: http://www.namingwiz.com
 [9]: http://www.nationaldomainreg.com/Domain-Parking.html
