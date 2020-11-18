# Readings 28: Component Composition

## react basics recap

[Link to artivle](https://www.freecodecamp.org/news/these-are-the-concepts-you-should-know-in-react-js-after-you-learn-the-basics-ee1d2f4b8030/)

1. **The Component Lifecycle** - By far the most important concept on this list is understanding the component lifecycle. The component lifecycle is exactly what it sounds like: it details the life of a component. Like us, components are born, do some things during their time here on earth, and then they die

![](https://cdn-media-1.freecodecamp.org/images/1*U13Mlxz_ktcajaeJCyYkwg.png)

- Let’s break this image down. Each colored horizontal rectangle represents a lifecycle method (except for “React updates DOM and refs”). The columns represent different stages in the components life.
- A component can only be in one stage at a time. It starts with mounting and moves onto updating. It stays updating perpetually until it gets removed from the virtual DOM. Then it goes into the unmounting phase and gets removed from the DOM.
- The lifecycle methods allow us to run code at specific points in the component’s life or in response to changes in the component’s life.

#### Mounting

- Since class-based components are classes, hence the name, the first method that runs is the constructor method. Typically, the constructor is where you would initialize component state.
- Next, the component runs the getDerivedStateFromProps
- Now we come to the render method which returns your JSX. Now React **“mounts”** onto the DOM.
- Lastly, the componentDidMount method runs. Here is where you would do any asynchronous calls to databases or directly manipulate the DOM if you need. Just like that, our component is born.

#### Updating

- This phase is triggered every time state or props change. Like in mounting, getDerivedStateFromProps is called (but no constructor this time!).
- Next shouldComponentUpdate runs. Here you can compare old props/state with the new set of props/state. You can determine if your component should re-render or not by returning true or false. This can make your web app more efficient by cutting down on extra re-renders. If shouldComponentUpdate returns false, this update cycle ends.
- If not, React re-renders and getSnapshotBeforeUpdate runs afterwards. This method has limited use as well. React then runs componentDidUpdate. Like componentDidMount you can use it to make any async calls or manipulate the DOM.

#### Unmounting

- Our component lived a good life, but all good things must come to an end. The unmounting phase is that last stage of the component lifecycle. When you remove a component from the DOM, React runs componentWillUnmount right before it gets removed. You should use this method to clean up any open connections such as WebSockets or intervals.

2. **Higher-Order Components or HOC** - A higher-order component is a function that takes a component and returns a new component

- When we call connect, we get a HOC back that we can use to wrap a component. From here we just pass our component to the HOC and start using the component our HOC returns.
- What HOCs allow us to do is abstract shared logic between components into a single overarching component.
- A good use case for an HOC is authorization. You could write your authentication code in every single component that needs it. It would quickly and unnecessarily bloat your code.

3. **React State and setState()**

- The only way you should change state is via the setState method. This method takes an object and merges it into the current state. On top of this, there are a few things you should also know about it.
- First, setState is asynchronous. This means state won’t update exactly after you call setState and this can lead to some aggravating behavior which we will hopefully now be able to avoid!

![](https://cdn-media-1.freecodecamp.org/images/1*qle8858T8Amobp6-WCrLZA.png)

- Looking at the above image, you can see that we call setState and then console.log state right after. Our new counter variable should be 1, but it’s in fact 0. So what if we want to access the new state after setState actually updates state?
- This brings us to the next piece of knowledge that we should know about setState and that is it can take a callback function. Let’s fix our code!

![](https://cdn-media-1.freecodecamp.org/images/1*typSaWY-BfT4fMUaAP_jJg.png)

- Great, it works, now we’re done right? Not exactly. We’re actually not using setState correctly in this case. Instead of passing an object to setState, we’re going to give it a function. This pattern is typically used when you’re using the current state to set the new state, like in our example above. If you’re not doing that, feel free to keep passing an object to setState. Let’s update our code again!

![](https://cdn-media-1.freecodecamp.org/images/1*jWrcTSN4rr3f1rEYNiFcxQ.png)

- What’s the point of passing a function instead of an object? Because setState is asynchronous, relying on it to create our new value will have some pitfalls. For example, by the time setState runs, another setState could have mutated state. Passing setState a function gives us two benefits. The first is it allows us to take a static copy of our state that will never change on its own. The second is that it will queue the setState calls so they run in order.

4. **React Context** - The React context API allows you to create global context objects that can be given to any component you make. This allows you to share data without having to pass props down all the way through the DOM tree.

5. **Stay up to date with React!** - This last concept is probably the easiest to understand. It’s simply keeping up with the latest releases of React. React has made some serious changes lately and it’s only going to continue to grow and develop.

## props.children

[Link to Article](https://codeburst.io/a-quick-intro-to-reacts-props-children-cb3d2fce4891)

- The React docs say that you can use props.children on components that represent ‘generic boxes’ and that ‘don’t know their children ahead of time’.
- A simple explanation of what this.props.children does is that it is used to display whatever you include between the opening and closing tags when invoking a component.
- Here’s an example of a stateless function that is used to create a component. Again, since this is a stateless function, there is no 'this' keyword so just use props.children

```js
const Picture = (props) => {
  return (
    <div>
      <img src={props.src}/>
      {props.children}
    </div>
  )
}
```
- This component contains an < img > that is receiving some props and then it is displaying {props.children}.

```js
//App.js
render () {
  return (
    <div className='container'>
      <Picture key={picture.id} src={picture.src}>
          //what is placed here is passed as props.children  
      </Picture>
    </div>
  )
}
```

- **Instead of invoking the component with a self-closing tag < Picture /> if you invoke it will full opening and closing tags < Picture> < /Picture> you can then place more code between it.**

## composition vs inheritance

[Link to Article](https://reactjs.org/docs/composition-vs-inheritance.html)

- React has a powerful composition model, and we recommend using composition instead of inheritance to reuse code between components.
- Some components don’t know their children ahead of time. This is especially common for components like Sidebar or Dialog that represent generic “boxes”.
- We recommend that such components use the special children prop to pass children elements directly into their output

```js
function FancyBorder(props) {
  return (
    <div className={'FancyBorder FancyBorder-' + props.color}>
      {props.children}
    </div>
  );
}
```

- This lets other components pass arbitrary children to them by nesting the JSX:

```js
function WelcomeDialog() {
  return (
    <FancyBorder color="blue">
      <h1 className="Dialog-title">
        Welcome
      </h1>
      <p className="Dialog-message">
        Thank you for visiting our spacecraft!
      </p>
    </FancyBorder>
  );
}
```

- Sometimes we think about components as being “special cases” of other components. For example, we might say that a WelcomeDialog is a special case of Dialog.
- In React, this is also achieved by composition, where a more “specific” component renders a more “generic” one and configures it with props:

```js
function Dialog(props) {
  return (
    <FancyBorder color="blue">
      <h1 className="Dialog-title">
        {props.title}
      </h1>
      <p className="Dialog-message">
        {props.message}
      </p>
    </FancyBorder>
  );
}

function WelcomeDialog() {
  return (
    <Dialog
      title="Welcome"
      message="Thank you for visiting our spacecraft!" />
  );
}
```

- Props and composition give you all the flexibility you need to customize a component’s look and behavior in an explicit and safe way. Remember that components may accept arbitrary props, including primitive values, React elements, or functions.
- If you want to reuse non-UI functionality between components, we suggest extracting it into a separate JavaScript module. The components may import it and use that function, object, or a class, without extending it.

## react testing library api example

[Link to test Library](https://testing-library.com/docs/react-testing-library/example-intro/)

[Back to code 401 notes](../401-Javascript.md)