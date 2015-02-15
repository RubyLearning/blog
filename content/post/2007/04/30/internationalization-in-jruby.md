---
title: Internationalization in JRuby
author: Satish Talim
date: 2007-04-30
layout: post
permalink: /2007/04/30/internationalization-in-jruby/
categories:
  - JRuby
  - Ruby
---
<div>
  <p>
    I have been using and teaching Java since 1995. The other day, I was talking to my students about Internationalization in Java.
  </p>
  
  <blockquote>
    <p>
      <i>Internationalization</i> is the process of designing an application so that it can be adapted to various languages and regions without engineering changes.
    </p>
    
    <p>
      <i>Localization</i> is the process of adapting software for a specific region or language by adding locale-specific components and translating text.
    </p>
  </blockquote>
  
  <p>
    The following is a simple example (in Java) to demonstrate how to internationalize a program so that it displays text messages in the appropriate language. Notice that the text of the messages is not hardcoded.
  </p>
  
  <pre>import java.util.*;
public class InternationalizationEx
{
  public static void main(String[] args)
  {
    String lang, country;
    Locale cLocale;
    ResourceBundle msg;

    lang = new String("de");
    country = new String("DE");

    cLocale = new Locale(lang, country);
    msg = ResourceBundle.getBundle("MessagesBundle", cLocale);

    System.out.println(msg.getString("greetings"));
    System.out.println(msg.getString("welcome"));
  }
}</pre>
  
  <p>
    To compile and run the above program, you need these source files:
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/data/MessagesBundle.properties" >MessagesBundle.properties</a>
    </li>
    <li>
      <a href="http://rubylearning.com/data/MessagesBundle_de_DE.properties" >MessagesBundle_de_DE.properties</a>
    </li>
    <li>
      <a href="http://rubylearning.com/data/MessagesBundle_en_US.properties" >MessagesBundle_en_US.properties</a>
    </li>
  </ul>
  
  <p>
    The internationalized program uses a language and a country code. In the above example the language code is de (German) and the country code is DE (Germany), so the program displays the messages in German:
  </p>
  
  <pre>java InternationalizationEx
Hallo
HeiBen Sie Willkommen nach Indien</pre>
  
  <p>
    If the language code is en (English) and the country code is US (United States), the program displays the messages in English:
  </p>
  
  <pre>java InternationalizationEx
Hello
Welcome to India</pre>
  
  <p>
    The arguments passed to the getBundle method identify which properties file will be accessed. The first argument, MessagesBundle, refers to this family of properties files:
  </p>
  
  <ul>
    <li>
      MessagesBundle_de_DE.properties
    </li>
    <li>
      MessagesBundle_en_US.properties
    </li>
  </ul>
  
  <p>
    The Locale, which is the second argument of getBundle, specifies which of the MessagesBundle files is chosen. When the Locale was created, the language code and the country code were passed to its constructor. Note that the language and country codes follow MessagesBundle in the names of the properties files.
  </p>
  
  <p>
    You may be wondering what&#8217;s the point of this post and that too about code in Java, whereas RubyLearning.com is a blog that talks about Ruby and Rails!
  </p>
  
  <h4>
    Internationalization in JRuby
  </h4>
  
  <p>
    Well, since I am currently exploring JRuby, I wanted to call these Java classes in Ruby using JRuby. In Ruby, one can use Masao Mutoh&#8217;s <a href="http://www.yotabanana.com/hiki/ruby-gettext.html" >Ruby-GetText-Package</a> to do the same, though personally I find it quite cumbersome to use.
  </p>
  
  <p>
    So here&#8217;s JRuby to my rescue! The program code in JRuby is:
  </p>
  
  <pre>#javaInternational.rb
require 'java'

module JavaLang
  include_package "java.lang"
end

ResourceBundle = java.util.ResourceBundle
Locale = java.util.Locale

lang = JavaLang::String.new("de")
country = JavaLang::String.new("DE")

cLocale = Locale.new(lang, country)
msg = ResourceBundle.getBundle("MessagesBundle", cLocale)

puts msg.getString("greetings")
puts msg.getString("welcome")
</pre>
  
  <p>
    Run the program on a command prompt as follows:
  </p>
  
  <pre>jruby javaInternational.rb</pre>
  
  <p>
    It works! Okay, a little explanation of some of the JRuby code &#8211; There can be name clashes between Java class names and Ruby class names. String is an example of this; Java has java.util.String and Ruby also has Kernel::String. To resolve this name clash, define a Ruby module that includes the Java class definition as follows:
  </p>
  
  <pre>module JavaLang
  include_package "java.lang"
end</pre>
  
  <p>
    If you know Java and have started using Ruby, please do explore JRuby &#8211; you shall not be disappointed.
  </p>
</div>

<div>
  <a href="http://technorati.com/tag/Instant+Rails" rel="tag"></a><a href="http://technorati.com/tag/Quick+Ruby" rel="tag"></a><a href="http://technorati.com/tag/Instant+Rails" rel="tag"></a><a href="http://technorati.com/tag/Pune+Ruby" rel="tag"></a><a href="http://technorati.com/tag/Quick+Ruby+Guide" rel="tag"></a><a href="http://technorati.com/tag/Programming+Languages" rel="tag"></a><a href="http://technorati.com/tag/Blogs" rel="tag"></a><a href="http://technorati.com/tag/Ruby" rel="tag"></a><a href="http://technorati.com/tag/PuneRuby" rel="tag"></a><a href="http://technorati.com/tag/QuickRuby" rel="tag"></a><a href="http://technorati.com/tag/PuneBloggers" rel="tag"></a><a href="http://technorati.com/tag/PuneBlogs" rel="tag"></a><a href="http://technorati.com/tag/Blogosphere" rel="tag"></a><a href="http://technorati.com/tag/Digg" rel="tag"></a><a href="http://technorati.com/tag/Media" rel="tag"></a><a href="http://technorati.com/tag/Tip" rel="tag"></a><a href="http://technorati.com/tag/RSS" rel="tag"></a><a href="http://technorati.com/tag/Marketing" rel="tag"></a><a href="http://technorati.com/tag/News" rel="tag"></a><a href="http://technorati.com/tag/IndianGuru" rel="tag"></a><a href="http://technorati.com/tag/Blogging" rel="tag"></a><a href="http://technorati.com/tag/Internet" rel="tag"></a><a href="http://technorati.com/tag/Blog" rel="tag"></a><a href="http://technorati.com/tag/Technical+Support" rel="tag"></a><a href="http://technorati.com/tag/Free+Software" rel="tag"></a><a href="http://technorati.com/tag/Help" rel="tag"></a><a href="http://technorati.com/tag/Pune" rel="tag"></a><a href="http://technorati.com/tag/SatishTalim" rel="tag"></a><a href="http://technorati.com/tag/Satish+Talim" rel="tag"></a><a href="http://technorati.com/tag/Weblog" rel="tag"></a><a href="http://technorati.com/tag/Weblogs" rel="tag"></a><a href="http://technorati.com/tag/Training" rel="tag"></a><a href="http://technorati.com/tag/Free+Training" rel="tag"></a><a href="http://technorati.com/tag/Tutorial" rel="tag"></a><a href="http://technorati.com/tag/Education" rel="tag"></a><a href="http://technorati.com/tag/Teacher" rel="tag"></a><a href="http://technorati.com/tag/Learning+Ruby" rel="tag"></a>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Internationalization+in+JRuby" rel="tag">Internationalization in JRuby</a>, <a href="http://technorati.com/tag/JRuby" rel="tag">JRuby</a>, <a href="http://technorati.com/tag/Java" rel="tag">Java</a>, <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>
