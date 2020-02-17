---
layout: post
title:      "Rails User Authentication"
date:       2020-02-17 17:46:42 +0000
permalink:  rails_user_authentication
---


Managing password security carries a lot of weight when building user sign in credentials in a Ruby on Rails application. Fortunately, Rails provides us with tools to store passwords so that hackers don't gain access to users' actual passwords. Introducing the bcrypt gem. 

Bcrypt is a password hashing function. A hash is a number computed by feeding a string to a hash function. It also incorporates a salt, a random string prepended to the password before hashing it. The 'bcrypt' gem needs to be added to your Gemfile.

```
# Gemfile:
gem 'bcrypt'
```

Bcrypt provides a method called has_secure_password that you can use on your ActiveRecord models. has_secure_password adds two fields to your model: password and password_confirmation. These fields don't correspond to database columns. Instead, the method expects there to be a password_digest column defined in your migrations.

```
class User < ActiveRecord::Base
  has_secure_password
end
```


```
class CreateUsers < ActiveRecord::Migration[5.2]
  def change
    create_table :users do |t|
      t.string :name
      t.string :email
      t.string :password_digest

      t.timestamps
    end
  end
end
```

has_secure_password method also allows us to use the authenticate method. Include the authenticate method in your create method in SessionsController to authenticate users' password.

```
class SessionsController < ApplicationController
  def create
           @user = User.find_by(email: params[:user][:email])
            if @user && @user.authenticate(params[:user][:password])
                session[:user_id] = @user.id 
                redirect_to user_path(@user)
            else
                flash[:message] = "Incorrect email or password"
                redirect_to login_path
            end
  end
end
```

