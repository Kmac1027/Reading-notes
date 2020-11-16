# Reading 26: Component Based UI

### Name 5 Javascript UI Frameworks (other than React)

1. angular
1. vue
1. JQuery
1. Backbone.js
1. node.js

### What’s the difference between a framework and a library?

- a framework is an environment that runs your code and you usually have to follow the rules of that environment whereas a library is a tool that you add to your code to create more functionality.

## react hello world

[Link to article](https://reactjs.org/docs/hello-world.html)

- React embraces the fact that rendering logic is inherently coupled with other UI logic: how events are handled, how the state changes over time, and how the data is prepared for display.
- React elements are immutable. Once you create an element, you can’t change its children or attributes. An element is like a single frame in a movie: it represents the UI at a certain point in time.
- With our knowledge so far, the only way to update the UI is to create a new element, and pass it to ReactDOM.render().
- Components let you split the UI into independent, reusable pieces, and think about each piece in isolation. This page provides an introduction to the idea of components
- This function is a valid React component because it accepts a single “props” (which stands for properties) object argument with data and returns a React element. We call such components “function components” because they are literally JavaScript functions.
- Always start component names with a capital letter. React treats components starting with lowercase letters as DOM tags. For example, < div / > represents an HTML div tag, but < Welcome / > represents a component and requires Welcome to be in scope.
- This page introduces the concept of state and lifecycle in a React component.
- Handling events with React elements is very similar to handling events on DOM elements. There are some syntax differences:
  1. React events are named using camelCase, rather than lowercase.
  1. With JSX you pass a function as the event handler, rather than a string.
- In React, you can create distinct components that encapsulate behavior you need. Then, you can render only some of them, depending on the state of your application.
- HTML form elements work a little bit differently from other DOM elements in React, because form elements naturally keep some internal state. For example, this form in plain HTML accepts a single name
- Often, several components need to reflect the same changing data. We recommend lifting the shared state up to their closest common ancesto
- React has a powerful composition model, and we recommend using composition instead of inheritance to reuse code between components.

## introducing JSX

[Same Link as above](https://reactjs.org/docs/introducing-jsx.html)

## rendering elements

[Same Link as above](https://reactjs.org/docs/introducing-jsx.html)

[Back to code 401 notes](../401-Javascript.md)