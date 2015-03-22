---
draft: false
title: 'RPCFN: Short Circuit - 3'
date: 2009-10-30
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/satishtalim/about
categories:
- beginners
- rpcfn
- ruby
layout: post
permalink: /2009/10/30/rpcfn-short-circuit-3/
tags:
- gautam rege
- programming
- rpcfn
- ruby
- ruby programming challenge for newbies
- the ruby programming language
---
## Ruby Programming Challenge For Newbies

### RPCFN: Short Circuit (\#3)

--  By Gautam Rege

## About Gautam Rege

![Gautam
Rege](http://rubylearning.com/images/gautamrege.png "Gautam Rege")Gautam
Rege ([twitter](http://twitter.com/gautamrege) /
[blog](http://gautamrege.wordpress.com/)) is based in Pune, one of the
busiest IT hubs in India. He has done his computer engineering from Pune
Institute of Computer Technology (PICT) and passed out in the year 2000.
After working for a few services based companies like Zensar and Cybage
he got exposure to product companies like Veritas (now Symantec). It was
always his aim to be self-employed and when he found the right partner
in his friend **Sethupathi Asokan**, they both started **[Josh Software
Pvt. Ltd.](http://blog.joshsoftware.com/)**.

Gautam has this to say about the challenge:

> *RPCFN is a unique idea on RubyLearning – and I wish I had some such
> help when I was starting to learn Ruby. This is learning and fun! Now
> that everyone seems to have got onto the challenger track, I think its
> time to raise the bar — very slightly
> ![;)](http://rubylearning.com/blog/wp-includes/images/smilies/icon_wink.gif)
> Short-circuit has a twist in the tail – its not just learning Ruby but
> also seeing how easy it is to implement well-known algorithms quickly
> and efficiently. Welcome newbies to this 3rd Challenge – all the
> best!*

## Sponsor

[![Josh Software Pvt.
Ltd.](http://rubylearning.com/images/joshbannerad.jpg "Josh Software Pvt. Ltd.")](http://blog.joshsoftware.com/)

This monthly programming challenge is sponsored by **[Josh Software Pvt.
Ltd.](http://joshsoftware.com/index.html)** Josh Software is an upcoming
Rails start-up in Pune, India. ‘Josh’ in Hindi (an Indian language),
means ‘enthusiasm’. The Josh team builds state-of-the-art web based
applications for various clients in various industry verticals with all
the ‘josh’. The work culture at Josh involves fun at work, sincerity in
coding and quality deliverables.

## Prizes

-   The person with the best Ruby solution (if there is a tie between
    answers, then the one who posted first will be the winner) will be
    awarded any **one** of PeepCode’s [Ruby on Rails
    screencasts](http://peepcode.com/screencasts/ruby-on-rails).
-   The other two prizes, selected randomly amongst the remaining
    working Ruby solutions, would be any **one** of:
    -   BDDCasts’ [screencasts](http://bddcasts.com/) and any **one**
        of,
    -   Pragmatic’s [The Ruby Object Model and
        Metaprogramming](http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming)
        screencasts.

The three persons who win, can’t win again in the next immediate
challenge but can still participate.

## The Ruby Challenge {style="color:#0000FF;"}

![RPCFN](http://rubylearning.com/images/rubypc.jpg "Ruby Programming Challenge For Newbies")

Given a closed electrical circuit, we need to identify the redundant
elements. For the sake of simplicity, we shall assume only resistors
between various points. **Electricity will flow through the path of
least resistance!** Source of electricity is A and the end-point is G.

The idea of the program is to find the redundant resistors.

![Short Circuit](http://rubylearning.com/images/short_circuit.jpg)

As shown in the diagram we can ‘translate’ load between points into any
simple data structures. For example:

    [
       [ A, B, 50],
       [ A, D, 150],
       [ B, C, 250],
       [ B, E, 250],
       [ C, E, 350],
       [ C, D, 50],
       [ C, F, 100],
       [ D, F, 400],
       [ E, G, 200],
       [ F, G, 100],
    ]

Feel free to use ANY other data structure as long as assumptions are
simple and understandable. The source and the end-point may be
hard-coded in the script or can be taken as command line parameters,
whichever you feel is convenient.

In the above example, the output expected MUST be the following array of
arrays:

    [
      [ 'A', 'B', 50 ],
      [ 'B', 'C', 250],
      [ 'B', 'E', 250],
      [ 'C', 'E', 350],
      [ 'D', 'F', 400],
      [ 'E', 'G', 200],
    ]

### Hint

-   ‘Short Circuit’ is a cryptic clue to the solution for this
    challenge.

**Requirements**: This has to be a pure Ruby script, using only the Ruby
Standard Libraries (meaning, no external Gems). You **do not** need to
build a gem for this. Pure Ruby code is all that is needed.

## How to Enter the Challenge {style="color:#0000FF;"}

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
-   **You should post your entries before midnight of 20th Nov. 2009
    (Indian Standard Time). No new solutions will be accepted from 21st
    Nov. onwards.**
-   On 21st Nov. 2009 all the solutions will be thrown open for everyone
    to see and comment upon.
-   The winning entries will be announced on this blog before end of
    Nov. The winners will be sent their prizes by email.

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
!](http://www.pledgie.com/campaigns/415.png?skin_name=chrome)](http://www.pledgie.com/campaigns/415)

## Acknowledgements

Special thanks to:

-   [Gautam Rege](http://gautamrege.wordpress.com/).
-   Sponsor [Josh Software Pvt.
    Ltd.](http://joshsoftware.com/index.html).
-   The RubyLearning team, namely Dave Lilley (New Zealand), Jeff Savin
    (Canada), [Michael Kohl](http://citizen428.net/) (Austria), Peter
    Crawford (Italy), Satoshi Asakawa (Japan) and Victor Goff (USA).

## Questions?

Contact Satish Talim at [satish [dot] talim [at]
gmail.com](mailto:satish.talim@gmail.com) OR if you have any doubts /
questions about the challenge (the current problem statement), please
post them as comments to this post and the author will reply asap.

## The Participants

There are two categories of participants. Some are vying for the prizes
and some are participating for the fun of it.

### In the competition

1.  James Daniels, USA
2.  Harshad R Wankhede, India
3.  Ben Marini, USA
4.  Robison WR Santos, Brazil
5.  Mark, USA
6.  Valério Farias, Brazil
7.  Prakash Sejwani, India
8.  Paul Smith, England
9.  Himansu Desai, USA
10. Rohit Sasikumar, India
11. Pat Harty, USA
12. Todd Huss, USA – declared winner (best solution)
13. Tom, France – declared winner (randomly selected)
14. Javier Blanco Gutiérrez, Spain
15. Sogo Ohta, Japan
16. Rainer Thiel, New Zealand
17. Andy Newport, New Zealand
18. Antonio, Canada
19. Glenn Goodrich, USA
20. Sam Johnson, Canada – declared winner (randomly selected)

### Just for Fun

1.  Aldric Giacomoni, USA

## The Winners {style="color:#0000FF;"}

![Winners](http://rubylearning.com/images/winner_icon_1.png)

Congratulations to the winners of this Ruby Challenge. They are:

-   **Todd Huss** from USA (his [Ruby Challenge
    solution](http://gist.github.com/228577)) – the person with the best
    Ruby solution. He wins any **one** of PeepCode’s [Ruby on Rails
    screencasts](http://peepcode.com/screencasts/ruby-on-rails).
-   **Tom** from France (his [Ruby Challenge
    solution](https://gist.github.com/8a70b216514ab5edab5d)) – selected
    randomly amongst the remaining working Ruby solutions. He wins any
    **one** of BDDCasts’ [screencasts](http://bddcasts.com/).
-   **Sam Johnson** from Canada (his [Ruby Challenge
    solution](https://gist.github.com/5ed31a447fb4c03a40fc)) – selected
    randomly amongst the remaining working Ruby solutions. He wins any
    **one** of Pragmatic’s [The Ruby Object Model and Metaprogramming
    screencasts](http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming).

## Previous Challenge

[RPCFN: Average Arrival Time For A Flight
(\#2)](http://rubylearning.com/blog/2009/10/08/rpcfn-average-arrival-time-for-a-flight-2/)
by Chris Strom.

![Update](http://rubylearning.com/images/update.jpg "Update")

**This challenge is now closed.** Gautam Rege has posted on his blog
[his observations on the code
submitted](http://gautamrege.wordpress.com/2009/11/20/rpcfn3-short-circuit/)
for this challenge. Do have a look.

-   The (\#4) challenge by **Michael Kohl, Austria** is scheduled for
    1st Dec. 2009.
-   The (\#5) challenge by **[Peter Cooper](http://rubyinside.com/),
    UK** is scheduled for 1st Jan. 2010.
-   The (\#6) challenge by John Trupiano, USA is scheduled for 1st Feb.
    2010.

