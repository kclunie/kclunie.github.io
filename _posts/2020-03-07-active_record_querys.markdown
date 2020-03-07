---
layout: post
title:      "Active Record Querys"
date:       2020-03-07 12:52:34 +0000
permalink:  active_record_querys
---


If you're used to using raw SQL to find database records, it turns out there’s a simpler way to carry out the same operations in Rails. Active Record produces the same results, but in a more concise manner. Instead of using SQL to retrieve data from the database, give Active Record a try.

To retrieve objects from the database, Active Record provides several finder methods. Each finder method allows you to pass arguments into it to perform certain queries on your database without writing raw SQL. Below are some popular query methods.

Finder methods that return a collection, such as where, return an instance of ActiveRecord::Relation. Methods that find a single entity, such as find, return a single instance of the model.

**Retrieving a Single Object**

Active Record provides several different ways of retrieving a single object for example, find.

Using the find method, you can retrieve the object corresponding to the specified primary key that matches any supplied options. For example:

```
# Find the client with primary key (id) 10.
client = Client.find(10)
# => #<Client id: 10, first_name: "Ryan">
```

The SQL equivalent of the above is:

```
SELECT * FROM clients WHERE (clients.id = 10) LIMIT 1
```

**Conditions**

The where method allows you to specify conditions to limit the records returned, representing the WHERE-part of the SQL statement. Conditions can either be specified as a string, array, or hash.
Pure String Conditions

If you'd like to add conditions to your find, you could just specify them in there, just like Client.where("orders_count = '2'"). This will find all clients where the orders_count field's value is 2.

**Ordering**

To retrieve records from the database in a specific order, you can use the order method.

For example, if you're getting a set of records and want to order them in ascending order by the created_at field in your table:

```
Client.order(:created_at)
# OR
Client.order("created_at")
```

You could specify ASC or DESC as well:

```
Client.order(created_at: :desc)
# OR
Client.order(created_at: :asc)
# OR
Client.order("created_at DESC")
# OR
Client.order("created_at ASC")
```

**Joining Tables**

Active Record provides two finder methods for specifying JOIN clauses on the resulting SQL: joins and left_outer_joins. While joins should be used for INNER JOIN or custom queries, left_outer_joins is used for queries using LEFT OUTER JOIN.

**joins**

There are many ways to use the joins method. You can just supply the raw SQL specifying the JOIN clause to joins:

```
Author.joins("INNER JOIN posts ON posts.author_id = authors.id AND posts.published = 't'")
```

This will result in the following SQL:

```
SELECT authors.* FROM authors INNER JOIN posts ON posts.author_id = authors.id AND posts.published = 't'
```

**Using Array/Hash of Named Associations**

Active Record lets you use the names of the associations defined on the model as a shortcut for specifying JOIN clauses for those associations when using the joins method. For example, consider the following Category, Article, Comment, Guest and Tag models:

```
class Category < ApplicationRecord
  has_many :articles
end
 
class Article < ApplicationRecord
  belongs_to :category
  has_many :comments
  has_many :tags
end
 
class Comment < ApplicationRecord
  belongs_to :article
  has_one :guest
end
 
class Guest < ApplicationRecord
  belongs_to :comment
end
 
class Tag < ApplicationRecord
  belongs_to :article
end
```

Now all of the following will produce the expected join queries using INNER JOIN:

Joining a Single Association

```
Category.joins(:articles)
```

This produces:

```
SELECT categories.* FROM categories
  INNER JOIN articles ON articles.category_id = categories.id
```

This is saying: "return a Category object for all categories with articles". You will see duplicate categories if more than one article has the same category. If you want unique categories, you can use Category.joins(:articles).distinct.

**Joining Multiple Associations**

```
Article.joins(:category, :comments)
```

This produces:

```
SELECT articles.* FROM articles
  INNER JOIN categories ON categories.id = articles.category_id
  INNER JOIN comments ON comments.article_id = articles.id
```

This is saying: "return all articles that have a category and at least one comment". Again, articles with multiple comments will show up multiple times.

**left_outer_joins**

If you want to select a set of records whether or not they have associated records you can use the left_outer_joins method.

```
Author.left_outer_joins(:posts).distinct.select('authors.*, COUNT(posts.*) AS posts_count').group('authors.id')
```

Which produces:

```
SELECT DISTINCT authors.*, COUNT(posts.*) AS posts_count FROM "authors"
LEFT OUTER JOIN posts ON posts.author_id = authors.id GROUP BY authors.id
```

This is saying: "return all authors with their count of posts, whether or not they have any posts at all"

