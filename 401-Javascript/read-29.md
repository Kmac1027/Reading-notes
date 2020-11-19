# Readings 29: Routing

## browser router tutorial

[Link to article](https://blog.pshrmn.com/simple-react-router-v4-tutorial/)

- When starting a new project, you need to determine which type of router to use. For browser based projects, there are < BrowserRouter> and < HashRouter> components. The < BrowserRouter> should be used when you have a server that will handle dynamic requests (knows how to respond to any possible URI), while the < HashRouter> should be used for static websites (where the server can only respond to requests for files that it knows about).
- Each router creates a history object, which it uses to keep track of the current location 1 and re-render the website whenever that changes. The other components provided by React Router rely on having that history object available through React’s context, so they must be rendered as descendants of a router component. A React Router component that does not have a router as one of its ancestors will fail to work.
- Router components only expect to receive a single child element. To work within this limitation, it is useful to create an < App> component that renders the rest of your application. Separating your application from the router is also useful for server rendering because you can re-use the < App> on the server while switching the router to a < MemoryRouter>.

```js
import { BrowserRouter } from 'react-router-dom';

ReactDOM.render((
  <BrowserRouter>
    <App />
  </BrowserRouter>
), document.getElementById('root'));

```

- Our application is defined within the <App> component. To simplify things, we will split our application into two parts. The <Header> component will contain links to navigate throughout the website. The <Main> component is where the rest of the content will be rendered.

```js
// this component will be rendered by our <___Router>
function App() {
  return (
    <div>
      <Header />
      <Main />
    </div>
  );
}
```

- The < Route> component is the main building block of React Router. Anywhere that you want to only render content based on the location’s pathname, you should use a < Route> element.
- A < Route> expects a path prop, which is a string that describes the pathname that the route matches — for example, < Route path='/roster'/> should match a pathname that begins with /roster 2. When the current location’s pathname is matched by the path, the route will render a React element. When the path does not match, the route will not render anything 3.

```js
<Route path='/roster'/>
// when the pathname is '/', the path does not match
// when the pathname is '/roster' or '/roster/2', the path matches
// If you only want to match '/roster', then you need to use
// the "exact" prop. The following will match '/roster', but not
// '/roster/2'.
<Route exact path='/roster'/>
// You might find yourself adding the exact prop to most routes.
// In the future (i.e. v5), the exact prop will likely be true by
// default. For more information on that, you can check out this
// GitHub issue:
// https://github.com/ReactTraining/react-router/issues/4958
```

- React Router uses the path-to-regexp package to determine if a route element’s path prop matches the current location. It compiles the path string into a regular expression, which will be matched against the location’s pathname. path strings have more advanced formatting options than will be covered here. You can read about them in the path-to-regexp documentation.
- < Route>s can be created anywhere inside of the router, but often it makes sense to render them in the same place. You can use the < Switch> component to group < Route>s. The < Switch> will iterate over its children elements (the routes) and only render the first one that matches the current pathname.
- Routes have three props that can be used to define what should be rendered when the route’s path matches. Only one should be provided to a < Route> element.
  1. component — A React component. When a route with a component prop matches, the route will return a new element whose type is the provided React component (created using React.createElement).
  1. render — A function that returns a React element 5. It will be called when the path matches. This is similar to component, but is useful for inline rendering and passing extra props to the element.
  1. children — A function that returns a React element. Unlike the prior two props, this will always be rendered, regardless of whether the route’s path matches the current location.

```js
  <Route path='/page' component={Page} />
const extraProps = { color: 'red' }
<Route path='/page' render={(props) => (
  <Page {...props} data={extraProps}/>
)}/>
<Route path='/page' children={(props) => (
  props.match
    ? <Page {...props}/>
    : <EmptyPage {...props}/>
)}/>
```

  - Typically, either the component or render prop should be used. The children prop can be useful occasionally, but typically it is preferable to render nothing when the path does not match. We do not have any extra props to pass to the components, so each of our < Route>s will use the component prop.
  - Now that we have figured our root route structure, we just need to actually render our routes. For this application, we will render our < Switch> and < Route>s inside of our < Main> component, which will place the HTML generated by a matched route inside of a < main> DOM node.
  - Finally, our application needs a way to navigate between pages. If we were to create links using anchor elements, clicking on them would cause the whole page to reload. React Router provides a < Link> component to prevent that from happening. When clicking a < Link>, the URL will be updated and the rendered content will change without reloading the page.

```js
  import { Link } from 'react-router-dom'
function Header() {
  return (
    <header>
      <nav>
        <ul>
          <li><Link to='/'>Home</Link></li>
          <li><Link to='/roster'>Roster</Link></li>
          <li><Link to='/schedule'>Schedule</Link></li>
        </ul>
      </nav>
    </header>
  );
}
```

## browser router api docs

[Link to docs](https://reactrouter.com/web/api)

[Back to code 401 notes](../401-Javascript.md)