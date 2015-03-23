---
draft: false
title: 'Interview: Author Dave Thomas'
date: 2009-05-24
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/rubylearning
categories:
- Beginners
- Book Promotions
- Interview
- Promotions
- Ruby
description:
- Dave Thomas, author of Programming Ruby 1.9 talks to RubyLearning.
keywords:
- Dave Thomas,Programming Ruby 1.9,Ruby programming,Book promotion,Pragmatic Programmer
layout: post
permalink: /2009/05/24/interview-author-dave-thomas/
tags:
- Book promotion
- Dave Thomas
- Pragmatic Programmer
- Programming Ruby 1.9
- ruby programming
---
Our Book Promotion: “**Programming Ruby 1.9**” starts soon. Win one of
four books to be given out for active participation. The coolest thing?<!--more-->
Author **Dave Thomas** will be on site to answer questions! [Click
here](http://rubylearning.com/blog/2009/05/24/book-promotion-programming-ruby-19/)
for more details. Here, in this brief interview, Satish Talim of
RubyLearning talks to Dave Thomas.

![Dave
Thomas](http://www.pragprog.com/images/people/dave-large.jpg "Dave Thomas")

**Satish\>\>** Dave, could you tell us something about yourself – your
background, where you are based?

**Dave\>\>** Well, I was born in Cheshire, England (up by Liverpool). My
family moved around when I was young, living in Canada and the US,
before moving back to England in time for my secondary schooling. Back
then, we took a group of exams when you were 15/16 (the O-levels) and
another set at 18 (A-levels). A bunch of us took O-levels early, and the
school was looking for something that would keep us busy. The local
technical college had just started an A-level course in computers, so
some of us wandered across the road and started taking it. I fell in
love in the first week. We were creating Basic programs on paper tape
using an ASR-33 teletype, then sending them over a 110 baud modem to our
local town council’s ICL mainframe. And it was great! Somewhere in the
middle of that year I wrote what it possibly the world’s only
self-modifying Basic programâ€”we were only allowed to store 5 programs
up on the mainframe, so I wrote a program that stored other programs
inside itself, and that would extract and run those programs on demand.
The following summer I got a job writing code for a local water board,
and I decided to change my college applications from mathematics to
computer science. I ended up at Imperial College in London, which had an
incredibly good courseâ€”I enjoyed every minute (apart, perhaps, from
the statistics… :).

After graduating I worked for a small start-up. Initially the work was
in the UK, but pretty soon I was traveling around the world. The work
was great fun: we were doing all the weird interfacing between large
systems and different kinds of front ends (including some early
precursors to web browsers). I also worked for a small UK computer
manufacturer in their skunk works. Probably the most interesting project
there was the low-level interfaces to the hardware that did the checkout
of the Giotto satellite that went to Comet Halley.

I met my wife on a project in New York. After we married, she moved back
to the UK with me, but after our first boy was born we moved over to
Dallas, Texas, where I’ve now been living for 15 years.

Andy Hunt and I met on a project in the mid 90s, and we’ve been working
together ever since. We wrote *The Pragmatic Programmer*, and formed a
business of the same name. A few years later, we used the experience we
gained on the production side of that book to form our own publishing
business. That business has grown and grown, and now takes the majority
of our time. But, I still carve out time to play with softwareâ€”that’s
still my passion.

![Programming Ruby
1.9](http://rubylearning.com/images/ruby3_180.png "Programming Ruby 1.9")

**Satish\>\>** Who’s the audience for your book – Programming Ruby 1.9?
Does it teach Ruby programming or is it a reference book?

**Dave\>\>** I first came across Ruby about 10 years ago. At that time,
almost no one outside Japan had heard of it. Andy and I both wanted to
use Ruby in a book project we were considering, but discovered that the
explanations of Ruby were getting in the way of the material that was
supposed to be the topic of the book. So we put the original book
project on hold, and instead started writing up notes on Ruby. We wrote
those notes for developers who knew a programming language and who
wanted to get good at Ruby. And we wrote the book we’d want to read
ourselves: a fairly fast tutorial that skims through the main features,
starting not at the bottom (variables and if statements) but instead at
the top (classes and objects). After this, there’s a section on the
environment in which Ruby programs run: basically describing how to use
Ruby in the real world. We then documented all the built-in classes and
methods that come with Ruby. So it’s really three books in one. Anyone
who has programmed should find it an easy and instructive read. It both
teaches Ruby and is a reference.

**Satish\>\>** What all has changed from the first edition of the book?

**Dave\>\>** Oh, a lot! The most obvious changes have been driven by
Ruby itself. Ruby 1.9 has a ton of exciting new features. It’s
multinationalisation support is unprecedented. It now has a far more
functional feel. And a whole lot more classes and methods are now built
in. I haven’t counted, but I’d guess the number of built-in methods has
doubled since that first edition.

At the same time, much has changed in the Ruby community since that
first edition. When the first edition came out, almost no one was using
Ruby, so we didn’t really know good ways to do things. Now we know a lot
more, and I’ve tried to incorporate all that experience that we’ve
gained into the book.

Finally, I’ve taken literally thousands of pieces of individual feedback
and used them to change the way I describe things. The tutorial in
particular has changed a lot, and now contains many more self-contained
example programs.

I’m very proud of this resultâ€”the book is both an evolution of the
previous two books, but it’s also a fairly dramatic rewrite.

And, just to clarify, *Programming Ruby 1.9* is technically not a new
edition of the previous book. We originally planned it to be, as we
anticipated that Ruby 1.9 would replace Ruby 1.8. But the reality is
that many people are still using 1.8, so we wanted to keep the second
edition of the PickAxe (which covers 1.8) around as well. Booksellers
automatically pull a prior edition out of stock if you release a new
one, and we didn’t want that to happen, so *Programming Ruby 1.9* is
technically a brand new book, rather than being a new edition.

**Satish\>\>** Tell us something about “The Pragmatic Bookshelf”.

**Dave\>\>** Andy and I wrote both *The Pragmatic Programmer* and the
first edition of *Programming Ruby* for Addison Wesley. But, unlike most
authors, we did all the typesetting, layout, indexing, and so on,
ourselves.

I wrote most of the book production system for this exercise. I wanted
to avoid that kinds of problems most technical book authors face. I
wanted to keep my source code in real program files, where it could be
run and tested, rather that cut-and-paste it into the book. I wanted to
use plain text to store the book’s content, because then we could use
programmer’s tools, such as source code control, `grep`, and `diff`. And
I wanted the books to look nice.

After finishing the Ruby book, we got back to our consulting business.
And we noticed that many of the teams we were working with didn’t use
basic practicesâ€”things such as unit testing, source code control, and
automationâ€”that we considered essential to successfully completing
software projects. So we decided to start writing a set of three books
on these areas. We were going to write them with Addison Wesley, but we
got to thinking: we already had the technology to create the books: all
we’d need is access to a book printer and a way of distributing the
result. How hard could that be? Well, that’s what we did. And we’re
still discovering just how hard the rest is!

But we’ve had a blast. The Pragmatic Bookshelf isn’t like other
publishers. For a start, we’re a publisher for developers. We use
developer tools to get books created. When you sign up as an author, we
create a Subversion repository where you write your book. You don’t use
something like Word to author your text. Instead you write directly in
the markup language that we use to create the final typeset product.
This means that you’re always working with what will become the final
bookâ€”we don’t take what you type and then get someone else to typeset
it using a different tool. This immediacy means we can get a book into
print faster that just about anyone else. If you want, you can build
that final version on your machine, just as we do when we send a book to
the printer. Or you can let our continuous build system do it for you.

We also automate just about everything we can. For example, if an author
has an updated version of a book that they’d like to push out to their
readers, I can issue a single `rake` command (`rake` is a build tool
written in Ruby) will create up-to-date PDF, mobi, and epub versions of
the book.

The heavy use of tools and automation means that our overhead is really
low. And that in turn means we can pay our authors well: we pay 3 to 4
times more as a royalty than other publishers we know.

It also helps that we really aren’t publishers, so we don’t know how
things are supposed to be done. I think we were the first people to
offer PDF versions of all our titles. (We now offer epub and mobi
versions too, for use on eBook devices and mobile phones). We were the
first publisher to have a solid beta-book program, where we give readers
early access to books as they are in development. I think we were the
first publisher to create electronic versions of our books with no DRM,
instead adding a simply watermark to the books and relying on our
customers’ honesty.

From my personal perspective, it’s a very heady business: I get to help
select books that we publish based on books that I’d personally like to
read. How cool is that?

**Satish\>\>** I know that it is too early to say, but looking back are
there some topics that you now wish should have been covered or dropped
from the book?

**Dave\>\>** Not really: I only just finished the book, and I made all
the changes I wanted to make while I was rewriting it.

Every now and then I think that maybe I should split it into two books,
but I still think it’s valuable to have all the content in one place.
Having it in one volume also makes it cheaper for its readers.

**Satish\>\>** Anything else you would like to add?

**Dave\>\>** Although I know this is supposed to be a book promotion,
I’d like to take to opportunity here to talk about Ruby, too. I love the
language, and after more than 10 years still find new things that
surprise and delight me. I’d love to talk with your members about those
thingsâ€”about the importance of loving and respecting the tools that
you use. I’d love to talk about Ruby 1.9, and about all the various
issues that surround the language. Let’s make programming fun again!

*Thank you Dave. In case you have any queries and/or questions, kindly
post your questions here (as comments to this blog post) and Dave would
be glad to answer.*

