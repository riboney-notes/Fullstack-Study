# React Offical Docs Notes

_Notes based on the "main concepts" section in the official react [docs](https://reactjs.org/docs/hello-world.html)_

## 2: JSX Intro

**JSX**
- combines HTML and JS
- produces React elements

**Embedding expressions in JSX**
- valid js expressions can be placed in between curly braces `{...}`
- ex: `<h1>Hello, {getUserName()}</h1>`

**Specifying attributes with JSX**
- Use quotes to specify string literals as attributes
- Use curly braces for embedding js expressions in an attribute
- React DOM uses camelCase naming convention for HTML attribute names
  - ex: `className` is `class` in HTML; `tabIndex` is `tabindex` in HTML

**JSX under the hood**
- JSX expressions are equivalent to `React.createElement()` calls

## 3: Rendering Elements

**React elements **
- they represent the UI
  - by way of representing DOM tags or user-defined components
- components composed of one or many elements

**Rendering**
- to render react elements, pass the DOM element with the id `root` to `ReactDOM.createRoot()` to produce a `root` object
- then, render react elements by passing it to the root object with `roote.render()`
- ex:

```js
const root = ReactDOM.createRoot(
  document.getElementById('root')
);
const element = <h1>Hello, world</h1>;
root.render(element);

// displays "Hello, World" on the page
```

**Updating rendered elements**
- Since react elements are immutable, the only way to update the UI is to create a new element and pass it to `root.render()`
- in practice, `root.render()` is usually only called once
- React DOM only updates the DOM elements that has been changed, instead of updating the entire UI tree

## 4: Components and Props

**Components**
- Organizes UI into independent, reusable pieces that accepts some input ("props") and returns React elements
- Component name must start with capital letter
  - otherwise, its treated as a DOM tag
- ComponeNts can refer to other components (by using them or returning them)
- ex:

```js
// valid react component because it accepts single argument (props) and returns a React element
function Welcome(props){
  return <h1>Hello {props.name}</h1>
}
```

**Props**
- single object that encapsualtes JSX attributes and children
- React passes `props` into user-defined components
  - Ex: `const element = <Welcome name="Sara" />;`
- props are read-only
  - a component must never modify its own props
  - Side Note: pure functions are functions that don't change their inputs and always return the same result for the same set of inputs
    - react components must act like pure functions with respect to their props
  - instead of modifying props, `state` is utilized

## 5: State and Lifecycle

**State**
- similiar to props
- private and fully controlled by the component
- See [page](https://reactjs.org/docs/state-and-lifecycle.html#adding-local-state-to-a-class) for example on how to more `props` value to state and have the component re-render itself based on state change
