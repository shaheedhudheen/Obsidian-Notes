

## What is JSON?

 JSON, or JavaScript Object Notation, is a popular, language-independent, standard format for storing and exchanging data. Adopted by [ECMA International](http://ecma-international.org/), an industry association founded in 1961 to standardize information and communication systems, [JSON](http://www.ecma-international.org/publications/files/ECMA-ST/ECMA-404.pdf) has become the de facto standard that facilitates storing and sending data between all [programming languages](https://www.codecademy.com/resources/blog/programming-languages/).
## Uses

JSON is heavily used to facilitate data transfer in web applications between a client, such as a web browser, and a server. A typical example where such data transfer occurs is when you fill out a web form. The form data is converted from HTML to JavaScript objects to JSON objects and sent to a remote web server for processing. These transactions could be as simple as entering a search engine query to a multi-page job application.

When companies make their data public for other applications, like Spotify sharing its music library or Google sharing its map data, the information is formatted in JSON. This way, any application, regardless of language, can collect and parse the data.

 **Popular web apis that used json in data exchange** 
- [Google Maps](https://developers.google.com/maps/documentation/geocoding/start)
- [Google Auth 2.0 Authentication](https://developers.google.com/identity/protocols/oauth2/service-account)
- [Facebook Social Graph API](https://developers.facebook.com/docs/messenger-platform/reference/send-api)
- [Spotify Music Web API](https://developer.spotify.com/documentation/web-api/)
- [LinkedIn Profile API](https://docs.microsoft.com/en-us/linkedin/shared/integrations/people/profile-api)

## JSON Syntax

- JSON is derived from the JavaScript programming language,
- its appearance is similar to that of JavaScript objects.

sample: 

```json 
{  
  "student": {  
    "name": "Ahammed Shaheedhudheen",  
    "age": 24,  
    "fullTime": true,  
    "languages": [ "JavaScript", "HTML", "CSS" ],  
    "GPA": 3.9,  
    "favoriteSubject": null  
  }  
}
```

## Rules

- The curly braces, `{..}`, hold objects.
- The square brackets, `[..]`, hold arrays.
- Data is stored in name-value pairs separated by a colon, `:`.
- Every name-value pair is separated from another pair by a comma, `,`. Similarly, every item in an array is delimited by a comma as well. [Trailing commas](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Trailing_commas) are forbidden.
- JSON property names must be in double-quoted `(" ")` text even though JavaScript names do not hold by this stringency.

## Data Types

- string (double-quoted)
- number (integer or floating point)
- object (name-value pair)
- array (comma-delimited)
- boolean (true or false)
- null

JSON doesn’t cover every data type. Types that are not represented in JSON such as dates can be stored as a string and converted to a language-specific data structure

**Eg** -  an acceptable internationally-recognized date format in [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html):

```
"2014-01-01T23:28:56.782Z"
```
 
 every programming language has built-in JSON facilities to convert this string into a more readable and usable format