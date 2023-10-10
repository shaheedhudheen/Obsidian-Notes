
sometimes servers need to make [requests](https://www.codecademy.com/resources/docs/javascript/requests) to external APIs to accomplish some goal.

Some common situations are payment processing, service integrations with other products, webhooks, and so on.

There are a few [methods](https://www.codecademy.com/resources/docs/javascript/methods) provided by the `http` module that facilitate making HTTP requests to external services.

One of these methods is the `request()` method.

The `request()` method takes two arguments; it takes a configuration object containing details about the request as well as a callback to handle the response

```js
const options = {  
hostname: 'example.com',
port: 8080,
path: '/projects',
method: 'GET',
headers: {    
'Content-Type': 'application/json'  }}
const request = http.request(options, res => {  // Handle response here})
```


For convenience, the `http` module provides a convenient method for making `GET` requests in the form of the `get()` method.

This method differs from the `request()` method in that it automatically [sets](https://www.codecademy.com/resources/docs/javascript/sets) the method to `GET` and calls `req.end()` automatically.

The fact that servers can make HTTP requests to other services opens up possibilities for different architecture designs for back-ends.

One example of an architecture made possible by this ability is [microservice architectures](https://en.wikipedia.org/wiki/Microservices).

Microservice architectures divide needs into separate lightweight services that communicate via HTTP over a network.

As such, a single application can be comprised of dozens of microservices, which could all be written in different programming languages, but work together by communicating over HTTP.

![[Pasted image 20231006121958.png]]

example:

1. In our HTTP server, we will process incoming `GET` requests by invoking a handler function called `handleGetRequest()`. Part of this processing will include making a `GET` request to the following URL which requires some configuration.

```
https://static-assets.codecademy.com/Courses/Learn-Node/http/data.json
```

Let’s begin this configuration by creating a `const` variable called `options` within the `handleGetRequest()` function. Set the variable to be an object containing the properties `hostname`, `path`, and `method`. Using the URL above, set appropriate values for the properties of the `options` object.

**Note**: In the code editor, you may notice that both the `http` and `https` modules are being used. We use the `https` module to request data over HTTPS protocol and use the `http` module to create a localhost server to run our node application.

Stuck? Get a hint

Checkpoint 2 Passed

2. Now that the request has been configured, we can execute the request in the `handleGetRequest()` function. To make the request, we will use the `.request()` method from the `https` module.

Create a `const` variable called `request`. Set the variable to the `https.request()` method with the `options` object as the first argument and a callback function as the second argument. Create a callback function using the [ES6 arrow function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions) syntax. The callback function should also take a single argument called `response`.

Stuck? Get a hint

Checkpoint 3 Passed

3. Our HTTPS request needs to be set up to be able to receive the data properly. Data from the response will usually be received in chunks and pieced together. As such, we need to watch for these chunks of data and process them. We can do this by listening to the `data` event.

In the callback of the `.request()` method, create a variable called `data` initialized with an empty string. Then, listen for the `data` event and add the received data to the `data` variable.

Hint

You can listen for events on the response of a request using the `.on()` method. The `.on()` method takes an event as the first argument and a callback as the second argument.

```
response.on('EVENT', () => {  // Handle event processing here})
```

Checkpoint 4 Passed

4. Once all of the data has been received from the response, we need to handle that data.

To know when a response is finished, we can listen for the `end` event. Still in the callback of the `.request()` method, set up a listener for the `end` event of the response.

Stuck? Get a hint

Checkpoint 5 Passed

5. When the `end` event is triggered, we can work with the data from the response. In this case, we will act as a proxy and relay the data from the external API to the client that made the request. In the callback of the listener for the `end` event, log the data retrieved from the API to the console, then return the data by dispatching a response to the caller.

After the definition of `request` but still within `handleGetRequest`, be sure to signal the end of the request.

Run your code with `node app.js`, then click on the “Check Work” button.


```js
const http = require("http");

const https = require("https");

  

const handleGetRequest = (req, res) => {

  // Write external API request code here

  const options = {

    hostname: "static-assets.codecademy.com",

    path: "/Courses/Learn-Node/http/data.json",

    method: "GET",

    Headers: {

      "Content-Type": "application/json",

    },

  };

  const request = https.request(options, (response) => {

    let data = "";

    response.on("data", (chunk) => {

      data += chunk;

    });

  

    response.on("end", () => {

      console.log("Retrieved Data:", data);

      res.end(data);

    });

  });

  request.end();

};

  

// Creates server instance

const server = http.createServer((req, res) => {

  const { method } = req;

  

  switch (method) {

    case "GET":

      return handleGetRequest(req, res);

    default:

      throw new Error(`Unsupported request method: ${method}`);

  }

});

  

// Starts server listening on specified port

server.listen(4001, () => {

  const { address, port } = server.address();

  console.log(`Server is listening on: http://${address}:${port}`);

});
```



#  Review



```js

const http = require("http");
  

// Handle GET Request

const handleGetRequest = (req, res) => {

  const options = {

    hostname: "static-assets.codecademy.com",

    path: "/Courses/Learn-Node/http/data.json",

    method: "GET",

  };

  

  const request = http.request(options, (response) => {

    let data = "";

  

    response.on("data", (chunk) => {

      data += chunk;

    });

  

    response.on("end", (chunk) => {

      res.end(data);

    });

  });

  

  request.end();

};

  

// Creates server instance

const server = http.createServer((req, res) => {

  const { method } = req;

  

  switch (method) {

    case "GET":

      return handleGetRequest(req, res);

    default:

      throw new Error(`Unsupported request method: ${method}`);

  }

});

  

// Starts server listening on specified port

server.listen(4001, () => {

  const { address, port } = server.address();

  console.log(`Server is listening on: http://${address}:${port}`);

});
```