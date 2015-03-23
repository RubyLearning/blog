---
draft: false
title: 'Interview: Chris Wanstrath of GitHub'
date: 2009-02-21
author: Chris Wanstrath
socialsharing: true
andre.java@gmail.com:
- andrefaria
ashbbb@gmail.com:
- ashbb
categories:
- Beginners
- Interview
- Ruby
- Training
description:
- On the eve of the first ever free, online course on "Git and GitHub", Chris Wanstrath
  founder of GitHub talks to RubyLearning.
jccalistro@gmail.com:
- joaocalistro
keywords:
- Chris Wanstrath
- Git
- GitHub
- Interviews
- Ruby
- The Ruby Programming Language
layout: post
permalink: /2009/02/21/interview-chris-wanstrath-of-github/
tags:
- Chris Wanstrath
- Git
- GitHub
- interviews
- Ruby
- The Ruby Programming Language
---
On the eve of the first ever free, online course on “Git and GitHub”,
Satish Talim of RubyLearning caught up with **Chris Wanstrath** and
talked to him, in this short interview.

![Chris Wanstrath,
USA](http://rubylearning.com/images/ChrisWanstrath.jpg "Chris Wanstrath, USA")

**Satish Talim\>\>** Welcome, Chris and thanks for taking out time to
share your thoughts. For the benefit of the readers, could you tell us
something about your self?

**Chris Wanstrath\>\>** I’m a Ruby and JavaScript programmer living in
San Francisco, CA. *I was one of the guys who started **GitHub***. When
I’m not working on the site, I can be found playing guitar or drinking
bourbon. Sometimes at the same time!

**Satish\>\>** Why according to you, is it important for a new Ruby
developer to know and use Git and GitHub?

**Chris\>\>** I learned how to program by reading other people’s code
and contributing to open source projects. Submitting a patch and seeing
how the maintainer rewrites it is invaluable: it’s like getting free,
personalized programming lessons from someone with more experience than
you.

GitHub is important because it’s one of the best places to participate
in active open source development. The barrier to entry is extremely
low, and with casual forking it’s basically designed for the “make small
changes to a foreign project and see what happens” workflow.

**Satish\>\>** Why GitHub? Why not SourceForge?

**Chris\>\>** SourceForge is about publishing projects, GitHub is about
collaborating on code. SourceForge is helpful when exploring or working
on projects, but this is really where GitHub shines.

**Satish\>\>** What were the challenges of putting GitHub together?

**Chris\>\>** We’re still facing them today. We not only have to worry
about the database when growing, but also Git repositories on disk – we
essentially have two different data stores, one of which has never been
used at this scale before. We’re constantly doing lots of very cool
caching things under the hood to try and make everything faster.

Big database tables and high IO are our biggest issues. I think the key
is to recognize problems early on and not be afraid of throwing out
existing code in order to implement a better solution. It’s okay to do
things the simple way early on – probably better, really – but you need
to understand that they’re only going to take you so far before you need
to spend more time coming up with a smarter solution that works for
higher load.

**Satish\>\>** Do you have any suggestions for RubyLearning’s Git &
GitHub course participants?

**Chris\>\>** Create and share open source – whether on GitHub or
elsewhere! It’s very rewarding, a great way to meet people, and the best
way to improve your skills.

**Satish\>\>** Thanks Chris for sharing your views with the RubyLearning
GitHub course participants.

***Disclaimer:***\
*The opinions expressed are those of Chris Wanstrath and do not
necessarily reflect those of
**[www.RubyLearning.com](http://rubylearning.com/)**.*

