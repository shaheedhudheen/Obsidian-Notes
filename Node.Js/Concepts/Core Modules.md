*As the program grows bigger, it may contain many lines of code. Instead of putting everything in a single file, modules can be used to separate codes in separate files as per their functionality. This makes the code more organized and easier to maintain.*

_Modularity_ is a software design technique where one program has distinct parts, each providing a single piece of the overall functionality.

These separate [_modules_](https://www.codecademy.com/resources/docs/javascript/modules) come together to build a cohesive whole.

a module is a collection of code located in a file. Instead of having an entire program located in a single file, code is organized into separate files based on the concerns they address. These files can then be included in other files by using the `require()` function.

To save developers from reinventing the wheel each time, Node.js has several built-in modules to perform common tasks efficiently. These are known as the _core modules_.

The core modules are defined within Node.js’s source code and are located in the **lib/** folder.

Core **modules** can be required by passing a string with the name of the module into the `require()` function:

```javascript
// Require in the 'events' core module:  
const events = require('events');
```

Some core modules are actually used inside other core modules. For instance, the `util` module can be used in the `console` module to format messages.

### The Console Module

In Node.js, the terminal is used to send and receive text feedback to and from a program, often for debugging purposes.

in Node.js, the built-in `console` module exports a global `console` object that gives the terminal similar functionality. The `console` object provides many of the same familiar [methods](https://www.codecademy.com/resources/docs/javascript/methods) such as:

- `.log()` — to print messages to the terminal.
- `.assert()` — to print a message to the terminal if the value is falsy.
- `.table()` — to print out a table in the terminal from an object or array

### The Process Module

In computer science, a _process_ is the instance of a computer program that is being executed

 Node has a global `process` object with useful methods and information about the current process.

The `process.env` property is an object which stores and controls information about the environment in which the process is currently running.

For example, the `process.env` object contains a `PWD` property which holds a string with the directory in which the current process is located.

It can be useful to have some `if/else` logic in a program depending on the current environment— a web application in a development phase might perform different tasks than when it’s live to users.

We could store this information on the `process.env`. One convention is to add a property to `process.env` with the key `NODE_ENV` and a value of either `production` or `development`.

```javascript
if (process.env.NODE_ENV === 'development'){  
  console.log('Testing! Testing! Does everything work?');  
}
```

he `process.memoryUsage()` returns information on the CPU demands of the current process. It returns a property that looks similar to this:

```javascript
{ rss: 26247168,  
  heapTotal: 5767168,  
  heapUsed: 3573032,  
  external: 8772 }
```

*_Heap_ can mean different things in different contexts: a heap can refer to [a specific data structure](https://en.wikipedia.org/wiki/Heap_(data_structure)), but it can also refer to a block of [computer memory](https://en.wikipedia.org/wiki/Memory_management).*

`process.memoryUsage().heapUsed` method will return a number representing how many bytes of memory the current process is using.

### `process.argv`

The `process.argv` property holds an array of command line values provided when the current process was initiated.

The first element in the array is the absolute path to Node, which ran the process. 

The second element in the array is the path to the file that’s running. 

The following elements will be any command line arguments provided when the process was initiated

### The OS Module

When developing or debugging an app, it can be helpful to have information about the computer, operating system, and network on which the program is running.

Before Node, this information could not be retrieved using JavaScript due to the language being confined to the browser. 

However, Node.js is a JavaScript runtime, which means it can execute code outside of the browser, and we’re able to get access to much of this information through the `os` core module.

os is not an global object, need to included in the file in order to access 

```js
const os = require('os');
```

With the `os` module saved to the `os` variable, you can call methods like:

- `os.type()` — to return the computer’s operating system.
- `os.arch()` — to return the operating system CPU architecture.
- `os.networkInterfaces()` — to return information about the network interfaces of the computer, such as IP and MAC address.
- `os.homedir()` — to return the current user’s home directory.
- `os.hostname()` — to return the hostname of the operating system.
- `os.uptime()` — to return the system uptime, in seconds.

example: 
```js
const os = require('os');  
  
const local = {    
  'Home Directory': os.homedir(),      
  'Operating System': os.type(),  
  'Last Reboot': os.uptime()  
}
```

we first require the `os` module and store it in a variable, `os`.

Below that, we have an object, `local`,that will hold some information about the user’s computer:
the name of the home directory, the type of operating system, and the time since the computer was last rebooted.

### The Util Module

 Developers sometimes classify outlier [functions](https://www.codecademy.com/resources/docs/javascript/functions) used to maintain code and debug certain aspects of a program’s functionality as _utility functions_.
 
 Utility functions don’t necessarily create new functionality in a program, but you can think of them as internal tools used to maintain and debug your code.

 The Node.js `util` core module contains [methods](https://www.codecademy.com/resources/docs/javascript/methods) specifically designed for these purposes

```js
const util = require('util');
```

you have access to many useful [objects](https://www.codecademy.com/resources/docs/javascript/objects) and methods within the `util` module

One important object is `types`, which provides methods for runtime type checking in Node

```js
const util = require('util');  
  
const today = new Date();  
const earthDay = 'April 22, 2022';  
  
console.log(util.types.isDate(today));  
console.log(util.types.isDate(earthDay));
```

Since `today` is a `Date` object, it returns `true`, and since `earthDay` is a string, it returns `false`!

Another important `util` method is `.promisify()`, which turns [callback functions](https://www.codecademy.com/learn/introduction-to-javascript/modules/learn-javascript-iterators/cheatsheet#:~:text=Callback%20Functions,can%20be%20passed%20as%20arguments.) into [promises](https://www.codecademy.com/learn/introduction-to-javascript/modules/javascript-promises/cheatsheet). 

As you know, [asynchronous programming is essential to Node.js](https://www.codecademy.com/content-items/9abb26ac5476a0967d2675d03fce444c). In the beginning, this asynchrony was achieved using error-first callback functions, which are still very prevalent in the Node ecosystem today.

But since promises are often preferred over [callbacks](https://www.codecademy.com/resources/docs/javascript/callbacks) [and especially nested callbacks](http://callbackhell.com/), Node offers a way to turn these into promises.

Example:
```js
function getUser (id, callback) {  
  return setTimeout(() => {  
    if (id === 5) {  
      callback(null, { nickname: 'Teddy' })  
    } else {  
      callback(new Error('User not found'))  
    }  
  }, 1000)  
}  
  
function callback (error, user) {  
  if (error) {  
    console.error(error.message)  
    process.exit(1)  
  }  
  
  console.log(`User found! Their nickname is: ${user.nickname}`)  
}  
  
getUser(1, callback) // -> `User not found`  
getUser(5, callback) // -> `User found! Their nickname is: Teddy`
```

This way of handling this function may seem a bit convoluted these days, but with `.promisify()`,

we can easily change it into a modern, cleaner, and more maintainable version of itself:

```js
const getUserPromise = util.promisify(getUser);  
  
getUserPromise(id)  
  .then((user) => {  
      console.log(`User found! Their nickname is: ${user.nickname}`);  
  })  
  .catch((error) => {  
      console.log('User not found', error);  
  });  
  
getUser(1) // -> `User not found`  
getUser(5) // -> `User found! Their nickname is: Teddy`
```

We declare a `getUserPromise` variable that stores the `getUser` method turned into a promise using the `.promisify()` method.

With that in place, we’re able to use `getUserPromise` with [`.then()`](https://www.codecademy.com/resources/docs/javascript/promise/then) and [`.catch()`](https://www.codecademy.com/resources/docs/javascript/promise/catch) methods (or we could also use the `async...await` syntax here) to resolve the promise returned or catch any [errors](https://www.codecademy.com/resources/docs/javascript/errors).



### Review

- Node.js is a JavaScript _runtime_, an environment that allows us to execute our JavaScript code by converting it into something a computer can understand.
- REPLs are processes that **r**ead, **e**valuate, **p**rint, and repeat (**l**oop), and Node.js comes with its own REPL we can access in our terminal with the `node` command.
- We run JavaScript programs with Node in the terminal by typing `node` followed by the file name (if we’re in the same directory) or the absolute path of the file.
- Code can be organized into separate files, modules, and combined through _requiring_ them where needed using the `require()` function.
- Core modules are built into the Node.js environment to efficiently perform common tasks.
- The `console` module exports a global `console` object allowing the terminal to act as a debugging console, similar to the JavaScript `console` object provided by web browsers.
- The `process` module is a global module that gives access to information about the Node.js runtime environment.
- The `os` module provides [methods](https://www.codecademy.com/resources/docs/javascript/methods) to retrieve information about the computer, operating system, and network interfaces.
The `util` module contains methods used to maintain and debug your code
