# ⚛️ React Notes - Day 1

## Date: October 2, 2025

### 1. React vs. Vanilla JavaScript

React offers several core advantages that simplify the development of complex, dynamic user interfaces compared to traditional Vanilla JavaScript DOM manipulation.

* **Component-Based Architecture:** Encourages breaking the UI into independent, reusable pieces (components). This improves **modularity**, **maintainability**, and **reusability**.
* **Virtual DOM (VDOM):** An in-memory representation of the Real DOM. React uses the VDOM to compare the previous state of the UI with the new state, calculating the most efficient way to update the Real DOM. This significantly improves **performance** by minimizing direct, expensive DOM manipulations.
* **React Hooks (e.g., `useState`, `useEffect`):** Functions that let you "hook into" React features from functional components. Hooks like `useMemo` and `useCallback` are crucial for **performance optimization** by preventing unnecessary re-calculations and re-renders.
* **State Management Tools:** Provides robust patterns and tools (like Redux, Zustand) for managing complex application state, which is often difficult to control in large-scale Vanilla JS applications.

---

### 2. The Relationship Between JSX and JavaScript

A React component is fundamentally a JavaScript function that returns a description of the UI, written in **JSX** (JavaScript XML).

| Context | Syntax | Environment Status |
| :--- | :--- | :--- |
| **Default** (Function Body) | `function App() { ... }` | **Standard JavaScript** (Logic, variables, functions) |
| **Entering JSX** | `return ( ... );` | **JSX Markup** (Writing UI structure, looks like HTML) |
| **Escaping JSX** | `{ expression }` | **JavaScript Environment** (Used to embed dynamic content, variables, or execute functions within JSX) |

---

### 3. Dynamic Attributes with Template Literals

When setting the value for attributes like `className`, we use a specific nesting of environments to create a single, dynamic string.

| Layer | Syntax | Environment | Purpose |
| :---: | :---: | :--- | :--- |
| **Layer 1** | `className={...}` | **JavaScript Escape** | Tells JSX to evaluate the expression inside. |
| **Layer 2** | `` `...` `` | **String Template Literal** | Defines the main string structure, allowing static text and dynamic insertions. |
| **Layer 3** | `${...}` | **JavaScript Interpolation** | Executes logic (like the ternary operator) and inserts its result (as a string) into the template. |

#### Corrected Example:

```jsx
<div 
  className={`
    ${product.id % 2 === 0 ? 'bg-red' : 'bg-gray'} 
    m-8
  `}
>
    {product.item}
</div>



### 2. JSX (JavaScript XML)

JSX is a syntax extension that allows writing HTML-like code inside JavaScript.

| Context | Syntax | Environment Status |
| :--- | :--- | :--- |
| Default (Function Body) | `function App() { ... }` | Standard JavaScript (Logic, variables, functions) |
| Entering JSX | `return ( ... );` | JSX Markup (UI structure) |
| Escaping JSX | `{ expression }` | JavaScript Environment (dynamic content, variables, functions) |

**Example:**
```jsx
const element = <h1>Hello, world!</h1>;


const element = React.createElement("h1", null, "Hello, world!");


### 3. ClassComponents

  import React, { Component } from 'react';

  class Welcome extends Component {
    constructor(props) {
      super(props);
      this.state = { count: 0 };
    }
  
    render() {
      return (
        <div>
          <h1>Hello, {this.props.name}</h1>
          <p>Count: {this.state.count}</p>
          <button onClick={() => this.setState({ count: this.state.count + 1 })}>
            Increment
          </button>
        </div>
      );
    }
  }
  
  export default Welcome;

 ### Updating State in class component

  this.setState({ count: this.state.count + 1 });
  or
  this.setState(prevState => ({ count: prevState.count + 1 }));//better approach


### React Life Cycle Methods

  | Phase      | Method                      | Purpose                                           |
| ---------- | --------------------------- | ------------------------------------------------- |
| Mounting   | `constructor()`             | Initialize state, bind methods                    |
| Mounting   | `render()`                  | Render JSX                                        |
| Mounting   | `componentDidMount()`       | Runs after component mounts; useful for API calls |
| Updating   | `shouldComponentUpdate()`   | Control re-rendering                              |
| Updating   | `getSnapshotBeforeUpdate()` | Capture DOM info before update                    |
| Updating   | `componentDidUpdate()`      | Runs after updates (called on re-render)          |
| Unmounting | `componentWillUnmount()`    | Cleanup resources, timers, subscriptions          |
| Error      | `componentDidCatch()`       | Catch errors in child components                  |


### HigherOrderComponent

  A HOC is a function that takes a component and returns a new, enhanced component.

  const withExtraProps = (WrappedComponent) => {
  return (props) => <WrappedComponent {...props} extraProp="Hello" />;
};


### Shadow Dom v/s Virtual Dom

  | Feature                | Virtual DOM                              | Shadow DOM                     |
| ---------------------- | ---------------------------------------- | ------------------------------ |
| Purpose                | Performance optimization (React diffing) | Encapsulation (Web Components) |
| Scope                  | In-memory JS object                      | Browser DOM subtree            |
| Visibility in DevTools | No                                       | Yes (`#shadow-root`)           |
| Analogy                | Draft paper                              | House with private rooms       |



