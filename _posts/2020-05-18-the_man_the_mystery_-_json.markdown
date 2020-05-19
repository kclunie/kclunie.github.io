---
layout: post
title:      "The Man, The Mystery - JSON"
date:       2020-05-19 00:57:47 +0000
permalink:  the_man_the_mystery_-_json
---


Who is this JSON everyone seems to know about? Behind those 4 letters stands JavaScript Object Notation. JSON is a way of structuring data, it is a data representation format just like XML. It is used primarily to transmit data between a server and web application. It's used widely across the internet for almost any APIs you'd access as well as for config files. It's lightweight to send back and forth data across the internet through different APIs due to its small file size. This makes things move faster and users much happier. It's easy to read and it integrates nicely with JavaScript since it's a superset of JavaScript. So, anything you write in JSON is valid JavaScript and JavaScript is used all throughout the web for the backend and frontends of applications. JSON can be used with most programming languages, it is language independent. You will find libraries to support it and parse JSON strings into objects or classes in that particular language. Easy to get along with.

To create a JSON file you'd use the extension .json such as user.json

The two primary parts that make up JSON are keys and values. Together they make a key/value pair. A key value pair follows a specific syntax, with the key followed by a colon followed by the value. Key/value pairs are comma separated.

```
{
"firstname": "John",
"lastname": "Smith",
"age": 30,
"address": 
     { "city": "New York"
     "state": "New York" },
"phone":
     [{"type": "cell", "number": "202-123-1234"}, 
		 {"type": "home", "number": "202-703-1234'}]
}
```

A JSON instance contains a single JSON value. A JSON value can be an array, object, number, string, true, false or null. The JSON key is always in a string format though, always well dressed. 

JSON has all sorts of tricks up its sleeves; its data is easy to work with inside of programming languages, it's used to create or consme APIs and it's used to create config files to use for applications.
