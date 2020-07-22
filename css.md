# CSS

## Duckett: HTML & CSS, Chapter 10: Introducing CSS

- CSS - Cascading Style Sheet
- CSS os the design side of the website, it dictates how a site should look and feel
- CSS deals with how elements within a HTML file should appear

### Link tags

```
<Link>
```
a link tag lives inside the head of the HTML document and tells the broweser where to find the CSS file to style the page, it is made up of three attributes

- href - path to the css file
- type - specifies the type of document being linked
- rel -  specifies the relationship between the HTML file and the file it is being linked to

```
<link href=" " type=" " rel=" ">
```
does not need a closing tag

### Summary

- CSS treats each element as if it appears inside its own box and uses rules to indicate how that element should look
- rules are made up of selectors (that specify the element the rule applies to) and declerations (that indicate what the elemnts should look like)
- different types of selectors allow you to target your rules at different elements
-  Declerations are made up of two parts: the properties of the element that you want to change, and the values of those properties. 
- CSS rules usually appear in a seperate document although they may also appear within and HTML page

## Duckett: HTML & CSS, Chapter 11: Color

### Forground and background Color

- the color property allows you to specify the color of test  inside an element, there are 3 ways to specify a color
    1. RGB values
    1. Hex Codes
    1. Color Names
- Opacity - (RGBA) specify the opacity of an element with a value between 0.0 and 1.0 (i.e. 0.5 is 50% 0.15 is 15% ect...)
- hsl - deal with the color hue
- hsla - opacity of the hue

### summary

- color brings site to life and evokes reaction
- three ways to specify color, RGB, Hex, Names
- important to hav e enough contrast between text and background color
- RGBA deals with color opacity
- HSL to specify colors an d HSLA for dealing with opacity of those specified colors

[Back Home](README.md)