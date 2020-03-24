---
layout: post
title:      "Object Oriented Programming Pillars"
date:       2020-03-24 01:23:16 +0000
permalink:  object_oriented_programming_pillars
---


What exactly are the 4 core concepts in object oriented programming?

Encapsulation, Abstraction, Inheritance, and Polymorphism.... also known as the 4 pillars of object oriented programming.

In object oriented programming we combine a group of related variables and functions into a unit which is called an object. Varaibles are refered to as properties and functions as methods. This grouping of related variables and functions into objects is called **encapsulation**. This allow us to reduce complexity and reuse objects in different programs. For example, browsers have local storage objects that have properties such as `length` and methods such as `setItem`.

**Abstraction** refers to hiding properties and methods from the outside to make the interface simpler. This helps us reduce the impact of change. Changes going on inside private methods won't present themselves to the outside and therefore complexity is reduced. In others words, you could delete a private method and it won't change the rest of the application's code. For example, a cell phone has a lot going on in the inside, but you only have to use the buttons to make it work. The interface is simpler for users and the impact of changes can be isolated.

**Inheritance** allows us to elimnate redundant code. For example, HTML elements have similar methods such as `click()` and `focus()`. Instead of redefining these properties for all elements, we can define one generic object and have other objects inherant these methods or properties, eliminating redundant code.

**Polymorhpism** means many forms. Object oriented polymorphism is a technique used to get rid of long if/else and switch/case statements. If objects have the ability to render on a page, the way each element is rendered could be different. We can implement a render method in each object and the render method will behave differently depending on the object you're referencing.

