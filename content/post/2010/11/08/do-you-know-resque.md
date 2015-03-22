---
draft: false
title: Do YOU know Resque?
date: 2010-11-08
author: Dave Hoover
categories:
- Beginners
- Popular
- Ruby
- Ruby Masters
layout: post
permalink: /2010/11/08/do-you-know-resque/
tags:
- programming
- Resque
- ruby programming
---
This guest post is by **[Dave Hoover](http://redsquirrel.com/dave)**,
who authored the book [Apprenticeship Patterns: Guidance for the
Aspiring Software Craftsman](http://oreilly.com/catalog/9780596518387)
for O’Reilly, instigated the [Software Craftsmanship North America
conference](http://scna.softwarecraftsmanship.org/), and is the Chief
Craftsman at [Obtiva](http://obtiva.com). Dave began teaching himself to
program in 2000<!--more-->, back when he was a family therapist. Dave lives near
Chicago with his wife and three children. In his spare time, Dave
competes in endurance sports.

![Dave Hoover](http://rubylearning.com/images/davehoover.jpg) Web
developers can sometimes forget the importance of doing as little work
as possible during the HTTP request-response life-cycle. When we’re
developing new features, the simplest thing to do is just handle all the
work that has been requested before responding, making the user wait,
patiently watching their browser spin. This is nearly always a bad idea,
and for reasons beyond user experience, most notably, it ties up a web
process, making your site more likely to experience outages as traffic
spikes. While it often makes sense to develop features with slow
responses for your initial implementation, it’s usually unwise to deploy
that version of the feature to your production environment. Thankfully,
Ruby developers can choose from a number of “background job” libraries.
I’m going to introduce you to
[Resque](http://github.com/defunkt/resque), developed at
[Github](http://github.com/), built on top of
[Redis](http://code.google.com/p/redis/), an advanced key-value store
which Resque uses for queuing.

One nice thing about Resque is that it’s not dependant on Rails or any
web framework. This is great, because today, I’m not interested in
writing a web application. I want to write a fast-running Ruby program
that figures out what work needs to be done, tells someone else to do
it, and then exits. (Similar to a web request, but simpler.) I’ll start
with this:

{{< highlight ruby >}}
    idea = ARGV
    puts "Analyzing your idea: #{idea.join(" ")}"
    idea.each do |word|
      puts "Asking for a job to analyze: #{word}"
      # This is where we would enqueue something
    end
{{< /highlight >}}

If I named this program `idea_analyzer.rb` and it was in my current
working directory, I could run it like this:

{{< highlight bash >}}
    $ ruby idea_analyzer.rb I will learn ruby
    Analyzing your idea: I will learn ruby
    Asking for a job to analyze: I
    Asking for a job to analyze: will
    Asking for a job to analyze: learn
    Asking for a job to analyze: ruby
{{< /highlight >}}.

As you can see, this program takes an “idea” from the command line and
claims to ask for a “job” to analyze each word in the idea. Obviously,
the next step is to actually ask for that job, instead of just talking
about it. First, I’ll write the code that tells Resque to enqueue a job,
and then we’ll get Resque in place. That might seem backward to some of
you, since I’m writing code I know will fail, but “fast-failure” is a
technique I use all the time, whether I’m practicing [test-driven
development](http://en.wikipedia.org/wiki/Test-driven_development), or
learning a new technology with a toy problem like this:

{{< highlight ruby >}}
    idea = ARGV
    puts "Analyzing your idea: #{idea.join(" ")}"
    idea.each do |word|
      puts "Asking for a job to analyze: #{word}"
      Resque.enqueue(WordAnalyzer, word)
    end
{{< /highlight >}}.

Nice and simple. We’re calling a method on the Resque class. We’re
passing in the word, but we’re also passing in the class
`WordAnalayzer`. This is the only code that interacts directly with
Resque. The `enqueue` method takes the name of the class responsible for
doing the background work and the data required to accomplish the work,
in this case the `word` variable. It will attempt to place a job in the
appropriate queue. If we run the current version of this program, it
fails like this:

{{< highlight bash >}}.
    $ ruby idea_analyzer.rb I will learn ruby
    Analyzing your idea: I will learn ruby
    Asking for a job to analyze: I
    idea_analyzer.rb:5: uninitialized constant Resque (NameError)
        from /tmp/stuff.rb:3:in `each'
        from /tmp/stuff.rb:3
{{< /highlight >}}.

The `uninitialized constant Resque` error is telling me that Ruby
doesn’t know about Resque yet. I can fix that by installing the Resque
gem.

{{< highlight bash >}}
    $ gem install resque
    Successfully installed resque-1.10.0
    1 gem installed
    Installing ri documentation for resque-1.10.0...
    Installing RDoc documentation for resque-1.10.0...
{{< /highlight >}}

You’ll likely see other gems being installed as well, these are the gems
that Resque depends on. Now I’ll just tell our program about Resque:

{{< highlight ruby >}}
    require "resque"

    idea = ARGV
    puts "Analyzing your idea: #{idea.join(" ")}"
    idea.each do |word|
      puts "Asking for a job to analyze: #{word}"
      Resque.enqueue(WordAnalyzer, word)
    end
{{< /highlight >}}

When we run this, we’ll get a different error. Excellent! We’re making
progress.

{{< highlight bash >}}
    $ ruby idea_analyzer.rb I will learn ruby
    Analyzing your idea: I will learn ruby
    Asking for a job to analyze: I
    idea_analyzer.rb:7: uninitialized constant WordAnalyzer (NameError)
        from idea_analyzer.rb:5:in `each'
        from idea_analyzer.rb:5
{{< /highlight >}}

If you see an error like `no such file to load -- resque`, then you need
to add `require "rubygems"` at the top of your program. You should
eventually see the error about a missing `WordAnalyzer`. I’ll take care
of that next by creating a `word_analyzer.rb` file, defining the class…

{{< highlight ruby >}}
    class WordAnalyzer

    end
{{< /highlight >}}

…and then require it.

{{< highlight ruby >}}
    require "resque"
    require "word_analyzer"

    idea = ARGV
    puts "Analyzing your idea: #{idea.join(" ")}"
    idea.each do |word|
      puts "Asking for a job to analyze: #{word}"
      Resque.enqueue(WordAnalyzer, word)
    end
{{< /highlight >}}

And this fails with a different error, we’re almost there!

{{< highlight ruby >}}
    $ ruby idea_analyzer.rb I will learn ruby
    Analyzing your idea: I will learn ruby
    Asking for a job to analyze: I
    /my/gems/resque-1.10.0/lib/resque/job.rb:44:in `create': Jobs must be placed onto a queue. (Resque::NoQueueError)
        from /my/gems/resque-1.10.0/lib/resque.rb:206:in `enqueue'
        from idea_analyzer.rb:8
        from idea_analyzer.rb:6:in `each'
        from idea_analyzer.rb:6
{{< /highlight >}}

Now our problem is that we haven’t specified a queue for the
`WordAnalyzer` class. As its name suggests, Resque is all about queues.
Each Resque class, such as `WordAnalyzer`, can specify its default
queue, like this:

{{< highlight ruby >}}
    class WordAnalyzer
      @queue = "word_analysis"
    end
    {{< /highlight >}}

Re-running this results in:

{{< highlight bash >}}
    $ ruby idea_analyzer.rb I will learn ruby
    Analyzing your idea: I will learn ruby
    Asking for a job to analyze: I
    /my/gems/redis-2.0.10/lib/redis/client.rb:226:in `connect_to': Connection refused - Unable to connect to Redis on localhost:6379 (Errno::ECONNREFUSED)
{{< /highlight >}}

Resque is trying to enqueue a `WordAnalyzer` job for “I” on the
`word_analysis` queue, and is using the default host (localhost) and
port (6379). I’ll start Redis and our program should be much happier. I
recommend installing Redis via
[https://github.com/antirez/redis/archives/master](https://github.com/antirez/redis/archives/master)
with `antirez-redis-v2.0.3-stable-0-gb766149.zip`. Then starting it in a
new console with `redis-server`. With that running, you can rerun your
program and it should look like the output of the first version:

{{< highlight bash >}}
    $ ruby idea_analyzer.rb I will learn ruby
    Analyzing your idea: I will learn ruby
    Asking for a job to analyze: I
    Asking for a job to analyze: will
    Asking for a job to analyze: learn
    Asking for a job to analyze: ruby
{{< /highlight >}}

But this time, after its quick run, it has left some work behind,
sitting in Redis. You can see it if you type `resque-web` in your
console. This will launch a browser and bring up a little
[Sinatra](http://www.sinatrarb.com/) app that ships with Resque,
allowing you to watch the activity between Resque’s queues and workers.
Now that we can see 4 jobs waiting patiently in the `word_analysis`
queue, let’s get a worker started. The customary way to start Resque
workers is via Rake, so I’ll create a `Rakefile` beside my other 2 files
and just put this in the `Rakefile`:

{{< highlight ruby >}}
    require "word_analyzer"
    require "resque/tasks"
{{< /highlight >}}

Then, from the command line, I can start the worker with:

{{< highlight bash >}}
    $ rake resque:work QUEUE=*
{{< /highlight >}}

This will start a worker listening on all of Resque’s queues, and will
never exit. If you want to stop it, just hit CTRL-C. Once it has run for
a few seconds, refresh the browser you had pointing at resque-web,
click-through to the failure queue, and you’ll see all the jobs failed
with `undefined method 'perform' for WordAnalyzer:Class`. That’s a nice
way of telling us it’s time to write the `perform` method for our Resque
class:

{{< highlight ruby >}}
    class WordAnalyzer
      @queue = "word_analysis"

      def self.perform(word)
        puts "About to do heavy duty analysis on #{word}"
        sleep 3 # fake analysis here
        # this would be something impressive
        puts "Finished with analysis on #{word}"
      end
    end
{{< /highlight >}}

If your worker is still running, stop it with a CTRL-C. Then restart it
via Rake so it loads up our new `perform` method. As you’ve probably
guessed, Resque simply calls a method named `perform` on the class you
enqueue. Be aware that any arguments you pass into `Resque.enqueue` are
going to be serialized as [JSON](http://www.json.org/), which means Ruby
Symbols will turn into Strings, and complex objects like instances of
ActiveRecord will not work. When I need to work with ActiveRecords in
Resque, I just pass their ids across and re-query them from the
database.

Now that the worker is restarted and `WordAnalyzer` knows what to
perform, our background processing system is ready. Start a new console
and execute `ruby idea_analyzer.rb I will learn ruby`. Your Resque
worker should perform some “successful” analysis over the course of
about 12 seconds:

{{< highlight bash >}}
    $ rake resque:work QUEUE=*
    (in /Users/redsquirrel/Desktop)
    About to do heavy duty analysis on I
    Finished with analysis on I
    About to do heavy duty analysis on will
    Finished with analysis on will
    About to do heavy duty analysis on learn
    Finished with analysis on learn
    About to do heavy duty analysis on ruby
    Finished with analysis on ruby
{{< /highlight >}}

That’s all there is to it. You can keep running your `idea_analyzer.rb`
and the worker will keep analyzing words. Here is a visual workflow of
this little system that may help clarify the different roles:

![resque_workflow](http://rubylearning.com/images/resque_workflow.jpg)

We have a fast running program that queues work for later. We have a
simple class that performs a time-consuming job, managed by a
long-running Resque worker. We also have a web interface to monitor our
queues and workers. These are the building blocks used by large-scale
web sites like [Github](http://github.com/), [Mad
Mimi](http://madmimi.com/), and [Groupon](http://groupon.com/), who
leverage Resque for their mission critical background processing.

*I hope you found this article valuable. Feel free to ask questions and
give feedback in the comments section of this post. Thanks!*

***Do also read* these awesome Guest Posts:**

-   [Do You Understand Ruby’s Objects, Messages and Blocks?](/blog/2010/11/03/do-you-understand-rubys-objects-messages-and-blocks/)
-   [How Does One Use Design Patterns In Ruby?](/blog/2010/11/02/how-does-one-use-design-patterns-in-ruby/)
-   [Do you know what’s new in Ruby 1.9?](/blog/2010/10/26/do-you-know-whats-new-in-ruby-1-9/)
-   [The value of a personal bug log](/blog/2010/10/25/the-value-of-a-personal-bug-log/)
-   [Do You Enjoy Your Code Quality?](/blog/2010/10/18/do-you-enjoy-your-code-quality/)

