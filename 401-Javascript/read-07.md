# Read: Class 07 Express

## Define

SOAP
ReST Verbs
CRUD Verbs
Swagger

## express middleware explained

- [Link to video](https://www.youtube.com/watch?v=9HOem0amlyg&ab_channel=JsWiz)

## using express middleware

- [Link to Article](https://expressjs.com/en/guide/using-middleware.html)

- Express is a routing and middleware web framework that has minimal functionality of its own: An Express application is essentially a series of middleware function calls.
- Middleware functions are functions that have access to the request object (req), the response object (res), and the next middleware function in the application’s request-response cycle. The next middleware function is commonly denoted by a variable named next.
- Middleware functions can perform the following tasks:
  1. Execute any code.
  1. Make changes to the request and the response objects.
  1. End the request-response cycle.
  1. Call the next middleware function in the stack.
- If the current middleware function does not end the request-response cycle, it must call next() to pass control to the next middleware function. Otherwise, the request will be left hanging.

### Application-level middleware

- Bind application-level middleware to an instance of the app object by using the app.use() and app.METHOD() functions, where METHOD is the HTTP method of the request that the middleware function handles (such as GET, PUT, or POST) in lowercase.
- This example shows a middleware function with no mount path. The function is executed every time the app receives a request.

```js
var express = require('express')
var app = express()

app.use(function (req, res, next) {
  console.log('Time:', Date.now())
  next()
})

```

- This example shows a middleware function mounted on the /user/:id path. The function is executed for any type of HTTP request on the /user/:id path.

```js
app.use('/user/:id', function (req, res, next) {
  console.log('Request Type:', req.method)
  next()
})
```

- This example shows a route and its handler function (middleware system). The function handles GET requests to the /user/:id path.

```js
app.get('/user/:id', function (req, res, next) {
  res.send('USER')
})
```

- Here is an example of loading a series of middleware functions at a mount point, with a mount path. It illustrates a middleware sub-stack that prints request info for any type of HTTP request to the /user/:id path.

```js
app.use('/user/:id', function (req, res, next) {
  console.log('Request URL:', req.originalUrl)
  next()
}, function (req, res, next) {
  console.log('Request Type:', req.method)
  next()
})
```

## express middleware

- [Link to Article](https://www.tutorialspoint.com/expressjs/expressjs_middleware.htm)

- Middleware functions are functions that have access to the request object (req), the response object (res), and the next middleware function in the application’s request-response cycle. These functions are used to modify req and res objects for tasks like parsing request bodies, adding response headers, etc.

### Order of Middleware Calls

- One of the most important things about middleware in Express is the order in which they are written/included in your file; the order in which they are executed, given that the route matches also needs to be considered.
- For example, in the following code snippet, the first function executes first, then the route handler and then the end function. This example summarizes how to use middleware before and after route handler; also how a route handler can be used as a middleware itself.

[](https://www.tutorialspoint.com/expressjs/images/middleware_desc.jpg)

### Third Party Middleware

- A list of Third party middleware for Express is available here. Following are some of the most commonly used middleware; we will also learn how to use/mount these −

**body-parser**
This is used to parse the body of requests which have payloads attached to them. To mount body parser, we need to install it using npm install --save body-parser and to mount it, include the following lines in your index.js

```js
var bodyParser = require('body-parser');

//To parse URL encoded data
app.use(bodyParser.urlencoded({ extended: false }))

//To parse json data
app.use(bodyParser.json())
```

**cookie-parser**
It parses Cookie header and populate req.cookies with an object keyed by cookie names. To mount cookie parser, we need to install it using npm install --save cookie-parser and to mount it, include the following lines in your index.js

```js
var cookieParser = require('cookie-parser');
app.use(cookieParser())
```

## using express routing

[Link to article](https://expressjs.com/en/guide/routing.html)

- **Routing** refers to how an application’s endpoints (URIs) respond to client requests.
- You define routing using methods of the Express app object that correspond to HTTP methods; for example, app.get() to handle GET requests and app.post to handle POST requests. For a full list, see app.METHOD. You can also use app.all() to handle all HTTP methods and app.use() to specify middleware as the callback function (See Using middleware for details).
- These routing methods specify a callback function (sometimes called “handler functions”) called when the application receives a request to the specified route (endpoint) and HTTP method. In other words, the application “listens” for requests that match the specified route(s) and method(s), and when it detects a match, it calls the specified callback function.
- In fact, the routing methods can have more than one callback function as arguments. With multiple callback functions, it is important to provide next as an argument to the callback function and then call next() within the body of the function to hand off control to the next callback.
- The following code is an example of a very basic route.

```js
var express = require('express')
var app = express()

// respond with "hello world" when a GET request is made to the homepage
app.get('/', function (req, res) {
  res.send('hello world')
})
```

### Route methods

```js
// GET method route
app.get('/', function (req, res) {
  res.send('GET request to the homepage')
})

// POST method route
app.post('/', function (req, res) {
  res.send('POST request to the homepage')
})

app.all('/secret', function (req, res, next) {
  console.log('Accessing the secret section ...')
  next() // pass control to the next handler
})

```

### Route handlers

- You can provide multiple callback functions that behave like middleware to handle a request. The only exception is that these callbacks might invoke next('route') to bypass the remaining route callbacks. You can use this mechanism to impose pre-conditions on a route, then pass control to subsequent routes if there’s no reason to proceed with the current route.
- Route handlers can be in the form of a function, an array of functions, or combinations of both, as shown in the following examples.
- A single callback function can handle a route. For example:

```js
app.get('/example/a', function (req, res) {
  res.send('Hello from A!')
})
//More than one callback function can handle a route (make sure you specify the next object). For example:

app.get('/example/b', function (req, res, next) {
  console.log('the response will be sent by the next function ...')
  next()
}, function (req, res) {
  res.send('Hello from B!')
})
//An array of callback functions can handle a route. For example:

var cb0 = function (req, res, next) {
  console.log('CB0')
  next()
}

var cb1 = function (req, res, next) {
  console.log('CB1')
  next()
}

var cb2 = function (req, res) {
  res.send('Hello from C!')
}

app.get('/example/c', [cb0, cb1, cb2])
//A combination of independent functions and arrays of functions can handle a route. For example:

var cb0 = function (req, res, next) {
  console.log('CB0')
  next()
}

var cb1 = function (req, res, next) {
  console.log('CB1')
  next()
}

app.get('/example/d', [cb0, cb1], function (req, res, next) {
  console.log('the response will be sent by the next function ...')
  next()
}, function (req, res) {
  res.send('Hello from D!')
})
```

[Back to code 401 notes](../401-Javascript.md)