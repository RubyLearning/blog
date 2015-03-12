---
author: Satish Talim
categories:
- jruby
- ruby
date: 2007-04-30
layout: post
title: Internationalization in JRuby
---

I have been using and teaching Java since 1995. The other day, I was
talking to my students about Internationalization in Java.  <!--more-->

> *Internationalization* is the process of designing an application so
> that it can be adapted to various languages and regions without
> engineering changes.
>
> *Localization* is the process of adapting software for a specific
> region or language by adding locale-specific components and
> translating text.

The following is a simple example (in Java) to demonstrate how to
internationalize a program so that it displays text messages in the
appropriate language. Notice that the text of the messages is not
hardcoded.

    import java.util.*;
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
    }

To compile and run the above program, you need these source files:

-   [MessagesBundle.properties](http://rubylearning.com/data/MessagesBundle.properties)
-   [MessagesBundle\_de\_DE.properties](http://rubylearning.com/data/MessagesBundle_de_DE.properties)
-   [MessagesBundle\_en\_US.properties](http://rubylearning.com/data/MessagesBundle_en_US.properties)

The internationalized program uses a language and a country code. In the
above example the language code is de (German) and the country code is
DE (Germany), so the program displays the messages in German:

    java InternationalizationEx
    Hallo
    HeiBen Sie Willkommen nach Indien

If the language code is en (English) and the country code is US (United
States), the program displays the messages in English:

    java InternationalizationEx
    Hello
    Welcome to India

The arguments passed to the getBundle method identify which properties
file will be accessed. The first argument, MessagesBundle, refers to
this family of properties files:

-   MessagesBundle\_de\_DE.properties
-   MessagesBundle\_en\_US.properties

The Locale, which is the second argument of getBundle, specifies which
of the MessagesBundle files is chosen. When the Locale was created, the
language code and the country code were passed to its constructor. Note
that the language and country codes follow MessagesBundle in the names
of the properties files.

You may be wondering what’s the point of this post and that too about
code in Java, whereas RubyLearning.com is a blog that talks about Ruby
and Rails!

#### Internationalization in JRuby

Well, since I am currently exploring JRuby, I wanted to call these Java
classes in Ruby using JRuby. In Ruby, one can use Masao Mutoh’s
[Ruby-GetText-Package](http://www.yotabanana.com/hiki/ruby-gettext.html)
to do the same, though personally I find it quite cumbersome to use.

So here’s JRuby to my rescue! The program code in JRuby is:

    #javaInternational.rb
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

Run the program on a command prompt as follows:

    jruby javaInternational.rb

It works! Okay, a little explanation of some of the JRuby code – There
can be name clashes between Java class names and Ruby class names.
String is an example of this; Java has java.util.String and Ruby also
has Kernel::String. To resolve this name clash, define a Ruby module
that includes the Java class definition as follows:

    module JavaLang
      include_package "java.lang"
    end

If you know Java and have started using Ruby, please do explore JRuby –
you shall not be disappointed.

Technorati Tags: [Internationalization in
JRuby](http://technorati.com/tag/Internationalization+in+JRuby),
[JRuby](http://technorati.com/tag/JRuby),
[Java](http://technorati.com/tag/Java),
[Ruby](http://technorati.com/tag/Ruby)

