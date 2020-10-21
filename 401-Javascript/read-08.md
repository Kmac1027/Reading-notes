# Readings: Express Routing & Connected API

## Review, Research, and Discussion

1. Name 3 real world use cases where you’d want to change the request with custom middleware
  password
  making sure a user is logged in before letting them move forward
  Logging Data for analytics
1. True or false: The route handler is middleware? 
  True
1. In what ways can a middleware function end the process and send data to the browser?
  res.send()/res.end()
1. At what point in the request lifecycle can you “inject” middleware?
  Anywear before it hits the end
1. What can cause express to error with “Request headers sent twice, cannot start a second response”
the request handler function somehow ends up in a loop because it was never ended or sent next();

## Vocabulary Terms - from Tif

Middleware - software that acts as a bridge between an operating system or database and applications
Request Object - reps the HTTP request with properites - the object that asks the server for something
Response Object - HTTP response, carries back the information to the client
Application Middleware - middleware affecting and talking to your entire application and talks to other applications
Routing Middleware - ust like app level except it is glued to a specific instance of express.router() method

## using express routing

[Link to Article](https://expressjs.com/en/guide/routing.html)
[Basic Routing](https://expressjs.com/en/starter/basic-routing.html)

- You define routing using methods of the Express app object that correspond to HTTP methods; for example, app.get() to handle GET requests and app.post to handle POST requests. For a full list, see app.METHOD. You can also use app.all() to handle all HTTP methods and app.use() to specify middleware as the callback function (See Using middleware for details).
- These routing methods specify a callback function (sometimes called “handler functions”) called when the application receives a request to the specified route (endpoint) and HTTP method. In other words, the application “listens” for requests that match the specified route(s) and method(s), and when it detects a match, it calls the specified callback function.
- The routing methods can have more than one callback function as arguments. With multiple callback functions, it is important to provide next as an argument to the callback function and then call next() within the body of the function to hand off control to the next callback.

-  [full list of all HTTP request methods](https://expressjs.com/en/4x/api.html#app.METHOD)

- There is a special routing method, app.all(), used to load middleware functions at a path for all HTTP request methods. For example, the following handler is executed for requests to the route “/secret” whether using GET, POST, PUT, DELETE, or any other HTTP request method supported in the http module.

### Route paths

- Route paths, in combination with a request method, define the endpoints at which requests can be made. Route paths can be strings, string patterns, or regular expressions.
- The characters ?, +, *, and () are subsets of their regular expression counterparts. The hyphen (-) and the dot (.) are interpreted literally by string-based paths.
- If you need to use the dollar character ($) in a path string, enclose it escaped within ([ and ]). For example, the path string for requests at “/data/$book”, would be “/data/([\$])book”.

### Route parameters

- Route parameters are named URL segments that are used to capture the values specified at their position in the URL. The captured values are populated in the req.params object, with the name of the route parameter specified in the path as their respective keys.

```

Route path: /users/:userId/books/:bookId
Request URL: http://localhost:3000/users/34/books/8989
req.params: { "userId": "34", "bookId": "8989" }
```

- To define routes with route parameters, simply specify the route parameters in the path of the route as shown below.

```js
app.get('/users/:userId/books/:bookId', function (req, res) {
  res.send(req.params)
})
```

### Route handlers

- You can provide multiple callback functions that behave like middleware to handle a request. The only exception is that these callbacks might invoke next('route') to bypass the remaining route callbacks. You can use this mechanism to impose pre-conditions on a route, then pass control to subsequent routes if there’s no reason to proceed with the current route.

### Response methods

- The methods on the response object (res) in the following table can send a response to the client, and terminate the request-response cycle. If none of these methods are called from a route handler, the client request will be left hanging.

[Response Methods](response-methods.png)

- app.route() - You can create chainable route handlers for a route path by using app.route(). Because the path is specified at a single location, creating modular routes is helpful, as is reducing redundancy and typos

### express.Router

- Use the express.Router class to create modular, mountable route handlers. A Router instance is a complete middleware and routing system; for this reason, it is often referred to as a “mini-app”.
- The following example creates a router as a module, loads a middleware function in it, defines some routes, and mounts the router module on a path in the main app. (Create a router file named birds.js in the app directory, with the following content:)

```js
var express = require('express')
var router = express.Router()

// middleware that is specific to this router
router.use(function timeLog (req, res, next) {
  console.log('Time: ', Date.now())
  next()
})
// define the home page route
router.get('/', function (req, res) {
  res.send('Birds home page')
})
// define the about route
router.get('/about', function (req, res) {
  res.send('About birds')
})

module.exports = router

// then add the router module in the app

var birds = require('./birds')

// ...

app.use('/birds', birds)
```

## express routing

[Link to article](https://scotch.io/tutorials/learn-to-use-the-new-router-in-expressjs-4)

### Learn to Use the New Router in ExpressJS 4.0

- Express 4.0 comes with the new Router. Router is like a mini express application. It doesn't bring in views or settings, but provides us with the routing APIs like .use, .get, .param, and route.
- **Express Router** is a mini express application without all the bells and whistles of an express application, just the routing stuff.
- Using the Router, we are allowed to make our applications more modular and flexible than ever before by creating multiple instances of the Router and applying them accordingly. Now we'll take a look at how we can use middleware to handle requests.

### Route Middleware router.use()

- Route middleware in Express is a way to do something before a request is processed. This could be things like checking if a user is authenticated, logging data for analytics, or anything else we'd like to do before we actually spit out information to our user.
- **The order you place your middleware and routes is very important. Everything will happen in the order that they appear. This means that if you place your middleware after a route, then the route will happen before the middleware and the request will end there. Your middleware will not run at that point.**
- We can define our routes right on our app. This is similar to using app.get, but we will use app.route. app.route is basically a shortcut to call the Express Router. Instead of calling express.Router(), we can call app.route and start applying our routes there. 
- Using app.route lets us define multiple actions on a single login route. We'll need a GET route to show the login form and a POST route to process the login form.

### Conclusion

- Recap
  1. Use express.Router() multiple times to define groups of routes
  1. Apply the express.Router() to a section of our site using app.use()
  1. Use route middleware to process requests
  1. Use route middleware to validate parameters using .param()
  1. Use app.route() as a shortcut to the Router to define multiple requests on a route

[Back to code 401 notes](../401-Javascript.md)