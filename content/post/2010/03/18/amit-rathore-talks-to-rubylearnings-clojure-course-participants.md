---
draft: false
title: Amit Rathore talks to RubyLearning's Clojure Course Participants
date: 2010-03-18
author: Michael Kohl
socialsharing: true
categories:
- Clojure
- Interview
layout: post
permalink: /2010/03/18/amit-rathore-talks-to-rubylearnings-clojure-course-participants/
tags:
- Amit Rathore
- Clojure
- Clojure course
- Clojure in Action
- Clojure Training
---
On the eve of the first free, online “**[Clojure
101](http://rubylearning.com/blog/2010/03/09/clojure-101-a-new-course/)**”
course, Michael Kohl of RubyLearning caught up with **Amit Rathore**,
author of the forthcoming book – [Clojure in
Action](http://www.clojureinaction.com/). In this interview, Amit
Rathore talks to the Clojure 101 course participants on **Clojure**.

![Amit
Rathore](http://rubylearning.com/images/amitrathore.png "Amit Rathore")

**Michael\>\>** Welcome, Amit and thanks for taking out time for
RubyLearning’s Clojure course participants. For their benefit, could you
tell us something about yourself?

**Amit\>\>** I’ve been programming since I was 11, and been designing
and developing software systems in a professional setting for about ten
years now. The last few years have seen me transition from Java to Ruby,
along with a smattering of other languages such as Python, Scheme, and
Smalltalk. Since late 2008, I’ve been using Clojure full-time. I’ve made
a few open-source contributions to the Clojure community – some examples
are data-mappers for HBase and Redis, and another one called Swarmiji
which allows you to write distributed programs (that span multiple CPUs,
not just multiple cores) in Clojure. I’m currently the Chief Software
Architect at a startup called [Runa](http://runa.com/), in Mountain
View, CA. We are a provider of SaaS solutions to online e-tailers to
enable them to provide real-time, analytics-driven promotions to their
shoppers. More than 90% of our backend is written in Clojure.

**Michael\>\>** How did you get involved with Clojure?

**Amit\>\>** As I said earlier, I’ve used Scheme on my personal projects
from time to time. At Runa, we always knew we could benefit from using a
Lisp for our back-end, what with all the analytics and machine-learning
that the system needs to do. When all the scalability requirements were
thrown in, we seriously considered using Erlang, thanks to it being
functional and its concurrency support. It was just around then that the
Clojure community really started taking off, and we decided to try it
out. We’ve never looked back, and we’re extremely pleased with the
outcome so far. Our analytics-powered, adaptive, conversion-marketing
engine is miles ahead of any potential competition… and we can add
features (and make sure things still work, and are as performant as
needed) faster than any potential competition. If you have read Paul
Graham’s essay called Beating The Averages, you know what I’m talking
about. In Jan 2009, following our initial Clojure deployment, I started
the [Bay Area Clojure User
Group](http://www.meetup.com/The-Bay-Area-Clojure-User-Group/). It’s
going to host its 17th Meetup next month. It’s great to see the
community growing, and its great being a part of it.

**Michael\>\>** You are currently writing “Clojure in Action”. What can
you tell us about the book?

**Amit\>\>** When Manning Publications contacted me regarding a new
Clojure book, they wanted something different from what was already
available, and what they knew was in progress. When we discussed my
Clojure experience and startup background, we came up with the concept
of the Clojure in Action book. The idea basically resulted in a Clojure
book that does a few things:

1.  Teaches Clojure from first principles i.e. why are certain things
    the way they are, and how they’re better than what currently exists
    in popular languages.
2.  Teaches a developer new to Clojure to get going after reading the
    book – it answers the “OK, what now?” question – by addressing
    issues like test-driven development, IDEs, dependency management,
    debugging/profiling, and so on.
3.  Real-world usage for web-scale applications – from all the
    experience I’ve gleaned working with HBase, Redis, RabbitMQ, Amazon
    services, Hadoop/MapReduce, and so on.
4.  And finally, advanced usage of macros to build DSLs (domain-specific
    languages). So readers of all levels will get something from the
    book – folks new to Clojure can get started quickly, while
    intermediate to advanced users can gain also.

**Michael\>\>** Many of RubyLearning’s Clojure course participants have
a Java and or Ruby background. What, according to you, are the benefits
to these participants after learning Clojure?

**Amit\>\>** The functional approach is just a better way to program. So
that, in itself, is a huge learning opportunity. In the words of Eric
Raymond, the famed hacker, “LISP is worth learning for a different
reason — the profound enlightenment experience you will have when you
finally get it. That experience will make you a better programmer for
the rest of your days, even if you never actually use LISP itself a
lot.” And the great news is that Clojure, the latest incarnation of
LISP, is actually so usable that once you start, you will never want to
program in any other language again. This influence includes
meta-programming, which will especially benefit Ruby folks. On the other
hand, it will also make developers from both the camps (especially Java)
realize just how limiting their languages are. Actually, this is also a
good thing.

**Michael\>\>** Why do you think that such a free, online Clojure course
at RubyLearning would be beneficial to the Clojure community?

**Amit\>\>** Clojure will only succeed if more and more people adopt it.
While it is a no-brainer once you understand what it offers in terms of
productivity and code-quality, it has the initial problem of
getting-the-word-out. Such a free, online course can do this quite
effectively.

**Michael\>\>** How should they go about acquiring knowledge and skills
in Clojure? What’s the best approach?

**Amit\>\>** There is one book published so far, and several coming out.
Those are good resources. There are plenty of tutorials online, as well
as a ton of open-source code which can be great resources. There are
several very active Clojure user groups around the country, and indeed
all over the world. Also, the IRC channel is fantastic.

**Michael\>\>** Which areas in Clojure should a would-be Clojure
programmer concentrate on?

**Amit\>\>** Functional programming would be an important topic. People
coming from an imperative background have to sort of re-wire their
brains. Another topic is “the Lisp way”, which is this idea of bottom-up
design (as opposed to the traditional top-down approach to breaking
things down). Creating mini-languages (fashionably called Domain
Specific Languages these days) that allow the developer to program at a
much higher-level of abstraction is another important design philosophy.
These I’d say are things that take time to really “get into”… so some
deliberate attention should be paid them. Other things, such as
Clojure’s concurrency mechanism are also important, and yet easy to
learn and use.

**Michael\>\>** Do you have any suggestions for RubyLearning’s Clojure
course participants? Anything you would like to share with them?

**Amit\>\>** I’d just like to say this: As developers gain experience,
they learn certain things that become guiding principles. One such thing
is the power of abstractions. As they gain expertise of the programming
language they’re using, they discover the natural limit to the kind of
abstractions that their language of choice can create. They realize that
certain things just can’t be expressed in that language. At times this
manifests in wishing that the language had this feature or that. Lisp
frees you from such tyranny. The parenthesis are there for a reason, and
that reason is to make the macro system possibly. And that makes
wonderful things happen. And Clojure is an incredible Lisp. So, stay
with it, give it a real go, the parenthesis disappear in a few days, and
the real power becomes apparent. And then you can never go back
![:)](http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif)

**Michael\>\>** After the course, most participants would like to
contribute their time, skills and expertise to a Clojure project but
invariably are unaware of where and how to do so. Could you suggest how
this can be achieved?

**Amit\>\>** There are plenty of open-source projects that add something
to the Clojure world. GitHub is a great place to start looking, and
there are others.

**Michael\>\>** On a final note: What do you perceive as the future of
Clojure?

**Amit\>\>** We are all craftsmen: programming languages and software
requirements are our raw material. Given that complexity of software
requirements is continuing to grow, it behooves us all to use better and
better tools and languages to create the next software system. As a
matter of fact, tomorrow’s software almost needs to be adaptive – it
needs to learn and adjust its behavior based on things like the data
that it sees, or patterns of usage, and so on. This kind of complexity
needs really flexible and powerful tools on the implementation side. A
Lisp is a natural fit for such a dynamic, demanding world. Further,
Clojure’s functional and concurrency story is very strong – as software
moves to clouds of multi-core CPUs, this becomes a great advantage.
Finally, being able to leverage battle-tested Java libraries in such a
seamless manner is another boon. I see more and more people being
enlightened about these issues, and more and more adoption of Clojure.
I’d be very surprised if it doesn’t become the discerning developer’s
first choice within the next couple of years.

*Thank you Amit. In case you have any queries and/or questions, kindly
post your questions here (as comments to this blog post) and Amit would
be glad to answer.*
