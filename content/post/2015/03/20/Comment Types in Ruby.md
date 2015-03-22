+++
title = "Comment Types in Ruby"
author = "Victor Goff"
authorlink = "http://twitter.com/kotp"
authorgoogleplus = "https://plus.google.com/+VictorGoff/about"
authorlinkedin = "https://www.linkedin.com/in/vgoff"
authortwitter = "http://twitter.com/kotp"
date = "2015-03-20T01:15:34-04:00"
draft = false
nocomment = false
tags = ["basics", "ruby"]
categories = ["ruby"]
totop = true
+++
There are basically two types of comments in Ruby.  And they work the
same.<!--more-->

## The block comment
The comment block is created with the `=begin` and `=end` delimiters.
This looks like:

<script
src="https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/a4d5c34572559d8add34e6dfddbcdfb79bd4cf29/2015/03/20/comment-types-in-ruby/comment_block.rb?embed=t"></script>

It helps to make readable areas that are without extra marks.  And
wherever and whatever you write in those areas are not interpreted by
Ruby.

## The line comment
This is the simple comment where you place an octothorpe as the first
non-whitespace character of the line, and everything else written is
excluded from being interpreted by Ruby.  It is ignored. It looks like:

<script
src="https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/a4d5c34572559d8add34e6dfddbcdfb79bd4cf29/2015/03/20/comment-types-in-ruby/comment_in_line.rb?embed=t"></script>

## The in-line comment
The "baasically two types" part comes in when you comment code at the
end of a statement.

It looks like this:

<script
src="https://bitbucket.org/teamrubylearning/rubylearning-code-snippets/src/a4d5c34572559d8add34e6dfddbcdfb79bd4cf29/2015/03/20/comment-types-in-ruby/comment_line.rb?embed=t"></script>

## What comment style should you use and when?
What comment style you use depends on a few factors.

* Personal taste
* Team style guides
* The amount of commenting needed
  * a class or module comment may need quite a few lines of comments and
    may use the block  style
  * a method may need one or two lines and should be above that method
  * a clever line of code may need a small comment, so in-line comments
    may be appropriate
* Functional comments
  * may not give you a choice
    * `#!/usr/bin/env ruby`
* directive comments

That last one is dependent on what that means.  They exist usually to
assist a tool that is not your program, to do something useful.  The
first one that I can think of is the gem `rubocop`.  It has directives
that are comment based to allow you to forgive a style infraction.  It
may be more flexible in what is acceptable than the functional comment,
but still not include the ability to use all three styles.

### In Summary

So, the three styles of comments that are directly related to Ruby are;

1. Block Comment
2. Line Comment
3. In-line Comment

The comment that is system dependent is the "magic comment" on the first
line of some files that help them know that they are meant to be
'executable'.

Finally, not really a "Ruby Comment Style" but used by some gems are
what I call "directive comments" and may have rules all of their own.

Of course, the best code is code that doesn't rely on comments at
all.  But we still need them!  What is your comment style?

