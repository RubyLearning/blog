---
draft: false
title: 'RPCFN: XML Transformer - 8'
date: 2010-04-07
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
permalink: /2010/04/07/rpcfn-xml-transformer-8/
tags:
- jamie van dyke
- programming
- rpcfn
- ruby
- ruby programming challenge for newbies
- the ruby programming language
---
## Ruby Programming Challenge For Newbies

### RPCFN: XML Transformer (\#8)

-- By Jamie van Dyke

## About Jamie van Dyke

![Jamie van
Dyke](http://rubylearning.com/images/jamiedyke.jpg "Jamie van Dyke")Jamie
van Dyke has been using Ruby and Rails since the beginning of 2005, has
contributed significantly to the Rails documentation and code base, as
well as running his own Rails business and being responsible for
building Engine Yard’s European support team. Jamie is now the CTO over
at [Boxedup](http://www.boxedup.com/).

Jamie has this to say about the challenge:

> *This challenge is ideal for both beginner and advanced users. You can
> solve it in multiple ways and with differing levels of complexity,
> each level giving more flexibility. I hope you enjoy trying to solve
> the challenge and I look forward to seeing the results.*

## Our Awesome Sponsors

This monthly programming challenge is co-sponsored by **Eden
Development** and **Backup My App**.

[![A leading software development firm based in Winchester,
UK](http://rubylearning.com/images/eden-new-logo-leaf-square.png "A leading software development firm based in Winchester, UK")](http://edendevelopment.co.uk/)

**[Eden Development](http://edendevelopment.co.uk/)** is a leading
software development firm based in Winchester, UK, specialising in Ruby
applications. They craft dependable, flexible and beautifully made
software which meets real business needs. They stand for quality,
integrity, real craftsmanship and peace of mind for their customers.
They also teach basic Ruby to Agile/XP courses: they love learning
themselves and are delighted to support the RubyLearning initiative.

[![Backup My
App](http://rubylearning.com/images/banner1.gif "Backup My App")](http://backupmyapp.com/)

**Backup My App** is an automatic backup service for Ruby on Rails
applications. You simply install the plugin to your Rails application
and they handle the rest of the process. They store backup history for
several weeks and you can restore any of them automatically. Try out
their 1 GB plan for free. [Backup My App](http://backupmyapp.com/) has
co-sponsored this challenge and is proud to make this contribution to
the Ruby community.

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

#### Introduction

I love a good challenge and find it helps you discover different aspects
of a language, and also different methods to achieve the same goal.
Seeing how others completed a quiz also helps you to expand your
knowledge and experience which will give you more insight in the future.

The best tests are always ones based on real world examples. I’ve tried
to simplify this one so it’s accessible to all that want to take a stab,
while at the same time allowing those that one to be more advanced the
opportunity to show off a little. You could complete this with a simple
solution, or spend more time and give an elegant, more ruby-ish answer.
You choose.

A library I recently wrote had to import data on a regular basis. I
needed to normalise the data before I could import it because the data
was from different XML feeds, but in unknown formats. So, your challenge
is to build an XML transformer that can take any (within reason) XML
file and change it into an expected XML format.

#### Specifics

You can [download 3 source XML
files](http://rubylearning.com/data/xmlfiles.zip) as examples. You need
to work out how to convert each of these files in to the expected
output, bearing in mind that these are merely examples and therefore you
should make your transformer as flexible as possible to handle other
source inputs.

You will need to employ the use of an XML library, personally I use the
**nokogiri rubygem**, but feel free to choose your own. Once you’ve
decided on XML parser it’s up to you how you go about solving this quiz.
I’ve designed this quiz to give you the freedom to solve this however
you see fit, the only stipulation is that you stick to Ruby!

#### Additional Information

**Qs.** Do we have to use an XML parser?

**Ans.** Well, no, but it will probably be easier if you do.

**Qs.** Is it okay to assume that the source file has only first names
and last names? It has no other data, e.g. ages, sexes, … ?

**Ans.** In this example there are only 2 fields that you need to worry
about. Bonus points go to the results that can handle multiple formats
with multiple fields. Of course, any file that has 3 fields in the
source, should be outputting 3 fields in the result.

**Qs.** Is it necessary to indent output data (result xml)?

**Ans.** The results may ignore whitespace outside of elements but not
inside.

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
-   **You should post your entries before midnight of 26th Apr. 2010
    (Indian Standard Time). No new solutions will be accepted from 27th
    Apr. onwards.**
-   On 27th Apr. 2010 all the solutions will be thrown open for everyone
    to see and comment upon.
-   The winning entries will be announced on this blog before 30th Apr.
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
!](http://www.pledgie.com/campaigns/415.png?skin_name=chrome)](http://www.pledgie.com/campaigns/415)

## Acknowledgements

Special thanks to:

-   [Jamie van Dyke](http://www.boxedup.com/).
-   Sponsors **Eden Development** and **Backup My App**.
-   [GitHub](http://github.com/), for giving us access to a private
    repository on GitHub to store all the submitted solutions.
-   The RubyLearning team, namely Satoshi Asakawa (Japan) and Victor
    Goff III (USA).

## Questions?

Contact Satish Talim at [satish [dot] talim [at]
gmail.com](mailto:satish.talim@gmail.com) OR if you have any doubts /
questions about the challenge (the current problem statement), please
post them as comments to this post and the author will reply asap.

## The Participants

There are two categories of participants. Some are vying for the prizes
and some are participating for the fun of it.

### In the competition

1.  Richard Colley, Australia
2.  **Paul Barry, USA – declared winner (best solution)**
3.  John Prince, USA – declared winner (randomly selected)
4.  Tanzeeb Khalili, Canada – declared winner (randomly selected)
5.  Rémy Coutable, France
6.  Adam Lum, USA – declared winner (randomly selected)
7.  Vijay Thiruvallur, India
8.  Benoit Daloze, Belgium

### Just for Fun

## **The Winners**

![Winners](http://rubylearning.com/images/winner_icon_1.png)

Congratulations to the winners of this Ruby Challenge. They are:

-   **Paul Barry** from USA (his [Ruby Challenge
    solution](https://gist.github.com/9575443f97f8f09bf104)) – the
    person with the best and most creative Ruby solution. He wins any
    **one** of PeepCode’s [Ruby on Rails
    screencasts](http://peepcode.com/screencasts/ruby-on-rails) and a
    free 10 GB account for a year from [Backup My
    App](http://backupmyapp.com/).
-   **Adam Lum** from USA, **John Prince** from USA and **Tanzeeb
    Khalili** from Canada win any **one** of Pragmatic’s [The Ruby
    Object Model and Metaprogramming
    screencasts](http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming).
-   **All the participants in this challenge (except Paul Barry who gets
    a free 10 GB account for a year) will get a free 5 GB account for 6
    months from [Backup My App](http://backupmyapp.com/)**.

## Previous Challenge

[RPCFN: Broadsides
(\#7)](http://rubylearning.com/blog/2010/02/23/rpcfn-broadsides-7/) by
James Edward Gray II.

**Note**: All the previous challenges, sponsors and winners can be seen
on the [Ruby Programming Challenge for
Newbies](http://ruby-challenge.rubylearning.org/) page.

![Update](http://rubylearning.com/images/update.jpg "Update")

-   This challenge is now closed.
-   The (\#9) challenge by **Avdi Grimm, USA** is scheduled for 1st May
    2010.

