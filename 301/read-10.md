# Read: 10 - The Call Stack and Debugging

## The Call Stack defined on MDN

- A call stack is a mechanism for an interpreter (like the JavaScript interpreter in a web browser) to keep track of its place in a script that calls multiple functions — what function is currently being run and what functions are called from within that function, etc.
  1. When a script calls a function, the interpreter adds it to the call stack and then starts carrying out the function.
  1. Any functions that are called by that function are added to the call stack further up, and run where their calls are reached.
  1. When the current function is finished, the interpreter takes it off the stack and resumes execution where it left off in the last code listing.
  1. If the stack takes up more space than it had assigned to it, it results in a "stack overflow" error.

```
function greeting() {
   // [1] Some codes here
   sayHi();
   // [2] Some codes here
}
function sayHi() {
   return "Hi!";
}

// Invoke the `greeting` function
greeting();

// [3] Some codes here
```

1. Ignore all functions, until it reaches the greeting() function invocation.
1. Add the greeting() function to the call stack list.
1. Execute all lines of code inside the greeting() function.
1. Get to the sayHi() function invocation.
1. Add the sayHi() function to the call stack list.
1. Execute all lines of code inside the sayHi() function, until reaches its end.
1. Return execution to the line that invoked sayHi() and continue executing the rest of the greeting() function.
1. Delete the sayHi() function from our call stack list.
1. When everything inside the greeting() function has been executed, return to its invoking line to continue executing the rest of the JS code.
1. Delete the greeting() function from the call stack list.

- In summary, then, we start with an empty Call Stack. Whenever we invoke a function, it is automatically added to the Call Stack. Once the function has executed all of its code, it is automatically removed from the Call Stack. Ultimately, the Stack is empty again.

## The JavaScript Call Stack - What It Is and Why It's Necessary

- The JavaScript engine (which is found in a hosting environment like the browser), is a single-threaded interpreter comprising of a heap and a single call stack. The browser provides web APIs like the DOM, AJAX, and Timers.
- LIFO: When we say that the call stack, operates by the data structure principle of Last In, First Out, it means that the last function that gets pushed into the stack is the first to be pop out, when the function returns.
- Let us take a look at a code sample to demonstrate LIFO by printing a stack trace error to the console.
```
  throw new Error('Stack Trace Error');
}

function secondFunction(){
  firstFunction();
}

function thirdFunction(){
  secondFunction();
}

thirdFunction();
```
- Manage function invocation (call): The call stack maintains a record of the position of each stack frame. It knows the next function to be executed (and will remove it after execution). This is what makes code execution in JavaScript synchronous.
1. It is single-threaded. Meaning it can only do one thing at a time.
1. Code execution is synchronous.
1. A function invocation creates a stack frame that occupies a temporary memory.
1. It works as a LIFO — Last In, First Out data structure.

## JavaScript error messages && debugging

- Reference errors
- Syntax errors
- Range errors
- Type errors

- testing is automatically called since it’s an IIFE (immediately Invoked Function Expression);
- obj variable is declared with the function add (using ES6 shorthand for functions in objects, it would be the same having var obj = { add: add } ;
- the function add is called from the obj variable with two strings has parameters, there are added which makes them “12” in this scenario and then split is called before returning [“1”, “2”];
- the function add is called again, this time with number, the values are added making it 3 but then, split (which is not available for number type variables) is called which makes an error being thrown;

- Handling errors
- About the light blue part of our earliest example of an error message, that shows up like that when we do not handle errors properly, meaning that anything after that error will not be executed. To avoid this we usually try to catch the errors so we can gracefully fallback to a default state of our application in case of an error 

### Tools to avoid runtime errors

1. quokka to evaluate your code as you type
1. eslint to make sure your style guide is consistency and it will grab you an error or two along the way and
1. For those of you looking to make JS a more strong typed experience you can check out stuff like TypeScript (like I said in a previous article, when learning I rather avoid libraries that abstract the core language so I wouldn’t recommend this last one when starting).

[Back to code 301 notes](../301.md)