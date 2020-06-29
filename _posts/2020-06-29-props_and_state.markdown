---
layout: post
title:      "Props and State"
date:       2020-06-29 18:24:21 +0000
permalink:  props_and_state
---


React is a front-end JavaScript library that makes user interface creation simple. Being component-based, React relies on props and state to pass and update data accordingly.

**Props**

Props is short for properties and come in hand when you need to make data available to another component. Input data is passed from one component to another and then accessed by the render() method using this.props. Components call the render() method and it returns what to display. React’s data flow between components is uni-directional from parent to child only. Below we see "name" as the passed prop. Data from props is read-only and therefore cannot be modified by the receiving component.

```
class User extends React.Component {
  render() {
    return (
      <div>
        Hello {this.props.name}
      </div>
    );
  }
}

ReactDOM.render(
  <User name="Frank" />,
  document.getElementById('user-name')
);
```

**State**

On the other hand, a component's internal data can be maintained and created by state and accessed using this.state. When a component’s state data changes, the rendered markup will be updated by calling render(). State data is contained and managed internally, and does not get passed to other components nor can it be accessed by outside components. State can also be updated using the setState( ) method. When the setState( ) method gets called and state is changed, re-rendering of the component with the updated state, instead of the whole DOM, takes place making React very efficient.

```
class StopWatch extends React.Component {
  constructor(props) {
    super(props);
    this.state = { seconds: 0 };
  }

  clock() {
    this.setState(state => ({
      seconds: state.seconds + 1
    }));
  }

  componentDidMount() {
    this.interval = setInterval(() => this.clock(), 1000);
  }

  componentWillUnmount() {
    clearInterval(this.interval);
  }

  render() {
    return (
      <div>
        Seconds: {this.state.seconds}
      </div>
    );
  }
}

ReactDOM.render(
  <StopWatch />,
  document.getElementById('stopwatch')
);
```


