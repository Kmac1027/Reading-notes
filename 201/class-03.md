# Read: 03 - HTML Lists, CSS Boxes, JS Control Flow

## Ducket HTML

### Chapter 3: Lists

- there are two types of lists
  1. ordered lists: uses numbers
  1. unordered lists: uses bullet points
- both lists will list their items with the ``` <li> ``` tag
 - example
```
<ol> - ordred list
<li> - item
<li> - item
<li> - item
</ol> - end ordered list

<ul> - unordred list
<li> - item
<li> - item
<li> - item
</ul> - end unordered list
```
- lists can be nested inside one another

### Chapter 13" Boxes

- you can create box dimentions with width and height tages
- you can limit width and heith with the example below
```
min-width
max-width
min-height
max-height
```
- border, margin, and padding are all different
  1. border - seperates the edge of one box from another
  1. margin - sit outside the edge of the border
  1. padding - the space between the box and any content within that box
- CSS treats each element as if it was in its own box
- you can use CSS to control the dimentions of the box
- you can hide elements using the display and visibility properties
- you can create image borders and rounded borders

## Ducket Javascript

### Chapter 2: Basic Javascript Instruction

- Refer to [class 02](class-02.md) notes

### Chapter 4: Descisions and Loops, continuation from class 02 notes

- if/else statments checks a condition
- switch statments allows you to compare a value against possible outcomes, and can provide a default option if none match
- due to type coercion, every value in javascript can be treated as if it were true or false
  1. **FALSY** values are trearted as if they are false, they can also be treated as the number 0
  1. **TRUTHY** values are treated as if they are true, almost everuything not in the falsy table can be treated as true
- Loops
  1. a **For** loop is often used to loop throughn the items in an array
  1. a **While** loop will continue to run as long as the variable is true
  1. a **Do While** has the statement in the code block come before the condition, this means they will run at least once, weather the condition is met or not
- all values evaluate to either **TRUTHY** or **FALSY**
- there are 3 types of loops, **For**, **While**, **Do While**

[Back to code 201 notes](../201.md)