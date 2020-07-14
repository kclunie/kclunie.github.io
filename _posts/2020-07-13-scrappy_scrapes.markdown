---
layout: post
title:      "Scrappy Scrapes"
date:       2020-07-14 01:49:49 +0000
permalink:  scrappy_scrapes
---


What comes to mind when you hear scraping? Pulling data hopefully. When we talk about scraping we are referring to parsing a web page's HTML and pulling, or "scraping" data from that HTML. In order to get the data we want, we need to closely examine the HTML and identify exactly which elements contain the information we need. 

We can't always find the data we need through APIs, therefore scraping comes in handy. For example, let's say you're creating an app that allows a user to subscribe to a non-mainstream, not so popular news feed. A site less popular may not have an API that makes their articles easily available to you, forcing you to scrape those sites for their latest news articles for your users to access.

So how do we do it? Nokogiri and Open-URI help get the job done. Open-URI is a module in Ruby that allows us to programmatically make HTTP requests. It gives us the open method. This method takes one argument, a URL, and will return to us the HTML content of that URL.

If we use the code below, it stores the Google HTML in a temporary file that we can then call read on to get the raw HTML.

`html = open('http://www.google.com')`

Nokogiri on the other hand, is a Ruby gem that allows us to parse HTML and collect data from it. It takes the string HTML and returns a collection of objects that we can grab specific data from using different methods.

We can install Nokogiri using:

`gem install nokogiri`

Now, we need to require Nokogiri and open-uri in our file:

```
require 'nokogiri'
require 'open-uri'
```
 
Next, we'll use the Nokogiri::HTML method to take the string of HTML returned by open-uri's open method and convert it into nested nodes that we can further work with.

`doc = Nokogiri::HTML(html)`

Next, we want to inspect our page and use CSS selectors to retrieve our desired data out of the HTML document. Let's say we want the following text in this h1:

`<h1 class="greetings">Hi, there!</h1>`

We can use `doc.css(".greetings").text` to grab the text content inside the element.

Nokogiri is super useful when we need data from a website. Using methods such as .css, we can zone in on the specific website elements we need and use additional methods like .text to grab the content we want.




