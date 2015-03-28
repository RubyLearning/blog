---
draft: false
title: 'RPCFN: Shift Subtitle 1'
date: 2009-09-24
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/satishtalim/about
permalink: /2009/09/24/rpcfn-shift-subtitle-1/
categories:
- beginners
- rpcfn
- ruby
layout: post
tags:
- fabio akita
- programming
- rpcfn
- ruby
- ruby programming challenge for newbies
- the ruby programming language
---
## Ruby Programming Challenge For Newbies

### RPCFN: Shift Subtitle (\#1)

-- By Fabio Akita

After a [very encouraging response to our
poll](http://rubylearning.com/blog/2009/09/13/poll-ruby-problems-for-beginners-and-prizes/)
from YOU, the readers of the RL blog, RL is happy to announce the
first-ever **fortnightly** ( bi-weekly / every 14 days) “**Ruby
Programming Challenge For Newbies (RPCFN)**” in Ruby. Thanks to YOU, the
Ruby community, people like Fabio Akita and companies like Locaweb who
make all of this possible.

## About Fabio Akita

![Fabio
Akita](http://www.rubylearning.com/images/akita.jpg "Fabio Akita")**Fabio
Akita** is a Brazilian Rails enthusiast, also known online as
“AkitaOnRails”. He regularly write posts on his own
[blog](http://www.akitaonrails.com/) and had published the very first
book tailored for the Brazilian audience called “Repensando a Web com
Rails”.

He is now a full-time Ruby on Rails developer working as Project Manager
at
[Locaweb](http://www.locaweb.com/default.html?utm_campaign=Rails&utm_source=rubylearning&utm_medium=quadrado),
Brazil. He’s also the creator of the “[Rails Summit Latin
America](http://www.railssummit.com.br/)“, the largest international
Rails event in South America.

Fabio has this to say about the challenge:

> *If you’re learning a new language such as Ruby, it is important that
> you practice it. And the best way to start is by scratching your own
> itch. Anything goes. It’s not unusual to start by writing simple
> command line scripts to help out your everyday routine. That’s why I
> thought of a very trivial exercise in the first challenge. It should
> demand that you know the basics for a variety of Ruby subjects such as
> regular expressions, file manipulation, time calculation and so on.
> The only way to achieve mastery is by practice. So let’s get started!*

## Sponsor

[![UK based Passenger
Hosting](http://rubylearning.com/images/rubylearning125.gif "UK based Passenger Hosting")](http://www.1steasy.com/ruby-on-rails.htm)

**[1st Easy Limited](http://www.1steasy.com/)** are delighted to have
been given the opportunity to support the work of Satish Talim and his
team at RubyLearning.

Taking part in the Ruby Programming Challenge? You’re welcome to take
advantage of the free [Ruby on Rails hosting
trials](http://www.1steasy.com/ruby-on-rails.htm) that 1st Easy offer:
simply register your details, and a full-featured account is yours to do
with as you please for one month. Once the trial is over, you can
transfer your work to a paid account, or walk away with no questions
asked!

## Prizes

-   The person with the best Ruby solution (if there is a tie between
    answers, then the one who posted first will be the winner) will be
    awarded any **one** of PeepCode’s [Ruby on Rails
    screencasts](http://peepcode.com/screencasts/ruby-on-rails).
-   The other prize, selected randomly amongst the remaining working
    Ruby solutions, will be awarded any **one** of Pragmatic’s [The Ruby
    Object Model and
    Metaprogramming](http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming)
    screencasts.

The two persons who win, can’t win again in the next immediate challenge
but can still participate.

## The Ruby Challenge {style="color:#0000FF;"}

![RPCFN](http://rubylearning.com/images/rubypc.jpg "Ruby Programming Challenge For Newbies")

**Difficulty**: Ruby beginner.

**Goals**: Basic control over Ruby elements, specially command line
scripting.

**Description**: There are several ways to subtitle a movie nowadays,
and one of the most well known format is the SubRip format
([http://en.wikipedia.org/wiki/SubRip](http://en.wikipedia.org/wiki/SubRip)).
It has entries like these:

    645
    01:31:51,210 --> 01:31:54,893
    the government is implementing a new policy...

    646
    01:31:54,928 --> 01:31:57,664
    In connection with a dramatic increase
    in crime in certain neighbourhoods,

Each line has an increasing integer identification, then comes the time
range (start and end time) in the format
“hours:minutes:seconds,milliseconds”. The decimal separator used is the
comma. Finally there are the subtitles themselves and a line break marks
the end of an entry.

Sometimes the timing is shifted for a small amount, 2 or 3 seconds. Then
comes the trouble when you need to shift everything a few seconds back
or ahead.

The goal is to create a small command line script in Ruby that will read
an SRT file, and output another one with the new calculated times.

So, for example, if I want to shift everything 2,500 (2 seconds and 500
milliseconds) ahead, I would start with this:

    01:32:04,283 --> 01:32:07,769

and end up with:

    01:32:06,783 --> 01:32:10,269

The command line should accept arguments such as:

    shift_subtitle --operation add --time 02,110 input_file output_file

This means “--operation” can accept either ‘add’ or ‘sub’ to add or
subtract times. The “--time” will accept the amount of time to shift in
the format 11,222 where “11” is the amount of seconds and “222” the
amount of milliseconds.

**Requirements**: This has to be a pure Ruby script, using only the Ruby
Standard Libraries (meaning, no external Gems).

It has to implement “optparse” to parse the command line arguments.

As an observation, bear in mind that the first thing that you might
attempt will look like this:

    a = Time.at(04,283)
    b = a + 2.500
    puts b.usec
    => 500283

This is wrong, the proper result should’ve been “783” (as in the example
in the previous section). So it means that you will have to find another
way out.

**Extras (Optional)**: If you want:

-   It would be interesting to exercise the process of a Gem creation.
    So you would have to package your script.
-   Another thing that would be good is to have RSpec unit tests
    covering your code, to exercise software development best practices.

**(Note that the above two points are optional and not a requirement).**

## How to Enter the Challenge {style="color:#0000FF;"}

**It’s free and registration is not required**. You can enter the
challenge just by posting the following as a comment to this blog post:

1.  Your name:
2.  Email address (will not be published):
3.  Brief description of what you do (will not be published):
4.  Country of Residence:
5.  Your Solution (i.e. Ruby code): Prefix your code with

         tag and suffix it with 

    tag.

6.  Code works with Ruby 1.8 / 1.9 / Both:
7.  Explanation (if any):
8.  Test cases (if any):

**Note**:

-   You may provide the URL of your source code, in case it is hosted on
    GitHub.
-   All solutions posted would be hidden to allow users to come up with
    their own solutions.
-   **You should post your entries before midnight of 4th Oct. 2009
    (Indian Standard Time). No new solutions will be accepted from 5th
    to 8th Oct. 2009.**
-   On Monday, 5th Oct. 2009 all the solutions will be thrown open for
    everyone to see and comment upon.
-   The winning entries will be announced on this blog. The winners will
    be sent their prizes by email.

## More details on the RPCFN?

Please refer to the **[RPCFN
FAQ](http://rubylearning.com/blog/ruby-programming-challenge-faq/)** for
answers to the following questions:

-   [What Is The Ruby Programming Challenge For Newbies
    (RPCFN)?](http://rubylearning.com/blog/ruby-programming-challenge-faq/index.php#rpc1)
-   [How does RPCFN benefit
    you?](http://rubylearning.com/blog/ruby-programming-challenge-faq/index.php#rpc2)
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

-   [Fabio Akita](http://www.akitaonrails.com/).
-   Sponsor [1st Easy Limited](http://www.1steasy.com/), U.K.
-   The RubyLearning team, namely [Michael Kohl](http://citizen428.net/)
    (Austria), Peter Crawford (Italy), Satoshi Asakawa (Japan) and
    Victor Goff (USA).
-   [Ruby Inside,
    Brazil](http://www.rubyinside.com.br/participe-do-desafio-do-ruby-learning-e-concorra-a-premios-2227).
-   [Amanda and Michael’s Ruby
    Blog](http://ruby.about.com/b/2009/10/02/have-you-tried-the-ruby-programming-challenge-for-newbies-yet.htm)
-   [Adrian](http://redshinythings.blogspot.com/2009/10/ruby-challenge.html)
-   [Charles
    Feduke](http://www.deploymentzone.com/2009/09/29/temp-files-and-ruby-1-8-6-on-windows/)
-   [Fabio
    Kreusch](http://blog.kreusch.com.br/post/199158389/my-ruby-programming-challenge-for-newbies-1-entry)
-   [Fernando
    Quadro](http://www.fernandoquadro.com.br/html/2009/09/25/desafio-ruby-learning-participe-e-concorra-a-premios/)
-   [It’s so
    shiny](http://charpcfn.wordpress.com/2009/10/06/shift-subtitle-results/)
-   [Jeff
    Craig](http://blog.foxxtrot.net/2009/09/ruby-programming-challenge-for-newbies.html)

## Questions?

Contact Satish Talim at
[satish.talim@gmail.com](mailto:satish.talim@gmail.com) OR if you have
any doubts / questions about the challenge (the current problem
statement), please post them as comments to this post and the author
will reply asap.

## The Participants

There are two categories of participants. Some are vying for the prize
and some are participating for the fun of it. The participants were:

### In the competition

1.  Felipe Giotto, Brazil
2.  Eduardo, Brazil
3.  Kalle Lindström, Sweden – declared winner
4.  Robison WR Santos, Brazil
5.  Aldric, USA
6.  Akshay Gupta, India
7.  Fabio Kreusch, Brazil
8.  Chris Jones, USA
9.  Chuck Ha, USA
10. Milan Dobrota, Serbia
11. Parag Shah, India
12. Hugo Figueiredo, Brazil
13. John McDonald, USA
14. [Felipe Elias
    Philipp](http://rubylearning.com/blog/2009/10/08/felipe-elias-philipp-winner-rpcfn-1/),
    Brazil – declared winner
15. Charles Feduke, USA
16. Hari Rajagopal, USA
17. Brad O’Connor, Australia
18. Oliver, UK
19. Jacob Lichner, USA
20. Todd Huss, USA
21. Antonio, Canada
22. Sriram Varahan, India
23. Giordano Scalzo, Italy
24. Phil Kates, USA

### Just for Fun

1.  Michael Kohl, Austria
2.  Rodrigo Rosenfeld Rosas, Brazil
3.  Dominik Honnef, Germany
4.  Mike Hodgson, Canada

## The Winners {style="color:#0000FF;"}

![Winners](http://rubylearning.com/images/winner_icon_1.png)

Congratulations to the winners of this Ruby Challenge. They are:

-   **Felipe Elias Philipp** from Brazil (his [Ruby Challenge
    solution](http://github.com/felipeelias/shift_subtitle)) – the
    person with the best Ruby solution. He wins any **one** of
    PeepCode’s [Ruby on Rails
    screencasts](http://peepcode.com/screencasts/ruby-on-rails).
-   **Kalle Lindström** from Sweden (his [Ruby Challenge
    solution](https://gist.github.com/fa3ec5afe7b19d22c44a)) – selected
    randomly amongst the remaining working Ruby solutions. He wins any
    **one** of Pragmatic’s [The Ruby Object Model and
    Metaprogramming](http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming)
    screencasts.

## Next Challenge

[RPCFN: Average Arrival Time For A Flight
(\#2)](http://rubylearning.com/blog/2009/10/08/rpcfn-average-arrival-time-for-a-flight-2/)
by Chris Strom.

![Update](http://rubylearning.com/images/update.jpg "Update")

-   **The Challenge is now closed**. **Fabio Akita** has a [working
    solution to this
    problem](http://github.com/akitaonrails/Shift-Subtitle). This is not
    a “perfect” or the sole “correct” solution, but just one way of
    doing it. Fabio is thankful to **Satoshi Asakawa** for using one of
    his ideas in this implementation.

