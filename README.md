# React interview questions

## Virtual DOM

### Differentiate between Real DOM and Virtual DOM.

The Real DOM is always tree-structured. The DOM trees are huge nowdays because of large apps. We need to modify the DOM tree a lot of times. And this a real perfomance and development pain. 

The Virtual DOM is abstraction of the Real DOM. It is lightweight and detached from the browser-specific implimentation details. Its not invented by React but it uses it and provide it. ReactElements lives in Virtual DOM. They make basics nodes here. Once we defined the elements, ReactElements can be reder into Real DOM.

#### Real DOM
- Real DOM updates slow
- Can directly update HTML
- Creates new DOM elements if  elements updates
- DOM manipulations is very expensive
- To much memory wastage

#### Virtual DOM
- Virtual DOM updates fast
- Can't directly update HTML
- Updates JSX if elements updates
- DOM manipulations is very easy
- No memory wastage

## React 

### How React works?

React creates a virtual DOM. When state changes in a component it firstly runs a "diffing" algoritm, which identifies was changed on the Virtual DOM. The second step is reconciliation, where it updates the DOM with results of diff.

### What is JSX?

JSX is a syntax extension to JS and comes with the full power of JavaScript. JSX produces React elements. You can embed any JavaScript expresion in JSX by wrapping it in curly braces. After compilation, JSX expressions become regular JS objects. This means that you can use JSX inside of if statements and for loops, assign it to variables, accept it as arguments, and return it from functions. Eventhough React does not require JSX, it is recommended way to describing our UI in React app.

### What is ReactDOM?

React DOM is the glue between React and the DOM. Often we use it for one single thing: mounting with ReactDOM. Another useful feature of ReactDOM is ReactDOM.findDOMNode() which we can use to gain direct access to DOM elements.

### What the difference between state and props?

The state is data structure that starts with a default value when a Component mount.

Props are a Component's configuration. Props are how components talks to each other. They are received them is concerned. A Component cannot change its props, but it is responsible for putting together the props of its child Component. Props do not have just to be data - callback functions may be passed in as props.

### What are controlled components? 

In HTML, form elememts such as input, select, textarea have their own state and update it based user input. When user submits a form the values of this elements are sent with the form.
With React it works differently. The component containing the form will keep track of the value of the input in its state and will re-render the component each time the callback function is fired as the state will be update. A form element whose value is controlled by React in this way callend a "controlled component".

### What is a higher order component?

A HOC is an advanced technique in React for reusing component logic. HOCs are not part of the React API. They are a pattern for reuse code, logic, and bootstrap astraction. They takes a component and returns a new component. The most common is Context and Redux's connect function.

### What are controlled and uncotrolled components in React?

#### Controlled component

A controlled component(dumb component) is one that takes its current value through props and notifies changes through callback like onChange.
A parent component controls it by handling the callback and managing his own state and passing new values as props to the controlled component.

#### Uncontrolled component

A uncontrolled component is one that stores its own state internaly, and you query the DOM using ref to find its current value when you need it. Its a bit more like traditional HTML.

### What are synthetic events in React?

Synthetic events is a cross-browser wrapper around the browser's native elements. It's API is same as the browser's native event, including stopPropagation() and preventDefault(), except the events work identically across all browsers.

### What is React fiber?

Fiber is a new reconcilation engine or reimplementation of core algoritm in React v16. The goal of React fiber is to increase its suitabulity for areas like animation, layout, gestures, abilyty to pause, or reuse work and asign priority to different types of updates and new concurrency primitives.

### What is Lifting state up in React?

When several components need to share the same changing data then it is recommended to lift shared state up to their closest common ancestor. That means if two child components share the same data from its parent, then move the state to parent instead of maintaining local state in both of the child components.

### What are portals in React?

Portals is a recommended way to render children into a DOM node that exist outside the DOM hierarchy of the parent component.

### Do Hooks replace render props and higher order components?

Both render props and hider-order components render only a single child but it most of the cases Hooks are a simpler way to serve this by reducing nesting in your tree.

## Redux

### What is Redux?

Redux is based on the idea that there should be only a single source of truth for your app state. The basic idea of Redux is that the entry app state is kept in a single store. The store is a JS object. The only way to change state is by firing actions from your app and then writing reducer for these actions that modify state. Reducers are clean functions and should not have any side-effects.

### Explain the components of Redux?

#### Action 
Actions are payloads of information that send data from our application to our store. They are the only source of information for the store. Primarly, they are just and object describes what happend in our app.

### Reducer 
Reducers specify how the application's state changes in response to actions sent to the store. So this place determines how state will change to an action.

### Store
The store is the object that brings Actions and Reducer together. 
The store has the following responsibilities: 
- Holds app state;
- Allow access to state via getState();
- Allow state to be update via dispatch(action);
- Register listeners;

## Javascript

### What the difference between Function Expression and Function Declaration?

Function Expression creates when the execution reaches it and can then be used.

Function Declaration can be used in all script or code block when function determined in block.

### What the difference between var, let and const?

var - haven't got block scope. They are limited by function's body. var announcement occurs at the beginning of the f-tion.

### Symbols, Objects, Map, Set, WeakMap, WeakSet, BigInt.

Symbol - is a primitive datatype used to create unique identifiers. Symbols are created by a call to the Symbol() function, to which you can pass Symbol description Symbol(name). Object.getOwnPropertySymbols(obj) with it you can get all the properties of an object with keys-symbols. There is also a Reflect.ownKeys(obj) method that returns an object keys. Even if the Symbol have the same name, they are different Symbols.

Map is a key/value collection just like Object. But the main difference is that Map allows you to use keys of any type.

Set is a special kind of collection (without keys) where each value can appear only once.

WeakMap is a Map-like collection that allows only objects to be used as keys and automatically deletes them together with their values as soon as they become innacessible another ways. 

WeakSet is a Set like collection that allows only objects and automatically deletes them as soon as they innacessible another ways.

### Closure 

Closure is the ability of a function to maintain its lexical enviroment when it is called outside its lexical enviroment.

### Lexical enviroment

The object of lexical enviroment consist of two parts:
- Enviroment record is an object where all local variables are stored as properties.
- A reference to an external is on that corresponds to the code externally(outside of currend curly brackets).
All functions receive a hidden property [[Enviroment]], which refers to a lexical enviroment of the place where they are created.

### Spread operator(...)

Spread operator is interpretated differently depending on the context. Spread is used to separate collections into separate elements and rest to merge individual values into an array.

### Event loop

- Select and execute the oldest tasks from the macrotasks queue.
- Execute all microtasks 
- - While the microtask queue is not empty: select from the queue and execute the oldest microtask
- Render page changes if any.
- If macrotasks queue is empty, wait until task appears.
- Go to step 1.
