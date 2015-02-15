---
title: A Teeny-weeny mp3 player using Ruby and Shoes
author: Satish Talim
date: 2008-05-31
layout: post
permalink: /2008/05/31/a-teeny-weeny-mp3-player-using-ruby-and-shoes/
f.c.b.moh@hotmail.fr:
  - 56lkjk6+
jonesparker01@gmail.com:
  - Generic Cialis
topsy_short_url:
  - http://bit.ly/aCCAee
categories:
  - Ruby
tags:
  - japan
  - mp3 player
  - ruby on shoes
  - ruby programming
  - Shoes
---
<div>
  <h3>
    By Satoshi Asakawa
  </h3>
  
  <p>
    <img class="alignleft" title="Satoshi Asakawa" src="http://www.rubylearning.com/images/satoshi.jpg" alt="Satoshi Asakawa" width="100" height="100" /><strong><a href="mailto:ashbbb@gmail.com">Satoshi Asakawa</a></strong> is a Japanese Ruby enthusiast, a former student and now a Patron of the FORPC101 course.
  </p>
  
  <p>
    <strong>Shoes</strong> is a cross-platform, tiny graphics and windowing toolkit for the Ruby programming language written by <a href="http://whytheluckystiff.net/">Why</a>. You can find more information on Shoes <a href="http://code.whytheluckystiff.net/shoes/">here</a>.
  </p>
  
  <p>
    <strong>Objective</strong>: To build a teeny-weeny mp3 player.
  </p>
  
  <p>
    <strong>Step 1</strong>: Let us first download <a href="http://code.whytheluckystiff.net/shoes/wiki/DownloadShoes">Shoes</a>. We shall be using stable build file <strong>shoes-0.r396-curious.exe</strong>.
  </p>
  
  <p>
    <strong>Step 2</strong>: Next, we start writing the code for our teeny-weeny mp3 player. To begin with, we just have 6 lines of code but which provides enough functionality.
  </p>
  
  <pre><code>&lt;span style="color:blue">#my_mp3player01.rb
Shoes.app do
  button( 'play' ){ @v.play }
  button( 'pause' ){ @v.pause }
  button( 'stop' ){ @v.stop }
  @v = video "C:/rubyprograms/mp3player/ruby.mp3"
end&lt;/span></code></pre>
  
  <p>
    On Windows, run Shoes from your Start Menu. Enter the C:/rubyprograms/mp3player folder and select my_mp3player01.rb. A screen pops up:
  </p>
  
  <p>
    <img src="http://rubylearning.com/data/fig1.jpg" width= "500" alt="Screen 1" title="Shoes Screen 1" />
  </p>
  
  <p>
    Now click on play. That&#8217;s it!
  </p>
  
  <p>
    A Shoes application is simply a Ruby block: Shoes.app{ &#8230; } The Shoes.app part means &#8220;open the main Shoes window.&#8221; Inside the block, we describe what&#8217;s inside the window. Let&#8217;s add three buttons to our application that when pressed play/pause/stop our MP3. The last statement uses the video method to setup a Shoes::Video object. Shoes supports embedding of QuickTime, Flash video (FLV), DivX, Xvid and various other popular video formats, and some audio formats such as MP3, WAV and Ogg Vorbis. For more information, open the built-in Manual and read Elements Video section.
  </p>
  
  <p>
    <strong>Step 3</strong>: Change Window size. Add background colors and caption.
  </p>
  
  <pre><code>&lt;span style="color:blue"># my_mp3player02.rb
Shoes.app :width => 300, :height =>165 do
  background green
  background rgb(255,208,208), :radius => 24
  caption 'My original tiny MP3 player!'

  button( 'play' ){ @v.play }
  button( 'pause' ){ @v.pause }
  button( 'stop' ){ @v.stop }
  @v = video "C:/rubyprograms/mp3player/ruby.mp3"
end&lt;/span></code></pre>
  
  <p>
    We have added just three more lines. The background method draws a Background element with a specific color, gradient or image. Shoes backgrounds are actual elements, not styles. Hence Shoes layers background elements. It&#8217;s not the same as HTML. For more information, open the built-in Manual and read Slots Element section. Also see &#8220;<a href="http://hackety.org/press/">Nobody Knows Shoes (NKS)</a>&#8221; &#8211; Backgrounds & Borders and Smooth Corner Cuts.
  </p>
  
  <p>
    <img src="http://rubylearning.com/data/fig2.jpg" alt="Screen 2" title="Shoes Screen 2" />
  </p>
  
  <p>
    The caption method is one of the TEXT BLOCKS. Try to run the following sample code:
  </p>
  
  <pre><code>&lt;span style="color:blue"># textsize.rb
Shoes.app do
  banner "Banner\n"
  title "Title\n"
  subtitle "Subtitle\n"
  tagline "Tagline\n"
  caption "Caption\n"
  para "Para\n"
  inscription "Inscription\n"
  para "Specific font size", :size => 48
end&lt;/span></code></pre>
  
  <p>
    For more information, see NKS &#8211; the 1st chapter of 10 essentials.
  </p>
  
  <p>
    <img src="http://rubylearning.com/data/fig2_1.jpg" width= "500" alt="Screen 2_1" title="Shoes Screen 2_1" />
  </p>
  
  <p>
    <strong>Step 4</strong>: Oh! We need to layout the elements.
  </p>
  
  <pre><code>&lt;span style="color:blue"># my_mp3player03.rb
Shoes.app :width => 300, :height =>165 do
  background green
  background rgb(255,208,208), :radius => 24
  caption 'My original tiny MP3 player!'
  
  flow :left => 0, :top => 120  do
    button( 'play' ){ @v.play }
















    button( 'pause' ){ @v.pause }
    button( 'stop' ){ @v.stop }
    @v = video "C:/rubyprograms/mp3player/ruby.mp3"
  end
end&lt;/span></code></pre>
  
  <p>
    In this case, we can use flow{ &#8230; } Shoes has a fundamental concept: stacks and flows. We need to understand the concept completely for layouting elements inside the window. Read <a href="http://code.whytheluckystiff.net/shoes/wiki/StacksAndFlows">this page</a> carefully.
  </p>
  
  <p>
    <img src="http://rubylearning.com/data/fig3.jpg" width= "500" alt="Screen 3" title="Shoes Screen 3" />
  </p>
  
  <p>
    Now try to run the above program &#8211; <strong>my_mp3player03.rb</strong> by replacing the word &#8216;flow&#8217; to &#8216;stack&#8217; and see the result (shown below).
  </p>
  
  <p>
    <img src="http://rubylearning.com/data/fig3_1.jpg" width= "500" alt="Screen 3_1" title="Shoes Screen 3_1" />
  </p>
  
  <p>
    <strong>Step 5</strong>: Want to listen other mp3 files?
  </p>
  
  <pre><code>&lt;span style="color:blue"># my_mp3player04.rb
Shoes.app :width => 300, :height =>165 do
  background green
  background rgb(255,208,208), :radius => 24
  caption 'My original tiny MP3 player!'
  
  flow :left => 0, :top => 120  do
    button( 'select?' ){@v = video ask_open_file}
    button( 'play' ){ @v.play }
    button( 'pause' ){ @v.pause }
    button( 'stop' ){ @v.stop }
  end
end&lt;/span></code></pre>
  
  <p>
    We can use built-in methods (also called: Kernel methods.) In this case, we can use ask_open_file method which pops up an &#8216;Open file&#8230;&#8217; window.
  </p>
  
  <p>
    <img src="http://rubylearning.com/data/fig4.jpg" width= "500" alt="Screen 4" title="Shoes Screen 4" />
  </p>
  
  <p>
    For more information, see the built-in Manual for Built-in Methods section.
  </p>
  
  <p>
    <strong>Step 6</strong>: Need to control select button depending on the situation.
  </p>
  
  <pre><code>&lt;span style="color:blue"># my_mp3player05.rb
Shoes.app :width => 300, :height =>165 do
  background green
  background rgb(255,208,208), :radius => 24
  caption 'My original tiny MP3 player!'
  
  flow :left => 0, :top => 120  do
    button 'select?' do
      tmp = @file
      (@v = video(@file)  unless (@file = ask_open_file).nil?)  if @file.nil? || !@v.playing?
      @file ||= tmp
    end
    button( 'play' ){ @v.play }
    button( 'pause' ){ @v.pause }
    button( 'stop' ){ @v.stop }
  end
end&lt;/span></code></pre>
  
  <p>
    As we write the program code, we need to consider several cases. Here, we have to handle the following cases:
  </p>
  
  <ul>
    <li>
      if user doesn&#8217;t select the MP3 file yet
    </li>
    <li>
      if the MP3 is playing
    </li>
    <li>
      if the user pressed the cancel button on the select window
    </li>
  </ul>
  
  <p>
    <img src="http://rubylearning.com/data/fig5.jpg" width= "500" alt="Screen 5" title="Shoes Screen 5" />
  </p>
  
  <p>
    <strong>Step 7</strong>: Want to display mp3 file name and runtime per second?
  </p>
  
  <pre><code>&lt;span style="color:blue"># my_mp3player06.rb
Shoes.app :width => 300, :height =>165 do
  background green
  background rgb(255,208,208), :radius => 24
  caption 'My original tiny MP3 player!'
  
  stack :left => 0, :top => 70 do
    @l = para('', :stroke => white)
    animate do
      @l.replace strong "#{@file} : #{@v.time.to_i / 1000} sec"  unless @file.nil?
    end
  end
  
  flow :left => 0, :top => 120  do
    button 'select?' do
      tmp = @file
      (@v = video(@file)  unless (@file = ask_open_file).nil?)  if @file.nil? || !@v.playing?
      @file ||= tmp
    end
    button( 'play' ){ @v.play }
    button( 'pause' ){ @v.pause }
    button( 'stop' ){ @v.stop }
  end
end&lt;/span></code></pre>
  
  <p>
    To display the runtime per second, we can use the animate method: animate(fts){ &#8230; } The block will run fts times per second. fts is a option. If no number is given, default is 10.
  </p>
  
  <p>
    For more information, see the built-in Manual: Slots Element section.
  </p>
  
  <p>
    The para method sets up a Shoes::TextBlock object. In this case, it is assigned to @l. We can use the replace method in the block of the animate method to replace and redisplay the specific string such as the mp3 file name and the time position of the mp3. The time method shows the time position in milliseconds &#8211; so transform it into seconds.
  </p>
  
  <p>
    <img src="http://rubylearning.com/data/fig6.jpg" width= "500" alt="Screen 6" title="Shoes Screen 6" />
  </p>
  
  <p>
    <strong>Step 8</strong>: Want dancing loogink (Her (the creature) name) in the background while MP3 is playing?
  </p>
  
  <pre><code>&lt;span style="color:blue"># my_mp3player07.rb
$BASE_PATH = "C:/rubyprograms/mp3player/"

Shoes.app :width => 300, :height =>165 do
  background green
  background rgb(255,208,208), :radius => 24
  caption 'My original tiny MP3 player!'
  
  stack :left => 0, :top => 30 do
    @img = image $BASE_PATH + "loogink.png"
    n = 0
    animate(5) do
      @img.move( (n+=1) % 300 , 10 - rand(10))  if !@file.nil? &#038;&#038; @v.playing?
    end
  end
  
  stack :left => 0, :top => 70 do
    @l = para('', :stroke => white)
    animate do
      @l.replace strong "#{@file} : #{@v.time.to_i / 1000} sec"  unless @file.nil?
    end
  end
  
  flow :left => 0, :top => 120  do
    button 'select?' do
      tmp = @file
      (@v = video(@file)  unless (@file = ask_open_file).nil?)  if @file.nil? || !@v.playing?
      @file ||= tmp
    end
    button( 'play' ){ @v.play }
    button( 'pause' ){ @v.pause }
    button( 'stop' ){ @v.stop }
  end
end&lt;/span></code></pre>
  
  <p>
    We can use the same structure of Step 7. The image method sets up a Shoes::Image object. In this case, it is assigned to @img. We can use the move method in the block of the animate method to move the object. For more information, see the built-in Manual: Elements Image section.
  </p>
  
  <p>
    <img src="http://rubylearning.com/data/fig7.jpg" width= "500" alt="Screen 7" title="Shoes Screen 7" />
  </p>
  
  <p>
    As you can see, if you know <a href="http://www.rubylearning.org/class/">Ruby programming</a>, you can easily learn Shoes to quickly build UIs. I&#8217;d like to take this opportunity to thanks Anita Kuno from Canada who created the oogink.png and ruby.mp3 files used in this blog post.
  </p>
  
  <p>
    <strong>Conclusion</strong>: Some ideas to personalize this MP3 player:
  </p>
  
  <ul>
    <li>
      use your favorite photo as a background
    </li>
    <li>
      display the name of the song playing &#8211; You can learn how to extract the name of the song from a mp3 file in the excellent course conducted by Satish Talim at <a href="http://www.rubylearning.org/class/">FORPC101</a>
    </li>
  </ul>
  
  <p>
    If you come up with any new idea, do write your original mp3 player and please do let me know. Have fun with Ruby!
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/mp3+Player" rel="tag">mp3 Player</a>, <a href="http://technorati.com/tag/Japan" rel="tag">Japan</a>, <a href="http://technorati.com/tag/Ruby+on+Shoes" rel="tag">Ruby on Shoes</a>, <a href="http://technorati.com/tag/Ruby+Programming" rel="tag">Ruby Programming</a>, <a href="http://technorati.com/tag/Satoshi+Asakawa" rel="tag">Satoshi Asakawa</a>
