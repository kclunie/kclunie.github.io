---
layout: post
title:      "Relationships by Active Record"
date:       2020-08-10 18:47:41 -0400
permalink:  relationships_by_active_record
---


Seeking relationship advice? Active Record is here to save the day. We want to be able to build great relationships so that our classes can get along and feel close to one another. Active Record allows us to press the easy button to associate models and their database tables. Active Record lets us write quicker and easier code.

Active Record offers many different relationship options:

belongs_to
has_one
has_many
has_many :through
has_one :through
has_and_belongs_to_many

Let's look at an example of how this works. Say we have three models: Writers, Books, and Genres. We need to get these three egotistical classes to work together. 

What we know for sure:

Writers have many books and a book belongs to a writer.
Writers have many genres through books.
Books belong to a genre.
A genre has many books.
A genre has many writers through books.

What are these models and tables going to look like?

**Book Model:**

| id | name | writer_id | genre_id |
| -------- | -------- | -------- | -------- |
| 2     | Harry Potter      | 4     | 3     |

The Books table will have a writer_id column and a genre_id column. These values are foreign keys and will allow us to query a writer's books or genres, a book's writer or genre, and a genre's books and writers through Active Record methods on our classes. 

Our model will now look like this:

```
class Book < ActiveRecord::Base
  belongs_to :writer
  belongs_to :genre
end
```

Keep in mind, ActiveRecord::Base allows us to use these methods such as belongs_to.

**Writer Model**

A writer will have many books and many genres through books. Remeber, books is the joins table and holds the writer_id and a genre_id, so that's taken care of.

| id | name | 
| -------- | -------- | 
| 4     | J. K. Rowling      | 


```
class Writer < ActiveRecord::Base
  has_many :books
  has_many :genres, through: :books
end
```

**Genre Model**

Last but not least, the genre model also relies on the books model to do the heavy lifting and can keep things simple.

| id | name | 
| -------- | -------- | 
| 3     | Fantasy      | 



```
class Genre < ActiveRecord::Base
  has_many :books
  has_many :writers, through: :books
end
```


