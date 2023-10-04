
input is data provided to the computer

`console.log()` we prompt the computer to output information to the console.

In the Node environment, the console is the terminal, and the `console.log()` method is a “thin wrapper” on the `.stdout.write()` method of the `process` object. `stdout` stands for standard output.

In Node, we can also receive input from a user through the terminal using the `stdin.on()` method on the `process` object:
 ```js
 process.stdin.on('data', (userInput) => {  
  let input = userInput.toString()  
  console.log(input)  
});
```

Here, we were able to use `.on()` because under the hood `process.stdin` is an instance of `EventEmitter`.

When a user enters text into the terminal and hits enter, a `'data'` event will be fired and our anonymous listener callback will be invoked.

The `userInput` we receive is an instance of [the Node `Buffer` class](https://nodejs.org/api/buffer.html#buffer_buffer), so we convert it to a string before printing.