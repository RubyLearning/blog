---
draft: false
title: Why don't you use and review these useful Ruby Gems?
date: 2011-07-25
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: https://www.facebook.com/rubylearning
categories:
- beginners
- ruby
layout: post
permalink: /2011/07/25/why-dont-you-use-and-review-these-useful-ruby-gems/
tags:
- programming
- ruby
- ruby gems
- rubyists
---
## Showcasing some Ruby Gems from developers like you and me

Why don’t you try out some of the Ruby Gems mentioned below, built by
developers like you and me, and review them? Maybe there are some real
‘hidden’ gems out there, wanting to be exposed!

**[ascii-data-tools](https://github.com/benilovj/ascii-data-tools)**
developed by [Jake Benilov](http://twitter.com/#!/benilov). In his own
words – “It provides a suite of tools for identifying, reading,
enriching and editing ASCII data records. Such records are commonly used
for data transfer within the banking (e.g. transfer statements between
banks) and telecommunications sectors (e.g. call detail records).”

The subject matter may be quite dry, but for me this gem has been a
training dojo of sorts and hence may be of interest to you. I’ve tried
to do several things with the development of the code:

-   I’ve polished the code (some parts several times) in order to learn
    how to follow Uncle Bob’s clean code concepts and good OO principles
    (“tell, don’t ask”, etc)
-   I’ve developed it using acceptance-test driven (with cucumber) and
    test-driven (with rspec). I’ve tried to apply [Specification by
    Example](http://specificationbyexample.com/key_ideas.html) ideas to
    push the tests to the status of living documentation.
-   I’ve tried to utilize Rubyisms (lots of composition with mixins,
    some meta-programming, internal DSLs) to maximise code clarity,
    simplicity, extensibility and testability.

**[constructable](https://github.com/mkorfmann/constructable)**
developed by [Manuel Korfmann](http://twitter.com/#!/mkorfmann). In his
own words – “constructable is a macro, kinda similar in spirit to
`attr_reader` and `attr_accessor`, that makes the `new` method accept a
hash, kinda like the way ‘create’ does on ActiveRecord models.”

**[copyrb](https://github.com/milandobrota/copyrb)** developed by [Milan
Dobrota](http://milandobrota.com/). In his own words – “I have written a
quick gem that allows you to copy and paste Ruby objects across
terminals. This gem was created primarily to simplify the process of
copying objects between different Rails environments for people who
spend a lot of time in the Rails console. For [more
details](http://rubylove.info/post/3409677596/copyrb-gem-for-copying-and-pasting-ruby-objects).”

**[document\_mapper](https://github.com/ralph/document_mapper)**
developed by [Ralph von der Heyden](http://twitter.com/#!/ralph). In his
own words – “A simple model layer that let’s you query text documents as
if they were a database.”

**[green\_shoes](https://github.com/ashbb/green_shoes)** developed by
[Satoshi Asakawa](http://twitter.com/#!/ashbb). In his own words –
“green\_shoes is a Ruby domain specific language for beautiful Desktop
Applications. The green\_shoes dsl is so simple, even your pointy haired
boss can understand it. The green\_shoes project is based on
\_why-the-lucky-stiff’s Shoes, except for the following:

-   green\_shoes source code is all Ruby, so even you can contribute.
-   green\_shoes takes the Ruby DSL block-style approach, so all you
    have to do is write what you know: Ruby.
-   green\_shoes is a gem, so you can simply install with this command:
    **gem install green\_shoes**“

**[guard-rails-assets](https://github.com/dnagir/guard-rails-assets)**
developed by [Dmytrii
Nagirniak](https://plus.google.com/116807208912177719748/). In his own
words – “Automatically compile Rails 3.1 assets when files are modified.
You can use it to automatically run the JavaScript tests and always have
the files ready for it. It uses guard gem and Rails 3.1 built-in assets
pipeline. Works great in combination with
guard-jasmine-headless-webkit.”

**[ip-world-map](https://github.com/darxriggs/ip-world-map)** developed
by [Rene Scheibe](https://plus.google.com/102020526201098205404). In his
own words – “ip-world-map can be used to visualize web access logfiles
(Apache format) on a world map. It performs geo-location resolution on
the IPs and can generate fixed images, animated images or even videos.”

**[jsdebug-rails](https://github.com/jeremygpeterson/jsdebug-rails)**
developed by [Jeremy
Peterson](https://plus.google.com/u/0/111499813995138329804/). In his
own words – “On June 16, 2011, Ruby Rogues described using `puts` as the
best way to debug Ruby code, in same way, I wanted a way to log
JavaScript debug statements in Firebug’s console. The main purpose of
jsdebug-rails is to provide console wrapper for debug statements in
JavaScript code during development, thus including the file name, line
number, and comment/object. Once in production, all debug statements are
removed from the JavaScript source code, so they are never processed and
much smaller.”

**[methodfinder](https://github.com/citizen428/methodfinder)** developed
by [Michael Kohl](https://plus.google.com/u/0/101046237539584353961/).
In his own words – “This isn’t the first Ruby port of Smalltalk’s Method
Finder, but I couldn’t find the old one and so decided to write one
myself for the benefit of the
[RubyLearning.org](http://RubyLearning.org/) students. After being
mentioned on the Ruby5 podcast, the project really caught on and I got
some very good feedback as well as feature suggestions and patches. The
main purpose of the library is helping new Rubyists find methods they
didn’t know about. There are various usage examples in the README.”

**[omelettes](https://github.com/marksim/omelettes)** developed by [Mark
Simoneau](http://twitter.com/#!/marksim). In his own words – “omelettes
is a low-to-no configuration database obfuscation gem for ActiveRecord
that allows you to remove sensitive data from the database and replace
it with meaningless words that are the same length. It also integrates
with Faker automatically and allows for full configuration in a single
file.”

**[rails-web-console](https://github.com/rosenfeld/rails-web-console)**
developed by [Rodrigo Rosenfeld
Rosas](https://plus.google.com/u/1/112046748094887665556/). In his own
words – “Some time ago I was planning to write an article comparing
Rails and Grails and while trying to figure out what I did find useful
in Grails that was missing in Rails, the only think I could think of was
the console plugin for Grails. So, I decided to write one for Rails,
which took only about an hour… It is just an interface for running Ruby
commands in the context of a controller of the application. Think of it
as the Rails console on the web, although with no auto-complete (yet). I
was planning to add auto-complete, syntax highlight and other features,
but couldn’t find any free time for doing that. There’s already some
auto-complete examples in Github using websockets as well as Javascript
code highlighters for Ruby available on the Internet. It is just a
matter of getting some free time…
![:)](http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif)
Since, I prefer the new Hash declaring syntax, this gem is not
compatible with Ruby 1.8, but there’s a fork of it just for allowing its
usage in Ruby 1.8 (replacing the new Hash declaration style with the old
one).”

**[secretsharing](http://git.alech.de/?p=secretsharing.git)** developed
by [Alexander Klink](http://twitter.com/#!/alech). In his own words –
“It is not on GitHub, but I’m hosting the git repository myself.
Cryptographic secret sharing is one of the lesser known cryptographic
techniques. I’ve implemented the most prominent version, which was
invented by Adi Shamir (the »S« in RSA) and can be used to share a
secret (such as a password) between a number of people (let’s call that
n) and only recover it if a certain number (k \<= n) come together and
combine their secret shares. Interestingly enough, if less than k people
combine their shares, they learn nothing at all (in an
information-theoretic understanding of »nothing«).”

**[sequel-jdbc-hxtt-adapter](https://github.com/colincasey/sequel-jdbc-hxtt-adapter)**
developed by [Colin
Casey](https://plus.google.com/103966022068171083922/). In his own words
– “I had to do a lot of work with MS Access databases at my previous job
and I found that the options for interacting with these databases
programatically on the Windows platform left a lot to be desired. JRuby
was beginning to make Ruby development on Windows a lot less painful so,
using that interpreter and a pure JDBC driver, I created a Sequel
adapter for working with MS Access files.”

**[SGFParser](https://github.com/Trevoke/SGFParser)** developed by
[Aldric Giacomoni](http://gplus.to/trevoke). In his own words –
“SgfParser allows you to parse, create and save SGF files. SGF (Smart
Game Format) is a plain text format used to record moves in various
board games, most famously Go/Weiqi/Baduk but also Chess and Backgammon.
When I started this project, there was only one available, and it was a
relatively tricky-to-find Ruby file online; no gems. This one aims to be
the fastest (currently parses a 1.2 Mb SGF in \~3 seconds) and
eventually also keep track of all the potential parsing or format errors
that may have occurred without dying.”

**[standalone-migrations](https://github.com/thuss/standalone-migrations)**
developed by [Todd Huss](http://twobitlabs.com/). In his own words –
“standalone-migrations allows you to easily use Rails migrations in
non-Rails and non-Ruby projects. My company, Two Bit Labs, develops iOS
and Android apps for companies looking to go mobile and we usually use
Rails on the server side. However, some of our clients use other server
side platforms and we noticed that often our non-Rails clients struggled
to effectively version and manage their database schema. So in 2008 we
created standalone-migrations so non-Rails shops can enjoy all the
database migration goodness that Rails offers. It’s been great to see
standalone-migrations grow over the years with an active community!”

**[xapian\_db](https://rubygems.org/gems/xapian_db)** developed by
[Gernot Kogler](mailto:gernot@kogler-informatik.ch). In his own words –
“xapian\_db is a Ruby gem that combines features of nosql databases and
fulltext indexing. It is based on Xapian, an efficient and powerful
indexing library.”

I’ll be updating this page from time to time. *If you have written a
Ruby Gem and want to showcase it here, please email me at **satish [dot]
talim [at] gmail.com**. If you know of some real useful, ‘hidden’ Ruby
Gems, please let us know by commenting on this blog post*. Thank you for
your time and help.
