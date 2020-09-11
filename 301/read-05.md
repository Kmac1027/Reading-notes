# Read: 05 - Heroku Deployment

## Heroku: Getting Started with Node

- Comleted all steps up through "View Logs"

## Deploying a Simple Blog to Heroku

- Node.js is an open source, cross-platform runtime environment, which allows you to build server-side and networking applications
- It'- Simple JavaScript server example
```
var http = require("http");

http.createServer(function(request, response) {
  response.writeHead(200, {"Content-Type": "text/plain"});
  response.write("It's alive!");
  response.end();
}).listen(3000);
```
- This is an example of how Node provides you with non-blocking and event-driven behavior
```
$.post('/some_requested_resource', function(data) {
  console.log(data);
});
```
- https://howtonode.org/deploy-blog-to-heroku

[Back to code 301 notes](../301.md)