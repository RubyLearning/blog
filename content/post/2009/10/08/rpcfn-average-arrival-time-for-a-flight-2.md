---
draft: false
title: 'RPCFN: Average Arrival Time For A Flight - 2 repost'
date: 2009-10-08
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/rubylearning
categories:
- beginners
- code snippets
- rpcfn
- ruby
layout: post
permalink: /2009/10/08/rpcfn-average-arrival-time-for-a-flight-2/
tags:
- chris strom
- programming
- rpcfn
- ruby
- ruby programming challenge for newbies
- the ruby programming language
---
## Ruby Programming Challenge For Newbies

### RPCFN: Average Arrival Time For A Flight (\#2)

-- By Chris Strom

Thank you for the very encouraging response to the
[first-ever](http://rubylearning.com/blog/2009/09/24/rpcfn-shift-subtitle-1/)
“**Ruby Programming Challenge For Newbies (RPCFN)**“. The second Ruby
challenge is from Chris Strom.

## About Chris Strom

![Chris
Strom](http://rubylearning.com/images/chris_strom.jpg "Chris Strom")Chris
Strom ([twitter](http://twitter.com/eee_c) /
[blog](http://japhr.blogspot.com/)) in his day job, is the Director of
Software Engineering for mdlogix, a small company in Baltimore,
Maryland. They develop software that manages clinical research trials
and associated data. They primarily code with Ruby on Rails. His
background is in web development, mostly in Perl until \~2005 when he
made the switch to Ruby.

Chris has this to say about the challenge:

> *RPCFN is a good idea as reading books and documentation can only take
> you so far when learning a new language. To really learn, you need to
> use the language. RPCFN provides a fabulous forum for using Ruby in
> the form of regular, engaging (but not arcanely difficult) challenges.
> Better yet, it provides feedback on how to use Ruby well, as each
> fortnight the best solution to a challenge is chosen. RPCFN is a
> wonderful introduction to the Ruby language and to the Ruby community.
> Welcome newbies!*

## Sponsor

[![Railsware for premium-quality web
applications](http://rubylearning.com/images/Railsware125x125.png "Railsware for premium-quality web applications")](http://www.railsware.com/)

This fortnights programming challenge is sponsored by
**[Railsware](http://www.railsware.com/)**. Railsware is glad to support
the Ruby Programming Challenge and help the Ruby community grow and get
stronger.

Railsware is a product development company specializing in Ruby on Rails
and UI design creating premium-quality web applications. The company
works with startups and established businesses looking to build
ecommerce, social networking, specialized business applications and many
other products.

## Prizes

-   The person with the best Ruby solution (if there is a tie between
    answers, then the one who posted first will be the winner) will be
    awarded any **one** of PeepCode’s [Ruby on Rails
    screencasts](http://peepcode.com/screencasts/ruby-on-rails).
-   The other prize, selected randomly amongst the remaining working
    Ruby solutions, will be awarded any **one** of BDDCasts’
    [screencasts](http://bddcasts.com/).

The two persons who win, can’t win again in the next immediate challenge
but can still participate.

## The Ruby Challenge {style="color:#0000FF;"}

![RPCFN](http://rubylearning.com/images/rubypc.jpg "Ruby Programming Challenge For Newbies")

You owe a big favor and have agreed to pick up a friend at the airport
every Friday night. The airline on which your friend flies is cheap, but
terrible with reporting delays and departure/arrival times. You soon
realize that the 10pm flight is never on time and is usually late by
more than an hour. If the plane has arrived at 11:15pm, 12:03am,
11:30pm, 11:23pm and 11:48pm, what is the average arrival time?

Does the solution still work if your friend changes to a flight arriving
6 hours later? What about 12 hours later?

### Program Output

The output should look something like this when run from the console:

    >> average_time_of_day(["11:51pm", "11:56pm", "12:01am", "12:06am", "12:11am"])
    => "12:01am"

    >> average_time_of_day(["6:41am", "6:51am", "7:01am"])
    => "6:51am"

### Hint

-   Your digital ways will not help you, time of day is cyclical.
-   You may need to use the **Math** and **Time** classes.

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
2.  Email address (will not be published):
3.  Brief description of what you do (will not be published):
4.  Country of Residence:
5.  [GIST URL of your
    Solution](http://rubylearning.com/blog/ruby-programming-challenge-faq/#rpc5)
    (i.e. Ruby code) with explanation and / or test cases:
6.  Code works with Ruby 1.8 / 1.9 / Both:

**Note**:

-   As soon as we receive your GIST URL, we will fork your submission.
    This means that your solution is frozen and accepted. Please be sure
    that is the solution you want, as it is now recorded in time and is
    the version that will be evaluated.
-   All solutions posted would be hidden to allow participants to come
    up with their own solutions.
-   **You should post your entries before midnight of 18th Oct. 2009
    (Indian Standard Time). No new solutions will be accepted from 19th
    to 22nd Oct. 2009.**
-   On Monday, 19th Oct. 2009 all the solutions will be thrown open for
    everyone to see and comment upon.
-   The winning entries will be announced on this blog on 22nd Oct. The
    winners will be sent their prizes by email.

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

-   [Chris Strom](http://japhr.blogspot.com/).
-   Sponsor [Railsware](http://www.railsware.com/).
-   Jeff Schoolcraft of [BDDCasts](http://bddcasts.com/).
-   The RubyLearning team, namely Dave Lilley (New Zealand), Jeff Savin
    (Canada), [Michael Kohl](http://citizen428.net/) (Austria), Peter
    Crawford (Italy), Satoshi Asakawa (Japan) and Victor Goff (USA).
-   [Giordano
    Scalzo](http://giordano.scalzo.biz/2009/10/10/entering-rpcfn-2/)
-   [Jonathan
    Julian](http://jonathanjulian.com/2009/10/i-just-entered-rpcfn-2/)
-   [Loïc
    Paillotin](http://www.loicpaillotin.com/2009/10/getting-back-in-shape.html)

## Questions?

Contact Satish Talim at
[satish.talim@gmail.com](mailto:satish.talim@gmail.com) OR if you have
any doubts / questions about the challenge (the current problem
statement), please post them as comments to this post and the author
will reply asap.

## The Participants

There are two categories of participants. Some are vying for the prizes
and some are participating for the fun of it.

### In the competition

1.  Othmane Benkirane, Morocco – declared winner
2.  Tisho Georgiev, Bulgaria
3.  Pete Campbell, USA
4.  Jonathan Julian, USA
5.  Antonio, Canada
6.  Robison WR Santos, Brazil
7.  Ricardo Duarte, Brazil
8.  Paul Barry, USA
9.  Haris Amin, USA
10. [Charles
    Feduke](http://rubylearning.com/blog/2009/10/22/charles-feduke-winner-rpcfn-2/),
    USA – declared winner
11. Oliver, UK
12. Bryan Liles, USA
13. Gunther Diemant, Germany
14. Valério Farias, Brazil
15. Vikas Maskeri, India
16. Jiren Patel, India
17. Stefan, Germany
18. Ahmed Al Hafoudh, Slovakia
19. Tom Voltz, USA
20. David Jenkins, USA
21. Michael Lang, USA
22. Thiago Fernandes Massa, Brazil
23. Tim Rand, USA
24. Milan Dobrota, Serbia
25. Mike Hodgson, Canada
26. Brad O’Connor, Australia
27. Giordano Scalzo, Italy
28. Rainer Thiel, New Zealand
29. Todd Huss, USA
30. Pankaj Sisodiya, India
31. Loïc Paillotin, USA
32. Chuck Ha, USA
33. Josh Baxley, USA
34. Javier Blanco Gutiérrez, Spain
35. Sogo Ohta, Japan
36. Daniel Wanek, USA
37. Himansu Desai, USA
38. John McDonald, USA
39. Ben Miller, UK
40. Sriram Varahan, India
41. Conner Peirce, USA
42. Ben Marini, USA

### Just for Fun

1.  Michael Kohl, Austria
2.  [Peter Cooper, UK](http://rubyinside.com/)

## The Winners {style="color:#0000FF;"}

![Winners](http://rubylearning.com/images/winner_icon_1.png)

Congratulations to the winners of this Ruby Challenge. They are:

-   **Charles Feduke** from USA (his [Ruby Challenge
    solution](https://gist.github.com/5b371226faf83af50d7e)) – the
    person with the best Ruby solution. He wins any **one** of
    PeepCode’s [Ruby on Rails
    screencasts](http://peepcode.com/screencasts/ruby-on-rails).
-   **Othmane Benkirane** from Morocco (his [Ruby Challenge
    solution](http://gist.github.com/205002)) – selected randomly
    amongst the remaining working Ruby solutions. He wins any **one** of
    BDDCasts’ [screencasts](http://bddcasts.com/).

## Previous Challenge

[RPCFN: Shift Subtitle (#1)](http://rubylearning.com/blog/2009/09/24/rpcfn-shift-subtitle-1/)
by Fabio Akita.

## Next Challenge

[RPCFN: Short Circuit (#3)](http://rubylearning.com/blog/2009/10/30/rpcfn-short-circuit-3/)
by Gautam Rege.

![Update](http://rubylearning.com/images/update.jpg "Update")

-   **This Challenge is now closed**. **Chris Strom** has a [working
    solution to this
    problem](https://gist.github.com/4f6807eef49064027a3c). This is not
    a “perfect” or the sole “correct” solution, but just one way of
    doing it.
-   Chris Strom has written a blog post that talks about the [most
    common “issues” faced by Ruby
    beginners](http://japhr.blogspot.com/2009/10/newbie-feedback.html).
-   The (#3) challenge by **Gautam Rege, India** is scheduled for 1st
    Nov. 2009.
-   The (#4) challenge by **Michael Kohl, Austria** is scheduled for
    1st Dec. 2009.
-   The (#5) challenge by **[Peter Cooper](http://rubyinside.com/),
    UK** is scheduled for 1st Jan. 2010.

