
With the introduction of ES6 (ECMAScript) in 2015 came a new feature called _[arrow expressions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)_. Arrow expressions has allowed developers to omit parts of the function they don’t need. This means that it allows your code to become more maintainable and organized.

When using an arrow expression, we do not use the `function` declaration. To define an arrow expression you simply use: `() => { }`. You can pass arguments to an arrow expression between the parenthesis (`()`).

```javascript
// Defining an anonymous arrow expression that simply logs a string to the console.  
console.log(() => console.log('Shhh, Im anonymous'));  
  
// Defining a named function by creating an arrow expression and saving it to a const variable helloWorld.  
const helloWorld = (name) => {  
  console.log(`Welcome ${name} to Codecademy, this is an arrow expression.`)  
};  
  
// Calling the helloWorld() function.  
helloWorld('Codey'); //Output: Welcome Codey to Codecademy, this is an Arrow Function Expression.
```
