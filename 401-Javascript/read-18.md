# Readings 18: Socket.io

## Web Sockets

[Link to Wikipedia Article](https://en.wikipedia.org/wiki/WebSocket)

- WebSocket is a computer communications protocol, providing full-duplex communication channels over a single TCP connection. The WebSocket protocol was standardized by the IETF as RFC 6455 in 2011, and the WebSocket API in Web IDL is being standardized by the W3C.

## Socket.io Tutorial

[Link to Article](https://www.tutorialspoint.com/socket.io/)

- Socket.IO enables real-time bidirectional event-based communication. It works on every platform, browser or device, focusing equally on reliability and speed. Socket.IO is built on top of the WebSockets API (Client side) and Node.js. It is one of the most depended upon library on npm (Node Package Manager).
- Socket.IO is a JavaScript library for real-time web applications. It enables real-time, bi-directional communication between web clients and servers. It has two parts: a client-side library that runs in the browser, and a server-side library for node.js. Both components have an identical API.

### Audience

- This tutorial has been created for anyone who has a basic knowledge of HTML, Javascript and Node.js work. After completing this tutorial, the reader will be able to build moderately complex real-time websites, back-ends for mobile applications and push notification systems.

### Prerequisites

- The reader should have a basic knowledge of HTML, JavaScript and Node.js. If the readers are not acquainted with these, we will suggest them to go through these tutorials first. We will be using Express to ease creating servers; it is not a prerequisite though.

### Real-time applications

- A real-time application (RTA) is an application that functions within a period that the user senses as immediate or current.
  1. Instant messengers − Chat apps like Whatsapp, Facebook Messenger, etc. You need not refresh your app/website to receive new messages.
  1. Push Notifications − When someone tags you in a picture on Facebook, you receive a notification instantly.
  1. Collaboration Applications − Apps like google docs, which allow multiple people to update same documents simultaneously and apply changes to all people's instances.
  1. Online Gaming − Games like Counter Strike, Call of Duty, etc., are also some examples of real-time applications.

## Socket.io vs Web Sockets

[Link to Article](https://www.educba.com/websocket-vs-socket-io/)

- **WebSocket** is the communication Protocol which provides bidirectional communication between the Client and the Server over a TCP connection, WebSocket remains open all the time so they allow the real-time data transfer. When clients trigger the request to the Server it does not close the connection on receiving the response, it rather persists and waits for Client or server to terminate the request.
- **Socket.IO** is a library which enables real-time and full duplex communication between the Client and the Web servers. It uses the WebSocket protocol to provide the interface. Generally, it is divided into two parts, both WebSocket vs Socket.io are event-driven libraries

[](https://cdn.educba.com/academy/wp-content/uploads/2018/11/WebSocket-protocol-schema.png)

- Why do we need websocket?
  1. It provides the full duplex communication which helps in persisting the connection established between the Client and the Web Server.
  1. It also lives up to the standards and provides the accuracy and efficiency stream events to and from with negligible latency.
  1. WebSocket removes the overhead and reduce complexity.
  1. It makes real-time communication effortless and efficient.

## Socket.io Documentation

[link to documentation](https://socket.io/docs/)

## Socket.io Server API

[Link to API](https://socket.io/docs/server-api)

## Socket.io Client API

[Link to API](https://socket.io/docs/client-api)

## Socket Testing Tool

[Link to testing Tool](https://amritb.github.io/socketio-client-tool/)


[Back to code 401 notes](../401-Javascript.md)