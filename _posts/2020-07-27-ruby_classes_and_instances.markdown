---
layout: post
title:      "Ruby Classes and Instances"
date:       2020-07-28 01:04:52 +0000
permalink:  ruby_classes_and_instances
---


When we want to build objects in Ruby we need 2 ingredients: classes and instances. We need to make classes and create instances of those classes. A class is like the instructions on how to build an object and an instance refers to the individual object created from the class. 

A Ruby class has the "recipe" for creating new objects and the ability to create those objects by calling .new on a class. Think of using a cookie cutter to get a brand new cookie that looks exactly like the other cookies, but is a separate cookie. The cookie cutters says this is what the cookie should look like and it creates it over and over.

Let's say we have a cookie app that has tasty cookies up for order. We want to be able to store information about each type of cookie and operate on the information about a particular cookie. Once we have instructions on how to make a cookie, we're obviously going to want more. We need to be able to store information regarding each cookie that is added over and over to the application.

Let's create a cookie class that produces individual cookie objects, each of which contains all the information and attributes of an individual cookie.

```
class Cookie
  # body of the cookie class
end
```

The Cookie class is defined with the class keyword, the class name and an end. We can add information about the class in the body and class names start with a capital letter since they are stored in constants. 

Now, let's bake some cookies:

```
class Cookie
end
 
chocolatechip = Cookie.new
chocolatechip #=> #<Cookie:0zy123a45b6c7d80>

snickerdoodle = Cookie.new
snickerdoole #=> #<Cookie:0zy123a45b6c7d81>
```

We have a Cookie class and we're making cookies by creating a variable such as chocolatechip and setting it equal to a new cookie object. When we call the .new method, that instantiates a new cookie and who wouldn't want more cookies in the world? These newly birthed cookies are also known as instances. An instance is the creation of a single object. Snickerdoodle and chocolatechip are 2 different variables and 2 separate instances of the Cookie class.

When you make an instance of a class, Ruby gives you a return value of with some numbers and letters like this <Cookie:0zy123a45b6c7d80>. This syntax is called Ruby Object Notation and tells you that the object is an instance of Cookie. The number/letter mish-mash is called the object identifier and is the object's address in the computer. Each instance is baked from the same Cookie class, but is unique. So, if we compare snickerdoodle to chocolatechip we get:

``` 
snickerdoodle == chocolatechip #=> false
```

Classes allow us to create the recipe for our cookies and make the instances that are the individual cookies that we gobble up!



