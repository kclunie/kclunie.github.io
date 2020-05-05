---
layout: post
title:      "InterActiveRecordFace"
date:       2020-05-05 02:22:42 +0000
permalink:  interactiverecordface
---


Simply put, Active Record is the middle man between a database and application. AKA the M in MVC. Active Record serves up data models for users in a non-complicated way. Active Record can also be called an ORM, Object Relational Mapping system. This means that Active Record lets you interact with data like a normal Ruby object by taking data stored in a database table in rows and columns and modifying or retrieving them without writing direct SQL statements. 

Active Record lets you create a Ruby object that represents a row in one of your database tables, like a User. First, in storing information about your users, you create a database table called users. Second, you want to be able to access that data from your application, so you create a model called User which inherits methods from Active Record. One table corresponds with one model. To query a list of all your users in a database, you can type User.all and Active Record returns your list of User objects in an array. 

An important feature of Active Record are migrations. A migration is a set of directions that tell Rails how you want to create or change a database. Again, Active Record allows you to avoid manually writing SQL code to create your database table. Just specify the correct Ruby method and parameters. You can add or drop a table and add or remove a column. For example:

`rails generate migration AddNameToProducts name:string`

Will generate:

```
class AddNameToProducts < ActiveRecord::Migration[5.0]
  def change
    add_column :products, :name, :string
  end
end
```

The `rails db:migrate` command runs migrations to create tables and update a database schema. When you run that command, Rails will use Ruby code to execute the proper SQL code to set up your database table. Errors happen, but don't worry if you make a mistake during a migration. Use `rails db:rollback` and the last series of migrations that you ran will be reversed.

In Rails, an association is a connection between two Active Record models. There are 6 different types of associations in Rails including: belongs_to, has_one, has_many, has_many :through, has_one :through, and has_and_belongs_to_many. Declaring associations in Rails, make common operations simpler and easier in your code. Lets say we have a Rails application that includes a model for users and a model for posts, and users have many posts:

```
class User < ApplicationRecord
  has_many :posts
end
 
class Post < ApplicationRecord
  belongs_to :user
end
```

Creating a new post for a user works as simply as:

`@post = @user.posts.create`

Models represent data and logic and Active Record facilitates the creation and use of objects whose data requires persistent storage to a database. Active Record is the interface that Rails provides you between the database and an application. 
