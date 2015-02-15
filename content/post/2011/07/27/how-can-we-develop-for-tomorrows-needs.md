---
title: "How Can We Develop For Tomorrow's Needs?"
author: James Schorr
date: 2011-07-27
layout: post
permalink: /2011/07/27/how-can-we-develop-for-tomorrows-needs/
thesis_description:
  - "James M. Schorr gives real-world tips on how to develop and cater to tomorrow's needs.."
thesis_keywords:
  - Programming, James M. Schorr
topsy_short_url:
  - 
categories:
  - Beginners
  - Ruby
  - Ruby Masters
tags:
  - James M. Schorr
  - programming
---
<div>
  <h3>
    How Can We Develop For Tomorrow&#8217;s Needs?
  </h3>
  
  <p class="update">
    This guest post is by <strong>James Schorr</strong>, who has been developing software since 1999. He is the owner of an IT consulting company, <a href="https://enspirenconsulting.com">Enspiren IT Consulting, LLC</a>.  He lives with his lovely wife, Tara, and their children in Kansas City, Missouri. James spends a lot of time writing code in many languages, doing IT security audits, and has a passion for Ruby on Rails in particular. He also loves spending time with his family, playing chess, going to the shooting range, hiking, fishing, and investing. His professional profile is on <a href="http://www.linkedin.com/in/jamesschorr">LinkedIn</a>.
  </p>
  
  <p class="block">
    <img class="alignright" alt="James M. Schorr" src="http://rubylearning.com/images/James_Schorr.png" width="125" height="125" /> <span class="drop_cap">T</span>he average developer is often forced to get code out the door as quickly as possible, primarily due to unrealistic deadlines and budgets. As a result, the quality and future expandability of software is greatly harmed. Software is now used in medical machinery, our vehicles, power plants, stock markets, aircraft, weapons, etc&#8230; As software becomes more and more critical in our lives, the need to think long-term is becoming increasingly critical.
  </p>
  
  <p>
    Obviously, the quickest way is almost always not the best way. I hope to give some practical steps to those involved in software development that will help in the development of stable, long-lasting software. A proper strategy session involving the below steps can help save a lot of wasted time and money.
  </p>
  
  <p>
    Quality, future-resilient software is tough to define, but reveals itself when it does what it’s supposed to without unpleasant surprises, handles unpredictable user input and system issues in gracious, non-devastating ways, and, in general, makes the user’s life easier. The tough part is that user’s needs and systems change. How do we engineer for tomorrow’s needs?
  </p>
  
  <p>
    The keys to successfully developing long-term software are:
  </p>
  
  <p>
    <strong>Establishing the Purpose</strong>: What is the point of the software? Do the needs that it are anticipated to be met look as though they will be the same core needs in the foreseeable future? In other words, will the main needs be met by this software and can we easily build out from there? If not, we need to keep the anticipated future needs in mind as we &#8220;scope&#8221; out the architecture of the project and provide &#8220;space&#8221; for them.
  </p>
  
  <p>
    <strong>Choosing the &#8220;Stack&#8221;</strong>: (what technologies, languages, etc&#8230; will be used). The stack should be chosen carefully, based upon:
  </p>
  
  <ul>
    <li>
      <strong>proven stability</strong>. For example, it may be &#8220;cool&#8221; but unwise to write the software in the latest-and-greatest language. I&#8217;ve seen instances where a language/framework is chosen strictly due to its current popularity. This is typically a recipe for disaster, as those who go (and enjoy) that route typically move on to the next greatest thing, leaving code behind for non-fad-following developers to handle.
    </li>
    <li>
      <strong>current in-house knowledge</strong>. For instance, maybe our developers love and know Ruby, should we really force them to write an app in VB? Or perhaps it is a Microsoft-shop, are time and funds available to facilitate the learning-on-the-fly of non-MS technologies? I don’t believe that it is ever appropriate to write mission critical software using a language/framework that is unfamiliar to the developers. There are times, however, where the software is so mission-critical and matches a language’s abilities to the point where it makes sense to pull in new talent. It can be argued that software can be written in almost any language, that the language itself doesn’t matter much. But sometimes it really does, both in terms of expressiveness and developer satisfaction (note: I still contend that a happy developer is a good developer, or at least becoming one).
    </li>
    <li>
      <strong>infrastructure requirements</strong>. Do we have the hardware and network necessary to <em>decently</em> support the software and its anticipated usage? Disk space, memory requirements, OS, network speed, etc&#8230; All of these matter, a lot. It&#8217;s best to always plan for 2-3x the anticipated usage. For instance, for a web app, if we anticipate 1k users, let&#8217;s build for 2-3k users, with built-in monitoring of the resources being used and a plan of how to scale up quickly when we hit a &#8220;soft&#8221; threshold.
    </li>
  </ul>
  
  <p>
    <strong>Planning</strong>:
  </p>
  
  <ul>
    <li>
      <strong>Architectural Drawing</strong>: I&#8217;m a big fan of having at least the &#8220;skeleton&#8221; of the project drawn out, particularly on a white-board (I’m a bit old-school, I know). It doesn&#8217;t have to be a fancy diagram or complicated UML diagram, just a simple drawing; the more understandable, the better. This high-level overview provides guidance when we&#8217;re deep into code, as we can look up and see if we’re on track (as it&#8217;s all too easy to go down a code &#8220;rabbit trail&#8221; if we&#8217;re not careful). It is counterproductive, however, to draw out every little detail, as this will stifle creativity and overwhelm us while we’re writing code (we just won’t look at the diagram then).
    </li>
    <li>
      <strong>Establish Deadlines</strong>: we do need to know the deadlines. It&#8217;s best, in my opinion, to have several small deadlines with a semi-flexible final deadline. This helps us keep on track and measure our progress little by little. As we hit the small deadlines, our confidence builds, which then improves our productivity and, in general, our code quality.
    </li>
    <li>
      <strong>Using Available Expertise Wisely</strong>: does it make sense to assign Bob, the awesome Python programmer, to doing CSS and Bill, the great designer, to slinging code? Obviously not (I have seen some managers try this, though), we may lose both team members or end up with Google copy-and-paste code and animated GIFs in our Project. Cross-training is a nice and potentially valuable concept, but it should be done outside of a software project with its accompanying deadlines. Future minor features might provide a better opportunity ground for cross-training. If Bob&#8217;s swamped, maybe we need to find him some decent help. <img src="http://rubylearning.com/blog/wp-includes/images/smilies/icon_smile.gif" alt=":)" class="wp-smiley" />
    </li>
    <li>
      <strong>Determine the Deployment Strategy</strong>(for both during and after the Project): <ul>
        <li>
          code should be checked into our version control system prior to any deployments.
        </li>
        <li>
          maybe we should only deploy code after business hours after alerting such-and-such a group. If our project has any possibility of negatively impacting others, notification is not only kind, but often necessary, especially for large changes.
        </li>
        <li>
          a rollback strategy must <em>always</em> be in place. This strategy must be easily understandable with simple steps, so that little, if any interpretation by support staff, needs to be done in the &#8220;heat of the moment&#8221; support calls. Even if our developers are top-notch, until code gets into Production, we <em>cannot</em> be 100% sure that it will not need to be rolled back. This is why major companies often have to release an update quickly after a major release. Some things just can&#8217;t be easily discovered until they’re released into &#8220;the wild&#8221;.
        </li>
      </ul>
    </li>
  </ul>
  
  <p>
    <strong>Building with Expansion in Mind</strong>:
  </p>
  
  <ul>
    <li>
      One of the wonderful aspects of developing software is also its most dangerous aspect: flexibility. A feature or component can often be written in different ways. There typically are only one or two best ways, though. It can be very difficult to determine, unless one steps back from the project and thinks it through. Well-known software principles help a great deal with this, but come up short if they are not &#8220;placed up against&#8221; the anticipated needs of the future (in other words, if we don&#8217;t understand where we&#8217;re going, our code will still be awful even if we follow DRY, OOP, GOF, etc&#8230;). As much as possible, this needs to be done not by the developer but by someone outside the code, so to speak, perhaps a technical team lead, etc&#8230;
    </li>
    <li>
      When adding core features, we need to at least take a few moments to think through possible future implications of what we’re doing. For example, our Component A is currently parsing JSON from website B using C credentials. Component D depends upon Component A’s data. Wouldn&#8217;t it make sense to have these in an encrypted setting field somewhere to make it easy to change in the future? If Component A&#8217;s data was slightly different, would Component B &#8220;blow up&#8221;? Maybe we can abstract all of this a bit?
    </li>
    <li>
      Avoiding Spaghetti-Code: proper design and a commitment to sticking to the design in the future helps to prevent our code from such entanglement. In other words, we need to commit to never, ever quickly throwing code in to the project, as this leads to &#8220;spaghetti-code&#8221;. Of course, there may be the exceedingly rare occasions, where we may need to do such a stop-gap measure due to an emergency, but we must then learn from our mistake and commit to re-engineering that portion of the code properly.
    </li>
  </ul>
  
  <p>
    <strong>Data Safety</strong>:
  </p>
  
  <ul>
    <li>
      As we depend more and more upon data, it&#8217;s becoming increasingly important that we do our best to have automated backups, which are then checked frequently by a <em>person</em>. This cannot be emphasized heavily enough. All too often, properly designed backups can stop working without anyone noticing until it is too late.
    </li>
    <li>
      If encryption is used: <ul>
        <li>
          the encryption keys need to be stored off-site in at least 2 secure places. Imagine if we lost our server(s), our office burned down, our VPS provider goes offline, etc&#8230;- even if we had backups, could we get to the raw data if needed? No one wants to start over from scratch.
        </li>
        <li>
          Does the encryption depend upon a certain cipher? If so, what is the game plan for when that cipher is cracked someday? How easy will it be for us to move to a new cipher?
        </li>
      </ul>
    </li>
    
    <li>
      Does our data depend upon a specific version? For instance, maybe database X version Y can open the data but no other versions can. Do we have a backup of that version to access the data if needed? Better yet, this reveals a key flaw in our design. Our data should not be heavily dependent upon any software version.
    </li>
    <li>
      Would our data be understandable if a new developer 10 years from now is assigned to work with it? For instance, if a column for a user’s API Key is called usrscr_ak12, we may understand it, but it&#8217;s not future-proof (a better term may be &#8220;future-resilient&#8221;, since nothing is truly future-proof). Such obfuscation attempts provide little security, as if someone can get that far (to the data), we&#8217;ve lost the security &#8220;battle&#8221; anyhow. Data should be clearly understood by those who can access it.
    </li>
    <li>
      Can our data be exported easily when the software that we&#8217;re lovingly developing now someday gets decommissioned? All software will eventually get replaced by something better. How easily can our data be decoupled from our application?
    </li>
  </ul>
  
  <p>
    <strong>Pin-pointing Possible &#8220;Dominoes&#8221;</strong> in our project and code-base (e.g. if A happens, does it affect B, which then affects C, etc&#8230;, these can be like dominoes). Amazon&#8217;s recent AWS issues in 2011 revealed the criticality of this step. The more time that we spend anticipating what can go wrong, the more we can establish quick steps to both prevent such issues and to mitigate possible damage. At the bare minimum, the possible &#8220;dominoes&#8221; and recommended quick steps need to be written down somewhere. This can greatly help to expedite future troubleshooting.
  </p>
  
  <ul>
    <li>
      <strong>Our Software</strong>: We must try to anticipate, as much as possible, what the interdependencies are in our project and its surrounding infrastructure. These dependencies should be in written form and re-reviewed as further functionality is added to the software in the future (e.g. ITIL Change Management).
    </li>
    <li>
      <strong>Dependent Software</strong>: What software or systems will depend upon our software? When our system goes down, will other software be slamming our system asking for a response?
    </li>
    <li>
      <strong>Dependent Systems</strong>: if we saturate our network, is our software designed to &#8220;back-off&#8221; and retry after an appropriate, randomized delay?
    </li>
  </ul>
  
  <p>
    Obviously, none of the above can be done overnight. If even some of the above is done, however, the chance of our software having a longer-lasting, positive impact will be greater. I recommend that the start of each project have at least a 3-5 days dedicated to going through these steps. Gathering input from the teams of people who are responsible for various components (e.g. clients/end users, network, sysadmins, developers of other dependent software, etc&#8230;) will be invaluable. The payoff will be great.
  </p>
  
  <p class="update">
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post.</em> Also, do check out James&#8217; other article: &#8220;<a href="http://rubylearning.com/blog/2010/10/18/do-you-enjoy-your-code-quality/">Do You Enjoy Your Code Quality?</a>&#8221; on RubyLearning. Thanks!
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/James+M.+Schorr" rel="tag"> James M. Schorr</a>
