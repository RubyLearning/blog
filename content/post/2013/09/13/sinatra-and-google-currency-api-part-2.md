---
title: 'Sinatra and Google Currency API - Part 2'
author: Girish Sonawane
date: "2013-09-13"
layout: post
permalink: /2013/09/13/sinatra-and-google-currency-api-part-2/
thesis_description:
  - Learn how to use the Google currency API with Sinatra in this two part blog post on RubyLearning.
thesis_keywords:
  - Girish Sonawane, Google currency API, Sinatra
topsy_short_url:
  - http://bit.ly/161LcAm
categories:
  - beginners
  - ruby
  - sinatra
tags:
  - girish sonawane
  - google currency api
  - sinatra
---
<div>
  <h2>
    Sinatra and Google Currency API &#8211; Part 2
  </h2>
  
  <p class="update">
    This guest post is by <b>Girish Sonawane</b>, a self-taught programmer. He came across Ruby in 2008 and has since been working full-time on Ruby. He worked as a Rails freelancer and later co-founded <a href="http://cuberoot.in/">Cube Root</a>, an exclusive Ruby on Rails software boutique catering to outsourced work. His interests are everything related to technology or science. You can reach him at <a href="mailto:girish@cuberoot.in">girish@cuberoot.in</a> or via twitter @girishso.
  </p>
  
  <p class="block">
    <img class="alignright" alt="Girish Sonawane" src="http://rubylearning.com/images/girishsonawane.png" width="125" height="125" /> <strong><span class="drop_cap">I</span></strong>n this two-part series, I will show you how to use Google currency conversion API and use it in a small Sinatra app. In <a href="http://rubylearning.com/blog/2013/09/04/sinatra-and-google-currency-api-part-1/">Part 1</a> we built a small function to access the Google API for currency conversion. This is Part 2, where we will build a small Sinatra app using the function we created in Part 1.
  </p>
  
  <p>
    The source code for this series is available on <a href="https://github.com/girishso/goog_currency_tutorial">Github</a>, with commits for each step. This little library is available as a Ruby Gem at <a href="https://rubygems.org/gems/goog_currency">GoogCurrency</a>.
  </p>
  
  <h3>
    Wireframes
  </h3>
  
  <p>
    We will have two screens, one with a form where a user can submit data and another showing the result.
  </p>
  
  <p>
    <code>Home page</code>
  </p>
  
  <p>
    <img src="http://rubylearning.com/images/bloghome.png" width="600" title="Home" alt="Home" />
  </p>
  
  <p>
    <code>Results page</code><br /> <img src="http://rubylearning.com/images/blogresult.png" width="600" title="Result" alt="Results" />
  </p>
  
  <h3>
    Sinatra
  </h3>
  
  <p>
    Since this is a very basic app, we are going to use Sinatra in classic style. We need following files.
  </p>
  
  <p>
    <code>Gemfile</code> for all the gem dependencies.
  </p>
  
  <pre>1 source 'https://rubygems.org'
2
3 gem "rest-client", "1.6.7"
4 gem "json", "1.8.0"
5 gem "rspec", "2.14.1"
6 gem "fakeweb", "1.3.0"
7 gem "sinatra", "1.4.3"
8 gem "capybara", "2.1.0"
9 gem "haml"
</pre>
  
  <p>
    <code>config.ru</code> required to run the app on Rack servers like Passenger, Heroku etc.
  </p>
  
  <pre>1 require 'bundler'
2 Bundler.require
3 require './app'
4 run Sinatra::Application
</pre>
  
  <p>
    <code>Bundler.require</code> will require all the gems listed in our Gemfile and made available to our Sinatra app.
  </p>
  
  <p>
    Let&#8217;s create an empty <code>app.rb</code>, the main Sinatra app file with <code>touch app.rb</code>
  </p>
  
  <p>
    Continuing with the same spirit as Part 1, we are going to test drive this app. We are going to use <code>capybara</code> for acceptance tests.
  </p>
  
  <p>
    <code>spec/acceptance_spec.rb</code>
  </p>
  
  <pre>1  require 'bundler'
2  Bundler.require
3
4  disable :run
5  set :root, File.dirname(__FILE__) + "/.."
6  require Sinatra::Application.root + '/app'
7
8  Capybara.app = Sinatra::Application
9
10 RSpec.configure do |config|
11   config.include Capybara::DSL
12 end
13
14 describe 'currency converter' do
15   it "loads currency converter form"
16   it "converts currencies"
17   it "handles errors"
18 end
</pre>
  
  <p>
    Line 4, disables the web server, we don&#8217;t need a webserver for specs. Line 8, tells <code>capybara</code> it&#8217;s a Sinatra app. Line 11, makes <code>capybara</code> DSL available to our specs.
  </p>
  
  <p>
    Line 15, 16, 17, adds three pending specs.
  </p>
  
  <p>
    If we execute our spec now with <code>rspec spec/acceptance_spec.rb</code>, it says:
  </p>
  
  <pre>1  ***
2
3  Pending:
4    currency converter loads currency converter form
5      # Not yet implemented
6      # ./spec/acceptance_spec.rb:15
7    currency converter converts currencies
8      # Not yet implemented
9      # ./spec/acceptance_spec.rb:16
10   currency converter handles errors
11     # Not yet implemented
12     # ./spec/acceptance_spec.rb:17
</pre>
  
  <p>
    Let&#8217;s define the first spec and make it pass.
  </p>
  
  <pre>1 it "loads currency converter form" do
2     visit "/"
3     page.should have_content("Currency Converter")
4     find('form').should have_button('Convert')
5   end
</pre>
  
  <p>
    <code>capybara</code> simulates user interactions with the website. <code>visit "/"</code> takes the user to the home page of the site as expected. Line 3, checks for existence of &#8220;Currency Converter&#8221; text on the page. Line 4, expects a <code>form</code> with the <code>Convert</code> button.
  </p>
  
  <p>
    Typically, there is no need of such granular level testing, but this tells us if the test suite is working as expected.
  </p>
  
  <p>
    Executing the spec fails with:
  </p>
  
  <pre>1 expected #has_content?("Currency Converter") to return true, got false
</pre>
  
  <p>
    Now to make this spec pass, let&#8217;s modify <code>app.rb</code>:
  </p>
  
  <pre>1 get "/" do
2     haml :"index"
3   end
</pre>
  
  <p>
    <code>get "/"</code> loads the home page. We are using <code>haml</code> view templates instead of <code>erb</code>. It expects <code>views/index.haml</code> in views folder. Let&#8217;s add it.
  </p>
  
  <pre>1 %h1 Currency Converter
2
3   %form(action = "/convert" method = "post")
4
5       %input#convert(type="submit" value="Convert")
</pre>
  
  <p>
    Let&#8217;s also add a layout <code>views/layout.haml</code>:
  </p>
  
  <pre>1 !!!
2   %html
3     %head
4       %title Currency Conversion Tutorial
5     %body
6       = yield
</pre>
  
  <p>
    Executing specs with <code>rspec spec/acceptance_spec.rb</code> passes the spec. We are good to go with the next pending spec.
  </p>
  
  <pre>1  valid_response =&lt;&lt;-VALID
2    {lhs: "1 U.S. dollar",rhs: "54.836587 Indian rupees",error: "",icc: true}
3    VALID
4    .
5    .
6    .
7    it "converts currencies" do
8      FakeWeb.register_uri(:get,
9                         "http://www.google.com/ig/calculator?hl=en&#038;q=1USD=?INR",
10                        :status => "200",
11                        :body => valid_response)
12     visit '/'
13
14     fill_in "amount", :with => 1
15     select "USD", :from => "from"
16     select "INR", :from => "to"
17     click_button 'Convert'
18
19     find("#result").should have_content('54.836587')
20   end
</pre>
  
  <p>
    We are again using <code>fakeweb</code> gem to simulate the Google API interaction, Line 8.
  </p>
  
  <p>
    We are simulating user converting 1 USD to INR, using <code>capyabara</code> DSL to simulate the user interactions
  </p>
  
  <p>
    Line 12, visit home page.
  </p>
  
  <p>
    Line 14, Fill <code>amount</code> input field with 1.
  </p>
  
  <p>
    Line 15, select <code>USD</code> from <code>from</code> currencies select box.
  </p>
  
  <p>
    Line 16, select <code>INR</code> from <code>to</code> currencies select box.
  </p>
  
  <p>
    Line 18, click button &#8220;Convert&#8221;
  </p>
  
  <p>
    Line 20, we expect to have <code>#result</code> with the converted amount.
  </p>
  
  <p>
    Executing spec fails with:
  </p>
  
  <pre>1 Unable to find field "amount"
</pre>
  
  <p>
    Let&#8217;s go ahead and add the <code>amount</code> field and other fields as well in <code>index.haml</code>.
  </p>
  
  <pre>1  %h1 Currency Converter
2
3  %form(action = "/convert" method = "post")
4    %fieldset
5      %legend
6      From
7      %input#amount(name="amount")
8
9      %select#from(name="from")
10       %option(value="inr") INR
11       %option(value="usd") USD
12       %option(value="eur") EUR
13
14     To
15     %select#to(name="to")
16       %option(value="inr") INR
17       %option(value="usd") USD
18       %option(value="eur") EUR
19
20     %input#convert(type="submit" value="Convert")
</pre>
  
  <p>
    Executing the spec now fails with:
  </p>
  
  <pre>1 Unable to find css "#result"
</pre>
  
  <p>
    To fix this, we need to add <code>post "/convert"</code> handler in <code>app.rb</code>:
  </p>
  
  <pre>1 post "/convert" do
2   @result = GoogCurrency.send("#{params[:from]}_to_#{params[:to]}".to_sym, params[:amount])
3   haml :"convert"
4 end
</pre>
  
  <p>
    Line 2, we are generating the GoogCurrency method to call dynamically. <code>params[:form]</code>, <code>params[:to]</code> have the from and to currencies respectively. <code>params[:amount]</code> has the amount to convert. <code>"#{params[:from]}_to_#{params[:to]}"</code> gets converted to <code>usd_to_inr</code> in our case. But how do we invoke this method? In Ruby, we don&#8217;t invoke methods, we send a message to the object and the object responds to the message. To invoke this method we <code>send</code> message <code>usd_to_inr</code> to <code>GoogCurrency</code>, along with the method parameter (<code>amount</code>).
  </p>
  
  <p>
    Then we render <code>haml</code> template <code>convert</code>.
  </p>
  
  <p>
    <code>convert.haml</code>
  </p>
  
  <pre>1 %div
2   #{params[:amount]} #{params[:from]} =
3   %span#result= @result
4   #{params[:to]}
5
6 %a(href="/") Back
</pre>
  
  <p>
    The spec now passes.
  </p>
  
  <p>
    Now, we only have one more spec left i.e. &#8220;currency converter handles errors&#8221;. Let&#8217;s get at it.
  </p>
  
  <pre>1  it "handles errors" do
2      invalid_response =&lt;&lt;-INVALID
3      {lhs: "",rhs: "",error: "4",icc: false}
4      INVALID
5      FakeWeb.register_uri(:get,
6                           "http://www.google.com/ig/calculator?hl=en&#038;q=xyzUSD=?INR",
7                           :status => "200",
8                           :body => invalid_response)
9
10     visit '/'
11
12     fill_in "amount", :with => "xyz"
13     select "USD", :from => "from"
14     select "INR", :from => "to"
15     click_button 'Convert'
16
17     find("#error").should have_content("An error occurred: 4")
18   end
</pre>
  
  <p>
    It&#8217;s similar to the earlier spec, but <code>Fakeweb</code> now returns an error response, because the <code>amount</code> is invalid. Executing the spec now fails with:
  </p>
  
  <pre>1 Unable to find css "#error"</pre>
  
  <p>
    To make this spec pass, let&#8217;s handle the exception raised by <code>GoogCurrency</code> in <code>app.rb</code>:
  </p>
  
  <pre>1 post "/convert" do
2     begin
3       @result = GoogCurrency.send("#{params[:from]}_to_#{params[:to]}".to_sym, params[:amount])
4     rescue Exception => ex
5       @error = ex.message
6     end
7     haml :"convert"
8   end
</pre>
  
  <p>
    Here, we&#8217;re rescuing the exception and setting <code>@error</code> instance variable.
  </p>
  
  <p>
    Now in <code>convert.haml</code>, let&#8217;s display the error message.
  </p>
  
  <pre>1 -if @error
2   #error= @error
3 -else
4   %div
5     #{params[:amount]} #{params[:from]} =
6     %span#result= @result
7     #{params[:to]}
8
9 %a(href="/") Back
</pre>
  
  <p>
    All the specs now pass. Note, we haven&#8217;t opened the browser manually even once! Let&#8217;s do it and <em>hope</em> everything is fine and dandy! Execute the command <code>rackup -p 4567</code> and visit <code>localhost:4567</code>.
  </p>
  
  <p>
    That&#8217;s it!
  </p>
  
  <p class="alert">
    <em><b>Feel free to ask questions and give feedback in the comments section of this post</b>. Thanks!</em>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Girish+Sonawane" rel="tag">Girish Sonawane</a>, <a href="http://technorati.com/tag/Google+currency+API" rel="tag"> Google currency API</a>, <a href="http://technorati.com/tag/Sinatra" rel="tag"> Sinatra</a>
