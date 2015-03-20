+++
title = "Comment Types in Ruby"
author = "Victor Goff"
authorgoogleplus = "https://plus.google.com/+SatishTalim/about"
authorlinkedin = "https://www.linkedin.com/in/satishtalim"
authortwitter = "http://twitter.com/indianguru"
date = "2015-03-20T01:15:34-04:00"
draft = false
nocomment = false
tags = ["basics", "ruby"]
totop = true
+++
There are basically two types of comments in Ruby.  And they work the
same.<!--more-->

## The block comment
The comment block is created with the `=begin` and `=end` delimiters.
This looks like:

{{< highlight ruby >}}
=begin
The answer to Life, The Universe, and Everything.
=end
puts 42
{{< /highlight >}}

It helps to make readable areas that are without extra marks.  And
wherever and whatever you write in those areas are not interpreted by
Ruby.

## The line comment
This is the simple comment where you place an octothorpe as the first
non-whitespace character of the line, and everything else written is
excluded from being interpreted by Ruby.  It is ignored. It looks like:

{{< highlight ruby >}}
# The answer to Life, The Universe, and Everything.
puts 42
{{< /highlight >}}


## The in-line comment
The "baasically two types" part comes in when you comment code at the
end of a statement.

It looks like this:

{{< highlight ruby >}}
puts "42" # The answer to Life, The Universe, and Everything.
{{< /highlight >}}

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

