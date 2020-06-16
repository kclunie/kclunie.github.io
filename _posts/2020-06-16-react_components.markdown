---
layout: post
title:      "React Components"
date:       2020-06-16 10:12:21 -0400
permalink:  react_components
---


Components are like JavaScript functions. They accept inputs aka “props” and return React elements which define what you see on your screen. Components are independent, reusable and return HTML with the render function. Components can be Class components or Function components.

Class Component

The React component's name must be capitalized and include the extends React.Component statement. This creates an inheritance to React.Component, and gives your component access to React.Component's functions. The component also requires a render() method that returns HTML. Below is a component called Person that returns an h2 element.

```
class Person extends React.Component {
  render() {
    return <h2>My name is Betty</h2>;
  }
}
```

We can use and display the Person component in the "root" element by using:

```
ReactDOM.render(<Person />, document.getElementById('root'));
```

Function Component

Similarly, we can write the Person component as a Function component. The set up is sightly different, but will still return HTML.

```
function Person() {
  return <h2>Hi my name is Betty</h2>;
}
```

Component Constructor

Sometimes we want our components to have properties. Component properties are kept in a state object. The constructor() function is called when a component gets initialized and therefore the component's properties as well get initialized. The constructor function can also inheritant a parent component by including super() in your code. This executes the parent component's constructor function which gives your component access to all the functions of the parent component.

```
class Person extends React.Component {
  constructor() {
    super();
    this.state = {name: "Betty"};
  }
  render() {
    return <h2>Hi my name is {this.state.name}.</h2>;
  }
}
```

We can also call components inside other components:

```
class Person extends React.Component {
  render() {
    return <h2>Hi my name is Betty</h2>;
  }
}

class Family extends React.Component {
  render() {
    return (
      <div>
      <h1>Meet my family:</h1>
      <Person />
      </div>
    );
  }
}

ReactDOM.render(<Family />, document.getElementById('root'));
```
 
If your component is in a separate file, you must import React and export default Component.

```
import React from 'react';
import ReactDOM from 'react-dom';

class Person extends React.Component {
  render() {
    return <h2>Hi my name is Betty</h2>;
   
}
}

export default Person;
```


