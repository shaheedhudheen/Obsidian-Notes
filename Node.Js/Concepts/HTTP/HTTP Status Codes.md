Once a request is processed, a response must be returned to the client to inform it of what happened.

To build a response for the client, several pieces of information are required.

One of these pieces of information is the [HTTP response status code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status),

which is responsible for indicating whether a specific HTTP request has been successfully completed.

Response status codes are grouped into five classes:

1. [Informational](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#information_responses): Range from `100` to `199`. 
2. [Successful](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#successful_responses): Range from `200` to `299`.
3. [Redirects](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#redirection_messages): Range from `300` to `399`.
4. [Client Errors](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#client_error_responses): Range from `400` to `499`.
5. [Server Errors](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#server_error_responses): Range from `500` to `599`.

Each response status code conveys information about what happened during the processing of the request,

which in turn helps the client decide how to handle the response and if further action is necessary.

Status codes are paired with a short text-based description to help elucidate the meaning of the code.

Some common types of status codes that you are likely to encounter are `200 OK`, `400 Bad Request`, and `500 Internal Server Error`.

