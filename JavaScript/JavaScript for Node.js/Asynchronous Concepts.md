
synchronous code (blocking I/O), and [asynchronous code](https://nodejs.org/en/docs/guides/blocking-vs-non-blocking/) (non-blocking I/O).
### Promises

A [_Promise_](https://www.codecademy.com/courses/asynchronous-javascript/lessons/promises/exercises/introduction) is a JavaScript object that represents the eventual outcome of an asynchronous operation. A `Promise` has three different outcomes: **pending** (the result is undefined and the expression is waiting for a result), **fulfilled** (the promise has been completed successfully and returned a value), and **rejected** (the promise did not successfully complete, the result is an error object)

**Example**:

new `Promise` is being defined and is passed a function that takes two arguments, a *fulfilled* condition, and a *rejected* condition.

We then log the returned value of the `Promise` to the console and chain a `.catch()` method to handle errors.

```javascript
// Creating a new Promise and saving it to the testLuck variable. Two arguments are being passed, one for when the promise resolves, and one for if the promise gets rejected.  
const testLuck = new Promise((resolve, reject) => {  
  if (Math.random() < 0.5) {   
    resolve('Lucky winner!')  
  } else {  
    reject(new Error('Unlucky!'))  
  }  
});  
  
testLuck.then(message => {  
  console.log(message) // Log the resolved value of the Promise  
}).catch(error => {  
  console.error(error) // Log the rejected error of the Promise  
});
```

### Async/Await

The [`async...await` syntax](https://www.codecademy.com/courses/asynchronous-javascript/lessons/async-await/exercises/introductio) allows developers to easily implement `Promise`-based code.
The keyword `async` used in conjunction with a function declaration creates an _async function_ that returns a `Promise`.
Async functions allow us to use the keyword `await` to block the event loop until a given `Promise` resolves or rejects.
The `await` keyword also allows us to assign the resolved value of a `Promise` to a variable.

**Example**:

an asynchronous arrow expression is defined with the `async` keyword. In the function body we are creating a new `Promise` which passes a function that is executed after 5 seconds, we `await` the `Promise` to resolve and save the value returned to `finalResult`, and the output of the `Promise` is logged to the console.

```javascript
// Creating a new promise that runs the function in the setTimeout after 5 seconds.  
const newPromise = new Promise((resolve, reject) => {  
  setTimeout(() => resolve("All done!"), 5000);  
});  
  
// Creating an asynchronous function using an arrow expression and saving it to a the variable asyncFunction.  
const asyncFunction = async () => {  
  // Awaiting the promise to resolve and saving the result to the variable finalResult.  
  const finalResult = await newPromise;  
      
  // Logging the result of the promise to the console  
  console.log(finalResult); // Output: All done!  
}  
  
asyncFunction();
```

### `setInterval()` and `setTimeout()`

The [`setInterval()` function](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setInterval) executes a code block at a specified interval, in milliseconds.
The `setInterval()` function requires two arguments:
the *name of the function* (the code block that will be executed), and the *number of milliseconds* (how often the function will be executed). Optionally, we can pass additional arguments which will be supplied as parameters for the function that will be executed by `setInterval()`. The `setInterval()` function will continue to execute until the `clearInterval()` function is called or the node process is exited.

**Example**:
the `setInterval()` function in the `showAlert()` function will display an alert box every 5000 milliseconds

```javascript

// Defining a function that instantiates setInterval  
const showAlert = () => {  
  // Calling setInterval() and passing a function that shows an alert every 5 seconds.  
  setInterval(() => {  
    alert('I show every 5 seconds!')  
  }, 5000);  
};  
  
// Calling the newInterval() function that calls the setInterval  
showAlert();
```

The [`setTimeout()` function](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/setTimeout) executes a code block after a specified amount of time (in milliseconds) and is only executed once. The `setTimeout()` function accepts the same arguments as the `setInterval()` function. Using the `clearTimeout()` function will prevent the function specified from being executed. In the code block below, a function named `showTimeout()` is declared as an arrow expression. The `setTimeout()` function is then defined and displays an alert box after 5 seconds.

```javascript

// Defining a function that calls setTimeout  
const showTimeout = () => {  
  // Calling setTimeout() that passes a function that shows an alert after 5 seconds.  
  setTimeout(() => {  
    alert('I only show once after 5 seconds!');  
  }, 5000);  
};  
  
// Calling the showTimeout() function  
showTimeout();
```