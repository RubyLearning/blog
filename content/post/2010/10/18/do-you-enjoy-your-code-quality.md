---
title: Do You Enjoy Your Code Quality?
author: James Schorr
date: 2010-10-18
layout: post
permalink: /2010/10/18/do-you-enjoy-your-code-quality/
thesis_description:
  - James M. Schorr gives real-world tips on how to enjoy crafting software by improving the quality of your code and your development habits.
thesis_keywords:
  - Programming, James M. Schorr, Code Quality
topsy_short_url:
  - 
categories:
  - Beginners
  - Popular
  - Ruby
  - Ruby Masters
tags:
  - Code Quality
  - James M. Schorr
  - programming
---
<div>
  <h3>
    Do You Enjoy Your Code Quaility?
  </h3>
  
  <p class="update">
    This guest post is by <strong>James Schorr</strong>, who has been developing software since 1999. He is the owner of an IT consulting company, <a href="https://enspirenconsulting.com">Enspiren IT Consulting, LLC</a>.  He lives with his lovely wife, Tara, and their children in Kansas City, Missouri. James spends a lot of time writing code in many languages, doing IT security audits, and has a passion for Ruby on Rails in particular. He also loves spending time with his family, playing chess, going to the shooting range, hiking, fishing, and investing. His professional profile is on <a href="http://www.linkedin.com/in/jamesschorr">LinkedIn</a>.
  </p>
  
  <p class="block">
    <img class="alignright" alt="James M. Schorr" src="http://rubylearning.com/images/James_Schorr.png" width="125" height="125" /> <span class="drop_cap">T</span>here&#8217;s something innately satisfying about programming; or, at least, there should be. It&#8217;s a creative act in and of itself that has incredible power and potential to affect change. Craftsmanship, in and of itself, typically attracts those who like to think outside the box and those who like to create. In this way, it really is more of an art than anything else and can produce a great deal of satisfaction and delight.
  </p>
  
  <p>
    Compare the carpenter that hand-crafts a beautiful cabinet to a factory worker who pushes buttons to cause a machine to form identical cabinets over and over again. While both can experience a measure of satisfaction in their work, only the carpenter enjoys long-term satisfaction. The goal of this article is to enable you to improve code quality and, thus, transform the mundane into the beautiful. No matter where you&#8217;re at on the spectrum, beginner to advanced, there is always room for improvement. As the code quality improves, your ability to delight in it and enjoy what you&#8217;re doing does as well.
  </p>
  
  <p>
    I have a number of applications in Production and have learned a lot over the years about the code quality, systems, and programming in general. I&#8217;ve also been regularly called on to carefully check a tremendous amount of others&#8217; source code in my consulting business and earlier jobs. Here are some practical, real-world ways to improve your code quality and development habits in general. I have learned the hard way on a few of these. Some may only apply to the non-employee developer, but almost all are pretty universal:
  </p>
  
  <h3>
    Pre-Development
  </h3>
  
  <ul>
    <li>
      Gather the requirements and &#8220;stories&#8221; from the client. I like the idea of stories better because it&#8217;s more in line with how the non-developer thinks. In other words, &#8220;I want A to happen as a B when I do C&#8221;. Make sure that those you’re meeting with are told to come prepared with as much information as possible, especially from the end users of the planned application.
    </li>
    <li>
      Question every need and distill them down by asking &#8220;Why?&#8221; In general, the requirements of users are based on what they know the possibilities are and what they&#8217;ve used before. You, however, may quickly see that a need is better met a different way, or even cause issues if fulfilled.
    </li>
    <li>
      Clarify what is necessary and &#8220;nice-to-have&#8221;, as this has a direct impact on the timeline and budget.
    </li>
    <li>
      Refuse to reproduce lousy software. In other words, turn down work, if necessary, that will need you to reproduce some other system that wasn&#8217;t designed well unless you&#8217;re given the freedom to do it right. It&#8217;s just not worth it, both for you or the users. How do you recognize lousy software? Look at the UI, speed, security, and stability; would you want to use it?
    </li>
    <li>
      Reject unrealistic timelines nicely, &#8220;Yes, I could do this in 3 months, but you won&#8217;t get the quality that you deserve. To do this right, we need 5 months.&#8221; Stick to your deadlines if possible. Ask yourself, &#8220;Do I want to work 17-20 hours a day to hit an unrealistic deadline?&#8221; Been there, done that, lesson learned.
    </li>
    <li>
      Accept the least amount of features for functionality for the first version. It&#8217;s far more important to have a stable foundation than a ton of features. Slate other features for future releases after the foundation is laid properly. You can expect future needs (and should), but only include the minimums for the first version or iteration.
    </li>
    <li>
      Realize that just because we &#8220;can&#8221; doesn&#8217;t mean that we &#8220;should&#8221;. Anything&#8217;s possible, but not everything&#8217;s advisable. This is a tough one, especially in the pre-development excitement, brainstorming phase. For instance, yes we could pull in a Google map for every row, but should we? How long will the requests take as the data set size increases?
    </li>
    <li>
      If you don&#8217;t know the answer to &#8220;Why&#8221; for a feature and &#8220;What&#8221; it will impact, don&#8217;t even start answering &#8220;How&#8221;.
    </li>
    <li>
      Ensure that you&#8217;re using a great version control system (I&#8217;m partial to GIT) and a hosted code repository if necessary. Backups are essential as well.
    </li>
    <li>
      Block off large amounts of undivided time to work on the project. For instance, it&#8217;s not a good day to write code if you have to leave every few minutes.
    </li>
  </ul>
  
  <h3>
    Development
  </h3>
  
  <ul>
    <li>
      Spend as much time as possible understanding the real-world and data needs of the client before writing <em>any</em> code. This is absolutely <em>critical</em> to make sure that your application is designed from the ground as a stable, relevant application. Don&#8217;t move forward until you think that you have a pretty good grasp of the needs; get help if you need to.
    </li>
    <li>
      Out-engineer user-error as much as possible. In other words, never trust that the user will do what you expect, especially when entering data. For instance, about 4 years ago, I was reviewing a proposed payroll-entry system software for a Fortune-500 company. The software trusted the user to enter the number of their dependents properly for tax deduction purposes. When I questioned the developer, &#8220;What if someone enters a negative number?&#8221;, his face grew pale. We found that an employee would end up with a raise, instead of a deduction! Ouch.
    </li>
    <li>
      Don&#8217;t reinvent the wheel. For instance, it makes no sense to develop your own login system for Ruby on Rails when there are great ones already out there that have run through a gauntlet in the real-world.
    </li>
    <li>
      Don&#8217;t implement <em>anything</em> unless you understand, as much as time allows, what you&#8217;re &#8220;plugging in&#8221;. Read the issues reported, read through the source code, and familiarize yourself with how it works. Don&#8217;t choose something merely because 3 people recommended it in some forum. I&#8217;ve seen this often: a developer quickly slaps in a 3rd party open source app or gem and a few months later, there&#8217;s an issue that they do not know how to resolve. Usually it&#8217;s because they thought they&#8217;d found a quick fix, without thinking about any future issues. Perhaps the worst example that I&#8217;ve seen is hot-linking to Javascript code on a website somewhere, in blind trust that the link will stay live.
    </li>
    <li>
      Be open to including other languages and technologies where appropriate. For instance, just because your app is written in Ruby, if a Perl or Python is better suited for a certain backend feature, it may be good to use it. Even if you don&#8217;t integrate it, reading through it can help you see a better way to solve an issue at hand.
    </li>
    <li>
      Don&#8217;t do in code what your database can already do, as this will cut down the speed quite a bit. For instance, why use <tt>Date</tt> in Ruby in a SQL query on a MySQL-backed application when MySQL&#8217;s <tt>CURRENT_DATE()</tt> will work fine (and faster)? In other words, know the capabilities of the technologies that you&#8217;re using.
    </li>
    <li>
      Avoid including &#8220;experimental&#8221; or &#8220;cutting-edge&#8221; features in your project if possible. While fun, the risk of issues just isn&#8217;t worth it unless your project is just a learning exercise.
    </li>
    <li>
      Communicate what you need to keep the client in the loop. That being said, too much communication about every little snag and solution will only frustrate them.
    </li>
  </ul>
  
  <h3>
    Post-Development
  </h3>
  
  <ul>
    <li>
      Review your code for speed, stability, security, and usability.
    </li>
    <li>
      Have someone else review it or discuss it with them.
    </li>
    <li>
      Have non-technical people do real-world testing on your product. You&#8217;d be surprised at how many things you think are intuitive and easy that really aren&#8217;t to an average user.
    </li>
    <li>
      Never, ever, ever stop learning, even if it&#8217;s unrelated to your current development language of choice.
    </li>
    <li>
      Don&#8217;t be afraid to ask for help. Even the best developers can gain a lot of insight and knowledge from reading others&#8217; code and interacting with others.
    </li>
    <li>
      Revisit old code and see what you would&#8217;ve done differently. Often, you&#8217;ll find yourself encouraged as you see how better your code is now than then.
    </li>
  </ul>
  
  <h3>
    Enjoying Your Development:
  </h3>
  
  <ul>
    <li>
      How do you work best? In quiet, with music, with lots of lighting, dim lighting, etc&#8230;? A happy developer is much more likely to produce quality. Spend some time setting up your work environment the way that you&#8217;re most comfortable with. It&#8217;s amazing how mood-based programming can be. Improve your mood and you&#8217;ll improve your code.
    </li>
    <li>
      What tool(s) do you like to use? As much as possible, insist on those tools, &#8220;Yes, I can write this app in TextEdit or Notepad, but I can do it better with this $79 tool X.&#8221;
    </li>
    <li>
      Give yourself time to think and rest. There are some days where I just can&#8217;t write code well; other days where it’s just flowing. This is due to how your brain functions. You need sleep and a change of pace and scenery now and then. Schedule breaks if you must and realize that some days are going to be tough. On tough days, learn something new.
    </li>
    <li>
      Walk away for a while. It&#8217;s easy to get &#8220;tunnel vision&#8221; and think that you&#8217;re close to solving a problem and to think that more effort will solve it. While true at times, I find that it&#8217;s best to walk away from the issue at hand for a while and do something completely different. For example, I tried once for 7 hours to power-through a complicated area of code and just couldn&#8217;t get it right. I finally stopped working on code that day, came back the next day to it, and solved it in 16 minutes. You would be surprised at the ideas or solutions that will spring into your mind as you are thinking about or doing other things.
    </li>
    <li>
      Set realistic deadlines. For instance, before telling your client or boss that this will be done next Friday, add a week. You never know what issues you might hit and will find yourself, more often than not, very grateful for the extra time to get it done right. If you end early, you&#8217;re a hero!
    </li>
    <li>
      Remember, you&#8217;re a person, not a robot. In other words, you deserve time to eat, sleep, get away, etc&#8230; When necessary, remind others nicely.
    </li>
    <li>
      Know your limits and enforce them. In other words, &#8220;No, I can&#8217;t and won&#8217;t recreate Gmail.&#8221;
    </li>
  </ul>
  
  <p>
    As the work quality improves, it will stand out and you will be called upon more and more to help others, do other projects, etc&#8230; As your level of expertise grows, help others by tactfully pointing out improvements, respecting them, and encouraging them. In doing so, you will find yourself enjoying the quality of your work.
  </p>
  
  <p>
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/James+M.+Schorr" rel="tag"> James M. Schorr</a>, <a href="http://technorati.com/tag/Code+Quality" rel="tag"> Code Quality</a>
