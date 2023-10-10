
The `querystring` module is dedicated to providing utilities solely focused on parsing and formatting URL query strings

the module provides a much smaller number of [methods](https://www.codecademy.com/resources/docs/javascript/methods) to use.

- [`.parse()`](https://www.codecademy.com/resources/docs/javascript/json/parse): This method is used for parsing a URL query string into a collection of key-value pairs. The `.decode()` method does the same.

```js
const str = 'prop1=value1&prop2=value2';
querystring.parse(str); // Returns { prop1: value1, prop2: value2}
```

- [`.stringify()`](https://www.codecademy.com/resources/docs/javascript/json/stringify): This method is used for producing a URL query string from a given object via iteration of the object’s “own properties.” The `.encode()` method does the same.

```js
const props = { "prop1": value1, "prop2": value2};
querystring.stringify(props); // Returns 'prop1=value1&prop2=value2'
```

- `.escape()`: This method is used for performing [percent-encoding](https://developer.mozilla.org/en-US/docs/Glossary/percent-encoding) on a given query string.
- `.unescape()`: This method is used to decode percent-encoded characters within a given query string.

The `querystring` module is focused solely on manipulating URL query strings

so it requires the query string to have already been isolated from an incoming URL as part of a request.

This means that some pre-processing of the URL is necessary before being able to use the module

Additionally, it is worth noting that in the latest versions of Node (v16.x) the `querystring` module has become a legacy feature, with its core functionality having been absorbed into the `url` module via the `URLSearchParams` API. However, the features in the `querystring` module are still handy when using the long-term support versions of Node.js (v14.x).