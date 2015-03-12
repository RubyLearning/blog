---
Hide OgTags:
- 0
Hide SexyBookmarks:
- 0
author: Evan Light
categories:
- Beginners
- Ruby
date: 2011-11-30
layout: post
permalink: /2011/11/30/do-you-ponder-what-to-name-things-in-your-code/
tags:
- code
- programming
- ruby programming
thesis_description:
- Do you ponder what to name things in your code? A guest post on RubyLearning by
  Evan Light.
thesis_keywords:
- Programming,Ruby programming,code,TDD,BDD,naming
title: Do you ponder what to name things in your code?
topsy_short_url:
- http://bit.ly/vy1E0m
---

<div>
  <p class="update">
    This guest post is by <strong><a href="https://twitter.com/#!/elight">Evan Light</a></strong> a test-obsessed developer, the author of several rarely used gems, and the curator of Ruby DCamp. When he&#8217;s not a talking head at conferences, he&#8217;s usually working at home as a freelance developer remotely mentoring a developer, working for one or more startups, playing with open source, keeping his wife and four cats company, hacking nonsensically, talking at people on the internet, and/or attempting to lose weight (or any combination of the above). What else do you do when you live 3 hours from civilization?
  </p>
  
  <h2 id="why-should-i-care">
    Why should I care?
  </h2>
  
  <p class="block">
    <img class="alignright" src="http://www.gravatar.com/avatar/3c51f636715fb42bc82141702aa92b09?s=125" alt="Evan Light" /> &#8220;The hell with clean code!<sup class='footnote'><a href='#fn-6401-1' id='fnref-6401-1'>1</a></sup>, you say. &#8220;I&#8217;ve got stuff to get done!&#8221; You beat on keys for a while. Characters appear. The characters don’t make a lot of sense but, hey, the compiler compiles it or the virtual machine interprets it. Things happen. Eventually, an application emerges.
  </p>
  
  <p>
    Success? Hell no!
  </p>
  
  <p>
    Most of the time, someone has to maintain that pile of crap you just birthed! It may be someone else. It may be you! But it&#8217;s always wise to pretend that the person who will own your code next is an axe-wielding lunatic who knows where you live.
  </p>
  
  <p>
    The worst sin that I&#8217;ve seen people make in their code: choosing poor names&#8230; for their classes, methods, literals, you name it.
  </p>
  
  <p>
    &#8220;I don&#8217;t have time to sit around thinking about the perfect name for a class! Besides, I know how the code works! I can fix it.&#8221;
  </p>
  
  <p>
    Oh, yeah? You may now. But how about in a month? Or three? Or a year? Wait&#8230; will you even be working for this company or on this project in a year? Who inherits this code?
  </p>
  
  <h2 id="prototypes-spikes-and-other-rationalizations">
    Prototypes, spikes, and other rationalizations
  </h2>
  
  <p>
    Occasionally, developers invoke the &#8220;p&#8221; word: prototype. Prototypes are ugly little creatures that live only a short while.
  </p>
  
  <p>
    At least that&#8217;s the myth.
  </p>
  
  <p>
    The truth of the matter is that prototypes don&#8217;t exist. Prototypes don&#8217;t get thrown away. What happens when you show a manager working code? He says, &#8220;Great! Here&#8217;s your next feature!&#8221;
  </p>
  
  <p>
    &#8220;But&#8230;&#8221;, you start to say.
  </p>
  
  <p>
    &#8220;But what? It&#8217;s working! Marvelous! Right, here you are. Next feature!&#8221;
  </p>
  
  <p>
    Heard of a &#8220;spike&#8221;? That&#8217;s basically a small prototype that you may not tell management about. You spend maybe 30 minutes working on one. The pain of throwing away the code is lessened. But even then it may offend your sensibilities. And that code is going to be ugly too.
  </p>
  
  <p>
    We tell ourselves that the code will be temporary. Most of the time, this just isn&#8217;t so. These techniques are rationalizations for writing ugly code that will likely outlive its intended lifespan.
  </p>
  
  <h2 id="think-about-the-future">
    Think about the future!
  </h2>
  
  <p>
    So don&#8217;t throw that code away! Don&#8217;t prototype. Don&#8217;t spike<sup class='footnote'><a href='#fn-6401-2' id='fnref-6401-2'>2</a></sup>.
  </p>
  
  <p>
    Dave Thomas sometimes describes writing an application as writing a Domain Specific Language. That is, creating an application is akin to developing a semantically meaningful API to describe an application&#8217;s behavior.
  </p>
  
  <p>
    Therefore, the smartest thing you can do, when starting a new application, is to cultivate an understanding of the overall problem the application is intended to solve.
  </p>
  
  <p>
    How can we do this? Personally, I favor contemporary Test Driven Development techniques:
  </p>
  
  <p>
    For a given feature:
  </p>
  
  <ol>
    <li>
      Describe, in English, what the feature is trying to accomplish
    </li>
    <li>
      Exercise the API that I wish I&#8217;d write as a test
    </li>
    <li>
      Make the test pass
    </li>
    <li>
      <strong>Compare 1 & 2</strong>
    </li>
    <li>
      Refactor
    </li>
  </ol>
  
  <p>
    For instance, consider this simplistic example:
  </p>
  
  <p>
  </p>
  
  <h2 id="names-should-match-intent">
    Names should match intent
  </h2>
  
  <p>
    The English uses the word &#8220;subscribe&#8221;. That&#8217;s the action that I want the user to perform. So I make it the method name because that&#8217;s what I want to tell the user to do. That&#8217;s the message that I want to send the user.
  </p>
  
  <p>
    Now what if I need an entity to representation that relationship between a User and a Plan?
  </p>
  
  <p>
    I&#8217;ve seen (and written) some egregiously bad code in situations like this. Once upon a time, my initial reaction would be to call such a thing a &#8220;UserPlan&#8221;.
  </p>
  
  <p>
    That&#8217;s just vile and disgusting. Sure, it conjoins the two entities but it does so like Siamese twins!
  </p>
  
  <p>
    The better answer should be in plain sight. I used the word &#8220;subscribe&#8221; in the description! Call that entity a &#8220;Subscription&#8221;!
  </p>
  
  <p>
    But maybe your description was
  </p>
  
  <p>
  </p>
  
  <p>
    That would probably cause me to write sample code
  </p>
  
  <p>
  </p>
  
  <p>
    It&#8217;s still valid though I did less to model the relationship between the User and the Plan because words matter and <strong>naming matters</strong>.
  </p>
  
  <h2 id="counter-example">
    Counter example
  </h2>
  
  <p>
    So what happens when we name things badly?
  </p>
  
  <p>
    Is &#8220;UserPlan&#8221; so bad? Perhaps not. But UserPlan only represents a relationship between two entities. Perhaps I need a greater monstrosity to make the point plain.
  </p>
  
  <p>
    So what is a SelfpropelledFourWheelGroundVehicle? It&#8217;s pretty plainly a Car/Automobile. But it&#8217;s a disgusting name. Yet these are the kinds of names that people frequently use in their code due to lack of effort!
  </p>
  
  <p>
    Or there&#8217;s the other direction: Haskell developers often like to abstract functions such that they have no clear applicability to a domain. That is, their functions will have semantically meaningless variables such as &#8220;x&#8221; and &#8220;xs&#8221;. I&#8217;m told this is because Haskell has its roots in Lambda Calculus. Be that as it may, mathematical variables have only place in code: in implementing a mathematical calculation!
  </p>
  
  <p>
    How would you feel maintaining code where the classes, literals, and methods read like that?!
  </p>
  
  <p>
    How productive would you be working in such code? If you cannot trust the names in a code base to accurately represent the ideas at work then you need to understand vast swaths of the code base to be the least bit productive!
  </p>
  
  <h2 id="conclusion">
    Conclusion
  </h2>
  
  <p>
    If you did not before, I hope that you now have a better appreciation why it is worth your time to get the names right in your code. It will make yours, your colleagues&#8217;, and any who later touch your code lives better and more productive.
  </p>
  
  <p>
    And if you don&#8217;t use good names, I have an axe and I know where you live.
  </p>
  
  <p>
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post.</em> Thanks!
  </p>
  
  <p class="update">
    Subscribe to the waiting list of the free, online &#8220;<a href="http://satishtalim.github.com/webruby/">Intermediate Ruby Course</a>&#8220;.
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>, <a href="http://technorati.com/tag/code" rel="tag">code</a>

<div class='footnotes'>
  <div class='footnotedivider'>
  </div>
  
  <ol>
    <li id='fn-6401-1'>
      Robert Martin also wrote about this topic, and, in part, inspired this diatribe with the first chapter of his book, Clean Code. <span class='footnotereverse'><a href='#fnref-6401-1'>&#8617;</a></span>
    </li>
    <li id='fn-6401-2'>
      Yes, this is a sweeping generalization. Yes, I occasionally spike on code. However, I only do this for technically challenging pieces which is to say very infrequently. And I throw my few spikes away. <span class='footnotereverse'><a href='#fnref-6401-2'>&#8617;</a></span>
    </li>
  </ol>
</div>
