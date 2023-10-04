The Node environment’s `error` module has all the standard JavaScript errors such as `EvalError`, `SyntaxError`, `RangeError`, `ReferenceError`, `TypeError`, and `URIError` as well as the JavaScript `Error` class for creating new error instances.

we can generate errors and `throw` them, and, with synchronous code in Node, we can use [error handling](https://www.codecademy.com/learn/javascript-errors-debugging/modules/errors-and-error-handling) techniques such as `try...catch` statements.

the `error` module is within the global scope—there is no need to import the module with the `require()` statement.

Many asynchronous Node APIs use -
_error-first callback functions_—callback functions which have an error as the first expected argument and the data as the second argument.

If the asynchronous task results in an error, it will be passed in as the first argument to the callback function. If no error was thrown, the first argument will be `undefined`

example: 
```js
const errorFirstCallback = (err, data)  => {  
  if (err) {  
    console.log(`There WAS an error: ${err}`);  
  } else {  
    // err was falsy  
    console.log(`There was NO error. Event data: ${data}`);  
  }  
}
```