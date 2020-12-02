# Readings 38: Redux - Asynchronous Acti

## dan abramov on suspense

[Link to Video - Video was unavailable](https://www.youtube.com/watch?v=6g3g0Q_XVb4)

## async actions

[Link to Article](https://redux.js.org/tutorials/fundamentals/part-6-async-logic)

- By itself, a Redux store doesn't know anything about async logic. It only knows how to synchronously dispatch actions, update the state by calling the root reducer function, and notify the UI that something has changed. Any asynchronicity has to happen outside the store.
- Earlier, we said that Redux reducers must never contain "side effects". A "side effect" is any change to state or behavior that can be seen outside of returning a value from a function. Some common kinds of side effects are things like:
  1. Logging a value to the console
  1. Saving a file
  1. Setting an async timer
  1. Making an AJAX HTTP request
  1. Modifying some state that exists outside of a function, or mutating arguments to a function
  1. Generating random numbers or unique random IDs (such as Math.random() or Date.now())
- a Redux middleware can do anything when it sees a dispatched action: log something, modify the action, delay the action, make an async call, and more. Also, since middleware form a pipeline around the real store.dispatch function, this also means that we could actually pass something that isn't a plain action object to dispatch, as long as a middleware intercepts that value and doesn't let it reach the reducers.
- Both of the middleware in that last section were very specific and only do one thing. It would be nice if we had a way to write any async logic ahead of time, separate from the middleware itself, and still have access to dispatch and getState so that we can interact with the store.
- Just like with a normal action, we first need to handle a user event in the application, such as a click on a button. Then, we call dispatch(), and pass in something, whether it be a plain action object, a function, or some other value that a middleware can look for.
- Once that dispatched value reaches a middleware, it can make an async call, and then dispatch a real action object when the async call completes.
- Earlier, we saw a diagram that represents the normal synchronous Redux data flow. When we add async logic to a Redux app, we add an extra step where middleware can run logic like AJAX requests, then dispatch actions. That makes the async data flow look like this:

![](https://redux.js.org/assets/images/ReduxAsyncDataFlowDiagram-d97ff38a0f4da0f327163170ccc13e80.gif)

- As it turns out, Redux already has an official version of that "async function middleware", called the Redux "Thunk" middleware. The thunk middleware allows us to write functions that get dispatch and getState as arguments. The thunk functions can have any async logic we want inside, and that logic can dispatch actions and read the store state as needed.
- Redux middleware were designed to enable writing logic that has side effects
  - "Side effects" are code that changes state/behavior outside a function, like AJAX calls, modifying function arguments, or generating random values
- Middleware add an extra step to the standard Redux data flow
  - Middleware can intercept other values passed to dispatch
  - Middleware have access to dispatch and getState, so they can dispatch more actions as part of async logic
- The Redux "Thunk" middleware lets us pass functions to dispatch
  - "Thunk" functions let us write async logic ahead of time, without knowing what Redux store is being used
  - A Redux thunk function receives dispatch and getState as arguments, and can dispatch actions like "this data was received from an API response"

## thunk middleware

[Link to Github redux-thunk](https://github.com/reduxjs/redux-thunk)

## redux thunk

[Link to Article](https://www.digitalocean.com/community/tutorials/redux-redux-thunk)

- Thunk is a programming concept where a function is used to delay the evaluation/calculation of an operation.
- Redux Thunk is a middleware that lets you call action creators that return a function instead of an action object. That function receives the store’s dispatch method, which is then used to dispatch regular synchronous actions inside the function’s body once the asynchronous operations have been completed.
- to install

```js
npm install redux-thunk@2.3.0
```

- it is applied as such

```js
import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux';
import { createStore, applyMiddleware } from 'redux';
//vvvvvvvvvvvvvvv
import thunk from 'redux-thunk';
//^^^^^^^^^^^^^^^
import './index.css';
import rootReducer from './reducers';
import App from './App';
import * as serviceWorker from './serviceWorker';

// use applyMiddleware to add the thunk middleware to the store
const store = createStore(rootReducer, applyMiddleware(thunk));

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
);
```

- The most common use case for Redux Thunk is for communicating asynchronously with an external API to retrieve or save data. Redux Thunk makes it easy to dispatch actions that follow the lifecycle of a request to an external API.
- Creating a new todo item normally involves first dispatching an action to indicate that a todo item creation as started. Then, if the todo item is successfully created and returned by the external server, dispatching another action with the new todo item. In the case where there’s an error and the todo fails to be saved on the server, an action with the error can be dispatched instead.
- Inside the function’s body, you first dispatch an immediate synchronous action to the store to indicate that you’ve started saving the todo with the external API. Then you make the actual POST request to the server using Axios. On a successful response from the server, you dispatch a synchronous success action with the data received from the response, but on a failure response, we dispatch a different synchronous action with the error message.


[Back to code 401 notes](../401-Javascript.md)