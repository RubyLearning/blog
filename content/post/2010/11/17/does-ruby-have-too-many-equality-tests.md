---
title: Does Ruby Have Too Many Equality Tests?
author: Eric Anderson
date: 2010-11-17
layout: post
permalink: /2010/11/17/does-ruby-have-too-many-equality-tests/
thesis_description:
  - |
    Learn the difference between the myriad of equality tests that Ruby provides. Explanations and examples of when to use 
    ==, ===, eql?, equal? and =~.
thesis_keywords:
  - Ruby Equality Tests,Programming,Ruby programming
topsy_short_url:
  - http://bit.ly/avdLgp
categories:
  - Beginners
  - Ruby
  - Ruby Masters
tags:
  - programming
  - Ruby Equality Tests
  - ruby programming
---
<div>
  <h3>
    Does Ruby Have Too Many Equality Tests?
  </h3>
  
  <p class="update">
    This guest post is by <strong>Eric Anderson</strong>, who develops web-based applications for small businesses though his company <a href="http://pixelwareinc.com/resume.html">Pixelware, LLC</a> in Atlanta, GA. He also runs <a href="http://www.saveyourcall.com/">SaveYourCall.com</a> which allows people to record phone calls from any phone without the need for any complicated hardware.
  </p>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/eric-anderson.jpg" alt="Eric Anderson" /> <span class="drop_cap">Y</span>ou probably started using == out of habit from other languages. It seems to work and that seems good enough. But then you might start seeing ===, =~, eql? and equal? and wonder what the heck those are about? How are they different and why does Ruby make you insane with so many equality tests?
  </p>
  
  <p>
    This article will explain the purpose of each test. It will help you understand the intention of the test by looking at how the standard library defines them. Once you understand the intent you will know how to define that method in your own objects and what you should expect when you are using standard library and 3rd party objects.
  </p>
  
  <h3>
    ==
  </h3>
  
  <p>
    == is your main equality test. Most of the time when you want to test for equality this is what you will use. The intent of this method is &#8220;do the objects have the same value regardless of class?&#8221; The following are a few examples that will illustrate the behavior:
  </p>
  
  <pre>a = Object.new
a == a                             # true
a == Object.new                    # false
"foo"           == "foo"           # true
"foo".object_id == "foo".object_id # false
1 == 1.0                           # true
1.class == 1.0.class               # false</pre>
  
  <p>
    The first two examples show the default behavior when comparing instances of class Object. If the two objects are the same object in memory it will return true. But if it is compared to another instance of Object it will return false.
  </p>
  
  <p>
    The next example compares two String instances with the same value. As you can see when compared they return true even though they are different objects in memory (as noted by the fact that their object id returns false when compared). So even though the default behavior is fairly strict subclasses should open up if they are able to decide the objects have the same value.
  </p>
  
  <p>
    The final example shows us the value comparison carries across different classes. 1 is a Fixnum while 1.0 is a Float. But since they still have the same value they are considered equal. This means when implementing your own objects you should ignore the class of the other objects and concentrate solely on the value of the objects.
  </p>
  
  <p>
    Also when implementing == it is important to ensure the equality test is reversible. a == b should return the same value as b == a.
  </p>
  
  <p>
    One last note on ==. You may occasionally see the != operator. != is not a method you can define but a language feature. It will call your == method and then return the opposite boolean value returned by ==.
  </p>
  
  <h3>
    eql?
  </h3>
  
  <p>
    eql? operates slightly more restrictive than ==. Like == it is concerned with the value of the object and not concerned if two objects are the same instance. But unlike ==, eql? does care about the class. Let&#8217;s look at some examples:
  </p>
  
  <pre>a = Object.new
a.eql? a                             # true
a.eql? Object.new                    # false
"foo".eql? "foo"                     # true
"foo".object_id == "foo".object_id   # false
1.eql? 1.0                           # false</pre>
  
  <p>
    As you can see eql? starts out like ==, but when comparing the Fixnum to the Float the result is false even though they have the same value. An object is data plus behavior. Since == is intended to be ignorant of class it is basically ignoring differences in behavior and only concerned with differences in data. By using eql? you are indicating you not only care that the value is the same but that the behavior of the object is the same.
  </p>
  
  <h3>
    equal?
  </h3>
  
  <p>
    equal? is the most strict of any equality tests. It will test to ensure that the objects being compared are the same instances in memory. This means the value of their object id will be same as they are literally two pointers to the same instance.
  </p>
  
  <pre>a = Object.new
a.equal? a                           # true
a.equal? Object.new                  # false
"foo".equal? "foo"                   # false
"foo".object_id == "foo".object_id   # false
1.equal? 1                           # true
1.object_id == 1.object_id           # true</pre>
  
  <p>
    So our default behavior is like the other equality tests but the similarities end there. When you compare two difference instances of String with the same value you get false. This is because despite having the same value they are two different instances in memory.
  </p>
  
  <p>
    The last example is an interesting quirk of Ruby. For performance and memory optimization reasons there is only once instance of each value of Fixnum. This means that even though we created our instances separately they have the same object id and therefore equal? will return true when compared.
  </p>
  
  <p>
    Ruby requires equal? conform to this intent. You should not override this method in your subclasses. Doing so might cause unpredictable behavior by the Ruby runtime.
  </p>
  
  <h3>
    ===
  </h3>
  
  <p>
    === can allow you to write code in a very concise and readable way. === is a way you can compare two objects using a single operator but having the intent change depending on the context of the comparison. Lets give some examples:
  </p>
  
  <pre>a = Object.new
a === a                             # true
a === Object.new                    # false
"foo"           === "foo"           # true
"foo".object_id == "foo".object_id  # false
1 === 1.0                           # true
1.class == 1.0.class                # false
Fixnum  === 1                       # true
(1..10) === 5                       # true
/o/ === 'foo'                       # true</pre>
  
  <p>
    As we can see this starts out looking a LOT like ==. We can see that the comparison is concerned with value not the instance in memory. It also doesn&#8217;t care about class. The last three examples really show this method&#8217;s uniqueness. When comparing a class with an instance of that class we get true. When comparing a range with a value in that range we get true. When comparing a regexp with a string it returns true if the regexp matches the string. Why does Class, Range and Regexp define === this way? Because the === operator is used in the case control flow statement. Review the following example:
  </p>
  
  <pre>case obj
  when "foo"          then ....
  when Fixnum, Float  then ...
  when 1..10          then ....
  when /o/            then ....
end</pre>
  
  <p>
    This is the magic of ===. It lets the intent change depending on the context of the comparison. So sometimes you want a simple value comparison like ==. Other times you want to know if an object is an instance of the given class. Other times you want to know if a value is in a range and sometimes you want to know if a regexp matches an object. You have one operator the case statement can use that works for all these types of comparisons.
  </p>
  
  <p>
    It is important to note that just because a === b, this does not imply b === a. The order of the comparison is very important. For example 1 === Fixnum will return false while Fixnum === 1 returns true.
  </p>
  
  <h3>
    =~
  </h3>
  
  <p>
    =~ is a pretty special equality operator. Object defines it to always return false (even if comparing two objects that are the same instance). Where this operator gets interesting is with the Regexp class. Take a look at the following examples:
  </p>
  
  <pre>a = Object.new
a =~ a                                          # false
/o/   =~ 'foo'                                  # true
'foo' =~ /o/                                    # true
Mime::Type.new('application/xml') =~ 'text/xml' # true</pre>
  
  <p>
    Regexp defines =~ as alias to the match method. This provides the familiar =~ syntax found in languages like Perl while still providing a fully object-oriented regexp library. Note that String defines =~ to reverse the operands. So &#8216;foo&#8217; =~ obj will execute obj =~ &#8216;foo&#8217;. This allows =~ to be reversible when comparing a String even though =~ is not generally reversible.
  </p>
  
  <p>
    Regexp is the primary place =~ is used but the last example shows where =~ is defined by a class in the Rails framework to allow mime type aliases to match a specific mime type object.
  </p>
  
  <p>
    Like the == method there is an inverse of =~ which is a language feature and not a method that can be overridden. So if you see !~ the =~ method will be called then the inverse of the result will be returned.
  </p>
  
  <h3>
    Conclusion
  </h3>
  
  <p>
    So does Ruby have too many equality tests? I think not! == obviously is the work horse equality test. But the case statement would not be nearly as elegant without ===. Testing a regexp would not be nearly as concise without =~. == is great most of the time but sometimes it is too broad. eql? and equal? are great way to be more precise.
  </p>
  
  <p>
    When creating your own classes try to make sure that these methods are conforming to their intent and not just inheriting the default behavior of Object. This can often make your API much more elegant.
  </p>
  
  <p>
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
  
  <p>
    <strong><em>Do also read</em> these awesome Guest Posts:</strong>
  </p>
  
  <ul>
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
    Also check out the <a href="http://rubylearning.com/blog/ebooks/">free and paid Ruby-related eBooks</a> from RubyLearning.
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby+Equality+Tests" rel="tag">Ruby Equality Tests</a>, <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>
