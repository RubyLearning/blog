---
author: Harold Gimenez
categories:
- Beginners
- Popular
- Ruby
- Ruby Masters
date: 2010-10-05
layout: post
permalink: /2010/10/05/outside-in-development/
tags:
- "Harold Giménez"
- Outside-in Development
- programming
- Ruby
- Ruby Beginners
- Ruby for Noobs
thesis_description:
- "Harold Giménez introduces us to Outside-in Development that helps add value to
  a product's users and stakeholders. A guest post on RubyLearning."
thesis_keywords:
- "Ruby, Programming, Harold Giménez, Ruby for Noobs, Ruby beginners, Outside-in Development"
title: An Introduction to Outside-in Development
topsy_short_url:
- http://bit.ly/9hTxef
---

<div>
  <h3>
    An Introduction to Outside-in Development
  </h3>
  
  <p class="update">
    This guest post is contributed by <b>Harold Giménez</b>, who is a web developer with the crew at <a href="http://thoughtbot.com/">thoughtbot</a>, where he spends his days working with Rails and writing open source software. He&#8217;s also involved with thoughtbot&#8217;s <a href="http://workshops.thoughtbot.com/">workshops</a>, which is a great way to dig deeper into subjects like test-driven Rails development. Follow Harold on twitter at <a href="http://twitter.com/hgimenez">@hgimenez</a>.
  </p>
  
  <p class="block">
    <img class="alignright" height="125" width="125" src="http://rubylearning.com/images/harold-125x125.jpg" alt="Harold Giménez" /> <span class="drop_cap">O</span>utside-in Development is a software development methodology that focuses on providing value to the product&#8217;s users and stakeholders. Cucumber is a BDD tool that supports Outside-in development by running plain text features or user stories as acceptance tests. Well written user stories state clearly their business value, and help developers bring themselves out of the software developer role and into the user role, where we can get a more realistic overview of the application&#8217;s interface and general flow. This leads to more cohesive and simpler software, because you write the simplest amount of code that satisifies a user story, and you often review the application as a user. Outside-in along with the test-driven process helps you write just the minimum amount of code that provides value to stakeholders, and not a line more.
  </p>
  
  <p>
    While still great and recommended, reading much theory and praise about outside-in is not as effective as actually trying it and seeing it in action. We will write the beginnings of <b>twiddr</b>, a small twitter clone in Rails 3 using the outside-in process. Our testing arsenal will consist of the following excellent Ruby libraries.
  </p>
  
  <ul>
    <li>
      Cucumber: A plain text story runner.
    </li>
    <li>
      RSpec: A BDD framework for Ruby.
    </li>
    <li>
      Factory Girl: A fixture replacement framework.
    </li>
    <li>
      Shoulda: A set of RSpec matchers, among other things.
    </li>
  </ul>
  
  <p>
    We will explain in more detail how these frameworks work together as we start developing the application. To get started quickly, we will use <a href="http://github.com/thoughtbot/suspenders">suspenders</a> to create an application with all of our tools installed and configured. Since this is a Rails 3 application, we will use the beta version of suspenders. Install it by running <code>gem install suspenders --pre</code>. Now that suspenders is installed, we can bootstrap twiddr with <code>suspenders create twiddr</code>.
  </p>
  
  <p>
    At this point, we have a twiddr application including authentication with <a href="http://github.com/thoughtbot/clearance">clearance</a>, a simple Rails authentication solution with email and password. Clearance also includes cucumber features that you can view in the <code>features</code> directory. Let&#8217;s run them right now by running <code>rake db:migrate</code> to create the users table, <code>script/rails generate clearance_views</code> to generate clearance views with <a href="http://github.com/justinfrench/formtastic">formtastic</a>, and <code>rake</code> to run all specs and features. You should see a very satisfying series of green dots appear on your terminal, along with &#8220;0 Failures&#8221;.
  </p>
  
  <p>
    Let&#8217;s create our first feature. The anatomy of a feature is the following:
  </p>
  
  <pre>In order to [business value]
As a [role]
I want to [some action]</pre>
  
  <p>
    Notice how a feature includes who, what and most importantly: <em>why</em>. Our first feature could look something like the following:
  </p>
  
  <pre>Feature: Users have a twiddr login name
  In order to mention other twiddr users by login name
  As a twiddr user
  I can pick a login name</pre>
  
  <p>
    There will be many scenarios accompanying this feature. Scenarios will follow the four stages of testing: setup, exercise, verify and teardown. Let&#8217;s write a few scenarios that come to mind. A simple scenario looks like this:
  </p>
  
  <pre>Given [context]
When I do [action]
Then I should see [outcome]</pre>
  
  <p>
    The <code>Given</code> step is where you set up the context of your scenario. Every scenario starts with a blank slate, so it is important to create a state in your application for example by creating data in the database, or by navigating to a specific page. The <code>When</code> step is where you exercise the application in order to accomplish what needs testing. In the case of a web app like twiddr, this is usually where you fill in forms, press buttons, click links, or otherwise interact with the system in some way. Finally, the <code>Then</code> step is where you verify the result, and it&#8217;s where we check that the correct pages are rendered, that we see a success or error message, or anything that could help us verify that the prior action was successful. As we move along with creating our own features, this will become much clearer.
  </p>
  
  <p>
    The final stage of testing, <code>teardown</code>, is taken care of by cucumber automatically. It refers to clearing out the state of the system so that there are no nasty leftovers from one test to the next. In most cases, this means deleting all data from the database.
  </p>
  
  <p>
    Back to developing our app, we already have authentication set up in the application via clearance, but there is value in also having a twiddr login, so let&#8217;s go ahead and add that functionality to user model. To get started, we can work off of the clearance sign up scenarios that you can find in <code>features/sign_up.feature</code>. Let&#8217;s modify the scenario titled &#8220;User signs up with valid data&#8221; and add a step where the user fills in their twiddr name. The step definition ends up looking like this:
  </p>
  
  <pre>Scenario: User signs up with valid data
  When I go to the sign up page
  And I fill in "Email" with "email@person.com"
  And I fill in "Twiddr name" with "user"
  And I fill in "Password" with "password"
  And I fill in "Confirm password" with "password"
  And I press "Sign up"
  Then I should see "instructions for confirming"
  And a confirmation message should be sent to "email@person.com"</pre>
  
  <p>
    The above is executable code. Cucumber uses regular expressions to match the plain text features and executes the resulting step definitions. Finally, note that each of these stages of a cucumber feature can have many steps: by adding more steps starting with <code>And</code>, we can create more complex contexts (Given/And), actions (When/And) or outcomes (Then/And).
  </p>
  
  <p>
    At this point it is worth viewing the step definitions provided by Capybara if you haven&#8217;t already. They can be found in <code>features/step_definitions/web_steps.rb</code>, and have definitions for most web interactions like <code>I go to...</code>, <code>I fill in...</code>, or <code>I should see...</code>
  </p>
  
  <p>
    Let&#8217;s run the new scenario, and watch it fail:
  </p>
  
  <p>
    $ bundle exec cucumber features/sign_up.feature
  </p>
  
  <p>
    The output will look something like this:
  </p>
  
  <pre>........F-----.................

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
</pre>
  
  <p>
    The error message tells us that the text field labeled &#8220;Twiddr name&#8221; was not found on the form, which is exactly what we were expecting. Cucumber is also telling us what to do next: Add a Twiddr name input field to the user signup form. To do that, open up <code>app/views/users/_inputs.html.erb</code> and add a line to include the :twiddr&#095;name input. It should look like this:
  </p>
  
  <pre>&lt;%= form.inputs do %&gt;
  &lt;%= form.input :email %&gt;
  &lt;%= form.input :twiddr_name %&gt;
  &lt;%= form.input :password %&gt;
  &lt;%= form.input :password_confirmation, :label =&gt; "Confirm password" %&gt;
&lt;% end %&gt;</pre>
  
  <p>
    Part of the outside-in process is to only write the simplest amount of code that could make the test pass, and not a line more. At this point you may be tempted to go on with implementing the twiddr&#095;name functionality, but it&#8217;s important to contain your fingers from typing any further, and instead rerun the feature to see what the next step should be.
  </p>
  
  <p>
    Rerunning the feature now shows that not only does our scenario not pass, but we&#8217;ve also broken a different scenario. Don&#8217;t panic! All scenarios that display this form are now broken because the <code>User</code> model doesn&#8217;t have a <code>twiddr_name</code> attribute. To add it, we create a database migration. On your terminal, type:
  </p>
  
  <pre>$ ./script/rails generate migration add_twiddr_name_to_users twiddr_name:string
$ rake db:migrate && rake db:test:prepare</pre>
  
  <p>
    This will add a column called <code>twiddr_name</code> of type <code>string</code> to the <code>users</code> table. Run the scenario once again, and you&#8217;ll note that we&#8217;ve reached a clean build: all tests pass. We should add some more behavior around our new <code>twiddr_name</code>. For example, we probably want to require that new users enter a twiddr&#095;name when signing up to the site. We can add a scenario that tests for that:
  </p>
  
  <pre>Scenario: User tries to sign up without a twiddr name
  When I go to the sign up page
  And I fill in "Email" with "email@person.com"
  And I fill in "Password" with "password"
  And I fill in "Confirm password" with "password"
  And I press "Sign up"
  Then the "Twiddr name" field should have the "can't be blank" error</pre>
  
  <p>
    Run the scenario, and you will note that the last step is not defined. Cucumber will even print out a starting point for the step definition. Copy the provided template and paste it in a new file called <code>features/step_definitions/form_error_steps.rb</code>. The definition of this step will use CSS selectors to verify that the field contains the expected error message, based on the markup generated by formtastic:
  </p>
  
  <pre>Then /^the "([^"]*)" field should have the "([^"]*)" error$/ do |field_label, error_message|
  within('form li') do
    page.should have_css("label:contains('#{field_label}') ~ p.inline-errors", :text =&gt; error_message)
  end
end</pre>
  
  <p>
    Dropping that into the <code>form_error_steps.rb</code> will allow us to move forward with our scenario: It fails because we don&#8217;t have any validations on <code>twiddr_name</code>. We want to always make sure that <code>twiddr_name</code> is present. Let&#8217;s drop to the model spec level to specify this new behavior. Create a file called <code>spec/models/user_spec.rb</code> and let&#8217;s specify this requirement:
  </p>
  
  <pre>require 'spec_helper'

describe User, 'valid' do
  it { should validate_presence_of :twiddr_name }
end</pre>
  
  <p>
    The <code>validate_presence_of</code> method is a <a href="http://github.com/thoughtbot/shoulda">shoulda</a> matcher. There are a ton of useful matchers. For other active record matcher examples, please refer to <a href="http://rdoc.info/github/thoughtbot/shoulda/master/Shoulda/ActiveRecord/Matchers">the documentation</a>.
  </p>
  
  <p>
    First, watch it fail by running <code>bundle exec rspec spec/models/user_spec.rb</code>. To make it pass, we open up <code>app/models/user.rb</code> and add the one required validation line: <code>validates_presence_of :twiddr_name</code>. Running the spec again will reveal that we&#8217;re once again green. Now we can return back up to the cucumber level by rerunning our feature: <code>bundle exec cucumber features/sign_up.feature</code>. This time we notice that the feature we are developing is passing, but we broke a few other features because of invalid users being created, which brings us to another aspect of testing: <code>factories</code>.
  </p>
  
  <p>
    During testing it is very often required to generate setup data to create context for the test. One great way to manage that is by using a factory library, where we define a few factory templates, and then we ask the factory to create instances of those objects to either get a hold of them in a variable or store them in the database. It then becomes trivial to get a hold of valid instances of models in your application, which is very useful for setting up a test&#8217;s context. In this application, we are using <a href="http://github.com/thoughtbot/factory_girl">factory_girl</a>.
  </p>
  
  <p>
    What&#8217;s breaking in the above feature is that the user factory is not including <code>:twiddr_name</code> when it generates objects. Therefore it is creating invalid objects, and ActiveRecord is rightfully raising an error. The fix in this case is to add the new required attribute to the user factory, found in <code>spec/factories/clearance.rb</code>. In that file, the user factory definition could look like so (we simply use the email to create a twiddr_name):
  </p>
  
  <pre>Factory.define :user do |user|
  user.email                 { Factory.next :email }
  user.password              { "password" }
  user.password_confirmation { "password" }
  user.twiddr_name           { |u| u.email.split("@").first }
end</pre>
  
  <p>
    At this point, we once again have a green build. We can move on to another feature (save the following in <code>features/user_views_profiles.feature</code>):
  </p>
  
  <pre>Feature: user profiles
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
    And I should see "Follow"</pre>
  
  <p>
    Notice the first setup step in the above scenario: &#8220;Given the following email confirmed user exists:&#8221; followed by a table. Furthermore, if you run this scenario you will notice that that step passes even though we haven&#8217;t written a step definition for it. What&#8217;s going on here is that Factory Girl conveniently creates step definitions for all of our factories, making it very easy to create the data required to provide some context for your tests. In the above example, &#8220;email confirmed user&#8221; is the name of a factory defined in <code>spec/factories/clearance.rb</code>, and the cucumber <a href="http://github.com/aslakhellesoy/cucumber/wiki/multiline-step-arguments">table</a> that follows maps attributes to values for the records you&#8217;re creating. It&#8217;s simpler and therefore recommended to provide values only for the attributes that you&#8217;re interested in for this scenario. So in this case, we really don&#8217;t care what the user&#8217;s password is, but we care about the twiddr name and email because we&#8217;re verifying them a few lines down.
  </p>
  
  <p>
    When you run this scenario, you will notice that cucumber did not know how to map <code>the profile page for "hgimenez"</code> to an actual URL in your application. To tell cucumber how to do that, we add an entry in <code>features/support/path.rb</code> like so:
  </p>
  
  <pre>when /the profile page for "([^\"]+)"/
  user = User.find_by_twiddr_name!($1)
  user_path(user)</pre>
  
  <p>
    We are using a regular expression to capture the twiddr name provided in the step definition, and using the captured string to find that user in the database. On tests it is a good idea to use the &#8220;dangerous&#8221; versions of active record finders (ending with <code>!</code>), so that if the record is not found, Active Record will raise a clear error message, making debugging much easier.
  </p>
  
  <p>
    Adding that entry in <code>features/support/paths.rb</code> gets us further in that step definition. That step still fails though, but this time for a different reason: <code>The action 'show' could not be found for Clearance::UsersController (AbstractController::ActionNotFound)</code>. In this case, our users controller does not specify a show action. Since this is a clearance controller, we can extend it by simply creating a new controller and inheriting from <code>Clearance::UsersController</code>. This will allow us to both create new actions or extend the default ones provided by clearance. Following cucumber&#8217;s failure message, our next step is to create show action on the users controller:
  </p>
  
  <pre>class UsersController &lt; Clearance::UsersController
  def show
  end
end</pre>
  
  <p>
    But even with this in place, cucumber continues to complaint about the show action being unavailable. It seems like there could be a routing problem, so let&#8217;s again move down to the controller spec level and specify our new route:
  </p>
  
  <pre>require 'spec_helper'

describe UsersController, 'routes' do
  it { should route(:get, 'users/1').to(:action =&gt; 'show', :id =&gt; 1) }
end</pre>
  
  <p>
    The spec above is a shoulda <a href="http://rdoc.info/github/thoughtbot/shoulda/master/Shoulda/ActionController/Matchers">controller matcher</a>. We have created a new class for the UsersController, and need the user routes to map to this new class (without the Clearance namespace). Additionally, clearance has a few nested resources under users that we will still need. If we look at the clearance routes file, we can pull out the relevant pieces and include it in our own app&#8217;s <code>config/routes.rb</code>, where we can get rid of the clearance namespace:
  </p>
  
  <pre>resources :users, :controller =&gt; 'users', &#058;only =&gt; [:show, :create] do
  resource :password,
    :controller =&gt; 'clearance/passwords',
    &#058;only       =&gt; [:create, :edit, :update]

  resource :confirmation,
    :controller =&gt; 'clearance/confirmations',
    &#058;only       =&gt; [:new, :create]
end</pre>
  
  <p>
    Running the controller spec again will show that we&#8217;ve wired up the routes correctly, and running the entire cucumber suite will show that we have not broken any of the nested routes that clearance originally provided. This is just another advantage of having the kind of strong test coverage that is achieved by BDD, and definitely brings confidence in the quality of the application you&#8217;re building: We&#8217;ve made a somewhat major refactor, and but we&#8217;re confident that things are wired up correctly <em>because our test suite passes</em>.
  </p>
  
  <p>
    Moving along, we can rerun the feature file, at which point cucumber complaints that there&#8217;s no users/show view. Let&#8217;s create it!
  </p>
  
  <pre>&lt;h2&gt;&lt;%= @user.twiddr_name -%&gt;&lt;/h2&gt;

&lt;div id="profile"&gt;
  &lt;div class="twiddr_name"&gt;&lt;%= @user.twiddr_name -%&gt;&lt;/div&gt;
  &lt;div class="email"&gt;&lt;%= @user.email -%&gt;&lt;/div&gt;
  &lt;div class="follow"&gt;Follow&lt;/div&gt;
&lt;/div&gt;</pre>
  
  <p>
    Running the feature now reveals that the <code>@user</code> instance variable is not set. We can assign this instance variable in the users controller and try again:
  </p>
  
  <pre>def show
  @user = User.find(params[:id])
end</pre>
  
  <p>
    Run rake, and find that all specs and scenarios are passing. We can move on to following users. In <code>features/user_follows_another_user.feature</code>:
  </p>
  
  <pre>Feature: Follow twiddr users
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
    And I should see "bob" within "div.following"</pre>
  
  <p>
    The first failure message is &#8220;no button with value or id or text &#8216;Follow bob&#8217; found (Capybara::ElementNotFound)&#8221;, because the user profile pages do not have an actual follow button. At this point, we should have some idea of how we&#8217;ll implement user following. A clean RESTful way to go about it is to create a user_follows resource, and to POST to it when a user wants to follow someone else. Let&#8217;s add a button that posts to that resource, in <code>app/views/users/show.html.erb</code>:
  </p>
  
  <pre>&gt;&lt;div id="profile"&gt;
  &lt;div class="twiddr_name"&gt;&lt;%= @user.twiddr_name -%&gt;&lt;/div&gt;
  &lt;div class="email"&gt;&lt;%= @user.email -%&gt;&lt;/div&gt;
  &lt;div class="follow"&gt;&lt;%= button_to("Follow #{@user.twiddr_name}", user_follows_path(@user)) -%&gt; &lt;/div&gt;
&lt;/div&gt;</pre>
  
  <p>
    Rerunning the feature now shows <code>"undefined method `user&lt;em>follows&lt;/em>path' for #&lt;#&lt;Class:0x103d108e0&gt;:0x103d0a4e0&gt; (ActionView::Template::Error)"</code> because there is no <code>user&#095;follows</code> resource or route yet. This is a good point to step down into RSpec land while we build this resource. We create <code>spec/controller/follows&#095;controller&#095;spec.rb</code> and specify a route:
  </p>
  
  <pre>require 'spec_helper'

describe FollowsController, 'routes' do
  it { should route(:post, '/users/1/follows').to(:action =&gt; 'create', :user_id =&gt; 1) }
end</pre>
  
  <p>
    And we can now enter BDD cycle. Run the spec with <code>bundle exec rspec spec/controllers/follows_controller_spec.rb</code> and we get the error <code>"uninitialized constant FollowsController (NameError)"</code> because we have not created the follows controller. Create it in <code>app/controllers/follows_controller.rb</code> with the following content:
  </p>
  
  <pre>class FollowsController &lt; ApplicationController
end</pre>
  
  <p>
    Rerunning the spec, we now see <code>No route matches "/users/1/follows"</code>. Great, let&#8217;s add that route nested within the users resource, which now looks like this:
  </p>
  
  <pre>resources :users, :controller =&gt; 'users', &#058;only =&gt; [:show, :create] do
  resource :password,
    :controller =&gt; 'clearance/passwords',
    &#058;only       =&gt; [:create, :edit, :update]

  resource :confirmation,
    :controller =&gt; 'clearance/confirmations',
    &#058;only       =&gt; [:new, :create]

  resource :follows, &#058;only =&gt; [:create] # add this
end</pre>
  
  <p>
    Run the spec again to get feedback from RSpec: The test passes so the route is working as we expected. Back on the cucumber level we rerun the feature which now finds the button and route, but errors on <code>"The action 'create' could not be found for FollowsController (AbstractController::ActionNotFound)"</code>. Time to bring the follows controller to life with the create action.
  </p>
  
  <p>
    Let&#8217;s specify the controller behavior in RSpec. We want only signed in users to be able to hit this action, so let&#8217;s spec that out:
  </p>
  
  <pre>describe FollowsController, 'POST to create without authenticating' do
  before do
    post :create, :user_id =&gt; 1
  end
  it { should redirect_to(sign_in_path) }
end</pre>
  
  <p>
    This test makes sure that we redirect to the sign in path if no user is authenticated. To make it pass, we simply add <code>before_filter :authenticate</code> to our controller. Now on to the more details about the create action: We want to verify that the signed in user ends up following the provided user when the action runs.
  </p>
  
  <p>
    In spec&#8217;s setup we create two users, we simulate authenticating by assigning controller&#8217;s the current_user, and we exercise the controller by invoking a POST to create. We then verify two things: that the user is indeed following the provided user, and that we redirect to the root path. Note that we still don&#8217;t have any logic or even models to hold the user following relationships, but we can start to think about how that interface will look like. One of these tests already shows some of that: <code>current_user.follows?</code>.
  </p>
  
  <pre>describe FollowsController, 'authenticated POST to create' do
  let(:follower)       { Factory(:email_confirmed_user) }
  let(:user_to_follow) { Factory(:email_confirmed_user) }
  before do
    controller.current_user = follower #sign in
    post :create, :user_id =&gt; user_to_follow.id
  end

  it { should redirect_to(root_path) }
  it 'makes the signed in user follow the provided user' do
    controller.current_user.follows?(user_to_follow).should be_true
  end
end</pre>
  
  <p>
    We run this test, watch it fail, and come up with a first pass at an implementation:
  </p>
  
  <pre>def create
  user = User.find(params[:user_id])
  current_user.follow(user)
  redirect_to :root_path
end</pre>
  
  <p>
    This gets us a little further, because the redirect spec now passes. It&#8217;s time to specify our models, and how the <code>follow</code> method on the user class will behave. We will also need a <code>follows?</code> method that determines whether a user follows another one. Let&#8217;s spec this out <code>spec/models/user_spec.rb</code>.
  </p>
  
  <pre>describe User, '#follows?' do
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
end</pre>
  
  <p>
    We can model user followings with a simple has_many association on the user model. Let&#8217;s specify that on the valid user context using another shoulda matcher:
  </p>
  
  <pre>describe User, 'valid' do
  it { should validate_presence_of   :twiddr_name }
  it { should have_many :followings } # add this
end</pre>
  
  <p>
    Our error message is now: &#8220;Expected User to have a has_many association called followings (no association called followings)&#8221;. Let&#8217;s add the followings table with a database migration. Run <code>./script/rails generate migration create_followings</code> and add the following definition:
  </p>
  
  <pre>class CreateFollowings &lt; ActiveRecord::Migration
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
end</pre>
  
  <p>
    Run <code>rake db:migrate && rake db:test:prepare</code> to create the table. We can now create a Following spec and model, where we probably want to validate presence of user_id:
  </p>
  
  <pre>require 'spec_helper'

describe Following, 'valid' do
  it { should validate_presence_of(:user_id) }
  it { should validate_presence_of(:followed_user_id) }
  it { should belong_to(:user) }
  it { should belong_to(:followed_user) }
end</pre>
  
  <pre>class Following &lt; ActiveRecord::Base
  validates_presence_of :user_id
  validates_presence_of :followed_user_id
  belongs_to :user
  belongs_to :followed_user, :class_name =&gt; 'User'
end</pre>
  
  <p>
    We finally add the association on our user model to make the test pass:
  </p>
  
  <pre>class User
  has_many :followings
end</pre>
  
  <p>
    We are now ready to write up the implementation of the <code>#follows?</code> and the <code>#follow</code> methods on the User class:
  </p>
  
  <pre>def follow(another_user)
  self.followings.create(:followed_user_id =&gt; another_user.id)
end

def follows?(another_user)
  self.followings.exists?(['followed_user_id = ?', another_user])
end</pre>
  
  <p>
    Now we can move up to the following controller spec, and guess what: It passes. When we wrote the controller spec and the controller code we thought about what the API for following should look like, then we specified it at the model level and wrote an implementation which adhered to the <em>contract</em> we had established earlier.
  </p>
  
  <p>
    We can move up one more level to the cucumber feature. Running it, we see the following error: <code>"expected #has_content?("You are now following bob!") to return true, got false (RSpec::Expectations::ExpectationNotMetError)"</code>. We can make that pass by adding a flash message on our controller action:
  </p>
  
  <pre>  flash[:notice] = "You are now following #{user.twiddr_name}!"
</pre>
  
  <p>
    We now have one more failing step, which is verifying that the home page displays the users we are following. So far we haven&#8217;t really created a home or welcome page, and have been staying with the default root path provided by clearance (<code>Clearance::Sessions#new</code>). Let&#8217;s specify that controller&#8217;s routes in <code>spec/controllers/welcome_controller.rb</code>:
  </p>
  
  <pre>describe WelcomeController, 'routes' do
  it { should route(:get, '/').to(:action =&gt; 'index') }
end</pre>
  
  <p>
    To make that pass, we create the <code>WelcomeController</code> class in <code>app/controllers/welcome_controller.rb</code>, and add the following routes to <code>config/routes.rb</code>:
  </p>
  
  <pre>&gt;root :to =&gt; 'welcome#index'
resource :welcome, &#058;only =&gt; [:index]</pre>
  
  <p>
    Now let&#8217;s specify some behavior for our welcome controller. When the user is not logged in, we want to redirect to the sign in page, otherwise we just render the welcome page:
  </p>
  
  <pre>describe WelcomeController, 'GET to index without authenticating' do
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
end</pre>
  
  <p>
    Making this pass is quite simple. We&#8217;ve already seen how to require authentication with clearance: <code>before_filter :authenticate</code>. We also add an empty index action, and create the <code>app/views/welcome/index.html.erb</code> file, currently empty, where we can start creating twiddr&#8217;s welcome page.
  </p>
  
  <p>
    Now we rerun our cucumber feature which once again reminds us that we need to list out the user&#8217;s followings in the welcome page. Easy peasy:
  </p>
  
  <pre>&gt;&lt;h3&gt;You follow&lt;/h3&gt;
&lt;ul&gt;
&lt;% current_user.followings.each do |following| %&gt;
  &lt;li class="following"&gt;&lt;%= following.followed_user.twiddr_name -%&gt;&lt;/li&gt;
&lt;% end %&gt;
&lt;/ul&gt;</pre>
  
  <p>
    At this point, we also realize that an <code>&lt;li&gt;</code> tag is more appropriate than a <code>&lt;div&gt;</code> for a list of followings, so we also change the scenario to look for an <code>li</code> and not a <code>div</code>. Therefore that verification steps looks like so:
  </p>
  
  <pre>And I should see "bob" within "li.following"</pre>
  
  <p>
    Run the feature. It&#8217;s all green. Run all specs and cucumber scenarios. We see one failure: <code>"expected #has_content?("Follow") to return true, got false (RSpec::Expectations::ExpectationNotMetError)"</code>. Not a big deal: we changed the Follow text to an actual button, so we need to change our feature accordingly. The step can now look like this:
  </p>
  
  <pre>And I should see the "Follow" button</pre>
  
  <p>
    The step definition is quite simple, because Capybara has an easy way to find and verify buttons on a page:
  </p>
  
  <pre>Then /^I should see the "([^"]*)" button$/ do |button_label|
  page.should have_button(button_label)
end</pre>
  
  <p>
    We can now rerun the feature, as well as the entire suite with just <code>rake</code>, and behold a clean build once again.
  </p>
  
  <h2>
    What we&#8217;ve learned
  </h2>
  
  <p>
    We have started building our own social network using the Outside-in development methodology with Cucumber, Rspec and other great tools. If you&#8217;ve followed along and actually built this app, you&#8217;ve experienced first hand what the process feels like, and hopefully you&#8217;ve started to see the benefit of writing tests first and value of Outside-in development:
  </p>
  
  <ul>
    <li>
      We&#8217;ve already encountered places where a small refactor was required, and our tests gave us the confidence to know that everything is still working as intended. More significant refactors or code optimizations down the road will also be much easier because we have significant test coverage in the app.
    </li>
    <li>
      We build more coherent and simpler UIs and workflows, because it approaches code from the stakeholder&#8217;s and business value perspectives.
    </li>
    <li>
      While the ability to refactor with confidence is a huge win, we&#8217;ve also seen how the process also helps designing the system. We&#8217;ve used cucumber for acceptance tests, and used RSpec&#8217;s tighter feedback loop for more fine grained internal design of the APIs. BDD allows us to focus on the task at hand, as the primary goal is to make the test pass.
    </li>
    <li>
      We constantly get feedback from the system while developing new features, so we always know if what we&#8217;ve written is correct, and where to go next.
    </li>
    <li>
      We write small pieces of code that make a test pass. Bad code is hard to test, so if we write the test first, we are less likely to write complex code. Therefore our app will be easier to maintain on the long run.
    </li>
    <li>
      If we follow and embrace BDD, we are keeping the test coverage in our app high, which will help catch regression bugs when new functionality is added and the application gets more complex.
    </li>
  </ul>
  
  <p>
    <em>I hope that this introduction to Outside-in development inspires you to continue to learn more about the method and the numerous tools that support it. I encourage you to continue to build out this app &#8211; or any other project &#8211; so that you can continue to get better until you are able to experience the development flow that can be achieved with BDD. <b>Feel free to ask questions and give feedback in the comments section of this post</b>. Thanks!</em>
  </p>
  
  <p>
    <b><em>Do read</em> these awesome Guest Posts:</b>
  </p>
  
  <ul>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/04/ruby-forensics/">Ruby Forensics</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/10/01/an-introduction-to-eventmachine-and-how-to-avoid-callback-spaghetti/">An introduction to eventmachine, and how to avoid callback spaghetti</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/30/the-testing-mindset/">The Testing Mindset</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/29/an-introduction-to-desktop-apps-with-ruby/">An Introduction to Desktop Apps with Ruby</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/28/the-ruby-movement/">The Ruby movement</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/27/almost-everything-is-an-object-and-everything-is-almost-an-object/">Almost everything is an object (and everything is almost an object!)</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/24/so-youre-new-to-ruby/">So… you’re new to Ruby!</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/23/incorporating-web-apis-to-spark-computer-programming-exercises/">Incorporating Web APIs to spark computer programming exercises</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/22/14-ways-to-have-fun-coding-ruby/">14 Ways To Have Fun Coding Ruby</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/21/writing-modular-web-applications-with-rack/">Writing modular web applications with Rack</a>
    </li>
    <li>
      <a href="http://rubylearning.com/blog/2010/09/20/how-to-learn-ruby-or-any-programming-language/">How to Learn Ruby (or any programming language)</a>
    </li>
  </ul>
</div>

Technorati Tags: <a href="http://technorati.com/tag/Ruby" rel="tag">Ruby</a>, <a href="http://technorati.com/tag/Programming" rel="tag"> Programming</a>, <a href="http://technorati.com/tag/Harold+Gim%C3%A9nez" rel="tag"> Harold Giménez</a>, <a href="http://technorati.com/tag/Ruby+for+Noobs" rel="tag"> Ruby for Noobs</a>, <a href="http://technorati.com/tag/Ruby+beginners" rel="tag"> Ruby beginners</a>, <a href="http://technorati.com/tag/Outside-in+Development" rel="tag"> Outside-in Development</a>
