
## What is a Component?

Components in React can be thought of as building blocks for building user interfaces. 

They are like reusable pieces of a web page that you can create and customize, and then you can put these pieces together to create a complete web application. 

Imagine you are building a web page, and you want to break it down into smaller, manageable parts. Each part could be a component. For example, you might have a component for the header of your page, another for a navigation menu, one for a product list, and so on.

**In React, components are defined as JavaScript functions or classes that return JSX, describing what should be rendered on the screen.**

## Creating a Component:

React component names must start with a capital letter.

there are two common ways to create a component - as a functional component or as a class component. 

1. Functional Component : Functional components are simpler and more concise. These are simply like JavaScript functions. 
2. Class Component : These components are simple classes (made up of multiple functions that add functionality to the application). All class components are child classes for the Component class of ReactJS. Class components are used when you need to manage component state or use lifecycle methods. (not that much used now a days)

## What do you mean by rendering a component?

Rendering a component in React refers to the process of displaying or showing a component's user interface on a web page. In simpler terms, it means making the content and functionality defined within a React component visible to the user in a web application. When you render a component, you are instructing React to take the component's description (typically written in JSX) and transform it into actual HTML elements that appear on the screen.

### To render a component:

include the file in the header of "App.js" and pass the props*. 

Syntax : <Component_name prop="value" />


## What are Props? 

In React, "props" is a shorthand for "properties," and they are a way to pass data from a parent component to a child component. 

Props allow you to customize and configure child components, making them dynamic and reusable. Props are read-only, meaning that child components cannot modify the data they receive via props. They are purely for receiving and using data. React Props are like function arguments in JavaScript and attributes in HTML.

## How do you pass props between components?

Parent (P): You have a bag of candies, and you want to give some to your child.

Pass Props: To pass candies, you put them in a small box (props), and you write your child's name (prop name) on the box. Then you hand the box to your child. 

Child (C): Your child receives the box with their name on it and opens it to find the candies (props) inside. In this example, the candies are like data, and the box with your child's name on it is like a prop. You use props to give information from the parent component to the child component in React.

![[Pasted image 20231003115909.jpg]]![[Pasted image 20231003115912.jpg]]

next  [[States - Prop drilling]]
