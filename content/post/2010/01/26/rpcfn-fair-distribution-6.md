---
draft: false
title: 'RPCFN: Fair Distribution - 6'
author: Satish Talim
authorlink: "http://satishtalim.com"
date: 2010-01-26
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: https://www.facebook.com/satishtalim/about
categories:
- beginners
- rpcfn
- ruby
layout: post
permalink: /2010/01/26/rpcfn-fair-distribution-6/
tags:
- john trupiano
- programming
- rpcfn
- ruby
- ruby programming challenge for newbies
- the ruby programming language
---
### Ruby Programming Challenge For Newbies

#### RPCFN: Fair Distribution (\#6)

-- By John Trupiano

## About John Trupiano

![John
Trupiano](http://rubylearning.com/images/johntrupiano.jpg "John Trupiano")John
Trupiano ([twitter](http://twitter.com/jtrupiano)) is the co-founder of
[SmartLogic](http://smartlogicsolutions.com/), the premiere Ruby
development team in Baltimore, Maryland. He is an active member in the
technology and business communities in the mid-Atlantic region. He is
highly involved with the local Ruby user group ([Bmore on
Rails](http://www.meetup.com/bmore-on-rails/)) and recently organized
the first ever [Maryland TechCrawl](http://mdtechcrawl.com/), a show and
tell event showcasing the exciting and innovative technologies being
developed in the region. He is also very active in the open source
community having authored [timecop](http://github.com/jtrupiano/timecop)
and [Rack::Rewrite](http://github.com/jtrupiano/rack-rewrite) and
contributing to a slew of projects including rails, capistrano, shoulda,
factory\_girl, gemcutter and multitest.

John has this to say about the challenge:

> *I think the Ruby challenge is great because it instills from the very
> start the idea that you need to practice to become a great programmer.
> Even as a problem setter, I have found the exercise of defining a
> problem and iterating through various solutions to be extremely
> educational and beneficial. Satish has cultivated a fantastic program
> here that provides access for beginners to seasoned Ruby programmers.
> Furthermore, the Ruby challenge serves as a notice to the Ruby
> community that it is important for us to provide a welcoming and
> nurturing environment for newcomers.*

## Our Awesome Sponsors

This monthly programming challenge is co-sponsored by **Backup My App**
and **Caliper**.

[![Backup My
App](http://rubylearning.com/images/banner1.gif "Backup My App")](http://backupmyapp.com/)

**Backup My App** is an automatic backup service for Ruby on Rails
applications. You simply install the plugin to your Rails application
and they handle the rest of the process. They store backup history for
several weeks and you can restore any of them automatically. Try out
their 1 GB plan for free. [Backup My App](http://backupmyapp.com/) has
co-sponsored this challenge and is proud to make this contribution to
the Ruby community.

[![Caliper](http://rubylearning.com/images/caliper.png "Caliper")](http://devver.net/caliper)

**[Caliper](http://devver.net/caliper)** provides free, hosted metrics
for Ruby programmers. Find duplication, code smells, complex code and
more! Get set up with just one click!

## Prizes

-   The participant with the best Ruby solution (if there is a tie
    between answers, then the one who posted first will be the winner)
    will be awarded any **one** of PeepCode’s [Ruby on Rails
    screencasts](http://peepcode.com/screencasts/ruby-on-rails) and a
    free 10 GB account for a year from [Backup My
    App](http://backupmyapp.com/).
-   From the remaining working Ruby solutions, three participants would
    be selected randomly and each one would be awarded any **one** of
    Pragmatic’s [The Ruby Object Model and
    Metaprogramming](http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming)
    screencasts.
-   **All the participants in this challenge (except the participant
    with the best Ruby solution) will get a free 5 GB account for 6
    months from [Backup My App](http://backupmyapp.com/)**.

The four persons who win, can’t win again in the next immediate
challenge but can still participate.

## **The Ruby Challenge** 

![RPCFN](http://rubylearning.com/images/rubypc.jpg "Ruby Programming Challenge For Newbies")

### The Challenge

Imagine that you manage a t-shirt printing company. Each morning you
review all orders placed the prior day and determine how long each order
will take to fulfill. On any given day, only a certain number of your
printing machines are operational. Your job is to schedule each printing
job with one of the operational printing machines in such a manner that
(a) all t-shirts are printed in the least amount of time, and (b) the
distribution of work across machines is as fair as possible (i.e. the
standard deviation of the time each machine spends working is
minimized).

Your objective is to write a **FairDistribution** class that satisfies
the following test cases. The code in the test cases is sufficient to
define the methods you must implement.

This is an NP complete problem, and as such I have only provided very
small datasets in the test cases. Test case \#3 takes the longest to
solve (See \*\*Notes below about how to run the Test Case \#3) and you
may find it easier to comment it out early in your development phase. On
a MBP Pro with a 2.4 GHz dual core processor and 4GB RAM, it took just
over 3 minutes to solve. The other three test cases took only a couple
of seconds.

Note that test cases 2 and 4 define specific distributions against which
you can verify. Test cases 1 and 3 have more than one acceptable
distribution and as such I have not provided a specific distribution to
test against.

Note also that there is a well known algorithm that provides a much
faster though not optimal solution. It will pass all tests except for
test case \#3. If you are only able to determine this particular
solution, please still consider submitting your solution for
consideration.

**\*\* Notes**: To accommodate the fact that Test Case \#3 takes a long
time to run, you can run the test normally, and TC\#3 will not run. When
you want the TC\#3 to run, then you can run the following:

    ruby test_solution_acceptance.rb full

The word “full” will signal it to run all the test cases.

### The Test Suite

[test\_solution\_acceptance.rb](http://gist.github.com/286495)

### Requirements

The solution to the challenge has to be a pure Ruby script, using only
the Ruby Standard Libraries (meaning, no external Gems). You **do not**
need to build a gem for this. Pure Ruby code is all that is needed.

* * * *

## **How to Enter the Challenge**

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
-   **You should post your entries before midnight of 20th Feb. 2010
    (Indian Standard Time). No new solutions will be accepted from 21st
    Feb. onwards.**
-   On 21st Feb. 2010 all the solutions will be thrown open for everyone
    to see and comment upon.
-   The winning entries will be announced on this blog before end of
    Feb. 2010. The winners will be sent their prizes by email.

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

-   [John Trupiano](http://twitter.com/jtrupiano).
-   Sponsors **Caliper** and **Backup My App**.
-   [GitHub](http://github.com/), for giving us access to a private
    repository on GitHub to store all the submitted solutions.
-   The RubyLearning team, namely Jeff Savin (Canada), Mareike Hybsier
    (Germany), Peter Crawford (Italy) and Satoshi Asakawa (Japan).

## Questions?

Contact Satish Talim at [satish [dot] talim [at]
gmail.com](mailto:satish.talim@gmail.com) OR if you have any doubts /
questions about the challenge (the current problem statement), please
post them as comments to this post and the author will reply asap.

## The Participants

There are two categories of participants. Some are vying for the prizes
and some are participating for the fun of it.

## In the competition

1.  Rajesh Tripathi, USA
2.  Aleksey Gureiev, Australia
3.  Aldric Giacomoni, USA
4.  Adam Lum, USA
5.  Brad O’Connor, Australia
6.  Martin Linkhorst, Germany
7.  Ilya Ermolin, Russia
8.  Elijah Miller, USA – declared winner (randomly selected)
9.  **Guillaume Petit, France – declared winner (best solution)**
10. Marc Minneman, USA
11. Cary Swoveland, Canada
12. Aurélien Bottazzini, France
13. Benoit Daloze, Belgium – declared winner (randomly selected)
14. Jacob Hodes, USA – declared winner (randomly selected)

### Just for Fun

1.  Dominik Masur, Germany

## **The Winners**

![Winners](http://rubylearning.com/images/winner_icon_1.png)

Congratulations to the winners of this Ruby Challenge. They are:

-   **Guillaume Petit** from France (his [Ruby Challenge
    solution](https://gist.github.com/3e3b45010e8fae7c7d9b)) – the
    person with the best and most creative Ruby solution. He wins any
    **one** of PeepCode’s [Ruby on Rails
    screencasts](http://peepcode.com/screencasts/ruby-on-rails) and a
    free 10 GB account for a year from [Backup My
    App](http://backupmyapp.com/).
-   **Elijah Miller** from USA (his [Ruby Challenge
    solution](http://gist.github.com/297449)), **Jacob Hodes** from USA
    (his [Ruby Challenge
    solution](https://gist.github.com/a460231c78f2a90180ab)), and
    **Benoit Daloze** from Belgium (his [Ruby Challenge
    solution](https://gist.github.com/43c82d5127d5d05ebe2e)) – selected
    randomly amongst the remaining working Ruby solutions. They win any
    **one** of Pragmatic’s [The Ruby Object Model and Metaprogramming
    screencasts](http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming).
-   **All the participants in this challenge (except Guillaume Petit who
    gets a free 10 GB account for a year) will get a free 5 GB account
    for 6 months from [Backup My App](http://backupmyapp.com/)**.

## Previous Challenge

[RPCFN: Mazes
(\#5)](http://rubylearning.com/blog/2009/12/27/rpcfn-mazes-5/) by Peter
Cooper.

**Note**: All the previous challenges, sponsors and winners can be seen
on the [Ruby Programming Challenge for
Newbies](http://ruby-challenge.rubylearning.org/) page.

![Update](http://rubylearning.com/images/update.jpg "Update")

-   This challenge is now closed.
-   The (\#7) challenge by **James Edward Gray II, USA** is scheduled
    for 1st Mar. 2010.

