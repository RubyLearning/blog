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
  - Ruby
  - The Ruby Programming Language
  - Volt framework
---
<div>
  <p>
    <b>By Amaury Andres Peniche Gonzalez &#8211; Software Engineer at <a href="http://www.toptal.com/">Toptal</a></b>
  </p>
  
  <p class="block">
    <img class="alignleft" title="Amaury Andres Peniche Gonzalez" src="http://rubylearning.com/images/amaury.jpg" alt="Amaury Andres Peniche Gonzalez" width="125" height="125" />Amaury is a systems and production engineer with experience in front and back-end development, computer graphics, and networking. Amaury currently works as a freelance <a href="http://www.toptal.com/ruby">Ruby engineer at Toptal</a>, where he was involved in numerous projects, mainly related to Ruby on Rails.
  </p>
  
  <h2 id="ruby-and-the volt-framework">
    Ruby and the Volt framework
  </h2>
  
  <p>
    <b>Volt</b> is a Ruby web framework designed for data rich applications. Both the server and client sides are written in Ruby (which is then compiled to JS using OPAL), so this allows the developer to write very dynamic applications without having to write a single line of Javascript code. If you&#8217;re a Ruby fan like me, you&#8217;ll love this framework.
  </p>
  
  <p>
    In an attempt to make web applications a lot more dynamic, front-end Javascript frameworks like Angular.js, Backbone.js and Ember.js have gained a lot of popularity. However, these frameworks often require a back-end application to be useful, so they are used in conjunction with web frameworks like Ruby on Rails and Django.
  </p>
  
  <p>
    On the other hand, Volt is capable of managing the back-end and a dynamic front-end. Since both functionalities are tightly integrated into its core (in fact, Volt is more like an MVVM architecture, leveraging the advantages of data bindings), it enables the developer to build these applications quickly.
  </p>
  
  <p>
    A very cool feature that comes out of the box is Volt&#8217;s real-time feature. If you ever made real-time applications, you know the process can be challenging – you probably implemented AJAX-polling, web sockets, Server-Sent Events (SSE) or even used external services, adding complexity to the application and even incurring additional costs. Unlike other frameworks, Volt keeps a connection with the server alive (via web sockets), so instead of making Ajax requests for each action, it pushes changes instantly to all clients. No configuration is needed for this to work.
  </p>
  
  <h3 id="using-volt-to-create-a-chat-application">
    Using Volt To Create A Chat Application
  </h3>
  
  <p>
    In this guide I am going to take you through the process of creating a real-time application using Volt, and what better way than a chat application to demonstrate its capabilities, since chat remains the number one use case of real time applications.
  </p>
  
  <p>
    First of all, let&#8217;s install Volt and MongoDB. The latter process will not be covered in detail:
  </p>
  
  <pre>gem install volt

brew install mongodb
mkdir -p /data/db (create dbpath)
chown `id -u` /data/db (change the owner to have the proper dbpath permissions)
</pre>
  
  <p>
    Now we&#8217;re ready to create our first app, lets call it &#8216;chat&#8217;. We can do that easily in a couple of lines:
  </p>
  
  <pre>volt new chat
cd chat
</pre>
  
  <p>
    The document structure has some similarities to Rails. The main difference Rails users will notice is that we have an extra folder inside app that contains the rest of the folders like assets, controllers, models and views, this extra folder is a &#8216;Component&#8217;.
  </p>
  
  <p>
    A Component is an isolated section of the app. All pages inside a Component are rendered without reloading the page since all files for that component are loaded with the initial http request, so if we visit a page of a different component, a new http request will be made and the page will be &#8216;reloaded&#8217;. For this example let&#8217;s use the default component called &#8216;main&#8217;.
  </p>
  
  <p>
    Let&#8217;s start the server by executing &#8216;volt server&#8217; command in console, and see how it looks in the browser by navigating to <a href="http://localhost:3000">localhost:3000</a>:
  </p>
  
  <pre>volt server
</pre>
  
  <p>
    Also don’t forget to start MongoDB in console:
  </p>
  
  <pre>mongod
</pre>
  
  <p>
    We can notice that Volt comes with a number of default pages, including &#8216;Home&#8217; and &#8216;About&#8217;. These can be customized right away.
  </p>
  
  <p>
    The other thing worth mentioning is the login button at the top right side of the page. Volt has a &#8220;user&#8221; functionality integrated to the framework via the &#8216;volt-user-templates&#8217; gem, which provides a way to register and authenticate users, right out of the box.
  </p>
  
  <h3 id="getting-started">
    Getting Started
  </h3>
  
  <p>
    Now, let&#8217;s start working on our app. First of all we don&#8217;t need the &#8216;About&#8217; page so we can go ahead and delete the following: The app/main/views/main/about.html file, the about action in app/main/controllers/main_controller.rb, remove the &#8216;/about&#8217; route in the app/main/config/routes.rb and the nav link in app/main/views/main/main.html.
  </p>
  
  <pre>&lt;ul class="nav nav-pills pull-right"&gt;
  &lt;:nav href="/" text="Home" /&gt;
  &lt;:user-templates:menu /&gt;
&lt;/ul&gt;
</pre>
  
  <p>
    Now let&#8217;s get down to business and start by listing all registered users:
  </p>
  
  <pre>&lt;:Body&gt;
  &lt;h1&gt;Home&lt;/h1&gt;
  &lt;div class="row"&gt;
	&lt;div class="col-md-4"&gt;
  	{{ _users.each do |user| }}
    	&lt;div class="contact"&gt;
      	{{user._name}}
    	&lt;/div&gt;
  	{{ end }}
	&lt;/div&gt;
  &lt;/div&gt;
</pre>
  
  <p>
    Now all the registered users are being listed in the homepage. Note that the code written inside {{ }} is Ruby code that gets executed. This way we can iterate over user collection and print each one out.
  </p>
  
  <p>
    As you may have noticed, &#8216;<em>users&#8217; is the name of the collection where all users are stored; something to have in mind is that attributes are accessed with an underscore &#8216;</em>&#8216; prepended to the attribute name. For this to work, we first need to add a line of code at the top of the main_controller.rb file:
  </p>
  
  <pre>model :store
</pre>
  
  <p>
    Volt comes with multiple collection models accessible from the controller, and each of them stores the information in a different place. The store collection model stores the data in the data store, and here we are specifying the controller to use that one (right now the only data store supported is MongoDB). Let&#8217;s create a couple of users to see what it looks like:
  </p>
  
  <p>
    Right now there is nothing exciting about this page, we&#8217;re just listing the registered users. Now I would like to be able to select a user to send a message to, remove the name of the currently logged in user from the list (since he shouldn&#8217;t be able to send messages to himself), show the list only to authenticated users and show a &#8216;landing&#8217; page to non-authenticated users:
  </p>
  
  <pre>&lt;:Body&gt;
  &lt;h1&gt;Home&lt;/h1&gt;
  {{ if Volt.user }}
	&lt;div class="row"&gt;
  	&lt;div class="col-md-4"&gt;
    	{{ _users.each do |user| }}
      	{{ if user._id != Volt.user._id }}
        	&lt;div class="contact {{ if params._user_id == user._id }} active {{ end }}" e-click="select_conversation(user)"&gt;
          	{{user._name}}
        	&lt;/div&gt;
      	{{ end }}
    	{{ end }}
  	&lt;/div&gt;
	&lt;/div&gt;
  {{ else }}
	&lt;p&gt;This is a sample application built with Volt to demonstrate its real-time capabilities. Please log in to access it.&lt;/p&gt;
  {{ end }}

Volt.user return the current (logged in) user or nil.
</pre>
  
  <p>
    The e-click attribute lets us select a method from the controller that will be called when that element is clicked.
  </p>
  
  <h3 id="attributes-and-css">
    Attributes and CSS
  </h3>
  
  <p>
    In fact, all &#8216;e-&#8216; attributes are event binders in Volt, so for example we can add e-submit to a form to choose the action that will be called on the controller. We are going to add the &#8216;selected&#8217; user&#8217;s ID to the parameters so we can know which one has been selected and add a class called &#8216;active&#8217; which we can later style.
  </p>
  
  <p>
    Now let&#8217;s create the select_conversation method in the controller:
  </p>
  
  <pre>def select_conversation(user)
  params._user_id = user._id
end
</pre>
  
  <p>
    And that&#8217;s it – if you check out the page again, you can see that the URL changes every time you click on a user&#8217;s name. Also, the class &#8216;active&#8217; is being added to that element, so let&#8217;s add some CSS to make it visible (I&#8217;ll go ahead and add the CSS for items we will add later on):
  </p>
  
  <p>
    Now let&#8217;s create a form on the right side to send messages to each user:
  </p>
  
  <p>
    First, we&#8217;re checking if there is a user selected before displaying the form, then we display all messages from the current conversation (the conversation with the selected user) from a method in the controller we&#8217;re going to define in a bit and at the bottom we&#8217;re displaying a form for sending new messages.
  </p>
  
  <p>
    Notice that the value of the input is an attribute we&#8217;re creating on the page collection model since we don&#8217;t want it to be stored in the data store. Now let&#8217;s define the &#8216;current_conversation&#8217; and &#8216;send_message&#8217; methods in the controller:
  </p>
  
  <pre>def send_message
  unless page._new_message.strip.empty?
	_messages &lt;&lt; { sender_id: Volt.user._id, receiver_id: params._user_id, text: page._new_message }
	page._new_message = ''
  end
end
</pre>
  
  <pre>def current_conversation
  _messages.find({ "$or" =&gt; [{ sender_id: Volt.user._id, receiver_id: params._user_id }, { sender_id: params._user_id, receiver_id: Volt.user._id }] })
end
</pre>
  
  <p>
    In the send_message method we add a new message to the collection if the message is not blank (we&#8217;re checking inline so we don&#8217;t have to mess with validations at the moment), then we set the page._new_message to &#8221; so we empty the input field.
  </p>
  
  <p>
    We might want to add that line to the end of the select_conversation method as well. The current conversation method just queries the _messages collection for messages between the selected user and the current user.
  </p>
  
  <h3 id="wrap-up-with-real-time-notifications">
    Wrap Up With Real-Time Notifications
  </h3>
  
  <p>
    To finish, I would like to have some kind of notification system, so users could see when other users are messaging them.
  </p>
  
  <p>
    Let&#8217;s add a new collection called _notifications and create a new one after each message is sent:
  </p>
  
  <p>
    Also, we need to delete notifications from after a user selects the conversation and sees the new messages, so I added that part to the select_conversation method.
  </p>
  
  <p>
    Let&#8217;s add a notification counter right next to the user name:
  </p>
  
  <pre>&lt;div class="contact {{ if params._user_id == user._id }} active {{ end }}" e-click="select_conversation(user)"&gt;
  {{user._name}}
  {{ if unread_notifications_from(user).count &gt; 0 }}
	&lt;span class="badge"&gt;
  	{{ unread_notifications_from(user).count }}
	&lt;/span&gt;
  {{ end }}
&lt;/div&gt;
</pre>
  
  <p>
    Now the app is ready, you can open a couple of browsers and start testing the real-time capabilities of Volt.
  </p>
  
  <h3 id="volt-is-definitely-worth-a-try">
    Volt Is Definitely Worth A Try
  </h3>
  
  <p>
    Even though Volt is not as mature and robust as most of the popular frameworks that have been around for years (at the moment of Volt is still in beta), it is worth considering and studying.
  </p>
  
  <p>
    In case you are interested, take it out for a spin and keep an eye on further developments, as Volt looks like a very promising framework even at this early stage of development.
  </p>
  
  <p>
    There are a lot of cool new features in the pipeline and I&#8217;m pretty sure Volt will become more relevant over the next couple of years, as more people start experimenting with it. Due to a number of innovative features, many developers could fall in love with Volt and use it for their next project.
  </p>
  
  <p>
    Finally, here&#8217;s the complete code that we have developed:
  </p>
  
  <p>
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/The+Ruby+Programming+Language" rel="tag">The Ruby Programming Language</a>, <a href="http://technorati.com/tag/Volt+framework" rel="tag">Volt framework</a>
