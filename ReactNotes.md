
# React.memo(Component)
* React.memo prevents unnecessary re-rendering i.e re-render on unchanged props.
* React.memo can not prevent rendering when render it is intentionally triggerd (by state change or effect)

UseMemo
```js
import React, { useEffect } from "react";

function MemoExample({ count }) {
  useEffect(() => {
    console.log("MemoExample Renderd : " + count);
  });
  return <div>UsingMemo</div>;
}

export default MemoExample;

```
in above example Component WILL ONLY render when there is change in its props.

# States in React
* State in react is Component's memory object which can change over lifetime of component.
* Change in state triggers re-rendering.

useState()
```js
import React, { useState } from "react";
import UsingMemo from "./components/UsingMemo";

function App() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <button
        onClick={() => {
          setCount((prev) => prev + 1);
        }}
      >
        Increase Count : {count}
      </button>
    </div>
  );
}

export default App;
```
> It is always recommended to make our state as simple as possible and ***minimize the number of stateful components***.

# What are synthetic events in React?
`SyntheticEvent` is a cross-browser wrapper around the browser's native event. Its API is same as the browser's native event, including `stopPropagation()` and `preventDefault()`, except the events work identically across all browsers. The native events can be accessed directly from synthetic events using `nativeEvent` attribute.

Let's take an example of BookStore title search component with the ability to get all native event properties

```js
    function BookStore() {
      function handleTitleChange(e) {
        console.log("The new title is:", e.target.value);
        // 'e' represents synthetic event
        const nativeEvent = e.nativeEvent;
        console.log(nativeEvent);
        e.stopPropagation();
        e.preventDefault();
      }

      return <input name="title" onChange={handleTitleChange} />;
    }
```

### What is "key" prop and what is the benefit of using it in arrays of elements?

A `key` is a special attribute you **should** include when mapping over arrays to render data. _Key_ prop helps React identify which items have changed, are added, or are removed.
Keys should be unique among its siblings. Most often we use ID from our data as _key_:

```jsx harmony
const todoItems = todos.map((todo) => <li key={todo.id}>{todo.text}</li>);
```

When you don't have stable IDs for rendered items, you may use the item _index_ as a _key_ as a last resort:

```jsx harmony
    const todoItems = todos.map((todo, index) => (
      <li key={index}>{todo.text}</li>
    ));
```

**Note:**

1. Using _indexes_ for _keys_ is **not recommended** if the order of items may change. This can negatively impact performance and may cause issues with component state.
2. If you extract list item as separate component then apply _keys_ on list component instead of `li` tag.
3. There will be a warning message in the console if the `key` prop is not present on list items.
4. The key attribute accepts either string or number and internally convert it as string type.
5. Don't generate the key on the fly something like `key={Math.random()}`. Because the keys will never match up between re-renders and DOM created everytime.

# Shadow DOM vs Virtual DOM
The Shadow DOM is a browser technology designed primarily for scoping variables and CSS in web components. The Virtual DOM is a concept implemented by libraries in JavaScript on top of browser APIs.

# Controlled vs Uncontrolled Components
* Controlled components controls the input field in forms using states and input value and state value always in sync.
* Uncontrolled components uses ***ref*** to query data from input fields and input values are managed by DOM itself.

# createElement() vs cloneElement()
When react creates new element it uses createElement and whent it re-renders any element it just clones it and changes props of the data and replaces it with Actual Node.

# HOC in react
Components which provides additional functionality to an existing component are called HOC 
Uses:
* Code reuse, logic and bootstrap abstraction.
* Render hijacking.- (adding additional props to component to change its rendering behaviour.)
* State abstraction and manipulation.
* Props manipulation.

# ReactDOM.createPortal()
Portal is a recommended way to render children into a DOM node that exists outside the DOM hierarchy of the parent component. When using CSS transform in a component, its descendant elements should not use fixed positioning, otherwise the layout will blow up.
```js
ReactDOM.createPortal(child, container);
```
# Props validation in react
When the application is running in development mode, React will automatically check all props that we set on components to make sure they have correct type. If the type is incorrect, React will generate warning messages in the console. It's disabled in production mode due to performance impact. The mandatory props are defined with isRequired.

* PropTypes.number
* PropTypes.string
* PropTypes.array
* PropTypes.object
* PropTypes.func
* PropTypes.node
* PropTypes.element
* PropTypes.bool
* PropTypes.symbol
* PropTypes.any

  ```js
import React from "react";
import PropTypes from "prop-types";

function User({ name, age }) {
  return (
    <>
      <h1>{`Welcome, ${name}`}</h1>
      <h2>{`Age, ${age}`}</h2>
    </>
  );
}

User.propTypes = {
  name: PropTypes.string.isRequired,
  age: PropTypes.number.isRequired,
};
  ```
