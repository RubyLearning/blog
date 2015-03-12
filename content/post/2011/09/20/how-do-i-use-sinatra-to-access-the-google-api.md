---
author: Satish Talim
categories:
- Heroku
- Ruby
- Sinatra
date: 2011-09-20
layout: post
permalink: /2011/09/20/how-do-i-use-sinatra-to-access-the-google-api/
tags:
- Google+
- programming
- Ruby
- ruby programming
- Sinatra
thesis_description:
- A simple Sinatra app that accesses the Google+ API.
thesis_keywords:
- Ruby, Programming, Ruby programming, Sinatra, Google+
thesis_post_image_frame:
- true
thesis_post_image_horizontal:
- center
thesis_post_image_vertical:
- before-post
title: How do I use Sinatra to access the Google+ API?
topsy_short_url:
- null
---

<div>
  <h2>
    How do I use Sinatra to access the Google+ API?
  </h2>
  
  <p class="alert">
    RubyLearning is conducting <a href="http://goo.gl/he9ao">many free, online courses on Google+</a>. Some participants wanted an answer to their question &#8220;<strong>How do I use Sinatra to access the Google+ API?</strong>&#8221; This blog post explains the same. Read on.
  </p>
  
  <h3>
    Pre-requisite
  </h3>
  
  <h4>
    Install Sinatra, Git, Heroku, Bundler
  </h4>
  
  <p>
    <a href="http://goo.gl/Wr51F">Refer RubyLearning&#8217;s article on Google+</a>.
  </p>
  
  <h3>
    Create a folder on your hard disk
  </h3>
  
  <p>
    Create a folder <code>sinatragplus</code>. This is where we will store our Sinatra app. Open a Bash shell in this folder.
  </p>
  
  <h3>
    Create the following folders also
  </h3>
  
  <p>
    <img src="http://rubylearning.com/blog/wp-content/uploads/folder_gplus.jpg" alt="Folder for app" />
  </p>
  
  <h3>
    Organize your application
  </h3>
  
  <h4>
    Static Files
  </h4>
  
  <p>
    Static files are served from the <code>public</code> folder. Note that the <code>public</code> folder name will not be included in the URL. A file ./public/stylesheets/style.css is made available as rubylearning.org/stylesheets/style.css. Do note that we can have <em>any</em> directory layout under the <code>public</code> folder.
  </p>
  
  <h4>
    Layout
  </h4>
  
  <p>
    We will soon create <code>layout.erb</code> file in the <code>views</code> folder. This allows the basic layout of our site headers, footers and navigation panes to be controlled independently. A change in <code>layout.erb</code> is instantly applied across our whole site.
  </p>
  
  <p>
    Let&#8217;s look at a sample file:
  </p>
  
  <pre>&lt;html&gt;
  &lt;head&gt;..&lt;/head&gt;
  &lt;body&gt;
    &lt;%= yield %&gt;
  &lt;/body&gt;
&lt;/html&gt;
</pre>
  
  <p>
    In the above file, note the usage of <code>yield</code>. The file calls <code>yield</code> at the point you want the content to be included i.e. it refers to some .erb in the <code>views</code> folder and the results of that .erb are stuck at the place, where you called <code>yield</code>.
  </p>
  
  <p>
    Now, let&#8217;s write our app&#8217;s <code>layout.erb</code> file:
  </p>
  
  <pre>&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"&gt;
&lt;html xmlns="http://www.w3.org/1999/xhtml"&gt;
  &lt;head&gt;
    &lt;title&gt;A Sinatra app to access Google+&lt;/title&gt;
    &lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8" /&gt;
    &lt;meta name="description" content="RubyLearning.org" /&gt;
    &lt;meta name="keywords" content="rubylearning,ruby,ruby programming,ruby course,sinatra course" /&gt;
    &lt;link rel="stylesheet" type="text/css" href="/stylesheets/style.css" /&gt;
    &lt;link rel="icon" type="image/ico" href="/images/favicon.ico" /&gt;
  &lt;/head&gt;
  &lt;body&gt;
    &lt;%= yield %&gt;
  &lt;/body&gt;
&lt;/html&gt;
</pre>
  
  <h4>
    Image
  </h4>
  
  <p>
    I am using a favicon (<a href="http://rubylearning.com/images/favicon.ico">favicon.ico</a>) for my app, which is stored in the <code>public/images</code> folder.
  </p>
  
  <h4>
    Stylesheet
  </h4>
  
  <p>
    We have our stylesheet namely <code>style.css</code> in the folder <code>public/stylesheets</code>.
  </p>
  
  <pre>body
{
  line-height: 1.6em;
}

h1 {
  color: #2A1959;
  border-bottom: 2px solid #2A1959;
}

h2 {
  color: #474B94;
  font-size: 1.2 em;
}

#footer {
  clear: both;
  border-top: 1px solid #2A1959;
  text-align: left; 
  height: 50px; 
  font-size: 70%;
  width: 100%;
}

#hor-minimalist-a
{
  font-family: "Lucida Sans Unicode", "Lucida Grande", Sans-Serif;
  font-size: 12px;
  background: #fff;
  margin: 45px;
  width: 480px;
  border-collapse: collapse;
  text-align: left;
}
#hor-minimalist-a th
{
  font-size: 14px;
  font-weight: normal;
  color: #039;
  padding: 10px 8px;
  border-bottom: 2px solid #6678b1;
}
#hor-minimalist-a td
{
  color: #669;
  padding: 9px 8px 0px 8px;
}
#hor-minimalist-a tbody tr:hover td
{
  color: #009;
}
</pre>
  
  <h4>
    View
  </h4>
  
  <p>
    A view is responsible for generating a user interface, normally based on data. For example, an online store will have a list of products to be displayed on a catalogue screen. The view accesses the data and formats it for the end-user.
  </p>
  
  <p>
    All file-based views are looked up in the <code>views</code> folder.
  </p>
  
  <h3>
    Using ERB
  </h3>
  
  <p>
    ERB is written in pure Ruby and is included with the standard Sinatra distribution. ERB allows you to embed Ruby statements in an HTML page.
  </p>
  
  <p>
    The important things to know about an <code>.erb</code> file is that <code>&lt;%= ruby_code %&gt;</code> evaluates the ruby code and outputs the result, and <code>&lt;% ruby_code %&gt;</code> evaluates the code, but doesn&#8217;t output anything.
  </p>
  
  <p>
    We will use ERB for our app.
  </p>
  
  <p>
    <b>Note</b>: If we write:
  </p>
  
  <pre>get '/' do
  erb :index
end
</pre>
  
  <p>
    This tells Sinatra that when a <code>GET</code> request for &#8216;/&#8217; comes in, that we should use the ERB helper to render the <code>index.erb</code> template, which is stored in the <code>views</code> sub-folder by convention and marked up with embedded Ruby (ERB).
  </p>
  
  <h3>
    Write the sinatragplus.rb app
  </h3>
  
  <p>
    Store <code>sinatragplus.rb</code> in the folder <code>sinatragplus</code>:
  </p>
  
  <pre># sinatragplus.rb
require 'sinatra'
require 'google_plus'

error do
  erb :'500'
end

#class
class GPlus
  def initialize(apikey, gid)
    @apikey = apikey
    @gid = gid
    get_info
  end
  attr_reader :row0, :row1, :row2
  private
    #Get info about specific G+ ID
    def get_info
      # GooglePlus.api_key = 'Your API Key'
      begin
        GooglePlus.api_key = @apikey
        person = GooglePlus::Person.get(@gid.to_i)
        @row0 = person.display_name
        @row1 = person.tagline
        @row2 = person.url
      rescue Exception => msg  
        # display the system generated error message  
        puts msg  
      end  
    end
end
 
get '/' do
  erb :index
end

# Display Google+ details
post '/show' do
  @gplus = GPlus.new(params[:apikey], params[:gid])
  erb :show
end
</pre>
  
  <h4>
    Explanation
  </h4>
  
  <ul>
    <li>
      Install: <code>gem install google_plus</code>.
    </li>
    <li>
      We are going to use the above installed <a href="https://github.com/seejohnrun/google_plus">google_plus</a> gem.
    </li>
    <li>
      To access the Google+ API, <a href="https://code.google.com/apis/console#access">get your own Google API key</a>.
    </li>
    <li>
      Note down the Google+ ID of the person whose Google+ profile you want to display using this app. For example, here&#8217;s my <a href="https://plus.google.com/107809992818057105754/">Google+ URL</a> and the number in the URL namely <b>107809992818057105754</b> is my Google+ ID.
    </li>
    <li>
      When a GET request for &#8216;/&#8217; comes in, we are going to render the <code>index.erb</code> template in the <code>public/views</code> folder.
    </li>
    <li>
      The file <a href="https://gist.github.com/1228369#file_index.erb">index.erb</a> has a HTML form that accepts the Google+ API key and ID for the user profile that you want to display. <b>Note</b> that even if you do not give any value to these fields, the app will not crash. <em>Handler</em> is the generic term that Sinatra uses for the &#8220;controllers&#8221;. A handler is the initial point of entry for new HTTP requests into your application. In handlers you can reach submitted form parameters directly via the <code>params</code> hash. Also note, that when you click on the submit button of the form a <code>POST</code> request is being sent.
    </li>
    <li>
      The <code>post '/show' do</code> creates an object of our class <code>GPlus</code> passing to the <code>initialize</code> method the apikey and google id that your entered on the screen (via <code>params</code>). The <code>initialize</code> method in-turn calls a private method <code>get_info</code> that accesses the Google+ API and returns a <a href="http://developers.google.com/+/api/latest/people">person</a> object We call the method <code>display_name</code>, <code>tagline</code> and <code>url</code> on the <code>person</code> object and populate instance variables <code>@row0</code>, <code>@row1</code> and <code>@row2</code>.
    </li>
    <li>
      The <a href="https://gist.github.com/1228369#file_show.erb">show.erb</a> displays these values in a HTML table.
    </li>
  </ul>
  
  <h3>
    Error Handling
  </h3>
  
  <p>
    When someone comes to a page on your domain that is no longer there (either because it’s been deleted, because they’ve typed something in wrong or because the link that they followed was wrong) they are shown the dreaded 404 ‘page not found’ error page.
  </p>
  
  <p>
    This error simply means that the person was able to communicate with your server but that the server couldn&#8217;t find the page that they were after.
  </p>
  
  <p>
    404 errors should not be confused with &#8220;server not found&#8221; or similar errors, in which a connection to the destination server could not be made at all.
  </p>
  
  <p>
    When a <code>Sinatra::NotFound</code> exception is raised, or the response&#8217;s status code is 404, the <code>not_found</code> handler is invoked:
  </p>
  
  <p>
    Write <a href="https://gist.github.com/1228369#file_404.erb">404.erb</a> in the <code>public/views</code> folder. Note that I had to surround the <code>erb :'404'</code> in single quotes. This is because Ruby syntax doesn&#8217;t let symbol&#8217;s first character be a number. By quoting it, it gets around that issue.
  </p>
  
  <p>
    A 500 error page will be thrown to the client when the Web server (running the Web Site) encounters an unexpected condition that prevents it from fulfilling the request by the client (e.g. your Web browser) for access to the requested URL.
  </p>
  
  <p>
    By default error will catch <code>Sinatra::ServerError</code>. Sinatra will pass you the error via the &#8216;sinatra.error&#8217; in <code>request.env</code>.
  </p>
  
  <p>
    Write <a href="https://gist.github.com/1228369#file_500.erb">500.erb</a> in the <code>public/views</code> folder.
  </p>
  
  <p>
    Our app is ready! Let&#8217;s deploy it to Heroku.
  </p>
  
  <h3>
    Create config.ru file in the folder sinatragplus
  </h3>
  
  <p>
    This file contains:
  </p>
  
  <pre>require './sinatragplus'
run Sinatra::Application
</pre>
  
  <h3>
    Install required gems for our app
  </h3>
  
  <p>
    In the Bash shell type:
  </p>
  
  <pre>$ bundle init
</pre>
  
  <p>
    Edit the created <code>Gemfile</code> with your preferred text editor to let it look like this:
  </p>
  
  <pre>source "http://rubygems.org"
gem 'sinatra'
gem 'google_plus'
</pre>
  
  <p>
    In the Bash shell type:
  </p>
  
  <pre>$ bundle check
</pre>
  
  <p>
    Finally in the open Bash shell, type:
  </p>
  
  <pre>$ bundle install
</pre>
  
  <h3>
    Create a Procfile
  </h3>
  
  <p>
    Use a <code>Procfile</code>, a text file in the root directory of your application, to explicitly declare what command should be executed to start a web dyno. In this case, you simply need to execute the sinatragplus.rb using Ruby.
  </p>
  
  <p>
    Here&#8217;s our <code>Procfile</code>:
  </p>
  
  <pre>web: bundle exec ruby sinatragplus.rb -p $PORT</pre>
  
  <h3>
    Setup your local app to use Git
  </h3>
  
  <p>
    I have the <code>sinatragplus.rb</code>, <code>Procfile</code> and <code>config.ru</code> files already in the folder <code>sinatragplus</code>.
  </p>
  
  <p>
    In the already open Bash shell, type:
  </p>
  
  <pre>$ git init
$ git add .
$ git commit -m "sinatragplus first commit"
</pre>
  
  <h3>
    Create the app on Heroku
  </h3>
  
  <p>
    In the bash shell, type:
  </p>
  
  <pre>$ heroku create sinatragplus
</pre>
  
  <h3>
    Push your application to Heroku
  </h3>
  
  <pre>$ git push heroku master
</pre>
  
  <p>
    That&#8217;s it, the app is now running on Heroku! You can take a look at it, in your browser type: <a href="http://sinatragplus.herokuapp.com/">http://sinatragplus.herokuapp.com/</a>.
  </p>
  
  <h3>
    What next?
  </h3>
  
  <p>
    On the <code>person</code> object use the <code>attributes</code> method to get all the <code>person</code> fields back as a Hash:
  </p>
  
  <pre>properties = person.attributes
properties.each { |key, value| puts "#{key} equals #{value}" }
</pre>
  
  <h3>
    Exercise
  </h3>
  
  <p>
    In <code>show.erb</code> I have populated only the <code>display_name</code>, <code>tagline</code> and <code>url</code> fields of <code>person</code>. Populate all the other <code>person</code> fields in the HTML table that is generated by <code>show.erb</code>.
  </p>
  
  <p>
    Have fun!
  </p>
  
  <p class="alert">
    <em>Do post a link to your version of this program. Feel free to ask questions and give feedback in the comments section of this post.</em> Fellow Rubyists, if you would like to write a guest blog post for RubyLearning email me at <b>satish [at] rubylearning.org</b>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Programming" rel="tag"> Programming</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag"> Ruby programming</a>, <a href="http://technorati.com/tag/Sinatra" rel="tag"> Sinatra</a>, <a href="http://technorati.com/tag/Google%2B" rel="tag"> Google+</a>
