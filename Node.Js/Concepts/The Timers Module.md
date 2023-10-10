
There are times when we want some of our code to be executed at a specified point in time.

This is what the [`timers` module](https://nodejs.org/api/timers.html#timers_class_immediate) is used for.

`timer` module are global.

You may already be familiar with some timer [functions](https://www.codecademy.com/resources/docs/javascript/functions) such as, [`setTimeout()`](https://www.codecademy.com/resources/docs/javascript/window/setTimeout) and `setInterval()`.

Timer functions in Node.js behave similarly to how they work in front-end JavaScript programs(such as, [`setTimeout()`](https://www.codecademy.com/resources/docs/javascript/window/setTimeout) and `setInterval()`),  but the difference is that they are added to the Node.js [event loop](https://nodejs.org/en/docs/guides/event-loop-timers-and-nexttick/).

This means that the timer functions are scheduled and put into a queue.
This queue is processed at every iteration of the event loop.

If a timer function is executed outside of a module, the behavior will be random (non-deterministic).

The `setImmediate()` function is often compared with the `setTimeout()` function.

When `setImmediate()` is called, it executes the specified callback function after the current ([poll phase](https://nodejs.org/en/docs/guides/event-loop-timers-and-nexttick/#setimmediate-vs-settimeout)) is completed.

 The method accepts two parameters: the *callback function* (required) and *arguments* for the callback function (optional).
 
 If you instantiate multiple `setImmediate()` functions, they will be queued for execution in the order that they were created.
 
```js
setImmediate(() => {  
    console.log('Hello! My name is Codey.')  
});
```
