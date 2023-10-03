### States

In React, **state** is an object that holds some information that may change over the lifetime of a component ¹. It is a built-in React object that is used to contain data or information about the component ³. A component’s state can change over time; whenever it changes, the component re-renders ³. 

State is often called local or encapsulated because it is not accessible to any component other than the one that owns and sets it ¹. A component may choose to pass its state down as props to its child components ¹. This is commonly called a “top-down” or “unidirectional” data flow ¹.

To set the state of a component, we use the `setState()` method ⁴. When a value in the state object changes, the component re-renders ⁴. 

Source: Conversation with Bing, 10/3/2023
(1) State and Lifecycle – React. https://reactjs.org/docs/state-and-lifecycle.html.
(2) ReactJS State: SetState, Props and State Explained - Simplilearn. https://www.simplilearn.com/tutorials/reactjs-tutorial/reactjs-state.
(3) React State - W3Schools. https://www.w3schools.com/react/react_state.asp.
(4) ReactJS State - GeeksforGeeks. https://www.geeksforgeeks.org/reactjs-state/.

## notes

Imagine you're building a digital thermostat. The "state" in React is like the current temperature displayed on the screen. It's a way for your app to remember and show information that changes over time. For instance, as the room gets warmer or cooler, the displayed temperature updates to show the current temperature.

In React, we use "state" to make sure our app can remember and show changing information like this. It's like a note that React keeps, and whenever something important changes (like the temperature), React takes a look at the note and updates what's displayed on the screen to match.

**The state object is where you store property values that belong to the component. Whenever the state object changes, the component re-renders.**

**useState** When you want to change something on your web page (like updating a score in a game or displaying a new message), you need two things:

*Remember the Change*: You need a way to remember what you want to change. For instance, if you're playing a game, you need to remember the score. 
*Make the Change Visible*: You also need a way to show the change on your web page. If your score goes up, the web page should update to show the new score.

#### The useState Hook

**in React helps with both of these things:** 

*Memory Box*: It gives you a special "memory box" where you can put the thing you want to change (like the score in a game). This box remembers it even when your web page refreshes or updates.
*Magic Button*: It also gives you a special "magic button" that you can press when you want to make the change visible. When you press this button, React looks in the memory box, sees what's changed, and updates your web page to show the new information. So, if your score goes up, React makes sure the new score is displayed.

Hook. -
Hooks are like building blocks in React that allow you to use various features in your web applications. These building blocks can be either pre-made (built-in) by React or custom-made by you by combining them.(We'll discuss about this in detail later)

### Prop Drilling

In React, **prop drilling** is the process of passing data from a parent component to its child components through multiple levels of nesting ²³. This is often done by passing the data as a prop to each intermediate component in the hierarchy until it reaches the final destination component ¹. 

Prop drilling can be problematic because it can lead to a long chain of component dependencies that can be difficult to manage and maintain ³. It can also cause performance issues because every component that consumes or uses these props is re-rendered whenever there is a change in the data ¹.

To avoid prop drilling, you can use **React Context API** or **Redux** ¹⁴. These tools allow you to pass data down the component tree without having to pass it through every intermediate component ¹. 

Another way to avoid prop drilling is by using **render props**. A render prop is a function that a component uses to pass data to its children ⁵. The children receive the data as an argument to the function and can use it as needed ⁵.

I hope this helps! Let me know if you have any more questions.

Source: Conversation with Bing, 10/3/2023
(1) What is prop drilling in React? – Let's React. https://www.letsreact.org/what-is-prop-drilling-in-react/.
(2) What is prop drilling in React? - DEV Community. https://dev.to/codeofrelevancy/what-is-prop-drilling-in-react-3kol.
(3) A better way of solving prop drilling in React apps. https://blog.logrocket.com/solving-prop-drilling-react-apps/.
(4) Simplifying React Props Drilling: A Beginner's Guide. https://dev.to/obere4u/simplifying-react-props-drilling-a-beginners-guide-3kpc.
(5) What is prop drilling and how to avoid it - GeeksforGeeks. https://www.geeksforgeeks.org/what-is-prop-drilling-and-how-to-avoid-it/.


Think of prop drilling like passing a message along a line of people. Imagine you're playing a game of "telephone" with your friends, and you want to tell the last person in line a secret message. You whisper it to the first person, who whispers it to the next, and so on until it reaches the last person. "Prop drilling" is a term used in React to describe the process of passing data from a parent component to a deeply nested child component through intermediary components. It can occur when you have a component hierarchy where data needs to be passed down multiple levels.

#### While prop drilling works, it can lead to several challenges:

**Complexity**: As your component tree deepens, prop drilling can make your code more complex and harder to maintain. 
**Performance**: Passing props through multiple components, especially when those components don't use the props themselves, can affect performance. 
**Readability**: Code readability can suffer as you pass props through multiple levels of components.

![[Pasted image 20231003122104.png]]
![[Pasted image 20231003122122.jpg]]

next [[Conditional Rendering - Component Life Cycle]]
