
an HTTP server will require information from the request URL to accurately process a request

This request URL is located on the `url` property contained within the `req` object itself.

To parse the different parts of this URL easily, Node.js provides the built-in [`url` module](https://nodejs.org/api/url.html).

The core of the `url` module revolves around the `URL` class.

A new `URL` object can be instantiated using the `URL` class as follows:

```js
const url = new URL('https://www.example.com/p/a/t/h?query=string');
```

Once instantiated, different parts of the URL can be accessed and modified via various properties

- `hostname`: Gets and [sets](https://www.codecademy.com/resources/docs/javascript/sets) the host name portion of the URL.
- `pathname`: Gets and sets the path portion of the URL.
- `searchParams`: Gets the search parameter object representing the query parameters contained within the URL. Returns an instance of the [URLSearchParams](https://nodejs.org/docs/latest-v14.x/api/url.html#url_class_urlsearchparams) class.

```js
const host = url.hostname; // example.com  
const pathname = url.pathname; // /p/a/t/h  
const searchParams = url.searchParams; // {query: 'string'}
```

While the `url` module can be used to deconstruct a URL into its constituent parts, it can also be used to construct a URL

```js
const createdUrl = new URL('https://www.example.com');  
createdUrl.pathname = '/p/a/t/h';  
createdUrl.search = '?query=string';  
  
createUrl.toString(); // Creates https://www.example.com/p/a/t/h?query=string
```