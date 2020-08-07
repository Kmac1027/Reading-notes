# Read: 05 - HTML Images; CSS Color & Text

## Duckett HTML

### chapter 5: Images

- keep all your images to be used in your site in their own directory
- images are added with the img tag

```
<img src="pathway to where the image is stored" alt="provides a text description" title="provides additional information about the image when the user hovers over the image">
```

- 3 rules to remember when creating images for your website
  1. save images in the right format
  1. save images at the right size
  1. measure images in pixels
- use .jpg format when an image has many colors
- use .gif or .png when images have few colors or large areas of same color
- the images you use should be saved at the same height and width you plan to use them at on your page
- when sizing an image for the screen always set dimentions in pixles
- < figure > element lets you keep an image and its caption in the same element so that the two are associated togehter
- < figcaption > element adds a caption to an image

```
<figure>
<img src="  " alt= " " >
<figcaption> add caption here</figcaption>
</figure>
```

### Chapter 11: Color

- the color property in CSS allows you to specify the color of text inside an element, it can be assigned in 3 ways
  1. RGB values
  1. Hex Code
  1. Color Names
- background-color sets the color of the background, the same assinging can be used as the regular color property
- opacity - you can specify the opacity of an element and its child elements
- the opacity can be set by a number 0.0 - 1.0 (0.5 is 50% and so on)
- HSL
  1. Hue
  1. Saturation
  1. Lightness
- HSLA - the same as HSL but the A allows us to assign transparency, again, with the 0.0 - 1.0 percentages

### Chapter 12: Text

- when chosing a typeface it is important to know that a browser will opnly display it if it is installed on the users computer
- Specifying Typefaces
  - font-family:  allows you to specify the typeface that should be sued  for any text inside the element to which a CSS rules applies
- font-size: specify the size of the font
- font-weight: can determin how **BOLD** you want the text
- font-style: creates italic text, there are three valiues it can have
  1. normal
  1. italic
  1. oblique
- text-transform: changes the case of text giving it one of the following values
  1. uppercase
  1. lowercase
  1. capitalize
- tect-decoration: allows you to specify the following values
  1. none
  1. underline
  1. overline
  1. line-through
  1. blink
- line-height: sets the height of an entire line of text
- letter-spacing: controls the sopace between each leter
- word-spacing: controls the space between each word
- text align: controls the alignment of text, it can take one of four values
  1. left
  1. right
  1. center
  1. justify
- vertical-align: NOT intended to allow you to vertically align text. it is used with inline elements such as < img > or < strong > . when used with these elements it works as an align attribute in HTML
  1. baseline
  1. sub
  1. super
  1. top
  1. text-top
  1. middle
  1. bottom
  1. text-bottom
  1. (it can also take length, specified in pixels or ems) or a percentage of the line height
- text-indent: indent the first line of text within an element
- text-shadow: creates a drop shadow (dark version of the word just behind it and slightly off set)
- pseudo-elements: you specify a pseudo-element at the end of the selector
  - :first-letter
  - :first-line
- pseudo-classes: 
  - :link allows you to specify the color and style of a link that has not been visited
  - :visited allows you to specify the color and style of a link that has been visited
  - :hover allows you to set the color and style when a user hovers over an element with their mouse
  -  :active set the color and style of an element when it is being activated by the user
  - :focus is applied when an element has focus. Any element you can interact with, such as a link or prompt box. focus occurs when the browser discovers that you are ready to interact with an element

[Back to code 201 notes](201.md)