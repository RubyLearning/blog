---
draft: false
title: How do I smell Ruby code?
date: 2011-03-01
author: Timon Vonk
categories:
- Beginners
- Ruby
- Ruby Masters
layout: post
permalink: /2011/03/01/how-do-i-smell-ruby-code/
tags:
- programming
- Ruby code smell
- ruby programming
topsy_short_url:
- http://bit.ly/hT9oKA
---

<div>
  <h3>
    How do I smell Ruby code?
  </h3>
  
  <h4>
    Understanding the worst of code
  </h4>
  
  <p class="update">
    This guest post is by <strong><a href="http://www.linkedin.com/in/timonv">Timon Vonk</a></strong>, who is a self-employed Ruby enthusiast and standard nerd with an edge. He has worked with Ruby for several years, but is well-known with many other (programming) languages. Also likes martial arts, loud music, varying quantities of booze and a good scotch.
  </p>
  
  <h3>
    Introduction
  </h3>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/TimonVonk.jpg" alt="Timon Vonk" title="Timon Vonk" /> <span class="drop_cap">W</span>riting bad code isn&#8217;t a bad thing. Not understanding the problem you&#8217;re trying to solve any better after having written that piece of code is. Fortunately, that happens far less often. In this article I hope to give a better understanding of Ruby code by going into Ruby specific code smells. We&#8217;ll start with some simple examples that are common in all programming languages – they just need to be covered – and then dive into some Ruby specific smells.
  </p>
  
  <h3>
    So what is that smell?
  </h3>
  
  <p>
    The term was coined in the 90s by Kent Beck on WardsWiki (one of the first wikis around) and has been popularized ever since. A code smell is a hunch, not necessarily measurable, that the code you&#8217;re looking at can be improved in some way. This process of improvement is called refactoring, as you might know. And as far as refactoring is concerned, there is no time like now, don&#8217;t leave open ends; it’s a bad habit.
  </p>
  
  <h3>
    The Basics
  </h3>
  
  <p>
    Let us give a quick rundown on the more basic code smells:
  </p>
  
  <ul>
    <li>
      Duplicated code, if you see any, is almost always a bad thing. We&#8217;ll get into this part a little later.
    </li>
    <li>
      Multiple method / class responsibility is always a bad thing. Try factoring out your solution in multiple methods. It will make you&#8217;re code more readable and a lot better maintainable. Large methods and classes are a dead giveaway for this as well.
    </li>
    <li>
      A class should never use more methods from other classes than from itself. Why is it even there?
    </li>
    <li>
      A child class should always honor the contract of the parent class, i.e., be a kind of that class. Check out the Liskov substitution principle for more information.
    </li>
    <li>
      If a class hardly does anything, why is it there?
    </li>
    <li>
      Does your solution have a more simple approach? Complexity can be a reason of pride for some – if not most – coders, but too much makes it terrible to understand, especially later on.
    </li>
    <li>
      Non-descriptive or too long identifiers or names are a good sign that either you can&#8217;t define the responsibility of the code, or you have a hard time with naming conventions.
    </li>
  </ul>
  
  <p>
    Simple, easy smells should give a good start on fine tuning your code. However, every language has its own specific quirks. Let us take a look at Ruby.
  </p>
  
  <h3>
    Calling eval on user input or unchecked code
  </h3>
  
  <pre>input = "'rm -rf /'"
klass =  eval input
</pre>
  
  <p>
    Of course this is bad. I hope it doesn&#8217;t need any explanation. Try not to use <tt>eval</tt>, but <tt>instance_eval</tt> instead. And if you use either, make sure that the code you eval is secure &#8212; never eval user input directly.
  </p>
  
  <h3>
    Nested blocks without added value
  </h3>
  
  <pre>array = [["banana", "apple"],["pineapple","beer"]]
# And I want to call reverse on each element, I could do
array.collect { |sub_array| sub_array.collect { |subsub_array| subsub_array.reverse }}
# But this is much nicer
array.collect { |sa| sa.collect(&:reverse) }
# => [["ananab", "elppa"],["elppaenip","reeb"]]
</pre>
  
  <p>
    The reason is simple enough. Your code is more readable, and that&#8217;s what we all want. So what about nested multi-line blocks? Check it out, big chance your solution is the root of this particular evil.
  </p>
  
  <h3>
    Code similarity
  </h3>
  
  <pre>def post_to_site(data)
  url = build_url(data)
  response = RestClient.post(url)
end

def get_from_site(data)
  url = build_url(data)
  response = RestClient.get(url)
end

def delete_from_site(data)
  url = build_url(data)
  response = RestClient.delete(url)
end
</pre>
  
  <p>
    You can easily solve this lump of code by introducing some meta-programming:
  </p>
  
  <pre>def  response_from_site(data, method = :get)
  url = build_url(data)
  response = RestClient.public_send(method, url)
end
</pre>
  
  <p>
    This gives you a clean, nicer method. And it&#8217;s readable too! Isn&#8217;t that nice?
  </p>
  
  <h3>
    Long, repetitive and cluttering statements
  </h3>
  
  <p>
    Often enough you have similar parameters that call similar methods. For instance, you might need to check on some parameter and call the associated method. Or even simpler, you might need to check if a certain user input matches your criteria. I prefer a simple rule of thumb, if you&#8217;re working with any sort of collection or set, the functional approach is always cleaner, more simple and most definitely faster. The point is not to dictate when and whether you should prefer the functional approach, just that you understand that long lines of repetitive clutter screw up your code.
  </p>
  
  <p>
    Take the following example:
  </p>
  
  <pre>input = "english"
case input
when "english"
  puts "English, ***, do you speak it?"
when "french"
  puts "Baguette!"
when "dutch"
  puts "I only smoke *** when it's free."
else
  puts "Dunno"
end
</pre>
  
  <p>
    You can imagine in complex applications that this goes on and on. I actually see it happen a lot and it’s not necessarily bad. However, it’s hard to maintain and in more complex situations it can get really hard to read through. I&#8217;ve seen loads of Rails applications where they use just this to check on a particular parameter. Really ugly!
  </p>
  
  <p>
    Since it seems like you&#8217;re white listing, one way to solve it would be to use a hash with input:result.
  </p>
  
  <pre>whitelist = {
  "english" =&gt; "English, ***, do you speak it?",
  "french" =&gt; "Baguette!",
  "dutch" =&gt; "I only smoke *** when it's free.",
  "other" =&gt; "Dunno."
}

if whitelist.has_key?(input)
  puts whitelist[input]
else
  puts whitelist[other]
end
</pre>
  
  <p>
    It&#8217;s always important to be proud of the code you write. It really helps if it doesn&#8217;t smell. And I hope this article helped you do that.
  </p>
  
  <p>
    <em>Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
  
  <p>
    <b>You might want to read a related article</b>:
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/blog/2010/11/08/how-does-your-code-smell/">How does your code smell?</a>
    </li>
  </ul>
</div>

