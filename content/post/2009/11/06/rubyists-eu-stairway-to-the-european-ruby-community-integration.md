---
draft: false
title: 'Rubyists.EU: Stairway to the European Ruby Community Integration'
date: 2009-11-06
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: http://www.facebook.com/rubylearning
categories:
- News
- Ruby
layout: post
permalink: /2009/11/06/rubyists-eu-stairway-to-the-european-ruby-community-integration/
tags:
- European Ruby Community
- Ruby
- Rubyists.EU
- The Ruby Programming Language
---
A Guest Post By [Mariela Dimitrova](http://twitter.com/dream_warrior),
[Gustavo Malamud](http://twitter.com/gusma) and [Javier
Cicchelli](http://twitter.com/monsieur_rock).<!--more-->

![European Ruby Community
Integration](http://rubylearning.com/images/EULogo.png "European Ruby Community Integration")At
the beginning of October 2009, a project, sweeping in both scope and
ambition, was born. Begotten out of the current integration trends in an
ever shrinking world with porous boundaries, this initiative is an
attempt to fill in a paradoxical void. Indeed, whereas the Internet has
dismantled the final barriers that prevent people from promoting their
work, sharing their knowledge, and cooperating with one another, it
still appears to be quite difficult to establish better communication
and keep in touch with Rubyists in Europe.

Driven by the idea that Ruby/Rails hackers and user groups in the Old
Continent do have something to show and share, the [Rock &
Code](http://rock-n-code.com/) team came up with the concept of
[Rubyists.EU](http://rubyists.eu/). In its essence, this initiative is a
free of charge communications platform, which aims at encouraging better
communications among communities and individual enthusiasts across
Europe. Its brave mission is to promote awareness, enhance assistance,
and further boost cooperation and collaboration among Ruby/Rails hackers
and user groups in Europe. This initiative harbors the grand vision that
in time, by forging long lasting bonds, European Rubyists could foster a
sense of belonging to something bigger than their local communities. All
the enthusiasts and, respectively, all the Ruby/Rails communities in
Europe are invited and encouraged to join forces on the
[Rubyists.EU](http://rubyists.eu/) arena of action and interaction.

This bold initiative has the potential to become a treasure trove for
both Ruby/Rails developers and communities in Europe. Indeed, by
partaking in **Rubyists.EU**, members can attach an extra layer of
visibility to their groups and respectively, to themselves. Enthusiastic
hackers have the opportunity to join new communities or even found their
own. Rubyists can share delicious details about their regular group
meetups, bring interesting events and conferences to the attention of
others, announce special presentations, make their groundbreaking Ruby
advancements public, or simply publish the pioneering Ruby projects they
are working on. Hopefully, the **Rubyists.EU** initiative will grow into
a living and breathing idea, which can precipitate the development of a
robust Ruby community in Europe.

The technical specification of the Rubyists.EU platform is essentially a
result of the perfect mix of several Open Source technologies. Before
elaborating on the whole constitution of this platform, it should be
pointed out that the testings are carried out by a combination of
[RSpec](http://rspec.info/) + [Cucumber](http://cukes.info/) to handle
both functional and integration tests. Due to the Web nature of the
project, both [Webrat](http://wiki.github.com/brynary/webrat) and
[Selenium](http://selenium.rubyforge.org/) are used in order to manage
simple Hypertext interactions and the significant amount of code written
in Javascript.

The Core of this platform is composed of
[Sinatra](http://www.sinatrarb.com/) +
[Rack](http://rack.rubyforge.org/). [Sinatra](http://www.sinatrarb.com/)
is a light-weight DSL used for quickly creating web applications in
Ruby. It keeps a minimal set of features for developers and it is an
excellent tool for creating small to mid-sized web applications. It is
based on [Rack](http://rack.rubyforge.org/), which as everyone probably
knows, is a Ruby library that provides an interface between web servers
supporting Ruby and Ruby web frameworks. Most of the underlying
infrastructure is handled by **Rack**.

The selected database is [PostgreSQL](http://www.postgresql.org/). This
Open Source ORDBMS (Object-Relational Database Management System) was
chosen because of its robustness, its features, and (mainly) because it
is the default database system supported by
[Heroku](http://www.heroku.com/).

The connection and the operations between the Sinatra-powered core and
the database are established by [DataMapper](http://datamapper.org/).
This is an object-relational mapping library for Ruby. **DataMapper**
has a number of excellent features. It is independent and it does not
tie in with any particular framework. It is designed to be fast and
efficient. One of its pros is that it often delays interaction with the
data store and it initiates it only when it is required.

The Rubyists.EU platform utilizes a user interface based on the [Google
Maps platform](http://code.google.com/apis/maps/). Google provides HTML
and Javascript APIs for their maps, which allow developers to easily
transform a simple map into an interactive application. In addition, the
[JQuery](http://jquery.com/) library is used in order to simplify and
simultaneously AJAXify the Javascript code on the client. The AJAX
functionality uses [JSON](http://json.org/) (JavaScript Object Notation)
to marshall objects for both synchronous and asynchronous transport. The
Google Maps standard UI is embedded in the generated HTML structure,
defined and generated by [HAML](http://haml-lang.com/). **HAML** is both
a simple markup language for templating HTML on a web page and a
compiler of HAML-to-HTML and vice-versa. Following the same principle,
the [SASS](http://sass-lang.com/) defines and generates the CSS
representation of the website. The main purpose of developing the
front-end this way is to secure the unobstructed separation of the HTML
structure, the CSS representation, and the Javascript functionality.

As a direct consequence of the **Sinatra** core, this platform already
provides a RESTful API that allows our platform to interact with any
existent client or system. This would allow both developers and
communities to integrate its functionality to their own websites,
projects, applications, etc.

Last, but not least, this framework is deployed in **Heroku**. For those
who still have no clue about this service, it is a Ruby-specific
cloud-computing platform that provides specialized Ruby hosting services
for developers. It allows developers to almost instantly deploy web
applications on the Internet. Heroku supports Rack-based web
applications so deploying the code on Heroku is a piece of cake. While
this service charges for hosting, it also provides a free basic tier
account. It should be remarked that this platform requires the intensive
use of [Git](http://git-scm.com/), a powerful decentralized SCM (Source
Control Management) system, in order to deploy applications.

Currently the Rubyists.EU platform is isolated from the rest of the
available systems out there but soon, it will be integrated with the
existing communications platforms such as
[Twitter](http://twitter.com/), [Facebook](http://www.facebook.com/),
[LinkedIn](http://www.linkedin.com/), [Freenode](http://freenode.net/),
[Google Groups](http://groups.google.com/), [Google
Wave](http://wave.google.com/), and [Github](http://github.com/) in
order to facilitate and ensure the transparent communications among
Rubyists in Europe.

This project is being built on tests. Whenever a functionality has to be
written or existing Ruby libraries have to be inserted into the code,
the BDD (Behavior Driven Development) approach is used to specify how
the piece of code should work in the platform. For those of you who are
still unfamiliar with the BBD, it is an approach that emphasizes on the
domain language of the problem and the interactions occurring in the
Software Development process. It implies outside-in development: it
starts with the either the definition of a class, a module or a user
interface and it ends with the creation of a functional piece of code.
Therefore, you have to design scenarios for the functionalities or
features you want to develop and then, you simply have to follow the BDD
process.

When a scenario is defined, the developer should write the tests and
then write the necessary code to make sure that the code passes the
tests. Then, the developer should focus on refactoring this code while
verifying it still passes the written tests. Once you are done, you can
move on to the next feature and so on. These scenarios guide developers
throughout the entire development process. They force people to focus on
writing down the tests and the required application code, and only then
are developers allowed to move on to the next step. Developers are
satisfied every time they pass a step successfully because they know for
sure, which of the features they have been developed function properly.

Since the Rubyists.EU is an initiative designed for the whole European
Ruby/Rails community, everybody is welcome to join in and even
collaborate with ideas, suggestions, comments, constructive criticism
and code. Developers can get involved by following the [Github
account](http://github.com/rock-n-code/rubyists.eu) and even forking the
source code. Some of the members of the Dutch
[Amsterdam.rb](http://amsterdam-rb.org/), the Belgium
[BRUG](http://wiki.rubyist.be/wiki/show/HomePage), the Greek
[Rubyst.es](http://rubyst.es/), and the Estonian
[Ruby.ee](http://www.ruby.ee/) have already volunteered to collaborate
on this project.

Rubyists can get in touch and make comments, suggestions for new
features or propositions to improve the existing ones by subscribing to
the [mailing list](http://groups.google.com/group/rubyists-eu). In
addition, hackers can follow the
[@rubyists\_eu](http://twitter.com/rubyists_eu) on Twitter, join the
[Rubyists.EU Facebook
page](http://www.facebook.com/pages/Europe/RubyistsEU/188196555796), and
the [Rubyists.EU group on
LinkedIn](http://http://www.linkedin.com/groups?gid=2400973).
Furthermore, developers and enthusiasts can also chat with other
Rubyists on the IRC channel on Freenode:
[#rubyists.eu](irc://irc.freenode.net/rubyists.eu) or exchange
enlightening information on the public [Google Wave
channel](https://wave.google.com/wave/?pli=1#restored:wave:googlewave.com!w%252Ba39S3saqF).

After all, the Rubyists.EU endeavor is a joint adventure that can become
as exciting as hackers and communities in Europe want it to be.
Hopefully, in the long run, this initiative could help eliminate the
obstacles that prevent the smooth adoption of the Ruby language as a
whole, and it would contribute to the development of a robust Ruby/Rails
community in Europe.

