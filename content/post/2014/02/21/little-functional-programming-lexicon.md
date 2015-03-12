---
title: Little Functional Programming Lexicon
author: Elise Huard
date: 2014-02-21
layout: post
permalink: /2014/02/21/little-functional-programming-lexicon/
thesis_description:
  - Elise Huard explains functional programming in simple terms. A guest post on RubyLearning.
thesis_keywords:
  - Functional Programming, Elise Huard
topsy_short_url:
  - http://bit.ly/1jUgBks
categories:
  - Beginners
  - General
tags:
  - Elise Huard
  - Functional Programming
---
<div>
  <p class="update">
    This guest post is by <strong>Elise Huard</strong>, who is working as a freelance software engineer. She has 15 years of software under her belt and is keen on providing experienced advice as well as coding help. She has programmed in Ruby for 6 years before turning to Clojure and Haskell, and enjoys exploring the world of functional programming. She lives in Berlin, Germany with her family.
  </p>

  <p class="block">
    <img class="alignright" alt="Elise Huard" src="http://rubylearning.com/images/elisehuard.jpg" width="125" height="167" /> <span class="drop_cap">W</span>ith Clojure, Scala and Haskell on the scene, functional programming is getting a lot of attention. I’m going to explain some terms that are related to functional programming, to help you understand, and – who knows – nod intelligently random discussions you read or overhear.
  </p>

  <p>
    This is meant to be a little “Don’t panic” lexicon, not going incredibly in-depth but trying to describe the terms in as simple and friendly a way as possible. To know more, I invite you to read up on the concepts, but I hope this’ll get you started.
  </p>

  <h3>
    <a name="clojure"></a>Closure
  </h3>

  <p>
    A closure is a function that “stores” the surrounding scope. An example in javascript to make this clearer:
  </p><figure class="code"><figcaption></figcaption></p>

  <div class="highlight">
    <table>
      <tr>
        <td class="gutter">
          <pre class="line-numbers"><span class="line-number">1</span>
<span class="line-number">2</span>
<span class="line-number">3</span>
<span class="line-number">4</span>
<span class="line-number">5</span></pre>
        </td>

        <td class="code">
          <pre><code class="javascript"><span class="line">  <span class="kd">function</span> <span class="nx">multiplier</span><span class="p">(</span><span class="nx">factor</span><span class="p">)</span> <span class="p">{</span>
</span><span class="line">    <span class="k">return</span> <span class="kd">function</span><span class="p">(</span><span class="nx">otherFactor</span><span class="p">)</span> <span class="p">{</span>
</span><span class="line">      <span class="k">return</span> <span class="nx">factor</span><span class="o">*</span><span class="nx">otherFactor</span><span class="p">;</span>
</span><span class="line">    <span class="p">}</span>
</span><span class="line">  <span class="p">}</span>
</span></code></pre>
        </td>
      </tr>
    </table>
  </div></figure>

  <p>
    The function multiplier returns another function, which will multiply any given number with the argument <em>factor</em>.
  </p>

  <p>
    The function that is returned by this function “closes” over <em>factor</em> – that is it will retain the factor variable information even though it is no longer in the scope of the multiplier function. Every number that is fed to the returned function will be multiplied by <em>factor</em>.
  </p>

  <p>
    In this example we used an argument of the surrounding scope, but it could also be any other variable in the function scope.
  </p>

  <h3>
    <a name="currying"></a>Currying
  </h3>

  <p>
    You have a function that takes several arguments – currying allows you to apply one or more of these arguments and return a new function which takes the remaining arguments. Applying one of the argument is called <em>partial application</em>.
  </p>

  <p>
    In some programming languages, this is a very easy operation
  </p><figure class="code"><figcaption>haskell currying</figcaption></p>

  <div class="highlight">
    <table>
      <tr>
        <td class="gutter">
          <pre class="line-numbers"><span class="line-number">1</span>
<span class="line-number">2</span></pre>
        </td>

        <td class="code">
          <pre><code class="haskell"><span class="line"><span class="nf">plusThree</span> <span class="ow">=</span> <span class="p">(</span><span class="o">+</span><span class="mi">3</span><span class="p">)</span>
</span><span class="line"><span class="nf">plusThree</span> <span class="mi">5</span> <span class="c1">-- 8</span>
</span></code></pre>
        </td>
      </tr>
    </table>
  </div></figure>

  <p>
    in some others, it’s a little more work syntactically, but it’s possible
  </p><figure class="code"><figcaption>javascript currying</figcaption></p>

  <div class="highlight">
    <table>
      <tr>
        <td class="gutter">
          <pre class="line-numbers"><span class="line-number">1</span>
<span class="line-number">2</span>
<span class="line-number">3</span>
<span class="line-number">4</span>
<span class="line-number">5</span></pre>
        </td>

        <td class="code">
          <pre><code class="javascript"><span class="line"><span class="kd">function</span> <span class="nx">plusThree</span><span class="p">(</span><span class="nx">x</span><span class="p">)</span> <span class="p">{</span>
</span><span class="line">  <span class="k">return</span> <span class="kd">function</span><span class="p">(</span><span class="nx">x</span><span class="p">)</span> <span class="p">{</span>
</span><span class="line">    <span class="k">return</span> <span class="nx">x</span><span class="o">+</span><span class="mi">3</span><span class="p">;</span>
</span><span class="line">  <span class="p">}</span>
</span><span class="line"> <span class="p">}</span>
</span></code></pre>
        </td>
      </tr>
    </table>
  </div></figure>

  <h3>
    <a name="higher-order-functions"></a>Higher Order Functions
  </h3>

  <p>
    In functional languages functions are first-class citizens. You use them more or less as you would use any other type of value (I say more or less, because establishing equality of two functions is not possible, you cannot compare 2 functions as you would some other types).
  </p>

  <p>
    Higher order functions act on this concept, and either:
  </p>

  <ul>
    <li>
      take one or more functions as arguments – one example is map or filter.
    </li>
    <li>
      return a function (like some of the earlier examples in <a href="#currying">currying</a> and <a href="#closure">closures</a>) which can then be used in later operations.
    </li>
  </ul>

  <h3>
    <a name="hindley-milner"></a>Hindley-Milner Type system
  </h3>

  <p>
    <a href="http://en.wikipedia.org/wiki/Hindley%E2%80%93Milner_type_system">The Hindley-Milner type system</a> is the name of a type system for the <a href="#lambda-calculus">lambda calculus</a>, which comes with a fast type inference algorithm. It’s called Hindley-Milner because it was independently described by first Roger Hindley, then Robin Milner.
  </p>

  <p>
    Type inference means you don’t have to specify the type of every single variable or function (as is the case in java or C), because the compiler will infer the type for you, which will save a lot of typing and makes it nicer to read.
  </p>

  <p>
    The H-M type system is used in Haskell and ML type languages (like OCaml).
  </p>

  <h3>
    <a name="homoiconicity"></a>Homoiconicity
  </h3>

  <p>
    <a href="http://en.wikipedia.org/wiki/Homoiconicity">Homoiconicity</a> means that the abstract syntax tree has the same structure as the program. Going from one to the other is a straightforward conversion.
  </p>

  <p>
    Another property of homoiconic languages is that the program representation is also a data structure in the language.<br /> Example below, for Clojure: every expression is also a list (which is why it’s a Lisp-like language, LISP = LISt Processing)
  </p><figure class="code"><figcaption></figcaption></p>

  <div class="highlight">
    <table>
      <tr>
        <td class="gutter">
          <pre class="line-numbers"><span class="line-number">1</span>
<span class="line-number">2</span></pre>
        </td>

        <td class="code">
          <pre><code class="clojure"><span class="line">  <span class="p">(</span><span class="kd">defn </span><span class="nv">addTwo</span> <span class="p">[</span><span class="nv">x</span><span class="p">]</span> <span class="p">(</span><span class="nb">+ </span><span class="nv">x</span> <span class="mi">2</span><span class="p">))</span>
</span><span class="line">  <span class="p">(</span><span class="nf">addTwo</span> <span class="mi">5</span><span class="p">)</span>
</span></code></pre>
        </td>
      </tr>
    </table>
  </div></figure>

  <p>
    The advantage of homoiconicity is that code = data. You can manipulate your program as if it were data, since it’s effectively a data structure already.<br /> Homoiconicity is used in lisp-like languages to allow powerful macros – anything that lisp can do to data structures, lisp macros can do to lisp code. Move over ruby DSL metaprogramming!
  </p>

  <h3>
    <a name="immutability"></a>Immutability
  </h3>

  <p>
    Strictly speaking <em>not</em> a property of functional programming, though it is a corrollary of purity. If your function can not change the state of the program, variables will be immutable. Say adding an element of a list will take a list as an argument and return another list, which is the same but with the element added.
  </p>

  <p>
    This may seem like a dreadful waste of memory (especially when the data structures/objects are large), but in functional programming languages there are often optimizations under the hood which will re-use the existing data structures.
  </p>

  <p>
    Immutability is considered an advantage when working in concurrent programs. There is no danger that the data you’re currently working on will be changed while you’re working on it, since it’s immutable. Then there are strategies of reconciliation to work out which function output will win.
  </p>

  <h3>
    <a name="impure"></a>Impure
  </h3>

  <p>
    Impure programming languages allow <a href="#side-effects">side-effects</a> in the code without pointing them out with loud syntactic claxons.
  </p>

  <p>
    The difference between a pure and an impure programming language is that in a pure programming language, it’s made very explicit when a function has side effects, and which kind, and that it’s impossible to confuse functions doing side-effecting with pure functions.
  </p>

  <p>
    Popular impure functional programming languages are Clojure and Lisps, OCaml, with Scala and Javascript in their own category since they implement both functional and object-oriented paradigm.
  </p>

  <h3>
    <a name="lambda"></a>Lambda
  </h3>

  <p>
    greek letter ?, used (in the functional programming context) to refer to:
  </p>

  <ol>
    <li>
      <a href="#lambda-calculus">lambda calculus</a>
    </li>
    <li>
      an anonymous function – a function which is used immediately and doesn’t need naming for further reference, for instance being passed in as an argument to a <a href="#higher-order-function">higher order function</a> (like filter, map, etc).
    </li>
  </ol>

  <h3>
    <a name="lambda-calculus"></a>Lambda calculus
  </h3>

  <p>
    <a href="http://en.wikipedia.org/wiki/Lambda_calculus">?-calculus</a>, Wikipedia says, is a formal system for expressing computation based on function abstraction and application using variable binding and substitution. Lambda calculus is a universal model of computation (one can express anything a Turing machine can do in lambda calculus).
  </p>

  <p>
    <strong>Should you know the details of lambda calculus to do functional programming?</strong>
  </p>

  <p>
    No, unless you’re really interested in the mathematical underpinnings of functional programming, have some time and aren’t afraid to spend some time reading with pen and paper scribbling mathematical formulas.
  </p>

  <h3>
    <a name="lazy"></a>Lazy
  </h3>

  <p>
    Lazy evaluation (so not lazy like lying on the couch) is strictly speaking independent of functional programming. It means that an expression is only evaluated when the resulting value is used or displayed. So you could have lazy evaluation in imperative languages.
  </p>

  <p>
    I mention it in this little lexicon because lazy evaluation was actually introduced for the <a href="#lambda-calculus">lambda calculus</a>, and Clojure and Haskell (especially the latter) have plenty of lazily evaluated functions in their standard library.
  </p>

  <p>
    Advantages:
  </p>

  <ul>
    <li>
      being able to create infinite list or series, and you only evaluate elements as you need them
    </li>
    <li>
      only evaluate the part of a conditional structure that needs evaluated (so in Ruby, if – else is actually lazily evaluated)
    </li>
    <li>
      sometimes performance gains by avoiding unnecessary calculations
    </li>
  </ul>

  <h3>
    <a name="monads"></a>Monads (et Al.)
  </h3>

  <p>
    There are numerous text and blog posts about what monads are, some of them crystal clear and some of them slightly obfuscating the concepts.<br /> Here’s the thing though: unless you’re doing Haskell or similar <em>statically typed <a href="“#purity”">pure</a> functional languages</em>, you don’t really need to know what they are.
  </p>

  <p>
    In short:
  </p>

  <ol>
    <li>
      monads allow people to bundle in side-effects in a pure typed language (IO monad, state monad, etc). They have a type, which indicates which kind of side-effect they’re used for
    </li>
    <li>
      monads also have a number of mathematical properties and associated functions. Those functions are designed to let you daisy chain monad-handling functions or to change ordinary functions to handle monads.
    </li>
  </ol>

  <p>
    Other terms you might hear: Monoids, Functors, Applicative, … these are also only really necessary in the context of Haskell and company. Learning about them when you&#8217;re working in other types of languages might be interesting in the abstract, but is not essential to your everyday programming.
  </p>

  <h3>
    <a name="purity"></a>Purity
  </h3>

  <p>
    Purity can be used in two contexts: a pure programming language, and a pure function.
  </p>

  <p>
    Purity for a functional programming language means: <a href="#side-effects">side-effecting</a> has to be explicitly indicated, as is the case for Haskell (both in the function signature, usually returning <a href="#monads">monads</a>, and in the code).
  </p>

  <p>
    In pure functions, there are no ‘leaks’. A pure function’s <em>only</em> input are its arguments, and its <em>only</em> output is its return value(s). This brings us to <a href="#referentialtransparency">referential transparency</a>
  </p>

  <h3>
    <a name="referentialtransparency"></a>Referential Transparency
  </h3>

  <p>
    This is a property of pure functions – if you apply a function on a set of input, then it will <em>always</em> return the same output. This is due to the lack of side-effects (see <a href="#side-effects">side-effects</a> for explanation), which means no hidden parameters will change anything about the execution.
  </p>

  <p>
    As an example of a function that wouldn’t be referentially transparent, consider a function that would use a random number in its result. The random number (a side-effect) will change the result every time the function is run, so the function is not referentially transparent.
  </p>

  <p>
    <strong>why is this useful?</strong>
  </p>

  <p>
    Well, referentially transparent part of the program are dependable and easy to test. You only have to test on the sets of expected arguments without setting up any other state that could influence it, and it will reliably crank out the same output every time you run it.
  </p>

  <h3>
    <a name="side-effects"></a>Side Effects
  </h3>

  <p>
    Side effects are everything that can change the state of the world – that means the state of your program (outside of the scope of current function), or the standard output of your terminal, or a file, or database content.
  </p>

  <p>
    Let’s be clear, a program has to have side effects (if only displaying a result in the terminal), otherwise it has very little point. Let’s put it more strongly: the program’s sole reason of existence is to have some desired side-effects, like migrating a database, showing a web page, calculating some statistics and showing them to you
  </p>

  <p>
    I hope this was helpful and will give you some terms to be going on with! Welcome to the wonderful world of functional programming, I wish you all a pleasant journey!
  </p>

  <p class="alert">
    <em>Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Functional+Programming" rel="tag">Functional Programming</a>, <a href="http://technorati.com/tag/Elise+Huard" rel="tag"> Elise Huard</a>
