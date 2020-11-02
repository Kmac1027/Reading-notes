
# Readings: Event Driven Applications

## Review, Research, and Discussion

1. Why is access control important?
1. Describe an application that would need access control.
1. What is a role used for?
1. Why is role based access control more scalable than discretionary or mandatory access control?

## Document the following Vocabulary Terms

- Authorization
- Role Based Access Control
- Capabilities

## Event Driven Programming

[Link to Article](https://www.digitalocean.com/community/tutorials/nodejs-event-driven-programming)

### Event-Driven Programming in Node.js

- Event-Driven Programming is a logical pattern that we can choose to confine our programming within to avoid issues of complexity and collision
- Every time you interact with a webpage through it’s user interface, an event is happening. When you click a button a click event is triggered. When you press a key a keydown event is triggered. These events have associated functions that, when triggered, are executed to make a change to the user interface in some way.
- Event-Driven Programming makes use of the following concepts:
  1. An Event Handler is a callback function that will be called when an event is triggered.
  1. A Main Loop listens for event triggers and calls the associated event handler for that event.

### EventEmitter

- Node.js natively provides us with a useful module called EventEmitter that allows us to get started incorporating Event-Driven Programming in our project right away. Of course, creating our own version of EventEmitter wouldn’t be much of a challange, and in fact there are several modules published on npm such as EventEmitter2 and EventEmitter3 which promise a faster performance than the native EventEmitter.
- We access the EventEmitter class through the events module. Once imported we’ll need to create a new object from the class to start using it.

```js
const EventEmitter = require('events').EventEmitter;
const myEventEmitter = new EventEmitter;
```

- Imagine we’re creating a chat room. We want to alert everyone when a new user joins the chat room. We’ll need an event listener for a userJoined event. First, we’ll write a function that will act as our event listener, then we can use EventEmitters on method to set the listener.

```js
const EventEmitter = require('events').EventEmitter;
const chatRoomEvents = new EventEmitter;

function userJoined(username){
  // Assuming we already have a function to alert all users.
  alertAllUsers('User ' + username + ' has joined the chat.');
}

// Run the userJoined function when a 'userJoined' event is triggered.
chatRoomEvents.on('userJoined', userJoined);
```

- The next step would be to make sure that our chat room triggers a userJoined event whenever someone logs in so that our event handler is called. EventEmitter has an emit method that we we use to trigger the event. We would want to trigger this event from within a login function inside of our chatroom module.

```js
function login(username){
  chatRoomEvents.emit('userJoined', username);
}
```

### Removing Listeners

- To remove event listeners in EventEmitter we can use the removeListener or removeAllListeners method. It’s important to note that in the EventEmitter that comes built-in with Node you must pass a reference to the exact function you wish to remove when using the removeListener method. This means wherever you wish to remove the event, you’ll need to make sure the function is able to be referenced from that place in your code. For this reason it is often best to name your event handling functions and declaring them before you register the event listener, as opposed to leaving them anonymous.
-In the following example, it would be a challenge to remove the listener for the message event from outside of the userJoined function due to the fact that it’s an anonymous function declared within a closure. In this case the only place we would be able to directly reference this method would be in the EventEmitter Object itself. This would be impractical if we ever had more than one listener registered to a single event as we would then have to figure out a way to decipher which of the listeners is our intended target.

```js
// not good code
const EventEmitter = require('events').EventEmitter;
const chatRoomEvents = new EventEmitter;

function userJoined(username){
  chatRoomEvents.on('message', function(message){
    document.write(message);
  })
}

chatRoomEvents.on('userJoined', userJoined);

// All of that headache can be avoided if we rewrite the code like so:

const EventEmitter = require('events').EventEmitter;
const chatRoomEvents = new EventEmitter;

function displayMessage(message){
  document.write(message);
}

function userJoined(username){
  chatRoomEvents.on('message', displayMessage);
}

chatRoomEvents.on('userJoined', userJoined);

// Now if we want to remove the displayMessage function from the message event’s list of handlers:

chatRoomEvents.removeListener('message', displayMessage);
```

### Object Oriented Programming + Event-Driven Programming

- The Object Oriented approach promotes the idea that all behavior of an individual unit (or object) be handled from code within that unit. Using this approach, applications are built with many different units that all speak to and interact with each other.
-  By registering event listeners we can actually reverse the flow of communication between our objects. Rather than on object needing to reach inside another object to trigger a function, our objects can just emit events and whichever objects are listening to those event will process it in the way they have been told to. The source of an objects behavior is now entirely contained within itself, rather than needing to be accessed by external objects.

## Node docs: events

[Link to the Node documentation](https://nodejs.org/api/events.html)

[Back to code 401 notes](../401-Javascript.md)