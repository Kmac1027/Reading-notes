# Read: 01 - SMACSS and Responsive Web Design

## Shay Howe’s intro to RWD

### Responsive Web Design

- Responsive web design is the practice of building a website suitable to work on every device and every screen size, no matter how large or small, mobile or desktop.
- Responsive web design is focused around providing an intuitive and gratifying experience for everyone
- check out this book by Ethan Marcotte, the man who coined the term Responsive Web Design: https://abookapart.com/products/responsive-web-design

### Responsive vs. Adaptive vs. Mobile

- Responsive - Responsive generally means to react quickly and positively to any change
- Adaptive - easily modified for a new purpose or situation
- Mobile - generally means to build a separate website commonly on a new domain solely for mobile users.

### Flexible Layouts

- Responsive web design is broken down into three main components
  1. Flexible Layouts
  1. Media Queries
  1. Flexible Media
- Flexible layouts do not advocate the use of fixed measurement units
- The formula is based around taking the target width of an element and dividing it by the width of it’s parent element. The result is the relative width of the target element.
```
target ÷ context = result
```
### Flexible Grid

- Let’s see how this formula works inside of a two column layout. Below we have a parent division with the class of container wrapping both the section and aside elements. The goal is to have have the section on the left and the aside on the right, with equal margins between the two. Normally the markup and styles for this layout would look a bit like the following.
- HTML
```
<div class="container">
  <section>...</section>
  <aside>...</aside>
</div>

```
- CSS
```
.container {
  width: 538px;
}
section,
aside {
  margin: 10px;
}
section {
  float: left;
  width: 340px;
}
aside {
  float: right;
  width: 158px;
}
```
- Using the flexible grid formula we can take all of the fixed units of length and turn them into relative units. In this example we’ll use percentages but em units would work equally as well. Notice, no matter how wide the parent container becomes, the section and aside margins and widths scale proportionally.

```
section,
aside {
  margin: 1.858736059%; /*  10px ÷ 538px = .018587361 */
}
section {
  float: left;
  width: 63.197026%;    /* 340px ÷ 538px = .63197026 */   
}
aside {
  float: right;
  width: 29.3680297%;  /* 158px ÷ 538px = .293680297 */
}

```
### Media Queries

- Media queries were built as an extension to media types commonly found when targeting and including styles. Media queries provide the ability to specify different styles for individual browser and device circumstances, the width of the viewport or device orientation for example.
- Initializing Media Queries
  1. the @media rule inside of an existing style sheet
  1. importing a new style sheet using the @import rule
  1. linking to a separate style sheet from within the HTML document
- Logical Operators in Media Queries
  1. AND
  1. NOT
  1. ONLY
- Media Features in Media Queries - Media features identify what attributes or properties will be targeted within the media query expression.
- Height & Width Media Features

### Mobile first

- mobile first -  includes using styles targeted at smaller viewports as the default styles for a website, then use media queries to add styles as the viewport grows.
- downloading unnecessary media assets can be stopped by using media queries.

### Flexible Media

- flexible media -  As viewports begin to change size media doesn’t always follow suit. Images, videos, and other media types need to be scalable, changing their size as the size of the viewport changes.
- One quick way to make media scalable is by using the max-width property with a value of 100%. Doing so ensures that as the viewport gets smaller any media will scale down according to its containers width.
-  max-width property doesn’t work well for all instances of media, specifically around iframes and embedded media. such as Youtube
 - to work around this - To get embedded media to be fully responsive, the embedded element needs to be absolutely positioned within a parent element. The parent element needs to have a width of 100% so that it may scale based on the width of the viewport. The parent element also needs to have a height of 0 to trigger the hasLayout mechanism within Internet Explorer

 ## All About Floats

 ### What is FLOAT
 - Float is a CSS positioning property
 - Aside from the simple example of wrapping text around images, floats can be used to create entire web layouts.
- Flexbox and Grid are much stronger tools for creating web page layout
- refer to 201 notes for more indepth notes on float

## Don’t Overthink It Grids

### Context

- A block level element is as wide as the parent it’s inside (width: auto;). We can think of it as 100% wide. The wrapper for a grid probably don’t have much to do with semantics, it’s just a generic wrapper, so a div is fine.
```
<div class="grid">
  <!-- 100% wide -->
</div>
```
- Columns - Let’s start with a practical and common need: a main content area being 2/3 the width and a sidebar being 1/3 the width. We just make two column divs with appropriate class names.
```
<div class="grid">
  <div class="col-2-3">
     Main Content
  </div>
  <div class="col-1-3">
     Sidebar
  </div>
</div>
```
- To make them next to each other, we just need to float them and apply widths. We can select both like this:
```
[class*='col-'] {
  float: left;
}
```
- and individual width like this:
```
.col-2-3 {
  width: 66.66%;
}
.col-1-3 {
  width: 33.33%;
}
```
- Clearing Context
```
.grid:after {
  content: "";
  display: table;
  clear: both;
}
```
- Gutters - The first step toward this is using box-sizing: border-box;. I like using it on absolutely everything.
```
*, *:after, *:before {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
```
- The second step is applying a fixed padding to the right side of all columns except the last one.
```
[class*='col-'] {
  padding-right: 20px;
}
[class*='col-']:last-of-type {
  padding-right: 0;
}
```
 - Outside Gutters

 ### More Column choices

```
.col-1-2 {
  width: 50%;
}
.col-1-4 {
  width: 25%;
}
.col-1-8 {
  width: 12.5%;
}
```
- Sass
```
* {
  @include box-sizing(border-box);
}

$pad: 20px;

.grid {
  background: white;
  margin: 0 0 $pad 0;
  
  &:after {
    /* Or @extend clearfix */
    content: "";
    display: table;
    clear: both;
  }
}

[class*='col-'] {
  float: left;
  padding-right: $pad;
  .grid &:last-of-type {
    padding-right: 0;
  }
}
.col-2-3 {
  width: 66.66%;
}
.col-1-3 {
  width: 33.33%;
}
.col-1-2 {
  width: 50%;
}
.col-1-4 {
  width: 25%;
}
.col-1-8 {
  width: 12.5%;
}

/* Opt-in outside padding */
.grid-pad {
  padding: $pad 0 $pad $pad;
  [class*='col-']:last-of-type {
    padding-right: $pad;
  }
}
```
- Modules - It feels nice breaking up content into bits this way. The bonus side effect being that each module can have padding of it’s own, keeping text away from the edges of the grid.
```
<div class="grid">
  <div class="col-2-3">
     <article class="module">
        stuff
     </article>
     <article class="module">
        stuff
     </article>
  </div>
  <div class="col-1-3">
    <aside class="module">
       Sidebar stuff. Sub modules?
    </aside>
  </div>
</div>
```

## Scalable and Modular Architecture for CSS

### What is SMACSS

- SMACSS (pronounced “smacks”) - a way to examine your design process and as a way to fit those rigid frameworks into a flexible thought process. It is an attempt to document a consistent approach to site development when using CSS.
- read about it in this online book - http://smacss.com/book/
