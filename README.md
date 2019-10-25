# React interview questions

## Virtual DOM

### 1. Differentiate between Real DOM and Virtual DOM.

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
