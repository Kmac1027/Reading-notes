# Read: 08 - More CSS Layout

### Chapter 15: Layout (notes from class 04 reading comtinued)

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
  
- < div > elements are often used as containing elements to group together sections of a page
- browsers display pages in normal flow unless you specify relative, absolute, or fixed positioning
- the float propertyt moves elements to the right or left of the page and can be used to create multi column layouts
- pages can be fixerd width or liquid (stretchy) layouts
- designers keep pages within 960-1000 pixels wide, and indicate what the site is about within the top 600 pixels
- grids help create professional and flexible designs
- CSS framworks provide rules for common tasks
- you can have multiple CSS files on one page.

[Back to code 201 notes](201.md)