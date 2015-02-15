---
title: Ruby Matrix, the Forgotten Library
author: Matthew Kirk
date: 2013-04-04
layout: post
permalink: /2013/04/04/ruby-matrix-the-forgotten-library/
thesis_keywords:
  - Ruby, Programming, Matthew Kirk, Ruby Matrix
thesis_description:
  - Matrices can be useful to solve problems involving systems of equations. Matthew Kirk shows us how.
topsy_short_url:
  - http://bit.ly/ZaQOvG
categories:
  - Ruby
  - Ruby Masters
tags:
  - Matthew Kirk
  - programming
  - Ruby
  - Ruby Matrix
---
<div>
  <h2>
    Ruby Matrix, the Forgotten Library
  </h2>
  
  <p class="update">
    This guest post is contributed by <b>Matthew Kirk</b>, who is a partner at <a href='http://modulus7.com/' title='Modulus 7'>Modulus 7</a>, specializing in software development and strategy. The basis of his career has been around utilizing science to improve businesses. He has spoken at technology conferences around the world and in his spare time, he enjoys traveling and adding to his 2000+ vinyl record collection.
  </p>
  
  <p class="block">
    <img class="alignright" height="125" width="125" src="http://rubylearning.com/images/Matt_Kirk_small.jpg" alt="Matthew Kirk" /> <span class="drop_cap">R</span>emember matrices from math class? No not the movie, but the rectangular array of numbers. While you might not see it often, Ruby has a matrix implementation that is well tested and allows you to accomplish tough calculations quickly.
  </p>
  
  <p>
    While I won&#8217;t be able to teach you everything there is to be known about matrices, we will cover how to use matrices within Ruby as well as some quirks and their major selling points. By the end of this I hope that you delve deeper into learning about matrices and use them in your next project.
  </p>
  
  <h3>
    What are matrices?
  </h3>
  
  <p>
    A matrix according to Wikipedia is a rectangular array of numbers. Used heavily in math, matrices are all over languages like R and Matlab. They can be a great way to store numerical data and simplify many difficult and tedious problems. Instead of solving systems of equations matrices can simplify these into one equation.
  </p>
  
  <p>
    In terms of how Ruby implements matrices, Ruby stores all matrix rows into one big array. The only requirement is that the arrays are of the same dimension. So for each row that is added to a matrix each one must be of the same size.
  </p>
  
  <p>
    Just like arrays, matrices are zero indexed meaning that the first row is index 0 and the first column is index 0. Unlike arrays though you have to have two indexes to get to an element:
  </p>
  
  <p>
  </p>
  
  <h4>
    Making matrices:
  </h4>
  
  <p>
  </p>
  
  <h4>
    Some quirks:
  </h4>
  
  <p>
    The <code>Matrix</code> library has some quirks. The <code>Matrix</code> class allows non-numerical data to go into itself. This could be useful for storing things like symbols in a more x, y format but render most of the matrix functions useless.
  </p>
  
  <p>
    For instance:
  </p>
  
  <p>
  </p>
  
  <p>
    Another quirk to be aware of: <code>Matrix[*rows]</code> does not copy the rows objects but instead points to it. To avoid this use <code>Matrix.rows(rows)</code> or <code>Matrix.columns(columns)</code>. Implementation wise <code>Matrix[*rows]</code> calls the function <code>Matrix.rows(rows, copy = false)</code>.
  </p>
  
  <h4>
    Iterating over matrices:
  </h4>
  
  <p>
    How do you iterate over a matrix? Most likely you would think that matrices read left to right top to bottom. And that’s true. But there are other cases as well.
  </p>
  
  <p>
    In total there are 7 ways to iterate over a Matrix in ruby:
  </p>
  
  <ul>
    <li>
      <code>:all</code> This reads left to right top to bottom. This is the default case when you type <code>matrix.each</code>
    </li>
    <li>
      <code>:diagonal</code>: This only reads the diagonal elements or row index == column index
    </li>
    <li>
      <code>&#58;off_diagonal</code>: This will read everything not on the diagonal or row index != column index
    </li>
    <li>
      <code>&#58;lower</code>: This reads the lower triangle of the matrix or row index <= column index
    </li>
    <li>
      <code>:strict_lower</code>: this is more strict and reads only row index < column index
    </li>
    <li>
      <code>:strict_upper</code>: this is a strict upper triangle and is row index > column index
    </li>
    <li>
      <code>:upper</code>: row index >= column index
    </li>
  </ul>
  
  <p>
    An example:
  </p>
  
  <p>
  </p>
  
  <h4>
    Example: Parabola with matrix:
  </h4>
  
  <p>
    Imagine you want to fit a curve through three points. If you remember math class you might remember that you can do this by fitting a quadratic. For instance lets say we want a line that goes through (1,2) (3, 5.5) and (6, 6). To solve this we would write the equations:
  </p>
  
  <p>
    <img src="http://rubylearning.com/images/mathe1.jpg" alt="Math equation" />
  </p>
  
  <p>
    The way to solve this would usually involve lots of algebra and substitutions. While it&#8217;s easy to solve this in the case where we already know the numbers it is difficult to come up with a general solution (try it I dare you).
  </p>
  
  <p>
    Instead of worrying about solving this using non-matrix algebra we can solve it using matrix algebra. The first step is to rewrite the above system into this form:
  </p>
  
  <p>
    <img src="http://rubylearning.com/images/mathe2.jpg" alt="Math equation" />
  </p>
  
  <p>
    To make it even easier to solve we would rewrite this as Ax = b. To solve this we would take the inverse of A and then multiply both sides by that. Which would yield:
  </p>
  
  <p>
    <img src="http://rubylearning.com/images/mathe3.jpg" alt="Math equation" />
  </p>
  
  <p>
    Now that we know this, we can easily solve this using Ruby with the following formula.
  </p>
  
  <p>
  </p>
  
  <p>
    While it&#8217;s close it won&#8217;t be correct unless you use <code>Rational</code>. Ruby&#8217;s matrix library graciously utilizes functions that preserve precision. You would expect most libraries to convert to floats but ruby does not.
  </p>
  
  <p>
    For instance you can change the above function call to:
  </p>
  
  <p>
  </p>
  
  <p>
    Whenever possible try to preserve the precision!
  </p>
  
  <h4>
    The general case, fitting an n-power polynomial to n points:
  </h4>
  
  <p>
    Up above we only fit this curve to 3 points. But what about 4 or 15 points? This would be quite simple to do and would only require a little bit of modification:
  </p>
  
  <p>
  </p>
  
  <h3>
    Conclusion:
  </h3>
  
  <p>
    While you might not use matrices every day, they can be useful to solve problems involving systems of equations. Ruby has a robust <code>matrix</code> library that can be useful in finding solutions to these types of problems. Next time you want to fit a curve keep in mind matrices might be the best way to go!
  </p>
  
  <p>
    For more information about matrices I recommend reading Wikipedia articles. There are lots of math professors who spend hours updating them tediously. If they are too confusing, think about picking up a book on matrix algebra like <a href="http://ow.ly/jJ9JA">Matrix Computations</a>.
  </p>
  
  <p>
    <em><b>Feel free to ask questions and give feedback in the comments section of this post</b>. Thanks!</em>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Programming" rel="tag"> Programming</a>, <a href="http://technorati.com/tag/Matthew+Kirk" rel="tag"> Matthew Kirk</a>, <a href="http://technorati.com/tag/Ruby+Matrix" rel="tag"> Ruby Matrix</a>
