---
draft: false
title: 'RPCFN: Ruby**Fun 4'
date: 2009-11-26
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/rubylearning
categories:
- beginners
- rpcfn
- ruby
layout: post
permalink: /2009/11/26/rpcfn-rubyfun-4/
tags:
- michael kohl
- programming
- rpcfn
- ruby
- ruby programming challenge for newbies
- the ruby programming language
---
## Ruby Programming Challenge For Newbies

### RPCFN: Ruby\*\*Fun (\#4)

#### By Michael Kohl

## About Michael Kohl

![Michael
Kohl](http://rubylearning.com/images/michael_kohl.jpg "Michael Kohl")Michael
Kohl ([Twitter](http://twitter.com/citizen428) /
[blog](http://citizen428.net/)) in his day job, works as an IT systems
engineer in Vienna, Austria. He fell in love with Ruby in 2003 or so,
maintained various Ruby-related packages for [Gentoo
Linux](http://www.gentoo.org/) from 2004-2006 and started being an
assistant teacher for
[RubyLearning.org](http://www.rubylearning.org/class/) in early 2009.
Besides all things Ruby his interests include mathematics, literature,
travelling, foreign languages, (functional) programming languages (e.g.
Clojure, Haskell), chess and so much more that he really wishes he
wouldn’t need to sleep.

Michael has this to say about the challenge:

> *The best way to learn programming is to write code! Ruby is fun
> because it’s easy to achieve results and I really believe that the
> RPCFN shows new Rubyists how much they can accomplish with relatively
> little Ruby. Thinking about a problem and then being able to compare
> your own solution to dozens of others is a lot of fun and a great
> opportunity for learning, so make sure to take part in these
> challenges! The reason that I picked this particular challenge is that
> it’s easy to solve, but requires a bit of thinking to get a somewhat
> attractive solution.*

## Sponsors

[![Chargify](http://rubylearning.com/images/chargify-125x125.gif "Chargify")](http://chargify.com/?utm_source=rubylearningblog&utm_medium=banner&utm_campaign=rubylearningbannerwinter09)

This monthly programming challenge is sponsored by Chargify and O’Reilly
Media.

**[Chargify](http://chargify.com/?utm_source=rubylearningblog&utm_medium=banner&utm_campaign=rubylearningbannerwinter09)**
simplifies recurring billing for Web 2.0 and SaaS companies. Build
innovative web applications without worrying about how to bill your
customers. Whether you’re a start up or an established business billing
thousands of customers a month, Chargify works for you.

Access customer insight, revenue, signups, and cancellation trends right
from your real-time dashboard, helping you focus on what’s important –
your company’s growth. Get started for FREE to Chargify your business
today.

[![O'Reilly
Media](http://oreilly.com/images/oreilly/banners/answers_banners-125-2.png "O'Reilly Media")](http://answers.oreilly.com/)

[O’Reilly Media](http://answers.oreilly.com/) spreads the knowledge of
innovators through its books, online services, magazine, and
conferences. Since 1978, O’Reilly has been a chronicler and catalyst of
leading-edge development, homing in on the technology trends that really
matter and spurring their adoption by amplifying “faint signals” from
the alpha geeks who are creating the future. An active participant in
the technology community, the company has a long history of advocacy,
meme-making, and evangelism.

## Prizes

-   The person with the best Ruby solution (if there is a tie between
    answers, then the one who posted first will be the winner) will be
    awarded any **one** of O’Reilly Media’s [Ebook
    bundle](http://oreilly.com/store/complete.html).
-   The person with the second best Ruby solution (if there is a tie
    between answers, then the one who posted first will be the winner)
    will be awarded any **one** of PeepCode’s [Ruby on Rails
    screencasts](http://peepcode.com/screencasts/ruby-on-rails).
-   The other two prizes, selected randomly amongst the remaining
    working Ruby solutions, would be any **one** of:
    -   BDDCasts’ [screencasts](http://bddcasts.com/) and any **one**
        of,
    -   Pragmatic’s [The Ruby Object Model and
        Metaprogramming](http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming)
        screencasts.

The four persons who win, can’t win again in the next immediate
challenge but can still participate.

## The Ruby Challenge

![RPCFN](http://rubylearning.com/images/rubypc.jpg "Ruby Programming Challenge For Newbies")

You just started working for CoolNewCompany which is developing
mathematics related software. Since you are new to the team, your boss
gives you an easy task to test your abilities. Write a class that
pretty-prints [polynomials](http://en.wikipedia.org/wiki/Polynomial),
following some simple rules:

-   if a coefficient is 1, it doesn’t get printed
-   if a coefficient is negative, you have to display something like “-
    2x\^3″, not “+ -2x\^3″
-   if a coefficient is 0, nothing gets added to the output
-   for x\^1 the \^1 part gets omitted
-   x\^0 == 1, so we don’t need to display it

Here’s a couple of usage examples:

    puts Polynomial.new([-3,-4,1,0,6]) # => -3x^4-4x^3+x^2+6
    puts Polynomial.new([1,0,2]) # => x^2+2

Don’t concern yourself too much with error handling, but if somebody
tries to create a polynomial with less than 2 elements, your program has
to raise an **ArgumentError** with the message “Need at least 2
coefficients.”

Please check the [provided unit
tests](https://gist.github.com/280aa4797a580fb8ae75) for more examples
and make sure to use them for verifying your solution!

**Requirements**: This has to be a pure Ruby script, using only the Ruby
Standard Libraries (meaning, no external Gems). You **do not** need to
build a gem for this. Pure Ruby code is all that is needed.

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
-   **You should post your entries before midnight of 20th Dec. 2009
    (Indian Standard Time). No new solutions will be accepted from 21st
    Dec. onwards.**
-   On 21st Dec. 2009 all the solutions will be thrown open for everyone
    to see and comment upon.
-   The winning entries will be announced on this blog before end of
    Dec. 2009. The winners will be sent their prizes by email.

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

-   [Michael Kohl](http://citizen428.net/).
-   Sponsor [Chargify](http://chargify.com/).
-   Book Sponsor [O’Reilly Media](http://answers.oreilly.com/).
-   The RubyLearning team, namely Jeff Savin (Canada), [Michael
    Kohl](http://citizen428.net/) (Austria), Peter Crawford (Italy) and
    Satoshi Asakawa (Japan).

## Questions?

Contact Satish Talim at [satish [dot] talim [at]
gmail.com](mailto:satish.talim@gmail.com) OR if you have any doubts /
questions about the challenge (the current problem statement), please
post them as comments to this post and the author will reply asap.

## The Participants

There are two categories of participants. Some are vying for the prizes
and some are participating for the fun of it.

### In the competition

1.  Gimi Liang, China – declared winner (randomly selected)
2.  William Yanez, Venezuela
3.  Christiaan Van den Poel, Belgium
4.  Tom Stuart, U.K.
5.  José Sazo, Chile
6.  James Daniels, USA
7.  Pedro Diogo, Portugal
8.  Felipe Elias Philipp, Brazil
9.  Fabio Kreusch, Brazil
10. Milan Dobrota, Serbia
11. Jefferson Mariano de Souza, Brazil
12. Aldric Giacomoni, USA
13. Michael Lang, USA
14. Rohit Arondekar, India
15. Bill Sullivan, USA
16. Jorge Dias, Spain
17. Alexander Klink, Germany
18. Chris Jones, USA
19. Aurélien Bottazzini, France
20. Ali Al-Sahaf, Saudi Arabia – declared winner (randomly selected)
21. John McDonald, USA
22. Aleksey Gureiev, Ukraine – declared winner (best solution)
23. Fred Fordham, Australia
24. Tony Chen, USA
25. Rohit Sasikumar, India
26. Paul Harrington, USA
27. Aashish Kiran Chittimilla, India
28. Benoit Daloze, Belgium
29. Steve Wilhelm, USA
30. Marc Minneman, USA
31. Othmane Benkirane, Morocco
32. Oleksandr Manzyuk, Ukraine
33. Pankaj Sisodiya, India
34. Oliver, UK
35. Sérgio Silva, Portugal
36. Isley Aardvark, USA
37. Rémy Coutable, France
38. Brad O’Connor, Australia
39. Suraj Dhakankar, India
40. Sunny Dackie, India
41. Philippe Antras, France
42. Amr Tamimi, Palestine
43. Sriram Varahan, India – declared winner (second best solution)

### Just for Fun

1.  James Daniels, USA
2.  Phil, Germany

## The Winners

![Winners](http://rubylearning.com/images/winner_icon_1.png)

Congratulations to the winners of this Ruby Challenge. They are:

-   **Aleksey Gureiev** from Ukraine (his [Ruby Challenge
    solution](http://gist.github.com/247055)) – the person with the best
    Ruby solution. He wins any **one** of O’Reilly Media’s [Ebook
    bundle](http://oreilly.com/store/complete.html).
-   **Sriram Varahan** from India (his [Ruby Challenge
    solution](https://gist.github.com/d5f3615f95aae4e2845b)) – the
    person with the second best Ruby solution. He wins any **one** of
    PeepCode’s [Ruby on Rails
    screencasts](http://peepcode.com/screencasts/ruby-on-rails).
-   **Gimi Liang** from China (his [Ruby Challenge
    solution](http://gist.github.com/243744)) – selected randomly
    amongst the remaining working Ruby solutions. He wins any **one** of
    BDDCasts’ [screencasts](http://bddcasts.com/).
-   **Ali Al-Sahaf** from Saudi Arabia (his [Ruby Challenge
    solution](https://gist.github.com/6e3da17378733c89d41e)) – selected
    randomly amongst the remaining working Ruby solutions. He wins any
    **one** of Pragmatic’s [The Ruby Object Model and Metaprogramming
    screencasts](http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming).

## Previous Challenge

[RPCFN: Short Circuit (\#3)](http://rubylearning.com/blog/2009/10/30/rpcfn-short-circuit-3/) by Gautam Rege.

![Update](http://rubylearning.com/images/update.jpg "Update")

-   **This challenge is now closed. Michael Kohl** has a [working solution](http://gist.github.com/260434) to this problem. This is not a “perfect” or the sole “correct” solution, but just one way of doing it.
-   The (\#5) challenge by **[Peter Cooper](http://rubyinside.com/), UK** is scheduled for 1st Jan. 2010.
-   The (\#6) challenge by **John Trupiano, USA** is scheduled for 1st Feb. 2010.

