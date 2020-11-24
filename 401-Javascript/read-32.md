# Reading 32- Custom Hooks

## Authoring

### custom hooks - all you need to know

[Link to Article](https://www.telerik.com/kendo-react-ui/react-hooks-guide/#toc-custom-react-hooks)

- React hook APIs provide an alternative to writing class-based components, and offer an alternative approach to state management and lifecycle methods. Hooks bring to functional components the things we once were only able to do with classes, like being able to work with React local state, effects and context through useState, useEffect and useContext.
- Additional Hooks include: useReducer, useCallback, useMemo, useRef, useImperativeHandle, useLayoutEffect and useDebugValue. You can read about these APIs in the React Hooks API Reference!
- The easiest way to describe Hooks is to show side-by-side examples of a class component that needs to have access to state and lifecycle methods, and another example where we achieve the same thing with a functional component.
- Five Important Rules for Hooks
  1. Never call Hooks from inside a loop, condition or nested function
  1. Hooks should sit at the top-level of your component
  1. Only call Hooks from React functional components
  1. Never call a Hook from a regular function
  1. Hooks can call other Hooks

### async hooks

[Link to Article](https://dev.to/vinodchauhan7/react-hooks-with-async-await-1n9g)

### useReducer Hook

[Link to Article](https://reactjs.org/docs/hooks-reference.html#usereducer)

- The following Hooks are either variants of the basic ones from the previous section, or only needed for specific edge cases

1. useReducer
1. useCallback
1. useMemo
1. useRef
1. useImperativeHandle
1. useLayoutEffect
1. useDebugValue

### react custom hooks

[Link to Article](https://reactjs.org/docs/hooks-custom.html)

- Building your own Hooks lets you extract component logic into reusable functions.
- When we want to share logic between two JavaScript functions, we extract it to a third function.
- A custom Hook is a JavaScript function whose name starts with ”use” and that may call other Hooks. For example, useFriendStatus below is our first custom Hook:

```js
import { useState, useEffect } from 'react';

function useFriendStatus(friendID) {
  const [isOnline, setIsOnline] = useState(null);

  useEffect(() => {
    function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }

    ChatAPI.subscribeToFriendStatus(friendID, handleStatusChange);
    return () => {
      ChatAPI.unsubscribeFromFriendStatus(friendID, handleStatusChange);
    };
  });

  return isOnline;
}
```

- Unlike a React component, a custom Hook doesn’t need to have a specific signature. We can decide what it takes as arguments, and what, if anything, it should return. In other words, it’s just like a normal function. Its name should always start with use so that you can tell at a glance that the rules of Hooks apply to it.
- Custom Hooks are a convention that naturally follows from the design of Hooks, rather than a React feature.
- Custom Hooks offer the flexibility of sharing logic that wasn’t possible in React components before. You can write custom Hooks that cover a wide range of use cases like form handling, animation, declarative subscriptions, timers, and probably many more we haven’t considered. What’s more, you can build Hooks that are just as easy to use as React’s built-in features.
- Try to resist adding abstraction too early.

## Hooks Lists/Collections

### use hooks

[Link to Article](https://usehooks.com/)

### hooks list

[link to github awesome-react-hooks](https://github.com/rehooks/awesome-react-hooks)

### 10 essential react hooks

[Linik to article](https://blog.bitsrc.io/10-react-custom-hooks-you-should-have-in-your-toolbox-aa27d3f5564d)]

1. useArray hook - Array manipulation is what a dev goes through every weekday. Adding elements to an array or removing an element at a given index is a daily routine for us. useArray reduces this burden by providing us with various array manipulation methods. This hook is a part of the react-hanger package.

```js
//Installation:- yarn add react-hanger
import {useArray} from 'react-hanger'
```

2. react-use-form-state hook - Forms are everywhere, even in the smallest of applications we have to encounter forms and manage their state. Managing form state in React can be a bit unwieldy sometimes.
react-use-form-state is a small React Hook that attempts to simplify managing form state, using the native form input elements you are familiar with.

```js
//Installation:- npm i react-use-form-state

```

3. react-fetch-hook - Making ajax calls is like the most basic and most performed task for a frontend developer. And the React community is quick enough to create a hook for this purpose too.

```js
//Installation:- npm i react-fetch-hook

```

4. useMedia hook - useMedia is a React sensor hook that tracks the state of a CSS media query. We all know the importance of the media queries and how much important is responsiveness for any site.

5. react-useportal hook - React Portals provide a first-class way to render children into a DOM node that exists outside the DOM hierarchy of the parent component. And this hook helps us do that.

```js
//Installation:- yarn add react-useportal

```

6. react-firebase-hooks - We all appreciate the greatness of firebase and use it a lot in our projects, whether its for authentication or storage. And this hook is the one we really need.

```js
//Installation:- npm i react-firebase-hooks

```

7. use-onClickOutside hook - An outside click is a way to know if the user clicks everything but a specific component. You may have seen this behavior when opening a dropdown menu or a modal or a dropdown list.

8. useIntersectionObserver hook - A React hook for using intersection observers.
The Intersection Observer API provides a way to asynchronously observe changes in the intersection of a target element with an ancestor element or with a top-level document’s viewport.

```js
//Installation:- npm i react-use-intersection-observer

```

9. use-location hook - The name says it all, this hook is used for getting the location of the browser.

10. use-redux hook - This one is for my redux readers. This hook returns the store and dispatch property.

```js
//Installation:- yarn add use-redux

```

[Back to code 401 notes](../401-Javascript.md)