---
draft: false
title: An Introduction to Outside-in Development
date: 2010-10-05
author: Harold Gimenez
authorlink: http://twitter.com/hgimenez
categories:
- Beginners
- Popular
- Ruby
- Ruby Masters
layout: post
permalink: /2010/10/05/outside-in-development/
tags:
- "Harold Giménez"
- Outside-in Development
- programming
- Ruby
- Ruby Beginners
- Ruby for Noobs
---
This guest post is contributed by **Harold Giménez**, who is a web
developer with the crew at [thoughtbot](http://thoughtbot.com/), where
he spends his days working with Rails and writing open source software.
He's also involved with<!--more--> thoughtbot's
[workshops](http://workshops.thoughtbot.com/), which is a great way to
dig deeper into subjects like test-driven Rails development. Follow
Harold on twitter at [@hgimenez](http://twitter.com/hgimenez).

![Harold Giménez](http://rubylearning.com/images/harold-125x125.jpg)

## An Introduction to Outside-in Development

Outside-in Development is a software development methodology that
focuses on providing value to the product's users and stakeholders.
Cucumber is a BDD tool that supports Outside-in development by running
plain text features or user stories as acceptance tests. Well written
user stories state clearly their business value, and help developers
bring themselves out of the software developer role and into the user
role, where we can get a more realistic overview of the application's
interface and general flow. This leads to more cohesive and simpler
software, because you write the simplest amount of code that satisifies
a user story, and you often review the application as a user. Outside-in
along with the test-driven process helps you write just the minimum
amount of code that provides value to stakeholders, and not a line more.

While still great and recommended, reading much theory and praise about
outside-in is not as effective as actually trying it and seeing it in
action. We will write the beginnings of **twiddr**, a small twitter
clone in Rails 3 using the outside-in process. Our testing arsenal will
consist of the following excellent Ruby libraries.

-   Cucumber: A plain text story runner.
-   RSpec: A BDD framework for Ruby.
-   Factory Girl: A fixture replacement framework.
-   Shoulda: A set of RSpec matchers, among other things.

We will explain in more detail how these frameworks work together as we
start developing the application. To get started quickly, we will use
[suspenders](http://github.com/thoughtbot/suspenders) to create an
application with all of our tools installed and configured. Since this
is a Rails 3 application, we will use the beta version of suspenders.
Install it by running `gem install suspenders --pre`. Now that
suspenders is installed, we can bootstrap twiddr with
`suspenders create twiddr`.

At this point, we have a twiddr application including authentication
with [clearance](http://github.com/thoughtbot/clearance), a simple Rails
authentication solution with email and password. Clearance also includes
cucumber features that you can view in the `features` directory. Let's
run them right now by running `rake db:migrate` to create the users
table, `script/rails generate clearance_views` to generate clearance
views with [formtastic](http://github.com/justinfrench/formtastic), and
`rake` to run all specs and features. You should see a very satisfying
series of green dots appear on your terminal, along with "0 Failures".

Let's create our first feature. The anatomy of a feature is the
following:

    In order to [business value]
    As a [role]
    I want to [some action]

Notice how a feature includes who, what and most importantly: *why*. Our
first feature could look something like the following:

    Feature: Users have a twiddr login name
      In order to mention other twiddr users by login name
      As a twiddr user
      I can pick a login name

There will be many scenarios accompanying this feature. Scenarios will
follow the four stages of testing: setup, exercise, verify and teardown.
Let's write a few scenarios that come to mind. A simple scenario looks
like this:

    Given [context]
    When I do [action]
    Then I should see [outcome]

The `Given` step is where you set up the context of your scenario. Every
scenario starts with a blank slate, so it is important to create a state
in your application for example by creating data in the database, or by
navigating to a specific page. The `When` step is where you exercise the
application in order to accomplish what needs testing. In the case of a
web app like twiddr, this is usually where you fill in forms, press
buttons, click links, or otherwise interact with the system in some way.
Finally, the `Then` step is where you verify the result, and it's where
we check that the correct pages are rendered, that we see a success or
error message, or anything that could help us verify that the prior
action was successful. As we move along with creating our own features,
this will become much clearer.

The final stage of testing, `teardown`, is taken care of by cucumber
automatically. It refers to clearing out the state of the system so that
there are no nasty leftovers from one test to the next. In most cases,
this means deleting all data from the database.

Back to developing our app, we already have authentication set up in the
application via clearance, but there is value in also having a twiddr
login, so let's go ahead and add that functionality to user model. To
get started, we can work off of the clearance sign up scenarios that you
can find in `features/sign_up.feature`. Let's modify the scenario titled
"User signs up with valid data" and add a step where the user fills in
their twiddr name. The step definition ends up looking like this:

    Scenario: User signs up with valid data
      When I go to the sign up page
      And I fill in "Email" with "email@person.com"
      And I fill in "Twiddr name" with "user"
      And I fill in "Password" with "password"
      And I fill in "Confirm password" with "password"
      And I press "Sign up"
      Then I should see "instructions for confirming"
      And a confirmation message should be sent to "email@person.com"

The above is executable code. Cucumber uses regular expressions to match
the plain text features and executes the resulting step definitions.
Finally, note that each of these stages of a cucumber feature can have
many steps: by adding more steps starting with `And`, we can create more
complex contexts (Given/And), actions (When/And) or outcomes (Then/And).

At this point it is worth viewing the step definitions provided by
Capybara if you haven't already. They can be found in
`features/step_definitions/web_steps.rb`, and have definitions for most
web interactions like `I go to...`, `I fill in...`, or `I should see...`

Let's run the new scenario, and watch it fail:

\$ bundle exec cucumber features/sign\_up.feature

The output will look something like this:

    ........F-----.................

    (::) failed steps (::)

    cannot fill in, no text field, text area or password field with id, name, or label 'Twiddr name' found (Capybara::ElementNotFound)
    ./features/step_definitions/web_steps.rb:41
    ./features/step_definitions/web_steps.rb:14:in `with_scope'
    ./features/step_definitions/web_steps.rb:40:in `/^(?:|I )fill in "([^"]*)" with "([^"]*)"(?: within "([^"]*)")?$/'
    features/sign_up.feature:17:in `And I fill in "Twiddr name" with "user"'

    Failing Scenarios:
    cucumber features/sign_up.feature:14 # Scenario: User signs up with valid data

    5 scenarios (1 failed, 4 passed)
    31 steps (1 failed, 5 skipped, 25 passed)
    0m0.852s

The error message tells us that the text field labeled "Twiddr name" was
not found on the form, which is exactly what we were expecting. Cucumber
is also telling us what to do next: Add a Twiddr name input field to the
user signup form. To do that, open up `app/views/users/_inputs.html.erb`
and add a line to include the :twiddr\_name input. It should look like
this:

    <%= form.inputs do %>
      <%= form.input :email %>
      <%= form.input :twiddr_name %>
      <%= form.input :password %>
      <%= form.input :password_confirmation, :label => "Confirm password" %>
    <% end %>

Part of the outside-in process is to only write the simplest amount of
code that could make the test pass, and not a line more. At this point
you may be tempted to go on with implementing the twiddr\_name
functionality, but it's important to contain your fingers from typing
any further, and instead rerun the feature to see what the next step
should be.

Rerunning the feature now shows that not only does our scenario not
pass, but we've also broken a different scenario. Don't panic! All
scenarios that display this form are now broken because the `User` model
doesn't have a `twiddr_name` attribute. To add it, we create a database
migration. On your terminal, type:

    $ ./script/rails generate migration add_twiddr_name_to_users twiddr_name:string
    $ rake db:migrate && rake db:test:prepare

This will add a column called `twiddr_name` of type `string` to the
`users` table. Run the scenario once again, and you'll note that we've
reached a clean build: all tests pass. We should add some more behavior
around our new `twiddr_name`. For example, we probably want to require
that new users enter a twiddr\_name when signing up to the site. We can
add a scenario that tests for that:

    Scenario: User tries to sign up without a twiddr name
      When I go to the sign up page
      And I fill in "Email" with "email@person.com"
      And I fill in "Password" with "password"
      And I fill in "Confirm password" with "password"
      And I press "Sign up"
      Then the "Twiddr name" field should have the "can't be blank" error

Run the scenario, and you will note that the last step is not defined.
Cucumber will even print out a starting point for the step definition.
Copy the provided template and paste it in a new file called
`features/step_definitions/form_error_steps.rb`. The definition of this
step will use CSS selectors to verify that the field contains the
expected error message, based on the markup generated by formtastic:

    Then /^the "([^"]*)" field should have the "([^"]*)" error$/ do |field_label, error_message|
      within('form li') do
        page.should have_css("label:contains('#{field_label}') ~ p.inline-errors", :text => error_message)
      end
    end

Dropping that into the `form_error_steps.rb` will allow us to move
forward with our scenario: It fails because we don't have any
validations on `twiddr_name`. We want to always make sure that
`twiddr_name` is present. Let's drop to the model spec level to specify
this new behavior. Create a file called `spec/models/user_spec.rb` and
let's specify this requirement:

    require 'spec_helper'

    describe User, 'valid' do
      it { should validate_presence_of :twiddr_name }
    end

The `validate_presence_of` method is a
[shoulda](http://github.com/thoughtbot/shoulda) matcher. There are a ton
of useful matchers. For other active record matcher examples, please
refer to [the
documentation](http://rdoc.info/github/thoughtbot/shoulda/master/Shoulda/ActiveRecord/Matchers).

First, watch it fail by running
`bundle exec rspec spec/models/user_spec.rb`. To make it pass, we open
up `app/models/user.rb` and add the one required validation line:
`validates_presence_of :twiddr_name`. Running the spec again will reveal
that we're once again green. Now we can return back up to the cucumber
level by rerunning our feature:
`bundle exec cucumber features/sign_up.feature`. This time we notice
that the feature we are developing is passing, but we broke a few other
features because of invalid users being created, which brings us to
another aspect of testing: `factories`.

During testing it is very often required to generate setup data to
create context for the test. One great way to manage that is by using a
factory library, where we define a few factory templates, and then we
ask the factory to create instances of those objects to either get a
hold of them in a variable or store them in the database. It then
becomes trivial to get a hold of valid instances of models in your
application, which is very useful for setting up a test's context. In
this application, we are using
[factory\_girl](http://github.com/thoughtbot/factory_girl).

What's breaking in the above feature is that the user factory is not
including `:twiddr_name` when it generates objects. Therefore it is
creating invalid objects, and ActiveRecord is rightfully raising an
error. The fix in this case is to add the new required attribute to the
user factory, found in `spec/factories/clearance.rb`. In that file, the
user factory definition could look like so (we simply use the email to
create a twiddr\_name):

    Factory.define :user do |user|
      user.email                 { Factory.next :email }
      user.password              { "password" }
      user.password_confirmation { "password" }
      user.twiddr_name           { |u| u.email.split("@").first }
    end

At this point, we once again have a green build. We can move on to
another feature (save the following in
`features/user_views_profiles.feature`):

    Feature: user profiles
      In order to see if I'm interested in following other users
      As a twiddr user
      I can see other user's profiles

      Scenario: View a user's profile
        Given the following email confirmed user exists:
          | twiddr_name | email                |
          | hgimenez    | hgimenez@example.com |
        Given I have signed in with "me@example.com/test"
        When I go to the profile page for "hgimenez"
        Then I should see "hgimenez" within "div.twiddr_name"
        And I should see "hgimenez@example.com" within "div.email"
        And I should see "Follow"

Notice the first setup step in the above scenario: "Given the following
email confirmed user exists:" followed by a table. Furthermore, if you
run this scenario you will notice that that step passes even though we
haven't written a step definition for it. What's going on here is that
Factory Girl conveniently creates step definitions for all of our
factories, making it very easy to create the data required to provide
some context for your tests. In the above example, "email confirmed
user" is the name of a factory defined in `spec/factories/clearance.rb`,
and the cucumber
[table](http://github.com/aslakhellesoy/cucumber/wiki/multiline-step-arguments)
that follows maps attributes to values for the records you're creating.
It's simpler and therefore recommended to provide values only for the
attributes that you're interested in for this scenario. So in this case,
we really don't care what the user's password is, but we care about the
twiddr name and email because we're verifying them a few lines down.

When you run this scenario, you will notice that cucumber did not know
how to map `the profile page for "hgimenez"` to an actual URL in your
application. To tell cucumber how to do that, we add an entry in
`features/support/path.rb` like so:

    when /the profile page for "([^\"]+)"/
      user = User.find_by_twiddr_name!($1)
      user_path(user)

We are using a regular expression to capture the twiddr name provided in
the step definition, and using the captured string to find that user in
the database. On tests it is a good idea to use the "dangerous" versions
of active record finders (ending with `!`), so that if the record is not
found, Active Record will raise a clear error message, making debugging
much easier.

Adding that entry in `features/support/paths.rb` gets us further in that
step definition. That step still fails though, but this time for a
different reason:
`The action 'show' could not be found for Clearance::UsersController (AbstractController::ActionNotFound)`.
In this case, our users controller does not specify a show action. Since
this is a clearance controller, we can extend it by simply creating a
new controller and inheriting from `Clearance::UsersController`. This
will allow us to both create new actions or extend the default ones
provided by clearance. Following cucumber's failure message, our next
step is to create show action on the users controller:

    class UsersController < Clearance::UsersController
      def show
      end
    end

But even with this in place, cucumber continues to complaint about the
show action being unavailable. It seems like there could be a routing
problem, so let's again move down to the controller spec level and
specify our new route:

    require 'spec_helper'

    describe UsersController, 'routes' do
      it { should route(:get, 'users/1').to(:action => 'show', :id => 1) }
    end

The spec above is a shoulda [controller
matcher](http://rdoc.info/github/thoughtbot/shoulda/master/Shoulda/ActionController/Matchers).
We have created a new class for the UsersController, and need the user
routes to map to this new class (without the Clearance namespace).
Additionally, clearance has a few nested resources under users that we
will still need. If we look at the clearance routes file, we can pull
out the relevant pieces and include it in our own app's
`config/routes.rb`, where we can get rid of the clearance namespace:

    resources :users, :controller => 'users', :only => [:show, :create] do
      resource :password,
        :controller => 'clearance/passwords',
        :only       => [:create, :edit, :update]

      resource :confirmation,
        :controller => 'clearance/confirmations',
        :only       => [:new, :create]
    end

Running the controller spec again will show that we've wired up the
routes correctly, and running the entire cucumber suite will show that
we have not broken any of the nested routes that clearance originally
provided. This is just another advantage of having the kind of strong
test coverage that is achieved by BDD, and definitely brings confidence
in the quality of the application you're building: We've made a somewhat
major refactor, and but we're confident that things are wired up
correctly *because our test suite passes*.

Moving along, we can rerun the feature file, at which point cucumber
complaints that there's no users/show view. Let's create it!

    <h2><%= @user.twiddr_name -%></h2>

    <div id="profile">
      <div class="twiddr_name"><%= @user.twiddr_name -%></div>
      <div class="email"><%= @user.email -%></div>
      <div class="follow">Follow</div>
    </div>

Running the feature now reveals that the `@user` instance variable is
not set. We can assign this instance variable in the users controller
and try again:

    def show
      @user = User.find(params[:id])
    end

Run rake, and find that all specs and scenarios are passing. We can move
on to following users. In `features/user_follows_another_user.feature`:

    Feature: Follow twiddr users
      So that I can see what they have to say
      As a twiddr user
      I can follow other twiddr users

      Scenario: Follow another twiddr user
        Given the following email confirmed user exists:
          | twiddr_name | email           |
          | bob         | bob@example.com |
        And I have signed in with "hgimenez@example.com/test"
        When I go to the profile page for "bob"
        And I press "Follow bob"
        Then I should be on the home page
        And I should see "You are now following bob!"
        And I should see "bob" within "div.following"

The first failure message is "no button with value or id or text 'Follow
bob' found (Capybara::ElementNotFound)", because the user profile pages
do not have an actual follow button. At this point, we should have some
idea of how we'll implement user following. A clean RESTful way to go
about it is to create a user\_follows resource, and to POST to it when a
user wants to follow someone else. Let's add a button that posts to that
resource, in `app/views/users/show.html.erb`:

    ><div id="profile">
      <div class="twiddr_name"><%= @user.twiddr_name -%></div>
      <div class="email"><%= @user.email -%></div>
      <div class="follow"><%= button_to("Follow #{@user.twiddr_name}", user_follows_path(@user)) -%> </div>
    </div>

Rerunning the feature now shows
`` "undefined method `user<em>follows</em>path' for #<#<Class:0x103d108e0>:0x103d0a4e0> (ActionView::Template::Error)" ``
because there is no `user_follows` resource or route yet. This is a good
point to step down into RSpec land while we build this resource. We
create `spec/controller/follows_controller_spec.rb` and specify a route:

    require 'spec_helper'

    describe FollowsController, 'routes' do
      it { should route(:post, '/users/1/follows').to(:action => 'create', :user_id => 1) }
    end

And we can now enter BDD cycle. Run the spec with
`bundle exec rspec spec/controllers/follows_controller_spec.rb` and we
get the error `"uninitialized constant FollowsController (NameError)"`
because we have not created the follows controller. Create it in
`app/controllers/follows_controller.rb` with the following content:

    class FollowsController < ApplicationController
    end

Rerunning the spec, we now see `No route matches "/users/1/follows"`.
Great, let's add that route nested within the users resource, which now
looks like this:

    resources :users, :controller => 'users', :only => [:show, :create] do
      resource :password,
        :controller => 'clearance/passwords',
        :only       => [:create, :edit, :update]

      resource :confirmation,
        :controller => 'clearance/confirmations',
        :only       => [:new, :create]

      resource :follows, :only => [:create] # add this
    end

Run the spec again to get feedback from RSpec: The test passes so the
route is working as we expected. Back on the cucumber level we rerun the
feature which now finds the button and route, but errors on
`"The action 'create' could not be found for FollowsController (AbstractController::ActionNotFound)"`.
Time to bring the follows controller to life with the create action.

Let's specify the controller behavior in RSpec. We want only signed in
users to be able to hit this action, so let's spec that out:

    describe FollowsController, 'POST to create without authenticating' do
      before do
        post :create, :user_id => 1
      end
      it { should redirect_to(sign_in_path) }
    end

This test makes sure that we redirect to the sign in path if no user is
authenticated. To make it pass, we simply add
`before_filter :authenticate` to our controller. Now on to the more
details about the create action: We want to verify that the signed in
user ends up following the provided user when the action runs.

In spec's setup we create two users, we simulate authenticating by
assigning controller's the current\_user, and we exercise the controller
by invoking a POST to create. We then verify two things: that the user
is indeed following the provided user, and that we redirect to the root
path. Note that we still don't have any logic or even models to hold the
user following relationships, but we can start to think about how that
interface will look like. One of these tests already shows some of that:
`current_user.follows?`.

    describe FollowsController, 'authenticated POST to create' do
      let(:follower)       { Factory(:email_confirmed_user) }
      let(:user_to_follow) { Factory(:email_confirmed_user) }
      before do
        controller.current_user = follower #sign in
        post :create, :user_id => user_to_follow.id
      end

      it { should redirect_to(root_path) }
      it 'makes the signed in user follow the provided user' do
        controller.current_user.follows?(user_to_follow).should be_true
      end
    end

We run this test, watch it fail, and come up with a first pass at an
implementation:

    def create
      user = User.find(params[:user_id])
      current_user.follow(user)
      redirect_to :root_path
    end

This gets us a little further, because the redirect spec now passes.
It's time to specify our models, and how the `follow` method on the user
class will behave. We will also need a `follows?` method that determines
whether a user follows another one. Let's spec this out
`spec/models/user_spec.rb`.

    describe User, '#follows?' do
      subject { Factory(:email_confirmed_user) }
      let(:followed_user) { Factory(:email_confirmed_user) }
      let(:another_user) { Factory(:email_confirmed_user) }

      before do
        subject.follow(followed_user)
      end

      it 'returns true when it follows the user' do
        subject.follows?(followed_user).should be_true
      end

      it 'returns false when it does not follow the user' do
        subject.follows?(another_user).should be_false
      end
    end

    describe User, 'following another user' do
      subject { Factory(:email_confirmed_user) }
      let(:user_to_follow) { Factory(:email_confirmed_user) }

      before do
        subject.follow(user_to_follow)
      end

      it 'makes the user follow the provided user' do
        subject.follows?(user_to_follow).should be_true
      end

      it 'does not make the provided user follow the user' do
        user_to_follow.follows?(subject).should be_false
      end
    end

We can model user followings with a simple has\_many association on the
user model. Let's specify that on the valid user context using another
shoulda matcher:

    describe User, 'valid' do
      it { should validate_presence_of   :twiddr_name }
      it { should have_many :followings } # add this
    end

Our error message is now: "Expected User to have a has\_many association
called followings (no association called followings)". Let's add the
followings table with a database migration. Run
`./script/rails generate migration create_followings` and add the
following definition:

    class CreateFollowings < ActiveRecord::Migration
      def self.up
        create_table :followings do |t|
          t.references :user
          t.integer    :followed_user_id
          t.timestamps
        end
        add_index :followings, :user_id
      end

      def self.down
        drop_table :followings
      end
    end

Run `rake db:migrate && rake db:test:prepare` to create the table. We
can now create a Following spec and model, where we probably want to
validate presence of user\_id:

    require 'spec_helper'

    describe Following, 'valid' do
      it { should validate_presence_of(:user_id) }
      it { should validate_presence_of(:followed_user_id) }
      it { should belong_to(:user) }
      it { should belong_to(:followed_user) }
    end

    class Following < ActiveRecord::Base
      validates_presence_of :user_id
      validates_presence_of :followed_user_id
      belongs_to :user
      belongs_to :followed_user, :class_name => 'User'
    end

We finally add the association on our user model to make the test pass:

    class User
      has_many :followings
    end

We are now ready to write up the implementation of the `#follows?` and
the `#follow` methods on the User class:

    def follow(another_user)
      self.followings.create(:followed_user_id => another_user.id)
    end

    def follows?(another_user)
      self.followings.exists?(['followed_user_id = ?', another_user])
    end

Now we can move up to the following controller spec, and guess what: It
passes. When we wrote the controller spec and the controller code we
thought about what the API for following should look like, then we
specified it at the model level and wrote an implementation which
adhered to the *contract* we had established earlier.

We can move up one more level to the cucumber feature. Running it, we
see the following error:
`"expected #has_content?("You are now following bob!") to return true, got false (RSpec::Expectations::ExpectationNotMetError)"`.
We can make that pass by adding a flash message on our controller
action:

      flash[:notice] = "You are now following #{user.twiddr_name}!"

We now have one more failing step, which is verifying that the home page
displays the users we are following. So far we haven't really created a
home or welcome page, and have been staying with the default root path
provided by clearance (`Clearance::Sessions#new`). Let's specify that
controller's routes in `spec/controllers/welcome_controller.rb`:

    describe WelcomeController, 'routes' do
      it { should route(:get, '/').to(:action => 'index') }
    end

To make that pass, we create the `WelcomeController` class in
`app/controllers/welcome_controller.rb`, and add the following routes to
`config/routes.rb`:

    >root :to => 'welcome#index'
    resource :welcome, :only => [:index]

Now let's specify some behavior for our welcome controller. When the
user is not logged in, we want to redirect to the sign in page,
otherwise we just render the welcome page:

    describe WelcomeController, 'GET to index without authenticating' do
      before do
        get :index
      end
      it { should redirect_to(sign_in_path) }
    end

    describe WelcomeController, 'GET to index when logged in' do
      let(:user) { Factory(:email_confirmed_user) }
      before do
        controller.current_user = user
        get :index
      end
      it { should render_template(:index) }
    end

Making this pass is quite simple. We've already seen how to require
authentication with clearance: `before_filter :authenticate`. We also
add an empty index action, and create the
`app/views/welcome/index.html.erb` file, currently empty, where we can
start creating twiddr's welcome page.

Now we rerun our cucumber feature which once again reminds us that we
need to list out the user's followings in the welcome page. Easy peasy:

    ><h3>You follow</h3>
    <ul>
    <% current_user.followings.each do |following| %>
      <li class="following"><%= following.followed_user.twiddr_name -%></li>
    <% end %>
    </ul>

At this point, we also realize that an `<li>` tag is more appropriate
than a `<div>` for a list of followings, so we also change the scenario
to look for an `li` and not a `div`. Therefore that verification steps
looks like so:

    And I should see "bob" within "li.following"

Run the feature. It's all green. Run all specs and cucumber scenarios.
We see one failure:
`"expected #has_content?("Follow") to return true, got false (RSpec::Expectations::ExpectationNotMetError)"`.
Not a big deal: we changed the Follow text to an actual button, so we
need to change our feature accordingly. The step can now look like this:

    And I should see the "Follow" button

The step definition is quite simple, because Capybara has an easy way to
find and verify buttons on a page:

    Then /^I should see the "([^"]*)" button$/ do |button_label|
      page.should have_button(button_label)
    end

We can now rerun the feature, as well as the entire suite with just
`rake`, and behold a clean build once again.

What we've learned
------------------

We have started building our own social network using the Outside-in
development methodology with Cucumber, Rspec and other great tools. If
you've followed along and actually built this app, you've experienced
first hand what the process feels like, and hopefully you've started to
see the benefit of writing tests first and value of Outside-in
development:

-   We've already encountered places where a small refactor was
    required, and our tests gave us the confidence to know that
    everything is still working as intended. More significant refactors
    or code optimizations down the road will also be much easier because
    we have significant test coverage in the app.
-   We build more coherent and simpler UIs and workflows, because it
    approaches code from the stakeholder's and business value
    perspectives.
-   While the ability to refactor with confidence is a huge win, we've
    also seen how the process also helps designing the system. We've
    used cucumber for acceptance tests, and used RSpec's tighter
    feedback loop for more fine grained internal design of the APIs. BDD
    allows us to focus on the task at hand, as the primary goal is to
    make the test pass.
-   We constantly get feedback from the system while developing new
    features, so we always know if what we've written is correct, and
    where to go next.
-   We write small pieces of code that make a test pass. Bad code is
    hard to test, so if we write the test first, we are less likely to
    write complex code. Therefore our app will be easier to maintain on
    the long run.
-   If we follow and embrace BDD, we are keeping the test coverage in
    our app high, which will help catch regression bugs when new
    functionality is added and the application gets more complex.

*I hope that this introduction to Outside-in development inspires you to
continue to learn more about the method and the numerous tools that
support it. I encourage you to continue to build out this app -- or any
other project -- so that you can continue to get better until you are
able to experience the development flow that can be achieved with BDD.
**Feel free to ask questions and give feedback in the comments section
of this post**. Thanks!*

***Do read* these awesome Guest Posts:**

-   [Ruby
    Forensics](http://rubylearning.com/blog/2010/10/04/ruby-forensics/)
-   [An introduction to eventmachine, and how to avoid callback
    spaghetti](http://rubylearning.com/blog/2010/10/01/an-introduction-to-eventmachine-and-how-to-avoid-callback-spaghetti/)
-   [The Testing
    Mindset](http://rubylearning.com/blog/2010/09/30/the-testing-mindset/)
-   [An Introduction to Desktop Apps with
    Ruby](http://rubylearning.com/blog/2010/09/29/an-introduction-to-desktop-apps-with-ruby/)
-   [The Ruby
    movement](http://rubylearning.com/blog/2010/09/28/the-ruby-movement/)
-   [Almost everything is an object (and everything is almost an
    object!)](http://rubylearning.com/blog/2010/09/27/almost-everything-is-an-object-and-everything-is-almost-an-object/)
-   [So... you're new to
    Ruby!](http://rubylearning.com/blog/2010/09/24/so-youre-new-to-ruby/)
-   [Incorporating Web APIs to spark computer programming
    exercises](http://rubylearning.com/blog/2010/09/23/incorporating-web-apis-to-spark-computer-programming-exercises/)
-   [14 Ways To Have Fun Coding
    Ruby](http://rubylearning.com/blog/2010/09/22/14-ways-to-have-fun-coding-ruby/)
-   [Writing modular web applications with
    Rack](http://rubylearning.com/blog/2010/09/21/writing-modular-web-applications-with-rack/)
-   [How to Learn Ruby (or any programming
    language)](http://rubylearning.com/blog/2010/09/20/how-to-learn-ruby-or-any-programming-language/)

