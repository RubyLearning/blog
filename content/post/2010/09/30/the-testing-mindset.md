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
---
This guest post is contributed by **[Noel
Rappin](http://www.railsrx.com/)**, who is a Senior Consultant with
Obtiva, and has been a professional web developer for a dozen years. He
is the author of four technical books. The most recent, *Rails Test
Prescriptions*<!--more-->, is available for purchase at
[http://www.pragprog.com/titles/nrtest/rails-test-prescriptions](http://www.pragprog.com/titles/nrtest/rails-test-prescriptions).
Noel has a Ph.D. from the Georgia Institute of Technology, where he
studied educational technology and learner-centered design. You can find
Noel on Twitter as [@noelrap](http://www.twitter.com/noelrap).

![Noel Rappin](http://rubylearning.com/images/new_head.jpg) If you want
your Test-Driven Development (TDD) process to be effective, you need to
have a testing mindset. Choosing the right tools helps, but the
difference between using the TDD process well and using the TDD process
poorly is much larger than any difference between tools.

If you've heard anything about testing, you've been told that the
process is "red, green, refactor", that is "write a failing test, make
it pass, clean it up". In order to use that process effectively, you
need to get in the habit of "thinking TDD" as you attack a problem.
Features of thinking TDD are:

-   The ability to break a task down into tiny, component pieces.
-   An embrace of the simplest solution to the problem.
-   A willingness to live with code that may feel unfinished until you
    write more tests.

The first one is not hard, and gets easier with practice. The second and
third are the ones that I struggle with. The temptation to move your
code just a little beyond your tests, or to put that little code
filigree is very compelling, and almost always winds up being regretted.

I want to look at the testing mindset in solving a small problem that I
first presented [as a small Ruby
Kata](http://railsrx.com/2010/09/27/a-quick-ruby-kata/):

Find all the unique sequences of digits, like [1, 1, 2, 3, 8] that have
the following properties:

-   Each element of the sequence is a digit between 1 and 9
-   The digits add to 15
-   There is at least digit that appears exactly twice
-   No digit appears more than twice
-   Order is irrelevant [1, 1, 2, 3, 8] and [1, 3, 2, 1, 8] are the same
    sequence and only count once.

There are 38 sequences.

At first glance, it seems like this problem would be hard to write in a
test-driven way. If you start from the end result and try to do the
whole thing in one try, then you wind up trying to test the final 38
number. That's a hard way to go. The first step is to try and find a
part of the problem that is small and verifiable.

After I little bit of analysis, I broke the problem into three parts.
The first, and probably the easiest to understand, is how to verify
whether a given sequence meets the parameters of the problem. The
parameters are reasonably simple and easy to verify.

The second problem is to determine which sequences of numbers to test. I
decided to solve this problem with a search through the potential
sequences using a mechanism where each sequence would be able to say
which sequence to test next. In other words, the problem starts by
testing [1], determines that does not meet the requirements, then asks
the sequence what to test next. The way I thought the problem through,
that sequence is [1, 1]. This is far from the only way to solve the
problem. However, by walking through the sequence this way, we have a
simple, easy to verify, fact about each sequence --- what comes after it
in order.

The third part of the test is a loop that walks through the sequences
and verifies each on in turn. We'll come back to that in a moment.

I start by setting up an RSpec file, and write out my first specs. The
first one is an easy one, just to make sure I can create my object and
do the basics.

      it "should be able to sum its items" do
        sequence = Sequence.new(1, 2, 3, 4)
        sequence.sum.should == 10
      end

Getting there is pretty easy.

    class Sequence

      attr_accessor :elements, :status

      def initialize(*elements)
        @elements = elements
      end

      def sum
        elements.inject { |sum, n| sum + n }
      end

    end

The verification steps are all laid out in the problem. The first one,
of course, is the sum.

      it "is valid if the sum is 15" do
        sequence = Sequence.new(1, 1, 7, 6)
        sequence.should be_valid
        sequence = Sequence.new(1, 1, 7, 7)
        sequence.should_not be_valid
      end

Two things to note. One is that I'm testing both the positive and
negative conditions (strictly speaking, those should probably be in two
different tests). Two is that I've picked a positive sequence that I
know will stay valid even after I add the other constraints. That makes
the test more stable as I add new requirements.

At this point, we pass with:

      def valid?
        sum == 15
      end

Gotta admit, that's pretty simple. This is where the other two parts of
the testing mindset come in. If you are a conscientious developer, then
part of you is screaming on the inside that this is too simple, and it's
incomplete. The temptation to add the next piece of the code right now
is pretty strong. Resist. Things are better if you go one step at a
time.

The next step is this test:

      it "is invalid if there is no pair" do
        sequence = Sequence.new(8, 7)
        sequence.should_not have_digit_pair
        sequence.should_not be_valid
      end

I don't need a positive test here, because my first test already covers
it, though if you wanted to insist that I need a separate test for
`should have_digit_pair`, I wouldn't argue too strenuously.

At this point, I cheat a little bit, because I have this histogram
method pre-tested from other projects, which makes the digit pair method
easy.

      def histogram
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
      end

In this case, `histogram` is an implementation detail --- if I didn't have
it, I would probably write it within the `has_digit_pair?` method and
then refactor it to a separate method on the next step.

The digit trio test and code are similar

      it "is invalid if there is a digit trio" do
        sequence = Sequence.new(1, 1, 1, 5, 7)
        sequence.should have_digit_trio
        sequence.should_not be_valid
      end

      def has_digit_trio?
        histogram.values.any? { |x| x > 2 }
      end

At this point, the `valid?` method has gotten really, really
complicated. Okay, not really:

      def valid?
        !has_digit_trio? && has_digit_pair? && sum == 15
      end

The need to test digit pair and digit trio as separate entities has
eliminated any impulse I might have to write those methods inline in the
valid method, which is an example of how writing in small pieces tends
to give you short and independent code methods.

At this point, I'm comfortable with the verification and it's time for
the order of the sequences. One great feature of TDD that helps with
ordering is that I can specify behavior without caring about
implementation. I have no idea, as I start, what the final
implementation is, but I can specify the behavior in a way that I can
verify whatever implementation I wind up with.

The basic idea here is that each sequence will know what sequence to
test next, and eventually we'll cover the whole space with something
like a while loop. It took a couple tries to get the rules for moving to
the next sequence correct, I'll spare you my back and forth. The first
couple rules are easy.

      it "should start with 1" do
        sequence = Sequence.new
        sequence.next.elements.should == [1]
      end

      it "a sequence with a low sum should spawn a new element" do
        sequence = Sequence.new(1)
        sequence.next.elements.should == [1, 1]
      end

The implementation at this point is also pretty easy:

      def next
        return Sequence.new(1) if elements.empty?
        Sequence.new(*(elements << elements[-1]))
      end

So if the sequence is not empty, we append a duplicate of the last
element to the end of the sequence. This helps guarantee that the digits
in the sequence are in numerical order, which keeps us from having to
worry about duplicate sequences in different orders, but that's beside
the immediate point (if we think there's a problem later, we'll write a
test). The immediate point is that the specs pass, and it's time to
think up the next example of navigation behavior.

It actually might be helpful to code up the actual loop at this point.
As much as I love TDD, it's helpful to see the big picture --- this
example is as much an exploration of the problem as it is a normal
feature, and having the loop in place makes it easy to see how the
ordering method is behaving.

In Ruby 1.9 you can use an Enumerator to walk the sequence. While
building the code, you can augment this with print statements to see
what's going on in a big picture sense, while using TDD to add new
features. Technically, since I've refactored this into a class method,
you could even write a test to verify the enumerator, although I didn't
when I originally solved the problem.

    def self.sequences
      Enumerator.new do |y|
        sequence = Sequence.new
        while sequence
          sequence = sequence.next
          break unless sequence
          y << sequence
        end
      end
    end

What's cool about that is that invoking the enumerator is very simple:

    if __FILE__ == $0
      result = Sequence.sequences.select { |s| s.valid? }
      p result.size
      p result.map(&:elements)
    end

Okay, the logic at this point goes like this: following the rule we have
so far, the first sequence we test is [1], the next one is [1, 1], and
the next one is [1, 1, 1]. They all fail, which is fine. The relevant
point is that there's no need to then test [1, 1, 1, 2], because we know
it will fail from the trio of 1's. We can move directly on to [1, 1, 2].

We're looking for a small, verifiable step, so to put it another way:

      it "a sequence with a trio should increase its last element" do
        sequence = Sequence.new(1, 1, 1)
        sequence.next.elements.should == [1, 1, 2]
      end

Which makes our developing program:

      def next
        return Sequence.new(1) if elements.empty?
        if has_digit_trio?
          elements[-1] += 1
          return Sequence.new(*elements)
        elsif sum < 15
          Sequence.new(*(elements << elements[-1]))
      end

Hey, we got a nice little side benefit from writing the digit trio
method separately, we get to use it here.

At this point the program will hum along merrily until it gets to a
sequence whose sum is over 15. (You can verify this by running the
program via the enumerator). What we want when a sequence sum gets too
high is to again stop, back up, and take the next to last digit and
increase it. Or:

      it "a sequence whose sum is too high should back up an element" do
        sequence = Sequence.new(1, 1, 2, 2, 3, 3, 4)
        sequence.next.elements.should == [1, 1, 2, 2, 3, 4]
      end

Our next method is starting to get kind of complex:

    def next
      return Sequence.new(1) if elements.empty?
      if has_digit_trio?
        elements[-1] += 1
        return Sequence.new(*elements)
      elsif sum < 15
        return Sequence.new(*(elements << elements[-1]))
      elsif sum >= 15
        new_elements = elements[0 .. -2]
        new_elements[-1] += 1
        return Sequence.new(*new_elements)
      end
    end

Two more pieces, both of which work toward ending the sequence. We need
to make sure that no digit goes over 9, and we need to make sure the
sequence ends.

      it "a sequence should not let a digit get over 9" do
        sequence = Sequence.new(1, 9, 5)
        sequence.next.elements.should == [2]
      end

      it "the last sequence should end" do
        sequence = Sequence.new(9, 6)
        sequence.next.should be_nil
      end

Which we can solve with:

    def next
      return Sequence.new(1) if elements.empty?
      if has_digit_trio?
        elements[-1] += 1
        return Sequence.new(*elements)
      elsif sum < 15
        return Sequence.new(*(elements << elements[-1]))
      elsif sum >= 15
        new_elements = elements[0 .. -2]
        if new_elements[-1] == 9
          return nil if new_elements.size == 1
          new_elements = new_elements[0 .. -2]
        end
        new_elements[-1] += 1
        return Sequence.new(*new_elements)
      end
    end

It's a little ugly, but I actually don't see all that much in the way of
necessary refactoring. I admit that the code as it stands is a little
goofy in terms of whether Sequence objects are mutable or not, but it
doesn't interfere with solving the problem. Which is the point. If I
need to worry about Sequence objects being immutable, I need to write
additional tests to drive that change in logic. If I want to just
refactor without changing logic, I can clean up as much as I want with
some confidence that the tests will catch any errors.

Now, running the entire sequence will return the 38 sequences that solve
this problem, with nearly the entire program under test. We were able to
isolate small pieces of a more complex problem and turn them into
concrete, verifiable pieces of code that enabled us to organically build
the larger program.

If you want to see my complete solution, the tests are at
[http://gist.github.com/602077](http://gist.github.com/602077) and the
program code is at
[http://gist.github.com/602076](http://gist.github.com/602076). Other
solutions, with different assumptions and methods, are referenced in the
original blog post at
[http://railsrx.com/2010/09/27/a-quick-ruby-kata/](http://railsrx.com/2010/09/27/a-quick-ruby-kata/).

*I hope you found this article valuable and that it gives you an insight
into the "Testing Mindset". Feel free to ask questions and give feedback
in the comments section of this post. Thanks!*

***Do read* these awesome Guest Posts:**

-   [An Introduction to Desktop Apps with
    Ruby](http://rubylearning.com/blog/2010/09/29/an-introduction-to-desktop-apps-with-ruby/)
-   [The Ruby
    movement](http://rubylearning.com/blog/2010/09/28/the-ruby-movement/)
-   [Almost everything is an object (and everything is almost an
    object!)](http://rubylearning.com/blog/2010/09/27/almost-everything-is-an-object-and-everything-is-almost-an-object/)
-   [So... you're new to
    Ruby!](http://rubylearning.com/blog/2010/09/24/so-youre-new-to-ruby/)
-   [Incorporating Web APIs to spark computer programming
    exercises](http://rubylearning.com/blog/2010/09/23/incorporating-web-apis-to-spark-computer-programming-exercises/)
-   [14 Ways To Have Fun Coding
    Ruby](http://rubylearning.com/blog/2010/09/22/14-ways-to-have-fun-coding-ruby/)
-   [Writing modular web applications with
    Rack](http://rubylearning.com/blog/2010/09/21/writing-modular-web-applications-with-rack/)
-   [How to Learn Ruby (or any programming
    language)](http://rubylearning.com/blog/2010/09/20/how-to-learn-ruby-or-any-programming-language/)

