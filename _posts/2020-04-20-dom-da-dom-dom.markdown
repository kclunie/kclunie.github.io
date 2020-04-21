---
layout: post
title:      "DOM-da-DOM-DOM"
date:       2020-04-21 01:26:36 +0000
permalink:  dom-da-dom-dom
---


The DOM can be daunting and somewhat scary, but not if you know what it is. So what is this real DOM and virtual DOM all about? The DOM aka the “Document Object Model” represents the user interface of an application. Every time there is a change in the state of an application's user interface, the DOM gets updated to represent the change. Since the user interface generally changes a lot this slows things down, affecting performance.

Changes to the DOM happen fast, but following the change the corresponding elements and children have to be re-rendered to update the application's user interface. This re-painting of the DOM is what slows us down. Every time the DOM needs to update, components need to be re-rendered which could be taxing if you have several components. 

This is where the virtual DOM comes into play. The virtual DOM is a virtual representation of the DOM. Every time there are changes to the state of an application, the virtual DOM gets updated instead of the real DOM making performance much faster and efficient than the real DOM.

The trick is in the comparision. Whenever the user interface changes, a virtual DOM is created and then compared with the previous virtual DOM version to see what the difference is. Then, the virtual DOM calculates the most efficient method to make these changes to the real DOM in order to reduce performance costs of updating the real DOM. Now you see it, now you don't... but hopefully you do.



