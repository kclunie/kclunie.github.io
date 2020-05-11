---
layout: post
title:      "Query on jQuery"
date:       2020-05-11 20:29:59 +0000
permalink:  query_on_jquery
---


jQuery is a reusable JavaScript library that simplifies JavaScript code. JavaScript is a language and jQuery is a library, so jQuery doesn't replace JavaScript, but it is derived from JavaScript. Keep in mind, a library is a colletion of tools that allow you to implement functionality without the need to write all the code that is needed to do it. We can use jQuery to manipulate content on a webpage. It makes things like HTML document traversal and manipulation much simpler with an easy-to-use API that works across many browsers. jQuery takes a lot of common tasks that require many lines of JavaScript code to accomplish, and wraps them into methods that you can call with a single line of code.

You can download jQuery here: www.jquery.com/download 

jQuery syntax starts with a $, then you select your element, and then you create a command. We can use jQuery to add text to an element:

HTML

`<h1>Hello Earth<h1/>`

JS

Using jQuery:

`$("h1").text("Hello World")`

Using plain JavaScript:

`document.querySelector("h1").textContent = "Hello World"`

jQuery can be used for more complex cases as well and offers methods such as `.each` and `.appendTo` to add data to individual elements:

HTML

`<div id="saluations"></div>`

JS

```
let data = ["hi", "hello", "greetings"]

$.each(data, function(index, element) {
    $("<div>" + element + "</div>").appendTo($("#salutation"))
})
```

The jQuery library contains many features including HTML/DOM manipulation, CSS manipulation, HTML event methods, effects and animations, AJAX, and utilities.
