---
title: How does one effectively combine Ruby with Git for source control?
author: Erik Andrejko
date: 2010-11-24
layout: post
permalink: /2010/11/24/how-does-one-effectively-combine-ruby-with-git-for-source-control/
thesis_description:
  - Erik Andrejko shows us some of the common workflows and best features of git, making Ruby and git a powerful combination.
thesis_keywords:
  - Git,Programming,Ruby programming
topsy_short_url:
  - http://bit.ly/hGlCxx
categories:
  - Beginners
  - Ruby
  - Ruby Masters
tags:
  - Git
  - programming
  - ruby programming
---
<div>
  <h3>
    How does one effectively combine Ruby with Git for source control?
  </h3>
  
  <p class="update">
    This guest post is by <strong>Erik Andrejko</strong>, a software developer living in San Francisco who spends his days working on web applications and solving data mining and machine learning problems integrating Ruby, Clojure and Java. When not spending time with his family, he blogs about web development and user experience at <a href="http://railsillustrated.com/">railsillustrated.com</a> and can found on Twitter at <a href="http://twitter.com/#!/eandrejko">@eandrejko</a>.
  </p>
  
  <h3>
    Introduction
  </h3>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/ErikAndrejko.jpg" alt="Erik Andrejko" title="Erik Andrejko" /> <span class="drop_cap">S</span>ource control is one of the primary tools of a developer&#8217;s toolbox and can be one of the most powerful. Git is one of the most popular source control systems used by Ruby developers and one of the most powerful available. Following good Ruby development practices, such as good use of unit tests, and disciplined code organization allow one to easily make use of some of most powerful features of Git. With good habits, Ruby and Git are a potent combination.
  </p>
  
  <p>
    This article assumes some basic familiarity with Git concepts and commands and discusses effective use of Git with Ruby projects. Git can take some time to learn well, a good introduction can be found at <a href="http://gitref.org/">gitref.org</a> and the canonical comprehensive reference can be found at <a href="http://progit.org/book/">Pro Git</a>.
  </p>
  
  <h3>
    Use Feature Branches
  </h3>
  
  <p>
    Git is remarkably capable of creating separate development branches and later merging those branches. A good developer can use this to their advantage by using feature branches. A feature branch is a branch of the codebase used to implement a single feature.
  </p>
  
  <p>
    To create a feature branch in Git just create a branch:
  </p>
  
  <pre>git checkout -b feature
</pre>
  
  <p>
    Once you get into the habit of using feature branches it is not uncommon to have many of them simultaneously, so it is helpful to name the feature branch with some descriptive name.
  </p>
  
  <p>
    Doing your development work on a feature branch provides many benefits:
  </p>
  
  <ul>
    <li>
      You can develop the feature over time and switch back to the master branch at any time to have a known good version of the code.
    </li>
    <li>
      You can abandon the feature at any time without having to carefully revert a partial implementation.
    </li>
    <li>
      You can change your commits on the feature branch before committing them to the master branch.
    </li>
  </ul>
  
  <p>
    When the feature is complete you can move the commits to the master branch with either a <tt>git merge</tt>:
  </p>
  
  <pre>git checkout master
git merge feature
</pre>
  
  <p>
    or alternatively with a <tt>git rebase</tt>, depending on how you prefer the history to be maintained:
  </p>
  
  <pre>git checkout master
git rebase feature
</pre>
  
  <p>
    When doing a merge, an additional commit will be created on the master branch which will show that two branches have merged at that point. Thus the history will forever reflect the existence of your feature branch. Some developers prefer to avoid having these merge commits in the history. To avoid these additional merge commits use <tt>git rebase</tt> instead, which will move the commits from the feature branch onto the master branch without creating an additional commit keeping the history of the master branch linear.
  </p>
  
  <h3>
    Rewrite to Keep Your Commits Clean
  </h3>
  
  <p>
    When using a feature branch it is generally a good practice to take the opportunity to rewrite the commits before placing them on the master branch. Generally, changing commits is often discouraged in Git and many Git guides advise against changing history by rewriting commits. This is good advice, as rewriting commits on a shared branch will cause headaches for other developers. However, on your private feature branch you can change any commits you like before they become published on the master branch.
  </p>
  
  <p>
    To rewrite your commits, from the <tt>feature</tt> branch use <tt>git rebase</tt> with the <tt>--interactive</tt> flag:
  </p>
  
  <pre>git rebase --interactive master
</pre>
  
  <p>
    which will start an interactive rebase. Using an interactive rebase will enable you to:
  </p>
  
  <ul>
    <li>
      Merge commits together (known as squashing).
    </li>
    <li>
      Change the order of the commits.
    </li>
    <li>
      Change the content of commits and their messages.
    </li>
  </ul>
  
  <p>
    Another important task before publishing your feature branch is to ensure that all the unit tests pass after each commit. As we shall see later, this will make it easier to use another powerful feature of Git.
  </p>
  
  <h3>
    Ruby and Git play well together
  </h3>
  
  <p>
    There is one disadvantage to using feature branches instead of just placing all commits on master: merge conflicts. Generally Git is very adept of avoiding merge conflicts but some conflicts are unavoidable.
  </p>
  
  <p>
    For example, suppose that on the feature branch we add the <tt>has_coupon?</tt> method to the <tt>User</tt> class:
  </p>
  
  <pre><span style="color: #cc7833;">class</span> <span style="color: #6E9CBE; font-weight: bold;">User</span>
  <span style="color: #cc7833;">def</span> <span style="color: #ffc66d;">name</span>
   <span style="color: #D0D0FF;">@name</span>
  <span style="color: #cc7833;">end</span>

  <span style="color: #cc7833;">def</span> <span style="color: #ffc66d;">has_coupon?</span>
    !coupons.empty?
  <span style="color: #cc7833;">end</span>
<span style="color: #cc7833;">end</span>
</pre>
  
  <p>
    If on the master branch, another developer were to also add a method to <tt>User</tt> after the <tt>name</tt> method there will be a merge conflict when merging or rebasing the feature branch onto the master branch. This type of merge conflict often occurs when classes get large and are often changed. o prevent this kind of conflict use Ruby modules to organize the methods in the <tt>User</tt> class.
  </p>
  
  <p>
    On the feature branch change the <tt>User</tt> object as follows:
  </p>
  
  <pre><span style="color: #cc7833;">class</span> <span style="color: #6E9CBE; font-weight: bold;">User</span>
  include <span style="color: #6E9CBE; font-weight: bold;">CouponMethods</span>

  <span style="color: #cc7833;">def</span> <span style="color: #ffc66d;">name</span>
   <span style="color: #D0D0FF;">@name</span>
  <span style="color: #cc7833;">end</span>
<span style="color: #cc7833;">end</span>
</pre>
  
  <p>
    and add a new file <tt>coupon_methods.rb</tt> containing the new methods:
  </p>
  
  <pre><span style="color: #cc7833;">module</span> <span style="color: #6E9CBE; font-weight: bold;">CouponMethods</span>
  <span style="color: #cc7833;">def</span> <span style="color: #ffc66d;">has_coupon?</span>
    !coupons.empty?
  <span style="color: #cc7833;">end</span>
<span style="color: #cc7833;">end</span>
</pre>
  
  <p>
    Since we have added a new file with we will likely avoid any merge conflict if another new methods are added to <tt>User</tt> in the master branch. Of course, if two developers both add <tt>include</tt> statements to the top of the <tt>User</tt> class there will again be a merge conflict. However fixing a conflict which involves only a single line is easier than a conflict involving many lines of method definitions.
  </p>
  
  <p>
    Ruby is flexible enough to use a pattern that guarantees no merge conflicts. If we change <tt>coupon_methods.rb</tt> to:
  </p>
  
  <pre><span style="color: #cc7833;">module</span> <span style="color: #6E9CBE; font-weight: bold;">CouponMethods</span>
  <span style="color: #cc7833;">def</span> <span style="color: #ffc66d;">has_coupon?</span>
    !coupons.empty?
  <span style="color: #cc7833;">end</span>
<span style="color: #cc7833;">end</span>
<span style="color: #6E9CBE; font-weight: bold;">User</span>.send(<span style="color: #3182be;">:include</span>, <span style="color: #6E9CBE; font-weight: bold;">CouponMethods</span>)
</pre>
  
  <p>
    then there <em>cannot</em> be a merge conflict as no two developers will change the same file. Generally, it may not be a good practice to extend the <tt>User</tt> object in this way. It does illustrate that Ruby can be made to play very well with Git when the need arises.
  </p>
  
  <p>
    Using submodules to extend classes in a unobtrustive way is particularly useful when modifying third-party code. In these cases avoiding merge conflicts is particularly important as it is usually more difficult to resolve the conflict when the other developer is not readily available to help or when test coverage is lacking. By modifying third-party code in Ruby ouside of the original source files you can avoid the need to resolve any merge conflicts when updating that third-party code. Typically in these cases a good suite of units tests testing both the original third part code and the modified code is essential to ensure that the behavior of the updated third-party code with your changes stays the same.
  </p>
  
  <h3>
    When Something Goes Wrong
  </h3>
  
  <p>
    Bugs are inevitable and Git has several features designed to help debugging. When a bug is discovered, the first place to look to find the commit that introduces the bug is to use <tt>git log</tt> to look for modified files and search for the obvious candidates.
  </p>
  
  <p>
    The <tt>git log --stat</tt> command will show each commit message together with a list of files modified by that commit.
  </p>
  
  <pre>git log --stat
</pre>
  
  <p>
    If you want to isolate the output of <tt>git log --stat</tt> to a particular subdirectory or file, you can provide a path:
  </p>
  
  <pre>git log --stat lib/
</pre>
  
  <p>
    It is preferable to avoid adding bugs in the first place and Git has some tools to help. In Ruby it is common to use descriptive method names in place of comments in the source code. Commit messages provide an alternative source of comments for each source file. To see the commits which are responsible for the current state of every line of code in a particular file use the <tt>git blame</tt> command.
  </p>
  
  <pre>git blame lib/user.rb
</pre>
  
  <p>
    The first column of the output will be the SHA of the commit. To view the commit message for this commit pass the SHA to <tt>git log</tt> which will show the commit message at the top of the log:
  </p>
  
  <pre>git log 1d35a63e
</pre>
  
  <p>
    Often, the commit message will provide very useful information about the intent behind a particular line of code.
  </p>
  
  <p>
    Sometimes the source of a bug is not found in the expected place. In this case finding the commit which introduces a bug can be difficult. Fortunately git provides a tool which can be incredibly useful and is guaranteed to find the commit which introduced the bug: <tt>git bisect</tt>. The <tt>git bisect</tt> command is designed to perform a binary search of the commit history to find the first &#8216;bad&#8217; commit. To start a bisect, checkout the commit which is known to contain the bug, mark this as &#8216;bad&#8217;, check out <em>any</em> commit known not to have the bug and mark this as &#8216;good':
  </p>
  
  <pre>git checkout known_bad_commit
git bisect start
git bisect bad
git checkout known_good_commit
git bisect good
</pre>
  
  <p>
    After marking a commit as &#8216;good&#8217;, Git will start a binary search of the commit history between the &#8216;good&#8217; and &#8216;bad&#8217; commit by checking out a series of commits. After each checkout, mark the commit as &#8216;good&#8217; or &#8216;bad&#8217; with the <tt>git bisect</tt> command. Eventually Git will report the first &#8216;bad&#8217; commit along with its commit message. Once completing the bisect you can restore Git to its original state by running <tt>git bisect reset</tt>. Alternatively if you make a mistake marking a particular commit or otherwise want to start over you can also use <tt>git bisect reset</tt>.
  </p>
  
  <p>
    Bisecting a long-range of commits can be time-consuming and fortunately this process can be automated. If you are using good testing practices, you will likely start after identifying the bug by adding a failing test. You can use this failing test to run git bisect automatically using <tt>git bisect run</tt>:
  </p>
  
  <pre>git checkout known_bad_commit
git bisect start
git bisect bad
git checkout know_good_commit
git bisect good
git bisect run ruby test/unit/unit_test.rb
</pre>
  
  <p>
    Using <tt>git bisect run</tt> will checkout a series of commits and run <tt>ruby test/unit/unit_test.rb</tt> after each checkout. If the test passes the commit will be marked &#8216;good&#8217;, if it fails the commit will be marked &#8216;bad&#8217;. Assuming that you simply edit <tt>test/unit/unit_test.rb</tt> you may run into trouble if any of the intermediate commits also change <tt>test/unit/unit_test.rb</tt> as Git may not be able to resolve the conflict. In this case, you can temporarily add the failing test to a new file before using <tt>git bisect run</tt>.
  </p>
  
  <p>
    It is should now be clear why it is important to keep the unit tests running after each commit. If not, using <tt>git bisect run</tt> may find the wrong commit.
  </p>
  
  <p>
    Any program can be used with <tt>git bisect run</tt>, not just a Ruby test. For some bugs it may not be possible to add a failing test because not enough information about the source of the bug is known. In this case, as long as the bug can be detected by some automated means you can still use <tt>git bisect run</tt> to find it. To use any Ruby program with <tt>git bisect run</tt> use the <tt>exit</tt> method to pass the correct state back to Git. f the test passes: use <tt>exit(0)</tt> to exit the Ruby program and indicate to <tt>git bisect run</tt> the commit is &#8216;good&#8217;, if the test fails use <tt>exit(1)</tt> to exit the Ruby program and indicate to <tt>git bisect run</tt> that the commit is bad.
  </p>
  
  <p>
    Git bisect is one of the best features of Git and has been used to find some difficult to trace bugs. Even better, by automating the search with <tt>git bisect run</tt>, no matter where the bug was introduced, it will be found.
  </p>
  
  <p>
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
  
  <p class="note">
    If you are new to Git then the <a href="http://rubylearning.com/blog/using-git-github-ebook/">Using Git & GitHub</a> eBook would be useful to you.
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Git" rel="tag">Git</a>, <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>
