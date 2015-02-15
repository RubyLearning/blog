---
title: How do I benchmark Ruby code?
author: Jesse Storimer
date: 2013-06-19
layout: post
permalink: /2013/06/19/how-do-i-benchmark-ruby-code/
thesis_description:
  - Jesse Storimer shows us how to benchmark Ruby code.
thesis_keywords:
  - Ruby, Programming, Jesse Storimer, Benchmark, Benchmark Ruby code
topsy_short_url:
  - http://bit.ly/13SgEDc
categories:
  - Ruby
  - Ruby Masters
  - Tricks
tags:
  - Benchmark
  - Benchmark Ruby code
  - Jesse Storimer
  - programming
  - Ruby
---
<div>
  <h2 id="how-do-i-benchmark-ruby-code">
    How do I benchmark Ruby code?
  </h2>
  
  <p class="update">
    This guest post is by Jesse Storimer. He&#8217;s the author of <a href="http://www.jstorimer.com/products/working-with-unix-processes">Working With Unix Processes</a>, a gentle introduction to Unix system programming for Ruby programmers. Jesse has been programming Ruby since joining Shopify in 2008 and is still going strong, always looking for a chance to dig lower down into the stack. He lives way in the backwoods of southern Ontario, Canada with his wife and two daughters. Jesse blogs at <a href="http://jstorimer.com/">jstorimer.com</a> and has authored a few <a href="http://www.jstorimer.com/books">other books</a> for Ruby developers.
  </p>
  
  <p class="block">
    <img class="alignright" alt="Jesse Storimer" src="http://rubylearning.com/images/jessestorimer.jpg" width="125" height="125" /> <b><span class="drop_cap">S</span></b>o you&#8217;ve got some Ruby code and you want to make it faster. Maybe you&#8217;ve already got a new implementation in mind, or maybe you&#8217;re still cooking that up. But how do you make <em>certain</em> that your new implementation is faster?
  </p>
  
  <p>
    Science, of course! Ruby&#8217;s standard library comes with a benchmarking library fit for measuring the execution time of your Ruby code. The <code>Benchmark</code> module offers several different ways for you to benchmark your code. I&#8217;ll take you through the different options and their use cases.
  </p>
  
  <h3 id="getting-started">
    Getting started
  </h3>
  
  <p>
    The <code>Benchmark</code> module is in the standard library, so you don&#8217;t need to install any gems to get it. Here&#8217;s the <a href="http://www.ruby-doc.org/stdlib-2.0/libdoc/benchmark/rdoc/Benchmark.html">documentation from the standard library</a>.
  </p>
  
  <p>
    The simplest way to measure your Ruby code is with <code>Benchmark.measure</code>.
  </p>
  
  <pre>require 'benchmark'
require 'bigdecimal/math'

# calculate pi to 10k digits
puts Benchmark.measure { BigMath.PI(10_000) }</pre>
  
  <p>
    This will return something that looks like this:
  </p>
  
  <pre>  0.310000   0.040000   0.350000 (  0.339958)</pre>
  
  <p>
    With no context, these might look like magic numbers. Here&#8217;s what they mean:
  </p>
  
  <div style="text-align: center">
    <img style="padding-bottom: 0.5em" alt="Benchmark numbers breakdown" src="http://rubylearning.com/images/benchmark-breakdown.jpg" />
  </div>
  
  <p>
    Generally, the number farthest to the right is the most important one. It tells how long it actually took to perform the operation. If you&#8217;re curious about why the clock time is so high, the other numbers can help you drill down to see if you&#8217;re spending time in system functions or your own code.
  </p>
  
  <p>
    Now that you know what those magic numbers mean, we can move on to the core <code>Benchmark</code> API. The truth is that I rarely use the <code>measure</code> method on its own. It only prints the benchmark for a single block of code. The most common way to use <code>Benchmark</code> is to compare the execution time of different approaches to the same problem.
  </p>
  
  <p>
    Benchmark has some built-in methods for this exact purpose.
  </p>
  
  <h3 id="benchmarkbm">
    Benchmark#bm
  </h3>
  
  <p>
    This method lets you define several blocks of code to benchmark, then prints the results side-by-side in the same format you saw earlier.
  </p>
  
  <pre>require 'benchmark'

iterations = 100_000

Benchmark.bm do |bm|
  # joining an array of strings
  bm.report do
    iterations.times do
      ["The", "current", "time", "is", Time.now].join(" ")
    end
  end

  # using string interpolation
  bm.report do
    iterations.times do
      "The current time is #{Time.now}"
    end
  end
end</pre>
  
  <p>
    This will print the following result:
  </p>
  
  <pre>       user     system      total        real
   0.540000   0.010000   0.550000 (  0.556572)
   0.410000   0.010000   0.420000 (  0.413467)</pre>
  
  <p>
    Notice that this is the same format I outlined earlier, but now you have little hints about each of the numbers.
  </p>
  
  <p>
    The core API here is this:
  </p>
  
  <pre>Benchmark.bm do |bm|
  bm.report { first_approach }
  bm.report { alternative_approach }
end</pre>
  
  <p>
    You call the <code>Benchmark#bm</code> method passing a block. The block variable is a special object provided by <code>Benchmark</code>. It gives you a <code>report</code> method that you call with the block of code that you want to measure. <code>Benchmark</code> then runs both blocks of code and prints their execution times side-by-side.
  </p>
  
  <p>
    <em>A note about iterations:</em> Often, when doing benchmarks that test code that executes very quickly, you need to do many iterations to see a meaningful number. In this case, I did 100,000 iterations of each variant just to get the execution time up to half a second so I could grasp the difference.
  </p>
  
  <h3 id="labels">
    Labels
  </h3>
  
  <p>
    In that last benchmark, I buried some comments in the source that said what each block of code was doing. That&#8217;s not so helpful when looking at the results! <code>Benchmark</code> allows you to pass in a label to the <code>report</code> method that will be printed along with the results.
  </p>
  
  <pre>require 'benchmark'

iterations = 100_000

Benchmark.bm(27) do |bm|
  bm.report('joining an array of strings') do
    iterations.times do
      ["The", "current", "time", "is", Time.now].join(" ")
    end
  end

  bm.report('string interpolation') do
    iterations.times do
      "The current time is #{Time.now}"
    end
  end
end</pre>
  
  <p>
    I&#8217;ve now removed the comments describing the blocks and pass them in to the <code>report</code> method as an argument. Now the output describes itself:
  </p>
  
  <pre>                                  user     system      total        real
joining an array of strings   0.550000   0.010000   0.560000 (  0.565089)
string interpolation          0.410000   0.010000   0.420000 (  0.416324)</pre>
  
  <p>
    There&#8217;s one more important change I made in that last example that may have gone unnoticed. I passed <code>27</code> as an argument to the <code>Benchmark.bm</code> method. This signifies how much padding the header labels should have in the result output. If you pass labels to <code>report</code>, but don&#8217;t set this value high enough, your output won&#8217;t line up properly.
  </p>
  
  <p>
    Let&#8217;s see an example with no argument passed to <code>Benchmark.bm</code>.
  </p>
  
  <pre>       user     system      total        real
joining an array of strings  0.520000   0.010000   0.530000 (  0.541942)
string interpolation  0.390000   0.010000   0.400000 (  0.394111)</pre>
  
  <p>
    That&#8217;s certainly not right. Make sure you pass a value that&#8217;s greater than the length of your longest label. That&#8217;s the happy path.
  </p>
  
  <h3 id="benchmarkbmbm">
    Benchmark#bmbm
  </h3>
  
  <p>
    The <code>Benchmark#bm</code> you just saw is really the core of <code>Benchmark</code>, but there&#8217;s one more method I should mention: <code>Benchmark#bmbm</code>. That&#8217;s right it&#8217;s the same method name, repeated twice.
  </p>
  
  <p>
    Sometimes, with a benchmark that creates a lot of objects, the results start to get skewed because of interactions with Ruby&#8217;s memory allocation or garbage collection routines. When creating a lot of objects, one block may need to run garbage collector, while the other doesn&#8217;t; or just one block may get stuck with the cost of allocating more memory for Ruby to use.
  </p>
  
  <p>
    In this case, the benchmark can produce unbalanced results. This is when you want to use <code>Benchmark#bmbm</code>.
  </p>
  
  <p>
    The method name is suitable because it actually benchmarks your blocks of code twice. First, it runs the code as a &#8216;rehearsal&#8217; to force any initialization that needs to happen, then it forces the GC to run, then it runs the benchmark again &#8216;for real&#8217;. This ensures that the system is fully initialized and the benchmark is fair.
  </p>
  
  <p>
    This last example benchmark allocates a lot of objects. When this runs at the rehearsal stage, Ruby has to allocate more memory to make room for all the objects. Then when the &#8216;real&#8217; benchmark happens, the memory is already available and just the actual implementation is tested.
  </p>
  
  <pre>require 'benchmark'

array = Array(1..10_000_000)

Benchmark.bmbm(7) do |bm|
  bm.report('reverse') do
    array.dup.reverse
  end

  bm.report('reverse!') do
    array.dup.reverse!
  end
end</pre>
  
  <p>
    And here&#8217;s the result:
  </p>
  
  <pre>Rehearsal --------------------------------------------
reverse    0.020000   0.020000   0.040000 (  0.050908)
reverse!   0.030000   0.020000   0.050000 (  0.048042)
----------------------------------- total: 0.090000sec

               user     system      total        real
reverse    0.010000   0.000000   0.010000 (  0.015385)
reverse!   0.030000   0.000000   0.030000 (  0.023973)</pre>
  
  <p>
    Notice the discrepancy between the rehearsal and the benchmark! Thanks <code>bmbm</code>!
  </p>
  
  <h3 id="conclusion">
    Conclusion
  </h3>
  
  <p>
    When you want to try your hand at speeding up some of your Ruby code, make sure that you measure, measure, measure to prove that your new implementation is faster than the old one. This great little benchmarking library ships with Ruby right in the standard library, so there&#8217;s no excuses!
  </p>
  
  <p class="alert">
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Programming" rel="tag"> Programming</a>, <a href="http://technorati.com/tag/Jesse+Storimer" rel="tag"> Jesse Storimer</a>, <a href="http://technorati.com/tag/Benchmark" rel="tag"> Benchmark</a>, <a href="http://technorati.com/tag/Benchmark+Ruby+code" rel="tag"> Benchmark Ruby code</a>
