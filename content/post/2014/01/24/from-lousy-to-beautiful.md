---
title: From Lousy to Beautiful
author: James Schorr
date: 2014-01-24
layout: post
permalink: /2014/01/24/from-lousy-to-beautiful/
thesis_description:
  - 'James M. Schorr shows you how to write beautiful code in Ruby. '
thesis_keywords:
  - James M. Schorr, Ruby
topsy_short_url:
  - http://bit.ly/19Rrujj
categories:
  - Beginners
  - Ruby
tags:
  - James M. Schorr
  - Ruby
---
This guest post is by **James Schorr**, who has been developing software
since 1999. He is the owner of an IT consulting company, [Enspiren IT
Consulting, LLC](https://enspirenconsulting.com).  He lives with his
lovely wife, Tara, and their children in Kansas City, Missouri. James
spends a lot of time writing code in many languages, doing IT security
audits, and has a passion for Ruby on Rails in particular. He also loves
spending time with his family, playing chess, going to the shooting
range, hiking, fishing, and investing. His professional profile is
on [LinkedIn](http://www.linkedin.com/in/jamesschorr).

![James M. Schorr](http://rubylearning.com/images/James_Schorr.png) Due
to the inherent flexibility of Ruby, there are often several ways of
doing the same thing. But how do you recognize the best way, the
“beautiful” way to go about something? It can be tough to describe and
there may indeed be several “best ways” to do something. The ease of
expressing real life through Ruby can give us a false sense of security.
I have come to realize that terrible code can be written — even with
such a beautiful language.

Let us work through a simple example together. In our example, we’re
calling a remote API service with
[`HTTParty`](https://github.com/jnunemaker/httparty), and parsing
through the JSON response, which consists of a simple array of stats,
which we’ll refer to as “Today’s Stats”. Please note that comments in
the code intended just for the reader of this article will be prefaced
with ‘\#\# Reader’. Hopefully, you’ll see the progression of the code’s
quality as we go.

Here’s our first attempt, which is pretty lousy. Can you spot a few of
the reasons why?

## Attempt 1 – Blind Trust

```ruby
module StatsApi
  require 'json'
  require 'httparty'
  require 'jsonpath'

  def find_users_stats(users_handle)
    params = { user: users_handle }
    a = HTTParty.get('http://928just-a-bogus-example-site.com/stats', params)
    t = JsonPath.on(a.body, '$.').first
    u = t.select {|k,v| k['user'] == users_handle }.first
    @users_stats = u['stats']
  end
end
```

Did you spot the issues? There are quite a few, some that affect us now
and some that might affect us in the future. For now, let’s focus on the
most pressing, immediate issues:

1.  We are trusting that our call to the API will succeed.
2.  We are trusting that the account that we pull back will indeed have
    the user that we’re looking for.
3.  In both cases, we are then attempting to parse through the data that
    may not even make it back to us or have what we expect it to have.
4.  What does ‘a’, ‘t’, and ‘u’ represent? Would the next developer
    working on this code know what I’m referring to? While it saves
    space, it isn’t very friendly to the next developer.

## Attempt 2 – Handling the Unexpected

```
module StatsApi
  require 'json'
  require 'httparty'
  require 'active_support/core_ext/string' ## Reader: provides .present? and .blank?
  require 'jsonpath'

   def find_users_stats(users_handle)
    params = { user: users_handle }

    a = HTTParty.get('http://928just-a-bogus-example-site.com/stats', params)
    ## Reader: .present? (or .blank? when appropriate) can be nice to use as they checks for more than just nil.
    ## Additionally, we make sure that 'a' is 'present?' before calling 'response' on it.
    if a.code == 200
      todays_stats = JsonPath.on(a.body, '$.').first
      if todays_stats.present?
        users_info = todays_stats.select {|k,v| k['user'] == users_handle }.first
        if users_info.present?
          @users_stats = users_info['stats']
        end
      end
    end
  end
end
```

Now we seem to have solved a couple of issues, but this code could still
be improved a bit. Notice that:

1.  Nothing is returned if the call to the API fails or the user’s stats
    aren’t found. Now, of course in the code that calls this method, we
    could handle that there but is that the “beautiful” thing to do?
    Perhaps in the future we’ll have 10 areas in our code that call this
    method.
2.  Nested if statements are present — ugh. When I was newer to Ruby, I
    would often write a lot of these; reading through them months later
    made my head hurt. It certainly wasn’t beautiful to look at and made
    it tough to follow as more logic was added over time. Thankfully,
    there is a better way.
3.  Note that we could add more conditionals to ‘a’ to ensure that
    [`HTTParty`](https://github.com/jnunemaker/httparty) returned a
    response correctly, but we’re going to choose not to as it’s a
    well-tested gem.

## Attempt 3 – Bringing Clarity

```
module StatsApi
  require 'json'
  require 'httparty'
  require 'active_support/core_ext/string'
  require 'jsonpath'

  def find_users_stats(users_handle)
    # This will call the Stats API and pull back the user's stats.
    params = { user: users_handle }

    todays_stats = HTTParty.get('http://928just-a-bogus-example-site.com/stats', params)
    raise "Today's Stats not found." if todays_stats.code != 200

     # Finding the User's information...
    users_info = todays_stats.select {|k,v| k['user'] == users_handle }.first
    raise "User's stats not found." if users_info.blank?

    # Determining the User's Stats...
    @users_stats = users_info['stats']
  end
end
```

Okay, we’re getting closer. Now we have ‘todays\_stats’ and
‘users\_info’ in the code so that it’s more  clear as to what we’re
referring to and an appropriate error message is returned if the account
or user are now found. Notice how we added a little white-space and
comments to make it easier to read. However, we’re still calling the API
and also parsing through stats in this one method. This might be fine
for now if we only call the API for one purpose. But what about the
future? What if a need arises to adjust the stats, add new stats, etc…
via the API?

Let’s try to future-proof our code a bit by making it more flexible and
configurable. We’ll use the excellent
[Settingslogic](https://github.com/binarylogic/settingslogic) gem (you
can add that yourself) to make the API settings configurable. This will
help when the Stats API’s URL, version, etc… changes. We’ll also add a
method to adjust the user’s stats and one that performs the actual API
call. Notice how we can accomplish this by using ‘send’. Thus the
various HTTP verbs can all be used as desired while keeping the code
pretty DRY.

## Attempt 4 – Sustainability

```
module StatsApi
  require 'json'
  require 'httparty'
  require 'active_support/core_ext/string'
  require 'jsonpath'

  def find_users_stats(users_handle)
    params = { user: users_handle }
    call_stats_api('get', 200, true, params)
    raise @error = 'Account not found.' unless @call_succeeded

    todays_stats = JsonPath.on(@result.body, '$.').first
    raise @error = "Today's Stats were not found." if todays_stats.blank?
    users_info = todays_stats.select {|k,v| k['user'] == users_handle }.first
    raise @error = "User's Stats not found." if users_info.blank?

    @users_stats = users_info['stats']
  end

  def adjust_users_stats(new_stats)
    call_stats_api('put', 201, new_stats)
    raise @error = 'Stats adjustment failed.' unless @call_succeeded
  end

  private
  def call_stats_api(http_verb, success_code, response_body_reqd=false, data=nil)
    begin
      params = { headers: AppSettings::Api.stats_headers, version: AppSettings::Api.stats_version,
                 format: AppSettings::Api.stats_format }
      raise 'Invalid data received' unless data.is_a?(Hash)
      params[:body] = data.to_json
      @result = HTTParty.send(http_verb, AppSettings::Api.stats_url, params)
      code_matches = @result.code == success_code
      @call_succeeded = response_body_reqd ? @result.body.present? && code_matches :
                                             code_matches
    rescue => e
      @error = e
      Rails.logger.error("Sorry, an error occurred: #{e}")
    end
  end
end
```

Now our code is quite a bit more flexible, configurable, and easier to
maintain.  Let’s add some comments in to explain to the next developer
what’s going on.

## Attempt 5 – Clarity

### module StatsApi

```
require 'json'
require 'httparty'
require 'active_support/core_ext/string'
require 'jsonpath'

## Reader: note that @error is raised so that we can easily handle that in our parent methods...

def find_users_stats(users_handle)
  # This will call the Stats API and pull back the user's stats.
  # All of the API settings are found in config/settings/api.yml.

  # Finding the Account...
  params = { user: users_handle }
  call_stats_api('get', 200, true, params)
  ## Reader: note that the following line is optional as you could have conditional code in
  ## the parental method based on @call_succeeded.
  raise @error = 'Account not found.' unless @call_succeeded

  # Finding the User's information...
  ## Reader note that we raise @error so that we can easily handle that in our parent methods...
  todays_stats = JsonPath.on(@result.body, '$.').first
  raise @error = "Today's Stats were not found." if todays_stats.blank?
  users_info = todays_stats.select {|k,v| k['user'] == users_handle }.first
  raise @error = "User's Stats not found." if users_info.blank?

  # Determining the User's Stats...
  @users_stats = users_info['stats']
end

def adjust_users_stats(new_stats)
  # Adjusts the users stats with the new_stats Hash.
  call_stats_api('put', 201, new_stats)
  ## Reader: note that the following line is optional as you could have conditional code in
  ## the parental method based on @call_succeeded.
  raise @error = 'Stats adjustment failed.' unless @call_succeeded
end

private
def call_stats_api(http_verb, success_code, response_body_reqd=false, data=nil)
  begin
    # This calls the Stats API, passing along the necessary params. The data refers to what
    # should go in the JSON payload.  The success_code is the desired code that the parent method
    # would consider to be 'successful'.  This allows us to pass in the actual HTTP status codes
    # that the 3rd party API returns.
    ## Reader: Note that the various Settings mentioned below reference the
    ## config/settings/api.yml file in order to make it very easy to change things in the future.

    ## Optional but more future-proof; these don't have to be configurable but probably should be:
    params = { headers: AppSettings::Api.stats_headers, version: AppSettings::Api.stats_version,
               format: AppSettings::Api.stats_format }

    # Adding the JSON data to the params...
    ## Reader: notice that we don't blindly trust that the data parameter is indeed
    ## a hash; what if something else was sent to this method by mistake?
    raise 'Invalid data received' unless data.is_a?(Hash)
    params[:body] = data.to_json

    ## Reader: notice that we use Object's 'send' so that we only need one method
    ## for API calls with the desired HTTP verb. The following line will be what's
    ## returned to the parent method.

    ## Optional (you can just write in the URL if you wish) but more future-proof:
    @result = HTTParty.send(http_verb, AppSettings::Api.stats_url, params)

    # Determining the success of the response.
    code_matches = @result.code == success_code

    ## Reader: if the response_body_reqd is set, then a call is only considered successful if the
    ## response code matches and the body has data in it. Otherwise, only a matching code is considered
    ## successful.
    @call_succeeded = response_body_reqd ? @result.body.present? && code_matches :
                                           code_matches
    rescue => e
      ## Reader: notice that in production-ready code, we'd never return the real error message to the
      ## end user as it would expose too much and not be very human friendly.  It would probably be best
      ## to just return a "human-friendly" error message and log the atual one.
      @error = e
      Rails.logger.error("Sorry, an error occurred: #{e}")
    end
  end
end
```

There are a few spots where we could probably get away with removing our
comments since the variables are so aptly named. We could also (and
should if there are needs for other types of APIs to be called) create a
new class that calls APIs. We’ll leave that for another day, though.

In general, though, our code has improved quite a bit.

Here are a few Ruby resources that I would like to recommend (discounts
given with author’s permission):

-   [The Ultimate Guide to Ruby Programming](http://t.co/z8zgvNddf5) by
    Satish Talim (50% off)
-   [Confident Ruby](http://www.confidentruby.com/) by Avdi Grimm (use
    promo code RUBYLEARN14 for 20% off)
-   [Exceptional Ruby](http://www.exceptionalruby.com/) by Avdi Grimm
    (use promo code RUBYLEARN14 for 20% off)
-   [Ruby Tapas Sreencasts](https://rubytapas.dpdcart.com/subscriber/content) by
    Avdi Grimm
-   [Eloquent Ruby](http://www.amazon.com/Eloquent-Ruby-Addison-Wesley-Professional-Series/dp/0321584104) by
    Russ Olsen
-   [The Ruby Way](http://www.amazon.com/The-Ruby-Way-Second-Edition/dp/0672328844) by
    Hal Fulton

*Feel free to ask questions and give feedback in the comments section of
this post. Thanks!*

Technorati Tags: [James M.
Schorr](http://technorati.com/tag/James+M.+Schorr)

