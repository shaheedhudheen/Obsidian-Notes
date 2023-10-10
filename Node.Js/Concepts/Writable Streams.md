
 create a writeable stream to a file using the`fs.createWriteStream()`
```js
const fs = require('fs')  
  
const fileStream = fs.createWriteStream('output.txt');  
  
fileStream.write('This is the first line!');  
fileStream.write('This is the second line!');  
fileStream.end();
```

we set the output file as **output.txt**. Then we `.write()` lines to the file. Unlike a readable stream, which ends when it has no more data to read, a writable stream could remain open indefinitely. We can indicate the end of a writable stream with the `.end()` method.


**Reading** and **Writing**

```js
const readline = require("readline");
const fs = require("fs");

const myInterface = readline.createInterface({
  input: fs.createReadStream("shoppingList.txt"),
});

const fileStream = fs.createWriteStream("shoppingResults.txt");

const transformData = (line) =>{
  fileStream.write(`They were out of: ${line}\n`)
}
myInterface.on('line', transformData)
```
