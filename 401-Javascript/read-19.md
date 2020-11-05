# Readings 19: Message Queues

## Socket.io Chat Example

[Link to article](https://socket.io/get-started/chat/)

- Writing a chat application with popular web applications stacks like LAMP (PHP) has normally been very hard. It involves polling the server for changes, keeping track of timestamps, and it’s a lot slower than it should be.
- Sockets have traditionally been the solution around which most real-time chat systems are architected, providing a bi-directional communication channel between a client and a server.
- This means that the server can push messages to clients. Whenever you write a chat message, the idea is that the server will get it and push it to all other connected clients.
- The first goal is to set up a simple HTML webpage that serves out a form and a list of messages. We’re going to use the Node.JS web framework express to this end. Make sure Node.JS is installed.
- So far in index.js we’re calling res.send and passing it a string of HTML. Our code would look very confusing if we just placed our entire application’s HTML there, so instead we’re going to create a index.html file and serve that instead.
- Socket.IO is composed of two parts:
  1. A server that integrates with (or mounts on) the Node.JS HTTP Server socket.io
  1. A client library that loads on the browser side socket.io-client
- The main idea behind Socket.IO is that you can send and receive any events you want, with any data you want. Any objects that can be encoded as JSON will do, and binary data is supported too.
- The next goal is for us to emit the event from the server to the rest of the users.
- In order to send an event to everyone, Socket.IO gives us the io.emit() method.

## Rooms and Namespaces

[Link to Article](https://socket.io/docs/rooms/)

- Within each Namespace, you can define arbitrary channels called “Rooms” that sockets can join and leave.
- This is useful to broadcast data to a subset of sockets:
[](https://socket.io/images/rooms.png)

- To leave a channel you call leave in the same fashion as join. Both methods are asynchronous and accept a callback argument.
- Each Socket in Socket.IO is identified by a random, unguessable, unique identifier Socket#id. For your convenience, each socket automatically joins a room identified by its own id.
- Upon disconnection, sockets leave all the channels they were part of automatically, and no special teardown is needed on your part.
- In some cases, you might want to emit events to sockets in Socket.IO namespaces / rooms from outside the context of your Socket.IO processes.
- There are several ways to tackle this problem, like implementing your own channel to send messages into the process.
- To facilitate this use case, we created two modules:
  1. socket.io-redis
  1. socket.io-emitter

## Socket.io Emit Cheatsheet

[Link to Cheatsheet](https://socket.io/docs/emit-cheatsheet/)

[Back to code 401 notes](../401-Javascript.md)