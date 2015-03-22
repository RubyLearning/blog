---
draft: false
title: The value of a personal bug log
date: 2010-10-25
author: Brian Tarbox
categories:
- Beginners
- General
- Ruby Masters
layout: post
permalink: /2010/10/25/the-value-of-a-personal-bug-log/
tags:
- Brian Tarbox
- Personal Bug Log
- programming
---

## The value of a personal bug log

This guest post is by **Brian Tarbox**, who is a Distinguished Member of
Technical Staff at Motorola where he works on Video On Demand Systems.
He also blogs about applying a Wabi Sabi approach to software, cognition
and philosophy at
[briantarbox.blogspot.com](http://briantarbox.blogspot.com/). He is a
regular contributor to the [Pragmatic Programmer
magazine](http://www.pragprog.com/magazines). His open source project
for converting computer log files to music just won an Oracle Duke’s
Choice award.

![Brian Tarbox](http://rubylearning.com/images/Brian.jpg "Brian Tarbox")
Although our field has huge amounts of diversity (languages, platforms,
team maturity) we all share the need to keep up and enhance our skills.
The person nipping at our heels may live in India, or China or just be
recently graduating from a local college. The point is that sharks have
to keep swimming or they die and software engineers have to keep growing
or they become expendable.

Many of the things we do to keep up our skills need the good graces of
others. Attending conferences, going to classes, getting to code a
module in a new language are all things that need permission. Some just
need time while other need your company to spend real money. Some
companies have policies about continuing education while others do not.
In either case there is a fair chance that your request will get a “no”
(though that shouldn’t stop you from asking). Things like attending a
Users Group meeting don’t tend to cost anything but those of you with
families are likely familiar with the process of negotiating evenings
off. Your mileage may vary.

While I have a very understanding wife and an encouraging boss I don’t
like to rely on others for my career. So I look for no-cost,
no-permission-required things I can do to keep up and enhance my skills.
Maintaining a personal bug diary is a great way to do that.

At this point allow me a segue to illustrate a point. I’m a private
pilot and so I’ve spent a lot of time learning to fly and reading up
about the process of learning to fly. A key milestone in this learning
is getting to your first solo flight. In the private sector there is an
enormous range in the amount of training time required for the first
solo. Some take as little as nine hours of instruction while others take
over a hundred. I was somewhere in the middle. In the military they have
a much more standardized approach which results in new pilots getting to
solo in remarkably small number of training hours. The secret is that
after flight they do a post-flight review. They go over every aspect of
the flight, highlighting the good and bad decisions that the student
pilot made. This anchors and solidifies the training so it has greater
impact.

Maintaining a personal bug log serves the same purpose: creating a
little learning experience from each bug.

The conventional wisdom says that the process of dealing with a bug is:

-   create a test case that demonstrates the bug
-   fix the bug, i.e. code until the test case passes
-   check in the code, close the bug in your bug system
-   never think about the bug again

It’s that last point that we want to change. I’m suggesting we change
that last step to “think about why the bug got past the unit and system
tests”. The answer might be that a requirement changed, that a user
tried something you hadn’t thought of, or that a unit test was less
thorough than you thought. The reasons you discover for your bugs will
vary, both with your environment and with your level of honesty. Be open
to the bug reason “because I messed up”. Remember, this is not a log
that you have to share with anyone, it’s the log you keep as a way to
get better.

One of the nice things about learning to fly was that I knew I didn’t
know how. So I was able to leave my ego on the ground and acknowledge
that on such and such a flight my landing was bad because I let myself
get distracted, or I forgot to factor in the crosswind or whatever. As
programmers we often let our pride get in the way of acknowledging our
mistakes. This of course leads us to make the mistake again.

As an experiment try maintaining a bug log for a month. At the end of
the month look back and see if you notice any patterns. This are areas
where you need to change your behavior, and that’s a fair definition of
learning.

*I hope you found this article valuable. Feel free to ask questions and
give feedback in the comments section of this post. Thanks!*

***Do read* this awesome Guest Post:**

-   [Do You Enjoy Your Code
    Quality?](http://rubylearning.com/blog/2010/10/18/do-you-enjoy-your-code-quality/)
