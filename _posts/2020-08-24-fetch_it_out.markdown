---
layout: post
title:      "Fetch it Out"
date:       2020-08-24 22:26:48 +0000
permalink:  fetch_it_out
---


When we use JavaScript to change the DOM and create events, we need to make sure our server is in on the fun.

The AJAX short for "asynchronous JavaScript and XML" technique is where it's at when making requests to the server without reloading the page. Our users see the webpage as HTML and CSS and can make changes to the page via JavaScript. A great tool to use to send that data to the server and bring it back is fetch(). The data that comes back from the server is in the JavaScript Object Notation (JSON) format. This communication with the server is vital for giving our users an engaging, responsive website.

So once we have data we need to show our users on our webpage, we can incorporate fetch(). The fetch() function retrieves the requested data. Let's take a look:

```
fetch("URL of data source")
.then(function(response) {
  return response.json();
})
.then(function(json){
  console.log(json)
})
```

Ok, so what's going on here:

1. We're calling fetch() that's taking in the URL data we would like. This function will return an object representing the requested data.
2. The then() method is then called on the returned object. then() takes in a function that received the response as its argument. Here we return our response after we've made any changes and make sure our response is in the JSON format.
3. Next, we have another then() method that has the JSON data provided. Now we can work with this data and manipulate the DOM. For example, we may use a console.log(json) to see our data in the console.


    


