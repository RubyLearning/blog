---
draft: false
title: The Testing Mindset
date: 2010-09-30
author: Noel Rappin
categories:
- Beginners
- Ruby
- Ruby Masters
layout: post
permalink: /2010/09/30/the-testing-mindset/
tags:
- Noel Rappin
- programming
- Ruby
- Ruby Beginners
- Ruby for Noobs
- Testing Mindset
topsy_short_url:
- http://bit.ly/cGa2QP
---

<div>
  <h3>
    The Testing Mindset
  </h3>
  
  <p class="update">
    This guest post is contributed by <strong><a href="http://www.railsrx.com/">Noel Rappin</a></strong>, who is a Senior Consultant with Obtiva, and has been a professional web developer for a dozen years. He is the author of four technical books. The most recent, <em>Rails Test Prescriptions</em>, is available for purchase at <a href="http://www.pragprog.com/titles/nrtest/rails-test-prescriptions">http://www.pragprog.com/titles/nrtest/rails-test-prescriptions</a>. Noel has a Ph.D. from the Georgia Institute of Technology, where he studied educational technology and learner-centered design. You can find Noel on Twitter as <a href="http://www.twitter.com/noelrap">@noelrap</a>.
  </p>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/new_head.jpg" alt="Noel Rappin" width="125" height="125" /> <span class="drop_cap">I</span>f you want your Test-Driven Development (TDD) process to be effective, you need to have a testing mindset. Choosing the right tools helps, but the difference between using the TDD process well and using the TDD process poorly is much larger than any difference between tools.
  </p>
  
  <p>
    If you&#8217;ve heard anything about testing, you&#8217;ve been told that the process is &#8220;red, green, refactor&#8221;, that is &#8220;write a failing test, make it pass, clean it up&#8221;. In order to use that process effectively, you need to get in the habit of &#8220;thinking TDD&#8221; as you attack a problem. Features of thinking TDD are:
  </p>
  
  <ul>
    <li>
      The ability to break a task down into tiny, component pieces.
    </li>
    <li>
      An embrace of the simplest solution to the problem.
    </li>
    <li>
      A willingness to live with code that may feel unfinished until you write more tests.
    </li>
  </ul>
  
  <p>
    The first one is not hard, and gets easier with practice. The second and third are the ones that I struggle with. The temptation to move your code just a little beyond your tests, or to put that little code filigree is very compelling, and almost always winds up being regretted.
  </p>
  
  <p>
    I want to look at the testing mindset in solving a small problem that I first presented <a href="http://railsrx.com/2010/09/27/a-quick-ruby-kata/">as a small Ruby Kata</a>:
  </p>
  
  <p>
    Find all the unique sequences of digits, like [1, 1, 2, 3, 8] that have the following properties:
  </p>
  
  <ul>
    <li>
      Each element of the sequence is a digit between 1 and 9
    </li>
    <li>
      The digits add to 15
    </li>
    <li>
      There is at least digit that appears exactly twice
    </li>
    <li>
      No digit appears more than twice
    </li>
    <li>
      Order is irrelevant [1, 1, 2, 3, 8] and [1, 3, 2, 1, 8] are the same sequence and only count once.
    </li>
  </ul>
  
  <p>
    There are 38 sequences.
  </p>
  
  <p>
    At first glance, it seems like this problem would be hard to write in a test-driven way. If you start from the end result and try to do the whole thing in one try, then you wind up trying to test the final 38 number. That&#8217;s a hard way to go. The first step is to try and find a part of the problem that is small and verifiable.
  </p>
  
  <p>
    After I little bit of analysis, I broke the problem into three parts. The first, and probably the easiest to understand, is how to verify whether a given sequence meets the parameters of the problem. The parameters are reasonably simple and easy to verify.
  </p>
  
  <p>
    The second problem is to determine which sequences of numbers to test. I decided to solve this problem with a search through the potential sequences using a mechanism where each sequence would be able to say which sequence to test next. In other words, the problem starts by testing [1], determines that does not meet the requirements, then asks the sequence what to test next. The way I thought the problem through, that sequence is [1, 1]. This is far from the only way to solve the problem. However, by walking through the sequence this way, we have a simple, easy to verify, fact about each sequence &#8212; what comes after it in order.
  </p>
  
  <p>
    The third part of the test is a loop that walks through the sequences and verifies each on in turn. We&#8217;ll come back to that in a moment.
  </p>
  
  <p>
    I start by setting up an RSpec file, and write out my first specs. The first one is an easy one, just to make sure I can create my object and do the basics.
  </p>
  
  <pre>  it "should be able to sum its items" do
    sequence = Sequence.new(1, 2, 3, 4)
    sequence.sum.should == 10
  end</pre>
  
  <p>
    Getting there is pretty easy.
  </p>
  
  <pre>class Sequence

  attr_accessor :elements, :status

  def initialize(*elements)
    @elements = elements
  end

  def sum
    elements.inject { |sum, n| sum + n }
  end

end</pre>
  
  <p>
    The verification steps are all laid out in the problem. The first one, of course, is the sum.
  </p>
  
  <pre>  it "is valid if the sum is 15" do
    sequence = Sequence.new(1, 1, 7, 6)
    sequence.should be_valid
    sequence = Sequence.new(1, 1, 7, 7)
    sequence.should_not be_valid
  end</pre>
  
  <p>
    Two things to note. One is that I&#8217;m testing both the positive and negative conditions (strictly speaking, those should probably be in two different tests). Two is that I&#8217;ve picked a positive sequence that I know will stay valid even after I add the other constraints. That makes the test more stable as I add new requirements.
  </p>
  
  <p>
    At this point, we pass with:
  </p>
  
  <pre>  def valid?
    sum == 15
  end</pre>
  
  <p>
    Gotta admit, that&#8217;s pretty simple. This is where the other two parts of the testing mindset come in. If you are a conscientious developer, then part of you is screaming on the inside that this is too simple, and it&#8217;s incomplete. The temptation to add the next piece of the code right now is pretty strong. Resist. Things are better if you go one step at a time.
  </p>
  
  <p>
    The next step is this test:
  </p>
  
  <pre>  it "is invalid if there is no pair" do
    sequence = Sequence.new(8, 7)
    sequence.should_not have_digit_pair
    sequence.should_not be_valid
  end</pre>
  
  <p>
    I don&#8217;t need a positive test here, because my first test already covers it, though if you wanted to insist that I need a separate test for <code>should have_digit_pair</code>, I wouldn&#8217;t argue too strenuously.
  </p>
  
  <p>
    At this point, I cheat a little bit, because I have this histogram method pre-tested from other projects, which makes the digit pair method easy.
  </p>
  
  <pre>  def histogram
    @histogram ||= begin
      @histogram = Hash.new(0)
      elements.each do |digit|
        @histogram[digit] += 1
      end
      @histogram
    end
  end

  def has_digit_pair?
    histogram.values.any? { |x| x == 2 }
  end</pre>
  
  <p>
    In this case, <code>histogram</code> is an implementation detail &#8212; if I didn&#8217;t have it, I would probably write it within the <code>has_digit_pair?</code> method and then refactor it to a separate method on the next step.
  </p>
  
  <p>
    The digit trio test and code are similar
  </p>
  
  <pre>  it "is invalid if there is a digit trio" do
    sequence = Sequence.new(1, 1, 1, 5, 7)
    sequence.should have_digit_trio
    sequence.should_not be_valid
  end</pre>
  
  <pre>  def has_digit_trio?
    histogram.values.any? { |x| x &gt; 2 }
  end</pre>
  
  <p>
    At this point, the <code>valid?</code> method has gotten really, really complicated. Okay, not really:
  </p>
  
  <pre>  def valid?
    !has_digit_trio? && has_digit_pair? && sum == 15
  end</pre>
  
  <p>
    The need to test digit pair and digit trio as separate entities has eliminated any impulse I might have to write those methods inline in the valid method, which is an example of how writing in small pieces tends to give you short and independent code methods.
  </p>
  
  <p>
    At this point, I&#8217;m comfortable with the verification and it&#8217;s time for the order of the sequences. One great feature of TDD that helps with ordering is that I can specify behavior without caring about implementation. I have no idea, as I start, what the final implementation is, but I can specify the behavior in a way that I can verify whatever implementation I wind up with.
  </p>
  
  <p>
    The basic idea here is that each sequence will know what sequence to test next, and eventually we&#8217;ll cover the whole space with something like a while loop. It took a couple tries to get the rules for moving to the next sequence correct, I&#8217;ll spare you my back and forth. The first couple rules are easy.
  </p>
  
  <pre>  it "should start with 1" do
    sequence = Sequence.new
    sequence.next.elements.should == [1]
  end

  it "a sequence with a low sum should spawn a new element" do
    sequence = Sequence.new(1)
    sequence.next.elements.should == [1, 1]
  end</pre>
  
  <p>
    The implementation at this point is also pretty easy:
  </p>
  
  <pre>  def next
    return Sequence.new(1) if elements.empty?
    Sequence.new(*(elements &lt;&lt; elements[-1]))
  end</pre>
  
  <p>
    So if the sequence is not empty, we append a duplicate of the last element to the end of the sequence. This helps guarantee that the digits in the sequence are in numerical order, which keeps us from having to worry about duplicate sequences in different orders, but that&#8217;s beside the immediate point (if we think there&#8217;s a problem later, we&#8217;ll write a test). The immediate point is that the specs pass, and it&#8217;s time to think up the next example of navigation behavior.
  </p>
  
  <p>
    It actually might be helpful to code up the actual loop at this point. As much as I love TDD, it&#8217;s helpful to see the big picture &#8212; this example is as much an exploration of the problem as it is a normal feature, and having the loop in place makes it easy to see how the ordering method is behaving.
  </p>
  
  <p>
    In Ruby 1.9 you can use an Enumerator to walk the sequence. While building the code, you can augment this with print statements to see what&#8217;s going on in a big picture sense, while using TDD to add new features. Technically, since I&#8217;ve refactored this into a class method, you could even write a test to verify the enumerator, although I didn&#8217;t when I originally solved the problem.
  </p>
  
  <pre>def self.sequences
  Enumerator.new do |y|
    sequence = Sequence.new
    while sequence
      sequence = sequence.next
      break unless sequence
      y &lt;&lt; sequence
    end
  end
end</pre>
  
  <p>
    What&#8217;s cool about that is that invoking the enumerator is very simple:
  </p>
  
  <pre>if __FILE__ == $0
  result = Sequence.sequences.select { |s| s.valid? }
  p result.size
  p result.map(&:elements)
end</pre>
  
  <p>
    Okay, the logic at this point goes like this: following the rule we have so far, the first sequence we test is [1], the next one is [1, 1], and the next one is [1, 1, 1]. They all fail, which is fine. The relevant point is that there&#8217;s no need to then test [1, 1, 1, 2], because we know it will fail from the trio of 1&#8217;s. We can move directly on to [1, 1, 2].
  </p>
  
  <p>
    We&#8217;re looking for a small, verifiable step, so to put it another way:
  </p>
  
  <pre>  it "a sequence with a trio should increase its last element" do
    sequence = Sequence.new(1, 1, 1)
    sequence.next.elements.should == [1, 1, 2]
  end</pre>
  
  <p>
    Which makes our developing program:
  </p>
  
  <pre>  def next
    return Sequence.new(1) if elements.empty?
    if has_digit_trio?
      elements[-1] += 1
      return Sequence.new(*elements)
    elsif sum &lt; 15
      Sequence.new(*(elements &lt;&lt; elements[-1]))
  end</pre>
  
  <p>
    Hey, we got a nice little side benefit from writing the digit trio method separately, we get to use it here.
  </p>
  
  <p>
    At this point the program will hum along merrily until it gets to a sequence whose sum is over 15. (You can verify this by running the program via the enumerator). What we want when a sequence sum gets too high is to again stop, back up, and take the next to last digit and increase it. Or:
  </p>
  
  <pre>  it "a sequence whose sum is too high should back up an element" do
    sequence = Sequence.new(1, 1, 2, 2, 3, 3, 4)
    sequence.next.elements.should == [1, 1, 2, 2, 3, 4]
  end</pre>
  
  <p>
    Our next method is starting to get kind of complex:
  </p>
  
  <pre>def next
  return Sequence.new(1) if elements.empty?
  if has_digit_trio?
    elements[-1] += 1
    return Sequence.new(*elements)
  elsif sum &lt; 15
    return Sequence.new(*(elements &lt;&lt; elements[-1]))
  elsif sum &gt;= 15
    new_elements = elements[0 .. -2]
    new_elements[-1] += 1
    return Sequence.new(*new_elements)
  end
end</pre>
  
  <p>
    Two more pieces, both of which work toward ending the sequence. We need to make sure that no digit goes over 9, and we need to make sure the sequence ends.
  </p>
  
  <pre>  it "a sequence should not let a digit get over 9" do
    sequence = Sequence.new(1, 9, 5)
    sequence.next.elements.should == [2]
  end

  it "the last sequence should end" do
    sequence = Sequence.new(9, 6)
    sequence.next.should be_nil
  end</pre>
  
  <p>
    Which we can solve with:
  </p>
  
  <pre>def next
  return Sequence.new(1) if elements.empty?
  if has_digit_trio?
    elements[-1] += 1
    return Sequence.new(*elements)
  elsif sum &lt; 15
    return Sequence.new(*(elements &lt;&lt; elements[-1]))
  elsif sum &gt;= 15
    new_elements = elements[0 .. -2]
    if new_elements[-1] == 9
      return nil if new_elements.size == 1
      new_elements = new_elements[0 .. -2]
    end
    new_elements[-1] += 1
    return Sequence.new(*new_elements)
  end
end</pre>
  
  <p>
    It&#8217;s a little ugly, but I actually don&#8217;t see all that much in the way of necessary refactoring. I admit that the code as it stands is a little goofy in terms of whether Sequence objects are mutable or not, but it doesn&#8217;t interfere with solving the problem. Which is the point. If I need to worry about Sequence objects being immutable, I need to write additional tests to drive that change in logic. If I want to just refactor without changing logic, I can clean up as much as I want with some confidence that the tests will catch any errors.
  </p>
  
  <p>
    Now, running the entire sequence will return the 38 sequences that solve this problem, with nearly the entire program under test. We were able to isolate small pieces of a more complex problem and turn them into concrete, verifiable pieces of code that enabled us to organically build the larger program.
  </p>
  
  <p>
    If you want to see my complete solution, the tests are at <a href="http://gist.github.com/602077">http://gist.github.com/602077</a> and the program code is at <a href="http://gist.github.com/602076">http://gist.github.com/602076</a>. Other solutions, with different assumptions and methods, are referenced in the original blog post at <a href="http://railsrx.com/2010/09/27/a-quick-ruby-kata/">http://railsrx.com/2010/09/27/a-quick-ruby-kata/</a>.
  </p>
  
  <p>
    <em>I hope you found this article valuable and that it gives you an insight into the &#8220;Testing Mindset&#8221;. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
  
  <p>
    <b><em>Do read</em> these awesome Guest Posts:</b>
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/29/an-introduction-to-desktop-apps-with-ruby/">An Introduction to Desktop Apps with Ruby</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/28/the-ruby-movement/">The Ruby movement</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/27/almost-everything-is-an-object-and-everything-is-almost-an-object/">Almost everything is an object (and everything is almost an object!)</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/24/so-youre-new-to-ruby/">So… you’re new to Ruby!</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/23/incorporating-web-apis-to-spark-computer-programming-exercises/">Incorporating Web APIs to spark computer programming exercises</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/22/14-ways-to-have-fun-coding-ruby/">14 Ways To Have Fun Coding Ruby</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/21/writing-modular-web-applications-with-rack/">Writing modular web applications with Rack</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/20/how-to-learn-ruby-or-any-programming-language/">How to Learn Ruby (or any programming language)</a>
    </li>
  </ul>
</div>

