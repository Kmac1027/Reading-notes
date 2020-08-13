
# Read: 06 - JS Object Literals; The DOM

## Understanding The Problem Domain Is The Hardest Part Of Programming

- link to article - https://simpleprogrammer.com/understanding-the-problem-domain-is-the-hardest-part-of-programming/
-  understanding the problem is the most critical piece to the equation. It is very difficult to solve a problem before you know the question.  It’s like buzzing in on Jeopardy before you hear the clue and shouting out random questions.

## From the Duckett JS book

### Chapter 3: Object Literals (p1 00-105)

- object litteral is a variable that has key: values and functions (called methods when inside an object litteral)
- object litterals can hold anything from...
  1. strings
  1. boolean
  1. functions
  1. numbers

### Chapter 5: Document Object Model

- the Document Object Model (DOM) specifies how browsers should create a model of an HTML page and how Javascript can access and update the contents of the webpage while it is in the browser window
- the DOM tree is the model of a webpage
- DOM tree has 4 types of **Nodes**
  1. Document Nodes
  1. Element Nodes
  1. Attribute Nodes
  1. Text Nodes
- you can select element nodes by their 
  1. ID or class attributes,
  1. tag name
  1. CSS selector syntax
- When a DOM query can return mnore than one Node, it will always remain a node list
- from an element nodeyou can access and update its content using properties such as textcontent and innerHTML, or using the DOM manipulation techniques
- an element node can contain multiple text nodes and child elements that are siblings of eachother
- Browsers offer tools for viewing the DOM tree

[Back to code 201 notes](201.md)