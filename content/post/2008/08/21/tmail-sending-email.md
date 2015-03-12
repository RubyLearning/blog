---
author: Satish Talim
categories:
- Code Snippets
- Ruby
- Training
date: 2008-08-21
layout: post
metadescription:
- TMail is a library used for composing and manipulating email messages for Ruby.
metakeywords:
- Ruby Beginners,Ruby programming,Ruby tutorials,tmail,email
permalink: /2008/08/21/tmail-sending-email/
tags:
- ActionMailer
- email
- programming
- Ruby
- ruby programming
- TMail
title: 'TMail: Sending email'
topsy_short_url:
- http://bit.ly/9OdFJL
---

<div>
  <blockquote class="right">
    <p>
      TMail is a commonly used library by the ActionMailer component of Ruby
    </p>
  </blockquote>
  
  <p>
    <span class="drop_cap">T</span>he students of the <a href="http://rubylearning.org/class/">FORPC101</a> batch wanted to know how they could <strong>send an email in Ruby</strong>. Today, out of the various options available, we will have a quick look at <strong><a href="http://tmail.rubyforge.org/index.html">TMail</a></strong> &#8211; a library used for composing and manipulating email messages for Ruby.
  </p>
  
  <p class="note">
    <em><strong>TMail</strong> is designed to be an Request For Comments (RFC) compatible library. The goal of TMail is to allow you to create emails programatically without having to know about the RFCs or how they work, or what their standards are</em>.
  </p>
  
  <h3>
    Installation
  </h3>
  
  <p>
    On a Windows box, we can install the TMail gem as follows:
  </p>
  
  <pre><code>c:\>gem install tmail</code></pre>
  
  <h3>
    Sending an email
  </h3>
  
  <p>
    You first put at the top of your class:
  </p>
  
  <pre><code>require 'tmail'</code></pre>
  
  <p>
    Accessing a TMail object is done via the <strong>TMail::Mail</strong> class. As email can be fairly complex creatures, you will find a large amount of accessor and setter methods in this class!
  </p>
  
  <p>
    You then create an empty mail object by calling <strong>TMail::Mail.new</strong>. This creates a completely blank email message. To be a valid email message, you&#8217;ll need to modify the headers by simply accessing them using the accessor methods. Some of the public instance methods we use are: from, to, subject, date and body (for full details, please refer to the <a href="http://tmail.rubyforge.org/rdoc/index.html">TMail documentation</a>). For example, the documentation for the instance method subject is:<br /><strong>subject( default = nil )</strong><br />Returns the subject of the mail instance. If the subject field does not exist, returns nil by default or you can pass in as the parameter for what you want the default value to be. Example:
  </p>
  
  <pre><code>mail = TMail::Mail.new
mail.subject #=> nil
mail.subject("") #=> ""
mail.subject = "Hello"
mail.subject #=> "Hello"</code></pre>
  
  <p>
    Once the email message is created, you can call the to_s method to convert it back into a string. Then it can be sent with the <strong><a href="http://www.ruby-doc.org/stdlib/libdoc/net/smtp/rdoc/index.html">Net::SMTP</a></strong> library. The Net::SMTP library provides functionality to send internet mail via SMTP, the Simple Mail Transfer Protocol. The Net::SMTP.start method creates a new Net::SMTP object, opens a TCP connection and connects to the server. &#8216;localhost&#8217; is the IP address of your SMTP server and the port used is 25. Since we have called with a block, the newly-opened Net::SMTP object is yielded to the block, and automatically closed when the block finishes.
  </p>
  
  <p>
    Before you run the program (full code below), you need to start the SMTP server. On Windows, I prefer to download and use the <a href="http://www.softstack.com/freesmtp.html">Free SMTP Server</a> for testing. Connect your PC to the Internet, then start the Free SMTP Server program. The program will try to detect your provider&#8217;s DNS server. If a DNS server is available and the standard SMTP port #25 is free, the program will become ready to process your mail. If it is not possible to detect provider&#8217;s DNS server, the program will prompt you to enter any DNS server you know, after that if the server exists the program will become ready to process mail. If the port #25 is busy by another local SMTP server/service, the program will show you an error message. You can specify any DNS server or SMTP port by using the button Options, which is situated on the Toolbar. You should use the word &#8220;localhost&#8221; as the SMTP server host in your mail program.
  </p>
  
  <p>
    Here&#8217;s the complete program code:
  </p>
  
  <pre><code>require 'rubygems'
require 'tmail'
require 'net/smtp'

tomail = 'satishtalim@gmail.com'
frommail = 'superman@world.com'
mail = TMail::Mail.new
mail.to = tomail
mail.from = frommail
mail.subject = 'Test message'
mail.date = Time.now
mail.body = 'Thanks to Locaweb for making this possible.'


Net::SMTP.start( 'localhost', 25 ) do|smtpclient|
  smtpclient.send_message(
    mail.to_s,
    frommail,
    tomail
  )
end</code></pre>
  
  <p>
    It is to be noted that TMail is a commonly used library by the ActionMailer component of Ruby on Rails, the Nitro web framework, the Ruby-Talk mail gateway and many others.
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/ActionMailer" rel="tag">ActionMailer</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Sending+Email" rel="tag">Sending Email</a>, <a href="http://technorati.com/tag/TMail" rel="tag">TMail</a>
