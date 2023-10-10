![[Pasted image 20231005132247.png]]

HTTP **[requests](https://www.codecademy.com/resources/docs/javascript/requests)** and **responses** have specific structures to help facilitate the exchange of information between a client and a server.

These structures encapsulate all of the important information required to instruct the recipient of the message on how to react.

### Requests

Requests are comprised of a few core elements that provide information to a server.

1. **HTTP Method**: The HTTP method is usually a verb, such as `GET` and `POST`, or a noun such as `OPTIONS` and `HEAD`. These [methods](https://www.codecademy.com/resources/docs/javascript/methods) inform the server of the intent of the request and are used in accurately routing and processing requests. For instance, an HTTP request containing a `GET` method implies that the client wants to fetch a resource. The list of supported HTTP methods can be found using the `http.METHODS` property.
2. **Path**: The path denotes the path of the resource relative to the root URL. For example, making a `GET` request to `https://codecademy.com/api/lessons` would strip common elements such as the protocol (`https://`) and domain (`codecademy.com`), leaving the path of `/api/lessons`.
3. **HTTP Protocol Version**: The version of the HTTP protocol (I.e. [HTTP/1.1](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol), [HTTP/2](https://en.wikipedia.org/wiki/HTTP/2), and [HTTP/3](https://en.wikipedia.org/wiki/HTTP/3)). We will learn more about this in the next exercise.
4. **Headers**: Headers are optional and are used to convey additional information that may be important in processing a request by a server. There is an extensive list of [standard headers](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers) that can be used, as well as custom headers that can be added on a per-application basis.  
5. **Body**: The body contains data required to be sent to the server to process a request. The body is not leveraged for all request types. It is most common to see a body attached to requests with verbs such as `POST`, `PUT`, and `PATCH`.

### Responses 

Responses are comprised of similar elements to their counterpart requests, with a few differences. 

1. **HTTP Protocol Version**: The version of the HTTP protocol, similar to the request.
2. **Status Code**: The status code indicates if the request was successful and, if not, why it wasn’t successful.
3. **Status Message**: The status message provides a short description of the corresponding status code. 
4. **Headers**: These response headers are similar to those provided in a request.
5. **Body**: The body of a response contains data corresponding to the fetched resource. The body is optional and contains data only when necessary to fulfill the request.

