# Read: 08 - More CSS Layout

## Ducket HTML

### Chapter 4: Links

- links are the defining feature of the web becuae they allow you to move from one web page to another - enabling the very idea of browsing or surfing
- links are created with the anchor tag
- example
```
<a href=" ">text</a>
```
- the text is the clickable link and the href is the address to where it goes
- relative url is linking to a page on the same site
- absolute url is when you have a link to a different website
- an email link is created ina similar way but you use the mailto: attriburte
```
<a href="mailto:john@example.com">Email John</a>
```
- the target attribute opens a link in a new window
- you can link to other places on the same page using the id tag

### Chapter 15: Layout

- CSS looks at everything as blocks
- block level elements - take up their whole line
- inline elements - flow inbetween surounding text
- a box may be nested inside several other block level elements,the containing element is always the **direct parent** of that element
- controling the position of elements
  1. normal flow - each block level element sits on top of the next
  1. relative positioning - moves an element in relation to where it would have been in normal flow
  1. absolute positioning - box is taken out of normal flow and no longer affects the position of other elements on the page
  1. fixed positioning - a type of absolute positioning that requires the position property to have a value of fixed
  1. floating elements - allows you to take an element in normal flow and place it as far to the left or right of the containing element as possible
- when you move any element from normal flow, boxes can overlap. The **z-index** property allows you to control which box appears on top.
- example
```
h1 {
  z-index: 10;
}
```
- use floats to place elements side by side
- clearing floats - the clear property allows you to say that no element should touch the left or right side of a box, i9t can take the following values
  1. left
  1. right
  1. both
  1. none

#### since this is such a big chapter i am going to finish my notes on a different page at another time and just focus on what i have here for the time being

## Ducket Javascript

### Chapter 3 Functions, Methods, and Objects (first part only p 86-99)

- Functions let you group a series of statements together to perform a specific task
- functiosn store a statment or group of statments so they can be called upon later
- the code in a function will only execute if the function is called
- example

```
function sayhello() {
  document.write('Hello');
}
```

- to call a function you simply write the name of the function

```
sayhello()
```

- variable scope - the location that you decalre a variable will affect where it can be used within your code, i.e. if declared in a function it can only be used in that function unless also declared outside the function
- local variables
- global variables
- Objects group together a set of variables and functions to create a model of something you would recognize from the real world
- in an object variables and functions take on new names
 1. in a object **variables** become known as **properties** and **functions** become known as **methods**


## Article: 6 Reasons for pairing programming

1. Greater efficiency
1. Engaged collaboration
1. Learning from Fellow students
1. Socila Skills
1. Job interview readiness
1. Work environment readiness

- link to article - https://www.codefellows.org/blog/6-reasons-for-pair-programming/

[Back to code 201 notes](201.md)