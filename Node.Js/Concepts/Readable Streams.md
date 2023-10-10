
In more realistic scenarios, data isn’t processed all at once but rather sequentially, piece by piece, in what is known as a _stream_.

Streaming data is often preferable since you don’t need enough RAM to process all the data at once nor do you need to have all the data on hand to begin processing it.

One of the simplest uses of streams is reading and writing to files line-by-line. To read files line-by-line, we can use the `.createInterface()` method from the `readline` core module.

`.createInterface()` returns an `EventEmitter` set up to emit `'line'` events

```js
const readline = require('readline');  
const fs = require('fs');  
  
const myInterface = readline.createInterface({  
  input: fs.createReadStream('text.txt')  
});  
  
myInterface.on('line', (fileLine) => {  
  console.log(`The line read: ${fileLine}`);  
});
```

- We require in the `readline` and `fs` core [modules](https://www.codecademy.com/resources/docs/javascript/modules).
- We assign to `myInterface` the returned value from invoking `readline.createInterface()` with an object containing our designated `input`.
- We set our `input` to `fs.createReadStream('text.txt')` which will create a stream from the **text.txt** file.
- Next we assign a listener callback to execute when `line` [events](https://www.codecademy.com/resources/docs/javascript/events) are emitted. A `'line'` event will be emitted after each line from the file is read.
- Our listener callback will log to the console `'The line read: [fileLine]'`, where `[fileLine]` is the line just read.