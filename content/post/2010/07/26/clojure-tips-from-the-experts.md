---
title: Clojure Tips from the Experts
author: Satish Talim
date: 2010-07-26
layout: post
permalink: /2010/07/26/clojure-tips-from-the-experts/
thesis_description:
  - A collection of the best tips on Clojure from the experts.
thesis_keywords:
  - Clojure,Clojure Tips
topsy_short_url:
  - http://bit.ly/d7qpuU
categories:
  - Beginners
  - Clojure
  - Tricks
tags:
  - Clojure
  - Clojure Tips
---
<div>
  <p class="alert">
    RubyLearning wrote to a lot of experts, gathering their best tips on Clojure. The tips are still coming in, but here are some to get you started with. Feel free to add your own tips in the comments section or send the same to <b>satishtalim [at] gmail.com</b>. Enjoy!
  </p>
  
  <h3>
    Antonio Cangiano
  </h3>
  
  <p>
    Find him on <a href="http://twitter.com/acangiano">Twitter</a>. His <a href="http://programmingzen.com/">Blog</a>.
  </p>
  
  <p>
    When learning a new programming language, I find <a href="http://projecteuler.net/">Project Euler</a> to be an invaluable source of self-contained, increasingly more challenging exercises. By solving these mathematical problems in your language of choice, you&#8217;ll get some degree of exposure and familiarity with that language before tackling more complex, real world tasks.
  </p>
  
  <p>
    When you solve a problem, you gain access to a forum where you can compare your implementation with those of other people who may have used the same language as you, or a different one. Normally there is a variety of common (and not so common) languages used by fellow participants.
  </p>
  
  <p>
    Through the forum you&#8217;ll learn about more efficient algorithms and clever tricks, but above all you&#8217;ll get to see different ways to solve the same problem. It&#8217;s not hard to spot clean, concise, and idiomatic implementations and as a result end up learning more about the language you used.
  </p>
  
  <p>
    Unfortunately for Clojure beginners, the threads in the forum for many of the initial problems were closed a long time ago. In practice, this means that you can usually read solutions implemented in many established programming languages, including Ruby and Haskell, but you won&#8217;t find solutions in Clojure for most of the problems (Clojure is after all much newer).
  </p>
  
  <p>
    Thankfully, <a href="http://clojure-euler.wikispaces.com/">a wiki</a> which collects many solutions in Clojure exists. If you solve the problems first on your own, you can then use this resource to compare your approach with those of other Clojure programmers. You may discover that there is a better, more idiomatic way of solving a given problem.
  </p>
  
  <p>
    In short, use <a href="http://projecteuler.net/">Project Euler</a> and the <a href="http://clojure-euler.wikispaces.com/">Clojure Euler wiki</a> if you want to get some experience with Clojure&#8217;s syntax and fundamental concepts, which you may have only read about in books or online tutorials.
  </p>
  
  <hr />
  
  <h3>
    Baishampayan Ghose
  </h3>
  
  <p>
    Find him on <a href="http://twitter.com/ghoseb">Twitter</a>. His <a href="http://github.com/ghoseb/">GitHub</a> a/c.
  </p>
  
  <p>
    It&#8217;s hard to pin point a few good tips because Clojure can do so many things in very nice and ingenious ways, that it&#8217;s not even funny. Anyway, here are a few:
  </p>
  
  <p>
    <b>Tip #1</b>: Sort a map on multiple keys:
  </p>
  
  <pre>
;;; Tip #1
;;; A vector of maps
(def some-maps [{:x 1 :y 2} {:x 2 :y 1} {:x 1 :y 4} {:x 2 :y 8}])

;;; Sort the maps first on &#58;x and then on :y

(defn sort-maps-by
  "Sort a sequence of maps (ms) on multiple keys (ks)"
  [ms ks]
  (sort-by #(vec (map % ks)) ms))

;;; (sort-maps-by some-maps [:x :y])
;;; output> ({:x 1, :y 2} {:x 1, :y 4} {:x 2, :y 1} {:x 2, :y 8})
</pre>
  
  <p>
    <b>Tip #2</b>: When dealing with infinite sequences on the REPL, you can set the number of items to be printed:
  </p>
  
  <pre>
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
</pre>
  
  <p>
    <b>Tip #3</b>: Use of the -> & ->> threading macros:
  </p>
  
  <p>
    The -> & ->> threading macros are very useful to sometimes untangle nested function calls. The -> macro takes a bunch of &#8216;forms&#8217; and &#8216;threads them&#8217; into each other by inserting every form as the second item of the next form and so on. So, (->> a (b c) (d e f) (g h)) becomes (g (d (b a c) e f) h). ->> is similar but it puts the form as the last item of the next form. (->> a (b c) (d e f) (g h)) then becomes (g h (d e f (b c a))).
  </p>
  
  <pre>
(ns tips
  ;; requires clojure 1.2 if you are on 1.1.x, use this instead
  ;; (:require [clojure.contrib.duck-streams :as io])
  (:require [clojure.contrib.io :as io]))

;;; Tip #3
;;; Use of the -> &#038; ->> threading macros.
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
</pre>
  
  <hr />
  
  <h3>
    Brian Carper
  </h3>
  
  <p>
    Find him on <a href="http://twitter.com/BrianCarper">Twitter</a>. His <a href="http://briancarper.net/">Blog</a>.
  </p>
  
  <p>
    &#8220;Named&#8221; or &#8220;keyword&#8221; arguments for functions have some benefits over positional arguments:
  </p>
  
  <ol>
    <li>
      You can specify arguments in any order.
    </li>
    <li>
      The arguments are named explicitly, resulting in less room for error compared to positional arguments, where it&#8217;s easy to transpose two arguments in the list.
    </li>
    <li>
      Your function can easily provide default argument values.
    </li>
  </ol>
  
  <p>
    For a function that takes only one or two arguments, keyword arguments might be overkill. But the benefits of keyword arguments quickly become more apparent the more argumentss your function accepts.
  </p>
  
  <p>
    Clojure doesn&#8217;t have canonical support for keyword arguments. But there are a couple of ways you can achieve the same result.
  </p>
  
  <p>
    The first is simply to force the user to pass a hash-map explicitly.
  </p>
  
  <pre>
(defn named-args-1 [foo argmap]
 (println "foo:" foo
          "bar:" (:bar argmap 0)
          "baz:" (:baz argmap 0))
 (println "bar-given?" (contains? argmap :bar)
          "baz-given?" (contains? argmap :baz)))

user> (named-args-1 1 {:baz 2})
foo: 1 bar: 0 baz: 2
bar-given? false baz-given? true
</pre>
  
  <p>
    But wrapping arguments in braces is arguably an unnecessary burden on users of your code. A better way is to use destructuring to allow the user to &#8220;flatten&#8221; the map:
  </p>
  
  <pre>
(defn named-args-2 [foo &#038; args]
 (let [argmap (apply hash-map args)
       {:keys [bar baz]
        &#58;or   {bar 0 baz 0}} argmap]
   (println "foo:" foo
            "bar:" bar
            "baz:" baz)
   (println "bar-given?" (contains? argmap :bar)
            "baz-given?" (contains? argmap :baz))))

user> (named-args-2 1 :baz 2)
foo: 1 bar: 0 baz: 2
bar-given? false baz-given? true
</pre>
  
  <p>
    This is OK for the user, but verbose for the function-writer. And the argument list for the function is specified as &#8220;args&#8221;, giving the user no clue as to what keys are expected or legal.
  </p>
  
  <p>
    As of recent releases of Clojure, you can do the destructuring right in the function&#8217;s argument list, leading to this version:
  </p>
  
  <pre>
(defn named-args-3 [foo &#038; {:keys [bar baz]
                          &#58;or   {bar 0 baz 0}
                          :as   argmap}]
 (println "foo:" foo
          "bar:" bar
          "baz:" baz)
 (println "bar-given?" (contains? argmap :bar)
          "baz-given?" (contains? argmap :baz)))

user> (named-args-3 1 :baz 2)
foo: 1 bar: 0 baz: 2
bar-given? false baz-given? true
</pre>
  
  <p>
    It&#8217;s also possible to roll your own macro to do keyword arguments. See <b>clojure.contrib.def/defnk</b>, for example.
  </p>
  
  <hr />
  
  <h3>
    Craig Andera
  </h3>
  
  <p>
    Find him on <a href="http://twitter.com/craigandera">Twitter</a>. His <a href="http://www.pluralsight-training.net/community/blogs/craig/">Blog</a>.
  </p>
  
  <p>
    I have two. The first one I stole from Mike Fogus: to use &#8220;,,,&#8221; as a placeholder in the <b>-></b> and <b>->></b> macros. Since commas are whitespace, they can be used as markers to indicate how the expressions flow through the threading macros. So, for instance, you can write:
  </p>
  
  <pre>
(->>
 (iterate inc 1)
 (map #(* 5 %) ,,,)
 (filter odd? ,,,))
</pre>
  
  <p>
    and the commas indicate &#8220;the previous expression will be inserted here&#8221;.
  </p>
  
  <p>
    It&#8217;s not something you should put in production code, but I found it enormously helpful in &#8220;getting&#8221; the -> and ->> macros. Honestly, I only had to write it out this way once or twice before it clicked with me and I stopped using the commas altogether.
  </p>
  
  <p>
    The other tip I have, has to do with understanding when to use <b>map</b>, <b>filter</b>, and <b>reduce</b>. These three functions are where an enormous amount of Clojure&#8217;s power comes from, but I find that beginners (such as myself) sometimes have a hard time selecting which one &#8211; or which combination &#8211; to use. What I&#8217;ve found is that it&#8217;s helpful to think of these in terms of what you *have* and what you *need*:
  </p>
  
  <ul>
    <li>
      If you *have* a sequence of length n and you *need* a sequence of length n, use <b>map</b>.
    </li>
    <li>
      If you *have* a sequence of length n and you *need* a shorter sequence, use <b>filter</b>.
    </li>
    <li>
      If you *have* a sequence of length n and you *need* a scalar, use <b>reduce</b>.
    </li>
  </ul>
  
  <p>
    It seems pretty obvious when stated like that, but it has been helpful to me on occasion when I start to get lost in how to express a particular algorithm.
  </p>
  
  <hr />
  
  <h3>
    Meikel Brandmeyer
  </h3>
  
  <p>
    Find him on <a href="http://twitter.com/kotarak">Twitter</a>. His <a href="http://bitbucket.org/kotarak">BitBucket Id</a>.
  </p>
  
  <p>
    Here is my tip on <b>atoms</b>.
  </p>
  
  <p>
    Clojure provides a lot of facilities to tackle the complexity of concurrent programming. But still you have to understand the semantics of the underlying facilities. One of these are <b>refs</b>, which allow coordinated access to several different entities at once. However, their use inflicts quite a bit of ceremony. You have to invoke the STM machinery whenever you want to write to a <b>ref</b> or want a consistent snapshot of several <b>refs</b>. Also your transaction is rolled back should a surrounding transaction retry. This is not always what you want.
  </p>
  
  <p>
    In such cases, it is interesting to use an <b>atom</b>. They are cheaper in terms of overhead and don’t interact with the STM. So the retry of a surrounding transaction doesn’t affect them. However they are uncoordinated: you can&#8217;t safely update multiple <b>atoms</b> at once.
  </p>
  
  <p>
    What is not so well known, is the fact, that <b>refs</b> also coordinate several accesses to the *same* <b>ref</b>. Again, this does *not* work well with <b>atoms</b>. Consider a cache, eg. for a <b>memoized</b> function.
  </p>
  
  <pre>
(defn memoize
 [f]
 (let [cache (atom {})]
   (fn [&#038; args]
     (when-not (contains? @cache args)
       (swap! cache assoc args (apply f args)))
     (get @cache args))))
</pre>
  
  <p>
    This code uses an <b>atom</b> and clojure datastructures, so we have no problems with concurrency, right? <b>Wrong!</b> There are plenty of race conditions between the different calls to <b>contains?</b>, <b>swap!</b> and <b>get</b>. In the example, the worst thing that can happen is that we compute the value of the function call several times. This can already be quite annoying if the call is expensive in computation time and/or resources. But consider a more involved cache implementation which could also remove entries from the cache. Then the call to <b>contains?</b> could see the value, but when we call get it might already be removed.
  </p>
  
  <p>
    The problem is, that we access the atom’s contents several times and this is not coordinated. Contrary to <b>refs</b> where we could call ensure to – well – ensure that the <b>ref</b> doesn’t change under our hands.
  </p>
  
  <p>
    How to solve this problem? Well, the problem is that we touch the <b>atom</b> several times. So the solution is to touch the <b>atom</b> only once!
  </p>
  
  <pre>
(defn memoize
 [f]
 (let [cache  (atom {})
       update (fn [state args]
                (if-not (contains? state args)
                  (assoc state args (apply f args))
                  state))]
   (fn [&#038; args]
     (get (swap! cache update args) args))))
</pre>
  
  <p>
    Here we do the contains check and update in one function which will see a consistent view of the cache state. Note that we also use the return value of the <b>swap!</b>. Otherwise we would again have to access to the atom several times!
  </p>
  
  <p>
    So while Clojure provides a lot of tools to tackle the problems of a concurrent world, you still have to understand what the semantics of the different tools are. And even then you have to carefully reason about your code. How it behaves. Where race conditions might hide. Life is not easy.
  </p>
  
  <p>
    <b>Note</b>: There are other problems to the above problem. Eg. doing expensive work – namely calling f – in a <b>swap!</b>. Please read <a href="http://kotka.de/blog/2010/03/memoize_done_right.html">Meikel&#8217;s blog post</a> on <b>memoize</b> where even more such considerations are taken into account.
  </p>
  
  <hr />
  
  <h3>
    Michael Fogus
  </h3>
  
  <p>
    Find him on <a href="http://twitter.com/fogus">Twitter</a>. His book <a href="http://fogus.me/">The Joy of Clojure</a>.
  </p>
  
  <p>
    Many macros that I write start exactly the same way:
  </p>
  
  <pre>
   (defmacro a-macro [&#038; forms]
     `'~forms)
</pre>
  
  <p>
    Then it proceeds to be transformed into a pipeline where each piece does a gradual transformation of forms:
  </p>
  
  <pre>
   (defn do-something [forms]
     (frobnicate forms))

   (defn do-something-else [forms]
     (moidilize forms))

   (defmacro a-macro [&#038; forms]
     (let [forms (do-something forms)
           forms (do-something-else forms)])
     `'~forms)
</pre>
  
  <p>
    This makes it easy to see the transformations occurring at each step, keeps my macros small, and allows me to put error handling in each of the transformation functions for compile-time exceptions.
  </p>
  
  <p>
    Although this is all pretty arcane as I try really really hard to avoid writing macros else I get beaten.
  </p>
  
  <hr />
  
  <h3>
    Michael Kohl
  </h3>
  
  <p>
    Find him on <a href="http://twitter.com/citizen428">Twitter</a>. His <a href="http://citizen428.net/">Blog</a>.
  </p>
  
  <p>
    My tip would be the <a href="http://clojure.org/reader">Clojure reader macro <b>#_</b></a> which completely ignores the next form. From the docs:
  </p>
  
  <p>
    &#8220;The form following <b>#_</b> is completely skipped by the reader. (This is a more complete removal than the <b>comment</b> macro which yields <b>nil</b>).&#8221;
  </p>
  
  <p>
    This can be immensely useful while debugging.
  </p>
  
  <hr />
  
  <h3>
    Nurullah Akkaya
  </h3>
  
  <p>
    Find him on <a href="http://twitter.com/nakkaya">Twitter</a>. His <a href="http://nakkaya.com/">Blog</a>.
  </p>
  
  <p>
    My tip would be on destructuring, which allows you to pull apart data structures into local bindings.
  </p>
  
  <pre>
     (let [[x y] [1 2]] 
       x)
     ;;user=> 1

     (let [[a b c] "abc"] 
       c)
     ;;user=> \c

     (let [[[x1 y1][x2 y2]] [[1 2] [3 4]]]
       [x1 y1 x2 y2])
     ;;user=> [1 2 3 4]
</pre>
  
  <p>
    Besides destructuring sequential things (vectors, lists, seqs, strings, arrays, or anything that supports nth), you can destructure maps as well:
  </p>
  
  <pre>
     (let [{key1 :key1 key2 :key2} {:key1 5 :key2 6}] 
       [key1 key2])
     ;;user=> [5 6]

     (let [{[x1 y1] :player1 [x2 y2] :player2} {:player1 [5 6] :player2 [9 9]}] 
       [x1 y1 x2 y2])
     ;;user=> [5 6 9 9]
</pre>
  
  <p>
    Most of the time, your local variables has the same names as the keywords, Clojure provides a shortcut that saves you from typing binding x keyword &#58;x over and over again:
  </p>
  
  <pre>
     (let [{:keys [key1 key2]} {:key1 5 :key2 6}] 
            [key1 key2])
     ;;user=> [5 6]
</pre>
  
  <p>
    For more on destructuring, checkout the <a href="http://clojure.org/special_forms#Special Forms--(let[bindings* ] exprs*">documentation</a>.
  </p>
  
  <hr />
  
  <h3>
    Ramakrishnan Muthukrishnan
  </h3>
  
  <p>
    Find him on <a href="http://twitter.com/vu3rdd">Twitter</a>. His <a href="http://github.com/vu3rdd">GitHub Id</a>.
  </p>
  
  <p>
    <b>Tip #1</b>:
  </p>
  
  <p>
    If you have a sequence and want to remove duplicates, there are (atleast) two ways to do it:
  </p>
  
  <pre>
(vec (into #{} [1 2 2 3 4 5])) ; => [1 2 3 4 5]
</pre>
  
  <p>
    or
  </p>
  
  <pre>
(distinct [1 2 2 3 4 5]) ; => [1 2 3 4 5]
</pre>
  
  <p>
    The second one is preferred.
  </p>
  
  <p>
    <b>Tip #2</b>:
  </p>
  
  <p>
    In a function, if you have a list of parameters, you can do the following:
  </p>
  
  <pre>
(defn foo [x &#038; xs]
 (...))
</pre>
  
  <p>
    The same can be done in anonymous functions too. What if you are using the abbreviated form (reader macro form) of an anonymous function? You can still use it by using the &#8220;%&&#8221; to denote the rest of the argument as a list. One example of the use of this form is shown <a href="http://www.bestinclass.dk/index.clj/2009/10/brians-functional-brain.html">here</a>.
  </p>
  
  <p>
    <b>Tip #3</b>: I echo Craig Andera&#8217;s opinions on <b>map</b>, <b>filter</b> and <b>reduce</b>. It is extremely important to master these three constructs. Especially, the way <b>reduce</b> can be used with hash-maps.
  </p>
  
  <p>
    <b>Tip #4</b>: If you want to have default values for some of the input parameters, one way is to define functions of diferent arity.
  </p>
  
  <pre>
(defn foo
 ([] (foo "bar"))
 ([s] (........)))
</pre>
  
  <p>
    Here, when &#8216;foo&#8217; is called without any arguments, we assume a default value of &#8220;bar&#8221;, a string as argument to the function and call foo with that argument.
  </p>
  
  <hr />
  
  <h3>
    Stuart Sierra
  </h3>
  
  <p>
    Find him on <a href="http://twitter.com/stuartsierra">Twitter</a>. His <a href="http://stuartsierra.com/">Blog</a>.
  </p>
  
  <p>
    Well, I&#8217;ve said this before, but it bears saying again: Don&#8217;t write a macro where a function will do. Functions are more flexible: they can be composed and passed as values. Do not use macros solely to make the syntax &#8220;prettier.&#8221;
  </p>
  
  <hr />
  
  <p class="alert">
    Do you like these tips? We are eager to know your reactions as comments to this post.
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Clojure" rel="tag">Clojure</a>, <a href="http://technorati.com/tag/Clojure+Tips" rel="tag">Clojure Tips</a>
