---
draft: false
title: How does your code smell?
date: 2010-11-08
author: Kevin Rutherford
categories:
- Beginners
- Ruby
- Ruby Masters
layout: post
permalink: /2010/11/08/how-does-your-code-smell/
tags:
- programming
- Reek
- ruby programming
---
## How does your code smell?

This guest post is by **Dr. Kevin Rutherford**, a UK-based agile/XP
coach, developer and project leader, with over 25 years experience in
software development. He is also the founder of AgileNorth and
XP-Manchester. Contact him
via [http://www.kevinrutherford.co.uk](http://www.kevinrutherford.co.uk/).

![Dr. Kevin
Rutherford](http://rubylearning.com/images/kr-bw-125x125.jpg) I expect
you’re a conscientious modern developer. You write your code using
test-driven or behaviour-driven development, and you never write a line
of production code unless it is needed in order to make a test pass. But
there’s more to TDD than RED-GREEN-RED-GREEN; you have to REFACTOR each
time the tests go green. Specifically, we write a test and see it fail;
then we write code in the most straightforward way we possibly can to
make it pass; then we refactor to clean up any mess we just made. But in
that third step, just what should we refactor, and why? And if we need
to refactor a pile of code that wasn’t developed in a test-driven
manner, how do we get a handle on where to begin?

Refactoring is defined as improving software without changing what it
does. The intention is to take bad code and replace it with something
better. The next question must then be: What is “good code” and what is
“bad code”? How can we tell them apart and recognize which is which? And
when we can recognize bad code, what should we do to eliminate it? The
best guiding principle here is the four rules of [Simple
Design](http://c2.com/xp/XpSimplicityRules.html), first described by
Kent Beck in the early descriptions of Extreme Programming. As
[re-expressed by
J.B.Rainsberger](http://www.jbrains.ca/permalink/the-four-elements-of-simple-design),
the design of a piece of code is “simple” when it:

1.  Passes its tests
2.  Minimizes duplication
3.  Maximizes clarity
4.  Has fewer elements

So that’s it: First ensure that your code passes all its tests, then
remove all duplication, then make sure the design intent is clear, and
then get rid of anything that doesn’t need to be there. Easy! But
“duplication” and “clarity” are non-trivial concepts. For example, it is
usually easy to see when a chunk of code has been copied and pasted, but
far less easy to see when a piece of knowledge, or a responsibility,
exists in more than one place. Textual duplication can be detected by
tools, but the more subtle kinds cannot. Similarly, the use of clear
names can appear subjective; maybe a name I believe to be clear confuses
you, and vice versa. Our goal is Simple Design, but the path to
simplicity may be very unclear.

To help with this difficulty, the agile community has developed informal
names for the most common kinds of “bad” code. These are anti-patterns,
and are often called “code smells,” after Kent Beck’s analogy between
code and babies: “If it stinks, change it”. Reflecting the rules of
Simple Design, code smells come in two major varieties: they either make
the code harder to understand, or something in the code is duplicated
(which more than doubles the risk involved in making future changes).
However, until recently there has been no catalog of the kinds of smell
you might find in Ruby code, and Bill Wake and I set about remedying
that problem with our book [Refactoring in
Ruby](http://www.refactoringinruby.info/). Here’s a list of the major
types of code smell we identified, grouped approximately according to
their impact on the rules of Simple Design:

  ----------------------------------------------- --------------------------------
  **Duplication**                                 **Names**
  Alternative Modules with Different Interfaces   Comments
  Combinatorial Explosion                         Complicated Boolean Expression
  Control Coupling                                Divergent Change
  Data Class                                      Dynamic Code Creation
  Data Clump                                      Global Variable
  Derived Value                                   Implementation Inheritance
  Duplicated Code                                 Inappropriate Intimacy
  Feature Envy                                    Incomplete Library Module
  Greedy Method                                   Inconsistent Names
  Greedy Module                                   Long Parameter List
  Large Module                                    Nil Check
  Lazy Class                                      Runaway Dependencies
  Long Method                                     Shotgun Surgery
  Message Chain                                   Simulated Polymorphism
  Middle Man                                      Special Case
  Open Secret                                     Speculative Generality
  Parallel Inheritance Hierarchies                Temporary Field
  Procedural Code                                 Type Embedded in Name
  Refused Bequest                                 Uncommunicative Name
  Reinvented Wheel                                Utility Function
  Repeated Value
  ----------------------------------------------- --------------------------------

For each different code smell identified, we give a set of tell-tale
symptoms so you can spot it easily, an indication of what refactorings
you can do to remove the smell, and an indication of what other smells
you might reveal as you do so. For example, here’s a brief summary of
one code smell from the catalog:

**Feature Envy**\
 *What To Look For:*

-   Code references another object more than it references itself, or
-   Several clients manipulate a particular type of object in similar
    ways.

*What To Do:*

-   Extract Method to isolate the envious code
-   Move Method to put it with the referenced object

*What To Look For Next:*

-   Duplication: Look for further duplication around the clients
-   Communication: Review names for the receiving class for consistency

[Refactoring in Ruby](http://www.refactoringinruby.info/) also provides
hundreds of challenges, exercises that will help you practice detecting
and removing smells from working Ruby code. For example, take a look at
the following code; which smells can you see?

    # Creates a report showing machine activity
    class Report
      def report(machines)
        statuses = machines.map { |machine| status(machine) }
        "FACTORY REPORT\n#{statuses.join("\n")}\n"
      end

      def status(machine)
        activity = machine.bin == nil ? '' : " bin=#{machine.bin}"
        "Machine #{machine.name}#{activity}\n"
      end
    end

As a companion to the book I have also created a very naive code smell
detector tool called
[Reek](https://github.com/kevinrutherford/reek/wiki). Reek cannot
perform enough static analysis to detect every code smell listed, but it
does a reasonable job of detecting some forms of Class Variable, Control
Couple, Data Clump, Duplication, Irresponsible Module, Large Class, Long
Method, Long Parameter List, Feature Envy, Utility Function, Nested
Iterators, Simulated Polymorphism and Uncommunicative Name. For example,
consider the little source file above; Reek reports the following code
smells:

    $ reek simple_report.rb
    simple_report.rb -- 3 warnings:
      Report#status calls machine.bin twice (Duplication)
      Report#status doesn't depend on instance state (LowCohesion)
      Report#status refers to machine more than self (LowCohesion)

Reek can also produce a YAML report giving extra details such as line
numbers:

    $ reek --yaml simple_report.rb
    ---
    - !ruby/object:Reek::SmellWarning
      location:
        lines:
        - 9
        - 9
        context: Report#status
        source: simple_report.rb
      smell:
        class: Duplication
        occurrences: 2
        subclass: DuplicateMethodCall
        call: machine.bin
        message: calls machine.bin twice
      status:
        is_active: true
    - !ruby/object:Reek::SmellWarning
      location:
        lines:
        - 8
        context: Report#status
        source: simple_report.rb
      smell:
        class: LowCohesion
        subclass: UtilityFunction
        message: doesn't depend on instance state
      status:
        is_active: true
    - !ruby/object:Reek::SmellWarning
      location:
        lines:
        - 8
        context: Report#status
        source: simple_report.rb
      smell:
        class: LowCohesion
        subclass: FeatureEnvy
        receiver: machine
        message: refers to machine more than self
        references: 3
      status:
        is_active: true

As you can see, this report is a little rough around the edges, and
there are still many more code smells that Reek could detect. But even
in its current draft state many people find Reek helpful, either as a
part of their build process (the Reek gem includes an easy-to-use Rake
task) or on an *ad hoc* basis. If you try it please [let me
know](http://groups.google.com/group/ruby-reek) how well it works for
you.

*I hope you found this article valuable. Feel free to ask questions and
give feedback in the comments section of this post. Thanks!*

***Do also read* these awesome Guest Posts:**

-   [Do YOU know Resque?](/blog/2010/11/08/do-you-know-resque/)
-   [Do You Understand Ruby’s Objects, Messages and Blocks?](/blog/2010/11/03/do-you-understand-rubys-objects-messages-and-blocks/)
-   [How Does One Use Design Patterns In Ruby?](/blog/2010/11/02/how-does-one-use-design-patterns-in-ruby/)
-   [Do you know what’s new in Ruby 1.9?](/blog/2010/10/26/do-you-know-whats-new-in-ruby-1-9/)
-   [The value of a personal bug log](/blog/2010/10/25/the-value-of-a-personal-bug-log/)
-   [Do You Enjoy Your Code Quality?](/blog/2010/10/18/do-you-enjoy-your-code-quality/)

