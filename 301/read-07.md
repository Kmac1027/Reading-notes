# Read: 07 - APIs continued

## What Google Learned From Its Quest to Build the Perfect Team

- [Refer to 201 notes -class 14b](201/class-14b.md)

## How I explained REST to my brother

- fun little article - https://gist.github.com/brookr/5977550

## Documentation for SuperAgent

- SuperAgent - SuperAgent is light-weight progressive ajax API crafted for flexibility, readability, and a low learning curve after being frustrated with many of the existing request APIs. It also works with Node.js!
```
 request
   .post('/api/pet')
   .send({ name: 'Manny', species: 'cat' })
   .set('X-API-Key', 'foobar')
   .set('Accept', 'application/json')
   .then(res => {
      alert('yay got ' + JSON.stringify(res.body));
   });
```

   - Request basics - .then() (or .end() or await) to send the request. For example a simple GET request:

```
 request
   .get('/search')
   .then(res => {
      // res.body, res.headers, res.status
   })
   .catch(err => {
      // err.message, err.response
   });
   ```

- HTTP method may also be passed as a string:
- Old-style callbacks are also supported, but not recommended. Instead of .then() you can call .end():
- Absolute URLs can be used. In web browsers absolute URLs work only if the server implements CORS.
- The Node client supports making requests to Unix Domain Sockets
- DELETE, HEAD, PATCH, POST, and PUT requests can also be used, simply change the method name:
- DELETE can be also called as .del() for compatibility with old IE where delete is a reserved word.
- Setting header fields is simple, invoke .set() with a field name and value:
```
request
   .get('/search')
   .set('API-Key', 'foobar')
   .set('Accept', 'application/json')
   .then(callback);
```
- You may also pass an object to set several fields in a single call:
```
 request
   .get('/search')
   .set({ 'API-Key': 'foobar', Accept: 'application/json' })
   .then(callback);
```
- GET requests - The .query() method accepts objects, which when used with the GET method will form a query-string. The following will produce the path /search?query=Manny&range=1..5&order=desc.
- POST / PUT requests - A typical JSON POST request might look a little like the following, where we set the Content-Type header field appropriately, and "write" some data, in this case just a JSON string.
- Setting the Content-Type
- Facebook and Accept JSON - If you are calling Facebook's API, be sure to send an Accept: application/json header in your request. If you don't do this, Facebook will respond with Content-Type: text/javascript; charset=UTF-8, which SuperAgent will not parse and thus res.body will be undefined. You can do this with either req.accept('json') or req.header('Accept', 'application/json')
- By default the query string is not assembled in any particular order. An asciibetically-sorted query string can be enabled with req.sortQuery(). You may also provide a custom sorting comparison function with req.sortQuery(myComparisonFn). The comparison function should take 2 arguments and return a negative/zero/positive integer.
 - TLS options - In Node.js SuperAgent supports methods to configure HTTPS requests:
  1. .ca(): Set the CA certificate(s) to trust
  1. .cert(): Set the client certificate chain(s)
  1. .key(): Set the client private key(s)
  1. .pfx(): Set the client PFX or PKCS12 encoded private key and certificate chain
  1. .disableTLSCerts(): Does not reject expired or invalid TLS certs. Sets internally rejectUnauthorized=true. Be warned, this method allows MITM attacks.
  - Buffering responses
    1. To force buffering of response bodies as res.text you may invoke req.buffer(). To undo the default of buffering for text responses such as "text/plain", "text/html" etc you may invoke req.buffer(false).
      1. When buffered the res.buffered flag is provided, you may use this to handle both buffered and unbuffered responses in the same callback.
- CORS - For security reasons, browsers will block cross-origin requests unless the server opts-in using CORS headers. Browsers will also make extra OPTIONS requests to check what HTTP headers and methods are allowed by the server. Read more about CORS.
- Note that superagent considers 4xx and 5xx responses (as well as unhandled 3xx responses) errors by default.
- esting on localhost - In Node.js it's possible to ignore DNS resolution and direct all requests to a specific IP address using .connect() method.
- Promise and Generator support - SuperAgent's request is a "thenable" object that's compatible with JavaScript promises and the async/await syntax.
- Browser and node versions
  1. SuperAgent has two implementations: one for web browsers (using XHR) and one for Node.JS (using core http module). By default Browserify and WebPack will pick the browser version.
  1. If want to use WebPack to compile code for Node.JS, you must specify node target in its configuration.
- Using browser version in electron
  1. Electron developers report if you would prefer to use the browser version of SuperAgent instead of the Node version, you can require('superagent/superagent'). Your requests will now show up in the Chrome developer tools Network tab. Note this environment is not covered by automated test suite and not officially supported.

  - link to article - https://visionmedia.github.io/superagent/



  

## API Keys - request API keys from the following APIs

1. Geocoding API Docs - Done
1. Weather Bit API Docs - Done
1. Yelp API Docs - Done
1. The Movie DB API Docs - Done
1. The Hiking Project API Docs - done

[Back to code 301 notes](../301.md)