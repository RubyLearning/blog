---
title: 'Interview with Ola Bini &#8211; JRuby Core Developer'
author: Satish Talim
date: "2007-08-30"
layout: post
permalink: /2007/08/30/interview-with-ola-bini-jruby-core-developer/
categories:
  - interview
  - jruby
  - rails
  - ruby
---
[![Ola
Bini](http://www.rubylearning.com/images/ola.jpg)](http://www.rubylearning.com/images/ola.jpg "Ola Bini")

*RubyLearning caught up with **[Ola
Bini](http://ola-bini.blogspot.com/)** at Bangalore, India and talked to
him about JRuby. Ola provides some insights for easy adoption of JRuby
by the large pool of Java and Ruby developers in India.*
<!--more-->

**Hello Ola, and welcome to RubyLearning.com. Tell us something about
your background and how you came to JRuby.**

Well, I’m a programming language geek and have looked at many languages
for a long time. I’ve used LISP since before I can remember, but Java
have always been the language that is economically viable to use. But
I’m not that fond of the Java language – the platform is very good, but
the language… well. So I looked around for something better. I’ve known
Ruby for a few years; it’s got some very nice similarities to LISP,
Smalltalk and other very nice languages. Finally I found the JRuby
project, realized that it would hit my sweet spot perfectly and decided
to start helping out on it.

**Could you tell us some reasons on why a Ruby developer should start
looking into JRuby?**

There are several good reasons: most of the problems of Ruby 1.8 are
actually resolved by JRuby in one way or the other. You get better
threading semantics, native unicode, active development, easier
extensions, very good garbage collection – and superb integration with
Java libraries. All of these are very nice things for a Ruby developer
since they fix deficiencies in the current MRI 1.8.

**How should a person working on Ruby approach JRuby?**

The first step is just to try your application out on it. If it’s a
regular Ruby application that doesn’t use native extensions, the chance
is very good that it will just run on JRuby. The next step – after the
application runs – is to get ready to integrate some of the Java
specific libraries and start using them instead. For example, theres a
backend to REXML that uses Java libraries instead; this makes REXML much
faster and also safer. It will also add new capabilities to REXML, like
validation and so on. And this is with the exact same interface as
regular REXML, so you get all this for free, just by moving. The same
thing applies for running JRuby on Rails, and using JDBC as a back end
connector.

**With a stable release now in hand what is your current focus and
roadmap for JRuby?**

Well, the current focus is on completing the compiler and also working
on performance. We are not making huge changes in the functionality
right now – instead looking at external libraries that enhance the value
of JRuby.

**Can you give some examples where JRuby is being persistently used?**

Well, ThoughtWorks sells Mingle, which runs on JRuby on Rails. Sun has
some JRuby projects. Oracle is working on JRuby projects. And there are
many, many smaller projects being developed all around the world.

**Can you tell us one area of JRuby wherein you feel there needs to be
an improvement?**

Well, the 1.0-release was focused on compatibility. The performance was
pretty good, but now we really want to surpass MRI in performance. So
that’s what we’re working on right now. Aside from that, documentation
is sorely needed too. (My book, that comes out Sept. 24th, will probably
help some with that.)

**Is there a plan to have a developers tool for JRuby?**

Well, right now there is a lack of development tools for Ruby itself –
many companies are working on it though. These tools will work for JRuby
too. I know that NetBeans are planning to add some JRuby specific things
to their Ruby tool later on.

**Can you highlight on some good mechanisms for deploying JRuby based
applications?**

That’s kinda hard. If you’re talking about Rails applications, using WAR
based deployment to a Java application server is generally the best
solution.

**How is the performance and scalability aspect of JRuby?**

I addressed performance above. Scalability is another thing. Generally
JRuby takes more memory than MRI, but usually scales better due to
better threading.

**Finally, how easy it is to pickup JRuby? Any pointers?**

It’s as easy as picking up Ruby. It’s really easy to get started, and if
you google for the JRuby wiki, you will find lots of good information
for getting started. Once again, my book will help here…
![:)](http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif)

*Thanks Ola for sharing your views with the RubyLearning.com members.*

Technorati Tags: [Interview with Ola Bini – JRuby Core
Developer](http://technorati.com/tag/Interview+with+Ola+Bini+%26%238211%3B+JRuby+Core+Developer),
[Interviews](http://technorati.com/tag/Interviews),
[JRuby](http://technorati.com/tag/JRuby), [Ola
Bini](http://technorati.com/tag/Ola+Bini),
[Ruby](http://technorati.com/tag/Ruby), [Ruby on
Rails](http://technorati.com/tag/Ruby+on+Rails), [Ruby
Interviews](http://technorati.com/tag/Ruby+Interviews)
