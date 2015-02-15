---
title: 'Routing Basics: Ruby on Rails for Front-End Developers'
author: Miles Matthias
date: 2014-01-29
layout: post
permalink: /2014/01/29/routing-basics-ruby-on-rails-for-front-end-developers/
thesis_description:
  - Miles Matthias explains to us in simple terms what Rails routes are.
thesis_keywords:
  - Miles Matthias, Routing Basics, Rails Routes
topsy_short_url:
  - http://bit.ly/1e5IxiS
categories:
  - Beginners
  - Rails
tags:
  - Miles Matthias
  - Rails Routes
  - Routing Basics
---
<div>
  <h3>
    Routing Basics: Ruby on Rails for Front-End Developers
  </h3>
  
  <p class="update">
    This guest post is by&nbsp;<strong>Miles Matthias</strong>, who in between trips and sips, usually with planes and bourbon, enjoys talking to people about difficult challenges and tapping on his keyboard to help solve them. He moved to Boulder in January of 2012, after meeting his future wife and picking up degrees in Computer Science and Information Assurance in Omaha, Nebraska. Boulder was his ninth move after growing up in Virginia, Kansas, Illinois, and Indiana, and would be more than happy if Colorado became his permanent home. With experience in network security monitoring, vulnerability assessments, red hat teaming, bash scripting, and web and iOS development, he enjoys building simple and beautiful applications, contributing to the open source community, and writing about his life experiences.
  </p>
  
  <p class="block">
    <img class="alignright" alt="Miles Matthias" src="http://rubylearning.com/images/MilesMatthias.jpg" width="125" height="125" /> <span class="drop_cap">H</span>ere&#8217;s an excerpt from my book&#8217;s chapter on routing, and then I&#8217;ll give you some examples:
  </p>
  
  <h3>
    Routes config
  </h3>
  
  <p>
    Remember that bit about convention over configuration? Well rails definitely prefers configuration to convention in one instance &#8211; routes. In the file <code>config/routes.rb</code>, you&#8217;ll find direction given to the rails router on which controller method to call for a given request. Here&#8217;s a simple route declaration:
  </p>
  
  <pre>match 'articles', to: 'articles#index'
</pre>
  
  <p>
    If a user makes a request to <code>yoursite.com/articles</code>, the rails router will look for a controller called <code>ArticlesController</code> and if there&#8217;s a method called <code>index</code>, it will call it, passing along the information in the request. Then it&#8217;s up to the controller to respond.
  </p>
  
  <h3>
    Resources
  </h3>
  
  <p>
    You&#8217;ll also see what rails calls <code>resources</code> in the routes file, which promotes the convention over configuration pattern. Resources handle the 85% case where your application is representing standard RESTful CRUD operations on a &#8216;thing&#8217;, such as an article. The above example route could be replaced with:
  </p>
  
  <pre>resources :articles
</pre>
  
  <p>
    which would then mandate that the method names in the matching controller match the rails resourceful actions.
  </p>
  
  <h3>
    Examples
  </h3>
  
  <p>
    If we had the following in your <code>config/routes.rb</code> file:
  </p>
  
  <pre>resources :articles
</pre>
  
  <p>
    and our <code>/app/controllers/articles_controller.rb</code> file looked like this:
  </p>
  
  <pre>class ArticlesController &lt; ApplicationController
    def index
        @articles = Article.all
    end

    def show
        @article = Article.find(params[:id])
    end

    def edit
        @article = Article.find(params[:id])
    end
end
</pre>
  
  <p>
    Here&#8217;s the list of what HTTP Verbs and URL combinations match to what methods inside a controller:
  </p>
  
  <p>
    <img src="https://draftin.com:443/images/8207?token=RfEJPDQAtoETzsOHSeHWJfDgHHYF2mPCJCqj-mBULXEgHHS7BmmbHwfL1IVM1qCU2zCxrt7d3LIUboyzJGQ3ir0" alt="" width="670" /><br /><em>(Credit: <a href="http://guides.rubyonrails.org/routing.html#crud-verbs-and-actions">http://guides.rubyonrails.org/routing.html#crud-verbs-and-actions</a>)</em>
  </p>
  
  <p>
    Notice in the controller that we didn&#8217;t call <code>render</code> at all. That&#8217;s because Rails automatically attempts to render a view that has a filename of the same name of the method called in the controller. If it can&#8217;t find one, it will default to the <code>index.html</code> view for the controller, or the application <code>index.html</code>.
  </p>
  
  <p>
    For example, if someone wanted to get an article at <code>http://mywebsite.com/articles/1234</code>, Rails would call the <code>show</code> method in our controller with <code>1234</code> as the id param. That method (above) will find the article that matches that id and then rails will call render on a view in <code>/app/views/articles/show.html.erb</code>. Here&#8217;s an example of what that view might look like:
  </p>
  
  <pre>&lt;h1&gt;&lt;%= @article.title %&gt;&lt;/h1&gt;

&lt;h2&gt;by &lt;%= @article.author %&gt;&lt;/h2&gt;

&lt;p&gt;
&lt;%= @article.body %&gt;
&lt;/p&gt;
</pre>
  
  <p>
    If you&#8217;d like to learn more about how Ruby on Rails&#8217; front-end stack works or you&#8217;re a front-end developer needing to do some work in Ruby on Rails, check out my book, <a href="http://dojo4.com/blog/we-wrote-a-book">&#8220;Ruby on Rails Explained for Front-End Developers&#8221;</a>.
  </p>
  
  <p class="alert">
    <em>Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Miles+Matthias" rel="tag">Miles Matthias</a>, <a href="http://technorati.com/tag/Routing+Basics" rel="tag"> Routing Basics</a>, <a href="http://technorati.com/tag/Rails+Routes" rel="tag"> Rails Routes</a>
