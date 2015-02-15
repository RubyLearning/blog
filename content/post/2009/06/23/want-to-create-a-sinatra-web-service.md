---
title: Want to create a Sinatra Web Service?
author: Satish Talim
date: 2009-06-23
layout: post
permalink: /2009/06/23/want-to-create-a-sinatra-web-service/
thesis_title:
  - 'Sinatra Web Service: Sorter'
thesis_description:
  - Learn how to quickly write and create a Sinatra web service.
thesis_keywords:
  - cURL,Sinatra,Sinatra web service,Ruby programming,sorter,cloudControl
topsy_short_url:
  - http://bit.ly/9y6qlm
categories:
  - Ruby
  - Sinatra
  - Training
tags:
  - cloudControl
  - cURL
  - ruby programming
  - Sinatra
  - Sinatra tutorial
  - Sinatra web service
  - sorter
---
<div>
  <p class="alert">
    With <strong>Sinatra</strong> you can quickly create your own tiny web-applications in Ruby and write lots of small services.
  </p>
  
  <h3>
    Problem definition
  </h3>
  
  <p>
    To upload a text file to a <strong>Sinatra web service</strong> and have its sorted content returned.
  </p>
  
  <h3>
    How to upload a file from the command line?
  </h3>
  
  <p>
    We shall use <strong>cURL</strong>, a tool and library designed to give you a user-friendly but low-level interface to making HTTP requests. cURL also supports many other protocols related to uploading and downloading files.
  </p>
  
  <p>
    In case you have not used cURL, please read the brief note &#8211; <a href="http://rubylearning.com/blog/do-you-know-how-to-use-curl/">Do you know how to use cURL?</a>. It explains how you can download, install and use cURL.
  </p>
  
  <p>
    The actual command from the command prompt to upload a text file to a <em>Sinatra web service</em> is:
  </p>
  
  <pre>curl -F "info=@alpha.txt" localhost:4567/sorter</pre>
  
  <p>
    Let&#8217;s look at the above command in more detail:
  </p>
  
  <ul>
    <li>
      The cURL -F option lets cURL emulate a filled-in form in which a user has pressed the submit button. This causes curl to POST data. This also enables uploading of binary files etc. To force the &#8216;content&#8217; part to be a file, we prefix the file name with an @ sign.
    </li>
    <li>
      alpha.txt is our text file to be uploaded. You can check the contents of this file <a href="http://rubylearning.com/data/alpha.txt">from here</a>.
    </li>
    <li>
      info is the name of the form-field to which alpha.txt will be the input.
    </li>
    <li>
      Our Sinatra web service will be running on localhost:4567/sorter
    </li>
  </ul>
  
  <h3>
    Sorter Sinatra Web Service
  </h3>
  
  <p>
    Our <em>Sinatra web service</em> is very simple. The contents of the program <b>sorter.rb</b> are:
  </p>
  
  <pre># sorter.rb
require 'sinatra'

# Usage: curl -F "info=@alpha.txt" localhost:4567/sorter
post '/sorter' do
  params[:info][:tempfile].readlines.sort
end</pre>
  
  <ul>
    <li>
      Handler is the generic term that Sinatra uses for the &#8220;controllers&#8221;. A handler is the initial point of entry for new HTTP requests into your application. In handlers you can reach submitted form parameters directly via the <b>params</b> hash. The support of Rails like nested parameters is built-in since Sinatra. Therefore in handlers you can use nested parameters like a regular hash: <b>params[:info][:tempfile]</b>
    </li>
    <li>
      The Ruby method <b>readlines</b> reads the entire file as individual lines and returns those lines in an array.
    </li>
    <li>
      The <b>Array.sort</b> method, sorts our array contents.
    </li>
  </ul>
  
  <h3>
    Starting the Sorter Sinatra Web Service
  </h3>
  
  <p>
    Open a new command window and change the folder to the folder that contains your file &#8211; <b>sorter.rb</b>. Next type:
  </p>
  
  <pre>ruby sorter.rb</pre>
  
  <p>
    Now open another command window and change the folder to the folder that contains your file &#8211; <b>alpha.txt</b>. Next type in our cURL command, namely:
  </p>
  
  <pre>curl -F "info=@alpha.txt" localhost:4567/sorter</pre>
  
  <p>
    The command window where you typed in your cURL command should get the results, namely:
  </p>
  
  <pre>apple
birthday
cat
pune
xmas
yen
zebra</pre>
  
  <h4>
    Use my Sorter Sinatra Web Service
  </h4>
  
  <p>
    For your pleasure, I have created the Sorter <em>Sinatra Web Service</em> on <a href="https://www.cloudcontrol.com">cloudControl</a> (it&#8217;s free). You can use this <em>Sorter Sinatra Web Service</em> service anytime you want. Open a command window and change your folder to the folder containing the file <b>alpha.txt</b>. Next type in the following cURL command:
  </p>
  
  <pre>curl -F "info=@alpha.txt" http://curlsorter.cloudcontrolled.com/sorter</pre>
  
  <p>
    The command window where you typed in this cURL command should display the desired results.
  </p>
  
  <p>
    <span style="background-color: #FFFFCC;">Remember to have fun with <strong>Sinatra</strong>!</span>
  </p>
  
  <h4>
    Credits
  </h4>
  
  <ul>
    <li>
      Michael C. Morin for the note on cURL.
    </li>
    <li>
      Jonathan Palardy whose blog post inspired me to write this article.
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/cURL" rel="tag">cURL</a>, <a href="http://technorati.com/tag/Sinatra" rel="tag">Sinatra</a>, <a href="http://technorati.com/tag/Sinatra+web+service" rel="tag">Sinatra web service</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>, <a href="http://technorati.com/tag/sorter" rel="tag">sorter</a>, <a href="http://technorati.com/tag/cloudControl" rel="tag">cloudControl</a>
