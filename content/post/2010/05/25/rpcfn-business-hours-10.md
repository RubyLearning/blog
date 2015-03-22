---
draft: false
title: 'RPCFN: Business Hours - 10'
date: 2010-05-25
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: https://www.facebook.com/satishtalim/about
categories:
- Beginners
- RPCFN
- Ruby
layout: post
permalink: /2010/05/25/rpcfn-business-hours-10/
tags:
- programming
- RPCFN
- Ruby
- Ruby Programming Challenge For Newbies
- Ryan Bates
- The Ruby Programming Language
---
## Ruby Programming Challenge For Newbies

### RPCFN: Business Hours (\#10)

#### By Ryan Bates

## About Ryan Bates

![Ryan
Bates](http://rubylearning.com/images/ryan_bates.jpg "Ryan Bates")**Ryan
Bates** has been involved in web development since 1998. In 2005 he
started working professionally with Ruby and Rails and is now best known
for his work on [Railscasts](http://railscasts.com/), the free Ruby on
Rails screencast series.

Ryan has this to say about the challenge:

> *Sometimes when working in a structured framework environment such as
> Rails it is easy to forget about the fundamentals of Ruby and how to
> organize code. The majority of this challenge could be done in one
> large method, but I encourage you to focus on readability through
> refactoring. This challenge also exercises working with times and
> iterations.*

## Our Awesome Sponsor

This monthly programming challenge is sponsored by **Backup My App**.

[![Backup My
App](http://rubylearning.com/images/banner1.gif "Backup My App")](http://backupmyapp.com/)

**Backup My App** is an automatic backup service for Ruby on Rails
applications. You simply install the plugin to your Rails application
and they handle the rest of the process. They store backup history for
several weeks and you can restore any of them automatically. Try out
their 1 GB plan for free. [Backup My App](http://backupmyapp.com/) has
sponsored this challenge and is proud to make this contribution to the
Ruby community.

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

## The Ruby Challenge {style="color:#0000FF;"}

![RPCFN](http://rubylearning.com/images/rubypc.jpg "Ruby Programming Challenge For Newbies")

### The Challenge

Chunky Bacon Begone is a dry-cleaning company known for its speedy
service. It guarantees to dry-clean anything within two business hours
or less. The problem is, when the customer drops off the clothes, he
needs to know what time they are guaranteed to be done.

It is your job to write a Ruby script which will determine the
guaranteed time given a business hour schedule. You must create a class
called **BusinessHours** which allows one to define the opening and
closing time for each day. It should provide the following interface:

    hours = BusinessHours.new("9:00 AM", "3:00 PM")
    hours.update :fri, "10:00 AM", "5:00 PM"
    hours.update "Dec 24, 2010", "8:00 AM", "1:00 PM"
    hours.closed :sun, :wed, "Dec 25, 2010"

The **update** method should change the opening and closing time for a
given day. The **closed** method should specify which days the shop is
not open. Notice days can either be a symbol for week days or a string
for specific dates. Any given day can only have one opening time and one
closing time — there are no off-hours in the middle of the day.

A method called **calculate\_deadline** should determine the resulting
business time given a time interval (in seconds) along with a starting
time (as a string). The returned object should be an instance of
**Time**. Here are some examples:

    hours.calculate_deadline(2*60*60, "Jun 7, 2010 9:10 AM") # => Mon Jun 07 11:10:00 2010
    hours.calculate_deadline(15*60, "Jun 8, 2010 2:48 PM") # => Thu Jun 10 09:03:00 2010
    hours.calculate_deadline(7*60*60, "Dec 24, 2010 6:45 AM") # => Mon Dec 27 11:00:00 2010

In the first example the time interval is 2 hours (7,200 seconds). Since
the 2 hours fall within business hours the day does not change and the
interval is simply added to the starting time.

In the second line an interval of 15 minutes (900 seconds) is used. The
starting time is 12 minutes before closing time which leaves 3 minutes
remaining to be added to the next business day. The next day is
Wednesday and therefore closed, so the resulting time is 3 minutes after
opening on the following day.

The last example is 7 hours (25200 seconds) which starts before opening
on Dec 24th. There are only 5 business hours on Dec 24th which leaves 2
hours remaining for the next business day. The next two days are closed
(Dec 25th and Sunday) therefore the deadline is not until 2 hours after
opening on Dec 27th.

**Tip**: Use **Time.parse** to generate a Time from a string. You may
need to **require “time”** in order to do this.

**Requirements**: This has to be a pure Ruby script, using only the Ruby
Standard Libraries (meaning, no external Gems, libraries). You do not
need to build a gem for this. Pure Ruby code is all that is needed. Ryan
will mostly be judging by the beauty of your code as long as it
satisfies his test case.

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
-   **You should post your entries before midnight of 27th June 2010
    (Indian Standard Time). No new solutions will be accepted from 28th
    June onwards.**
-   On 28th June 2010 all the solutions will be thrown open for everyone
    to see and comment upon.
-   The winning entries will be announced on this blog before 30th June
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

-   [Ryan Bates](http://railscasts.com/).
-   Sponsors **Backup My App**.
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

1.  Simon Menke, Belgium
2.  Colin Casey, Canada
3.  Stephane Tang, France
4.  Juan Villanelo, Chile
5.  Vasko Zdravevski, USA
6.  Sebastián Rabuini, Argentina
7.  Dmitry Lipovoi, Russia
8.  Andy Vanasse, USA
9.  Cary Swoveland, Canada
10. Jeremy Peterson, USA
11. Paul Mucur, UK
12. Delbert Mitten, USA
13. Theo Mills, USA
14. Rémy Coutable, France
15. James Silberbauer, South Africa
16. Michael Cramm, Canada
17. Christopher Fortenberry, USA
18. Tanzeeb Khalili, Canada

### Just for Fun

1.  James Edward Gray II, USA
2.  Eric Hutzelman, USA
3.  Benoit Daloze, Belgium

## The Winners {style="color:#0000FF;"}

![Winners](http://rubylearning.com/images/winner_icon_1.png)

Congratulations to the winners of this Ruby Challenge. They are:

-   **Dmitry Lipovoi** from Russia (his [Ruby Challenge
    solution](https://gist.github.com/e9c0da1a6e92dd12cbc7)) – the
    person with the best and most creative Ruby solution. He wins any
    **one** of PeepCode’s [Ruby on Rails
    screencasts](http://peepcode.com/screencasts/ruby-on-rails) and a
    free 10 GB account for a year from [Backup My
    App](http://backupmyapp.com/).
-   **Michael Cramm** from Canada, **Cary Swoveland** from Canada and
    **Jeremy Peterson** from USA win any **one** of Pragmatic’s [The
    Ruby Object Model and Metaprogramming
    screencasts](http://www.pragprog.com/screencasts/v-dtrubyom/the-ruby-object-model-and-metaprogramming).
-   **All the participants in this challenge (except Dmitry Lipovoi who
    gets a free 10 GB account for a year) will get a free 5 GB account
    for 6 months from [Backup My App](http://backupmyapp.com/)**.

## Previous Challenge

[RPCFN: Interactive Fiction
(\#9)](http://rubylearning.com/blog/2010/04/29/rpcfn-interactive-fiction-9/)
by Avdi Grimm.

**Note**: All the previous challenges, sponsors and winners can be seen
on the [Ruby Programming Challenge for
Newbies](http://ruby-challenge.rubylearning.org/) page.

![Update](http://rubylearning.com/images/update.jpg "Update")

-   This challenge is now closed.
-   All the solutions have been tested and the results are available
    [here](http://github.com/IndianGuru/RPCFN10).
-   The (\#11) challenge by **Elise Huard, Belgium** is scheduled for
    1st July 2010.

