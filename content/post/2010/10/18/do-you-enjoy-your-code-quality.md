---
draft: false
title: Do You Enjoy Your Code Quality?
date: 2010-10-18
author: James Schorr
categories:
- Beginners
- Popular
- Ruby
- Ruby Masters
layout: post
permalink: /2010/10/18/do-you-enjoy-your-code-quality/
tags:
- Code Quality
- James M. Schorr
- programming
---

This guest post is by **James Schorr**, who has been developing software
since 1999. He is the owner of an IT consulting company, [Enspiren IT
Consulting, LLC](https://enspirenconsulting.com).  He lives with his
lovely wife, Tara, and their children in Kansas City, Missouri. James
spends a lot of time writing code in many languages, doing IT security
audits, and has a passion for Ruby on Rails in particular. He also loves<!--more-->
spending time with his family, playing chess, going to the shooting
range, hiking, fishing, and investing. His professional profile is
on [LinkedIn](http://www.linkedin.com/in/jamesschorr).

![James M. Schorr](http://rubylearning.com/images/James_Schorr.png)

## Do You Enjoy Your Code Quaility?

There's something innately satisfying about programming; or, at least,
there should be. It's a creative act in and of itself that has
incredible power and potential to affect change. Craftsmanship, in and
of itself, typically attracts those who like to think outside the box
and those who like to create. In this way, it really is more of an art
than anything else and can produce a great deal of satisfaction and
delight.

Compare the carpenter that hand-crafts a beautiful cabinet to a factory
worker who pushes buttons to cause a machine to form identical cabinets
over and over again. While both can experience a measure of satisfaction
in their work, only the carpenter enjoys long-term satisfaction. The
goal of this article is to enable you to improve code quality and, thus,
transform the mundane into the beautiful. No matter where you're at on
the spectrum, beginner to advanced, there is always room for
improvement. As the code quality improves, your ability to delight in it
and enjoy what you're doing does as well.

I have a number of applications in Production and have learned a lot
over the years about the code quality, systems, and programming in
general. I've also been regularly called on to carefully check a
tremendous amount of others' source code in my consulting business and
earlier jobs. Here are some practical, real-world ways to improve your
code quality and development habits in general. I have learned the hard
way on a few of these. Some may only apply to the non-employee
developer, but almost all are pretty universal:

## Pre-Development

-   Gather the requirements and "stories" from the client. I like the
    idea of stories better because it's more in line with how the
    non-developer thinks. In other words, "I want A to happen as a B
    when I do C". Make sure that those you're meeting with are told to
    come prepared with as much information as possible, especially from
    the end users of the planned application.
-   Question every need and distill them down by asking "Why?" In
    general, the requirements of users are based on what they know the
    possibilities are and what they've used before. You, however, may
    quickly see that a need is better met a different way, or even cause
    issues if fulfilled.
-   Clarify what is necessary and "nice-to-have", as this has a direct
    impact on the timeline and budget.
-   Refuse to reproduce lousy software. In other words, turn down work,
    if necessary, that will need you to reproduce some other system that
    wasn't designed well unless you're given the freedom to do it right.
    It's just not worth it, both for you or the users. How do you
    recognize lousy software? Look at the UI, speed, security, and
    stability; would you want to use it?
-   Reject unrealistic timelines nicely, "Yes, I could do this in 3
    months, but you won't get the quality that you deserve. To do this
    right, we need 5 months." Stick to your deadlines if possible. Ask
    yourself, "Do I want to work 17-20 hours a day to hit an unrealistic
    deadline?" Been there, done that, lesson learned.
-   Accept the least amount of features for functionality for the first
    version. It's far more important to have a stable foundation than a
    ton of features. Slate other features for future releases after the
    foundation is laid properly. You can expect future needs (and
    should), but only include the minimums for the first version or
    iteration.
-   Realize that just because we "can" doesn't mean that we "should".
    Anything's possible, but not everything's advisable. This is a tough
    one, especially in the pre-development excitement, brainstorming
    phase. For instance, yes we could pull in a Google map for every
    row, but should we? How long will the requests take as the data set
    size increases?
-   If you don't know the answer to "Why" for a feature and "What" it
    will impact, don't even start answering "How".
-   Ensure that you're using a great version control system (I'm partial
    to GIT) and a hosted code repository if necessary. Backups are
    essential as well.
-   Block off large amounts of undivided time to work on the project.
    For instance, it's not a good day to write code if you have to leave
    every few minutes.

## Development

-   Spend as much time as possible understanding the real-world and data
    needs of the client before writing *any* code. This is absolutely
    *critical* to make sure that your application is designed from the
    ground as a stable, relevant application. Don't move forward until
    you think that you have a pretty good grasp of the needs; get help
    if you need to.
-   Out-engineer user-error as much as possible. In other words, never
    trust that the user will do what you expect, especially when
    entering data. For instance, about 4 years ago, I was reviewing a
    proposed payroll-entry system software for a Fortune-500 company.
    The software trusted the user to enter the number of their
    dependents properly for tax deduction purposes. When I questioned
    the developer, "What if someone enters a negative number?", his face
    grew pale. We found that an employee would end up with a raise,
    instead of a deduction! Ouch.
-   Don't reinvent the wheel. For instance, it makes no sense to develop
    your own login system for Ruby on Rails when there are great ones
    already out there that have run through a gauntlet in the
    real-world.
-   Don't implement *anything* unless you understand, as much as time
    allows, what you're "plugging in". Read the issues reported, read
    through the source code, and familiarize yourself with how it works.
    Don't choose something merely because 3 people recommended it in
    some forum. I've seen this often: a developer quickly slaps in a 3rd
    party open source app or gem and a few months later, there's an
    issue that they do not know how to resolve. Usually it's because
    they thought they'd found a quick fix, without thinking about any
    future issues. Perhaps the worst example that I've seen is
    hot-linking to Javascript code on a website somewhere, in blind
    trust that the link will stay live.
-   Be open to including other languages and technologies where
    appropriate. For instance, just because your app is written in Ruby,
    if a Perl or Python is better suited for a certain backend feature,
    it may be good to use it. Even if you don't integrate it, reading
    through it can help you see a better way to solve an issue at hand.
-   Don't do in code what your database can already do, as this will cut
    down the speed quite a bit. For instance, why use `Date` in Ruby in
    a SQL query on a MySQL-backed application when MySQL's
    `CURRENT_DATE()` will work fine (and faster)? In other words, know
    the capabilities of the technologies that you're using.
-   Avoid including "experimental" or "cutting-edge" features in your
    project if possible. While fun, the risk of issues just isn't worth
    it unless your project is just a learning exercise.
-   Communicate what you need to keep the client in the loop. That being
    said, too much communication about every little snag and solution
    will only frustrate them.

## Post-Development

-   Review your code for speed, stability, security, and usability.
-   Have someone else review it or discuss it with them.
-   Have non-technical people do real-world testing on your product.
    You'd be surprised at how many things you think are intuitive and
    easy that really aren't to an average user.
-   Never, ever, ever stop learning, even if it's unrelated to your
    current development language of choice.
-   Don't be afraid to ask for help. Even the best developers can gain a
    lot of insight and knowledge from reading others' code and
    interacting with others.
-   Revisit old code and see what you would've done differently. Often,
    you'll find yourself encouraged as you see how better your code is
    now than then.

## Enjoying Your Development:

-   How do you work best? In quiet, with music, with lots of lighting,
    dim lighting, etc...? A happy developer is much more likely to produce
    quality. Spend some time setting up your work environment the way
    that you're most comfortable with. It's amazing how mood-based
    programming can be. Improve your mood and you'll improve your code.
-   What tool(s) do you like to use? As much as possible, insist on
    those tools, "Yes, I can write this app in TextEdit or Notepad, but
    I can do it better with this \$79 tool X."
-   Give yourself time to think and rest. There are some days where I
    just can't write code well; other days where it's just flowing. This
    is due to how your brain functions. You need sleep and a change of
    pace and scenery now and then. Schedule breaks if you must and
    realize that some days are going to be tough. On tough days, learn
    something new.
-   Walk away for a while. It's easy to get "tunnel vision" and think
    that you're close to solving a problem and to think that more effort
    will solve it. While true at times, I find that it's best to walk
    away from the issue at hand for a while and do something completely
    different. For example, I tried once for 7 hours to power-through a
    complicated area of code and just couldn't get it right. I finally
    stopped working on code that day, came back the next day to it, and
    solved it in 16 minutes. You would be surprised at the ideas or
    solutions that will spring into your mind as you are thinking about
    or doing other things.
-   Set realistic deadlines. For instance, before telling your client or
    boss that this will be done next Friday, add a week. You never know
    what issues you might hit and will find yourself, more often than
    not, very grateful for the extra time to get it done right. If you
    end early, you're a hero!
-   Remember, you're a person, not a robot. In other words, you deserve
    time to eat, sleep, get away, etc... When necessary, remind others
    nicely.
-   Know your limits and enforce them. In other words, "No, I can't and
    won't recreate Gmail."

As the work quality improves, it will stand out and you will be called
upon more and more to help others, do other projects, etc... As your level
of expertise grows, help others by tactfully pointing out improvements,
respecting them, and encouraging them. In doing so, you will find
yourself enjoying the quality of your work.

*I hope you found this article valuable. Feel free to ask questions and
give feedback in the comments section of this post. Thanks!*
