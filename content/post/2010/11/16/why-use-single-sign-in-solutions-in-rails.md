---
author: Omar Mekky
categories:
- Beginners
- Ruby
- Ruby Masters
date: 2010-11-16
layout: post
permalink: /2010/11/16/why-use-single-sign-in-solutions-in-rails/
tags:
- Authentasaurus
- programming
- ruby programming
thesis_description:
- "Omar A. Mekky shows us how we can build single sign in solutions in Rails by previewing
  Authentasaurus for \nauthentication.\n"
thesis_keywords:
- Authentasaurus,Programming,Ruby programming
title: Why Use Single Sign-in Solutions in Rails?
topsy_short_url:
- http://bit.ly/bsXzf7
---

<div>
  <h3>
    Why Use Single Sign-in Solutions in Rails?
  </h3>
  
  <p class="update">
    This guest post is by <strong>Omar A. Mekky</strong>, a software developer living in Cairo, Egypt. His interests are every thing related to technology, sports or science. He is a partner in Mash Ltd. in Egypt and enjoys writing about Rails from time to time. Contact Omar at <a href="http://cousine.me/">cousine.me</a> or via twitter <a href="http://twitter.com/cousine">@cousine</a>.
  </p>
  
  <p class="block">
    <img class="alignright" src="http://rubylearning.com/images/small-125.jpg" alt="Omar A. Mekky" title="Omar A. Mekky" /> <span class="drop_cap">S</span>ingle sign-in solutions are becoming all popular and practical today. In this article we will see how we can approach this problem by building a simple restful provider and consumer using <strong>Authentasaurus</strong> on Rails.
  </p>
  
  <h3>
    Introduction
  </h3>
  
  <p>
    Single sign-in (SS) solutions lets your users sign in and use your different applications using one username and one password, it also helps you keep a centralized store of your users&#8217; data.
  </p>
  
  <p>
    This is good for a number of reasons; before the recent boom of online hosted services an average user would keep a long list of usernames, passwords and other important data for every service he/she was registered for, for a period of time that was fine and was usually accepted by the general population of the internet, but ever since the boom of internet services startups it became tedious and one of the reasons many users choose not to register for an extra service you are providing given that they would have to enter their data all over again even though they are already registered for another service you provide.
  </p>
  
  <p>
    The second reason is for you and your staff; a centralized store for your users&#8217; data can help you keep track of your users and keep their data consistent along your applications.
  </p>
  
  <p>
    Those reasons are usually popular for service providers, but as the number of your applications increase and your user base grow, you most probably will cook up a number of other reasons why you need a SS solution.
  </p>
  
  <h3>
    What is Authentasaurus?
  </h3>
  
  <p>
    <a href="https://github.com/cousine/Authentasuarus-2">Authentasaurus</a> is a simple and easy to use restful authentication and authorization plugin for Rails. It basically adds the functionality for authentication and authorization to your application without the need to generate files and code inside your application dir, but instead does that using Rails engines and Ruby Gems.
  </p>
  
  <p>
    In this article we will use authentasaurus for consuming the sign-in service we will build but I urge you to check authentasaurus and take it for a ride in your more basic applications so you can get a hold of its features.
  </p>
  
  <p>
    You can also use Authentasaurus in the provider to handle the authentication process, but it&#8217;s not necessary to use it.
  </p>
  
  <h3>
    The Approach
  </h3>
  
  <p>
    We want to give our users the ability to register and login once for all our applications, to do that we will need to create a provider that will hold all the user data and handle authentication of users, and have your applications consume the API of that provider.
  </p>
  
  <h3>
    Flow of the authentication process
  </h3>
  
  <p>
    We have two authentication scenarios:
  </p>
  
  <ol>
    <li>
      A user is logging in any of your applications and hasn&#8217;t logged in to any of your other applications.
    </li>
    <li>
      A user is logging in an application after logging into another application.
    </li>
  </ol>
  
  <h4>
    First scenario flow
  </h4>
  
  <p>
    In step one and two we handle new users and then we handle returning users:
  </p>
  
  <ol>
    <li>
      User registers for your application.
    </li>
    <li>
      The application communicates with the provider and creates a new user.
    </li>
    <li>
      User uses his/her credentials to login to your application.
    </li>
    <li>
      The application sends the user credentials to the provider and the provider authenticates the user.
    </li>
    <li>
      The provider then authenticates the user&#8217;s credentials and returns 401 Unauthorized if the credentials are invalid.
    </li>
    <li>
      If the credentials are correct, the provider returns the user data back to the application along with a token to authenticate the user with other applications automatically.
    </li>
    <li>
      The application sets a cookie with the provider&#8217;s domain containing the token it received with the user data.
    </li>
  </ol>
  
  <h4>
    Second scenario flow
  </h4>
  
  <p>
    In this scenario we are sure the user is a returning user not a new one.
  </p>
  
  <ol>
    <li>
      User goes to the login page (this can be another page but for the purpose of simplicity let us assume its the login page).
    </li>
    <li>
      The application redirects the user to the provider.
    </li>
    <li>
      The provider checks for the cookie set by the application where the user is already logged in at and authenticates the token inside it.
    </li>
    <li>
      The provider then redirects the user back to the application (the provider should have saved url of the application) and sends the username and token back to application if they are correct.
    </li>
    <li>
      The application authenticates the username and token again with the provider and follows the same flow as it did in the first scenario with the token instead of the password.
    </li>
  </ol>
  
  <p>
    Note that the redirection between the application and provider is invisible to the user. This is essential since the cookie is set using the provider&#8217;s domain, so only the provider can read it.
  </p>
  
  <p>
    Of course this is only a base for much more logic to be added, such as API keys and HTTPS connections but for now this is going to be enough.
  </p>
  
  <h3>
    Building the provider
  </h3>
  
  <p>
    We need our provider to handle 3 main tasks:
  </p>
  
  <ol>
    <li>
      Registering a new user and keep his/her data consistent.
    </li>
    <li>
      Authenticate a returning user using his/her username and password.
    </li>
    <li>
      Authenticate a returning user using a unique token. (for authenticating along a number of applications)
    </li>
  </ol>
  
  <p>
    To achieve that let&#8217;s start by creating a new Rails application, although I am using Rails 3 but most of the code is backward compatible with Rails 2.3 so you can still follow if you are using an older version, and I will try to point out the wrinkles between both versions of Rails (3 and 2.3.*) when they exist.
  </p>
  
  <h3>
    Creating the application
  </h3>
  
  <p>
    To create the application fire up your terminal, console or command line and type the following
  </p>
  
  <h4>
    Rails 3
  </h4>
  
  <pre>$&gt; rails new auth_provider
</pre>
  
  <h4>
    Rails 2.3.*
  </h4>
  
  <pre>$&gt; rails auth_provider
</pre>
  
  <p>
    I won&#8217;t be covering how to set up your database and prepare your application for development here, but you can head to <a href="http://guides.rubyonrails.org/">Rails Guides</a> for tutorials and more information about doing that.
  </p>
  
  <p>
    After you setup your database, you should install an authentication plugin, prepare your user model and make sure you can login locally successfully.
  </p>
  
  <p>
    You can use authentasaurus as an authentication plugin, you can read more about this <a href="https://github.com/cousine/Authentasuarus-2">here</a>.
  </p>
  
  <h3>
    Handling user registration and data consistency across your applications
  </h3>
  
  <p>
    To handle user registration all you need to do is expose your users controller, you can do this simply by making sure you accept either xml or json requests:
  </p>
  
  <p>
  </p>
  
  <p>
    <em>Note that exposing your user controller is dangerous and you will need to secure that by using an API key or any other mean to make sure only your applications are accessing it</em>
  </p>
  
  <p>
    This will also allow you to keep user data consistent through your applications; all you have to do is create an ActiveResource object in your applications and use it just as you would an ActiveRecord model to create, update and delete users.
  </p>
  
  <p>
    For more about ActiveRecord check <a href="http://api.rubyonrails.org/classes/ActiveResource/Base.html">this link</a>.
  </p>
  
  <h2>
    Authenticating a returning user using his/her username and password
  </h2>
  
  <p>
    Now that we have users in our database we need to authenticate them remotely from other applications.
  </p>
  
  <p>
    As we saw above in the process flow, we need to send the application a token after successfully authenticating a user so other applications can authenticate the user automatically. Lets create a model for the token:
  </p>
  
  <h4>
    Rails 3
  </h4>
  
  <pre>$&gt; rails g model token user_id:integer token_hash:string
</pre>
  
  <h4>
    Rails 2.3.*
  </h4>
  
  <pre>$&gt; script/generate model token user_id:integer token_hash:string
</pre>
  
  <p>
    This command will create the model and migration needed for the token, next we need to set up the relation between the user and the token and have the model create a random hash automatically for the token.
  </p>
  
  <p>
    <em>In app/models/token.rb</em>
  </p>
  
  <p>
  </p>
  
  <p>
    We can now start building a controller to authenticate users and communicate with our applications.
  </p>
  
  <h4>
    Rails 3
  </h4>
  
  <pre>$&gt; rails g controller remote_sessions
</pre>
  
  <h4>
    Rails 2.3.*
  </h4>
  
  <pre>$&gt; script/generate controller remote_sessions
</pre>
  
  <p>
    <em>In app/controllers/remote_sessions_controller.rb</em>
  </p>
  
  <p>
  </p>
  
  <p>
    Now your provider is all ready to accept authentication requests from your applications.
  </p>
  
  <h3>
    Authenticating a returning user using a unique token
  </h3>
  
  <p>
    The last thing we need to handle is authenticating a user using the unique token that is set by the application once he/she is successfully logged in, this will allow your applications to authenticate a user automatically if he/she has already logged in any of your applications.
  </p>
  
  <p>
    To do that we need to add two more action to the remote_sessions controller.
  </p>
  
  <p>
    <em>In app/controllers/remote_sessions_controller.rb add this to your class just below create</em>
  </p>
  
  <p>
  </p>
  
  <p>
    <em>Now we need to add the authenticate and authorize methods in app/models/token.rb</em>
  </p>
  
  <p>
  </p>
  
  <p>
    <em>Finally we need to add the routes to config/routes.rb</em>
  </p>
  
  <p>
  </p>
  
  <p>
    And that&#8217;s it, now our provider is ready to handle remote user authentication from your applications.
  </p>
  
  <p>
    Next we see how we can authenticate users from other applications using Authentasaurus.
  </p>
  
  <h3>
    Building the consumer
  </h3>
  
  <p>
    All we have left to do now is integrating your application with the provider we just built, for this part we will use Authentasaurus for remote authentication.
  </p>
  
  <p>
    Authentasaurus comes with remote authentication with caching built it, what this means is that you can choose to authenticate remotely but cache the important data locally in your database to decrease the number of requests between your application and the provider.
  </p>
  
  <p>
    The module responsible for remote authentication and caching in Authentasaurus is UserSync, by default when you install authentasaurus you will have access to the UserSync object which is in fact just an ActiveResource class extended with some methods to give it the ability to cache and authenticate users from a remote location.
  </p>
  
  <p>
    You can also build your own UserSync using the DSL provided by Authentasaurus and Rails.
  </p>
  
  <h3>
    What you need in your applications
  </h3>
  
  <p>
    To be able to consume the provider&#8217;s API you will need to change your applications a bit, first you will need to install authentasaurus and configure it to remotely authenticate from the provider.
  </p>
  
  <p>
    To configure Authentasaurus, open config/authentasaurus.yml and use the following values in the development section
  </p>
  
  <p>
  </p>
  
  <p>
    Since we are in development, we will run both applications (provider and consumer) on different ports so we can test them together; just choose one to run on the default port and for the other run the server using this command:
  </p>
  
  <h4>
    Rails 3
  </h4>
  
  <pre>$&gt; rails s -p 3001
</pre>
  
  <h4>
    Rails 2.3.*
  </h4>
  
  <pre>$&gt; script/server -p 3001
</pre>
  
  <p>
    I choose to run the provider on port 3000 and the consumer on port 3001 for simplicity.
  </p>
  
  <h3>
    Overriding Authentasaurus for remote authentication
  </h3>
  
  <p>
    To be able to authenticate users with tokens we need to override the default UserSync class, to do that create a new file (user_sync.rb) in your app/models directory and add the following to it:
  </p>
  
  <p>
  </p>
  
  <p>
    Next we need to override the sessions controller to authenticate a UserSync object instead of a User object (the default).
  </p>
  
  <p>
    Create a new file (sessions_controller.rb) in your app/controllers folder and add the following to it:
  </p>
  
  <p>
  </p>
  
  <p>
    Also we need to override the Session model to allow token authentication.
  </p>
  
  <p>
    Create a new file (session.rb) in your app/models folder and add the following to it:
  </p>
  
  <p>
  </p>
  
  <p>
    To cache users we need to tell authentasaurus which data to cache and the default values of extra data.
  </p>
  
  <p>
    Create a new file (user.rb) in your app/models and add the following to it:
  </p>
  
  <p>
  </p>
  
  <p>
    All that is left are the routes for the consumer, add the following routes to your config/routes.rb
  </p>
  
  <p>
  </p>
  
  <p>
    And that&#8217;s it, your consumer is ready to authenticate users remotely using the provider api.
  </p>
  
  <h3>
    Next Steps
  </h3>
  
  <p>
    You should add API key authentication and application handling, in the example above we only have the Application model to store the callback url of the applications we are integrating, your next step should be to add more functionality so you can make sure that your users&#8217; data are only released to your authorized applications.
  </p>
  
  <h3>
    Conclusion
  </h3>
  
  <p>
    As we saw SS solutions can be of much use when you have many applications sharing the same users and data. It is an expected feature for online service providers who give multiple services and indispensable in your maintenance.
  </p>
  
  <p>
    Even though we just scratched the very basic of building a SS solution for your projects, I urge you to dig deeper into SS Solutions and security of your application in general.
  </p>
  
  <p>
    <em>I hope you found this article valuable. Feel free to ask questions and give feedback in the comments section of this post. Thanks!</em>
  </p>
  
  <p>
    <strong><em>Do also read</em> these awesome Guest Posts:</strong>
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/blog/2010/11/08/how-does-your-code-smell/">How does your code smell?</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/11/08/do-you-know-resque/">Do YOU know Resque?</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/11/03/do-you-understand-rubys-objects-messages-and-blocks/">Do You Understand Ruby’s Objects, Messages and Blocks?</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/11/02/how-does-one-use-design-patterns-in-ruby/">How Does One Use Design Patterns In Ruby?</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/26/do-you-know-whats-new-in-ruby-1-9/">Do you know what’s new in Ruby 1.9?</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/25/the-value-of-a-personal-bug-log/">The value of a personal bug log</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/18/do-you-enjoy-your-code-quality/">Do You Enjoy Your Code Quality?</a>
    </li>
  </ul>
  
  <p class="note">
    Also check out the <a href="http://rubylearning.com/blog/ebooks/">free and paid Ruby-related eBooks</a> from RubyLearning.
  </p>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Authentasaurus" rel="tag">Authentasaurus</a>, <a href="http://technorati.com/tag/Programming" rel="tag">Programming</a>, <a href="http://technorati.com/tag/Ruby+programming" rel="tag">Ruby programming</a>
