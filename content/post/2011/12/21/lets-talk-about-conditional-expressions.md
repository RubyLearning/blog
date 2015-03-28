---
draft: false
title: Let's Talk About Conditional Expressions
date: 2011-12-21
author: Evan Light
categories:
- Beginners
- Ruby
layout: post
permalink: /2011/12/21/lets-talk-about-conditional-expressions/
social_broadcasted:
- a:0:{}
social_notify:
- 0
tags:
- Conditional Expressions
- programming
- ruby programming
topsy_short_url:
- null
---

<div>
  <p class="update">
    This guest post is by <strong><a href="https://twitter.com/#!/elight">Evan Light</a></strong> a test-obsessed developer, the author of several rarely used gems, and the curator of Ruby DCamp. When he&#8217;s not a talking head at conferences, he&#8217;s usually working at home as a freelance developer remotely mentoring a developer, working for one or more startups, playing with open source, keeping his wife and four cats company, hacking nonsensically, talking at people on the internet, and/or attempting to lose weight (or any combination of the above). What else do you do when you live 3 hours from civilization?
  </p>
  
  <p class="block">
    <img class="alignright" src="http://www.gravatar.com/avatar/3c51f636715fb42bc82141702aa92b09?s=125" alt="Evan Light" /> You know what bugs me? People who don&rsquo;t write idiomatic conditionals in Ruby.
  </p>
  
  <p>
    Many folks, especially those who came out of Java, .NET, or C/C++, use and abuse the ternary. The ternary is a humble little production rule that works like so:
  </p>
  
  <pre><code>&lt;boolean expression&gt; ? &lt;eval this expression if truthy&gt; : &lt;eval if falsey&gt;
</code></pre>
  
  <p>
    The ternary can be useful if the truthy and falsey cases are terse and well-named. However, it&rsquo;s common to see multi-line ternaries or, even worse, nested ternaries. For example:
  </p>
  
  <p>
  </p>
  
  <p>
    By the way, the above example comes out of Rails.
  </p>
  
  <p>
    Accepting that the above is just painful, how could we make it hurt less? Specifically, let&rsquo;s focus on the nested ternary on Line 7 (accepting that there are other ways that the code can be made clearer).
  </p>
  
  <p>
    For starters, let&rsquo;s DRY up these Hash lookups:
  </p>
  
  <p>
  </p>
  
  <p>
    Now let&rsquo;s unravel this into more idiomatic Ruby. We&rsquo;ll extract the outer ternary into a functional style if-else. Remember that every expression in Ruby returns the value of its last executed expression. The if-else returns either the value of the computed String in the <strong><em>if</em></strong> or the empty String <strong><em>else</em></strong>. It has the advantage of containing more English words and fewer characters that resemble modem line noise or PERL.
  </p>
  
  <p>
  </p>
  
  <p>
    We can get rid of this <strong><em>else</em></strong>. After all, it doesn&rsquo;t contain any logic. Let&rsquo;s just make it the default value for <strong><em>method_prefix</em></strong> and then assign a new value only when <strong><em>prefix</em></strong> is truthy.
  </p>
  
  <p>
  </p>
  
  <p>
    Ah so what this code really cares about, first and foremost, is whether <strong><em>prefix</em></strong> is falsey. When it&rsquo;s falsey, it just returns an empty String! Otherwise, if it&rsquo;s not, it generates a String possibly using the value of <strong><em>prefix</em></strong> if and only if <strong><em>prefix</em></strong> is not true &ndash; not a boolean.
  </p>
  
  <p>
    So why should we try to avoid ternaries? Because, when used within a complex expression, they tend to lack the clarity of intent of an if-else. The lack of clarity likely resulted in the less DRY previous implementation. Once we introduced more clarity, it became obvious how this code could be DRY&rsquo;d up, resulting in better readability.
  </p>
  
  <p>
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post.</em> Thanks!
  </p>
  
  <p class="update">
    Subscribe to the waiting list of the free, online &#8220;<a href="http://satishtalim.github.com/webruby/">Intermediate Ruby Course</a>&#8220;. As a bonus, get a free copy of the &#8220;Introduction to Rack&#8221; eBook (.pdf format).
  </p>
</div>

