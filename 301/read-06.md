# Read: 06 - Node, Express, and APIs

## What Is Node and When Should I Use It?

- Node.js® is a JavaScript runtime built on Chrome’s V8 JavaScript engine.
  - The V8 engine is the open-source JavaScript engine that runs in Google Chrome and other Chromium-based web browsers, including Brave, Opera, and Vivaldi. It was designed with performance in mind and is responsible for compiling JavaScript directly to native machine code that your computer can execute.
- Node.js is an event-based, non-blocking, asynchronous I/O runtime that uses Google’s V8 JavaScript engine and libuv library.
- You can check that Node is installed on your system by opening a terminal and typing node -v. If all has gone well, you should see something like v12.14.1 displayed. This is the current LTS version at the time of writing.
- As can be seen on this compatibility table, Node has excellent support for ECMAScript 2015 (ES6) and beyond. As you’re only targeting one runtime (a specific version of the V8 engine), this means that you can write your JavaScript using the latest and most modern syntax. It also means that you don’t generally have to worry about compatibility issues — as you would if you were writing JavaScript that would run in different browsers.
- Node has excellent support for ECMAScript 2015 (ES6) and beyond. As you’re only targeting one runtime (a specific version of the V8 engine), this means that you can write your JavaScript using the latest and most modern syntax. It also means that you don’t generally have to worry about compatibility issues — as you would if you were writing JavaScript that would run in different browsers.

```
function upcase(strings, ...values) {
  return values.map(name => name[0].toUpperCase() + name.slice(1))
    .join(' ') + strings[2];
}

const person = {
  first: 'brendan',
  last: 'eich',
  age: 56,
  position: 'CEO of Brave Software',
};

const { first, last } = person;
const emoticon = [ ['┌', '('], ['˘', '⌣'], ['˘', ')', 'ʃ'] ];

console.log(
  upcase`${first} ${last} is the creator of JavaScript! ` + emoticon.flat().join('')
);
```
- npm, the JavaScript Package Manager - npm is also the world’s largest software registry. There are over 1,000,000 packages of JavaScript code available to download, with billions of downloads per week. Let’s take a quick look at how we would use npm to install a package.
- Node.Js runes javascript on the server
- The fact that Node runs in a single thread does impose some limitations. For example, blocking I/O calls should be avoided, CPU-intensive operations should be handed off to a worker thread, and errors should always be handled correctly for fear of crashing the entire process.
- Aside from speed and scalability, an often-touted advantage of using JavaScript on a web server — as well as in the browser — is that your brain no longer needs to switch modes. You can do everything in the same language, which, as a developer, makes you more productive (and hopefully, happier). For example, you can easily share code between the server and the client.
- JSON is probably the most important data exchange format on the Web, and the lingua franca for interacting with object databases (such as MongoDB). JSON is ideally suited for consumption by a JavaScript program, meaning that when you’re working with Node, data can flow neatly between layers without the need for reformatting. You can have one syntax from browser to server to database.
- JavaScript is ubiquitous: most of us are familiar with JavaScript, or have used it at some point. This means that transitioning to Node development is potentially easier than to other server-side languages. To quote Craig Buckler in his Node vs PHP Smackdown, JavaScript might remain the world’s most misunderstood language — but, once the concepts click, it makes other languages seem cumbersome.
- it doesn’t stop at the server. There are many other exciting and varied uses of Node.js!
  - it can be used as a scripting language to automate repetitive or error prone tasks on your PC. It can also be used to write your own command line tool, such as this Yeoman-Style generator to scaffold out new projects.
  - Node.js can also can be used to build cross-platform desktop apps and even to create your own robots.
- Node.js is an event-based, non-blocking, asynchronous I/O runtime that uses Google’s V8 JavaScript engine and libuv library.

### Additional helpful articles

- https://www.sitepoint.com/webpack-beginner-guide/
- https://www.sitepoint.com/up-and-running-with-eslint-the-pluggable-javascript-linter/
- https://www.sitepoint.com/introduction-gulp-js/
- https://www.sitepoint.com/unit-test-javascript-mocha-chai/

[Back to code 301 notes](../301.md)