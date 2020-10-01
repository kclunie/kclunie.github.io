---
layout: post
title:      "Function vs Class Components"
date:       2020-09-30 22:26:22 -0400
permalink:  function_vs_class_components
---


In react we have two types of components: functions and classes. Let's take a deeper look at what this means.

Functional components are just like JavaScript functions, and can be created with arrow functions or the function keyword. They are considered stateless components. The do not maintain their own state, they only take in data that is passed to it and displays the data that is rendered in the UI. Functional components do not use React lifecycle methods nor do they use the render() method. Functional components can accept and use props and are best to use if you do not need to maintain a state. You can access props by calling props.

Here we have a ToDoCardContainer that receives props and maps over those props to eventually display them in ToDoCard.

```
import React from 'react'
import ToDoCard from '../components/ToDoCard'

function ToDoCardContainer(props){

  function renderCards(){
    return props.cards.map(card => {
      return <ToDoCard key={card.id} handleClickList={props.handleClickList} addList={props.addList} card={card}/>
    })
  }

  return (
    <div>
      {renderCards()}
    </div>
  )
}

export default ToDoCardContainer;
```

On the other hand, class components make use of ES6 class and extend the Component class in React. Class components hold state and implement logic. React lifecycle methods, such as componentDidMount, can be used inside class components. Class components can have props passed to them as well, but you will notice that you access them using this.props instead of just props as in functional components.

Here we have ToDoCard that has a form to enter data and state to hold that data. We can also notice props being called with this.props and the use of the render() method.

```
import React from 'react'
import ToDoList from './ToDoList'

class ToDoCard extends React.Component {

  state = {
    input: ''
  }

  handleListInput = (event) => {
    this.setState({
      input: event.target.value
    })
    console.log(this.state.input)
  }

  handleListSubmit = (event) => {
    event.preventDefault()
    this.props.addList(this.props.card.id, this.state.input)
    this.setState({
      input: ''
    })
  }

  renderLists(){
    return this.props.card.lists.map(list => {
      return <ToDoList key={list.id} handleClickList={this.props.handleClickList} cardId={this.props.card.id} list={list}/>
    })
  }

  render(){
    return (
      <div className="to-do-card">
        <h4>{this.props.card.title}</h4>
        <form onSubmit={this.handleListSubmit}>
          <input onChange={this.handleListInput} type="text" value ={this.state.input} />
        </form>
        {this.renderLists()}
      </div>
    )
  }
}


export default ToDoCard
```


