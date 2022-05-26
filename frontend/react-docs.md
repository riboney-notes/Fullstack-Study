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

**React elements**
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

**Lifecycle methods**
- `componentDidMount()` is a lifecylce method that runs after the component output has been rendered to the DOM
  - used for setting up action that will potentially be removed in the future to free up resources
- `componentWillUnmount()`
  - used for tearing down operations to free up resources

**Using state**
- State should not be modified directly
  - Ex: WRONG -> `this.state.comment = 'some new comment';`
  - State should be modified with `setState()`
    - Ex: `this.setState({comment: 'Hello'});`
- State updates may be asynchrounous
  - React may batch multiple `setState()` calls into a single update for performance
  - Because of this, `this.props` and `this.state` values should not be relied on for calculating next state since they are updated asynchrouously
    - ex:
    ```js
    // Wrong
    this.setState({
      counter: this.state.counter + this.props.increment,
    })
    ```
    - Correct way would be to pass a function into setState, ex:
    ```js
    // function passed into setState receives previous state as first agurment
    //   and the props at the time the update is applied as second argument
    this.setState(function(state,props){
      return {
        counter:state.counter + props.increment
      }
    });
    ```
- State updates are merged
  - when `setState()` is called, React merges the object that is provided in the current state
  - only provided properties are replaced; the rest are just copied over

- Data flow
  - Data flow in react is usually unidirectional from top to bottom (parent to child)
  - data is passed down, usually not propagated upwards

## 6: Handling Events

**Syntaxical differences of React events and DOM events**
- React events uses camelCase naming convention
- Functions are passed in for event handlers, not strings
  - Ex: 
    - HTML -> `<button onclick="activateLasers()">...</button>` 
    - JSX -> `<button onClick={activateLasers}>...</button>`

**Preventing default form behavior**
- In HTML, to prevent default form behavior, you return `false` in the `onsubmit` event handler method
- In react, you have to call `event.preventDefault()` inside the event handler method
  - NOTE: `event` object is referred to as `SyntheticEvent`; its defined according to DOM specs, but does not work exactly the same

**Passing arguments to event handlers**
- To pass extra arguments into an event handler function, this is the way you would do it:
  - Ex: `<button onClick={ e => deleteRow(extraArg, e)}>...</button>`

## 7: Conditional Rendering

- Example

```js
function Greeting(props) {
  const isLoggedIn = props.isLoggedIn;
  if (isLoggedIn) {
    return <UserGreeting />;
  }
  return <GuestGreeting />;
  
  const root = ReactDOM.createRoot(document.getElementById('root')); 
  root.render(<Greeting isLoggedIn={false} />);

}
```
