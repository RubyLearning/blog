---
title: "Advice For Ruby Beginners 2"
author: Satish Talim
date: "2007-10-01"
layout: post
permalink: /2007/10/01/advice-for-ruby-beginners-2/
categories:
  - beginners
  - interview
  - popular
  - rails
  - ruby
  - training
---
This is part 2 in our [ongoing
conversation](http://rubylearning.com/blog/2007/09/27/advice-for-ruby-beginners-1/)
– “**Advice For Ruby Beginners**“.<!--more-->

* * * * *

**Satish\>\> What kind of mini-projects one should work on, to get a
good grasp on Ruby?**

**Agnieszka (Poland)\>\>** Something useful for you personally or
internally for your company, this way you’ll be very clear about initial
requirements. Two things to remember from the start are [“Keep It
Simple, Stupid”](http://en.wikipedia.org/wiki/KISS_principle) and [“You
Ain’t Gonna Need
It”](http://en.wikipedia.org/wiki/You_Ain't_Gonna_Need_It) – rereading
your code and looking for better solutions with those in mind will be
extremely didactic and rewarding.

**David (USA)\>\>** It’s hard to generalize, but it’s often a good idea
to isolate something fairly specific — say, DRb (distributed Ruby) or
the GDBM API — and write something small, even if it isn’t terribly
useful in the long term, to get practice. That’s how I learn, anyway. My
“hacking/” directory is full of small, working examples of things I
wanted to learn about.

**Fabio (Brazil)\>\>** In the open source community there’s that great
motto: “scratch your own itch”. I’d suggest the same thing. Just because
you saw the now famous blog screencast from David Hansson, you don’t
have to start with a blog. I won’t tell you what to do. You can’t learn
how to paint if you don’t know what you’d want to picture. You can’t be
a good chef if you don’t know what do you’d want to eat. Do something
for yourself. You don’t have a blog yet? Great, instead of signing up
for WordPress, create your own blog. You’d like an online portfolio for
your photographs? Good, instead of signing up for Flickr, create your
own online album. It doesn’t need to be as full featured. You need the
basics: do the basics. If it can’t fit in a week of spare time
development, it’s too much. You will learn fast if you have something
that you need and you develop it on your own. That’s the spirit of the
craftsmanship: once you start your own project, you will play the
several different roles: not only programming, but also design, systems
administration and so on. That makes you a more complete and competent
professional. Everything new you learn adds up to your craft.

**Jamie (UK)\>\>** Well that depends on the person learning it. I’ve
always found it best to learn whilst doing something productive, so if
you’re a sysadmin then learn how to automate some of your daily tasks,
or maybe you’re a web developer…so learn through Rails.

**Jamis (USA)\>\>** Anything. What do you need? What are you interested
in? My first real project in Ruby was a simple web server, and it turned
out to take only 400 lines of code or so.

**Jens (Switzerland)\>\>** Whatever interests you – small systems
utilities, games, tools you can use for your current projects. I bet you
have dozens of ideas of things to write. Pick on of them and get
started.

**Juanjo (Spain)\>\>** Whatever fits your needs. I think the important
thing with a project you are using to learn, is that it is useful for
some personal need, so you keep having fun and are also interested in
finishing it for its own sake, not just to learn a new language. A good
approach is to find a library you like and try to code as a mini-project
where you can use it.

**Julian (Netherlands)\>\>** Anything that suits your fancy, except a
GUI application. There is a big amount of flux in this area, and you
will be immediately burdened with choosing the right GUI toolkit, making
it run cross-platform etc. Anything else should work – text processing
and the web (using vanilla CGI), maintenance scripts, socket servers.
IRC bots. Whatever suits your fancy.

**Manik (India)\>\>** I think, one can start with any app for self use,
following the “scratch your own itch” notion of the open source
community. Any application that you need but is not there or can be
improved upon will be a good target. The key to mastery however is
persistence. Don’t just stop at the first usable version of the app. But
re-factor it and try to make it dynamic and extendable by others. That
is when a lot of learning happens.

**Matt (Australia)\>\>** I’m a re-implementationist. Write Ruby versions
of small programs you use regularly. For Unix/Linux people, that’s easy
— there’s a pile of small shell tools (grep, cat, sort, uniq, head,
tail, echo, even sed) that you know (or should know) how to use, and
that (in some cases) can be replaced with a single line (or a small
number of lines) of Ruby. Windows people are behind the 8-ball on this,
though, as GUI programming is orders of magnitude harder than console
programming, and while Rails lowers the barriers to entry, it still
involves understanding a lot more concepts than writing a replacement
for grep. Beyond that, solving problems that you come across on a
day-to-day basis is what keeps your skills sharp, and you should do it
as often as you can. Never do anything repetitive on the computer if you
can help it; while it might take you 10 minutes to do it by hand but an
hour or two to write a program to do it, you’ll be: a. giving yourself a
handy tool to use \*next\* time you need to do that repetitive task, and
b. exercising your programming skills.

**Mislav (Croatia)\>\>** I wrote a lot of “screen-scraping” scripts;
those are the ones that parse and extract data from web pages. I also
started with scripts that process other kinds of input: certain log
files or long lists of data that should be sanitized and imported into a
database. Soon I was able to write useful scripts to solve a particular
problem even quicker than actually searching if the problem was already
been solved or before even thinking to use another language or tool.
Then I started with easy Rails apps. The important thing is the
attitude: *have fun while doing it*; let the problems challenge you.

**Ola (Sweden)\>\>** Anything that is hard or awkward in other languages
usually make a good project for Ruby. This will allow you to go further
out and find all of the more interesting things that Ruby is capable of.
That said, most programmers have several manual processes in their daily
life. A typical mini project would be to implement a tool that helps you
with these daily tasks. Almost everything can be automated.

**Pedro (Portugal)\>\>** It’s always hard to reply to a question like
this one, each project is a project, has it’s own requirements and
constraints, Therefore I think you should leverage your projects
according to your skills, but other than that, any project is a learning
track. I specially recommend that people start with projects that they
need or that they really understand; its a safe path for motivation.

**Peter (UK)\>\>** If you’re interested in Rails, the best projects
would simply be Web sites and Web applications that you, yourself, need.
For example, my “Code Snippets” project was started simply because I
needed somewhere to store snippets of code. Within two years the site
grew to hundreds of thousands of page-views each month and I sold the
site to DZone.com. If you’re more interested in focusing on Ruby for the
time being, then it’s worth focusing on projects that will give you the
opportunity to try out lots of different aspects of Ruby’s core
libraries. It’s amazing how many long-time Ruby developers, including
myself, don’t realize when something we need is in the core library.
Work your way through random classes and modules in the core library,
becoming familiar with how to use new methods and techniques, and work
your way up to more fully-featured programs over time. irb is great for
this sort of experimentation.

**Remco (Netherlands)\>\>** Ruby is great for doing administrative
things on your computer; find files, rename them according to their
content, comparing directories. I have a bunch of scripts to do tasks
like this. There even is a cool gem to organize script like that as rake
tasks called sake. I like to speedup my work by making small Ruby DSLs
(Domain Specific Languages) to make tedious jobs more manageable. For
instance: last week I made a module to make creating S5 presentations
easier. The module is just 20 lines of code but makes writing
presentations a lot easier. Find an excuse to write Ruby code, there are
plenty of opportunity!

**Sau (Singapore)\>\>** Any project is a good project as long as
youâ€™re interested in making it work. Even if it doesnâ€™t work out
right in the end, itâ€™s the journey, not the goal, that will make it
worthwhile.

**Satish\>\> What’s the Ruby / Rails scene in your country?**

**Agnieszka (Poland)\>\>** We have at least two Polish hosting companies
that offer Ruby and Rails support. There are several software houses,
startups and also freelancers. Ruby is present at international
conferences held in Poland, there are a number of local ruby communities
and the Polish [Ruby](http://www.ruby-lang.org/pl) and [Ruby on
Rails](http://www.rubyonrails.pl) sites. Ruby books are published in
Polish, and it is also taught at some academic institutions.

**Fabio (Brazil)\>\>** Brazil is not a place known for much
technological breakthroughs. There are some, but limited. We are always
playing catch up with the rest of the world. This is kind of a bad
thing. I evaluate our local Ruby on Rails environment as being similar
with the USA scenario of late 2004 or 2005. We are around 2 years behind
them. There’s only 2 or 3 books written and published here. There’s
dozens in the USA. We have maybe half a dozens small companies betting
on Rails, while there are already hundreds in the USA. Their conferences
gather hundreds of people all over the year. We are still struggling to
have a small one here. So, this is not a very friendly environment and
anyone that wants to play with Rails here will find a blank canvas. This
is bad for anyone that wants the traditional corporate ‘career’ but
maybe a good window of opportunity for entrepreneurs. Some people
started their own businesses around Ruby and Rails and are doing fairly
well. Some people are teaching, which is also good because they are
graduating the next generation. This is a very fertile soil that needs
more seeds. We do what we like to do, not what we are told to do, and
that’s important. It’s not only about the ideology of going against the
status quo, it’s about being pragmatic and do what matters to you. It’s
about gathering around smart people, about improving your own skills.
The Ruby community here has these conditions. Evans Data recently ran a
world-wide poll and measured that Ruby/Rails interest is rising fast in
Brazil, so programmers already know what ‘Ruby’ stands for and lots of
them are interested to see what’s behind it. They predict that until
next year Brazil will be only behind China around the emergent
countries, interest-wise. Big companies don’t have interest in Ruby or
Rails here. There are always exceptions, but the majority don’t. They
want to protect their old investments in old technologies, the old
contracts and negotiations, and they just won’t switch. They are for
sale to the highest bidder and Rails is not backed by any company. So
there’s no big campaigns, no aggressive marketing. That’s how the market
has always worked here and Rails is not reason enough to change that.
Not just yet.

**Jamie (UK)\>\>** Ruby/Rails is a popular tool in the UK and it
continues to expand every day, it’s not going to dwindle in popularity
any time soon, that’s for sure.

**Jamis (USA)\>\>** I’m in the USA, and Ruby (particularly Rails) is
taking the industry by storm. Adoption continues to balloon. It’s a
great time to be learning Ruby and Rails.

**Jens (Switzerland)\>\>** There’s a small but growing community that
meets regularly – [Swiss Ruby User Group](http://www.swissrug.ch/) and
[Ruby on Rails Switzerland User Group](http://www.rubyonrails.ch/).
There’s a lot of projects around and all I know are swamped with work.
Most customers don’t care about the technology used, but about the
results – and that we can deliver.

**Juanjo (Spain)\>\>** Ruby/Rails is getting popular in Spain. It is
used in some of the more popular Spanish webs and there are a couple of
companies using only Rails for all their projects. There are also a good
number of freelancers, so we have a nice small growing community with
even a big event every year in the Spanish Rails Conference.

**Julian (Netherlands)\>\>** Depends on the country, really. In Russia,
where I come from, Ruby is a \_superminority\_ language – you gotta be a
real freak to try to find a job doing Ruby. There’s a couple of
translated books out, and there are a few companies doing Rails jobs,
but don’t expect anything stellar (or fast) in the market if you go
looking for a job. Ruby generalists are not welcome, but if you can
wield the Rail you stand a chance (at least in the capital). There is
some progress on the outsourcing scene – but it works only if you accept
outsourcing as a practice. A major roadblock are people using Windows
for development (you have to be ready to accept it’s shortcomings when
you go doing code, and they aren’t). But ultimately if you are good in
what you do and you got a year – two years of experience under your belt
[the]([http://novemberain.com/](http://novemberain.com/))
[right]([http://getalime.ru/](http://getalime.ru/))
[people]([http://www.rubybrothers.ru/](http://www.rubybrothers.ru/))
will find their ways to you. Here in the Netherlands is much better,
with a few companies that do Ruby and Rails with class. There’s
[Fingertips](http://www.fngtps.com/), there’s
[Holder](http://www.holder.nl/) – and they are good folks. The
experience of working together with Fingertips was nothing but stellar,
for instance. I’d say that you can find a job doing Rails/Ruby full time
here and not be held back by the public attitude, there are companies
that need you and you’ll find your way when your time has come. We don’t
have a RUG as such, but we do have “Coffee meetings” where anyone might
just drop along and chitchat about his latest Ruby musings with others.
I never attended because they always schedule it for 9 in the morning,
I’m mostly nocturnal and never get there. But you should (if you are in
the premises, that is). Granted, still not the level of the US but you
have the Internet for that. The only thing I miss is a hardcore group in
the style of
[Seattle.rb](http://www.zenspider.com/Languages/Ruby/Seattle/index.html),
I think.

**Manik (India)\>\>** One thing for which I am extremely happy is that
Rails has encouraged developers to come out of these big organizations
or code factories and startup on their own. There are a lot of startups
in India doing Rails work today. Though we have always had excellent
developers in India, but most of them were working for the larger
companies. Most of these developers actually never contributed to Open
Source as it was something that wasn’t encouraged by these big
companies. As a result India was always more popular as an outsourcing
destination, pitching more on cost arbitrage rather than technical
proficiency of the developers. Rails has given developers a chance to
come out of that “outsourcing and cheap resource” branding and assert
their identity as good developers. We see a lot more people contributing
to Open Source projects from India now. Rails has given them much more
visibility as well. Financially also, good Rails developers are doing
well. And there is a strong and growing demand for more developers. To
give an idea of the demand, we at VinSol have been receiving Rails
training requests at such a consistent rate that we have setup a
dedicated training page on our website. We recently did a corporate
training in Bangalore, and we have companies from Chandigarh, Hyderabad
and even Colombo in the pipeline.

**Matt (Australia)\>\>** Ruby’s gaining in popularity as a scripting and
“glue” language for systems admins, taking up much the same niche as
Perl, as well as really taking off with Rails. There’s no shortage of
Rails work out there if you want it, too.

**Mislav (Croatia)\>\>**Nil. There is interest because of the hype, but
I only know several people that actually continued to use it in the work
place. I haven’t met all of them personally (although I would like to!),
but I’m still unable to count even 10 people that are working with Rails
professionally in Croatia. Rails is not a young technology, but
companies here aren’t exactly agile. Even if you find a company where
you will be allowed to use the tools of your choice, there is low chance
that your co-workers will agree. I’ve worked at 2 companies where, over
the course of months, my co-workers still weren’t able to understand
anything I wrote. Learning a new technology that has the potential of
replacing the things you used in the past isn’t something that will
happen by destiny or chance; you have to be willing to take the plunge.

**Ola (Sweden)\>\>** This is actually kind of hard for me to tell, since
I don’t live in Sweden anymore. Ruby and Rails is definitely gaining
traction, but it’s going quite slow. Uptake in the US have in the
general been much quicker than in Europe and Sweden is no exception. Of
course, there are some companies and individuals in all major cities
doing Ruby work and from what I’ve seen it’s growing very quickly. There
is lots of interest and several courses about Ruby have been held so I
think the situation will soon change.

**Pedro (Portugal)\>\>** Ruby, especially because of RubyOnRails is just
starting in Portugal. The market and projects have been primarily
dominated by Perl and PHP on the internet project levels, and Java and
other “heavy” languages for the business oriented development.

**Peter (UK)\>\>** Here in the UK there are a couple of Ruby user
groups, the most notable being the [London Ruby Users
Group](http://lrug.org/). Generally, however, I am not involved with any
local Ruby or Rails efforts, as when you’re online the whole world is
accessible to you. Blogs, mailing lists, and IRC channels mean that you
don’t need to do things locally, although there are clearly a lot of
people interested in that side of things.

**Remco (Netherlands)\>\>** The Dutch Ruby scene is very loosely
coupled. The only two reoccurring get-togethers I know of are the
Morning Coffee Meetings in Amsterdam initiated by the guys at Fingertips
and the yearly RubyEnRails conference.

**Sau (Singapore)\>\>** Ruby is very little known in Singapore outside
of Ruby on Rails. Ruby on Rails in Singapore is a fledgling, fringe
technology that is gaining tremendous traction in recent months. The
[Singapore Ruby Brigade](http://groups.google.com/group/singapore-rb) is
the main Ruby user group in Singapore and has been around for about 1.5
years. Itâ€™s a very informal group of people, with a core of 10 – 20
people but an extended group of maybe up to 150 people. We meet every
last Thursday of the month, usually at a venue sponsored by the local
library, where we come together to talk and just get to know other
Rubyists. With the recent
[code::XtremeApps](http://www.itsc.org.sg/prevEvent.do?eventKey=9)
24-hour programming competition, there has been an increase in the
awareness of Rails amongst the software industry in Singapore as well as
the undergraduate community.

* * * * *

[Advice For Ruby Beginners
1](http://rubylearning.com/blog/2007/09/27/advice-for-ruby-beginners-1/)

**[Advice For Ruby Beginners
3](http://rubylearning.com/blog/2007/10/04/advice-for-ruby-beginners-3/)**

Technorati Tags: [Advice For Ruby
Beginners](http://technorati.com/tag/Advice+For+Ruby+Beginners), [Ruby
Beginners](http://technorati.com/tag/Ruby+Beginners), [Ruby
Interviews](http://technorati.com/tag/Ruby+Interviews), [Ruby Serial
Interview](http://technorati.com/tag/Ruby+Serial+Interview)
