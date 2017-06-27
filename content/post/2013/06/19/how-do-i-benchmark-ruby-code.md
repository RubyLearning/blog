---
draft: false
title: How do I benchmark Ruby code?
date: 2013-06-19
author: Jesse Storimer
authorlink: "http://jstorimer.com"
socialsharing: true
authortwitter: https://twitter.com/jstorimer
categories:
- Ruby
- Ruby Masters
- Tricks
layout: post
permalink: /2013/06/19/how-do-i-benchmark-ruby-code/
tags:
- Benchmark
- Benchmark Ruby code
- Jesse Storimer
- programming
- Ruby
---
This guest post is by Jesse Storimer. Hes the author of [Working With Unix Processes](http://www.jstorimer.com/products/working-with-unix-processes),
a gentle introduction to Unix system programming for Ruby programmers.
Jesse has been programming Ruby since joining<!--more--> Shopify in 2008 and is
still going strong, always looking for a chance to dig lower down into
the stack. He lives way in the backwoods of southern Ontario, Canada
with his wife and two daughters. Jesse blogs at
[jstorimer.com](http://jstorimer.com/) and has authored a few [other books](http://www.jstorimer.com/books) for Ruby developers.

![Jesse Storimer](http://rubylearning.com/images/jessestorimer.jpg)
**S**o you've got some Ruby code and you want to make it faster. Maybe
youve already got a new implementation in mind, or maybe you're still
cooking that up. But how do you make *certain* that your new
implementation is faster?

Science, of course! Rubys standard library comes with a benchmarking
library fit for measuring the execution time of your Ruby code. The
`Benchmark` module offers several different ways for you to benchmark
your code. I'll take you through the different options and their use
cases.

## Getting started

The `Benchmark` module is in the standard library, so you don't need to
install any gems to get it. Heres the [documentation from the standard library](http://www.ruby-doc.org/stdlib-2.0/libdoc/benchmark/rdoc/Benchmark.html).

The simplest way to measure your Ruby code is with `Benchmark.measure`.

<script src="https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/01_code.rb?embed=t"></script>
[Code](https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/01_code.rb)

This will return something that looks like this:

<script src="https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/01_result.txt?embed=t"></script>
[Code](https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/01_result.txt)

With no context, these might look like magic numbers. Here's what they
mean:

![Benchmark numbers breakdown](http://rubylearning.com/images/benchmark-breakdown.jpg)

Generally, the number farthest to the right is the most important one.
It tells how long it actually took to perform the operation. If you're
curious about why the clock time is so high, the other numbers can help
you drill down to see if you're spending time in system functions or your
own code.

Now that you know what those magic numbers mean, we can move on to the
core `Benchmark` API. The truth is that I rarely use the `measure`
method on its own. It only prints the benchmark for a single block of
code. The most common way to use `Benchmark` is to compare the execution
time of different approaches to the same problem.

Benchmark has some built-in methods for this exact purpose.

## `Benchmark#bm`

This method lets you define several blocks of code to benchmark, then
prints the results side-by-side in the same format you saw earlier.

<script src="https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/02_code.rb?embed=t"></script>
[Code](https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/02_code.rb)

This will print the following result:

<script src="https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/02_result.txt?embed=t"></script>
[Code](https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/02_result.txt)

Notice that this is the same format I outlined earlier, but now you have
little hints about each of the numbers.

The core API here is this:

<script src="https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/03_core_example.rb?embed=t"></script>
[Code](https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/03_core_example.rb)

You call the `Benchmark#bm` method passing a block. The block variable
is a special object provided by `Benchmark`. It gives you a `report`
method that you call with the block of code that you want to measure.
`Benchmark` then runs both blocks of code and prints their execution
times side-by-side.

*A note about iterations:* Often, when doing benchmarks that test code
that executes very quickly, you need to do many iterations to see a
meaningful number. In this case, I did 100,000 iterations of each
variant just to get the execution time up to half a second so I could
grasp the difference.

## Labels

In that last benchmark, I buried some comments in the source that said
what each block of code was doing. Thats not so helpful when looking at
the results! `Benchmark` allows you to pass in a label to the `report`
method that will be printed along with the results.

<script src="https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/f4c734192682d7576b3ff804bfbb1271a16ae250/2013/06/19/how-do-i-benchmark-ruby-code/04_benchmark_labels.rb?embed=t"></script>
[Code](https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/04_benchmark_labels.rb)

Ive now removed the comments describing the blocks and pass them in to
the `report` method as an argument. Now the output describes itself:

<script src="https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/04_benchmark_results_padding.txt?embed=t"></script>
[Code](https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/04_benchmark_results_padding.txt)

There's one more important change I made in that last example that may
have gone unnoticed. I passed `27` as an argument to the `Benchmark.bm`
method. This signifies how much padding the header labels should have in
the result output. If you pass labels to `report`, but dont set this
value high enough, your output wont line up properly.

Lets see an example with no argument passed to `Benchmark.bm`.

<script src="https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/04_benchmark_results_no_padding.txt?embed=t"></script>
[Code](https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/04_benchmark_results_no_padding.txt)


Thats certainly not right. Make sure you pass a value thats greater than
the length of your longest label. Thats the happy path.

## Benchmark\#bmbm

The `Benchmark#bm` you just saw is really the core of `Benchmark`, but
theres one more method I should mention: `Benchmark#bmbm`. Thats right
its the same method name, repeated twice.

Sometimes, with a benchmark that creates a lot of objects, the results
start to get skewed because of interactions with Rubys memory allocation
or garbage collection routines. When creating a lot of objects, one
block may need to run garbage collector, while the other doesnt; or just
one block may get stuck with the cost of allocating more memory for Ruby
to use.

In this case, the benchmark can produce unbalanced results. This is when
you want to use `Benchmark#bmbm`.

The method name is suitable because it actually benchmarks your blocks
of code twice. First, it runs the code as a ‘rehearsal to force any
initialization that needs to happen, then it forces the GC to run, then
it runs the benchmark again ‘for real. This ensures that the system is
fully initialized and the benchmark is fair.

This last example benchmark allocates a lot of objects. When this runs
at the rehearsal stage, Ruby has to allocate more memory to make room
for all the objects. Then when the ‘real benchmark happens, the memory
is already available and just the actual implementation is tested.

<script src="https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/05_benchmark_bmbm.rb?embed=t"></script>
[Code](https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/05_benchmark_bmbm.rb)

And here's the result:

<script src="https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/05_benchmark_bmbm_results.txt?embed=t"></script>
[Code](https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/c40eadba0e5256e0c5c27f538315222c2e5d290f/2013/06/19/how-do-i-benchmark-ruby-code/05_benchmark_bmbm_results.txt)

Notice the discrepancy between the rehearsal and the benchmark! Thanks
`bmbm`!

## Conclusion

When you want to try your hand at speeding up some of your Ruby code,
make sure that you measure, measure, measure to prove that your new
implementation is faster than the old one. This great little
benchmarking library ships with Ruby right in the standard library, so
theres no excuses!

*I hope you found this article valuable. Feel free to ask questions and
give feedback in the comments section of this post. Thanks!*
