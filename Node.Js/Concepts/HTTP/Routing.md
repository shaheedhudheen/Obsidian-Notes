a server needs to maintain a way to handle each request based on specific criteria such as `method`, `pathname`, etc. The process of handling requests in specific ways based on the information provided within the request is known as _routing_.

The `method` is one important piece of information that can be used to route requests

Since each HTTP request contains a `method` such as `GET` and `POST`, it is a great way to discern different classes of requests based on the action intended for the server to carry out.

Thus, all `GET` requests could be routed to a specific function for handling, while all `POST` requests are routed to another function to be handled.
This also allows for the logical co-location of processing code with the specific verb to be handled.

```js

const server = http.createServer((req, res) => {  
  const { method } = req;  
  
  switch(method) {  
    case 'GET':  
      return handleGetRequest(req, res);  
    case 'POST':  
      return handlePostRequest(req, res);  
    case 'DELETE':  
      return handleDeleteRequest(req, res);  
    case 'PUT':  
      return handlePutRequest(req, res);  
    default:  
      throw new Error(`Unsupported request method: ${method}`);  
  }  
})
```

In the above example, the HTTP `method` property is [destructured](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) from the `req` object and used to conditionally invoke a handler function built specifically for handling those types of requests

This is great at first glance, but it should soon become apparent that the routing is not specific enough. After all, how will one `GET` request be distinguished from another?

We can distinguish one request from another of the same method through the use of the `pathname`. The `pathname` allows the server to understand what resource is being targeted

example: 
```js
function handleGetRequest(req, res) {  
  const { pathname } = new URL(req.url);  
  let data = {};  
  
  if (pathname === '/projects') {  
    data = await getProjects();  
    res.setHeader('Content-Type', 'application/json');  
    return res.end(JSON.stringify(data));  
  }  
  
  res.statusCode = 404;  
  return res.end('Requested resource does not exist');  
  
}
```

Within the `handleGetRequest()` function, the `pathname` is being checked to match a known resource, `'/projects'`.

If the `pathname` matches, the resource data is fetched and then subsequently dispatched from the server as a successful response. 

Otherwise, the `.statusCode` property is set to `404`, indicating that the resource is not found, and a corresponding error message is dispatched. 

This pattern can be extrapolated to any number of conditional resource matches, allowing the server to handle many different types of requests to different resources.

