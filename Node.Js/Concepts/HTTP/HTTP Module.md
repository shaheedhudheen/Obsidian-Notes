To process HTTP [requests](https://www.codecademy.com/resources/docs/javascript/requests) in JavaScript and Node.js, we can use the built-in [`http` module](https://nodejs.dev/en/api/v19/http).

This core module is key in leveraging Node.js networking and is extremely useful in creating HTTP servers and processing HTTP requests.

The `http` module comes with various [methods](https://www.codecademy.com/resources/docs/javascript/methods) that are useful when engaging with HTTP network requests.

One of the most commonly used methods within the `http` module is the `.createServer()` method - it creates an HTTP server.

```js
const server = http.createServer((req, res) => {  
  res.end('Server is running!');  
});  
  
server.listen(8080, () => {  
  const { address, port } = server.address();  
  console.log(`Server is listening on: http://${address}:${port}`);  
})
```

The `req` object contains all of the information about an HTTP request ingested by the server. It exposes information such as the HTTP method (`GET`, `POST`, etc.), the pathname, headers, body, and so on.

The `res` object contains methods and properties pertaining to the generation of a response by the HTTP server.

This object contains methods such as `.setHeader()` (sets HTTP headers on the response), `.statusCode` (set the status code of the response), and `.end()` (dispatches the response to the client who made the request). In the example above, we use the `.end()` method to send the string ‘Server is Running!’ to the client, which will display on the web page.

Once the `.createServer()` method has instantiated the server, it must begin listening for connections. This final step is accomplished by the `.listen()` method on the server instance. This method takes a [port](https://en.wikipedia.org/wiki/Port_(computer_networking)) number as the first argument, which tells the server to listen for connections at the given port number. In our example above, the server has been set to listen on port `8080` 

Additionally, the `.listen()` method takes an optional callback function as a second argument, allowing it to carry out a task after the server has successfully started.

Using this simple `.createServer()` method, in conjunction with the callback, provides the ability to process HTTP requests dynamically and dispatch responses back to their callers.