---
layout: post
title:      "Node Package Manager"
date:       2020-03-11 20:44:45 +0000
permalink:  node_package_manager
---


JavaScript continues to be a vital player in web development. Many developers writing in JavaScript, continually contributing duplicate code to solve the same problems. JavaScript packages solve this problem. A package is a file or set of files full of existing, reusable code. They are designed to be shared, allowing many web developers to use the same code in their own projects. To help organize these packages in relation to your own work, use npm aka Node Package Manager.

It’s important to be able to identify existing code that fulfills your projects needs. You shouldn’t be wasting your time writing code that may already exist. It is likely someone else has already tested and created the code you want. As a professional problem solver, finding existing, good, open source code is the best solution.

**Setting Up Node Package Manager**

You need to ensure your environment is all set to work with npm, which is automatically installed along with Node.js. To confirm you have node installed, enter the following into your command line:

```
node -v
```

If a version appears, you have Node.js. If, by chance, you do not have Node.js installed, you can use Node Version Manager to install Node.js and keep it up to date.

You can also double check npm by running the following:

```
npm -v
```

A version number should appear in your terminal. If you'd like, you can update npm by entering the following:

```
npm install --global npm
```

**NPM**

npm is a package manager for JavaScript. This means that npm works with your JavaScript project directories via the command line, allowing you to install packages of preexisting code. Some packages are small and some packages are much more complicated. Larger libraries and frameworks, such as React, are available as npm packages. These packages are often themselves built using a combination of other packages. This modular design, the ability to build a package using other packages, allows for developers to evolve the JavaScript universe, creating new, powerful code and applications on top of existing code.

**npm install and package.json**

Some applications may rely on npm packages for their tests. The applications themselves don't actually contain all of these packages' code. Instead, they contain a list of dependencies in a file called package.json. The package.json file tells you and npm everything about what packages are required for a specific JavaScript application, listing out each package name. When you run the command npm install in a directory where a package.json file is present, npm reads the names of each dependency from the package.json file and downloads the packages from npmjs.com, where they are hosted. It then begins installing those packages. Note, those packages may also have their own package.json with their own dependencies. npm must also get those packages and those packages dependencies as well. This is called a dependency tree.

When building a project from scratch, you may realize you need some specific package. You can install packages by running npm install <package_name> while inside a project directory. If you do not have a correctly structured package.json file, the install will not work.

The package.json file is a key part of sharing JS code repositories on sites like GitHub. Instead of having to include all the dependencies' code with every project, you just include a small file, listing out what npm needs to get for the project. The file also typically includes information about the project, such as the name, version, author and license. The package.json file is written in JSON, so like an object in JavaScript, it is always wrapped in curly braces, and includes keys and values.

**npm init**

Since npm relies on a package.json file, it has a built in command to build package.json files. Running npm init on the command line will begin a series of prompts, asking about specific content to include in the file. At the end, it will create a file or edit an existing package.json file which is useful when you are creating your own projects from scratch.

Keep in mind, npm is a command line tool for handling packages of reusable JavaScript code and Node is a JavaScript runtime, allowing JavaScript to be run locally on your computer, instead of in a browser. We rely on npm to set up a lot of things 'under the hood' in our applications including the contributions of endless coders. If available, open, and secure code already exists, it should be used!

