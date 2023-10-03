### Hooks


**React Hooks** are a new addition to React that allows you to use state and other React features without writing a class ¹. They are functions that "hook into" React state and lifecycle features from function components ². Hooks are completely opt-in and 100% backwards-compatible, which means you can try them in a few components without rewriting any existing code ¹. 

Hooks provide a more direct API to the React concepts you already know: props, state, context, refs, and lifecycle ¹. They allow you to reuse stateful logic without changing your component hierarchy ³. 

The most commonly used hooks are `useState`, `useEffect`, `useContext`, and `useReducer` ⁴. Here is a brief description of each:

- `useState`: This hook allows you to add state to your functional components. It returns an array with two elements: the current state value and a function to update it ⁴.
- `useEffect`: This hook allows you to perform side effects in your functional components. It replaces the lifecycle methods `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` ⁴.
- `useContext`: This hook allows you to consume context that has been created by a parent component. It replaces the `static contextType` property and the `Context.Consumer` component ⁴.
- `useReducer`: This hook allows you to manage complex state logic in your functional components. It is similar to Redux's reducer function ⁴.

Hooks can help you write more concise and reusable code by allowing you to extract stateful logic from your components into reusable functions called **custom hooks** ¹³. 

I hope this helps! Let me know if you have any more questions.

Source: Conversation with Bing, 10/3/2023
(1) Introducing Hooks – React. https://reactjs.org/docs/hooks-intro.html.
(2) React Hooks - javatpoint. https://www.javatpoint.com/react-hooks.
(3) React Hooks Fundamentals for Beginners - freeCodeCamp.org. https://www.freecodecamp.org/news/react-hooks-fundamentals/.
(4) Learn React Hooks – A Beginner's Guide - freeCodeCamp.org. https://www.freecodecamp.org/news/the-beginners-guide-to-react-hooks/.
(5) React Hooks - W3Schools. https://www.w3schools.com/react/react_hooks.asp.

**Extras**

Hooks in React are like special tools that make it easier for components (the building blocks of React applications) to do things like remembering information, doing tasks at the right time, and sharing data with other parts of the app.
Hooks let us use different React features from our components. we can either use the built-in Hooks or combine them to build your own(custom hooks).

### State Hooks
Think of "state" in a component like a sticky note or a piece of paper that the component can use to remember important information. For instance, if you have a form on a website, the sticky note can hold the text you type into the form fields. If you have a gallery of pictures, the sticky note can remember which picture you've selected to display. It's a way for the component to keep track of what's happening or what the user has done.

To add state to a component, we can use:
useState - declares a state variable that you can update directly.
useReducer -declares a state variable with the update logic inside a reducer function

### Context Hooks
Think of "context" as a messenger that allows a component to get information from its parent, even if there are many layers of other components in between.
For example, imagine your top-level component has information about the current style or theme of your app, like whether it's light or dark mode. Instead of passing this information as a prop through all the intermediate components, you can use context to send this message directly to the component that needs it, even if it's far down the component tree. It's like a shortcut for sharing important data without making a long chain of deliveries through props.

useContext - reads and subscribes to a context.

### Ref Hooks

The useRef hook is a way to create and access a reference to a value or a DOM element in React. A reference is an object that has a current property that points to the value or element you want to reference. Unlike state, changing a reference does not cause a re-render of the component. This makes useRef useful for storing values that are not related to the visual output of the component, such as timers, intervals, previous state values, or DOM elements.

To use the useRef hook, you need to import it from React:

```javascript
import { useRef } from 'react';
```

Then, you can call it inside your function component and pass an initial value as an argument. The useRef hook will return a reference object that you can assign to a variable:

```javascript
const ref = useRef(initialValue);
```

The initial value can be anything, such as a number, a string, an object, or null. If you don't pass any argument, the initial value will be undefined. The initial value is only used for the first render of the component. On subsequent renders, the useRef hook will return the same reference object.

To access the value or element that the reference points to, you can use the current property of the reference object:

```javascript
const value = ref.current;
```

To update the value or element that the reference points to, you can assign a new value to the current property of the reference object:

```javascript
ref.current = newValue;
```

Note that updating a reference does not trigger a re-render of the component. If you want to use a reference to store a value that affects the visual output of the component, such as a piece of state, you should use the useState hook instead.

One common use case for useRef is to access a DOM element directly. For example, if you want to focus an input element when a button is clicked, you can use useRef to create and attach a reference to the input element:

```javascript
function App() {
  const inputRef = useRef(); // Create a reference

  const handleClick = () => {
    inputRef.current.focus(); // Access and focus the input element
  };

  return (
    <div>
      <input type="text" ref={inputRef} /> // Attach the reference to the input element
      <button onClick={handleClick}>Focus</button>
    </div>
  );
}
```

Another common use case for useRef is to keep track of the previous value of a state variable. For example, if you want to display both the current and previous values of an input field, you can use useRef to store and update the previous value whenever the state changes:

```javascript
function App() {
  const [value, setValue] = useState(''); // State variable for the input value
  const prevValueRef = useRef(); // Reference for the previous value

  useEffect(() => {
    prevValueRef.current = value; // Update the previous value when the state changes
  }, [value]);

  const handleChange = (e) => {
    setValue(e.target.value); // Update the state when the input changes
  };

  return (
    <div>
      <input type="text" value={value} onChange={handleChange} />
      <p>Current value: {value}</p>
      <p>Previous value: {prevValueRef.current}</p>
    </div>
  );
}
```

You can learn more about the useRef hook from these sources:

- [useRef – React](^1^)
- [React useRef Hook - W3Schools](^2^)
- [How to use React's useRef() hook | Felix Gerschau](^3^)
- [What is useRef hook and how do you use it? - DEV Community](^4^)
- [React JS useRef Hook - GeeksforGeeks](^5^)

Source: Conversation with Bing, 10/3/2023
(1) useRef – React. https://react.dev/reference/react/useRef.
(2) React useRef Hook - W3Schools. https://www.w3schools.com/react/react_useref.asp.
(3) How to use React's useRef() hook | Felix Gerschau. https://felixgerschau.com/useref-react-hooks/.
(4) What is useRef hook and how do you use it? - DEV Community. https://dev.to/nibble/what-is-useref-hook-and-how-do-you-use-it-5emo.
(5) React JS useRef Hook - GeeksforGeeks. https://www.geeksforgeeks.org/react-js-useref-hook/.

Think of "refs" as a way for a component to have a secret note that it keeps hidden, which contains some information it doesn't want to show on the screen. This information could be something like a reference to a specific part of a web page (like a button), or a timer that the component is using.
Unlike the regular information a component uses (which makes it update and change), this secret note (the ref) doesn't make the component change or re-render when you update it. It's like a special tool you can use when you need to work with parts of your app that don't follow the usual rules of React, like certain browser features.
In a way, refs are like a hidden escape route from the usual React way of doing things, allowing you to interact with the outside world when necessary, without causing your component to refresh or redraw.

*useRef* -declares a ref. You can hold any value in it, but most often it’s used to hold a DOM node.

### Effect Hooks

The useEffect hook in React is a way to perform side effects in function components. Side effects are any actions that affect something outside of the scope of the current function, such as fetching data, updating the DOM, or logging messages. The useEffect hook lets you run some code after React has updated the DOM, similar to how class components use the componentDidMount, componentDidUpdate, and componentWillUnmount lifecycle methods.

The basic syntax of the useEffect hook is:

```javascript
useEffect(setup, dependencies);
```

The setup parameter is a function that contains the logic of your effect. The dependencies parameter is an optional array of values that determine when your effect should run. If you omit the dependencies parameter, your effect will run after every render of the component. If you pass an empty array, your effect will only run once when the component mounts. If you pass an array with some values, your effect will run whenever any of those values change.

The setup function can also optionally return a cleanup function. The cleanup function is used to undo any changes that your effect made, such as removing event listeners, clearing timers, or canceling requests. The cleanup function will run before the next execution of the setup function, or when the component unmounts.

Here is an example of using the useEffect hook to fetch some data from an API and display it on the screen:

```javascript
import React, { useState, useEffect } from 'react';

function App() {
  const [posts, setPosts] = useState([]);

  useEffect(() => {
    // Fetch some posts from an API
    fetch('https://jsonplaceholder.typicode.com/posts')
      .then(response => response.json())
      .then(data => setPosts(data)); // Update the state with the fetched data
  }, []); // Pass an empty array to run the effect only once

  return (
    <div className="App">
      <h1>Posts</h1>
      <ul>
        {posts.map(post => ( // Map over the posts array and display each post
          <li key={post.id}>
            <h2>{post.title}</h2>
            <p>{post.body}</p>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default App;
```

You can learn more about the useEffect hook from these sources:

- [useEffect – React](^1^)
- [Using the Effect Hook – React](^2^)
- [Advanced React Hooks: Deep Dive into useEffect Hook - Educative](^3^)
- [ReactJS useEffect Hook - GeeksforGeeks](^4^)
- [Demystifying React's useEffect Hook - Kinsta®](^5^)

Source: Conversation with Bing, 10/3/2023
(1) useEffect – React. https://react.dev/reference/react/useEffect.
(2) Using the Effect Hook – React. https://reactjs.org/docs/hooks-effect.html.
(3) Advanced React Hooks: Deep Dive into useEffect Hook - Educative. https://www.educative.io/blog/react-useeffect-hook.
(4) ReactJS useEffect Hook - GeeksforGeeks. https://www.geeksforgeeks.org/reactjs-useeffect-hook/.
(5) Demystifying React's useEffect Hook - Kinsta®. https://kinsta.com/knowledgebase/react-useeffect/.

#### Examples

UseState Hook
useState is a built-in React Hook that lets you add a state variable to your component.

Usage of useState:
1. Adding State to a Component:
   - Employ useState to introduce and manage state within your component.

2. Updating State Based on the Previous State:
   - Utilize the previous state value to calculate and set the new state, ensuring accurate updates.

3. Updating Objects and Arrays in State:
   - Manage complex state structures like objects or arrays, modifying specific elements as needed.

4. Avoiding Recreating the Initial State:
   - Prevent unintentional state resets by using the functional update form to build upon the existing state.

5. Resetting State with a Key:
   - Implement state resets by using a unique key or identifier to revert to initial values.

6. Storing Information from Previous Renders:
   - Capture and retain information from previous render cycles, enabling data persistence and comparison.

**useEffect Hook**
useEffect is a built-in react hook that lets you synchronize a component with an external system.

**Usage of useEffect:**

1. Connecting to External Systems:
   - Use useEffect to interact with external systems like APIs or databases.

2. Custom Hooks for Effects:
   - Create custom hooks to encapsulate and reuse useEffect logic.

3. Non-React Widget Control:
   - Manage non-React components or widgets within your React app using useEffect.

4. Data Fetching:
   - Initiate data fetching operations with useEffect to retrieve and display data.

5. Reactive Dependencies:
   - Specify dependencies in useEffect to trigger effects when specific values change.

6. Updating State Sequentially:
   - Update state within useEffect based on previous state for sequential operations.

7. Optimizing Object Dependencies:
   - Efficiently manage dependencies in useEffect to avoid unnecessary updates.

#### Custom Hooks:

There are so many built-in hooks in react, but still if you wish to create on for yourself you can using "Custom hooks".

You can make a custom hook by following these steps:
Start with a Function:
Begin by creating a regular JavaScript function. Custom hooks should have names that start with "use" to adhere to the hook naming convention.

Define the Hook:
Inside your custom hook function, you can use built-in hooks or other custom hooks if needed. These hooks can include useState, useEffect, or other custom hooks you've created.

Encapsulate Logic:
Identify the logic you want to encapsulate and abstract into the custom hook. This logic can involve state management, data fetching, event handling, or any other functionality you want to reuse across components.

Return Values:
Your custom hook should return values that components can use. Typically, this includes variables, functions, or both, depending on the functionality of your hook.

Use the Custom Hook:
Import and use the custom hook in your components, just like you would with built-in hooks. This allows you to reuse the encapsulated logic across different parts of your application.

Custom hooks are a powerful tool in the React developer's toolkit. They enable you to encapsulate and share stateful logic, promoting reusability and maintainability in your codebase. By creating custom hooks, you can streamline your components, separate concerns, and write cleaner, more efficient code.