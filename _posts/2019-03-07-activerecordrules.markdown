---
layout: post
title:      "ActiveRecordRules"
date:       2019-03-07 14:30:55 +0000
permalink:  activerecordrules
---


1. Connect to the database using: ActiveRecord::Base.establish_connection

2. Create a table to hold your data

3. Link a class "model" to the database table using: class Example < ActiveRecord::Base - now your class will inherit all ActiveRecord's built-in ORM methods like .create, .find, .save

4. Use migrations to alter your database in a structured and organized manner

5. Each migration should go in a seperate file and increment the number in the file name 

6. Inherit from ActiveRecord's ActiveRecord::Migration using class Example < ActiveRecord::Migration

7. Use the change method, which is more common for basic migrations

8. Now that you have access to ActiveRecord::Migration, you can create tables using only Ruby - create_table :example

9. Run rake db:migrate
