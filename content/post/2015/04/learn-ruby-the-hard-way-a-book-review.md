+++
draft = false
title = "Learn Ruby The Hard Way: A Book Review"
date = "2015-04-25"
author = "Victor Goff"
authorlink = "http://twitter.com/kotp"
socialsharing = true
authorgoogleplus = "https://plus.google.com/+VictorGoff/about"
authorlinkedin = "https://www.linkedin.com/in/vgoff"
authortwitter = "http://twitter.com/kotp"
categories = ["book", "review", "ruby"]
nocomment = false
tags = ["Victor Goff"]
totop = true
+++
A book review of **Learn Ruby the Hard Way - Third Edition**.</br>
Review by: RubyLearning’s mentor Victor Goff.</br>
Book author: Zed A. Shaw.</br>
Publisher: Addison-Wesley</br><!--more-->
                      <!--more-->

**TL;DR**: Great idea, generally a good book.  Many minor problems or things taught
that may be misrepresented.

I got this book a while ago, and of course it is available online as well.  And
though it seems like it might be an easy book to review, it is, what I would
call, a “Pattern Book”.  Due to this, it is actually a bit more difficult to
review.

It is an instructional book, it is teaching you the “hard way”, because you
really need to follow along, it builds up from the basics and gets you to a
good place to continue to learn from.  And it covers a lot.

But it also has a lot of areas to review because of this, a lot of little
technical things.  And I went through every exercise.

One of the things that I got an impression of is that he wrote this while being
immersed in another language.  There are hints of it throughout.  One
problem area, which is not going to be a show stopper, but a problem area
nonetheless, is his explanation about the triple equals in Ruby.  There is no
such thing, but he uses it from the time he introduces it and through the book.
It is little things like this that can shake a new student in the language, if
they even spot it.  If they spot it, they start to wonder what else is not
right.  It can be a pretty large distraction.

This book is patterned from his prior “Learn The Hard Way” books, and follows
along with the theme, which is helpful.  I will be reading more of his books,
as once you now the format of one, you can know what to expect from the others.
The pace is good for a beginner programmer, and I am going through this with my
son who is starting to learn to program.

There are other areas that are difficult though, where he references things
that are not used, but addresses them in the “Questions” section.

There are things that are initially overlooked, using string interpolation early
on (Exercise 2) but not explaining what it does.  Why does the math happen in
`"3 + 2 #{3 + 2}"` inside the brackets?  Sometimes we do ignore things when
instructing but I felt it was fitting to explain at least briefly what is
happening.  But I think that is a little too magical, yet a simple concept, and
could have been at least addressed.

There are places were we are told that an error will happen if we do something,
yet doing so does not raise an error.  This can be very time consuming for
someone new to the language.

Using `gets.chomp.to_i` which I see occasionally in the wild, but it is never
needed together.  (An integer simply will never have a newline, and so you
don't need to remove it before you convert a string with a newline.)  As an
instructional tool, and the third revision, little things like these should be
taken care of.

There were also various areas where there seems to have been printing problems.
Where there should have been a backslash or two, but there were none.  This
happens when you programmatically format material, but with code, it is
important to leave some things alone.  Pretty sure those errors happen in
printing, not in the proofreading process while the material is written.  This
can be seen in some places where there should have been backslashes that should
be in the literal display, indicated by "What you should see" sections but were
removed in print.

The good news is that some of these problems can likely be taken care of in a
pull request.  The distractions are minor if you are teaching, or leading a
group, but reading this alone could be frustrating as you are trying to dig
into what is going on.  Especially since Zed Shaw states in places, to
paraphrase, "Don't worry about it right now, just do as I say."  He has the
right idea, but where there are mistakes it can be very confusing, and very
frustrating.

I would recommend the book for those that are leading a 'workshop' or putting
together some Ruby classes, that can provide the answers when strange things
are presented.  But for those new to Ruby, I can definitely expect some
confusion.  It would be recommended that someone that is familiar with Ruby be
available to answer questions.

I was surprised to see some of these problems in a "Third Edition" copy.

I may update this review once I have completed instructing with it.  This book
is getting a good workout with the questions and findings that someone with
fresh eyes to the language and the book, and a lot of graphite from my pencil
is seeing the surface of the pages with notes an things that could be
corrected.

## Summary

Too many little problems, some outright errors, and some not so
helpful lies, somehow it seems to be missing technical review, and final
proofing.  Yet still a good tool for supervised instruction.

Not a suggested book for a new programmer with no quick feedback loop, someone
to ask.  I would not give this book to one of my kids and leave them to it.
