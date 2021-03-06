---
draft: false
title: Michael Fogus talks to RubyLearning - Clojure Course Participants
date: 2010-03-10
socialsharing: true
author: Michael Kohl
categories:
- Clojure
- Interview
layout: post
permalink: /2010/03/10/michael-fogus-talks-to-rubylearnings-clojure-course-participants/
tags:
- Clojure
- Clojure course
- Clojure Training
- Michael Fogus
- The Joy of Clojure
---
On the eve of the first free, online “**[Clojure
101](http://rubylearning.com/blog/2010/03/09/clojure-101-a-new-course/)**”
course, Michael Kohl of RubyLearning caught up with **Michael Fogus**,
author of the forthcoming book<!--more--> – [The Joy of
Clojure](http://joyofclojure.com/). In this interview, Michael Fogus
talks to the Clojure 101 course participants on **Clojure**.

![Michael
Fogus](http://rubylearning.com/images/fogus.jpg "Michael Fogus")

**Michael\>\>** Welcome, Fogus and thanks for taking out time for
RubyLearning’s Clojure course participants. For their benefit, could you
tell us something about yourself?

**Fogus\>\>** I am a software programmer in the Washington DC area with
a background in Java, C, and C++ creating expert systems, hard real-time
acquisition systems, machine vision, and distributed simulations. Over
the past couple years I’ve been working professionally with Scala and
Java/GWT creating web services and user interfaces. On my own time I am
writing a book for Manning Publishing with a great hacker Chris Houser
titled “The Joy of Clojure” due out in fall 2010. I am an official
external contributor to the Scala language project, but have been
grossly negligent in that respect since starting the work on the book.
Finally, my only other claim to fame is that I am the “official”
custodian of why the lucky stiff’s little language Potion.

**Michael\>\>** How and when did you get involved with Clojure?

**Fogus\>\>** Sometime around October of 2007 I stood at a crossroads. I
had always loved Lisp having used it in undergrad and grad school and
like many programmers of a certain generation found Paul Graham’s Lisp
essays highly inspirational. So around that time I decided to finally
bite the bullet and really learn \*a\* Lisp as deeply as I could and
like many programmers, I decided to write my own. Actually, what I
started writing was a dialect of Scheme in Java that was complete and
utter rubbish, but while researching implementations of big numbers I
came across a Sourceforge project about a language called Clojure. Well,
soon after I scrapped my Scheme as a lost cause and instead decided to
dig deeper into Clojure by using it to write a few pet projects; but was
still mostly just dabbling. However, while reading through Graham’s “On
Lisp” I thought it might be a good idea to port the examples from the
book as a public project to elicit feedback about my style, Clojure
idioms, etc… That exercise turned out to be a huge success for me
because the unbelievably helpful Clojure community was the final and
definitive selling point for the language.

![The Joy of
Clojure](http://www.manning.com/fogus/fogus_cover150.jpg "The Joy of Clojure")

**Michael\>\>** You are currently writing “The Joy of Clojure” for
Manning Publications. What can you tell us about the book and your
co-author Chris Houser?

**Fogus\>\>** There are a few Clojure books coming out including our
own, but I think that ours stands out because it’s meant as the “next”
book on Clojure. That is, we intend to cover not only many of the
advanced techniques, but are also trying to develop the story of
Clojure, or rather the “why” of Clojure. Much of what comprises Clojure
has been done before (although there are plenty of novel ideas also),
but the confluence of features is so well put together that we feel that
readers can come away from a discussion of these underlying ideas a
better programmer overall. As far as my co-author goes, Chris Houser is
likely the most knowledgeable person in the world about Clojure not
named Rich Hickey. It’s been a challenge keeping up with him because the
guy is an endless fount of Clojure knowledge and eats difficult
programming problems for breakfast. It’s very motivational for me to
push out quality content with Houser as the co-author.

**Michael\>\>** Many of RubyLearning’s Clojure course participants have
a Java and or Ruby background. Why, in your opinion, should they learn
Clojure?

**Fogus\>\>** My knowledge of Ruby is superficial at best, so I hope I
do not speak out of turn. Having said that, I think that object-oriented
programming languages in general tend to foster very large solution
spaces. Another interesting point to take away from Clojure is that
immutable data is king. Applications built with the typical
object-oriented idioms are structured as graphs of mutable objects that
is difficult to reason about. However, there is a mountain of
single-threaded code written that seems to be “reasonable”. But with the
advent of multicore CPUs replacing the perpetually rising processor
clock speeds, the need to leverage those cores to gain application speed
will be very important. From day one Clojure has been designed and built
to make concurrent (and in some instances parallel) programming … well,
not easy, because it’s still a very hard problem … possible. Right now I
think there is no language, at least that I’m familiar with, that
facilitates the process of writing applications using shared-memory
concurrency quite like Clojure does.

More generally, Clojure favors simplicity in design and implementation,
with the core tenet being that most problems can be viewed as some
combination of maps, sets, and sequences rather than complex hierarchies
of classes. As a result, Clojure is built to make the case of handling
these abstractions very efficiently. The same efficiencies might not
necessarily be available in either Ruby or Java, but the overarching
goal is the same — striving for simplicity. Finally, Clojure is a
functional programming language at its core and with many programming
languages subsuming some subset of functional ideals, thinking
functionally will be an important skill to cultivate moving forward.

**Michael\>\>** Why do you think that such a free, online Clojure course
at RubyLearning would be beneficial to the Clojure community?

**Fogus\>\>** I think so. Clojure only celebrated its 2nd birthday late
last year, but it’s influence is already being felt throughout the
programming landscape. For example, Clojure’s JVM cousin Scala is
planning to adopt some of Clojure’s immutable, persistent, data
structures for its 2.8 release. People are talking about Clojure and are
hungry for more information, and anything that can spread information
about its benefits is great. All the better if people can get some value
from the proposition.

**Michael\>\>** How should interested developers go about acquiring
knowledge and skills in Clojure? What’s the best approach?

**Fogus\>\>** It’s hard to say since I can only speak from my
perspective, but keeping that in mind I say the best way is to write a
lot of Clojure code. There is a proverb about the game Go that goes
“Lose Your First 100 Games As Quickly As Possible”; it’s this phrase
perfectly describes how I went about learning Clojure. Additionally, I
can’t stress enough the fervent desire to help that pervades the Clojure
community. I think Rich Hickey has done a great job in setting the tone
of the community and leading by example. There is a [Clojure message
group](http://groups.google.com/group/clojure%20) and an IRC channel on
freenode.net \#clojure where really smart people go to talk about
Clojure all day long — drop by, ask questions.

**Michael\>\>** Do you see any areas in the language a would-be Clojure
programmer should concentrate on?

**Fogus\>\>** The immediate things that \*must\* be focused on are the
immutable data structures, laziness, and functional programming styles.
There is really no way around those, and this is a good thing because
they will force you to think about writing code differently. However,
aside from the things that you have no control over I would say that
neophytes should look into the interoperability that Clojure provides
for its host platform. In most cases people will use the Java Virtual
Machine as the host, but there are currently projects targeting the .NET
platform and Javascript. You can’t go wrong exploring Clojure’s
reference types for concurrency: atoms, agents, refs, futures, promises,
and cells (a feature currently being developed). Finally, the next
release of Clojure will provide new features, types and protocols for
structuring your larger codebases in abstract and powerful ways.

**Michael\>\>** After the course, most participants would like to
contribute their time, skills and expertise to a Clojure project but
invariably are unaware of where and how to do so. Could you suggest how
this can be achieved?

**Fogus\>\>** Seriously with the onslaught of GitHub there is no longer
an excuse not to contribute to open-source projects. Just recently
Clojure moved into the top-20 most-popular languages on GitHub, so there
are plenty of opportunities to contribute to many interesting Clojure
projects.

**Michael\>\>** Do you have any suggestions for RubyLearning’s Clojure
course participants? Anything you would like to share with them?

**Fogus\>\>** Well, the fact that they are taking the time to work
through the Clojure course is a good start. It’s tough to motivate
people who are already self-motivated. I guess I’d say to keep it up.

**Michael\>\>** On a final note: What do you perceive as the future of
Clojure?

**Fogus\>\>** Clojure stands as a direct call to action to both Java and
Common Lisp, so minimally it should stimulate some growth in both. I
also think that Clojure’s efficient persistent collection types have all
but signaled the beginning of the end for mutable structures. More and
more languages moving forward will adopt Clojure’s collections outright,
or further their state of the art. Likewise, Clojure’s novel
implementation of Software Transactional Memory system modeled on
database principles (e.g. Multiversion Concurrency Control) for some of
its concurrency features will likely find larger adoption in other
languages. Finally, Clojure in its own right will continue to grow in
popularity as the Lisp that finally breaks through into the mainstream.

*Thank you Fogus. In case you have any queries and/or questions, kindly
post your questions here (as comments to this blog post) and Fogus would
be glad to answer.*
