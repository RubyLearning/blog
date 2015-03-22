---
draft: false
title: Why Use Single Sign-in Solutions in Rails?
date: 2010-11-16
author: Omar Mekky
categories:
- Beginners
- Ruby
- Ruby Masters
layout: post
permalink: /2010/11/16/why-use-single-sign-in-solutions-in-rails/
tags:
- Authentasaurus
- programming
- ruby programming
---
## Why Use Single Sign-in Solutions in Rails?

This guest post is by **Omar A. Mekky**, a software developer living in
Cairo, Egypt. His interests are every thing related to technology,
sports or science. He is a partner in Mash Ltd. in Egypt and enjoys
writing about Rails from time to time. Contact Omar at
[cousine.me](http://cousine.me/) or via twitter
[@cousine](http://twitter.com/cousine).

![Omar A.
Mekky](http://rubylearning.com/images/small-125.jpg "Omar A. Mekky")
Single sign-in solutions are becoming all popular and practical today.
In this article we will see how we can approach this problem by building
a simple restful provider and consumer using **Authentasaurus** on
Rails.

## Introduction

Single sign-in (SS) solutions lets your users sign in and use your
different applications using one username and one password, it also
helps you keep a centralized store of your users’ data.

This is good for a number of reasons; before the recent boom of online
hosted services an average user would keep a long list of usernames,
passwords and other important data for every service he/she was
registered for, for a period of time that was fine and was usually
accepted by the general population of the internet, but ever since the
boom of internet services startups it became tedious and one of the
reasons many users choose not to register for an extra service you are
providing given that they would have to enter their data all over again
even though they are already registered for another service you provide.

The second reason is for you and your staff; a centralized store for
your users’ data can help you keep track of your users and keep their
data consistent along your applications.

Those reasons are usually popular for service providers, but as the
number of your applications increase and your user base grow, you most
probably will cook up a number of other reasons why you need a SS
solution.

## What is Authentasaurus?

[Authentasaurus](https://github.com/cousine/Authentasuarus-2) is a
simple and easy to use restful authentication and authorization plugin
for Rails. It basically adds the functionality for authentication and
authorization to your application without the need to generate files and
code inside your application dir, but instead does that using Rails
engines and Ruby Gems.

In this article we will use authentasaurus for consuming the sign-in
service we will build but I urge you to check authentasaurus and take it
for a ride in your more basic applications so you can get a hold of its
features.

You can also use Authentasaurus in the provider to handle the
authentication process, but it’s not necessary to use it.

## The Approach

We want to give our users the ability to register and login once for all
our applications, to do that we will need to create a provider that will
hold all the user data and handle authentication of users, and have your
applications consume the API of that provider.

## Flow of the authentication process

We have two authentication scenarios:

1.  A user is logging in any of your applications and hasn’t logged in
    to any of your other applications.
2.  A user is logging in an application after logging into another
    application.

### First scenario flow

In step one and two we handle new users and then we handle returning
users:

1.  User registers for your application.
2.  The application communicates with the provider and creates a new
    user.
3.  User uses his/her credentials to login to your application.
4.  The application sends the user credentials to the provider and the
    provider authenticates the user.
5.  The provider then authenticates the user’s credentials and returns
    401 Unauthorized if the credentials are invalid.
6.  If the credentials are correct, the provider returns the user data
    back to the application along with a token to authenticate the user
    with other applications automatically.
7.  The application sets a cookie with the provider’s domain containing
    the token it received with the user data.

### Second scenario flow

In this scenario we are sure the user is a returning user not a new one.

1.  User goes to the login page (this can be another page but for the
    purpose of simplicity let us assume its the login page).
2.  The application redirects the user to the provider.
3.  The provider checks for the cookie set by the application where the
    user is already logged in at and authenticates the token inside it.
4.  The provider then redirects the user back to the application (the
    provider should have saved url of the application) and sends the
    username and token back to application if they are correct.
5.  The application authenticates the username and token again with the
    provider and follows the same flow as it did in the first scenario
    with the token instead of the password.

Note that the redirection between the application and provider is
invisible to the user. This is essential since the cookie is set using
the provider’s domain, so only the provider can read it.

Of course this is only a base for much more logic to be added, such as
API keys and HTTPS connections but for now this is going to be enough.

## Building the provider

We need our provider to handle 3 main tasks:

1.  Registering a new user and keep his/her data consistent.
2.  Authenticate a returning user using his/her username and password.
3.  Authenticate a returning user using a unique token. (for
    authenticating along a number of applications)

To achieve that let’s start by creating a new Rails application,
although I am using Rails 3 but most of the code is backward compatible
with Rails 2.3 so you can still follow if you are using an older
version, and I will try to point out the wrinkles between both versions
of Rails (3 and 2.3.\*) when they exist.

## Creating the application

To create the application fire up your terminal, console or command line
and type the following

### Rails 3

    $> rails new auth_provider

### Rails 2.3.\*

    $> rails auth_provider

I won’t be covering how to set up your database and prepare your
application for development here, but you can head to [Rails
Guides](http://guides.rubyonrails.org/) for tutorials and more
information about doing that.

After you setup your database, you should install an authentication
plugin, prepare your user model and make sure you can login locally
successfully.

You can use authentasaurus as an authentication plugin, you can read
more about this [here](https://github.com/cousine/Authentasuarus-2).

## Handling user registration and data consistency across your applications

To handle user registration all you need to do is expose your users
controller, you can do this simply by making sure you accept either xml
or json requests:

*Note that exposing your user controller is dangerous and you will need
to secure that by using an API key or any other mean to make sure only
your applications are accessing it*

This will also allow you to keep user data consistent through your
applications; all you have to do is create an ActiveResource object in
your applications and use it just as you would an ActiveRecord model to
create, update and delete users.

For more about ActiveRecord check [this
link](http://api.rubyonrails.org/classes/ActiveResource/Base.html).

Authenticating a returning user using his/her username and password
-------------------------------------------------------------------

Now that we have users in our database we need to authenticate them
remotely from other applications.

As we saw above in the process flow, we need to send the application a
token after successfully authenticating a user so other applications can
authenticate the user automatically. Lets create a model for the token:

### Rails 3

    $> rails g model token user_id:integer token_hash:string

### Rails 2.3.\*

    $> script/generate model token user_id:integer token_hash:string

This command will create the model and migration needed for the token,
next we need to set up the relation between the user and the token and
have the model create a random hash automatically for the token.

*In app/models/token.rb*

We can now start building a controller to authenticate users and
communicate with our applications.

### Rails 3

    $> rails g controller remote_sessions

### Rails 2.3.\*

    $> script/generate controller remote_sessions

*In app/controllers/remote\_sessions\_controller.rb*

Now your provider is all ready to accept authentication requests from
your applications.

## Authenticating a returning user using a unique token

The last thing we need to handle is authenticating a user using the
unique token that is set by the application once he/she is successfully
logged in, this will allow your applications to authenticate a user
automatically if he/she has already logged in any of your applications.

To do that we need to add two more action to the remote\_sessions
controller.

*In app/controllers/remote\_sessions\_controller.rb add this to your
class just below create*

*Now we need to add the authenticate and authorize methods in
app/models/token.rb*

*Finally we need to add the routes to config/routes.rb*

And that’s it, now our provider is ready to handle remote user
authentication from your applications.

Next we see how we can authenticate users from other applications using
Authentasaurus.

## Building the consumer

All we have left to do now is integrating your application with the
provider we just built, for this part we will use Authentasaurus for
remote authentication.

Authentasaurus comes with remote authentication with caching built it,
what this means is that you can choose to authenticate remotely but
cache the important data locally in your database to decrease the number
of requests between your application and the provider.

The module responsible for remote authentication and caching in
Authentasaurus is UserSync, by default when you install authentasaurus
you will have access to the UserSync object which is in fact just an
ActiveResource class extended with some methods to give it the ability
to cache and authenticate users from a remote location.

You can also build your own UserSync using the DSL provided by
Authentasaurus and Rails.

## What you need in your applications

To be able to consume the provider’s API you will need to change your
applications a bit, first you will need to install authentasaurus and
configure it to remotely authenticate from the provider.

To configure Authentasaurus, open config/authentasaurus.yml and use the
following values in the development section

Since we are in development, we will run both applications (provider and
consumer) on different ports so we can test them together; just choose
one to run on the default port and for the other run the server using
this command:

### Rails 3

    $> rails s -p 3001

### Rails 2.3.\*

    $> script/server -p 3001

I choose to run the provider on port 3000 and the consumer on port 3001
for simplicity.

## Overriding Authentasaurus for remote authentication

To be able to authenticate users with tokens we need to override the
default UserSync class, to do that create a new file (user\_sync.rb) in
your app/models directory and add the following to it:

Next we need to override the sessions controller to authenticate a
UserSync object instead of a User object (the default).

Create a new file (sessions\_controller.rb) in your app/controllers
folder and add the following to it:

Also we need to override the Session model to allow token
authentication.

Create a new file (session.rb) in your app/models folder and add the
following to it:

To cache users we need to tell authentasaurus which data to cache and
the default values of extra data.

Create a new file (user.rb) in your app/models and add the following to
it:

All that is left are the routes for the consumer, add the following
routes to your config/routes.rb

And that’s it, your consumer is ready to authenticate users remotely
using the provider api.

## Next Steps

You should add API key authentication and application handling, in the
example above we only have the Application model to store the callback
url of the applications we are integrating, your next step should be to
add more functionality so you can make sure that your users’ data are
only released to your authorized applications.

## Conclusion

As we saw SS solutions can be of much use when you have many
applications sharing the same users and data. It is an expected feature
for online service providers who give multiple services and
indispensable in your maintenance.

Even though we just scratched the very basic of building a SS solution
for your projects, I urge you to dig deeper into SS Solutions and
security of your application in general.

*I hope you found this article valuable. Feel free to ask questions and
give feedback in the comments section of this post. Thanks!*

***Do also read* these awesome Guest Posts:**

-   [How does your code
    smell?](http://rubylearning.com/blog/2010/11/08/how-does-your-code-smell/)
-   [Do YOU know
    Resque?](http://rubylearning.com/blog/2010/11/08/do-you-know-resque/)
-   [Do You Understand Ruby’s Objects, Messages and
    Blocks?](http://rubylearning.com/blog/2010/11/03/do-you-understand-rubys-objects-messages-and-blocks/)
-   [How Does One Use Design Patterns In
    Ruby?](http://rubylearning.com/blog/2010/11/02/how-does-one-use-design-patterns-in-ruby/)
-   [Do you know what’s new in Ruby
    1.9?](http://rubylearning.com/blog/2010/10/26/do-you-know-whats-new-in-ruby-1-9/)
-   [The value of a personal bug
    log](http://rubylearning.com/blog/2010/10/25/the-value-of-a-personal-bug-log/)
-   [Do You Enjoy Your Code
    Quality?](http://rubylearning.com/blog/2010/10/18/do-you-enjoy-your-code-quality/)

Also check out the [free and paid Ruby-related
eBooks](http://rubylearning.com/blog/ebooks/) from RubyLearning.
