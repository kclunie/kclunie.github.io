---
layout: post
title:      "The Next Episode: SQL"
date:       2020-05-26 02:42:10 +0000
permalink:  the_next_episode_sql
---


What is SQL aka Structured Query Language?  SQL is a lanuage that is used to communicate with databases. Databases being where you store your data. If you want to add, edit or pull information to a database, you can use SQL. 

What Can SQL do?

* SQL can execute queries against a database
* SQL can retrieve data from a database
* SQL can insert records in a database
* SQL can update records in a database
* SQL can delete records from a database
* SQL can create new databases
* SQL can create new tables in a database
* SQL can create stored procedures in a database
* SQL can create views in a database
* SQL can set permissions on tables, procedures, and views

How does SQL work? A database is like a warehouse, data tables are like filing cabinets and data is the files. The warehouse aka database stores data and we access the files through a translator that knows how to speak to the database and speak SQL.

SQL only speaks to relational databases which is a database that has a tabular schema consisting of data tables with rows and columns. SQL is not the database, it's a language that allows you to write database queries with the following structure, assuming you have a Products table:

`SELECT id FROM products`

You can retrive and insert data, and update and create new tables or join new tables. A table is like a data bin or storage container. For example a Products table, there is an exact schema of strict requirements of how data is stored and which data can go into a table. The schema is defined by fields. So, the Products table could have the fields of id, name and price. Every new record we add aka every new row in the table, is a record that has values for these fields. Each record will have the same fields and all records have to follow the schema. Fields represent columns and records represent rows in the table. When we add data to the table we need to normalize the data and ensure the data is in a format that fits into the table. Typically you'll have mulitple tables that are related. Perhaps you have a Users table and Orders table too. The Orders table could be a combination of Users and Products. The Orders table would have the product_ id and user_id and therefore we can connect a specific user with a specific product which is known as a many-to-many relationship. You can also have one-to-one and one-to-many relationships too. Strong schemas and relational nature of the data are a must. Even when we store data amoung several different tables, we can connect them through relations and SQL can query these relations. 
