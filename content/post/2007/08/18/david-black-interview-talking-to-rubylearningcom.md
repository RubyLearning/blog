---
author: Satish Talim
categories:
- beginners
- interview
- rails
- ruby
- training
date: 2007-08-18
layout: post
title: 'David Black Interview: Talking to RubyLearning.com'
---

[![David
Black](http://www.rubylearning.com/images/david.jpg)](http://www.rubylearning.com/images/david.jpg "David Black")

*Today, I had the good fortune to talk to David Black the author of the
very popular book “[Ruby for Rails](http://www.manning.com/black/)“, on
behalf of all the [RubyLearning.com](http://rubylearning.com/) members.
I have been recommending his book to one and all and if you have not
read it yet, do buy yourself a copy.*

**Hello David, and welcome to RubyLearning.com. Why don’t we start with
a little bit of your background?**

I’m a self-taught computer programmer, currently specializing in Ruby
and Rails. My education includes an undergraduate double-major in German
and History of Art, and a Ph.D. in Cinema Studies. I’m also a
professionally-trained cellist.

For thirteen years, I taught in the Department of Communication at Seton
Hall University in New Jersey, USA. My curriculum was mainly media
history and research. At the same time, I was getting more and more into
computer programming, something that had been an interest of mine
literally for decades.

In the Fall of 2005, I was scheduled to start a one-year sabbatical from
the university. By that time, I was deeply involved in all sorts of Ruby
and Rails activities – including writing my first Ruby book, “Ruby for
Rails”. I decided that instead of taking the research leave, I would
resign from the university and pursue computer programming, writing, and
training full-time. That’s what I’ve been doing for the past two years.

I started using Ruby in 2000, right when the first edition of
“Programming Ruby” (the Pickaxe book) came out. I’ve written two Ruby
and/or Rails books (“Ruby for Rails” and “Rails Routing”), and I have my
own consultancy, [Ruby Power and Light, LLC](http://www.rubypal.com/).
I’m also one of the founding directors of [Ruby Central,
Inc.](http://www.rubycentral.org), the parent organization of the annual
International Ruby Conference (“RubyConf”) and the International Rails
Conference and RailsConf Europe.

**What according to you is the best approach to learn the Ruby
programming language?**

Same as with any language: write lots of code! I strongly recommend that
people make heavy use of IRB, the interactive Ruby console. It’s great
for learning how Ruby works. Of course, if you’re trying out something
that’s more than a few lines long, you’ll probably want to put it in a
file and run it.

Once you’ve bootstrapped yourself into some understanding of the Ruby
language, a good next step is to familiarize yourself with the unit
testing framework, TestUnit. (I don’t talk about testing in “Ruby for
Rails”, but as I explain in the preface, that’s because I wanted the
book to explore certain things in depth, not because testing is a bad
idea!)

I’ve also learned a ton about Ruby by answering people’s questions on
mailing lists and IRC channels. If I see a question and I don’t know the
answer, I generally feel that as a Ruby programmer, I \*should\* know
the answer – so I go figure it out, and then answer the question. And of
course someone else might come back with a better answer, and then I
learn even more.

I also recommend letting Ruby talk to you. Don’t project your
expectations onto Ruby. A great deal of the trouble I see people having
with Ruby comes about because they can’t believe it’s as simple as it
is. For example, there’s a simple rule that every time you see an
instance variable (such as @var), that instance variable belongs to
“self” (the default object) – whatever self may happen to be at that
point. There are no exceptions to this. So the answer to the question,
“What is this instance variable? Who can access it?” is always exactly
the same: it belongs to **self**. Just figure out what self is, and you
know what object governs that particular @var.

**Which areas in Ruby should a would-be Ruby programmer concentrate
on?**

Speaking of “self”: I recommend looking very closely at self.
Understanding self will help you understand a lot of what’s going on.
Ruby is like a novel with a different narrator for each chapter: the
role of self, or “I”, keeps changing, but there’s always an “I”. You
should try to develop a feel for how the role of self gets handed around
during execution.

Much too much fuss is made over the complexity of Ruby’s class model,
which is actually quite simple. It’s worth spending some time getting a
grasp on it, so that you can understand how objects resolve method calls
by searching through the classes and modules in their look-up paths.

Iterators, blocks, and procs can be tricky (and some of their syntax and
semantics is in flux as between Ruby 1.8 and Ruby 1.9/2.0), but they’re
important and powerful and just plain cool! I’d recommend becoming as
familiar as possible with how they work. When you see that there are at
least four ways to create a Proc object, don’t despair: it doesn’t go on
forever, and if you wonder whether it’s all a bit murky, you’re not the
first. But you’ll soon pinpoint the key concepts: closures, iteration,
capturing blocks in methods, etc.

**What do you think are the most exciting developments going on in Ruby
right now?**

The new implementations (JRuby, IronRuby, Rubinius) are very exciting.
As a long-time Ruby conference organizer (I co-organized RubyConf 2001,
the first one), I’m also thrilled to see that regional conferences are
flourishing. These events are really well produced and full of
interesting content. It’s also very gratifying to go into bookstores and
see an entire Ruby shelf. That’s something very new, from my archaic
perspective!

**According to you, how important is it for a would-be Ruby programmer
to know JRuby and / or IronRuby?**

Both of those implementations aim for compatibility with the standard
Ruby distribution, so if you know Ruby, you presumably know JRuby and
IronRuby. Of course each of them has a particular focus, in terms of
interoperability and programming context. So interest will be guided by
those concerns too.

**When do you think is the right time to start learning Rails?**

If you’re a Ruby programmer already, then any time you develop an
interest in it. If you’re not, then I would recommend learning at least
some Ruby first, or learning them together. That’s really why I wrote
“Ruby for Rails”: to give support to people whose main goal is learning
Rails, but who want to do it right. You can’t do Rails right without
some Ruby expertise, but you don’t have to postpone learning Rails
forever. After all, Rails applications are Ruby programs.

**On a final note: What do you perceive as the future of Ruby?**

I’m not clairvoyant – I don’t perceive the future
![:-)](http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif)
The present is awfully exciting, with lots going on and a lot to do. It
will certainly be exciting to see what the next “big thing” in Ruby
turns out to be. Meanwhile I’m enjoying my work with Rails, and I hope
both Ruby and Rails continue to flourish.

*Thanks David for sharing your views with the RubyLearning.com members.
I am confident that your insights would help all the would-be Ruby
programmers.*

Technorati Tags: [David Black](http://technorati.com/tag/David+Black),
[David Black Interview: Talking to
RubyLearning.com](http://technorati.com/tag/David+Black+Interview%3A+Talking+to+RubyLearning.com),
[Interviews](http://technorati.com/tag/Interviews),
[IronRuby](http://technorati.com/tag/IronRuby),
[JRuby](http://technorati.com/tag/JRuby),
[Ruby](http://technorati.com/tag/Ruby), [Ruby on
Rails](http://technorati.com/tag/Ruby+on+Rails), [Ruby
Interviews](http://technorati.com/tag/Ruby+Interviews), [Ruby
Training](http://technorati.com/tag/Ruby+Training)
