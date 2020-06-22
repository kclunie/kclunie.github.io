---
layout: post
title:      "Component Lifecycle"
date:       2020-06-22 22:21:57 +0000
permalink:  component_lifecycle
---


React Components exist in lifecycles which are series of methods that are invoked in different stages of the component’s life. A React Component has four stages of its life including initialization, mounting, updating and unmounting. According to the interactions made with the application, the component will run. So what does all this mean.

**Initialization:** Initialization is the stage where the component is constructed with the given props and default state, and is handled in the constructor of a Component Class.

**Mounting:** Mounting is the stage of rendering the JSX returned by the render method. When the initialization of the component is completed, the component is mounted on the DOM and rendered in the view. The function `componentWillMount()` is invoked right before the `render()` function is invoked and the component is mounted on the DOM. `The componentDidMount()` function is invoked right after the `render()` function is executed and the component is mounted on the DOM.

**Updating:** Updating is the stage when the state of a component is updated and the application is repainted on the DOM. Updating occurs when an event is triggered on the webpage by a click, for example, and the state and props of a component are updated. The `componentWillRecieveProps()` function is invoked before a mounted component gets its props reassigned and is independent of state. The `setState()` function is used to update the state of a component and can be invoked at any instant. The `shouldComponentUpdate()` function is invoked before rendering an already mounted component when new props or state are being received. Every state or props update re-renders the webpage automatically, but sometimes you may not want the page re-rendered. The `shouldComponentUpdate()` function lets React know whether the component’s output will be affected by the update or not. The function takes the new props and state as arguments and returns true or false to re-render. If returned false, rendering will not take place. The `componentWillUpdate()` function is invoked once before the `render()` function is executed and the `componentDidUpdate()` function is invoked after the `render()` function is executed and state and props are updated.

**Unmounting:** Unmounting is stage where the component is removed from the page. In this final phase of the component lifeycle, the component is removed from the DOM. The function `componentWillUnmount()` is invoked before the component is finally removed from the view and ends of the lifecycle.

```
import React from 'react'; 
import ReactDOM from 'react-dom'; 

class User extends React.Component { 
	constructor(props) 
	{ 
		super(props); 
		this.state = { name : "Bob" }; 
	} 

	componentWillMount() 
	{ 
		console.log("componentWillMount()"); 
	} 

	componentDidMount() 
	{ 
		console.log("componentDidMount()"); 
	} 

	changeState() 
	{ 
		this.setState({ name : "Bill" }); 
	} 

	render() 
	{ 
		return ( 
			<div> 
			<h1>Hello { this.state.name }</h1> 
			<h2> 
			<a onClick={this.changeState.bind(this)}>Click me</a> 
			</h2> 
			</div>); 
	} 

	shouldComponentUpdate(nextProps, nextState) 
	{ 
		console.log("shouldComponentUpdate()"); 
		return true; 
	} 

	componentWillUpdate() 
	{ 
		console.log("componentWillUpdate()"); 
	} 

	componentDidUpdate() 
	{ 
		console.log("componentDidUpdate()"); 
	} 
} 

ReactDOM.render( 
	<User />, 
	document.getElementById('root')); 

```










