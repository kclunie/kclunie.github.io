---
layout: post
title:      "The Mode for Node.js"
date:       2021-01-05 01:21:25 +0000
permalink:  the_mode_for_node_js
---


Let's get the down-low on Node.js. 

**What is it?**

Node.js is an open-source, cross-platform, back-end, JavaScript runtime environment that executes JavaScript code outside a web browser.

**The Background**

JavaScript achieves dynamic functionality and builds interactivity in the browser, and we need something that executes the language. The JavaScript engine executes the language and brings it to life. The JavaScript engine was built into the browser, so when the browser encounters a JavaScript file, it passes it to the JavaScript engine to execute it. You cannot have a runtime that runs in isolation, you need context. It needs to run in the browsers context and work on the page that is rendered. That context is the DOM, which is a bunch of objects that represent the page. The JavaScript engine receives access to the DOM and can manipiulate code. Using Node.js changes our context. Instead of being restricted to the DOM context, Node.js allows us to access files outside of the browser.

**What is Node.js used for?**

It's used for creating server-side web applications.

**Why use Node.js?**

It's fast with code execution because it's built on Google Chrome's V8 JavaScript engine.

Node Package Manager has over 50,000 bundles available for developers to use so it's easy to import different functionality into your application.

It's great for real-time web applications since all APIs of Node.js libaries are asynchronous and non-blocking, so a Node.js based server never waits for an API to return data.

It's easy for new web developers to learn since it's a JavaScript based library.

