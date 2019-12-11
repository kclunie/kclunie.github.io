---
layout: post
title:      "Let's Get Thunky"
date:       2019-12-11 23:17:01 +0000
permalink:  lets_get_thunky
---



Web requests in JavaScript are **asynchronous** which means if we make a fetch() request on the first line of our code, the code on the second line will start running before the web request resolves and we have a response to work with. When we retrieve data from APIs, we run into this problem where the action creator returns an action before the data is retrieved. 

In order to resolve this, we use a middleware called **Thunk**. Thunk allows us to return a function inside of our action creator instead of a plain JavaScript object. That returned function receives the store's dispatch function, and with that we are able to dispatch multiple actions such as updating our store with the returned data. Thunk allows us to slightly alter the behavior of our actions including adding in asynchronous requests. 

**Here are the steps to use Redux Thunk:**

1. Install the NPM package:

          npm install --save redux-thunk

2. Incorporate middleware when you initialize the store in your index.js file.

3. Import the function, applyMiddleware(), from react-redux, along with thunk from the redux-thunk package and pass in applyMiddleware(thunk) as a second argument to createStore:



```
import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux';
import { createStore, applyMiddleware } from 'redux';
import thunk from 'redux-thunk';
import rootReducer from './reducers';
 
const store = createStore(rootReducer, applyMiddleware(thunk));
 
ReactDOM.render(
  <Provider store={store} >
    <App />
  </Provider>, document.getElementById('container')
)
```


The above code is telling the store to use Thunk middleware which allows us to return a function inside of our action creator when normally our action creator returns a plain JavaScript object. Also, the function inside of Thunk receives the store's dispatch function as its argument. This allows us to dispatch multiple actions from inside the returned function, for example:

```
export function fetchRestaurants() {
  return (dispatch) => {
    dispatch({ type: 'START_ADDING_RESTAURANTS_REQUEST' });
    fetch('http://api.myrestaurants.org.json')
      .then(response => response.json())
      .then(restaurants => dispatch({ type: 'ADD_RESTAURANTS', restaurants }));
  };
}
```

Here we first dispatch an action to state that we are about to make a request to our API. Then we make the request. We do not hit our then() function until the response is received, which means that we are not dispatching our action of type 'ADD_RESTAURANTS' until we receive our data. Now, we are able to send along that data and update our store with the returned data!

With **Thunk**, we can incorporate asynchronous code in with our Redux actions. *Thunk about it*.

