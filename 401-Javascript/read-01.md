# Readings: Node Ecosystem, TDD, CI/CD

### Describe (in plain English) what Array.map() does

- Array.map() will run a function over the given array elements and return a new array

### Describe (in plain English) what Array.reduce() does

- Array.reduxe() does a lot of different stuff, it starts with an accumulator and then runs a function on the given input resulting in a single output value.

### Provide code snippets showing how to use superagent() to fetch data from a URL and log the result With normal Promise .then() syntax, and Again with async / await syntax

- normal promis
```
superagent.get(url)
    .set('Authorization', Key)
    .then(results => {
      let items = JSON.parse(results.text).items
```

- async/await

```
function apiCall(form) {
   async superagent.get(url)
    .set('Authorization', longKey)
    .then(results => {
      let items = JSON.parse(results.text).items
    }

    function getDataHandler(request, response) {
  let today = todaysDate();
  await let arrayOfresultsForm1 = apiCall('hogWCP3L');
    }
```


### Explain promises as though you were mentoring a Code 301 level student

- a promis is when you have a piece of code that will take a long time to finish and thus it makes a "promis" to do the said function when it completes runing that code, this is how to deal with javascript reading top to bottom and skipping over code taht may take longer to fulfill such as an API call

### Are all callback functions considered to be Asynchronous? Why or Why Not?

- no they are not, call backs that you call yourself are regular function calls thus making them synchronous, however they can be Asynchronous if they are a part of requesting outside information, such as an AJAX call.

### Notes on NodeJS and npm can be found in Code 301 notes

[Link to nodeJS docs](https://nodejs.org/en/docs/)
[Link to npm docs](https://docs.npmjs.com/)