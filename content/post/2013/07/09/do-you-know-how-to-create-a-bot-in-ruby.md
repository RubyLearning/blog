---
draft: false
title: Do you know how to create a bot in Ruby?
date: 2013-07-09
author: Apoorv Saxena
categories:
- ruby
layout: post
permalink: /2013/07/09/do-you-know-how-to-create-a-bot-in-ruby/
tags:
- apoorv saxena
- bot
- programming
- ruby
---
This guest post is by Apoorv Saxena. He’s a Ruby Enthusiast, and has
been coding in Ruby since 2009. In his free time, he builds hacks using
Ruby and JavaScript; latest being [Advanced Search for
Facebook](https://advancedsearch.in/). He likes to
[blog](https://apoorv.quora.com/) about Sinatra, Ruby, Digital Marketing
and Programming concepts.<!--more--> He would love to hear from you on [Google
Plus](https://plus.google.com/102770387697474092552/about) or through
[mail](mailto:root@apoorv.pro).

## Introduction

![Apoorv Saxena](http://rubylearning.com/images/apoorvsaxena.jpg) **A**
bot can be defined as a continuously running script that is responsible
for performing a specific task regularly or respond to an action
triggered on a specific event. Bots are targeted to perform an action
that is repetitive in nature or has a limited number of events to
respond. See the [Wikipedia
article](http://en.wikipedia.org/wiki/Internet_bot) on bots that
describes the different types of bots built to perform a variety of
different tasks.

Today, we are going to create a bot that repeats a certain task after
every X mins of time. The repetitive task that we have chosen to
perform, is to get the links of the Most Trending Stories on Internet in
Real Time (using Bitly’s Social Data APIs) and display them on our
command line. Our bot will also send notification pop-ups on our screen
whenever it fetches the latest data after every X mins of time. We will
name our bot as `Bitly-Bot` as it uses Bitly’s APIs to bring us Trending
Data in Real Time.

[![OurBot](http://rubylearning.com/blog/media/OurBot.png "OurBot")](http://rubylearning.com/blog/media/OurBot.png)

OurBot

## Running Bitly-Bot

You can clone Bitly Bot’s Code from
[GitHub](https://github.com/ApoorvSaxena/Bitly-Bot) for reference and
run it as well on your machine, it contains the instructions to setup
Bitly-Bot on your local machine, it also contains the links to create
Bitly Application (required to access Bitly’s Social Data APIs) and
install Growl Application on your Mac OS X (to send notification pop-ups
from Bitly-Bot).

## Understanding the Working of Bitly-Bot

We start with the initialization of a class named `Bitly` that is
responsible for handling the API calls interaction, it sends request to
Bitly  containing our Application Generic Access token, to validate our
application and fetches the Hot and Bursting Topics data along with the
Most Trending Story links associated with these topics in JSON format.
We have used Threads to make two network API calls simultaneously to
Bitly(one to bring Hot Topics and the other to bring Bursting Topics),
instead of triggering them sequentially, thus saving us time and
patience to see our Bot’s response.

    class Bitly

      def initialize()
        @access_token = $config['access_token']
        @colorize = Colorize.new
      end

      def get_url(phrase)
        @base_url = "https://api-ssl.bitly.com/v3/realtime/#{phrase}_phrases?access_token=#{@access_token}"
      end

      def get_topics(phrase_types)
        threads = []
        phrase_types.each do |phrase_type|
          base_url = get_url phrase_type
          threads << Thread.new(base_url, phrase_type) do |url, phrase_type|
            begin
              response = JSON.parse RestClient.get url
              if response['status_code'] != 200
                puts  @colorize.display 'Error: ' + response['status_txt'] + '\n', :error
                exit
              end
              display response,phrase_type
            rescue
              display_error_message
            end
            puts "\n\n"
          end
        end
        threads.each { |aThread|  aThread.join }
      end

      def display(response,phrase_type)
        puts GrowlNotifications.display "#{phrase_type.capitalize} Topics"
        puts @colorize.display "#{phrase_type.capitalize} Topics", :heading
        response['data']['phrases'].each do |data|
          puts @colorize.display("#{data['phrase']}", :text) + " " + @colorize.display("http://bit.ly/#{data['ghashes'][0]['ghash']}", :link)
        end
      end

      def display_error_message
       puts @colorize.display 'Unable to connect to the Server', :error
       exit
      end

    end

We have a class named `Colorize` which contains a method named `display`
that displays the different parts of APIs response in different colors,
while also colorizing an error message that is displayed when we are not
able to connect to Bitly. Another class named `GrowlNotifications`
simply echoes a text on the terminal that contains the code which
triggers the Growl Notifications on Mac OS X.

    class Colorize
      def display(text, element)
        color_code = case element
          when :text
            ['1;','32;','40m']
          when :heading
            ['1;','33;','40m']
          when :error
            ['1;','','31m']
          when :link
            ['4;','31;','48m']
        end
        "33[#{color_code[0]}#{color_code[1]}#{color_code[2]}#{text}33[0m"
      end
    end  

    class GrowlNotifications
      def self.display(text)
        "\e]9;#{text}07"
      end
    end

Now that we have finished writing our bot script, we would like to run
it as a Daemon in a terminal window. Most processes that run as Daemon,
are run as background jobs, however, in our case, we would like to see
the Trending Topics links inside our terminal window, for which the
daemon has to run in the current terminal window in which it is started.
We specify the bot to run in our current terminal window by giving an
additional parameter `ontop` when writing the code to run our Daemon.

    Daemons.run('application.rb', {:ontop => true, :app_name => 'Bitly-Bot'})

Now we code our application to run continuously with a delay of X
minutes while controlling it via our Daemon process.

    loop do
      Bitly.new.get_topics ['bursting', 'hot']
      sleep $config['delay'] * 60 # delaying in minutes
    end

That’s it! We are ready to receive Trending Story Links from our Bot
after every X mins, along with Notification Popups and Colored Output to
grab our attention.

*I hope this article explains and motivates you enough to create a bot
in Ruby by yourself, and explore the amazing stuff that you can perform
with a bot at your disposal. Feel free to ask questions and give
feedback in the comments section of this post. Thanks!*
