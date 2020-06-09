---
layout: post
title:      "Recycle Reuse Redux"
date:       2020-06-09 22:25:12 +0000
permalink:  recycle_reuse_redux
---


Redux is an open-source JavaScript library that manages application state. It's used with libraries such as React or Angular for building user interfaces. Redux is predictable, centralized, debuggable, and flexible which means:

* Redux helps you write applications that are consistent, run in different environments, and test easily.
* Centralizing your application's state and logic allows great capabilities such as state persistence.
* The Redux DevTools add simplicity to tracing your application's state changes. 
* Redux works with any user interface.

React Redux is the official React binding for Redux. It allows your React components to read data from a Redux store, and dispatch actions to the store to update data.

Installation is easy. To use React Redux with your React app:

`npm install react-redux`

You'll also need to install Redux and set up a Redux store in your app. To install Redux use:

`npm install redux`

To create your store we will use:

```
import React from 'react'
import { render } from 'react-dom'
import { Provider } from 'react-redux'
import { createStore } from 'redux'
import rootReducer from './reducers'
import App from './components/App'

const store = createStore(rootReducer)

render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
)
```

We are passing our reducers to the Redux createStore function, which returns a store object. Next, we pass this object to the react-redux Provider component, which is rendered at the top of our component tree.

React Redux gives us Provider, which makes the Redux store available to the rest of your app:

React Redux also gives us a connect function for you to connect your component to the store as well.

```
import { connect } from 'react-redux'
import { increment, decrement, reset } from './actionCreators'

const mapStateToProps = (state /*, ownProps*/) => {
  return {
    counter: state.counter
  }
}

const mapDispatchToProps = { increment, decrement, reset }

export default connect(
  mapStateToProps,
  mapDispatchToProps
)(Counter)
```
