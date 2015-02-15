---
title: Advice For Ruby Beginners 2
author: Satish Talim
date: 2007-10-01
layout: post
permalink: /2007/10/01/advice-for-ruby-beginners-2/
categories:
  - Beginners
  - Interview
  - Popular
  - Rails
  - Ruby
  - Training
---
<div>
  <p>
    This is part 2 in our <a href="http://rubylearning.com/blog/2007/09/27/advice-for-ruby-beginners-1/">ongoing conversation</a> &#8211; &#8220;<strong>Advice For Ruby Beginners</strong>&#8220;.
  </p>
  
  <hr align="center" width="70%" />
  
  <p>
    <strong><span style="color:#0060C0;">Satish>> What kind of mini-projects one should work on, to get a good grasp on Ruby?</span></strong>
  </p>
  
  <p class="block">
    <strong>Agnieszka (Poland)>></strong> Something useful for you personally or internally for your company, this way you&#8217;ll be very clear about initial requirements. Two things to remember from the start are <a href="http://en.wikipedia.org/wiki/KISS_principle">&#8220;Keep It Simple, Stupid&#8221;</a> and <a href="http://en.wikipedia.org/wiki/You_Ain't_Gonna_Need_It">&#8220;You Ain&#8217;t Gonna Need It&#8221;</a> &#8211; rereading your code and looking for better solutions with those in mind will be extremely didactic and rewarding.
  </p>
  
  <p class="block">
    <strong>David (USA)>></strong> It&#8217;s hard to generalize, but it&#8217;s often a good idea to isolate something fairly specific &#8212; say, DRb (distributed Ruby) or the GDBM API &#8212; and write something small, even if it isn&#8217;t terribly useful in the long term, to get practice. That&#8217;s how I learn, anyway. My &#8220;hacking/&#8221; directory is full of small, working examples of things I wanted to learn about.
  </p>
  
  <p class="block">
    <strong>Fabio (Brazil)>></strong> In the open source community there&#8217;s that great motto: &#8220;scratch your own itch&#8221;. I&#8217;d suggest the same thing. Just because you saw the now famous blog screencast from David Hansson, you don&#8217;t have to start with a blog. I won&#8217;t tell you what to do. You can&#8217;t learn how to paint if you don&#8217;t know what you&#8217;d want to picture. You can&#8217;t be a good chef if you don&#8217;t know what do you&#8217;d want to eat. Do something for yourself. You don&#8217;t have a blog yet? Great, instead of signing up for WordPress, create your own blog. You&#8217;d like an online portfolio for your photographs? Good, instead of signing up for Flickr, create your own online album. It doesn&#8217;t need to be as full featured. You need the basics: do the basics. If it can&#8217;t fit in a week of spare time development, it&#8217;s too much. You will learn fast if you have something that you need and you develop it on your own. That&#8217;s the spirit of the craftsmanship: once you start your own project, you will play the several different roles: not only programming, but also design, systems administration and so on. That makes you a more complete and competent professional. Everything new you learn adds up to your craft.
  </p>
  
  <p class="block">
    <strong>Jamie (UK)>></strong> Well that depends on the person learning it. I&#8217;ve always found it best to learn whilst doing something productive, so if you&#8217;re a sysadmin then learn how to automate some of your daily tasks, or maybe you&#8217;re a web developer&#8230;so learn through Rails.
  </p>
  
  <p class="block">
    <strong>Jamis (USA)>></strong> Anything. What do you need? What are you interested in? My first real project in Ruby was a simple web server, and it turned out to take only 400 lines of code or so.
  </p>
  
  <p class="block">
    <strong>Jens (Switzerland)>></strong> Whatever interests you &#8211; small systems utilities, games, tools you can use for your current projects. I bet you have dozens of ideas of things to write. Pick on of them and get started.
  </p>
  
  <p class="block">
    <strong>Juanjo (Spain)>></strong> Whatever fits your needs. I think the important thing with a project you are using to learn, is that it is useful for some personal need, so you keep having fun and are also interested in finishing it for its own sake, not just to learn a new language. A good approach is to find a library you like and try to code as a mini-project where you can use it.
  </p>
  
  <p class="block">
    <strong>Julian (Netherlands)>></strong> Anything that suits your fancy, except a GUI application. There is a big amount of flux in this area, and you will be immediately burdened with choosing the right GUI toolkit, making it run cross-platform etc. Anything else should work &#8211; text processing and the web (using vanilla CGI), maintenance scripts, socket servers. IRC bots. Whatever suits your fancy.
  </p>
  
  <p class="block">
    <strong>Manik (India)>></strong> I think, one can start with any app for self use, following the &#8220;scratch your own itch&#8221; notion of the open source community. Any application that you need but is not there or can be improved upon will be a good target. The key to mastery however is persistence. Don&#8217;t just stop at the first usable version of the app. But re-factor it and try to make it dynamic and extendable by others. That is when a lot of learning happens.
  </p>
  
  <p class="block">
    <strong>Matt (Australia)>></strong> I&#8217;m a re-implementationist. Write Ruby versions of small programs you use regularly. For Unix/Linux people, that&#8217;s easy &#8212; there&#8217;s a pile of small shell tools (grep, cat, sort, uniq, head, tail, echo, even sed) that you know (or should know) how to use, and that (in some cases) can be replaced with a single line (or a small number of lines) of Ruby. Windows people are behind the 8-ball on this, though, as GUI programming is orders of magnitude harder than console programming, and while Rails lowers the barriers to entry, it still involves understanding a lot more concepts than writing a replacement for grep. Beyond that, solving problems that you come across on a day-to-day basis is what keeps your skills sharp, and you should do it as often as you can. Never do anything repetitive on the computer if you can help it; while it might take you 10 minutes to do it by hand but an hour or two to write a program to do it, you&#8217;ll be: a. giving yourself a handy tool to use *next* time you need to do that repetitive task, and b. exercising your programming skills.
  </p>
  
  <p class="block">
    <strong>Mislav (Croatia)>></strong> I wrote a lot of &#8220;screen-scraping&#8221; scripts; those are the ones that parse and extract data from web pages. I also started with scripts that process other kinds of input: certain log files or long lists of data that should be sanitized and imported into a database. Soon I was able to write useful scripts to solve a particular problem even quicker than actually searching if the problem was already been solved or before even thinking to use another language or tool. Then I started with easy Rails apps. The important thing is the attitude: <em>have fun while doing it</em>; let the problems challenge you.
  </p>
  
  <p class="block">
    <strong>Ola (Sweden)>></strong> Anything that is hard or awkward in other languages usually make a good project for Ruby. This will allow you to go further out and find all of the more interesting things that Ruby is capable of. That said, most programmers have several manual processes in their daily life. A typical mini project would be to implement a tool that helps you with these daily tasks. Almost everything can be automated.
  </p>
  
  <p class="block">
    <strong>Pedro (Portugal)>></strong> It&#8217;s always hard to reply to a question like this one, each project is a project, has it&#8217;s own requirements and constraints, Therefore I think you should leverage your projects according to your skills, but other than that, any project is a learning track. I specially recommend that people start with projects that they need or that they really understand; its a safe path for motivation.
  </p>
  
  <p class="block">
    <strong>Peter (UK)>></strong> If you&#8217;re interested in Rails, the best projects would simply be Web sites and Web applications that you, yourself, need. For example, my &#8220;Code Snippets&#8221; project was started simply because I needed somewhere to store snippets of code. Within two years the site grew to hundreds of thousands of page-views each month and I sold the site to DZone.com. If you&#8217;re more interested in focusing on Ruby for the time being, then it&#8217;s worth focusing on projects that will give you the opportunity to try out lots of different aspects of Ruby&#8217;s core libraries. It&#8217;s amazing how many long-time Ruby developers, including myself, don&#8217;t realize when something we need is in the core library. Work your way through random classes and modules in the core library, becoming familiar with how to use new methods and techniques, and work your way up to more fully-featured programs over time. irb is great for this sort of experimentation.
  </p>
  
  <p class="block">
    <strong>Remco (Netherlands)>></strong> Ruby is great for doing administrative things on your computer; find files, rename them according to their content, comparing directories. I have a bunch of scripts to do tasks like this. There even is a cool gem to organize script like that as rake tasks called sake. I like to speedup my work by making small Ruby DSLs (Domain Specific Languages) to make tedious jobs more manageable. For instance: last week I made a module to make creating S5 presentations easier. The module is just 20 lines of code but makes writing presentations a lot easier. Find an excuse to write Ruby code, there are plenty of opportunity!
  </p>
  
  <p class="block">
    <strong>Sau (Singapore)>></strong> Any project is a good project as long as youâ€™re interested in making it work. Even if it doesnâ€™t work out right in the end, itâ€™s the journey, not the goal, that will make it worthwhile.
  </p>
  
  <p>
    <strong><span style="color:#0060C0;">Satish>> What&#8217;s the Ruby / Rails scene in your country?</span></strong>
  </p>
  
  <p class="block">
    <strong>Agnieszka (Poland)>></strong> We have at least two Polish hosting companies that offer Ruby and Rails support. There are several software houses, startups and also freelancers. Ruby is present at international conferences held in Poland, there are a number of local ruby communities and the Polish <a href="http://www.ruby-lang.org/pl">Ruby</a> and <a href="http://www.rubyonrails.pl">Ruby on Rails </a> sites. Ruby books are published in Polish, and it is also taught at some academic institutions.
  </p>
  
  <p class="block">
    <strong>Fabio (Brazil)>></strong> Brazil is not a place known for much technological breakthroughs. There are some, but limited. We are always playing catch up with the rest of the world. This is kind of a bad thing. I evaluate our local Ruby on Rails environment as being similar with the USA scenario of late 2004 or 2005. We are around 2 years behind them. There&#8217;s only 2 or 3 books written and published here. There&#8217;s dozens in the USA. We have maybe half a dozens small companies betting on Rails, while there are already hundreds in the USA. Their conferences gather hundreds of people all over the year. We are still struggling to have a small one here. So, this is not a very friendly environment and anyone that wants to play with Rails here will find a blank canvas. This is bad for anyone that wants the traditional corporate &#8216;career&#8217; but maybe a good window of opportunity for entrepreneurs. Some people started their own businesses around Ruby and Rails and are doing fairly well. Some people are teaching, which is also good because they are graduating the next generation. This is a very fertile soil that needs more seeds. We do what we like to do, not what we are told to do, and that&#8217;s important. It&#8217;s not only about the ideology of going against the status quo, it&#8217;s about being pragmatic and do what matters to you. It&#8217;s about gathering around smart people, about improving your own skills. The Ruby community here has these conditions. Evans Data recently ran a world-wide poll and measured that Ruby/Rails interest is rising fast in Brazil, so programmers already know what &#8216;Ruby&#8217; stands for and lots of them are interested to see what&#8217;s behind it. They predict that until next year Brazil will be only behind China around the emergent countries, interest-wise. Big companies don&#8217;t have interest in Ruby or Rails here. There are always exceptions, but the majority don&#8217;t. They want to protect their old investments in old technologies, the old contracts and negotiations, and they just won&#8217;t switch. They are for sale to the highest bidder and Rails is not backed by any company. So there&#8217;s no big campaigns, no aggressive marketing. That&#8217;s how the market has always worked here and Rails is not reason enough to change that. Not just yet.
  </p>
  
  <p class="block">
    <strong>Jamie (UK)>></strong> Ruby/Rails is a popular tool in the UK and it continues to expand every day, it&#8217;s not going to dwindle in popularity any time soon, that&#8217;s for sure.
  </p>
  
  <p class="block">
    <strong>Jamis (USA)>></strong> I&#8217;m in the USA, and Ruby (particularly Rails) is taking the industry by storm. Adoption continues to balloon. It&#8217;s a great time to be learning Ruby and Rails.
  </p>
  
  <p class="block">
    <strong>Jens (Switzerland)>></strong> There&#8217;s a small but growing community that meets regularly &#8211; <a href="http://www.swissrug.ch/">Swiss Ruby User Group</a> and <a href="http://www.rubyonrails.ch/">Ruby on Rails Switzerland User Group</a>. There&#8217;s a lot of projects around and all I know are swamped with work. Most customers don&#8217;t care about the technology used, but about the results &#8211; and that we can deliver.
  </p>
  
  <p class="block">
    <strong>Juanjo (Spain)>></strong> Ruby/Rails is getting popular in Spain. It is used in some of the more popular Spanish webs and there are a couple of companies using only Rails for all their projects. There are also a good number of freelancers, so we have a nice small growing community with even a big event every year in the Spanish Rails Conference.
  </p>
  
  <p class="block">
    <strong>Julian (Netherlands)>></strong> Depends on the country, really. In Russia, where I come from, Ruby is a _superminority_ language &#8211; you gotta be a real freak to try to find a job doing Ruby. There&#8217;s a couple of translated books out, and there are a few companies doing Rails jobs, but don&#8217;t expect anything stellar (or fast) in the market if you go looking for a job. Ruby generalists are not welcome, but if you can wield the Rail you stand a chance (at least in the capital). There is some progress on the outsourcing scene &#8211; but it works only if you accept outsourcing as a practice. A major roadblock are people using Windows for development (you have to be ready to accept it&#8217;s shortcomings when you go doing code, and they aren&#8217;t). But ultimately if you are good in what you do and you got a year &#8211; two years of experience under your belt [the](<a href="http://novemberain.com/">http://novemberain.com/</a>) [right](<a href="http://getalime.ru/">http://getalime.ru/</a>) [people](<a href="http://www.rubybrothers.ru/">http://www.rubybrothers.ru/</a>) will find their ways to you. Here in the Netherlands is much better, with a few companies that do Ruby and Rails with class. There&#8217;s <a href="http://www.fngtps.com/">Fingertips</a>, there&#8217;s <a href="http://www.holder.nl/">Holder</a> &#8211; and they are good folks. The experience of working together with Fingertips was nothing but stellar, for instance. I&#8217;d say that you can find a job doing Rails/Ruby full time here and not be held back by the public attitude, there are companies that need you and you&#8217;ll find your way when your time has come. We don&#8217;t have a RUG as such, but we do have &#8220;Coffee meetings&#8221; where anyone might just drop along and chitchat about his latest Ruby musings with others. I never attended because they always schedule it for 9 in the morning, I&#8217;m mostly nocturnal and never get there. But you should (if you are in the premises, that is). Granted, still not the level of the US but you have the Internet for that. The only thing I miss is a hardcore group in the style of <a href="http://www.zenspider.com/Languages/Ruby/Seattle/index.html">Seattle.rb</a>, I think.
  </p>
  
  <p class="block">
    <strong>Manik (India)>></strong> One thing for which I am extremely happy is that Rails has encouraged developers to come out of these big organizations or code factories and startup on their own. There are a lot of startups in India doing Rails work today. Though we have always had excellent developers in India, but most of them were working for the larger companies. Most of these developers actually never contributed to Open Source as it was something that wasn&#8217;t encouraged by these big companies. As a result India was always more popular as an outsourcing destination, pitching more on cost arbitrage rather than technical proficiency of the developers. Rails has given developers a chance to come out of that &#8220;outsourcing and cheap resource&#8221; branding and assert their identity as good developers. We see a lot more people contributing to Open Source projects from India now. Rails has given them much more visibility as well. Financially also, good Rails developers are doing well. And there is a strong and growing demand for more developers. To give an idea of the demand, we at VinSol have been receiving Rails training requests at such a consistent rate that we have setup a dedicated training page on our website. We recently did a corporate training in Bangalore, and we have companies from Chandigarh, Hyderabad and even Colombo in the pipeline.
  </p>
  
  <p class="block">
    <strong>Matt (Australia)>></strong> Ruby&#8217;s gaining in popularity as a scripting and &#8220;glue&#8221; language for systems admins, taking up much the same niche as Perl, as well as really taking off with Rails. There&#8217;s no shortage of Rails work out there if you want it, too.
  </p>
  
  <p class="block">
    <strong>Mislav (Croatia)>></strong>Nil. There is interest because of the hype, but I only know several people that actually continued to use it in the work place. I haven&#8217;t met all of them personally (although I would like to!), but I&#8217;m still unable to count even 10 people that are working with Rails professionally in Croatia. Rails is not a young technology, but companies here aren&#8217;t exactly agile. Even if you find a company where you will be allowed to use the tools of your choice, there is low chance that your co-workers will agree. I&#8217;ve worked at 2 companies where, over the course of months, my co-workers still weren&#8217;t able to understand anything I wrote. Learning a new technology that has the potential of replacing the things you used in the past isn&#8217;t something that will happen by destiny or chance; you have to be willing to take the plunge.
  </p>
  
  <p class="block">
    <strong>Ola (Sweden)>></strong> This is actually kind of hard for me to tell, since I don&#8217;t live in Sweden anymore. Ruby and Rails is definitely gaining traction, but it&#8217;s going quite slow. Uptake in the US have in the general been much quicker than in Europe and Sweden is no exception. Of course, there are some companies and individuals in all major cities doing Ruby work and from what I&#8217;ve seen it&#8217;s growing very quickly. There is lots of interest and several courses about Ruby have been held so I think the situation will soon change.
  </p>
  
  <p class="block">
    <strong>Pedro (Portugal)>></strong> Ruby, especially because of RubyOnRails is just starting in Portugal. The market and projects have been primarily dominated by Perl and PHP on the internet project levels, and Java and other &#8220;heavy&#8221; languages for the business oriented development.
  </p>
  
  <p class="block">
    <strong>Peter (UK)>></strong> Here in the UK there are a couple of Ruby user groups, the most notable being the <a href="http://lrug.org/">London Ruby Users Group</a>. Generally, however, I am not involved with any local Ruby or Rails efforts, as when you&#8217;re online the whole world is accessible to you. Blogs, mailing lists, and IRC channels mean that you don&#8217;t need to do things locally, although there are clearly a lot of people interested in that side of things.
  </p>
  
  <p class="block">
    <strong>Remco (Netherlands)>></strong> The Dutch Ruby scene is very loosely coupled. The only two reoccurring get-togethers I know of are the Morning Coffee Meetings in Amsterdam initiated by the guys at Fingertips and the yearly RubyEnRails conference.
  </p>
  
  <p class="block">
    <strong>Sau (Singapore)>></strong> Ruby is very little known in Singapore outside of Ruby on Rails. Ruby on Rails in Singapore is a fledgling, fringe technology that is gaining tremendous traction in recent months. The <a href="http://groups.google.com/group/singapore-rb">Singapore Ruby Brigade</a> is the main Ruby user group in Singapore and has been around for about 1.5 years. Itâ€™s a very informal group of people, with a core of 10 &#8211; 20 people but an extended group of maybe up to 150 people. We meet every last Thursday of the month, usually at a venue sponsored by the local library, where we come together to talk and just get to know other Rubyists. With the recent <a href="http://www.itsc.org.sg/prevEvent.do?eventKey=9">code::XtremeApps</a> 24-hour programming competition, there has been an increase in the awareness of Rails amongst the software industry in Singapore as well as the undergraduate community.
  </p>
  
  <hr align="center" width="70%" />
  
  <p>
    <a href="http://rubylearning.com/blog/2007/09/27/advice-for-ruby-beginners-1/">Advice For Ruby Beginners 1</a>
  </p>
  
  <p>
    <strong><a href="http://rubylearning.com/blog/2007/10/04/advice-for-ruby-beginners-3/">Advice For Ruby Beginners 3</a></strong>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Advice+For+Ruby+Beginners" rel="tag">Advice For Ruby Beginners</a>, <a href="http://technorati.com/tag/Ruby+Beginners" rel="tag">Ruby Beginners</a>, <a href="http://technorati.com/tag/Ruby+Interviews" rel="tag">Ruby Interviews</a>, <a href="http://technorati.com/tag/Ruby+Serial+Interview" rel="tag">Ruby Serial Interview</a>
