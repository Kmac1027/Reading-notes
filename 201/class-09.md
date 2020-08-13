# Read: 09 - Forms and Events

## Ducket HTML

### Chapter 7: Forms (p 144-175)

- there are several types of form controls
  1. adding text - text input, password input, and text area
  1. making choices - radio buttons, checkboxes or dropdown boxes
  1. submitting forms - submit buttons, image buttons, and file upload
- a user fills out a form and then presses a submit button to send that information to the server
- < textarea > - creates miltiple line input
- < button > - allows users more control over how their buttons appear, and to allow other elements to appear inside the button (this means you can combine text and images between the openeing and closing button tag)
- types of input
  1. type="text" creates a single line text input
  1. type="password" does the same as input except it stars out the information being typed in
  1. type="radio" allows to use to pick just one of a number of options
  1. type="checkbox" aloows to user to select (and unselect) one or more options
  1. type="file" this looks like a text input box but has a browse button to the side of it that when pressed will allow to use to pick a file on their system to upload
  1. type="submit" sends information to the server
  1. type="image" if you want to use an image for the submit button
  1. type="hidden" for a hidden form control on the page
  1. type="date" creates a date input
  1. type="email" for entering email addresses
  1. type="url" when asking the user for a web page address
  1. type="search" single line text box for seach queries
- < label > - used for IDing forms and wrapping forms in them,
- < fieldset > - grouping related form controls together
- < legend > - comes right after the < fieldset > tag and contains a caption which helps identify the purpose of that group of form controls

### Chapter 14: Lists, Tables & Forms (p 330-357)

- bullet point styles - list-style-type
- images for bullets - list-style-image
- positioning the marker - list-style-positioning
- list shorthand - list-style
- table properties
  1. width
  1. padding
  1. text-transform
  1. letter-spacing, font-size
  1. border-top, border-bottom
  1. text align
  1. background-color
  1. :hover
- list markers can be given different appearances using the list-style-type and list-style image properties
- table cells can have different boarders and spacing in defferent browsers, but there are properties you can use to control them and make them more consistent
- **forms are easier to use if the form controls are vertically aligned using CSS**
- forms benefit from styles that make them feel more interactive

## Ducket Javascript

### Chapter 6: Events (p. 243-292)

- an event is the browsers way of saying "HEY, THIS JUST HAPPENED" your script can then respond to these events
- when an event occurs it is often refered to as having been **Fired** or **Raised**
- events trigger a function or script.
- How events trigger javascript code
  1. select the element node, or nodes, you want the script to respond to
  1. indicate which event on the selected node will trigger the response
  1. state the code you want to run when the event occurs
- bind an event to an element
  1. HTML event handlers **THIS IS NOW CONSIDERED BAD PRACTACE**
  1. Traditional DOM event handlers
  1. DOM level 2 **Event Listeners**
- Event Delegation
- Different types of events
  1. W3C DOM events
  1. HTML5 Events
  1. BOM Events
- Binding is the process of stating which event you are waiting to happen, and which element you are waiting for that event to happen upon
- when an event occurs on an element, it can trigger a Javascript function. When this function then changes the web page in some way, it feels interactive because it has responded to the user
- you canuse event delegation to monitor for events that happen on all of the children of an event
- the most commonly used events are W3C DOM events, although there are others in the HTML5 specifications as well as browsers-specific events.

[Back to code 201 notes](201.md)