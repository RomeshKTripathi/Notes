
# React.memo(Component)
* React.memo prevents unnecessary re-rendering i.e re-render on unchanged props.
* React.memo can not prevent rendering when render it is intentionally/explicitly triggerd (by state change or effect)

React.memo
```js
import React, { useEffect } from "react";

function MemoExample({ count }) {
  useEffect(() => {
    console.log("MemoExample Renderd : " + count);
  });
  return <div>UsingMemo</div>;
}

export default React.memo(MemoExample);

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
> [!NOTE]
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
### `React.createElement()`
`React.createElement()` is used to create new element in DOM but it is not recommended to use because it is hard to debug and maintain
```js
import React from 'react';
import "./styles.css";
const title = React.createElement('h1',
    { className: 'title' }, 'GeeksforGeeks');
const App = () =>
    React.createElement('div', {}, [
        React.createElement('button', { className: 'btn' }, title),
        React.createElement('button', { className: 'btn' }, title),
    ]);
 
export default App;
```
In above example a div element is created using `React.createElement()`.
### `React.cloneElement()`
`React.cloneElement()` is can clone an existing element and can change its props.
```js
//App.js
import React from 'react';
import Button from './Button';
import './styles.css';
const App = () => {
	return (
		<Parent>
			<Button />
			<br /><br />
			<Button />
		</Parent>
	)
}

const Parent = (props) => {
	let btn = 'GeeksforGeeks';
	return (
		<div>
			{React.Children.map(props.children,
				child => {
					return React.cloneElement(child,
						{ btn }, null); 
					// third parameter is null
					// Because we are not adding
					// any children
				})}
		</div>
	)
}

export default App;
```
In above code we have modified an elements exisitng state by changing its _props_.


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
# Switching Component in React
Switching component renders one of many components, we can use Object map to achive switching component
```js
import Component1 from './Component1';
import Component2 from './Component2';
import Component3 from './Component3';
import Component4 from './Component4';

const PAGES = {
component1:Component1,
component2:Component2,
component3:Component3,
component4:Component4,
}

const Pages = (props)=>{
const Handler = PAGES[props.page] || Component4;
return <Handler />;
}
```

> [!NOTE]
> We cant use `for` loop in jsx because , JSX tags are transpiled into _function_ calls, and you can't use statements inside expressions. This may change thanks to `do` expressions which are _stage 1 proposal_.

# Why we can't update props in react ?
The react _Philosopy_ is that props should be ***Immutable***(Read Only) and _top down_. This means that a parent can send any prop values to a child, but the child can't modify received props.

# Can we use ***async/await*** in plain `React`?
If you want to use `async`/`await` in _React_, you will need _Babel_ and _transform-async-to-generator_ plugin. React Native ships with Babel and a set of transforms.
> [!NOTE]
> You can't use `async`/`await` directly to your _React_ component.

# Folder Structure in React:

## Grouping by feature of route
```txt
common/
├─ Avatar.js
├─ Avatar.css
├─ APIUtils.js
└─ APIUtils.test.js
feed/
├─ index.js
├─ Feed.js
├─ Feed.css
├─ FeedStory.js
├─ FeedStory.test.js
└─ FeedAPI.js
profile/
├─ index.js
├─ Profile.js
├─ ProfileHeader.js
├─ ProfileHeader.css
└─ ProfileAPI.js
```

## Grouping By fileType
```txt
api/
├─ APIUtils.js
├─ APIUtils.test.js
├─ ProfileAPI.js
└─ UserAPI.js
components/
├─ Avatar.js
├─ Avatar.css
├─ Feed.js
├─ Feed.css
├─ FeedStory.js
├─ FeedStory.test.js
├─ Profile.js
├─ ProfileHeader.js
└─ ProfileHeader.css
```

# React Animation Popular Packages
`React Transition` and `React Motion` are popular animation packages in react.

# State Management
### Flux
_flux_ is an _application design paradigm_ used as a replacement for the traditional MVC pattern. It is not a framework or a library but a new kind of architecture that complements React and the concept of Unidirectional Data Flow. Facebook uses this pattern internally when working with React.
The workflow between dispatcher, stores and views components with distinct inputs and outputs as follows.



![flux](https://github.com/user-attachments/assets/823f7cde-a028-4ffd-9f08-7529befc4cab)


### Redux
_Redux_ is predictable state container for JavaScript apps based on the _Flux design Pattern_. Redus can be use together with React, or with any other view library. It is tiny (about 2kb) and has no dependencies.

```
Redux follows three fundamental principles:

Single source of truth: The state of your whole application is stored in an object tree within a single store. The single state tree makes it easier to keep track of changes over time and debug or inspect the application.
State is read-only: The only way to change the state is to emit an action, an object describing what happened. This ensures that neither the views nor the network callbacks will ever write directly to the state.
Changes are made with pure functions: To specify how the state tree is transformed by actions, you write reducers. Reducers are just pure functions that take the previous state and an action as parameters, and return the next state.
```







