# Read: 11 - EJS

## youtube videos

- **EJS** is a simple templating language that lets you generate HTML markup with plain JavaScript. No religiousness about how to organize things. No reinvention of iteration and control-flow. It's just plain JavaScript.

- [Link to Youtube Videos](https://www.youtube.com/playlist?list=PL7sCSgsRZ-slYARh3YJIqPGZqtGVqZRGt)

- partials are natice to EJS like a nav bar or reuasble piece of text

-[EJS Docs](https://ejs.co/)

## EJS tutorial

- [Link to article](https://scotch.io/tutorials/use-ejs-to-template-your-node-application)
- [Link to source code for the article](https://github.com/scotch-io/node-ejs)

- package.json will hold our Node application information and the dependencies we need (express and EJS). server.js will hold our Express server setup, configuration. We'll define our routes to our pages here.
- Here we define our application and set it to show on port 8080. We also have to set EJS as the view engine for our Express application using app.set('view engine', 'ejs');. Notice how we send a view to the user by using res.render(). It is important to note that res.render() will look in a views folder for the view. So we only have to define pages/index since the full path is views/pages/index.
- Partials - reused code

### Using EJS Partials

- We have our partials defined now. All we have to do is call them in the files that we need them. Let's go into index.ejs and about.ejs and use them in there. We will also define the full width and sidebar layouts here using the good old Bootstrap grid. Using Partials The syntax to use an EJS partial is: <% include FILENAME %>. The path to the partial is relative to the current file.

- Currently, EJS doesn't support the ability to have layouts. So far we have just brought in other partials, but not really used layouts the way we would expect templating to work (extending a layout file and passing a view file into that). There have been projects in the past to try to bring templating to EJS. The two main projects are EJS Locals and EJS Express Layouts. These provide the ability to define different layouts like a sidebar layout and a full width layout and then call those on the fly. Sadly, EJS Locals is no longer maintained and EJS Express Layouts doesn't work with Express 4 at the time of this writing. Hopefully that will change in the future.

- EJS let's us spin up quick applications when we don't need anything too complex. By using partials and having the ability to easily pass variables to our views, we can build some great applications quickly.

[Back to code 301 notes](../301.md)