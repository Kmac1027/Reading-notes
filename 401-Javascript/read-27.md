# Reading 27: Props and State

## setState explained

[Link to article](https://css-tricks.com/understanding-react-setstate/)

- React components with state render UI based on that state. When the state of components changes, so does the component UI.
- That makes understanding when and how to change the state of your component important. At the end of this tutorial, you should know how setState works, and be able to avoid common pitfalls that many of us hit when when learning React.

[](https://i1.wp.com/css-tricks.com/wp-content/uploads/2018/04/image_preview-1.jpeg?w=645&ssl=1)

- This is basically kicking off a process that React calls reconciliation. The reconciliation process is the way React updates the DOM, by making changes to the component based on the change in state. When the request to setState() is triggered, React creates a new tree containing the reactive elements in the component (along with the updated state). This tree is used to figure out how the Search component’s UI should change in response to the state change by comparing it with the elements of the previous tree. React knows which changes to implement and will only update the parts of the DOM where necessary. This is why React is fast.

1. We have a search component that displays a search term
1. That search term is currently empty
1. The user submits a search term
1. That term is captured and stored by setState as a value
1. Reconciliation takes place and React notices the change in value
1. React instructs the search component to update the value and the search term is merged in

- When building React applications, there are times when you’ll want to calculate state based the component’s previous state. You cannot always trust this.state to hold the correct state immediately after calling setState(), as it is always equal to the state rendered on the screen.

1. Update to a component state should be done using setState()
1. You can pass an object or a function to setState()
1. Pass a function when you can to update state multiple times
1. Do not depend on this.state immediately after calling setState() and make use of the updater function instead.

## handling events

[Link to Article](https://reactjs.org/docs/handling-events.html)

- React events are named using camelCase, rather than lowercase.
- With JSX you pass a function as the event handler, rather than a string.
-  you cannot return false to prevent default behavior in React. You must call preventDefault explicitly.
- Inside a loop, it is common to want to pass an extra parameter to an event handler

## forms

[link to Article](https://reactjs.org/docs/forms.html)

- HTML form elements work a little bit differently from other DOM elements in React, because form elements naturally keep some internal state
- In HTML, form elements such as <input>, <textarea>, and <select> typically maintain their own state and update it based on user input. In React, mutable state is typically kept in the state property of components, and only updated with setState().
- We can combine the two by making the React state be the “single source of truth”. Then the React component that renders a form also controls what happens in that form on subsequent user input. An input form element whose value is controlled by React in this way is called a “controlled component”.
- Since the value attribute is set on our form element, the displayed value will always be this.state.value, making the React state the source of truth. Since handleChange runs on every keystroke to update the React state, the displayed value will update as the user types.
- With a controlled component, the input’s value is always driven by the React state. While this means you have to type a bit more code, you can now pass the value to other UI elements too, or reset it from other event handlers.
- When you need to handle multiple controlled input elements, you can add a name attribute to each element and let the handler function choose what to do based on the value of event.target.name.
- It can sometimes be tedious to use controlled components, because you need to write an event handler for every way your data can change and pipe all of the input state through a React component. This can become particularly annoying when you are converting a preexisting codebase to React, or integrating a React application with a non-React library. In these situations, you might want to check out uncontrolled components, an alternative technique for implementing input forms.
- If you’re looking for a complete solution including validation, keeping track of the visited fields, and handling form submission, Formik is one of the popular choices. However, it is built on the same principles of controlled components and managing state — so don’t neglect to learn them.

## state and lifecycle

[Link to Article](https://reactjs.org/docs/state-and-lifecycle.html)

- Consider the ticking clock example from one of the previous sections. In Rendering Elements, we have only learned one way to update the UI. We call ReactDOM.render() to change the rendered output:

### Cinverting a Function to a Class

- You can convert a function component like Clock to a class in five steps:
  1. Create an ES6 class, with the same name, that extends React.Component.
  1. Add a single empty method to it called render().
  1. Move the body of the function into the render() method.
  1. Replace props with this.props in the render() body.
  1. Delete the remaining empty function declaration.

### Adding Local State to a Class

1. Replace this.props.date with this.state.date in the render() method:
1. Add a class constructor that assigns the initial this.state:
1. Remove the date prop from the <Clock /> element:

- In applications with many components, it’s very important to free up resources taken by the components when they are destroyed.
- We want to set up a timer whenever the Clock is rendered to the DOM for the first time. This is called “mounting” in React.
- We also want to clear that timer whenever the DOM produced by the Clock is removed. This is called “unmounting” in React.
- We can declare special methods on the component class to run some code when a component mounts and unmounts:

### Recap

1. When <Clock /> is passed to ReactDOM.render(), React calls the constructor of the Clock component. Since Clock needs to display the current time, it initializes this.state with an object including the current time. We will later update this state.
1. React then calls the Clock component’s render() method. This is how React learns what should be displayed on the screen. React then updates the DOM to match the Clock’s render output.
1. When the Clock output is inserted in the DOM, React calls the componentDidMount() lifecycle method. Inside it, the Clock component asks the browser to set up a timer to call the component’s tick() method once a second.
1. Every second the browser calls the tick() method. Inside it, the Clock component schedules a UI update by calling setState() with an object containing the current time. Thanks to the setState() call, React knows the state has changed, and calls the render() method again to learn what should be on the screen. This time, this.state.date in the render() method will be different, and so the render output will include the updated time. React updates the DOM accordingly.
1. If the Clock component is ever removed from the DOM, React calls the componentWillUnmount() lifecycle method so the timer is stopped.

- The only place where you can assign this.state is the constructor.

## components and props

[Link to Article](https://reactjs.org/docs/components-and-props.html)

- Components let you split the UI into independent, reusable pieces, and think about each piece in isolation. This page provides an introduction to the idea of components.
- Conceptually, components are like JavaScript functions. They accept arbitrary inputs (called “props”) and return React elements describing what should appear on the screen.

```js
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}
```

- This function is a valid React component because it accepts a single “props” (which stands for properties) object argument with data and returns a React element. We call such components “function components” because they are literally JavaScript functions.

- Recap
  1. We call ReactDOM.render() with the < Welcome name="Sara" /> element.
  1. React calls the Welcome component with {name: 'Sara'} as the props.
  1. Our Welcome component returns a < h1 >Hello, Sara< /h1 > element as the result.
  1. React DOM efficiently updates the DOM to match < h1 >Hello, Sara< /h1 >.

- Always start component names with a capital letter.
- Components can refer to other components in their output. This lets us use the same component abstraction for any level of detail. A button, a form, a dialog, a screen: in React apps, all those are commonly expressed as components.
- Typically, new React apps have a single App component at the very top. However, if you integrate React into an existing app, you might start bottom-up with a small component like Button and gradually work your way to the top of the view hierarchy.
- Whether you declare a component as a function or a class, it must never modify its own props
- **All React components must act like pure functions with respect to their props.** application UIs are dynamic and change over time. In the next section, we will introduce a new concept of “state”. State allows React components to change their output over time in response to user actions, network responses, and anything else, without violating this rule.



## React Testing Library

[The Link to the Testing Library is Broken](https://testing-library.com/docs/dom-testing-library/react-testing-library)

## RTL Testing Example

[Link to Article](https://thomlom.dev/beginner-guide-testing-react-apps/)

- developers tend to test what we call implementation details. Let’s take a simple example to explain it. We want to create a counter that we can both increment and decrement. Here is the implementation (with a class component) with two tests: the first one is written with Enzyme and the other one with React Testing Library.
- Let’s say we want to refactor our components because we want to make it possible to set any count value. So we remove our increment and decrement methods and then add a new setCount method. We forgot to wire this new method to our different buttons

### False Posotive

```js
import React from "react"
class Counter extends React.Component {
  state = { count: 0 }
  setCount = (count) => this.setState({ count })
  render() {
    return (
      <div>
        <button onClick={this.decrement}>-</button>
        <p>{this.state.count}</p>
        <button onClick={this.increment}>+</button>
      </div>
    )
  }
}
export default Counter
```

- The first test (Enzyme) will pass, but the second one (RTL) will fail. Indeed, the first one doesn’t care if our buttons are correctly wired to the methods. It just looks at the implementation itself: our increment and decrement method. This is a false positive.

### False Negative

```js
import React, { useState } from "react"
const Counter = () => {
  const [count, setCount] = useState(0)
  const increment = () => setCount((count) => count + 1)
  const decrement = () => setCount((count) => count - 1)
  return (
    <div>
      <button onClick={decrement}>-</button>
      <p>{count}</p>
      <button onClick={increment}>+</button>
    </div>
  )
}
export default Counter
```

- This time, the first test is going to be broken even if your counter still works. This is a false-negative! Enzyme will complain about state not being able to work on functional components:

- Almost of your tests will be written that way:
  1. You arrange (= setup) your code so that everything is ready for the next steps.
  1. You act, you perform the steps a user is supposed to do (such as a click).
  1. You make assertions on what is supposed to happen.



[Back to code 401 notes](../401-Javascript.md)