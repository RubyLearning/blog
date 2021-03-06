---
draft: false
title: 'Performance Testing Rails Applications: How To?'
date: 2011-08-14
author: "Gonçalo Silva"
categories:
- Ruby
- Ruby Masters
- Ruby on Rails
layout: post
permalink: /2011/08/14/performance-testing-rails-applications-how-to/
tags:
- programming
- Ruby on Rails
- ruby programming
topsy_short_url:
- http://bit.ly/pZKKcu
---

<div>
  <h2>
    Performance Testing Rails Applications: How To?
  </h2>
  
  <p class="update">
    This guest post is by <strong>Gonçalo Silva</strong>, who is a full-time Ruby on Rails developer at <a href="http://escolinhas.pt/">escolinhas.pt</a> and has participated in the Ruby Summer of Code 2010. He loves and contributes to many open-source projects, being a fan of Linux, Ruby and Android. He likes to call himself a hacker, but that&#8217;s just an excuse for being in front of the computer all the time. Oh, and he tweets at <a href="http://twitter.com/goncalossilva">@goncalossilva</a>.
  </p>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/Goncalo_Silva_125x125.jpg" alt="Gonçalo Silva" /> <span class="drop_cap">R</span>ails 3.1 is just around the corner, and it brings enhanced performance testing tools. Let&#8217;s have a look at this often overlooked feature of our web application framework of choice.
  </p>
  
  <h3>
    This isn&#8217;t new
  </h3>
  
  <p>
    Rails has had built-in performance testing tools since version 2.2. Originally developed by <a href="https://github.com/rails/rails/commit/eab71208db1afead6803501c8d51d77625e5ad6e">Jeremy Kemper</a>, these allowed developers to test the performance of their applications by writing integration tests which could be benchmarked and profiled under <em>MRI</em>. He later introduced two scripts &#8211; <code>benchmarker</code> and <code>profiler</code> &#8211; which were great to quickly benchmark or profile small snippets of code.
  </p>
  
  <h3>
    Actually, this is kind of new
  </h3>
  
  <p>
    I came across these tools during last year&#8217;s <em>Ruby Summer of Code</em>. I remember feeling astonished and bit ashamed about not having played with them before. I couldn&#8217;t use them at their full potential because of the lack of full support for <em>YARV</em> (or <em>MRI 1.9</em>), so I set off fixing that. While working on it, I&#8217;ve made a list of other things these tools lacked, that I wanted to implement after <em>RSoC</em>, namely: &#8211; <em>Rubinius</em> support &#8211; <em>JRuby</em> support &#8211; Test configurability &#8211; Decoupling <code>benchmarker</code> and <code>profiler</code> from <em>RubyProf</em>
  </p>
  
  <p>
    Everything listed above is now implemented. Rails 3.1 will ship with these improvements and we&#8217;ll no longer have excuses for not using these great tools Rails provides for all of us.
  </p>
  
  <h3>
    Why you should care
  </h3>
  
  <p>
    The web should be fast. Response times are a key factor in user experience and there is very limited patience for slow websites. Ruby interpreters aren&#8217;t famous for being performant and our beloved framework <a href="http://www.youtube.com/watch?v=kWOAHIpmLAI&feature=player_detailpage#t=2058s">isn&#8217;t known for getting faster with new releases</a>. Nevertheless, we want our websites to be fast and responsive, and buying tons of hardware isn&#8217;t always an available choice &#8211; we need our code to be fast. We <strong>should</strong> care.
  </p>
  
  <h3>
    How does this work?
  </h3>
  
  <p>
    Rails&#8217; performance testing tools allow you to quickly detect performance bottlenecks. As a rule of thumb, use benchmarking to detect the problem and then use profiling to understand it. Profiling provides in-depth information about your code and what it&#8217;s doing, but it lacks the speed and simplicity of benchmarking.
  </p>
  
  <h4>
    Patching your Ruby interpreter
  </h4>
  
  <p>
    You can skip this section if you&#8217;re a <em>Rubinius</em>/<em>JRuby</em>/<em>REE</em> user.
  </p>
  
  <p>
    If you&#8217;re an MRI/YARV user, you&#8217;ll need a patched interpreter to access all available metrics. Before you run off, let me tell you that it&#8217;s <strong>very</strong> simple to install a patched Ruby interpreter nowadays. Thanks to Wayne, the author of <em><a href="https://rvm.beginrescueend.com/">RVM</a></em>, all you need to do is to specify an additional flag when installing your interpreter, like this: <code>rvm install 1.9.2 --patch gcdata</code> Or, if you&#8217;re still using 1.8 (really?): <code>rvm install 1.8.7 --patch ruby187gc</code>
  </p>
  
  <p>
    That&#8217;s all, folks. You now have a patched Ruby interpreter. If you want, you can have your patched interpreter side by side with your regular one, by simply assigning a name to it:
  </p>
  
  <pre>rvm install 1.9.2 --patch gcdata --name perf
rvm 1.9.2-perf  # my patched interpreter
rvm 1.9.2       # my regular interpreter</pre>
  
  <p>
    And that&#8217;s it.
  </p>
  
  <h4>
    Editing your Gemfile
  </h4>
  
  <p>
    You can skip this section if you&#8217;re using <em>Rubinius</em>/<em>JRuby</em>.
  </p>
  
  <p>
    If you&#8217;re not, you&#8217;ll need to add <a href="http://github.com/wycats/ruby-prof/commits/master">RubyProf</a> to your <em>Gemfile</em>:
  </p>
  
  <pre>gem 'ruby-prof', :git =&gt; 'git://github.com/wycats/ruby-prof.git'</pre>
  
  <p>
    Don&#8217;t forget to remove this from your <em>Gemfile</em> and re-run <code>bundle install</code> if you intend to switch to <em>Rubinius</em> or <em>JRuby</em>.
  </p>
  
  <h4>
    Performance tests
  </h4>
  
  <p>
    In order to use these tools, you&#8217;ll need to write performance tests. These tests are just like integration tests, except that the point is not to assert anything. They&#8217;ll just run the code that you want to see benchmarked/profiled.
  </p>
  
  <h5>
    Generating
  </h5>
  
  <p>
    As expected, Rails does this stuff for you. Just run:
  </p>
  
  <pre>script/rails generate performance_test example</pre>
  
  <p>
    And a new file will be placed in <code>test/performance/example_test.rb</code> containing the default test:
  </p>
  
  <pre>require 'test_helper'
require 'rails/performance_test_help'
class ExampleTest &lt; ActionDispatch::PerformanceTest
  # Refer to the documentation for all available options
  # self.profile_options = { :runs =&gt; 5, :metrics =&gt; [:wall_time, :memory]
  #                          &#58;output =&gt; 'tmp/performance', :formats =&gt; [:flat] }

  def test_homepage
    get '/'
  end
end</pre>
  
  <h5>
    Editing
  </h5>
  
  <p>
    Since <code>ActionDispatch::PerformanceTest</code> inherits from <code>ActionDispatch::IntegrationTest</code>, you can use <a href="http://guides.rubyonrails.org/testing.html#helpers-available-for-integration-tests">all available helpers for integration tests</a> in your performance tests. For instance, if you wanted a test for your login action you could use:
  </p>
  
  <pre>class LoginTest &lt; ActionDispatch::PerformanceTest
  fixtures :users
  self.profile_options = { :metrics =&gt; [:wall_time, :memory] }

  def test_login
    post_via_redirect "/login", :username =&gt; users(:youruser).username, :password =&gt; users(:youruser).password
  end
end</pre>
  
  <h5>
    Tweaking
  </h5>
  
  <p>
    Starting with Rails 3.1, performance tests can be configured. As you&#8217;ve probably figured out from the aforeshown <code>LoginTest</code>, all you need to do is to specify an optional hash of options to use when benchmarking/profiling. You can use <strong>one set of options for each class</strong>. Not all options are available to all interpreters, especially the ones related with profiling. Metric/output availability for each interpreter will be shown below. You can skip this section and come back later, after grasping the whole concept. You&#8217;ll also be able to check it out on <a href="http://guides.rubyonrails.org/performance_testing.html">Rails&#8217; performance testing guide</a> once 3.1 comes out.
  </p>
  
  <h6>
    Metric availability
  </h6>
</div>

<div style="width: image 669 px;font-size: 80%;text-align: left">
  Benchmarking<br /> <img style="padding-bottom: 0.5em" src="http://rubylearning.com/images/Screen Shot 2011-08-14 at 2.58.31 AM.png" alt="Benchmarking" width="669" />
</div>

<div style="width: image 667 px;font-size: 80%;text-align: left">
  Profiling<br /> <img style="padding-bottom: 0.5em" src="http://rubylearning.com/images/Screen Shot 2011-08-14 at 2.58.53 AM.png" alt="Profiling" width="667" />
</div>

<div style="width: image 281 px;font-size: 80%;text-align: left">
  Output availability<br /> <img style="padding-bottom: 0.5em" src="http://rubylearning.com/images/Screen Shot 2011-08-14 at 2.59.20 AM.png" alt="Output availability" width="281" />
</div>

<div>
  <h5>
    Running
  </h5>
  
  <p>
    Finally, it&#8217;s time to run your tests. Let&#8217;s start with benchmarking:
  </p>
  
  <pre>rake test:benchmark</pre>
  
  <p>
    And the output should be similar to this:
  </p>
  
  <pre>ExampleTest:
ExampleTest#test_homepage (16 ms warmup)
           wall_time: 0 ms
              memory: 17 KB
             objects: 195
             gc_runs: 0
             gc_time: 0 ms
 homepage (0.75s)

LoginTest:
LoginTest#test_login (92 ms warmup)
           wall_time: 10 ms
              memory: 180 KB
 login (0.44s)

Finished in 1.193759 seconds.</pre>
  
  <p>
    If any result disappoints you, profile it:
  </p>
  
  <pre>rake test:profile TEST=test/performance/login_test.rb</pre>
  
  <p>
    And you should get a similar output:
  </p>
  
  <pre>LoginTest:
LoginTest#test_login (105 ms warmup)
           wall_time: 69 ms
              memory: 2.4 KB
 login (5.02s)</pre>
  
  <p>
    Profiling will give you much more information than what&#8217;s printed on your terminal.
  </p>
  
  <h5>
    Reviewing results
  </h5>
  
  <p>
    By default, performance tests store their results in <code>tmp/performance</code> (although it can be changed by specifying a value for <code>&#58;output</code> in the <code>profile_options</code> hash). For benchmarks, this is pretty straightforward: it stores one <em>CSV</em> per metric (<code>LoginTest#test_login_memory.csv</code>, for instance) with the results as time goes by.
  </p>
  
  <pre>measurement,created_at,app,rails,ruby,platform
183222,2011-08-10T18:15:09Z,,3.1.0.rc5,ruby-1.9.2.290,i686-linux
216344,2011-08-11T14:37:59Z,,3.1.0.rc5,ruby-1.9.2.290,i686-linux
(...)</pre>
  
  <p>
    When profiling, however, the result files are extremely important. They contain the juicy details of your test runs. Similarly to benchmarking results, there will be one file per metric. There are, however, multiple formats available, specially if you&#8217;re using RubyProf (and consequently <em>MRI</em>/<em>REE</em>/<em>YARV</em>). These formats can range from messy flat text files to awesome HTML stack traces, and they will provide valuable input when spotting bottlenecks.
  </p>
  
  <p>
    The scope of this article is not to explore RubyProf&#8217;s available output formats, but you should <a href="http://ruby-prof.rubyforge.org/">have a look at the available printers</a>. However, keep in mind that RubyProf supports more metrics and output formats than <em>Rubinius</em>/<em>JRuby</em>&#8216;s profilers. These can only measure wall time when profiling, and will only print their results in Flat/Graph text formats.
  </p>
</div>

<div style="width: image 686 px;font-size: 80%;text-align: center">
  <img style="padding-bottom: 0.5em" src="http://rubylearning.com/images/ruby-prof_html_stack_printer.png" alt="RubyProf's HTML stack printer" width="686" /><br /> RubyProf&#8217;s HTML stack printer
</div>

<div>
  <h4>
    Quick tests
  </h4>
  
  <p>
    Performance tests are great, but they can be inconvenient when all you want is to quickly test a small snippet of code. For this, Rails provides two command line tools: <code>benchmarker</code> and <code>profiler</code>.
  </p>
  
  <p>
    Open your terminal and run:
  </p>
  
  <pre>rails benchmarker 'User.all'</pre>
  
  <p>
    And it will work as if you had created a performance test and put that code in it. Very simple, right? Another example:
  </p>
  
  <pre>rails profiler 'User.all' 'User.find_by_login("goncalossilva")' --runs 3 --metrics cpu_time,memory # profiling memory won't work under Rubinius/JRuby (benchmarking memory will!)</pre>
  
  <p>
    Two things pop up from this code snippet: you can run multiple tests in a single command and you can specify options as you would with normal performance tests.
  </p>
  
  <p>
    To get a glimpse at all available options, run:
  </p>
  
  <pre>rails benchmarker --help rails profiler --help</pre>
  
  <h3>
    What can be done with this?
  </h3>
  
  <p>
    A lot of things can be accomplished with these tools. First and foremost, you can assess the performance of your application by benchmarking certain parts, either through tests or simple snippets of code. After finding potential bottlenecks, you can use profiling to gain a greater insight into what&#8217;s happening and how it can be improved.
  </p>
  
  <p>
    There are other useful tasks that can be done with these tools. You could, for instance, compare the performance of different interpreters on your application:
  </p>
  
  <pre>    rvm 1.9.2
    rails benchmarker 'MyModel.slow_method' 'get "/"' --metrics wall_time,memory
    rvm ree
    rails benchmarker 'MyModel.slow_method' 'get "/"' --metrics wall_time,memory
    rvm rubinius
    rails benchmarker 'MyModel.slow_method' 'get "/"' --metrics wall_time,memory
    rvm jruby
    rails benchmarker 'MyModel.slow_method' 'get "/"' --metrics wall_time,memory</pre>
  
  <p>
    Now you&#8217;ll know which interpreter takes less/more time/memory when it&#8217;s opening your homepage/running <code>MyModel.slow_method</code>.
  </p>
  
  <h3>
    Giving it a try
  </h3>
  
  <p>
    If you&#8217;ve come this far, now you know how to use these powerful tools. Try playing with them: I&#8217;m sure you&#8217;ll find valuable information about your applications&#8217; performance, and potentially spot some easily fixable bottlenecks. With little effort, your application will be faster, you will be prouder and your users will be happier!
  </p>
  
  <p class="alert">
    <em>Feel free to ask questions and give feedback in the comments section of this post.</em> Gonçalo has also written a guest blog post for RubyLearning before, titled &#8211; &#8220;<a href="http://rubylearning.com/blog/2010/12/14/ruby-gems-%E2%80%94-what-why-and-how/">Ruby gems &#8212; what, why and how</a>&#8220;. Fellow Rubyists, if you would like to write a guest blog post for RubyLearning write to <b>satish [at] rubylearning.org</b>
  </p>
</div>

