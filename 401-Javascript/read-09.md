# Read: class 09: API Server

## Review, Reasearch, and Discussion

1. How does route prefixing work with an external routing module?
  adds routs with a shared path
1. When routing, what’s the difference between app.get('/data/:id') and app.get('/data/:name')?
  different paramaters
1. Explain how Express handles routing conflicts?
  first come first serve
1. What are the ways that a browser can send “data” or request variables to an HTTP server
  POST/PUT/PATCH/GET

## Terms

Routing - determins which handler recievs a specific request
Route Prefixing - what comes before the params
Request “Body” - the main stuff a user is asking for usually in JSON form
Request “Query” - the parameters set by a user to define what they are loking for
Request “Params” - what specific data the server needs to serve



## express router.param() middleware

[Link to Article](https://expressjs.com/en/4x/api.html#router.param)

- Adds callback triggers to route parameters, where name is the name of the parameter and callback is the callback function. Although name is technically optional, using this method without it is deprecated starting with Express v4.11.0 (see below).
- The parameters of the callback function are:
  1. req, the request object.
  1. res, the response object.
  1. next, indicating the next middleware function.
  1. The value of the name parameter.
  1. The name of the parameter.
- Param callback functions are local to the router on which they are defined. They are not inherited by mounted apps or routers. Hence, param callbacks defined on router will be triggered only by route parameters defined on router routes.
- The behavior of the router.param(name, callback) method can be altered entirely by passing only a function to router.param(). This function is a custom implementation of how router.param(name, callback) should behave - it accepts two parameters and must return a middleware.
- The first parameter of this function is the name of the URL parameter that should be captured, the second parameter can be any JavaScript object which might be used for returning the middleware implementation.
- The middleware returned by the function decides the behavior of what happens when a URL parameter is captured.
- In this example, the router.param(name, callback) signature is modified to router.param(name, accessId). Instead of accepting a name and a callback, router.param() will now accept a name and a number
- Uses the specified middleware function or functions, with optional mount path path, that defaults to “/”.
- This method is similar to app.use(). A simple example and use case is described below. See app.use() for more information.
- Middleware is like a plumbing pipe: requests start at the first middleware function defined and work their way “down” the middleware stack processing for each path they match.
- Although these middleware functions are added via a particular router, when they run is defined by the path they are attached to (not the router). Therefore, middleware added via one router may run for other routers if its routes match. For example, this code shows two different routers mounted on the same path:

## mongoose middleware

[Link to article](https://mongoosejs.com/docs/middleware.html)

- Middleware (also called pre and post hooks) are functions which are passed control during execution of asynchronous functions. Middleware is specified on the schema level and is useful for writing plugins.
- Mongoose has 4 types of middleware: document middleware, model middleware, aggregate middleware, and query middleware. Document middleware is supported for the following document functions. In document middleware functions, this refers to the document.
- Query middleware is supported for the following Model and Query functions. In query middleware functions, this refers to the query.
- Aggregate middleware is for MyModel.aggregate(). Aggregate middleware executes when you call exec() on an aggregate object. In aggregate middleware, this refers to the aggregation object.
- Model middleware is supported for the following model functions. In model middleware functions, this refers to the model.
- All middleware types support pre and post hooks.
- Note: If you specify schema.pre('remove'), Mongoose will register this middleware for doc.remove() by default. If you want to your middleware to run on Query.remove() use schema.pre('remove', { query: true, document: false }, fn).
- Note: Unlike schema.pre('remove'), Mongoose registers updateOne and deleteOne middleware on Query#updateOne() and Query#deleteOne() by default. This means that both doc.updateOne() and Model.updateOne() trigger updateOne hooks, but this refers to a query, not a document. To register updateOne or deleteOne middleware as document middleware, use schema.pre('updateOne', { document: true, query: false }).
- Note: The create() function fires save() hooks.
- Middleware are useful for atomizing model logic. Here are some other ideas:
  1. complex validation
  1. removing dependent documents (removing a user removes all his blogposts)
  1. asynchronous defaults
  1. asynchronous tasks that a certain action triggers
- If any pre hook errors out, mongoose will not execute subsequent middleware or the hooked function. Mongoose will instead pass an error to the callback and/or reject the returned promise. There are several ways to report an error in middleware:
- Middleware execution normally stops the first time a piece of middleware calls next() with an error. However, there is a special kind of post middleware called "error handling middleware" that executes specifically when an error occurs. Error handling middleware is useful for reporting errors and making error messages more readable.
- Error handling middleware is defined as middleware that takes one extra parameter: the 'error' that occurred as the first parameter to the function. Error handling middleware can then transform the error however you want.
- You can also define hooks for the Model.aggregate() function. In aggregation middleware functions, this refers to the Mongoose Aggregate object. For example, suppose you're implementing soft deletes on a Customer model by adding an isDeleted property. To make sure aggregate() calls only look at customers that aren't soft deleted, you can use the below middleware to add a $match stage to the beginning of each aggregation pipeline.
- Certain Mongoose hooks are synchronous, which means they do not support functions that return promises or receive a next() callback. Currently, only init hooks are synchronous, because the init() function is synchronous. Below is an example of using pre and post init hooks.

## Mongoose Sub-documents

[Link](https://mongoosejs.com/docs/subdocs.html)

## mongoose virtual joins

- So far you've only populated based on the _id field. However, that's sometimes not the right choice. In particular, arrays that grow without bound are a MongoDB anti-pattern. Using mongoose virtuals, you can define more sophisticated relationships between documents.
- Keep in mind that virtuals are not included in toJSON() output by default. If you want populate virtuals to show up when using functions that rely on JSON.stringify(), like Express' res.json() function, set the virtuals: true option on your schema's toJSON options.
- You can populate in either pre or post hooks. If you want to always populate a certain field, check out the mongoose-autopopulate plugin.

[Back to code 401 notes](../401-Javascript.md)