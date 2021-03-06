---
title: Minimal I18n with Rails 3.2
date: 2012-07-24
author: Fabio Akita
categories:
  - Rails
  - Ruby on Rails
layout: post
permalink: /2012/07/24/minimal-i18n-with-rails-3.2/
tags:
  - fabio akita
  - I18n with Rails
  - Ruby on Rails
---
<p class="update">
This guest post is by <strong>Fabio Akita</strong>, also known as <a href="http://twitter.com/akitaonrails">akitaonrails</a>. He is a known Brazilian Ruby Activist and has been the program chairman for <a href="http://www.rubyconf.com.br/en">Rubyconf Brazil 2012</a> for the last 5 years. He also co-founded <a href="http://www.codeminer42.com">Codeminer 42</a>, a software boutique specialized in taking care of outsourced work from fledgling startups that need great Rails developers. Fabio has been publicly evangelizing Ruby, Rails and agile techniques since 2006 and has talked around 100 times in conferences around the globe.
</p>

<p class="block">
<img class="alignright" src="http://www.rubylearning.com/images/akita.jpg" alt="Fabio Akita" width="125" height="125" /> <span class="drop_cap">I</span>f you don't know me, I'm natural from Brazil where we speak Brazilian Portuguese. If you're from outside of the USA, it's likely that you bump into the same issues as I do when writing apps that wants to achieve worldwide repercussion: internationalization and localization. Problem is, most developers are careless about it and start writing code with English and Portuguese all mixed up. And when the time comes to explicitly support both, we have to go deep intervention in the code to extract all the particular language bits into manageable structures.
</p>

<p>
Even though both Ruby and Ruby on Rails have gone through lots of improvements in this regard, several developers are still uncertain on how to properly use those features. One thing in particular, when talking about multi-cultural apps, there is more to it than just translating strings. Bear in mind that there is both <a href="http://en.wikipedia.org/wiki/Internationalization_and_localization">Localization (L10n) and Internationalization (I18n)</a>. I won't go too deep into the matters of L10n but if you're building the next multi-cultural app, keep that in mind.
</p>

<p>
I've posted all the code I'll use in this article to my Github account, you can <a href="https://github.com/akitaonrails/Rails-3-I18n-Demonstration">check it out here</a> and you can also see a live version at my Heroku free account <a href="http://i18n-demo.herokuapp.com/">here</a>.
</p>

<p>
Let's start with the basics:
</p>

## Database and string codification

<p>
I don't intend to repeat all that has been discussed in the past about encodings, unicode, UTF8 and everything that is now properly and fully supported on Ruby 1.9. If you didn't follow that thread, I highly recommend you start reading Yehuda Katz's great articles:
</p>

<ul>
<li>
<a href="http://yehudakatz.com/2010/05/05/ruby-1-9-encodings-a-primer-and-the-solution-for-rails/">Ruby 1.9 Encodings: A Primer and the Solution for Rails</a>
</li>
<li>
<a href="http://yehudakatz.com/2010/05/17/encodings-unabridged/">Encodings, Unabridged</a>
</li>
</ul>

<p>
If you're from countries that have English as the natural language, keep in mind one thing about Unicode and Latin1 encodings &#8211; from <a href="http://en.wikipedia.org/wiki/ASCII">Wikipedia</a>:
</p>

<blockquote>
<p>
To allow backward compatibility, the 128 ASCII and 256 ISO-8859-1 (Latin 1) characters are assigned Unicode/UCS code points that are the same as their codes in the earlier standards. Therefore, ASCII can be considered a 7-bit encoding scheme for a very small subset of Unicode/UCS, and, conversely, the UTF-8 encoding forms are binary-compatible with ASCII for code points below 128, meaning all ASCII is valid UTF-8. The other encoding forms resemble ASCII in how they represent the first 128 characters of Unicode, but use 16 or 32 bits per character, so they require conversion for compatibility (similarly UCS-2 is upwards compatible with UTF-16).
</p>
</blockquote>

<p>
Bottomline is that if you forget to deal with UTF8 and fallback to Latin1, you won't notice for a long time. Most modern systems: databases, text editors, etc already default to UTF8, but some don't. First things first: make sure you're saving your source code files as UTF8. Second: make sure your database was created with UTF8 support. For example, if you create your Rails app databases using the standard <tt>rake db:create</tt>, you're safe to have it as UTF8 but if you create them manually using your database command line tool, enforce UTF8. On MySQL you must do:
</p>
```
```EATE DATABASE dbname
CHARACTER SET utf8
COLLATE utf8_general_ci;
```

<p>
On PostgreSQL you must do:
</p>

```
CREATE DATABASE dbname
WITH OWNER "postgres"
ENCODING 'UTF8'
LC_COLLATE = 'en_US.UTF-8'
LC_CTYPE = 'en_US.UTF-8';
```

<p>
Obviously, change <tt>dbname</tt> and <tt>postgres</tt> accordingly. Don't mix up! If you're dealing with text, make sure your code, Ruby gems you depend on, all use UTF8. It was a much harder experience 2 years ago, but now that the community has committed to Ruby 1.9, you won't notice it most of the time.
</p>

<p>
About the source code, even if you save your file as UTF8 you have to take one extra care. If you're writing text in languages that need special characters, you must start your file with one the following lines:
</p>

```
# encoding: UTF-8
# coding: UTF-8
# -*- coding: UTF-8 -*-
# -*- coding: utf-8 -*-
```

<p>
Choose one and use just one, they all work the same and they instruct the Ruby interpreter to properly handle the special characters. Ruby will warn you of that if you try to run source code with non-English characters in it.
</p>

<p>
But I might add that most of the time, in a Rails app, having to add one of these lines can be considered a &#8220;code smell&#8221;. That's because you should've extracted that non-English text into external i18n files and your Ruby code should be free of language-specific text. So use this is you must, but in everyday programming you should extract those strings.
</p>

<p>
And an extra recommendation: people sometimes discuss whether we should write the code itself in our native languages or default to English. I hardly recommend that you must default to English for things such as class names, methods names, variables names, even documentation in comments within the code. We live in a globalized world and the market has already defaulted to English, so keep the pseudo-patriotic discussions for other places. In code you write in English. You never know when a foreigner might join your team. You never know when you will have to join a foreign team. Do not limit neither your code nor yourself.
</p>

## Starting a new Rails app

<p>
I'll assume you already at least the very basics on how to bootstrap a new Rails app. The official Rails support for I18n started at Rails 2.2, and the great Rails Guides has a very good introduction on <a href="http://guides.rubyonrails.org/i18n.html">Rails Internationalization API</a>. I'll assume that you read and understood it all so not to repeat what's already nicely explained there. The idea is to enhance on some of the points that I feel people still have a hard time dealing with.
</p>

<p>
L10n wise, you should start customizing your app by modifying the <tt>config/application.rb</tt>, approximately around line 28 to become something like the following snippet:
</p>

```
# Set Time.zone default to the specified zone and make Active Record auto-convert to this zone.
# Run "rake -D time" for a list of tasks for finding time zone names. Default is UTC.
config.time_zone = 'Brasilia'

# The default locale is :en and all translations from config/locales/*.rb,yml are auto loaded.
# config.i18n.load_path += Dir[Rails.root.join('my', 'locales', '*.{rb,yml}').to_s]
config.i18n.available_locales = [:en, :"pt-BR"]
config.i18n.default_locale = :"pt-BR"

# Configure the default encoding used in templates for Ruby 1.9.
config.encoding = "utf-8"
```

<p>
Throughout this article, I'll use Brazilian Portuguese and Brazil as an example non-English language and culture. You have to change it accordingly to your country. Time zone is one point that always confuses everybody, but the bottom line is that your database should always record date and time in UTC, the Greenwich GMT-0. I live in the &#8220;Brazilia&#8221;, which is GMT-3. That means that while in Greenwhich it's noon, in Brazil it's 9 AM. And I have an extra problem: my country is big enough to have 3 different time zones and Daylight Savings. Rails' ActiveSupport already does a decent job overriding what it must in order for you to be able to operate on dates and times regardless of their time zones because all basic operations goes through UTC.
</p>

<p>
Take this code (running within Rails console to have ActiveSupport already activated):
</p>

```
>> Time.zone = 'Brasilia'
=> "Brasilia"
>> t1 = Time.zone.local(2012,7,13,12,0,0)
=> Fri, 13 Jul 2012 12:00:00 BRT -03:00

>> Time.zone = 'Tokyo'
=> "Tokyo"
>> t2 = Time.zone.local(2012,7,13,12,0,0)
=> Fri, 13 Jul 2012 12:00:00 JST +09:00

[21] pry(main)> t1 - t2
=> 43200.0
[25] pry(main)> (t1 - t2) / 1.day
=> 0.5
```

<p>
We are using the exact same input date and time, 7/13/2012 12:00:00 PM. But when we create 2 Time objects using different time zones, you can see that the subtraction of both objects gives a 12 hours difference (which is the actual time difference between Brazil and Japan). Now, you can have people on both countries write in their local times and have operations that respect that difference.
</p>

<p>
But I digress. Coming back to Rails i18n support, you will read in the guides that the default location for translated strings is within <tt>config/locales</tt>. And you can have 2 difference kinds of files: Ruby or YAML. I recommend using YAML files but this is more a personal taste. You can even mix locale files in YAML and Ruby.
</p>

<p>
Now, Rails itself is internationalized, defaulting to English. So all ActiveRecord's validation messages, for example, are already properly extracted. One Rubyist that have been pitching about i18n support a long time ago is <a href="http://svenfuchs.com">Sven Fuchs</a> and he maintains a repository of i18n goodies for you to explore called <a href="https://github.com/svenfuchs/rails-i18n">rails-i18n</a>. There you will find the files needed to translate the Rails framework itself. And if your country/language is not there, please contribute back.
</p>

<p>
In my case, I'm interested in the Brazilian Portuguese translations, you can download it like this:
</p>

```
curl https://raw.github.com/svenfuchs/rails-i18n/master/rails/locale/pt-BR.yml > config/locales/rails.pt-BR.yml
```

<p>
Those locale files don't only add translated strings, it also starts the basics of L10n by properly adding data formats. Check out this <a href="https://github.com/akitaonrails/Rails-3-I18n-Demonstration/blob/master/app/views/welcome/index.html.erb">example view template</a> in my demonstration app.
</p>

<table>
<tr>
<td>
Rails commands
</td>

<td>
Output in English
</td>

<td>
Output in Brazilian Portuguese
</td>
</tr>

<tr>
<td>
number_to_currency(123.56)
</td>

<td>
$123.56
</td>

<td>
R$ 123,56
</td>
</tr>

<tr>
<td>
number_to_human(100_555_123.15)
</td>

<td>
101 Million
</td>

<td>
100 milhões
</td>
</tr>

<tr>
<td>
I18n.l(Time.current, format: :long)
</td>

<td>
July 23, 2012 22:26
</td>

<td>
Segunda, 23 de Julho de 2012, 22:25 h
</td>
</tr>

<tr>
<td>
distance_of_time_in_words(1.hour + 20.minutes)
</td>

<td>
about 1 hour
</td>

<td>
aproximadamente 1 hora
</td>
</tr>
</table>

<p>
You can see that Rails already does a lot of heavy lifting for you, so don't put all that effort to waste.
</p>

## Devise

<p>
Most web apps that have user authentication use Devise. If you want to learn more check out Ryan Bates' awesome screencasts:
</p>

<ul>
<li>
<a href="http://railscasts.com/episodes/209-devise-revised">Episode 209: Devise (revised)</a>
</li>
<li>
<a href="http://railscasts.com/episodes/210-customizing-devise">Episode 210: Customizing Devise</a>
</li>
<li>
<a href="http://railscasts.com/episodes/235-devise-and-omniauth-revised">Episode 235: Devise and OmniAuth (revised)</a>
</li>
</ul>

<p>
The same as Rails, Devise also has extracted its internal strings and is fully internationalizable. Check out it's <a href="https://github.com/plataformatec/devise/wiki/I18n">Wiki about i18n</a> for more details. But you can start by downloading your translated files from <a href="http://tigrish.com/">Christopher Dell's</a> project, like this:
</p>

```
curl https://raw.github.com/tigrish/devise-i18n/master/locales/en-US.yml > config/locales/devise.en.yml
curl https://github.com/tigrish/devise-i18n/blob/master/locales/pt-BR.yml > config/locales/devise.pt-BR.yml
```

<p>
But if you want to have everything translated, you have to go the extra mile and actually use Devise's generator to clone its view templates within your Rails app by running <tt>rails g devise:views</tt>. This will copy the templates in <tt>app/views/devise</tt>. Keep the templates you want and translate all of them. As an example, take the resend confirmation template:
</p>

```
<h2>Resend confirmation instructions</h2>

<%= form_for(resource, :as => resource_name, :url => confirmation_path(resource_name), :html => { :method => :post }) do |f| %>
<%= devise_error_messages! %>

<div><%= f.label :email %><br />
<%= f.email_field :email %></div>

<div><%= f.submit "Resend confirmation instructions" %></div>
<% end %>

<%= render "devise/shared/links" %>
```

<p>
You have to extract them manually. In the case of Brazilian Portuguese I have already done the heavy lifting myself, you can download them from my <a href="https://github.com/akitaonrails/Rails-3-I18n-Demonstration/tree/master/app/views/devise">demonstration project</a> and replace the originals. Don't forget to also download the YAML file:
</p>

```
wget https://raw.github.com/akitaonrails/Rails-3-I18n-Demonstration/master/config/locales/devise.views.en.yml > config/locales/devise.views.en.yml
wget https://raw.github.com/akitaonrails/Rails-3-I18n-Demonstration/master/config/locales/devise.views.pt-BR.yml > config/locales/devise.views.pt-BR.yml
```

<p>
&#8212;
</p>

<p>
This should take care of the view templates, but you also have to take care of Rails' Form Helpers properly translating your model attributes. The Rails Guides quickly explain that, but in summary you have to have something similar to the following snippets in your <tt>config/locales</tt> file:
</p>

```
activemodel:
  errors:
    <<: *errors
activerecord:
  errors:
    <<: *errors
  models:
    user: "Usuário"
    article: "Artigo"
  attributes:
    user:
      email: "E-mail"
      password: "Senha"
      password_confirmation: "Confirmar Senha"
      current_password: "Senha Atual"
      remember_me: "Lembre-se de mim"
    article:
      title: "Título"
      body: "Conteúdo"
      body_html: "Conteúdo em HTML"
```

<p>
The <tt>User</tt> model is what Devise creates for you by default. As an added example, there is a <tt>Article</tt> model. The code should speak for itself. You translate the model class name in <tt>activerecord.models</tt> and the attributes in <tt>activerecord.attributes.[model]</tt>.
</p>

## The extra mile on database tables with Globalize 3

<p>
We took care of most of the structural translations already but you still have your user generated content. If you will have an application that users from around the world can use, maybe you may want to have content that reflects each user's language. The concept is quite simple: each content <tt>:has_many</tt> translations.
</p>

<p>
O conceito é simples: queremos um suporte que me permita utilizar os mesmos nomes de atributos mas que devolvam valores diferntes dependendo da localização escolhida atualmente. If we would add an Rspec spec to cover this behavior, it would look like this:
</p>

```
describe Article do
  before(:each) do
    I18n.locale = :en
    @article = Article.create title: "Hello World", body: "Test"
    I18n.locale = :"pt-BR"
    @article.update_attributes(title: "Ola Mundo", body: "Teste")
  end

  context "translations" do
    it "should read the correct translation" do
      @article = Article.last

      I18n.locale = :en
      @article.title.should == "Hello World"
      @article.body.should == "Test"

      I18n.locale = :"pt-BR"
      @article.title.should == "Ola Mundo"
      @article.body.should == "Teste"
    end
  end
end
```

<p>
I chose to use Sven Fuchs' <a href="https://github.com/svenfuchs/globalize3">Globalize 3</a> gem. Add that to your <tt>Gemfile</tt> as <tt>gem 'globalize3'</tt>, run the <tt>bundle</tt> command and you're good to go.
</p>

<p>
If you already have a <tt>Article</tt> model in your app, you should add a new migration like this:
</p>

```
class CreateArticles < ActiveRecord::Migration
  def up
    create_table :articles do |t|
      t.string :slug, null: false
      t.timestamps
    end
    add_index :articles, :slug, unique: true

    Article.create_translation_table! :title => :string, :body => :text
  end

  def down
    drop_table :articles
    Article.drop_translation_table!
  end
end
```

<p>
Do not use Rails 3's new <tt>change</tt> migration method. After that just migrate your database and let's go back to the Article model:
</p>

```
class Article < ActiveRecord::Base
  attr_accessible :slug, :title, :body, :locale, :translations_attributes

  translates :title, :body
  accepts_nested_attributes_for :translations

  class Translation
    attr_accessible :locale, :title, :body
  end
end
```

<p>
Don't mind the table created in the migration, you will use the <tt>Article</tt> model as usual. It will detect the current <tt>I18n.locale</tt> and save the content in the proper fields. Changing the current locale makes it query the different translations.
</p>

<h2>
Managing your Globalized content with ActiveAdmin
</h2>

<p>
Whenever I need an administration section, my first choice is to use the formidable <a href="http://activeadmin.info">Active Admin</a>, it has a clean neutral design that my clients enjoy, it's easy to use, and easily customizable. If you have a model associated with a CarrierWave uploader, for example, it will automatically show a file input attribute and that's because it's using Formtastic underneath to assemble the forms automatically. Read Active Admin's documentation to understand how to get started.
</p>

<p>
Now, to support a Globalize 3 extended model we will need some more tweaking. First of all let's add additional gems to the <tt>Gemfile</tt> to help:
</p>

```
...
group :assets do
  gem 'jquery-ui-rails'
  ...
end
...
gem 'jquery-rails'
gem 'activeadmin'
gem 'ActiveAdmin-Globalize3-inputs'
...
```

<p>
Now, we need to tell Active Admin to handle the <tt>Article</tt> model. We do that by creating a <tt>app/admin/article.rb</tt> file like this:
</p>

```
ActiveAdmin.register Article do
  index do
    column :id
    column :slug
    column :title
    default_actions
  end

  show do |article|
    attributes_table do
      row :slug
      I18n.available_locales.each do |locale|
        h3 I18n.t(locale, scope: ["translation"])
        div do
          h4 article.translations.where(locale: locale).first.title
        end
      end
    end
    active_admin_comments
  end
...
end
```

<p>
The <tt>index</tt> block is quite standard. Now the <tt>show</tt> block is interesting as we are accessing the <tt>translations</tt> association from the <tt>Article</tt> model directly. We iterate through each supported translation, as defined in <tt>config/application.rb</tt>.
</p>
<!-- Find this graphic
<p style="text-align: center">
<img src="http://akitaonrails.com/uploads/2012/7/14/Screen%20Shot%202012-07-14%20at%208.28.56%20PM_original.png" />
</p>
-->
<p>
I'm using <a href="https://github.com/mimimi/ActiveAdmin-Globalize3-inputs">ActiveAdmin-Globalize3-inputs</a>, which is turn depends on JQuery UI to adapt the administration form to use tabs for each locale.
</p>

<p>
Then we take advantage of ActiveRecord's ability to handle mass assigned nested attributes through <a href="http://api.rubyonrails.org/classes/ActiveRecord/NestedAttributes/ClassMethods.html#method-i-accepts_nested_attributes_for">accepts_nested_attributes_for</a>. To take advantage of this feature, we need to edit our Article model like this:
</p>

```
class Article < ActiveRecord::Base
  attr_accessible :body, :slug, :title, :locale, :translations_attributes
    ...
  translates :title, :body
  accepts_nested_attributes_for :translations
    ...
  class Translation
    attr_accessible :locale, :title, :body
  end

  def translations_attributes=(attributes)
    new_translations = attributes.values.reduce({}) do |new_values, translation|
      new_values.merge! translation.delete("locale") => translation
    end
    set_translations new_translations
  end
    ...
end
```

<p>
Now we need to make sure JQuery UI is available by modifying <tt>app/assets/stylesheets/active_admin.css</tt> like this:
</p>

```
// Active Admin CSS Styles
@import "active_admin/mixins";
@import "active_admin/base";
@import "jquery.ui.tabs";
```

<p>
And also modify the <tt>app/assets/javascripts/active_admin.js</tt> like this:
</p>

```
//= require active_admin/base
//= require jquery.ui.tabs
```

<p>
Finally, there is a last bit that we need to add to the end of the <tt>app/admin/articles.rb</tt> file:
</p>

```
ActiveAdmin.register Article do
  ...
form do |f|
    f.input :slug
    f.globalize_inputs :translations do |lf|
      lf.inputs do
        lf.input :title
        lf.input :body

        lf.input :locale, :as => :hidden
      end
    end

    f.buttons
  end
end
```

<p>
That will tap into Active Admin's internal Formtastic dependency and with the gem we added it will produce a screen like this:
</p>
<!-- Find this graphic
<p style="text-align: center">
<img src="http://akitaonrails.com/uploads/2012/7/14/Screen%20Shot%202012-07-14%20at%208.28.41%20PM_original.png" />
</p>
-->

<p>
By the way, sometimes people forget that in order for the Asset Pipeline to properly compile Active Admin's assets in production, you have to declare them in the <tt>config/application.rb</tt> file like this:
</p>

```
config.assets.precompile += %w(active_admin.js active_admin.css)
```

<p>
As a last tip, Active Admin interface itself is fully internationalizable. Read it's <a href="http://activeadmin.info/docs/1-general-configuration.html#internationalization_i18n">documentation</a> and you will find the YAML files that you can use to translate it to your native language.
</p>

<h3>
I18n Routes
</h3>

<p>
Last, but not least, for SEO purposes it is a good idea to have all or at least most of your URLs fully translated to your native language. For instance, we would want to have the following routes pointing all to the same actions:
</p>

```
/users/sign_in
/en/users/sign_in
/pt-BR/usuarios/login
```

<p>
There are several gems that try to achieve this, but the best I found so far is <a href="https://github.com/francesc/rails-translate-routes">rails-translate-routes</a>. As usual, just add it to our <tt>Gemfile</tt> like this: <tt>gem 'rails-translate-routes'</tt> and run the <tt>bundle</tt> command. Then go edit your <tt>config/routes.rb</tt> file to looks like this:
</p>

```
I18nDemo::Application.routes.draw do
  # rotas para active admin
  ActiveAdmin.routes(self)
  devise_for :admin_users, ActiveAdmin::Devise.config

  # rotas de autenticação do Devise
  devise_for :users

  # rotas pra artigos
  resources :articles

  # pagina principal
  get "welcome/index", as: "welcome"
  root to: 'welcome#index'
end
```

<p>
We can translate just what we need, as an example let's say that we want our Article routes and Devise's routes to be translated but we don't care for Active Admin's routes. So we can organize the routes file like this:
</p>

```
I18nDemo::Application.routes.draw do
  devise_for :users
  resources :articles
  get "welcome/index", as: "welcome"
  root to: 'welcome#index'
end

ActionDispatch::Routing::Translator.translate_from_file(
  'config/locales/routes.yml', {
    prefix_on_default_locale: true,
    keep_untranslated_routes: true })

I18nDemo::Application.routes.draw do
  ActiveAdmin.routes(self)
  devise_for :admin_users, ActiveAdmin::Devise.config
end
```

<p>
Where we put the <tt>translate_from_file</tt> defines the separation between what's translated and what is not. Now it's just a matter of creating a file named <tt>config/locales/routes.yml</tt> with the following translations:
</p>

```
en:
  routes:
pt-BR:
  routes:
    welcome: bemvindo
    new: novo
    edit: editar
    destroy: destruir
    password: senha
    sign_in: login
    users: usuarios
    cancel: cancelar
    article: artigo
    articles: artigos
```

<p>
The <tt>en.routes</tt> block is empty because &#8211; as I recommended in the beginning of the article &#8211; all our code is in English, so Rails will just pick the classes' names and the entire app is in English by default. In the <tt>[your language].routes</tt> just make the translations for the words you want. After all that, when we run Rails' <tt>rake routes</tt> task, we will have an output that looks like this:
</p>

```
...
article_pt_br GET    /pt-BR/artigos/:id(.:format)    articles#show {:locale=>"pt-BR"}
   article_en GET    /en/articles/:id(.:format)      articles#show {:locale=>"en"}
              GET    /articles/:id(.:format)         articles#show
              PUT    /pt-BR/artigos/:id(.:format)    articles#update {:locale=>"pt-BR"}
              PUT    /en/articles/:id(.:format)      articles#update {:locale=>"en"}
              PUT    /articles/:id(.:format)         articles#update
              DELETE /pt-BR/artigos/:id(.:format)    articles#destroy {:locale=>"pt-BR"}
              DELETE /en/articles/:id(.:format)      articles#destroy {:locale=>"en"}
              DELETE /articles/:id(.:format)         articles#destroy
welcome_pt_br GET    /pt-BR/bemvindo/index(.:format) welcome#index {:locale=>"pt-BR"}
   welcome_en GET    /en/welcome/index(.:format)     welcome#index {:locale=>"en"}
              GET    /welcome/index(.:format)        welcome#index
   root_pt_br        /pt-BR                          welcome#index {:locale=>"pt-BR"}
      root_en        /en                             welcome#index {:locale=>"en"}
```

--

<p>
Have you ever questioned yourself on the usage of named routes such as <tt>new_article_path</tt> in your view templates when you could just easily write &#8220;/articles/new&#8221;? Now you know why: the same named route will obey the internal <tt>I18n.locale</tt> and output the correct translated route. Pro tip: always try to adhere to the conventions instead of trying to be too smart, in this case, having being smart will cost you a lot of time to reconvert every hard-coded route as a named route.
</p>

<p>
We now need the application to be able to detect the <tt>locale</tt> options within the <tt>params</tt> hash, so let's edit <tt>/app/controllers/application_controller.rb</tt>:
</p>

```
class ApplicationController < ActionController::Base
  protect_from_forgery

  before_filter :set_locale
  before_filter :set_locale_from_url

  private

  def set_locale
    if lang = request.env['HTTP_ACCEPT_LANGUAGE']
      lang = lang[/^[a-z]{2}/]
      lang = :"pt-BR" if lang == "pt"
    end
    I18n.locale = params[:locale] || lang || I18n.default_locale
  end
end
```

<p>
Now both <tt>http://localhost:3000/en/articles</tt> and <tt>http://localhost:3000/pt-BR/artigos</tt> will respond correctly. To create links in our pages to change the language, we can create a little helper to put in the view layout:
</p>

```
module ApplicationHelper
  def language_links
    links = []
    I18n.available_locales.each do |locale|
      locale_key = "translation.#{locale}"
      if locale == I18n.locale
        links << link_to(I18n.t(locale_key), "#", class: "btn disabled")
      else
        links << link_to(I18n.t(locale_key), url_for(locale: locale.to_s), class: "btn")
      end
    end
    links.join("\n").html_safe
  end
    ...
end
```

<p>
The <tt>url_for</tt> helper will create links that return to the current page in the browser, but with the translated route and proper <tt>locale</tt> parameter. Just add the helper somewhere in your layout view template:
</p>

```
...
<div class="form-actions">
  <%= language_links %>
</div>
</body>
</html>

```
<!-- Find these graphics 
<p>
This is the result you will see:
</p>

<p style="text-align: center">
<img src="http://akitaonrails.com/uploads/2012/7/14/Screen%20Shot%202012-07-14%20at%209.26.29%20PM_original.png" />
</p>

<p style="text-align: center">
<img src="http://akitaonrails.com/uploads/2012/7/14/Screen%20Shot%202012-07-14%20at%209.26.01%20PM_original.png" />
</p>
-->
<p>
There are several different techniques to detect the language. You can make Rails understand subdomains, user's authenticated session, browser default language, cookies, but I prefer simple URI sections like the above examples show.
</p>

## Conclusion

<p>
As you can see, there are several things we can add to our applications to make them fully international. But even if you're not planning to add multiple languages, it doesn't hurt to follow a few simple rules:
</p>

<ul>
<li>
Make sure your database and source files are all using UTF8. It's very common to find applications running under Latin1 and having lot's of pain to reconvert everything to UTF8.
</li>
<li>
Having language specific text within your Ruby source code or view templates has to be considered a "code smell". Rails already makes all the heavy lifting, so just create a simple <tt>config/locales/en.yml</tt> to start.
</li>
<li>
Adding something as Globalize 3, on the other hand, may not be necessary unless you're sure you will need it. It's not difficult to add it later.
</li>
<li>
Do not use methods such as <tt>strftime</tt> or other methods that hard code the format of data conversions. Use <tt><a href="http://api.rubyonrails.org/classes/ActionView/Helpers/TranslationHelper.html#method-i-localize">I18n.localize</a></tt> for formatting.
</li>
<li>
And study more about Time zones and Rails support, you never know when you're gonna be bitten by time related issues.
</li>
</ul>

<p>
There is a lot more you can tweak in your Rails application but this covers what you will face most commonly in your next multi-cultural world-wide application.
</p>

<p class="alert">
<em>I hope you found this article useful. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
</p>

