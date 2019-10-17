---
layout: post
title:      "JavaScripting"
date:       2019-10-09 23:27:34 -0400
permalink:  javascripting
---


For my Rails with a JavaScript front end app I built an event app where users can sign-up and log-in to create events and RSVP to attend events. Users can also add guests to their RSVP. Users are able to create any kind of event indicating date, time, location and details. 

The concept that I enjoyed the most while building my JavaScript project was understanding event listening. JavaScript has the ability to listen for things that happen inside the browser. Events, such as a click, are something that happens in the browser and a callback function is the work that will happen in response to the event being triggered. A mouse click, key press and form submission are a few of the many event listeners that can trigger a callback function.

If you have a button like so:

```
<button id='events-data'>See All Upcoming Events</button>
```
 
 you can create a listening event like so:
 
 ` function listenForClick() {
	$('button#events-data').on('click', function (event) {
		alert('I was clicked!');
	})
}`

and an alert box will pop up when the button is clicked!

Another great aspect about JavaScript is that it is great for debugging. You can easily use console.log(data) and see what your data is or you can open your DevTools, click the Sources tab and click on code line numbers to add breakpoints to your code. Breakpoints let you pause your code in the middle of its execution and examine all values at that moment in time.

I found this project to be challenging but with the right resources I made my way through my code and it became much more simple. I enjoyed implementing my JavaScript code on my new form page, testing my code, and watching my app transform every step of the way. Adding JavaScript to my rails app gave me a new perspective on my app, solidfied my JavaScript knowledge and reinforced my coding skills overall.
