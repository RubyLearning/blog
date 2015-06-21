---
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/rubylearning
draft: false
title: 'RPCFN: Mazes - 5'
date: 2009-12-27
categories:
- beginners
- rpcfn
- ruby
layout: post
permalink: /2009/12/27/rpcfn-mazes-5/
tags:
- peter cooper
- programming
- rpcfn
- ruby
- ruby programming challenge for newbies
- the ruby programming language
---
RubyLearning wishes all its readers and their friends and families a
happy, healthy 2010. Thanks to everyone for the support and
encouragement this year. It’s been a fun and rewarding year and we do
appreciate all that you contribute to this site.<!--more-->

## Ruby Programming Challenge For Newbies

### RPCFN: Mazes (\#5)

-- By Peter Cooper

## About Peter Cooper

![Peter
Cooper](http://rubylearning.com/images/peter-cooper-125.gif "Peter Cooper")Peter
Cooper ([twitter](http://twitter.com/peterc)) is the editor and curator
of several Ruby sites including [Ruby
Inside](http://www.rubyinside.com/), [Rails
Inside](http://www.railsinside.com/), and
[RubyFlow](http://www.rubyflow.com/). They develop software that manages
clinical research trials and associated data. They primarily code with
Ruby on Rails. His background is in web development, mostly in Perl
until \~2005 when he made the switch to Ruby.

Peter has this to say about the challenge:

> *RPCFN is designed to make you good at turning mental concepts into
> working Ruby code. If you can do that, the programming world is your
> oyster, and challenges like those presented with RPCFN are a great
> first (or second!) step. If I have any advice about how to approach
> the challenges, remember to keep it fun at all times, and if your
> solution isn’t working out, take a few steps back and be prepared to
> knock over your sandcastle and try a different approach. A common
> mistake in programming is to keep digging the same hole even deeper
> rather than finding a better place to dig
> ![:-)](http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif)
> Try lots of holes instead; Ruby makes it easy.*

## Sponsors

This monthly programming challenge is co-sponsored by **Backup My App**,
**InformIT** and **Thoughtworks**.

[![Backup My
App](http://rubylearning.com/images/banner1.gif "Backup My App")](http://backupmyapp.com/)

**Backup My App** is an automatic backup service for Ruby on Rails
applications. You simply install the plugin to your Rails application
and they handle the rest of the process. They store backup history for
several weeks and you can restore any of them automatically. Try out
their 1 GB plan for free. [Backup My App](http://backupmyapp.com/) has
co-sponsored this challenge and is proud to make this contribution to
the Ruby community.

[![InformIT](http://rubylearning.com/images/aw_ph_sams_informit_125x125.jpg "InformIT")](http://www.informit.com/ruby)

**[InformIT](http://www.informit.com/ruby)** is the online presence of
the family of information technology publishers and brands of
[Pearson](http://www.pearsoned.com/), the world’s largest educational
publisher. InformIT is home to the leading technology publishing
imprints Addison-Wesley Professional, Cisco Press, Exam Cram, IBM Press,
Prentice Hall Professional, QUE, and Sams. They also offer products
geared towards the professional business audience from their publishing
partners FT Press and Wharton School Publishing. Here you will gain
access to trusted and quality content and resources from the authors,
creators, innovators, and leaders of technology and business. Whether
you’re looking for a book on a new technology, a helpful article, timely
newsletters or access to the [Safari Books
Online](http://www.informit.com/about/#safari) digital library, InformIT
has a solution for you.

[![Thoughtworks](http://rubylearning.com/images/thoughtworks.jpg "Thoughtworks")](http://www.thoughtworker.com/)

**[ThoughtWorks](http://www.thoughtworker.com/)** kick-started the Agile
business era with pioneering software delivery practices and
world-leading open source software. Today, clients approach them to
solve their toughest business problems, and they deliver some of the
world’s most sophisticated custom applications. Their products division,
ThoughtWorks Studios, was established in 2006 to make cutting-edge
software development tools currently including Mingle (project
collaboration), Cruise (continuous integration) and Twist (functional
testing). Founded in 1993, ThoughtWorks is headquartered in Chicago, and
has offices in Australia, Canada, China, Hong Kong, India, Sweden,
United Kingdom and United States.

## Prizes

-   The participant with the best Ruby solution (if there is a tie
    between answers, then the one who posted first will be the winner)
    will be awarded a printed copy of the book “[Refactoring in
    Ruby](http://www.informit.com/store/product.aspx?isbn=0321545044)”
    from [InformIT](http://www.informit.com/ruby) and a free 10 GB
    account for a year from [Backup My App](http://backupmyapp.com/).
-   One other participants with an equally good Ruby solution will be
    awarded any **one** of PeepCode’s [Ruby on Rails
    screencasts](http://peepcode.com/screencasts/ruby-on-rails).
-   From the remaining working Ruby solutions, three participants would
    be selected randomly and each one would be awarded any **one** of
    Pragmatic’s [The Ruby Object Model and
    Metaprogramming](http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming)
    screencasts.
-   **All the participants in this challenge (except the participant
    with the best Ruby solution) will get a free 5 GB account for 6
    months from [Backup My App](http://backupmyapp.com/)**.

The five persons who win, can’t win again in the next immediate
challenge but can still participate.

## The Ruby Challenge

![RPCFN](http://rubylearning.com/images/rubypc.jpg "Ruby Programming Challenge For Newbies")

### Introduction

Mazes are known to have challenged humans from as far back as the 5th
century BC. There are many types of maze, but typically you need to find
your way from a start point to an end point.

In this Ruby challenge, you will need to develop a class that can be
used to solve mazes. Mazes will be provided as a string showing a
graphical representation of the maze’s layout. Spaces are navigable,
while \# (pound) symbols are used to denote walls. In this challenge the
letter “A” is used to mark the start point, and “B” the end point.
Here’s an example of a maze contained within a string:

    MAZE1 = %{#####################################
    # #   #     #A        #     #       #
    # # # # # # ####### # ### # ####### #
    # # #   # #         #     # #       #
    # ##### # ################# # #######
    #     # #       #   #     # #   #   #
    ##### ##### ### ### # ### # # # # # #
    #   #     #   # #   #  B# # # #   # #
    # # ##### ##### # # ### # # ####### #
    # #     # #   # # #   # # # #       #
    # ### ### # # # # ##### # # # ##### #
    #   #       #   #       #     #     #
    #####################################}

The prior maze would be loaded into a Maze object like so:

    Maze.new(MAZE1)

### The Challenge

There are two parts to the challenge: you can choose to do one or both,
depending on your skill level or how much time you have available.

1.  Implement a Maze\#solvable? method that returns true/false depending
    on whether it’s possible to navigate the maze from point A to point
    B.
2.  Implement a Maze\#steps method that returns an integer of the least
    number of “steps” one would have to take within the maze to get from
    point A to point B. “Steps” can only be taken up, down, left or
    right. No diagonals.

There are a number of ways to “solve” mazes but there’s a wide scope for
you to be as straightforward or as clever as you like with this
challenge (tip: I’d love to see some clever/silly solutions!). Your
“solvable?” and “steps” methods could share algorithms or you might come
up with alternate ways to be more efficient in each case. Good luck!

**Note**: Use the test suite to ensure your code interfaces in the right
way. The test suite demonstrates how your class will be called and used.

### The Test Suite

Your Maze class should be in maze.rb for the following test suite to
work
![:-)](http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif)

    require 'test/unit'
    require 'maze'

    MAZE1 = %{#####################################
    # #   #     #A        #     #       #
    # # # # # # ####### # ### # ####### #
    # # #   # #         #     # #       #
    # ##### # ################# # #######
    #     # #       #   #     # #   #   #
    ##### ##### ### ### # ### # # # # # #
    #   #     #   # #   #  B# # # #   # #
    # # ##### ##### # # ### # # ####### #
    # #     # #   # # #   # # # #       #
    # ### ### # # # # ##### # # # ##### #
    #   #       #   #       #     #     #
    #####################################}
    # Maze 1 should SUCCEED

    MAZE2 = %{#####################################
    # #       #             #     #     #
    # ### ### # ########### ### # ##### #
    # #   # #   #   #   #   #   #       #
    # # ###A##### # # # # ### ###########
    #   #   #     #   # # #   #         #
    ####### # ### ####### # ### ####### #
    #       # #   #       # #       #   #
    # ####### # # # ####### # ##### # # #
    #       # # # #   #       #   # # # #
    # ##### # # ##### ######### # ### # #
    #     #   #                 #     #B#
    #####################################}
    # Maze 2 should SUCCEED

    MAZE3 = %{#####################################
    # #   #           #                 #
    # ### # ####### # # # ############# #
    #   #   #     # #   # #     #     # #
    ### ##### ### ####### # ##### ### # #
    # #       # #  A  #   #       #   # #
    # ######### ##### # ####### ### ### #
    #               ###       # # # #   #
    # ### ### ####### ####### # # # # ###
    # # # #   #     #B#   #   # # #   # #
    # # # ##### ### # # # # ### # ##### #
    #   #         #     #   #           #
    #####################################}
    # Maze 3 should FAIL


    class MazeTest < Test::Unit::TestCase
      def test_good_mazes
        assert_equal true, Maze.new(MAZE1).solvable?
        assert_equal true, Maze.new(MAZE2).solvable?
      end

      def test_bad_mazes
        assert_equal false, Maze.new(MAZE3).solvable?
      end

      def test_maze_steps
        assert_equal 44, Maze.new(MAZE1).steps
        assert_equal 75, Maze.new(MAZE2).steps
        assert_equal 0, Maze.new(MAZE3).steps
      end
    end

### Requirements

This has to be a pure Ruby script, using only the Ruby Standard
Libraries (meaning, no external Gems). You **do not** need to build a
gem for this. Pure Ruby code is all that is needed.

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
-   **You should post your entries before midnight of 19th Jan. 2010
    (Indian Standard Time). No new solutions will be accepted from 20th
    Jan. onwards.**
-   On 20th Jan. 2010 all the solutions will be thrown open for everyone
    to see and comment upon.
-   The winning entries will be announced on this blog before end of
    Jan. 2010. The winners will be sent their prizes by email.

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

[![Josh Software Pvt.
Ltd.](http://rubylearning.com/images/joshbannerad.jpg "Josh Software Pvt. Ltd.")](http://joshsoftware.com/index.html)

Special thanks to:

-   [Peter Cooper](http://twitter.com/peterc).
-   Sponsors **Backup My App**, **InformIT** and **Thoughtworks**.
-   [Josh Software Pvt. Ltd.](http://joshsoftware.com/index.html) an
    upcoming Rails start-up in Pune, India for giving us access to a
    private repository on GitHub to store all the submitted solutions.
-   The RubyLearning team, namely Jeff Savin (Canada), Mareike Hybsier
    (Germany), [Michael Kohl](http://citizen428.net/) (Austria), Peter
    Crawford (Italy) and Satoshi Asakawa (Japan).

## Questions?

Contact Satish Talim at [satish [dot] talim [at]
gmail.com](mailto:satish.talim@gmail.com) OR if you have any doubts /
questions about the challenge (the current problem statement), please
post them as comments to this post and the author will reply asap.

## The Participants

There are two categories of participants. Some are vying for the prizes
and some are participating for the fun of it.

### In the competition

1.  Dmytro Shteflyuk, Ukraine
2.  Oleksandr Manzyuk, Ukraine
3.  Rajesh Kumar, USA
4.  Aleksey Gureiev, Australia
5.  Stu Henry, USA
6.  Douglas Barbosa Alexandre, Brazil
7.  Gimi Liang, China
8.  Aldric Giacomoni, USA
9.  Othmane Benkirane, Morocco
10. Paul Smith, England
11. Marc Seeger, Germany
12. Marc Minneman, USA
13. Tim Rand, USA
14. Amr N Tamimi, Palestine
15. Ian Stewart, USA
16. Toni Tuominen, Finland – declared winner (randomly selected)
17. Alexander Klink, Germany
18. Paul McKibbin, U.K.
19. Srikanth P Shreenivas, India
20. Suraj Dhakankar, India
21. Thomas Marek, Germany
22. Rainer Thiel, New Zealand – declared winner (randomly selected)
23. Guillaume Petit, France
24. Paul Damer, USA
25. Dmitriy Nagirnyak, Australia
26. Christian Knappskog, Norway
27. René Scheibe, Germany
28. Pranav Singh, Canada
29. Yuri Omelchuk, Ukraine
30. Benoit Daloze, Belgium
31. Himansu Desai, USA
32. Raoul Felix, Portugal – declared winner (second best solution)
33. Javier Blanco Gutiérrez, Spain
34. Brad O’Connor, Australia
35. Leonardo Bessa, Brazil
36. Radek Kotlarek, Ireland
37. Krzysztof Kotlarek, Poland
38. James Daniels, USA
39. Philippe Antras, France
40. Bill Kayser, USA
41. Jean-Christophe Cyr, Canada
42. **Patrick McKenzie, Japan – declared winner (best solution)**
43. Paul Gallagher, Singapore
44. Clément Julliard, France – declared winner (randomly selected)

### Just for Fun

1.  Satoshi Asakawa, Japan
2.  Alpha Chen, USA
3.  Juan Villanelo, Chile
4.  Dominik Masur, Germany
5.  Tamas Szabo, Australia
6.  Cary Swoveland, Canada

## The Winners

![Winners](http://rubylearning.com/images/winner_icon_1.png)

Congratulations to the winners of this Ruby Challenge. They are:

-   **Patrick McKenzie** from Japan (his [Ruby Challenge
    solution](http://gist.github.com/279979)) – the person with the best
    and most creative Ruby solution. He wins a printed copy of the book
    “[Refactoring in
    Ruby](http://www.informit.com/store/product.aspx?isbn=0321545044)”
    from [InformIT](http://www.informit.com/ruby) and a free 10 GB
    account for a year from [Backup My App](http://backupmyapp.com/).
-   **Raoul Felix** from Portugal (his [Ruby Challenge
    solution](https://gist.github.com/9983432fc2449991eb6b)) – the
    person with an equally good and best packaged (it has extra tests,
    fixtures, the code is easy to read and well structured) Ruby
    solution. He wins any **one** of PeepCode’s [Ruby on Rails
    screencasts](http://peepcode.com/screencasts/ruby-on-rails).
-   **Clément Julliard** from France (his [Ruby Challenge
    solution](https://gist.github.com/c92e6ca45764b4883294)), **Rainer
    Thiel** from New Zealand (his [Ruby Challenge
    solution](https://gist.github.com/37198dbfbe2dbfe11263)), and **Toni
    Tuominen** from Finland (his [Ruby Challenge
    solution](https://gist.github.com/b868e9633eb6b608e324)) – selected
    randomly amongst the remaining working Ruby solutions. They win any
    **one** of Pragmatic’s [The Ruby Object Model and Metaprogramming
    screencasts](http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming).
-   **All the participants in this challenge (except Patrick McKenzie
    who gets a free 10 GB account for a year) will get a free 5 GB
    account for 6 months from [Backup My
    App](http://backupmyapp.com/)**.

## Previous Challenge

[RPCFN: Ruby\*\*Fun
(\#4)](http://rubylearning.com/blog/2009/11/26/rpcfn-rubyfun-4/) by
Michael Kohl.

![Update](http://rubylearning.com/images/update.jpg "Update")

-   This challenge is now closed. Peter Cooper has a [working solution to this problem](http://gist.github.com/258432). This is not a “perfect” or the sole “correct” solution, but just one way of doing it.
-   The (#6) challenge by **John Trupiano, USA** is scheduled for 1st Feb. 2010.

