---
layout: post
title:      "OmniAuth Setup"
date:       2020-02-26 15:49:13 +0000
permalink:  omniauth_setup
---


It's becoming increasingly popular to allows users to login via a third-party account on modern websites. OmniAuth is a gem for Rails that lets you use multiple authentication providers alongside the more traditional username/password setup.

If you were using Facebook, for example, as your authentication provider, you would want to first add omniauth and omniauth-facebook to the Gemfile and then run bundle install. Next, you'll need to tell OmniAuth about your app's OAuth credentials and create a file named config/initializers/omniauth.rb. It will contain the following lines:

```
Rails.application.config.middleware.use OmniAuth::Builder do
  provider :facebook, ENV['FACEBOOK_KEY'], ENV['FACEBOOK_SECRET']
end
```

Here you're telling your Rails app to use a piece of middleware created by OmniAuth for the Facebook authentication strategy. The ENV constant refers to a global hash for your entire computer environment. You can store any key-value pairs in this hash, so it's a very useful place to keep credentials that you don't want to be managed by Git or displayed on GitHub. You're going to need two pieces of information from Facebook in order to get authentication working: the application key and secret that will identify your app to Facebook. Log in to the Facebook developer site. Create an app and provide your app URL as well as a Valid OAuth redirect URI. 

dotenv-rails is a great way to ensure that environment variables are correctly loaded into the ENV hash in a secure manner. You will want to:

1. Add dotenv-rails to your Gemfile and bundle install.
2. Create a file named .env at the root of your application.
3. Add your Facebook app credentials to the newly created .env file (take the App ID and App Secret values from the Facebook app dashboard).
4. Add .env to your .gitignore file to ensure that you don't accidentally commit your credentials.

```
FACEBOOK_KEY=255911982388118
FACEBOOK_SECRET=01eb24461830c123d732aa78babc901
```

You now need to create a link that will initiate the Facebook OAuth process such as:

```
<%= link_to('Log in with Facebook!', '/auth/facebook') %>
```

Next, you're going to need a User model and a SessionsController to track users who log in via Facebook. 

To handle user sessions, you need to create a single route, sessions#create, which is where Facebook will redirect users in the callback phase of the login process. Add the following to your config/routes.rb:

```
get '/auth/facebook/callback' => 'sessions#create'
```

Your SessionsController holds the create action:

```
class SessionsController < ApplicationController
  def create
    @user = User.find_or_create_by(uid: auth['uid']) do |u|
      u.name = auth['info']['name']
      u.email = auth['info']['email']
      u.image = auth['info']['image']
    end
 
    session[:user_id] = @user.id
 
    render 'welcome/home'
  end
 
  private
 
  def auth
    request.env['omniauth.auth']
  end
end
```

And, finally, since you're re-rendering the welcome#home view upon logging in via Facebook, add a control flow to display user data if the user is logged in and the login link otherwise:

```
<% if session[:user_id] %>
  <h1><%= @user.name %></h1>
  <h2>Email: <%= @user.email %></h2>
  <h2>Facebook UID: <%= @user.uid %></h2>
  <img src="<%= @user.image %>">
<% else %>
  <%= link_to('Log in with Facebook!', '/auth/facebook') %>
<% end %>
```

The end result should be gaining access to the user's data from the provider in your SessionsController, where you can then decide what to do with it. Typically, if a matching User exists in your database, the client will be logged in to your application. If no match is found, a new User will be created using the data received from the provider.
