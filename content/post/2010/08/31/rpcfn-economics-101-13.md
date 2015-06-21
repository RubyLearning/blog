---
draft: false
title: 'RPCFN: Economics 101 - 13'
date: 2010-08-31
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/satishtalim/about
categories:
- Beginners
- RPCFN
- Ruby
layout: post
permalink: /2010/08/31/rpcfn-economics-101-13/
tags:
- Dr. Bruce Scharlau
- programming
- RPCFN
- Ruby
- Ruby Programming Challenge For Newbies
- The Ruby Programming Language
---
## Ruby Programming Challenge For Newbies

### RPCFN: Economics 101 (\#13)

-- By Dr. Bruce Scharlau

## About Dr. Bruce Scharlau

![Dr. Bruce
Scharlau](http://rubylearning.com/images/self-head-final_thumb1.png "Dr. Bruce Scharlau")
In Dr. Bruce’s own words: “I’ve been using and teaching Ruby since
trying out the cookbook example in the summer of 2006. As soon as I saw
how much easier it all was with Ruby and Rails, I was hooked. I now try
to do as much with Ruby as I can with my teaching and own work. It’s a
joy to code with Ruby compared to using other languages, which don’t
seem as intuitive by comparison. When I’m not busy working, then I try
to spend time with the family, or get out sailing.”

Dr. Bruce has this to say about the challenge:

> The challenge is useful for newbies as a way to extend their skills in
> a useful manner. They will learn how they solved the problem, and also
> gain from seeing how others solved the problem too. We all start from
> different places when we solve problems, so the ‘obvious’ solution to
> you, might not occur to someone else who has a different experience of
> Ruby. This is why it’s good to share examples and code together when
> possible too.

## Prizes

-   The participant with the best Ruby solution (if there is a tie
    between answers, then the one who posted first will be the winner)
    will be awarded any **one** of PeepCode’s [Ruby on Rails
    screencasts](http://peepcode.com/screencasts/ruby-on-rails).
-   From the remaining working Ruby solutions, three participants would
    be selected randomly and each one would be awarded any **one** of
    Pragmatic’s [The Ruby Object Model and
    Metaprogramming](http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming)
    screencasts.

The four persons who win, can’t win again in the next immediate
challenge but can still participate.

## The Ruby Challenge

![RPCFN](http://rubylearning.com/images/rubypc.jpg "Ruby Programming Challenge For Newbies")

### The Challenge

As a developer it helps to be able to understand a client’s perspective
and to build suitable applications to help them in their field. This
means knowing a bit about the world. We’ll help this background
knowledge by doing looking at some economic data, and also testing our
XML parsing skills.

The file [cia-1996.xml](http://rubylearning.com/data/cia-1996.zip) is
the data from the CIA World Factbook of 1996 in XML format. It has
details about 260 countries across five continents. Your challenge,
should you choose to accept it, is to uncover the following details
buried within this file:

1.  What is the population of the country with the most people? Yes, we
    know it’s China, but just how many people lived there in 1996?
2.  What are the five countries with the highest inflation rates, and
    what were those rates in 1996?
3.  What are the six continents in the file and which countries belong
    to which continent? Can you also produce them in alphabetical order?

Once you’ve worked out how to do part (2), then you can do anything with
this file; all you need is a bit of time. Knowing how to do (2) you
could then do (3) without too much effort.

You can use any XML library. I used REXML as it’s already there if you
have Ruby installed; so don’t need to worry about any gem installs. You
may also want to look at how REXML uses XPath.

Submit your solution of your code, which includes a test file that
answers the three questions.

## How to Enter the Challenge

Read the [Challenge
Rules](http://rubylearning.com/blog/ruby-programming-challenge-faq/index.php#rpc6).
By participating in this challenge, you agree to be bound by these
Challenge Rules. **It’s free and
[registration](http://rubylearning.com/blog/wp-login.php?action=register)
is optional**. You can enter the challenge just by posting the following
as a comment to this blog post:

1.  Your name:
2.  Country of Residence:
3.  [GIST URL of your
    Solution](http://rubylearning.com/blog/ruby-programming-challenge-faq/#rpc5)
    (i.e. Ruby code) with explanation and / or test cases:
4.  Code works with Ruby 1.8 / 1.9 / Both:
5.  Email address (will not be published):
6.  Brief description of what you do (will not be published):

**Note**:

-   As soon as we receive your GIST URL, we will fork your submission.
    This means that your solution is frozen and accepted. Please be sure
    that is the solution you want, as it is now recorded in time and is
    the version that will be evaluated.
-   All solutions posted would be hidden to allow participants to come
    up with their own solutions.
-   **You should post your entries before midnight of 27th Sept. 2010
    (Indian Standard Time). No new solutions will be accepted from 28th
    Sept. onwards.**
-   On 28th Sept. 2010 all the solutions will be thrown open for
    everyone to see and comment upon.
-   The winning entries will be announced on this blog before 30th Sept.
    2010. The winners will be sent their prizes by email.

## More details on the RPCFN?

Please refer to the **[RPCFN
FAQ](http://rubylearning.com/blog/ruby-programming-challenge-faq/)** for
answers to the following questions:

-   [What Is The Ruby Programming Challenge For Newbies
    (RPCFN)?](http://rubylearning.com/blog/ruby-programming-challenge-faq/index.php#rpc1)
-   [How does RPCFN benefit
    you?](http://rubylearning.com/blog/ruby-programming-challenge-faq/index.php#rpc2)
-   [Challenge
    Rules](http://rubylearning.com/blog/ruby-programming-challenge-faq/index.php#rpc6)
-   [Best
    Solution](http://rubylearning.com/blog/ruby-programming-challenge-faq/index.php#rpc3)
-   [Can I Submit A Ruby Programming Challenge
    Topic?](http://rubylearning.com/blog/ruby-programming-challenge-faq/index.php#rpc4)

## Donations

RPCFN is entirely financed by RubyLearning and sometimes sponsors, so if
you enjoy solving Ruby problems and would like to give something back by
helping with the running costs then any donations are gratefully
received.

[![Click here to lend your support to: Support RubyLearning With Some
Love and make a donation at www.pledgie.com
!](http://www.pledgie.com/campaigns/12553.png?skin_name=chrome)](http://www.pledgie.com/campaigns/12553)

## Acknowledgements

Special thanks to:

-   [Dr. Bruce Scharlau](http://twitter.com/scharlau).
-   [GitHub](http://github.com/), for giving us access to a private
    repository on GitHub to store all the submitted solutions.
-   The RubyLearning team.

## Questions?

Contact Satish Talim at [satish [dot] talim [at]
gmail.com](mailto:satish.talim@gmail.com) OR if you have any doubts /
questions about the challenge (the current problem statement), please
post them as comments to this post and the author will reply asap.

## The Participants

There are two categories of participants. Some are vying for the prizes
and some are participating for the fun of it.

### In the competition

1.  Dmytrii Nagirniak, Australia
2.  Kirill Shchepelin, Russia
3.  Lukasz Hanuszczak, Poland
4.  Rick DeNatale, USA
5.  David Lake, England
6.  Julio C. Villasante, Cuba
7.  Dan Wanek, USA
8.  Matthew Dahl, USA
9.  Mark Tabler, USA
10. Kalle Lindström, Sweden
11. Chris Jones, USA
12. Tamas Szabo, Australia
13. Adrian Castillo, Mexico
14. Norman E. White, USA
15. Himansu Desai, USA
16. Samnang Chhun, Cambodia
17. Predrag Bradaric, Serbia
18. Jonathan, Mexico
19. Christopher Fortenberry, USA
20. Brad O’Connor, Australia

### Just for Fun

1.  Casimir Saternos, USA
2.  Paul McKibbin, U.K.

## The Winners

![Winners](http://rubylearning.com/images/winner_icon_1.png)

Congratulations to the winners of this Ruby Challenge. They are:

-   **Dmytrii Nagirniak** from Australia (his [Ruby Challenge
    solution](https://gist.github.com/a8c86e12d7bf7afff3a7)) – the
    person with the best and most creative Ruby solution. He wins any
    **one** of PeepCode’s [Ruby on Rails
    screencasts](http://peepcode.com/screencasts/ruby-on-rails).
-   **Adrian Castillo** from Mexico, **Dan Wanek** from USA and **Kalle
    Lindström** from Sweden win any **one** of Pragmatic’s [The Ruby
    Object Model and Metaprogramming
    screencasts](http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming).

## Previous Challenge

[RPCFN: Cycle Tracks
(\#12)](http://rubylearning.com/blog/2010/07/31/rpcfn-cycle-tracks-12/)
by David Griffiths.

**Note**: All the previous challenges, sponsors and winners can be seen
on the [Ruby Programming Challenge for
Newbies](http://ruby-challenge.rubylearning.org/) page.

![Update](http://rubylearning.com/images/update.jpg "Update")

-   This challenge is now closed.
-   The (\#14) challenge by **Joseph Wilk, U.K.** is scheduled for Oct.
    2010.
