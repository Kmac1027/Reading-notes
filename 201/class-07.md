# Read: 07 - HTML Tables; JS Constructor Functions

## Domain Modeling

- link to article - https://github.com/codefellows/domain_modeling#domain-modeling
- Domain modeling is the process of creating a conceptual model in code for a specific problem
- object-oriented model - An entity that stores data in properties and encapsulates behaviors in methods
- tips:
  1. When modeling a single entity that'll have many instances, build self-contained objects with the same attributes and behaviors.
  1. Model its attributes with a constructor function that defines and initializes properties.
  1. Model its behaviors with small methods that focus on doing one job well.
  1. Create instances using the new keyword followed by a call to a constructor function.
  1. Store the newly created object in a variable so you can access its properties and methods from **outside**
  1. Use the this variable within methods so you can access the object's properties and methods from **inside**.
- example from article

```
var EpicFailVideo = function(epicRating, hasAnimals) {
  this.epicRating = epicRating;
  this.hasAnimals = hasAnimals;
}

EpicFailVideo.prototype.generateRandom = function(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

var parkourFail = new EpicFailVideo(7, false);
var corgiFail = new EpicFailVideo(4, true);

console.log(parkourFail.generateRandom(1, 5));
console.log(corgiFail.generateRandom(1, 5));
```

## Ducket HTML

### Chapter 6: Tables

- Tables represent information in a grid format.

```
<table> - creates the table
<tr></tr> - indicates the start of each row
<td></td> - represents each cell
<th> - just like a <tr> element but its purpose is the represent a heading for either a colum of a row

colspan="number" - can be in <th> or <td> used to stretch accross more than one colum
rowspan="number" = used in the <th> or <td> to indicate how many rows a cell should span
for longer tables you can split the table into <thead> <tbody> <tfoot>
```

## Ducket JS

### Chapter 3: Functions, Methods, and Objects(p. 106-144)

- an object is a series of variables and functions that represent something from the real world around you
- Example

```
function Person(first, last, age, eye) {
  this.firstName = first;
  this.lastName = last;
  this.age = age;
  this.eyeColor = eye;
}
```

- It is considered good practice to name constructor functions with an upper-case first letter.
- **this.** is a keyword, not a variable. when placed before a variable it is making reference to the variable that is within that object
- in objects variables are known as properties and functions are known as methods
- web browsers impliment objects that represent both the browser window and the document loaded into the browser window
- Javascript has several built in objects, such as

```
String
Number
Math
Date
```

- Arrays and objects can be used to create complex data sets and they both can contain the other

[Back to code 201 notes](../201.md)