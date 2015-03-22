---
draft: false
title: Clojure Tips from the Experts
date: 2010-07-26
author: Satish Talim
authorlink: "http://satishtalim.com"
socialsharing: true
authorgoogleplus: https://plus.google.com/+SatishTalim/about
authorlinkedin: https://www.linkedin.com/in/satishtalim
authortwitter: http://twitter.com/IndianGuru
authorfacebook: https://www.facebook.com/satishtalim/about
categories:
- Beginners
- Clojure
- Tricks
layout: post
permalink: /2010/07/26/clojure-tips-from-the-experts/
tags:
- Clojure
- Clojure Tips
---
RubyLearning wrote to a lot of experts, gathering their best tips on
Clojure. The tips are still coming in, but here are some to get you
started with. Feel free to add your own tips in the comments section or
send the same to **satishtalim [at] gmail.com**. Enjoy!

## Antonio Cangiano

Find him on [Twitter](http://twitter.com/acangiano). His
[Blog](http://programmingzen.com/).

When learning a new programming language, I find [Project
Euler](http://projecteuler.net/) to be an invaluable source of
self-contained, increasingly more challenging exercises. By solving
these mathematical problems in your language of choice, you’ll get some
degree of exposure and familiarity with that language before tackling
more complex, real world tasks.

When you solve a problem, you gain access to a forum where you can
compare your implementation with those of other people who may have used
the same language as you, or a different one. Normally there is a
variety of common (and not so common) languages used by fellow
participants.

Through the forum you’ll learn about more efficient algorithms and
clever tricks, but above all you’ll get to see different ways to solve
the same problem. It’s not hard to spot clean, concise, and idiomatic
implementations and as a result end up learning more about the language
you used.

Unfortunately for Clojure beginners, the threads in the forum for many
of the initial problems were closed a long time ago. In practice, this
means that you can usually read solutions implemented in many
established programming languages, including Ruby and Haskell, but you
won’t find solutions in Clojure for most of the problems (Clojure is
after all much newer).

Thankfully, [a wiki](http://clojure-euler.wikispaces.com/) which
collects many solutions in Clojure exists. If you solve the problems
first on your own, you can then use this resource to compare your
approach with those of other Clojure programmers. You may discover that
there is a better, more idiomatic way of solving a given problem.

In short, use [Project Euler](http://projecteuler.net/) and the [Clojure
Euler wiki](http://clojure-euler.wikispaces.com/) if you want to get
some experience with Clojure’s syntax and fundamental concepts, which
you may have only read about in books or online tutorials.

* * * * *

## Baishampayan Ghose

Find him on [Twitter](http://twitter.com/ghoseb). His
[GitHub](http://github.com/ghoseb/) a/c.

It’s hard to pin point a few good tips because Clojure can do so many
things in very nice and ingenious ways, that it’s not even funny.
Anyway, here are a few:

**Tip \#1**: Sort a map on multiple keys:

    ;;; Tip #1
    ;;; A vector of maps
    (def some-maps [{:x 1 :y 2} {:x 2 :y 1} {:x 1 :y 4} {:x 2 :y 8}])

    ;;; Sort the maps first on :x and then on :y

    (defn sort-maps-by
      "Sort a sequence of maps (ms) on multiple keys (ks)"
      [ms ks]
      (sort-by #(vec (map % ks)) ms))

    ;;; (sort-maps-by some-maps [:x :y])
    ;;; output> ({:x 1, :y 2} {:x 1, :y 4} {:x 2, :y 1} {:x 2, :y 8})

**Tip \#2**: When dealing with infinite sequences on the REPL, you can
set the number of items to be printed:

    ;;; Tip #2
    ;;; When you type something like (iterate inc 1) on the REPL (or any
    ;;; kind of infinite, lazy sequence) the REPL will try to evaluate the
    ;;; whole thing and will never finish. One way to print some parts of
    ;;; an infinite sequence on the REPL is to do this on the REPL and
    ;;; then try to print the sequence -
    ;;; (set! *print-length* 10)
    ;;; (iterate inc 1)
    ;;; Which will only print the first 10 items of the above infinite
    ;;; sequence -
    ;;; (1 2 3 4 5 6 7 8 9 10 ...)
    ;;; There is also *print-level* which can be used to determine how
    ;;; nested/recursive data-structures are printed on the REPL

**Tip \#3**: Use of the -\> & -\>\> threading macros:

The -\> & -\>\> threading macros are very useful to sometimes untangle
nested function calls. The -\> macro takes a bunch of ‘forms’ and
‘threads them’ into each other by inserting every form as the second
item of the next form and so on. So, (-\>\> a (b c) (d e f) (g h))
becomes (g (d (b a c) e f) h). -\>\> is similar but it puts the form as
the last item of the next form. (-\>\> a (b c) (d e f) (g h)) then
becomes (g h (d e f (b c a))).

    (ns tips
      ;; requires clojure 1.2 if you are on 1.1.x, use this instead
      ;; (:require [clojure.contrib.duck-streams :as io])
      (:require [clojure.contrib.io :as io]))

    ;;; Tip #3
    ;;; Use of the -> & ->> threading macros.
    (defn word-freq
      "Calculate a frequency map of words in a text file."
      [f]
      (take 20 (->> f
                    io/read-lines
                    (mapcat (fn [l] (map #(.toLowerCase %) (re-seq #"\w+" l))))
                    (remove #{"the" "and" "of" "to" "a" "i" "it" "in" "or" "is"})
                    (reduce #(assoc %1 %2 (inc (%1 %2 0))) {})
                    (sort-by (comp - val)))))

    ;;; Run it like this (word-freq "/path/to/file.txt")

* * * * *

## Brian Carper

Find him on [Twitter](http://twitter.com/BrianCarper). His
[Blog](http://briancarper.net/).

“Named” or “keyword” arguments for functions have some benefits over
positional arguments:

1.  You can specify arguments in any order.
2.  The arguments are named explicitly, resulting in less room for error
    compared to positional arguments, where it’s easy to transpose two
    arguments in the list.
3.  Your function can easily provide default argument values.

For a function that takes only one or two arguments, keyword arguments
might be overkill. But the benefits of keyword arguments quickly become
more apparent the more argumentss your function accepts.

Clojure doesn’t have canonical support for keyword arguments. But there
are a couple of ways you can achieve the same result.

The first is simply to force the user to pass a hash-map explicitly.

    (defn named-args-1 [foo argmap]
     (println "foo:" foo
              "bar:" (:bar argmap 0)
              "baz:" (:baz argmap 0))
     (println "bar-given?" (contains? argmap :bar)
              "baz-given?" (contains? argmap :baz)))

    user> (named-args-1 1 {:baz 2})
    foo: 1 bar: 0 baz: 2
    bar-given? false baz-given? true

But wrapping arguments in braces is arguably an unnecessary burden on
users of your code. A better way is to use destructuring to allow the
user to “flatten” the map:

    (defn named-args-2 [foo & args]
     (let [argmap (apply hash-map args)
           {:keys [bar baz]
            :or   {bar 0 baz 0}} argmap]
       (println "foo:" foo
                "bar:" bar
                "baz:" baz)
       (println "bar-given?" (contains? argmap :bar)
                "baz-given?" (contains? argmap :baz))))

    user> (named-args-2 1 :baz 2)
    foo: 1 bar: 0 baz: 2
    bar-given? false baz-given? true

This is OK for the user, but verbose for the function-writer. And the
argument list for the function is specified as “args”, giving the user
no clue as to what keys are expected or legal.

As of recent releases of Clojure, you can do the destructuring right in
the function’s argument list, leading to this version:

    (defn named-args-3 [foo & {:keys [bar baz]
                              :or   {bar 0 baz 0}
                              :as   argmap}]
     (println "foo:" foo
              "bar:" bar
              "baz:" baz)
     (println "bar-given?" (contains? argmap :bar)
              "baz-given?" (contains? argmap :baz)))

    user> (named-args-3 1 :baz 2)
    foo: 1 bar: 0 baz: 2
    bar-given? false baz-given? true

It’s also possible to roll your own macro to do keyword arguments. See
**clojure.contrib.def/defnk**, for example.

* * * * *

## Craig Andera

Find him on [Twitter](http://twitter.com/craigandera). His
[Blog](http://www.pluralsight-training.net/community/blogs/craig/).

I have two. The first one I stole from Mike Fogus: to use “,,,” as a
placeholder in the **-\>** and **-\>\>** macros. Since commas are
whitespace, they can be used as markers to indicate how the expressions
flow through the threading macros. So, for instance, you can write:

    (->>
     (iterate inc 1)
     (map #(* 5 %) ,,,)
     (filter odd? ,,,))

and the commas indicate “the previous expression will be inserted here”.

It’s not something you should put in production code, but I found it
enormously helpful in “getting” the -\> and -\>\> macros. Honestly, I
only had to write it out this way once or twice before it clicked with
me and I stopped using the commas altogether.

The other tip I have, has to do with understanding when to use **map**,
**filter**, and **reduce**. These three functions are where an enormous
amount of Clojure’s power comes from, but I find that beginners (such as
myself) sometimes have a hard time selecting which one – or which
combination – to use. What I’ve found is that it’s helpful to think of
these in terms of what you \*have\* and what you \*need\*:

-   If you \*have\* a sequence of length n and you \*need\* a sequence
    of length n, use **map**.
-   If you \*have\* a sequence of length n and you \*need\* a shorter
    sequence, use **filter**.
-   If you \*have\* a sequence of length n and you \*need\* a scalar,
    use **reduce**.

It seems pretty obvious when stated like that, but it has been helpful
to me on occasion when I start to get lost in how to express a
particular algorithm.

* * * * *

## Meikel Brandmeyer

Find him on [Twitter](http://twitter.com/kotarak). His [BitBucket
Id](http://bitbucket.org/kotarak).

Here is my tip on **atoms**.

Clojure provides a lot of facilities to tackle the complexity of
concurrent programming. But still you have to understand the semantics
of the underlying facilities. One of these are **refs**, which allow
coordinated access to several different entities at once. However, their
use inflicts quite a bit of ceremony. You have to invoke the STM
machinery whenever you want to write to a **ref** or want a consistent
snapshot of several **refs**. Also your transaction is rolled back
should a surrounding transaction retry. This is not always what you
want.

In such cases, it is interesting to use an **atom**. They are cheaper in
terms of overhead and don’t interact with the STM. So the retry of a
surrounding transaction doesn’t affect them. However they are
uncoordinated: you can’t safely update multiple **atoms** at once.

What is not so well known, is the fact, that **refs** also coordinate
several accesses to the \*same\* **ref**. Again, this does \*not\* work
well with **atoms**. Consider a cache, eg. for a **memoized** function.

    (defn memoize
     [f]
     (let [cache (atom {})]
       (fn [& args]
         (when-not (contains? @cache args)
           (swap! cache assoc args (apply f args)))
         (get @cache args))))

This code uses an **atom** and clojure datastructures, so we have no
problems with concurrency, right? **Wrong!** There are plenty of race
conditions between the different calls to **contains?**, **swap!** and
**get**. In the example, the worst thing that can happen is that we
compute the value of the function call several times. This can already
be quite annoying if the call is expensive in computation time and/or
resources. But consider a more involved cache implementation which could
also remove entries from the cache. Then the call to **contains?** could
see the value, but when we call get it might already be removed.

The problem is, that we access the atom’s contents several times and
this is not coordinated. Contrary to **refs** where we could call ensure
to – well – ensure that the **ref** doesn’t change under our hands.

How to solve this problem? Well, the problem is that we touch the
**atom** several times. So the solution is to touch the **atom** only
once!

    (defn memoize
     [f]
     (let [cache  (atom {})
           update (fn [state args]
                    (if-not (contains? state args)
                      (assoc state args (apply f args))
                      state))]
       (fn [& args]
         (get (swap! cache update args) args))))

Here we do the contains check and update in one function which will see
a consistent view of the cache state. Note that we also use the return
value of the **swap!**. Otherwise we would again have to access to the
atom several times!

So while Clojure provides a lot of tools to tackle the problems of a
concurrent world, you still have to understand what the semantics of the
different tools are. And even then you have to carefully reason about
your code. How it behaves. Where race conditions might hide. Life is not
easy.

**Note**: There are other problems to the above problem. Eg. doing
expensive work – namely calling f – in a **swap!**. Please read
[Meikel’s blog
post](http://kotka.de/blog/2010/03/memoize_done_right.html) on
**memoize** where even more such considerations are taken into account.

* * * * *

## Michael Fogus

Find him on [Twitter](http://twitter.com/fogus). His book [The Joy of
Clojure](http://fogus.me/).

Many macros that I write start exactly the same way:

       (defmacro a-macro [& forms]
         `'~forms)

Then it proceeds to be transformed into a pipeline where each piece does
a gradual transformation of forms:

       (defn do-something [forms]
         (frobnicate forms))

       (defn do-something-else [forms]
         (moidilize forms))

       (defmacro a-macro [& forms]
         (let [forms (do-something forms)
               forms (do-something-else forms)])
         `'~forms)

This makes it easy to see the transformations occurring at each step,
keeps my macros small, and allows me to put error handling in each of
the transformation functions for compile-time exceptions.

Although this is all pretty arcane as I try really really hard to avoid
writing macros else I get beaten.

* * * * *

## Michael Kohl

Find him on [Twitter](http://twitter.com/citizen428). His
[Blog](http://citizen428.net/).

My tip would be the [Clojure reader macro
**\#\_**](http://clojure.org/reader) which completely ignores the next
form. From the docs:

“The form following **\#\_** is completely skipped by the reader. (This
is a more complete removal than the **comment** macro which yields
**nil**).”

This can be immensely useful while debugging.

* * * * *

## Nurullah Akkaya

Find him on [Twitter](http://twitter.com/nakkaya). His
[Blog](http://nakkaya.com/).

My tip would be on destructuring, which allows you to pull apart data
structures into local bindings.

         (let [[x y] [1 2]] 
           x)
         ;;user=> 1

         (let [[a b c] "abc"] 
           c)
         ;;user=> \c

         (let [[[x1 y1][x2 y2]] [[1 2] [3 4]]]
           [x1 y1 x2 y2])
         ;;user=> [1 2 3 4]

Besides destructuring sequential things (vectors, lists, seqs, strings,
arrays, or anything that supports nth), you can destructure maps as
well:

         (let [{key1 :key1 key2 :key2} {:key1 5 :key2 6}] 
           [key1 key2])
         ;;user=> [5 6]

         (let [{[x1 y1] :player1 [x2 y2] :player2} {:player1 [5 6] :player2 [9 9]}] 
           [x1 y1 x2 y2])
         ;;user=> [5 6 9 9]

Most of the time, your local variables has the same names as the
keywords, Clojure provides a shortcut that saves you from typing binding
x keyword :x over and over again:

         (let [{:keys [key1 key2]} {:key1 5 :key2 6}] 
                [key1 key2])
         ;;user=> [5 6]

For more on destructuring, checkout the
[documentation](http://clojure.org/special_forms#Special%20Forms--(let[bindings*%20]%20exprs*).

* * * * *

## Ramakrishnan Muthukrishnan

Find him on [Twitter](http://twitter.com/vu3rdd). His [GitHub
Id](http://github.com/vu3rdd).

**Tip \#1**:

If you have a sequence and want to remove duplicates, there are
(atleast) two ways to do it:

    (vec (into #{} [1 2 2 3 4 5])) ; => [1 2 3 4 5]

or

    (distinct [1 2 2 3 4 5]) ; => [1 2 3 4 5]

The second one is preferred.

**Tip \#2**:

In a function, if you have a list of parameters, you can do the
following:

    (defn foo [x & xs]
     (...))

The same can be done in anonymous functions too. What if you are using
the abbreviated form (reader macro form) of an anonymous function? You
can still use it by using the “%&” to denote the rest of the argument as
a list. One example of the use of this form is shown
[here](http://www.bestinclass.dk/index.clj/2009/10/brians-functional-brain.html).

**Tip \#3**: I echo Craig Andera’s opinions on **map**, **filter** and
**reduce**. It is extremely important to master these three constructs.
Especially, the way **reduce** can be used with hash-maps.

**Tip \#4**: If you want to have default values for some of the input
parameters, one way is to define functions of diferent arity.

    (defn foo
     ([] (foo "bar"))
     ([s] (........)))

Here, when ‘foo’ is called without any arguments, we assume a default
value of “bar”, a string as argument to the function and call foo with
that argument.

* * * * *

## Stuart Sierra

Find him on [Twitter](http://twitter.com/stuartsierra). His
[Blog](http://stuartsierra.com/).

Well, I’ve said this before, but it bears saying again: Don’t write a
macro where a function will do. Functions are more flexible: they can be
composed and passed as values. Do not use macros solely to make the
syntax “prettier.”

* * * * *

Do you like these tips? We are eager to know your reactions as comments
to this post.
