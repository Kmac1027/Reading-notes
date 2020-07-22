# Dynamic Web Pages with JavaScript

## Duckett: JavaScript & jQuery, Pages 43 - 69.

- JavaScript determins the behavior of the website and how it is interacted with
- progressive inhancment refers to the approach of using the 3 layers (HTML, CSS, JavaScript) of building web pages

Code Along Practace
```

var today = new date ();
var hourNow = today.getHours();
var greeting;

if (hourNow > 18) {
    greeting = 'Good evening!';
} else if (hourNow > 12) {
    greeting ='Good afternoon!';
} else if (hourNow > 0) {
    greeting = 'welcome!;"  
}

document.write('<h3>' + greeting + '</h3>');
```






[Back Home](README.md)