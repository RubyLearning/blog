---
draft: false
title: Little Functional Programming Lexicon
date: 2014-02-21
author: Elise Huard
categories:
- Beginners
- General
layout: post
permalink: /2014/02/21/little-functional-programming-lexicon/
tags:
- Elise Huard
- Functional Programming
---
This guest post is by **Elise Huard**, who is working as a freelance
software engineer. She has 15 years of software under her belt and is
keen on providing experienced advice as well as coding help. She has
programmed in Ruby for 6 years before turning to Clojure and Haskell,
and enjoys exploring the world of functional programming.<!--more-->
She lives in Berlin, Germany with her family.

![Elise Huard](/blog/media/elisehuard.jpg) With
Clojure, Scala and Haskell on the scene, functional programming is
getting a lot of attention. I’m going to explain some terms that are
related to functional programming, to help you understand, and – who
knows – nod intelligently random discussions you read or overhear.

This is meant to be a little “Don’t panic” lexicon, not going incredibly
in-depth but trying to describe the terms in as simple and friendly a
way as possible. To know more, I invite you to read up on the concepts,
but I hope this’ll get you started.

## Closure

A closure is a function that “stores” the surrounding scope. An example
in javascript to make this clearer:

<script src="https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/891ad0bfc9034f37b62cf28aad74d2b177e6c09e/2014/02/21/little-functional-programming-lexicon/javascript_sample_1.js?embed=t"></script>

The function multiplier returns another function, which will multiply
any given number with the argument *factor*.

The function that is returned by this function “closes” over *factor* –
that is it will retain the factor variable information even though it is
no longer in the scope of the multiplier function. Every number that is
fed to the returned function will be multiplied by *factor*.

In this example we used an argument of the surrounding scope, but it
could also be any other variable in the function scope.

## Currying

You have a function that takes several arguments – currying allows you
to apply one or more of these arguments and return a new function which
takes the remaining arguments. Applying one of the argument is called
*partial application*.

In some programming languages, this is a very easy operation

haskell currying

<script src="https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/bc067e4c977d26a83ec6a26c27f7d222e0117859/2014/02/21/little-functional-programming-lexicon/haskell_currying.hs?embed=t"></script>

in some others, it’s a little more work syntactically, but it’s possible

javascript currying

<script src="https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/bc067e4c977d26a83ec6a26c27f7d222e0117859/2014/02/21/little-functional-programming-lexicon/javascript_currying.js?embed=t"></script>

## Higher Order Functions

In functional languages functions are first-class citizens. You use them
more or less as you would use any other type of value (I say more or
less, because establishing equality of two functions is not possible,
you cannot compare 2 functions as you would some other types).

Higher order functions act on this concept, and either:

-   take one or more functions as arguments – one example is map or
    filter.
-   return a function (like some of the earlier examples in
    [currying](#currying) and [closures](#closure)) which can then be
    used in later operations.

## Hindley-Milner Type system

[The Hindley-Milner type
system](http://en.wikipedia.org/wiki/Hindley%E2%80%93Milner_type_system)
is the name of a type system for the [lambda
calculus](#lambda-calculus), which comes with a fast type inference
algorithm. It’s called Hindley-Milner because it was independently
described by first Roger Hindley, then Robin Milner.

Type inference means you don’t have to specify the type of every single
variable or function (as is the case in java or C), because the compiler
will infer the type for you, which will save a lot of typing and makes
it nicer to read.

The H-M type system is used in Haskell and ML type languages (like
OCaml).

## Homoiconicity

[Homoiconicity](http://en.wikipedia.org/wiki/Homoiconicity) means that
the abstract syntax tree has the same structure as the program. Going
from one to the other is a straightforward conversion.

Another property of homoiconic languages is that the program
representation is also a data structure in the language.
 Example below, for Clojure: every expression is also a list (which is
why it’s a Lisp-like language, LISP = LISt Processing)

<script src="https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/bc067e4c977d26a83ec6a26c27f7d222e0117859/2014/02/21/little-functional-programming-lexicon/lisp_example_1.lisp?embed=t"></script>

The advantage of homoiconicity is that code = data. You can manipulate
your program as if it were data, since it’s effectively a data structure
already.
Homoiconicity is used in lisp-like languages to allow powerful macros –
anything that lisp can do to data structures, lisp macros can do to lisp
code. Move over ruby DSL metaprogramming!

## Immutability

Strictly speaking *not* a property of functional programming, though it
is a corrollary of purity. If your function can not change the state of
the program, variables will be immutable. Say adding an element of a
list will take a list as an argument and return another list, which is
the same but with the element added.

This may seem like a dreadful waste of memory (especially when the data
structures/objects are large), but in functional programming languages
there are often optimizations under the hood which will re-use the
existing data structures.

Immutability is considered an advantage when working in concurrent
programs. There is no danger that the data you’re currently working on
will be changed while you’re working on it, since it’s immutable. Then
there are strategies of reconciliation to work out which function output
will win.

## Impure

Impure programming languages allow [side-effects](#side-effects) in the
code without pointing them out with loud syntactic claxons.

The difference between a pure and an impure programming language is that
in a pure programming language, it’s made very explicit when a function
has side effects, and which kind, and that it’s impossible to confuse
functions doing side-effecting with pure functions.

Popular impure functional programming languages are Clojure and Lisps,
OCaml, with Scala and Javascript in their own category since they
implement both functional and object-oriented paradigm.

## Lambda

greek letter λ used (in the functional programming context) to refer
to:

1.  [lambda calculus](#lambda-calculus)
2.  an anonymous function – a function which is used immediately and
    doesn’t need naming for further reference, for instance being passed
    in as an argument to a [higher order
    function](#higher-order-function) (like filter, map, etc).

## Lambda calculus

[λ-calculus](http://en.wikipedia.org/wiki/Lambda_calculus), Wikipedia
says, is a formal system for expressing computation based on function
abstraction and application using variable binding and substitution.
Lambda calculus is a universal model of computation (one can express
anything a Turing machine can do in lambda calculus).

**Should you know the details of lambda calculus to do functional
programming?**

No, unless you’re really interested in the mathematical underpinnings of
functional programming, have some time and aren’t afraid to spend some
time reading with pen and paper scribbling mathematical formulas.

## Lazy

Lazy evaluation (so not lazy like lying on the couch) is strictly
speaking independent of functional programming. It means that an
expression is only evaluated when the resulting value is used or
displayed. So you could have lazy evaluation in imperative languages.

I mention it in this little lexicon because lazy evaluation was actually
introduced for the [lambda calculus](#lambda-calculus), and Clojure and
Haskell (especially the latter) have plenty of lazily evaluated
functions in their standard library.

Advantages:

-   being able to create infinite list or series, and you only evaluate
    elements as you need them
-   only evaluate the part of a conditional structure that needs
    evaluated (so in Ruby, if – else is actually lazily evaluated)
-   sometimes performance gains by avoiding unnecessary calculations

## Monads (et Al.)

There are numerous text and blog posts about what monads are, some of
them crystal clear and some of them slightly obfuscating the concepts.
Here’s the thing though: unless you’re doing Haskell or similar
*statically typed [pure](“#purity”) functional languages*, you don’t
really need to know what they are.

In short:

1.  monads allow people to bundle in side-effects in a pure typed
    language (IO monad, state monad, etc). They have a type, which
    indicates which kind of side-effect they’re used for
2.  monads also have a number of mathematical properties and associated
    functions. Those functions are designed to let you daisy chain
    monad-handling functions or to change ordinary functions to handle
    monads.

Other terms you might hear: Monoids, Functors, Applicative, … these are
also only really necessary in the context of Haskell and company.
Learning about them when you’re working in other types of languages
might be interesting in the abstract, but is not essential to your
everyday programming.

## Purity

Purity can be used in two contexts: a pure programming language, and a
pure function.

Purity for a functional programming language means:
[side-effecting](#side-effects) has to be explicitly indicated, as is
the case for Haskell (both in the function signature, usually returning
[monads](#monads), and in the code).

In pure functions, there are no ‘leaks’. A pure function’s *only* input
are its arguments, and its *only* output is its return value(s). This
brings us to [referential transparency](#referentialtransparency)

## Referential Transparency

This is a property of pure functions – if you apply a function on a set
of input, then it will *always* return the same output. This is due to
the lack of side-effects (see [side-effects](#side-effects) for
explanation), which means no hidden parameters will change anything
about the execution.

As an example of a function that wouldn’t be referentially transparent,
consider a function that would use a random number in its result. The
random number (a side-effect) will change the result every time the
function is run, so the function is not referentially transparent.

**why is this useful?**

Well, referentially transparent part of the program are dependable and
easy to test. You only have to test on the sets of expected arguments
without setting up any other state that could influence it, and it will
reliably crank out the same output every time you run it.

## Side Effects

Side effects are everything that can change the state of the world –
that means the state of your program (outside of the scope of current
function), or the standard output of your terminal, or a file, or
database content.

Let’s be clear, a program has to have side effects (if only displaying a
result in the terminal), otherwise it has very little point. Let’s put
it more strongly: the program’s sole reason of existence is to have some
desired side-effects, like migrating a database, showing a web page,
calculating some statistics and showing them to you

I hope this was helpful and will give you some terms to be going on
with! Welcome to the wonderful world of functional programming, I wish
you all a pleasant journey!

*Feel free to ask questions and give feedback in the comments section of
this post. Thanks!*
