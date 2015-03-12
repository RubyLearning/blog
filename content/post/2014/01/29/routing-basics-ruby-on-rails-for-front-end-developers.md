---
author: Miles Matthias
categories:
- Beginners
- Rails
date: 2014-01-29
layout: post
permalink: /2014/01/29/routing-basics-ruby-on-rails-for-front-end-developers/
tags:
- Miles Matthias
- Rails Routes
- Routing Basics
title: 'Routing Basics: Ruby on Rails for Front-End Developers'
---

## Routing Basics: Ruby on Rails for Front-End Developers

This guest post is by&nbsp;<strong>Miles Matthias</strong>, who in between
trips and sips, usually with planes and bourbon, enjoys talking to people
about difficult challenges and tapping on his keyboard to help solve them.
He moved to Boulder in January of 2012, after meeting his future wife and
picking up degrees in Computer Science and Information Assurance in Omaha,
Nebraska. Boulder was his ninth move after growing up in Virginia, Kansas,
Illinois, and Indiana, and would be more than happy if Colorado became his
permanent home. With experience in network security monitoring,
vulnerability assessments, red hat teaming, bash scripting, and web and iOS
development, he enjoys building simple and beautiful applications,
contributing to the open source community, and writing about his life
experiences.

<img alt="Miles Matthias"
src="http://rubylearning.com/images/MilesMatthias.jpg" width="125" height="125"
/>

Here's an excerpt from my book's chapter on routing, and then I'll give you
some examples:

## Routes config

Remember that bit about convention over configuration? Well rails definitely
prefers configuration to convention in one instance -- routes. In the file
`config/routes.rb`, you'll find direction given to the rails router on which
controller method to call for a given request. Here's a simple route
declaration:

```rails
match 'articles', to: 'articles#index'
```

If a user makes a request to `yoursite.com/articles`, the rails router will
look for a controller called `ArticlesController` and if there's a method
called `index`, it will call it, passing along the information in the request.
Then it's up to the controller to respond.

## Resources

You'll also see what rails calls `resources` in the routes file, which promotes
the convention over configuration pattern. Resources handle the 85% case where
your application is representing standard RESTful CRUD operations on a 'thing',
such as an article. The above example route could be replaced with:

```rails
resources :articles
```

which would then mandate that the method names in the matching controller match
the rails resourceful actions.

## Examples

If we had the following in your `config/routes.rb` file:

```rails
resources :articles
```

and our `/app/controllers/articles_controller.rb` file looked like this:

```rails
class ArticlesController < ApplicationController
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
```

Here's the list of what HTTP Verbs and URL combinations match to what methods
inside a controller:

<img src="https://draftin.com:443/images/8207?token=RfEJPDQAtoETzsOHSeHWJfDgHHYF2mPCJCqj-mBULXEgHHS7BmmbHwfL1IVM1qCU2zCxrt7d3LIUboyzJGQ3ir0" alt="" width="670" /><br /><em>(Credit: <a href="http://guides.rubyonrails.org/routing.html#crud-verbs-and-actions">http://guides.rubyonrails.org/routing.html#crud-verbs-and-actions</a>)</em>

Notice in the controller that we didn't call `render` at all. That's because
Rails automatically attempts to render a view that has a filename of the same
name of the method called in the controller. If it can't find one, it will
default to the `index.html` view for the controller, or the application
`index.html`.

For example, if someone wanted to get an article at
`http://mywebsite.com/articles/1234`, Rails would call the `show` method in our
controller with `1234` as the id param. That method (above) will find the
article that matches that id and then rails will call render on a view in
`/app/views/articles/show.html.erb`. Here's an example of what that view might
look like:

```rhtml
<h1>
    <%= @article.title %>
</h1>
<h2>
    by <%= @article.author %>
</h2>
<%= @article.body %>
```

If you'd like to learn more about how Ruby on Rails' front-end stack works or
you're a front-end developer needing to do some work in Ruby on Rails, check
out my book, <a href="http://dojo4.com/blog/we-wrote-a-book">"Ruby on Rails
Explained for Front-End Developers"</a>.

<em>Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>

