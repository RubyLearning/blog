---
title: How does one effectively combine Ruby with Git for source control?
author: Erik Andrejko
categories:
  - Beginners
  - Ruby
  - Ruby Masters
date: 2010-11-24
layout: post
permalink: /2010/11/24/how-does-one-effectively-combine-ruby-with-git-for-source-control/
tags:
  - Git
  - programming
  - ruby programming
---
This guest post is by **Erik Andrejko**, a software developer living in
San Francisco who spends his days working on web applications and
solving data mining and machine learning problems<!--more--> integrating Ruby,
Clojure and Java. When not spending time with his family, he blogs about
web development and user experience at
[railsillustrated.com](http://railsillustrated.com/) and can found on
Twitter at [@eandrejko](http://twitter.com/#!/eandrejko).

## Introduction

![Erik
Andrejko](http://rubylearning.com/images/ErikAndrejko.jpg "Erik Andrejko")

Source control is one of the primary tools of a developer’s toolbox and
can be one of the most powerful. Git is one of the most popular source
control systems used by Ruby developers and one of the most powerful
available. Following good Ruby development practices, such as good use
of unit tests, and disciplined code organization allow one to easily
make use of some of most powerful features of Git. With good habits,
Ruby and Git are a potent combination.

This article assumes some basic familiarity with Git concepts and
commands and discusses effective use of Git with Ruby projects. Git can
take some time to learn well, a good introduction can be found at
[gitref.org](http://gitref.org/) and the canonical comprehensive
reference can be found at [Pro Git](http://progit.org/book/).

## Use Feature Branches

Git is remarkably capable of creating separate development branches and
later merging those branches. A good developer can use this to their
advantage by using feature branches. A feature branch is a branch of the
codebase used to implement a single feature.

To create a feature branch in Git just create a branch:

```bash
git checkout -b feature
```

Once you get into the habit of using feature branches it is not uncommon
to have many of them simultaneously, so it is helpful to name the
feature branch with some descriptive name.

Doing your development work on a feature branch provides many benefits:

- You can develop the feature over time and switch back to the master
  branch at any time to have a known good version of the code.
- You can abandon the feature at any time without having to carefully
  revert a partial implementation.
- You can change your commits on the feature branch before committing
  them to the master branch.

When the feature is complete you can move the commits to the master
branch with either a `git merge`:

```bash
git checkout master
git merge feature
```

or alternatively with a `git rebase`, depending on how you prefer the
history to be maintained:

```bash
git checkout master
git rebase feature
```

When doing a merge, an additional commit will be created on the master
branch which will show that two branches have merged at that point. Thus
the history will forever reflect the existence of your feature branch.
Some developers prefer to avoid having these merge commits in the
history. To avoid these additional merge commits use `git rebase`
instead, which will move the commits from the feature branch onto the
master branch without creating an additional commit keeping the history
of the master branch linear.

## Rewrite to Keep Your Commits Clean

When using a feature branch it is generally a good practice to take the
opportunity to rewrite the commits before placing them on the master
branch. Generally, changing commits is often discouraged in Git and many
Git guides advise against changing history by rewriting commits. This is
good advice, as rewriting commits on a shared branch will cause
headaches for other developers. However, on your private feature branch
you can change any commits you like before they become published on the
master branch.

To rewrite your commits, from the `feature` branch use `git rebase` with
the `--interactive` flag:

```bash
git rebase --interactive master
```

which will start an interactive rebase. Using an interactive rebase will
enable you to:

- Merge commits together (known as squashing).
- Change the order of the commits.
- Change the content of commits and their messages.

Another important task before publishing your feature branch is to
ensure that all the unit tests pass after each commit. As we shall see
later, this will make it easier to use another powerful feature of Git.

## Ruby and Git play well together

There is one disadvantage to using feature branches instead of just
placing all commits on master: merge conflicts. Generally Git is very
adept of avoiding merge conflicts but some conflicts are unavoidable.

For example, suppose that on the feature branch we add the `has_coupon?`
method to the `User` class:

```ruby
class User
  def name
   @name
  end

  def has_coupon?
    !coupons.empty?
  end
end
```

If on the master branch, another developer were to also add a method to
`User` after the `name` method there will be a merge conflict when
merging or rebasing the feature branch onto the master branch. This type
of merge conflict often occurs when classes get large and are often
changed. o prevent this kind of conflict use Ruby modules to organize
the methods in the `User` class.

On the feature branch change the `User` object as follows:

```ruby
class User
  include CouponMethods

  def name
   @name
  end
end
```

and add a new file `coupon_methods.rb` containing the new methods:

```ruby
module CouponMethods
  def has_coupon?
    !coupons.empty?
  end
end
```

Since we have added a new file with we will likely avoid any merge
conflict if another new methods are added to `User` in the master
branch. Of course, if two developers both add `include` statements to
the top of the `User` class there will again be a merge conflict.
However fixing a conflict which involves only a single line is easier
than a conflict involving many lines of method definitions.

Ruby is flexible enough to use a pattern that guarantees no merge
conflicts. If we change `coupon_methods.rb` to:

```ruby
module CouponMethods
  def has_coupon?
    !coupons.empty?
  end
end
User.send(:include, CouponMethods)
```

then there *cannot* be a merge conflict as no two developers will change
the same file. Generally, it may not be a good practice to extend the
`User` object in this way. It does illustrate that Ruby can be made to
play very well with Git when the need arises.

Using submodules to extend classes in a unobtrustive way is particularly
useful when modifying third-party code. In these cases avoiding merge
conflicts is particularly important as it is usually more difficult to
resolve the conflict when the other developer is not readily available
to help or when test coverage is lacking. By modifying third-party code
in Ruby ouside of the original source files you can avoid the need to
resolve any merge conflicts when updating that third-party code.
Typically in these cases a good suite of units tests testing both the
original third part code and the modified code is essential to ensure
that the behavior of the updated third-party code with your changes
stays the same.

## When Something Goes Wrong

Bugs are inevitable and Git has several features designed to help
debugging. When a bug is discovered, the first place to look to find the
commit that introduces the bug is to use `git log` to look for modified
files and search for the obvious candidates.

The `git log --stat` command will show each commit message together with
a list of files modified by that commit.

```sh
git log --stat
```

If you want to isolate the output of `git log --stat` to a particular
subdirectory or file, you can provide a path:

```sh
git log --stat lib/
```

It is preferable to avoid adding bugs in the first place and Git has
some tools to help. In Ruby it is common to use descriptive method names
in place of comments in the source code. Commit messages provide an
alternative source of comments for each source file. To see the commits
which are responsible for the current state of every line of code in a
particular file use the `git blame` command.

```sh
git blame lib/user.rb
```


The first column of the output will be the SHA of the commit. To view
the commit message for this commit pass the SHA to `git log` which will
show the commit message at the top of the log:

```sh
git log 1d35a63e 
```

Often, the commit message will provide very useful information about the
intent behind a particular line of code.

Sometimes the source of a bug is not found in the expected place. In
this case finding the commit which introduces a bug can be difficult.
Fortunately git provides a tool which can be incredibly useful and is
guaranteed to find the commit which introduced the bug: `git bisect`.
The `git bisect` command is designed to perform a binary search of the
commit history to find the first ‘bad’ commit. To start a bisect,
checkout the commit which is known to contain the bug, mark this as
‘bad’, check out *any* commit known not to have the bug and mark this as
‘good':

```sh
git checkout known_bad_commit
git bisect start
git bisect bad
git checkout known_good_commit
git bisect good
```

After marking a commit as ‘good’, Git will start a binary search of the
commit history between the ‘good’ and ‘bad’ commit by checking out a
series of commits. After each checkout, mark the commit as ‘good’ or
‘bad’ with the `git bisect` command. Eventually Git will report the
first ‘bad’ commit along with its commit message. Once completing the
bisect you can restore Git to its original state by running
`git bisect reset`. Alternatively if you make a mistake marking a
particular commit or otherwise want to start over you can also use
`git bisect reset`.

Bisecting a long-range of commits can be time-consuming and fortunately
this process can be automated. If you are using good testing practices,
you will likely start after identifying the bug by adding a failing
test. You can use this failing test to run git bisect automatically
using `git bisect run`:

```sh
git checkout known_bad_commit
git bisect start
git bisect bad
git checkout know_good_commit
git bisect good
git bisect run ruby test/unit/unit_test.rb
```

Using `git bisect run` will checkout a series of commits and run
`ruby test/unit/unit_test.rb` after each checkout. If the test passes
the commit will be marked ‘good’, if it fails the commit will be marked
‘bad’. Assuming that you simply edit `test/unit/unit_test.rb` you may
run into trouble if any of the intermediate commits also change
`test/unit/unit_test.rb` as Git may not be able to resolve the conflict.
In this case, you can temporarily add the failing test to a new file
before using `git bisect run`.

It is should now be clear why it is important to keep the unit tests
running after each commit. If not, using `git bisect run` may find the
wrong commit.

Any program can be used with `git bisect run`, not just a Ruby test. For
some bugs it may not be possible to add a failing test because not
enough information about the source of the bug is known. In this case,
as long as the bug can be detected by some automated means you can still
use `git bisect run` to find it. To use any Ruby program with
`git bisect run` use the `exit` method to pass the correct state back to
Git. f the test passes: use `exit(0)` to exit the Ruby program and
indicate to `git bisect run` the commit is ‘good’, if the test fails use
`exit(1)` to exit the Ruby program and indicate to `git bisect run` that
the commit is bad.

Git bisect is one of the best features of Git and has been used to find
some difficult to trace bugs. Even better, by automating the search with
`git bisect run`, no matter where the bug was introduced, it will be
found.

*I hope you found this article valuable. Feel free to ask questions and
give feedback in the comments section of this post. Thanks!*

If you are new to Git then the [Using Git &
GitHub](http://rubylearning.com/blog/using-git-github-ebook/) eBook
would be useful to you.
