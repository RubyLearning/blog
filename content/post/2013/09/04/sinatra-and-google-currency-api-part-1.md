---
title: 'Sinatra and Google currency API - Part 1'
author: Girish Sonawane
date: "2013-09-04"
layout: post
permalink: /2013/09/04/sinatra-and-google-currency-api-part-1/
thesis_description:
  - Learn how to use the Google currency API in this two part blog post on RubyLearning.
thesis_keywords:
  - Girish Sonawane, Google currency API
topsy_short_url:
  - http://bit.ly/1fyoZzh
categories:
  - ruby
  - sinatra
tags:
  - girish sonawane
  - google currency api
---
<div>
  <h2>
    Sinatra and Google currency API &#8211; Part 1
  </h2>
  
  <p class="update">
    This guest post is contributed by <b>Girish Sonawane</b>, a self-taught programmer. He came across Ruby in 2008 and has since been working full-time on Ruby. He worked as a Rails freelancer and later co-founded <a href="http://cuberoot.in/">Cube Root</a>, an exclusive Ruby on Rails software boutique catering to outsourced work. His interests are everything related to technology or science. You can reach him at <a href="mailto:girish@cuberoot.in">girish@cuberoot.in</a> or via twitter @girishso.
  </p>
  
  <p class="block">
    <img class="alignright" alt="Girish Sonawane" src="http://rubylearning.com/images/girishsonawane.png" width="125" height="125" /> <strong><span class="drop_cap">I</span></strong>n this two-part series, I will show you how to use the Google currency conversion API and use it in a small Sinatra app. This is Part 1, where<br /> we focus on using the API in Ruby. The source code for this series is available on <a href="https://github.com/girishso/goog_currency_tutorial">Github</a>, with commits for each step. This little library is available as a Ruby Gem at <a href="https://rubygems.org/gems/goog_currency">GoogCurrency</a>.
  </p>
  
  <p>
    The common need for e-commerce websites is to show the <em>price</em> of items in <strong>local</strong> currency rather than showing it up in US Dollars. It&#8217;s a very tedious job to convert price from one currency to another in this volatile market. To make your price up to date you need a <em>tool</em> to convert amount in realtime. Google has provided the currency conversion API. In this post I will show you how easy it is to use the Google&#8217;s API for this purpose. Here, we will develop a small function to use this API and then use it in a small Sinatra app in Part 2.
  </p>
  
  <h3>
    The API
  </h3>
  
  <p>
    We are going to use following Google API for currency conversion.
  </p>
  
  <pre>1 curl "http://www.google.com/ig/calculator?hl=en&#038;q=1USD=?INR"</pre>
  
  <p>
    The API accepts <code>q</code> the amount from the currency symbol <code>USD</code> and to the currency symbol prefixed with a question mark <code>?INR</code>.
  </p>
  
  <p>
    It returns the following, resembling the JSON format
  </p>
  
  <pre>1 {lhs: "1 U.S. dollar",rhs: "54.836587 Indian rupees",error: "",icc: true}</pre>
  
  <p>
    To make it easy for our users, we are going to make our method names very simple for users to remember. For example, to convert currency from US Dollars (USD) to Indian Rupees (INR), we will have a <code>usd_to_inr</code> method, similarly to convert from Euros (EUR) to Japanese Yen (JPY), we will have a <code>eur_to_jpy</code> method, and so on.
  </p>
  
  <h3>
    Converting US Dollars To Indian Rupees
  </h3>
  
  <p>
    Before we get started with the coding, like all good developers we will write some specs which the code needs to pass before we say it is complete.
  </p>
  
  <p>
    <code>spec/goog_currency_spec.rb</code>
  </p>
  
  <pre>1 $LOAD_PATH.unshift(File.join(File.dirname(__FILE__), '..', 'lib'))

3 require 'fakeweb'

5 valid_response =&lt;&lt;-VALID
6   {lhs: "1 U.S. dollar",rhs: "54.836587 Indian rupees",error: "",icc: true}
7 VALID

9 describe "GoogCurrency" do
10  describe "valid currencies" do
11    it "converts USD to INR" do
12      FakeWeb.register_uri(:get,
13                           "http://www.google.com/ig/calculator?hl=en&#038;q=1USD=?INR",
14                           :status => "200",
15                           :body => valid_response)
16      usd = GoogCurrency.usd_to_inr(1)
17      usd.should == 54.836587
18    end
19   end
20 end
</pre>
  
  <p>
    We are going to use the <code>fakeweb</code> gem to simulate the Google API calls.
  </p>
  
  <p>
    Line 1, adds the lib path in Load path, so the spec can find it. Line 5, 6 and 7, stores the Google API return string as it is in valid_response variable.
  </p>
  
  <p>
    Line 9, <code>describe "GoogCurrency"</code> block, is used to group related specs. Nested <code>describe "valid currencies"</code> block contains the valid currency specs.
  </p>
  
  <p>
    Line 11, spec for converting USD to INR.
  </p>
  
  <p>
    Line 12, uses Fakeweb to simulate the API in the spec, it returns the valid_response string on calling the API.
  </p>
  
  <p>
    Line 16, calls our actual method (that we are supposed to write).
  </p>
  
  <p>
    Line 17, tests if our method returns the actual value returned by the API.
  </p>
  
  <p>
    If we execute our spec now with <code>rspec spec/goog_currency_spec.rb</code>, it fails with:
  </p>
  
  <pre>1 uninitialized constant GoogCurrency</pre>
  
  <p>
    Since we don&#8217;t have the <code>goog_currency.rb</code> file yet. Let&#8217;s add it and define an empty GoogCurrency module.
  </p>
  
  <p>
    <code>lib/goog_currency.rb</code>
  </p>
  
  <pre>1 module GoogCurrency

3 end
</pre>
  
  <p>
    Also, add <code>require 'goog_currency'</code> in <code>goog_currency_spec.rb</code> on Line 2. Executing spec now, fails with:
  </p>
  
  <pre>1 undefined method 'usd_to_inr' for GoogCurrency:Module</pre>
  
  <p>
    Let’s add the method <code>usd_to_inr</code> in <code>module GoogCurrency</code>:
  </p>
  
  <pre>1 require "rest_client"
2 require "json"

4 module GoogCurrency
5   def self.usd_to_inr(amount)
6     response = RestClient.get("http://www.google.com/ig/calculator?hl=en&#038;q=#{amount}USD=?INR").body

8     # hack to convert API response to valid JSON
9     response.gsub!(/(lhs|rhs|error|icc)/, '"\1"')
10    response_hash = JSON.parse(response)
11    response_hash['rhs'].to_f
12  end
13end
</pre>
  
  <p>
    Line 6, uses <code>rest_client</code> gem to call the API passing appropriate parameters.
  </p>
  
  <p>
    The API unfortunately returns an invalid JSON. Line 9, converts it to a valid JSON. <code>String#gsub!</code> method in-place surrounds lhs, rhs, error and icc keys in response, with double quotes <code>"</code>, making it a valid JSON.
  </p>
  
  <p>
    We then parse it using parse method using <code>json</code> gem&#8217;s <code>JSON#parse</code> method. It returns us a ruby hash <code>response_hash</code>, Line 10.
  </p>
  
  <p>
    Line 11, simply picks the value of key <code>rhs</code> and converts it to float using <code>String#to_f</code> method to return converted currency value.
  </p>
  
  <p>
    We execute our spec with <code>rspec spec/goog_currency_spec.rb</code> and bravo our spec is passing! You can pat yourself on the back now.
  </p>
  
  <h3>
    Converting from any currency to any other currency
  </h3>
  
  <p>
    So we successfully used Google API to convert USD to INR. But, how do we convert USD to JPY? Let’s start with writing the spec for it.
  </p>
  
  <pre>1 it "converts USD to JPY" do
2   FakeWeb.register_uri(:get,
3                        "http://www.google.com/ig/calculator?hl=en&#038;q=1USD=?JPY",
4                        :status => "200",
5                        :body => valid_response_jpy)
6   jpy = GoogCurrency.usd_to_jpy(1)
7   jpy.should == 98.5124618
8 end
</pre>
  
  <p>
    It needs a corresponding valid API response string defined <code>valid_response_jpy</code>:
  </p>
  
  <pre>1 valid_response_jpy =&lt;&lt;-VALID
2 {lhs: "1 U.S. dollar",rhs: "98.5124618 Japanese yen",error: "",icc: true}
3 VALID
</pre>
  
  <p>
    Running the spec, fails with <code>undefined method 'usd_to_jpy'</code>. Now, we can write a method similar to usd_to_inr, but since we will have to write many such methods for each currency pair, it's not a DRY approach.
  </p>
  
  <p>
    Thanks to Ruby's metaprogramming support. We can use <code>method_missing</code> to dynamically create methods for any currency pair, that our users might need.
  </p>
  
  <p>
    Let's go ahead and write the <code>method_missing</code> in <code>GoogCurrency</code>:
  </p>
  
  <pre>1 def self.method_missing(meth, *args)
2   from, to = meth.to_s.split("_to_")

4   super(meth, *args) and return if from.nil? or from == "" or to.nil? or to == ""

6   response = RestClient.get("http://www.google.com/ig/calculator?hl=en&#038;q=#{args.first}#{from.upcase}=?#{to.upcase}").body

8   # response is not valid json
9   response.gsub!(/(lhs|rhs|error|icc)/, '"\1"')
10  response_hash = JSON.parse(response)

12  response_hash['rhs'].to_f
13end
</pre>
  
  <p>
    Line 1, <code>method_missing</code> accepts two parameters. First <code>meth</code> is a symbol the method name that is called (<code>usd_to_jpy</code> in our case) and second <code>args</code> is an array of the arguments passed to the method <code>meth</code> (<code>[1]</code> in our spec).
  </p>
  
  <p>
    We need to extract <code>to</code> and <code>from</code> currencies from the method name.
  </p>
  
  <p>
    Line 2, <code>meth.to_s</code> converts the method name symbol to string, then we call <code>String#split("_to_")</code> to convert it to an array <code>["usd", "jpy"]</code>. We then assign <code>from</code> to <code>"usd"</code> and <code>to</code> to <code>"jpy"</code>. We now have our <code>from</code> and <code>to</code> currencies.
  </p>
  
  <p>
    Line 4, in case <code>from</code> or <code>to</code> are <code>nil</code> or empty, because the user called it in a wrong way, like a good Ruby citizen we call <code>super</code> and let the parent class <code>method_missing</code> take over (which in our case raises <code>undefined method</code> error).
  </p>
  
  <p>
    Line 6, calls the API substituting the appropriate values. Since our method accepts only one parameter <code>args.first</code> returns it (<code>1</code>). <code>from</code> and <code>to</code> currencies are in lowercase but the API accepts it in uppercase, so we call <code>String#upcase</code> to convert these to uppercase.
  </p>
  
  <p>
    Rest of the lines are same as our <code>usd_to_inr</code> method.
  </p>
  
  <p>
    If we execute our specs with <code>rspec spec/goog_currency_spec.rb</code>, it passes. Now, we can convert from any currency to any other currency!
  </p>
  
  <p>
    Wait, we still have the old <code>usd_to_inr</code> method in <code>GoogCurrency</code> module. We can safely remove it, and let <code>method_missing</code> take over it. Let's go ahead and remove it, and see if the spec still passes.
  </p>
  
  <h3>
    respond_to?
  </h3>
  
  <p>
    As pointed out by Hao Liu in the comments, every <code>method_missing</code> should be accompanied with a <code>respond_to?</code> method.
  </p>
  
  <p>
    <code>respond_to?</code> method is used to determine if an object responds to a method before actually calling the method. Useful for avoiding runtime method not found errors.
  </p>
  
  <pre>def self.respond_to?(meth)
  from, to = meth.to_s.split("_to_")

  if from.nil? or from == "" or to.nil? or to == ""
    super
  else
    true
  end
end
</pre>
  
  <p>
    Here if we cannot handle a method we call <code>super</code> to let the parent class handle it.
  </p>
  
  <h3>
    Error handling
  </h3>
  
  <p>
    What good is a library if it does not handle errors graciously? What happens if the user submits a non-existent currency symbol? In that case the API returns the following, with <code>error</code> number.
  </p>
  
  <pre>1 {lhs: "",rhs: "",error: "4",icc: false}</pre>
  
  <p>
    Let's write a spec for the error condition, we also need to store the invalid error API response in a ruby variable:
  </p>
  
  <pre>1 invalid_response =&lt;&lt;-INVALID
2 {lhs: "",rhs: "",error: "4",icc: false}
3 INVALID

5 describe "GoogCurrency" do
6   .
7   .
8   [code omitted]
9   .
10  .
11  describe "invalid currencies" do
12    it "throws exception for USD to INX" do
13      FakeWeb.register_uri(:get,
14                           "http://www.google.com/ig/calculator?hl=en&#038;q=1USD=?INX",
15                           :status => "200",
16                           :body => invalid_response)
17      expect { GoogCurrency.usd_to_inx(1) }.to raise_error
18    end
19  end
20  .
21  .
22end
</pre>
  
  <p>
    Note we are calling method <code>usd_to_inx</code> with <code>INX</code> an invalid currency symbol. We have added a <code>describe</code> block, to group the error conditions. At Line 17, we are expecting an exception being raised. At this point, the specs fail with:
  </p>
  
  <pre>1expected Exception but nothing was raised</pre>
  
  <p>
    Now, let's go ahead and make this spec pass. Let's modify the <code>method_missing</code> to check for errors.
  </p>
  
  <pre>1 if response_hash['error'].nil? or response_hash['error'] == ""
2   response_hash['rhs'].to_f
3 else
4   raise "An error occurred: #{response_hash['error']}"
5 end
</pre>
  
  <p>
    If <code>response_hash['error']</code> is <code>nil</code> or it is blank, we return the converted amount, otherwise we raise an error, returning the error code. At this point all the specs should pass.
  </p>
  
  <p>
    Now, we are almost done with the currency conversion library, except for one little problem. So far we are only converting only small amounts, problems arise when the converted amount runs into thousands (e.g. calling <code>usd_to_inr(1000)</code>). The API at this point adds a thousands separator, and our little function fails to return the correct value. I will leave handling this special case, as an <em>assignment</em> for the readers.
  </p>
  
  <p>
    That's it for now. In <a href="http://rubylearning.com/blog/2013/09/13/sinatra-and-google-currency-api-part-2/">Part 2</a> of the blog post, we will use what we have developed so far in a small Sinatra app.
  </p>
  
  <p class="alert">
    <em><b>Feel free to ask questions and give feedback in the comments section of this post</b>. Thanks!</em>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Girish+Sonawane" rel="tag">Girish Sonawane</a>, <a href="http://technorati.com/tag/Google+currency+API" rel="tag"> Google currency API</a>
