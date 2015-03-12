---
author: Steve Klabnik
categories:
- Beginners
- Ruby
- Ruby Masters
date: 2011-07-28
layout: post
permalink: /2011/07/28/how-do-i-test-my-code-with-minitest/
tags:
- minitest
- programming
- ruby programming
thesis_description:
- Steve Klabnik introduces the readers to Ruby's minitest.
thesis_keywords:
- minitest, Programming,Ruby programming
title: How do I test my code with Minitest?
topsy_short_url:
- null
---

<div>
  <h3>
    How do I test my code with Minitest?
  </h3>
  
  <p class="update">
    This guest post is by <strong><a href="https://github.com/steveklabnik">Steve Klabnik</a></strong>, who is a software craftsman, writer, and former startup CTO. Steve tries to keep his Ruby consulting hours down so that he can focus on maintaining <a href="http://hackety-hack.com/">Hackety Hack</a> and being a core member of Team Shoes, as well as writing regularly for multiple blogs.
  </p>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/steve_cropped.jpg" alt="Steve Klabnik" /> <span class="drop_cap">P</span>rogramming is an interesting activity. Everyone has their favorite&nbsp;metaphor that really explains what programming means to them. Well, I&nbsp;have a few, but here&#8217;s one: Programming is all about automation. You&#8217;re&nbsp;really just getting the computer to automatically do work that you know&nbsp;how to do, but don&#8217;t want to do over and over again.
  </p>
  
  <p>
    When I realized this, it made me look for other things that I do that&nbsp;could be automated. I don&#8217;t like repeating myself over and over and over&nbsp;again. That&#8217;s boring! Well, there&#8217;s one particular task that&#8217;s related&nbsp;to programming that&#8217;s easily made automatic, and that&#8217;s testing that&nbsp;your software works!
  </p>
  
  <p>
    Does this story sound familiar? You run your program, try a few&nbsp;different inputs, check the outputs, and see that they&#8217;re right. Then,&nbsp;you make some changes in your code, and you&#8217;d like to see if they work&nbsp;or not, so you fire up Ruby and try those inputs again. That repetition&nbsp;should stick out. There has to be a better way.
  </p>
  
  <p>
    Luckily, there is! Ruby has fantastic tools that let you set up tests&nbsp;for your code that you can run automatically. You can save yourself tons&nbsp;of time and effort by letting the computer run thousands of tests every&nbsp;time you make a change to your code. And it&#8217;ll never get tired and&nbsp;accidentally type in a 2 when you mean to type 3&#8230; Many people take&nbsp;this one step farther. They find testing so important and so helpful&nbsp;that they actually write the tests before they write the code! I won&#8217;t&nbsp;expound on the virtues of &#8220;test driven development&#8221; in this post, but&nbsp;it&#8217;s actually easier to write the tests first, once you get some&nbsp;practice at it. So, let&#8217;s pick a tiny bit of code to work on, and I&#8217;ll&nbsp;show you how to test it using Ruby&#8217;s built-in testing library, minitest.
  </p>
  
  <p>
    For this exercise, let&#8217;s do something simple, so we can focus on the&nbsp;tests. We&#8217;ll make a Ruby class called CashRegister. It&#8217;ll have a bunch&nbsp;of features, but here&#8217;s the first two methods we&#8217;ll need:
  </p>
  
  <ul>
    <li>
      The register will have a scan method that takes in a price, and&nbsp;records it.
    </li>
    <li>
      The register will have a total method that shows the current total of&nbsp;all the prices that have been scanned so far.
    </li>
    <li>
      If no prices have been scanned, the total should be zero.
    </li>
    <li>
      The register will have a clear method that clears the register of all&nbsp;scanned items. The total should go back to zero again.
    </li>
  </ul>
  
  <p>
    Seems simple, right? You might even know how to code this already.&nbsp;Sometimes, intermediate programmers practice coding problems that are&nbsp;easy, just to focus on how to write good tests, or to work on getting&nbsp;the perfect design. We call these kinds of problems &#8216;kata.&#8217; It&#8217;s a&nbsp;martial arts thing.
  </p>
  
  <p>
    Anyway, enough about all of this! Let&#8217;s dig in to minitest. It already&nbsp;comes with Ruby 1.9, but if you&#8217;re still using 1.8, you can install it&nbsp;with &#8216;<code>gem install minitest</code>.&#8217; After doing so, open up a new file,&nbsp;register.rb, and put this in it:
  </p>
  
  <pre>require 'minitest/autorun'

class TestCashRegister &lt; MiniTest::Unit::TestCase
  def setup
    @register = CashRegister.new
  end
  def test_default_is_zero
    assert_equal 0, @register.total
  end
end</pre>
  
  <p>
    Okay! There&#8217;s a lot going on here. Let&#8217;s take it line by line. On the first line, we have a &#8216;require.&#8217; The autorun part of minispec includes everything you need to run your tests, automatically. All we need to do to run our tests is to type ruby register.rb, and they&#8217;ll run and check our code. But let&#8217;s look at the rest of the file before we do that. The next thing we do is set up a class that inherits from one of minitest&#8217;s base classes. That&#8217;s how minitest works, by running a series of TestCases. It also lets you group similar tests together, and split different ones up into multiple files.
  </p>
  
  <p>
    Anyway, enough organizational stuff. In this class, we have two methods: the first is the setup method. This runs before each test, and allows us to prepare for the test we want to run. In this case, we want a new CashRegister each time, and we&#8217;ll store it in a variable. Now we don&#8217;t have to repeat our setup over and over again&#8230; it&#8217;s just automatic!
  </p>
  
  <p>
    Finally, we get down to business, with the <code>test_default_is_zero</code> method. Minitest will run any method that starts with test_ as a test. In that method, we use the <code>assert_equal</code> method with two arguments. <code>assert_equal</code> is where it all happens, by comparing 0 to our register&#8217;s total, and it will complain if they&#8217;re not equal.
  </p>
  
  <p>
    Okay, so we have our first test. Rock! You might be tempted to start implementing our CashRegister class, but wait! Let&#8217;s try running the tests first. We know they&#8217;ll fail, because we don&#8217;t even have a CashRegister yet! But if we run the tests before writing code, the error messages will tell us what we need to do next. The tests will guide us through the implementation of our class. So, as I mentioned earlier, we can run the tests by doing this:
  </p>
  
  <pre>$ ruby register.rb</pre>
  
  <p>
    We get this as output:
  </p>
  
  <pre>Loaded suite register
Started
E
Finished in 0.000853 seconds.

1) Error:
test_default_is_zero(TestRegister):
NameError: uninitialized constant TestRegister::CashRegister
register.rb:5:in `setup'

1 tests, 0 assertions, 0 failures, 1 errors, 0 skips

Test run options: --seed 36463</pre>
  
  <p>
    Whoah! Okay, so you can see that we had one test, one error. Since we know classes are constants in Ruby, we know that the uninitialized constant error means we haven&#8217;t defined our class yet! So let&#8217;s do that. Go ahead and stick in an empty class at the bottom:
  </p>
  
  <pre>class CashRegister
end</pre>
  
  <p>
    And run the tests again. You should see this:
  </p>
  
  <pre>1) Error:
test_default_is_zero(TestRegister):
NoMethodError: undefined method `total' for #&lt;CashRegister:0x00000101032a80&gt;
register.rb:9:in `test_default_is_zero'</pre>
  
  <p>
    Progress! Now it says we don&#8217;t have a total method. So let&#8217;s define an empty one. Modify the class like this:
  </p>
  
  <pre>class CashRegister
  def total
  end
end</pre>
  
  <p>
    And run the tests again. Another failure:
  </p>
  
  <pre>1) Failure:
test_default_is_zero(TestRegister) [register.rb:9]:
Expected 0, not nil.</pre>
  
  <p>
    Okay! No more syntax errors, just the wrong result. Let&#8217;s keep it as simple as possible, and fill out a nice and easy total method:
  </p>
  
  <pre>def total
  0
end</pre>
  
  <p>
    Now, you may be saying, &#8220;Steve, that doesn&#8217;t calculate a total!&#8221; Well, you&#8217;re right. It doesn&#8217;t. But our tests aren&#8217;t yet asking to calculate a total, they&#8217;re just asking for a default. If we want a total, we should write a test that actually demonstrates adding it up. But we have fulfilled objective #3, so we&#8217;re doing good! Now, let&#8217;s work on objective #2, since we sorta feel like the total method is lying about what it&#8217;s supposed to do. In order to add up the items that were scanned, we need to scan them in the first place! Objective #1 says that this method should be called scan, so let&#8217;s write a test. Put it in your test class with the test_default_is_zero method:
  </p>
  
  <pre>def test_total_calculation
  @register.scan 1
  @register.scan 2
  assert_equal 3, @register.total
end</pre>
  
  <p>
    Make sense? We want to scan two things in, and then check that the total is correct. Let&#8217;s run our tests!
  </p>
  
  <pre>Loaded suite register
Started
.E
Finished in 0.000921 seconds.

1) Error:
test_total_calculation(TestRegister):
NoMethodError: undefined method `scan' for #&lt;CashRegister:0x00000101031838&gt;
register.rb:13:in `test_total_calculation'

2 tests, 1 assertions, 0 failures, 1 errors, 0 skips

Test run options: --seed 54501</pre>
  
  <p>
    Okay! See that &#8216;.E&#8217; up there? That graphically shows that we had one test passing, and one test with an error. Our first test still works, but our second is failing because we don&#8217;t have a scan method. Add an empty one to our CashRegister class, and run again:
  </p>
  
  <pre>1) Error:
test_total_calculation(TestRegister):
ArgumentError: wrong number of arguments (1 for 0)
register.rb:24:in `scan'
register.rb:13:in `test_total_calculation'</pre>
  
  <p>
    Whoops! It takes an argument. Let&#8217;s add that: def scan(price). Run the tests!
  </p>
  
  <pre>1) Failure:
test_total_calculation(TestRegister) [register.rb:15]:
Expected 3, not 0.</pre>
  
  <p>
    Okay! This sounds more like what we expected. Our total method just returns zero all the time! Let&#8217;s think about this for a minute. We need to have scan add the price to a list of scanned prices. So we&#8217;d better have it do that:
  </p>
  
  <pre>def scan(item)
  @items &lt;&lt; item
end</pre>
  
  <p>
    But if you run the tests, you&#8217;ll see this:
  </p>
  
  <pre>1) Error:
test_total_calculation(TestRegister):
NoMethodError: undefined method `&lt;&lt;' for nil:NilClass
register.rb:25:in `scan'
register.rb:13:in `test_total_calculation'</pre>
  
  <p>
    Oops! @items is undefined. Let&#8217;s make it be an empty array, when we create our register:
  </p>
  
  <pre>def initialize
  @items = []
end</pre>
  
  <p>
    And run the tests:
  </p>
  
  <pre>1) Failure:
test_total_calculation(TestRegister) [register.rb:15]:
Expected 3, not 0.</pre>
  
  <p>
    Okay! We&#8217;re back to our original failure. But we&#8217;ve made some progress: now that we have an actual list of items, we&#8217;re in a position to make our total method work. Also, at each step, even though one test was failing, the other was still passing, so we know that we didn&#8217;t break our default functionality while we were working on getting a real total going.
  </p>
  
  <p>
    Now, we&#8217;re in a better place to calculate the total:
  </p>
  
  <pre>def total
  @items.inject(0) {|sum, item| sum += item }
end</pre>
  
  <p>
    Or, if you want to make it even shorter:
  </p>
  
  <pre>def total
  @items.inject(0, &:+)
end</pre>
  
  <p>
    If you&#8217;re not familiar with <code>Enumerable#inject</code>, it takes a list of somethings and turns it into a single something by means of a function, in a block. So in this case, we can keep a running sum of all items, and then add the price of each one to the sum. Done! Run your tests:
  </p>
  
  <pre>Started
..
Finished in 0.000762 seconds.

2 tests, 2 assertions, 0 failures, 0 errors, 0 skips</pre>
  
  <p>
    Woo hoo! We&#8217;re done! Our total can now be calculated. Great job!
  </p>
  
  <p>
    Now, here&#8217;s a challenge, to see if you&#8217;ve really learned this stuff: write a test for a new method, clear, that clears the total. That&#8217;s objective #4 we talked about above.
  </p>
  
  <h4>
    Other parts of minitest
  </h4>
  
  <p>
    This has been a mini intro to minitest and using it to test your code. There are other methods in the <code>assert</code> family, too, like <code>assert_match</code>, which takes a regular expression and tries to match it against something. There&#8217;s the <code>refute</code> family of tests, which are the opposite of <code>assert</code>:
  </p>
  
  <pre>assert true #=&gt; pass
refute true #=&gt; fail</pre>
  
  <p>
    There are also other tools that make minitest useful, like mocks, benchmark tests, and the RSpec-style &#8216;spec&#8217; syntax. Those will have to wait until later! If you&#8217;d like to learn about them now, check out <a href="https://github.com/seattlerb/minitest">the source code on GitHub.</a>
  </p>
  
  <p>
    Happy testing!
  </p>
  
  <p class="update">
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post.</em> Also, do check out Steve&#8217;s other article: &#8220;<a href="http://rubylearning.com/blog/2010/12/20/how-do-i-keep-multiple-ruby-projects-separate/">How do I keep multiple Ruby projects separate?</a>&#8221; on RubyLearning. Thanks!
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/minitest" rel="tag">minitest</a>, <a href="http://technorati.com/tag/Programming" rel="tag"> Programming</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>
