
When running JavaScript code on a browser, it’s important for a script to have only limited access to a user’s filesystem.

This technique of isolating some applications from others is known as _sandboxing_. Sandboxing protects users from malicious programs and invasions of privacy.

The Node `fs` core module is an API for interacting with the **f**ile **s**ystem. It was modeled after the [POSIX](https://en.wikipedia.org/wiki/POSIX) standard for interacting with the filesystem

Each method available through the `fs` module has a synchronous version and an asynchronous version.

One method available on the `fs` core module is the `.readFile()` method which **read**s data from a provided **file**:

```js
const fs = require('fs');  
  
let readDataCallback = (err, data) => {  
  if (err) {  
    console.log(`Something went wrong: ${err}`);  
  } else {  
    console.log(`Provided file contained: ${data}`);  
  }  
};  
  
fs.readFile('./file.txt', 'utf-8', readDataCallback);
```

Explanation: 

- We required in the `fs` core module.
- We define an error-first callback function which expects an error to be passed as the first argument and `data` as the second. If the error is present, the function will print `Something went wrong: ${err}`, otherwise, it will print `Provided file contained: ${data}`.
- We invoked the `.readFile()` method with three arguments:
    1. The first argument is a string that contains a path to the file **file.txt**.
    2. The second argument is a string specifying the file’s [character encoding](https://en.wikipedia.org/wiki/Character_encoding) (usually ‘utf-8’ for text files).
    3. The third argument is the callback function to be invoked when the asynchronous task of reading from the file system is complete. Node will pass the contents of **file.txt** into the provided callback as its second argument.