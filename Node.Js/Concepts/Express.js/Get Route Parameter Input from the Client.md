
When building an API, we have to allow users to communicate to us what they want to get from our service

Example:

if the client is requesting information about a user stored in the database, they need a way to let us know which user they're interested in. One possible way to achieve this result is by using **route parameters**.

Route parameters are named segments of the URL, delimited by slashes (/).

Each segment captures the value of the part of the URL which matches its position. 

The captured values can be found in the `req.params` object.

	route_path: '/user/:userId/book/:bookId'  
	actual_request_URL: '/user/546/book/6754'  
	req.params: {userId: '546', bookId: '6754'}

# Get Query Parameter Input from the Client

Another common way to get input from the client is by encoding the data after the route path, using a query string

The query string is delimited by a question mark (?), and includes field=value couples.

Each couple is separated by an ampersand (&). 

Express can parse the data from the query string, and populate the object `req.query`.

Some characters, like the percent (%), cannot be in URLs and have to be encoded in a different format before you can send them.

If you use the API from JavaScript, you can use specific methods to encode/decode these characters.

	route_path: '/library'  
	actual_request_URL: '/library?userId=546&bookId=6754'  
	req.query: {userId: '546', bookId: '6754'}

# body-parser to Parse POST Requests

POST is the default method used to send client data with HTML forms. 
 
In REST convention, POST is used to send data to create new items in the database (a new user, or a new blog post).

In these kind of requests, the data doesn’t appear in the URL, it is hidden in the request body.

The body is a part of the HTTP request, also called the payload. 

Even though the data is not visible in the URL, this does not mean that it is private.

To see why, look at the raw content of an HTTP POST request

```http
POST /path/subpath HTTP/1.0
From: john@example.com
User-Agent: someBrowser/1.0
Content-Type: application/x-www-form-urlencoded
Content-Length: 20

name=John+Doe&age=25
```

the body is **encoded** like the **query string**.

This is the default format used by HTML forms.

With Ajax, you can also use JSON to handle data having a more complex structure.

There is also another type of encoding: **multipart/form-data**. 

This one is used to upload binary files.

To parse the data coming from POST requests, you must use the `body-parser` package. This package allows you to use a series of middleware, which can decode data in different formats.


---

Tip: There are several other http methods other than GET and POST. And by convention there is a correspondence between the http verb, and the operation you are going to execute on the server. The conventional mapping is:

POST (sometimes PUT) - Create a new resource using the information sent with the request,

GET - Read an existing resource without modifying it,

PUT or PATCH (sometimes POST) - Update a resource using the data sent,

DELETE - Delete a resource.

There are also a couple of other methods which are used to negotiate a connection with the server. Except from GET, all the other methods listed above can have a payload (i.e. the data into the request body). The body-parser middleware works with these methods as well.