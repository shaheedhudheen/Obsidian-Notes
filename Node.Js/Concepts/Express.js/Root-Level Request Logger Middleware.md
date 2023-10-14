
### Middleware

 `express.static()`

Middleware functions are functions that take 3 arguments: the **request object**, the **response object**, and the **next function** in the application’s request-response cycle.

These functions execute some code that can have *side effects* on the app, and usually add information to the request or response objects.

They can also end the cycle by sending a response when some condition is met.

If they don’t send the response when they are done, they start the execution of the next function in the stack. This triggers calling the 3rd argument, `next()`.

```js
function(req, res, next) {
  console.log("I'm a middleware...");
  next();
}
```


Let’s suppose you mounted this function on a route.

When a request matches the route, it displays the string “I’m a middleware…”, then it executes the next function in the stack.

*root-level middleware*

to mount a middleware function at root level, you can use the **`app.use(<mware-function>)`*** method. 

In this case, the function will be executed for all the requests, but you can also set more specific conditions. 

For example, if you want a function to be executed only for POST requests, you could use `app.post(<mware-function>)`. 
Analogous methods exist for all the HTTP verbs (GET, DELETE, PUT, …).


# Chain Middleware

Middleware can be mounted at a specific route using `app.METHOD(path, middlewareFunction)`

Middleware can also be chained within a route definition.

```js
app.get('/user', function(req, res, next) {
  req.user = getTheUserSync();  // Hypothetical synchronous operation
  next();
}, function(req, res) {
  res.send(req.user);
});
```


This approach is useful to split the server operations into smaller units. That leads to a better app structure, and the possibility to reuse code in different places.

This approach can also be used to perform some validation on the data. At each point of the middleware stack you can block the execution of the current chain and pass control to functions specifically designed to handle errors.

Or you can pass control to the next matching route, to handle special cases. 