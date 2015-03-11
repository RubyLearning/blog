---
title: Meet Volt, A Promising Ruby Framework For Dynamic Applications
author: Amaury
date: 2015-02-11
layout: post
permalink: /2015/02/11/meet-volt-a-promising-ruby-framework-for-dynamic-applications/
thesis_description:
  - Meet Volt, A Promising Ruby Framework For Dynamic Applications.
thesis_keywords:
  - Ruby,The Ruby Programming Language,Volt framework
topsy_short_url:
  - http://bit.ly/1IQhbgt
categories:
  - Ruby
tags:
  - ruby
  - volt
  - framework
---
**By Amaury Andres Peniche Gonzalez – Software Engineer at
[Toptal](http://www.toptal.com/)**

<img src="http://rubylearning.com/images/amaury.jpg" width=144 height=144>
</img>

Amaury is a systems and production engineer with experience in front and
back-end development, computer graphics, and networking. Amaury
currently works as a freelance [Ruby engineer at
Toptal](http://www.toptal.com/ruby), where he was involved in numerous
projects, mainly related to Ruby on Rails.
<!--more-->

Ruby and the Volt framework
---------------------------

**Volt** is a Ruby web framework designed for data rich applications.
Both the server and client sides are written in Ruby (which is then
compiled to JS using OPAL), so this allows the developer to write very
dynamic applications without having to write a single line of Javascript
code. If you’re a Ruby fan like me, you’ll love this framework.

In an attempt to make web applications a lot more dynamic, front-end
Javascript frameworks like Angular.js, Backbone.js and Ember.js have
gained a lot of popularity. However, these frameworks often require a
back-end application to be useful, so they are used in conjunction with
web frameworks like Ruby on Rails and Django.

On the other hand, Volt is capable of managing the back-end and a
dynamic front-end. Since both functionalities are tightly integrated
into its core (in fact, Volt is more like an MVVM architecture,
leveraging the advantages of data bindings), it enables the developer to
build these applications quickly.

A very cool feature that comes out of the box is Volt’s real-time
feature. If you ever made real-time applications, you know the process
can be challenging – you probably implemented AJAX-polling, web sockets,
Server-Sent Events (SSE) or even used external services, adding
complexity to the application and even incurring additional costs.
Unlike other frameworks, Volt keeps a connection with the server alive
(via web sockets), so instead of making Ajax requests for each action,
it pushes changes instantly to all clients. No configuration is needed
for this to work.

### Using Volt To Create A Chat Application

In this guide I am going to take you through the process of creating a
real-time application using Volt, and what better way than a chat
application to demonstrate its capabilities, since chat remains the
number one use case of real time applications.

First of all, let’s install Volt and MongoDB. The latter process will
not be covered in detail:

    gem install volt

    brew install mongodb
    mkdir -p /data/db (create dbpath)
    chown `id -u` /data/db (change the owner to have the proper dbpath permissions)

Now we’re ready to create our first app, lets call it ‘chat’. We can do
that easily in a couple of lines:

    volt new chat
    cd chat

The document structure has some similarities to Rails. The main
difference Rails users will notice is that we have an extra folder
inside app that contains the rest of the folders like assets,
controllers, models and views, this extra folder is a ‘Component’.

A Component is an isolated section of the app. All pages inside a
Component are rendered without reloading the page since all files for
that component are loaded with the initial http request, so if we visit
a page of a different component, a new http request will be made and the
page will be ‘reloaded’. For this example let’s use the default
component called ‘main’.

Let’s start the server by executing ‘volt server’ command in console,
and see how it looks in the browser by navigating to
[localhost:3000](http://localhost:3000):

    volt server

Also don’t forget to start MongoDB in console:

    mongod

We can notice that Volt comes with a number of default pages, including
‘Home’ and ‘About’. These can be customized right away.

The other thing worth mentioning is the login button at the top right
side of the page. Volt has a “user” functionality integrated to the
framework via the ‘volt-user-templates’ gem, which provides a way to
register and authenticate users, right out of the box.

### Getting Started

Now, let’s start working on our app. First of all we don’t need the
‘About’ page so we can go ahead and delete the following: The
app/main/views/main/about.html file, the about action in
app/main/controllers/main\_controller.rb, remove the ‘/about’ route in
the app/main/config/routes.rb and the nav link in
app/main/views/main/main.html.

    <ul class="nav nav-pills pull-right">
      <:nav href="/" text="Home" />
      <:user-templates:menu />
    </ul>

Now let’s get down to business and start by listing all registered
users:

    <:Body>
      <h1>Home</h1>
      <div class="row">
        <div class="col-md-4">
        {{ _users.each do |user| }}
            <div class="contact">
            {{user._name}}
            </div>
        {{ end }}
        </div>
      </div>

Now all the registered users are being listed in the homepage. Note that
the code written inside {{ }} is Ruby code that gets executed. This way
we can iterate over user collection and print each one out.

As you may have noticed, ‘*users’ is the name of the collection where
all users are stored; something to have in mind is that attributes are
accessed with an underscore ‘*‘ prepended to the attribute name. For
this to work, we first need to add a line of code at the top of the
main\_controller.rb file:

    model :store

Volt comes with multiple collection models accessible from the
controller, and each of them stores the information in a different
place. The store collection model stores the data in the data store, and
here we are specifying the controller to use that one (right now the
only data store supported is MongoDB). Let’s create a couple of users to
see what it looks like:

Right now there is nothing exciting about this page, we’re just listing
the registered users. Now I would like to be able to select a user to
send a message to, remove the name of the currently logged in user from
the list (since he shouldn’t be able to send messages to himself), show
the list only to authenticated users and show a ‘landing’ page to
non-authenticated users:

    <:Body>
      <h1>Home</h1>
      {{ if Volt.user }}
        <div class="row">
        <div class="col-md-4">
            {{ _users.each do |user| }}
            {{ if user._id != Volt.user._id }}
                <div class="contact {{ if params._user_id == user._id }} active {{ end }}" e-click="select_conversation(user)">
                {{user._name}}
                </div>
            {{ end }}
            {{ end }}
        </div>
        </div>
      {{ else }}
        <p>This is a sample application built with Volt to demonstrate its real-time capabilities. Please log in to access it.</p>
      {{ end }}

    Volt.user return the current (logged in) user or nil.

The e-click attribute lets us select a method from the controller that
will be called when that element is clicked.

### Attributes and CSS

In fact, all ‘e-‘ attributes are event binders in Volt, so for example
we can add e-submit to a form to choose the action that will be called
on the controller. We are going to add the ‘selected’ user’s ID to the
parameters so we can know which one has been selected and add a class
called ‘active’ which we can later style.

Now let’s create the select\_conversation method in the controller:

    def select_conversation(user)
      params._user_id = user._id
    end

And that’s it – if you check out the page again, you can see that the
URL changes every time you click on a user’s name. Also, the class
‘active’ is being added to that element, so let’s add some CSS to make
it visible (I’ll go ahead and add the CSS for items we will add later
on):

Now let’s create a form on the right side to send messages to each user:

First, we’re checking if there is a user selected before displaying the
form, then we display all messages from the current conversation (the
conversation with the selected user) from a method in the controller
we’re going to define in a bit and at the bottom we’re displaying a form
for sending new messages.

Notice that the value of the input is an attribute we’re creating on the
page collection model since we don’t want it to be stored in the data
store. Now let’s define the ‘current\_conversation’ and ‘send\_message’
methods in the controller:

    def send_message
      unless page._new_message.strip.empty?
        _messages << { sender_id: Volt.user._id, receiver_id: params._user_id, text: page._new_message }
        page._new_message = ''
      end
    end

    def current_conversation
      _messages.find({ "$or" => [{ sender_id: Volt.user._id, receiver_id: params._user_id }, { sender_id: params._user_id, receiver_id: Volt.user._id }] })
    end

In the send\_message method we add a new message to the collection if
the message is not blank (we’re checking inline so we don’t have to mess
with validations at the moment), then we set the page.\_new\_message to
” so we empty the input field.

We might want to add that line to the end of the select\_conversation
method as well. The current conversation method just queries the
\_messages collection for messages between the selected user and the
current user.

### Wrap Up With Real-Time Notifications

To finish, I would like to have some kind of notification system, so
users could see when other users are messaging them.

Let’s add a new collection called \_notifications and create a new one
after each message is sent:

Also, we need to delete notifications from after a user selects the
conversation and sees the new messages, so I added that part to the
select\_conversation method.

Let’s add a notification counter right next to the user name:

    <div class="contact {{ if params._user_id == user._id }} active {{ end }}" e-click="select_conversation(user)">
      {{user._name}}
      {{ if unread_notifications_from(user).count > 0 }}
        <span class="badge">
        {{ unread_notifications_from(user).count }}
        </span>
      {{ end }}
    </div>

Now the app is ready, you can open a couple of browsers and start
testing the real-time capabilities of Volt.

### Volt Is Definitely Worth A Try

Even though Volt is not as mature and robust as most of the popular
frameworks that have been around for years (at the moment of Volt is
still in beta), it is worth considering and studying.

In case you are interested, take it out for a spin and keep an eye on
further developments, as Volt looks like a very promising framework even
at this early stage of development.

There are a lot of cool new features in the pipeline and I’m pretty sure
Volt will become more relevant over the next couple of years, as more
people start experimenting with it. Due to a number of innovative
features, many developers could fall in love with Volt and use it for
their next project.

Finally, here’s the complete code that we have developed:

Technorati Tags: [Ruby](http://technorati.com/tag/Ruby), [The Ruby
Programming
Language](http://technorati.com/tag/The+Ruby+Programming+Language),
[Volt framework](http://technorati.com/tag/Volt+framework)
