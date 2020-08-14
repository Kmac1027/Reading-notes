# Read: 10 - JS Debugging

## Duckett JS

### Chapter 10: Error Handling and Debugging (p. 449)

- Order of Execution - knowing the order in which scripts are processed can help you track down errors in your code
- **Execution Contexts** - Javascript interpreter uses the concept of execution contexts, there is one globall and each funciton crates a new execution context, they correspond to varriable scope
- the stack - javascript interpreter processes one line of code at a time, when the statment needs data from another function it stacks the new function on top fo the current
- 
- If you understand execution context (which have two tages) and stacks, you are more likely to find the error in your code
- Debugging is the proccess of finding errors. It involves a process of deduction
- The Console helps narrow down the area in which the error is located, so you can try to find the exact error
- Javascript has 7 different types of errors. Each creates its own error object, which can tell you it's line number and gives a description of the error
- If you know that you may get an error, you can handel it gracfully using the **Try, Catch, Finally** statements. Use them to give your users helpful feedback/

[Back to code 201 notes](../201.md)