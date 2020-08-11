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



[Back to code 201 notes](201.md)