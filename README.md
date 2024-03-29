<h3>React Elements</h3>
<p>React elements mirror regular HTML elements in their syntax. Any valid HTML element can be expressed in React.</p>

```
<h1>My Header</h1>
<p>My paragraph</p>
<button>My button</button>

<img src="my-image.png" />
<br />
<hr />
```

<h3>React Element Attributes</h3>
<p>JSX introduces a modified syntax for attributes, aligning with JavaScript’s camelCase convention. For instance, the class attribute in HTML becomes className in JSX.</p>

```
<div className="container"></div>
```

<h3>React Element Styles</h3>
<p>Applying inline styles in JSX involves using double curly braces instead of double quotes. Styles are expressed not as plain strings, but as properties within objects:</p>

```
<h1 style={{ fontSize: 24, margin: '0 auto', textAlign: 'center' }}>My header</h1>
```

<h3>React Fragment</h3>
<p>React provides a special element known as a fragment to address the requirement of returning all elements within a single parent component. This is essential as React mandates a single “parent” for returned elements. If you prefer not to use a container element like a div, you can use a fragment:</p>

```
function MyComponent() {
  return (
    <>
      <h1>My header</h1>
      <p>My paragraph</p>
    </>
 );
}
```

<h3>React Components</h3>
<p>component names must kick off with a capital letter</p>

```
function App() {
  return (
     <div>Hello world!</div>
  );
}

or

const App = () => {
    return <div>Hello world!</div>
} 

```

<h3>React Props</h3>
<p>components have the ability to receive data passed down to them, which we refer to as props.</p>
<p>These props are dispatched from the parent component to the child component.</p>

```
function App() {
  return <User name="John Doe" />
}
function User(props) {
  return <h1>Hello, {props.name}</h1>; // Hello, John Doe!
}
```

Multiple Props

```
function App() {
  return <User name="John" age={23} />
}
function User(props) {
    return <p>{props.name}, {props.age}</p>
}
```

<p>For a cleaner code approach, especially when dealing with a single prop like “name,” object destructuring can be employed:</p>

```
function App() {
  return <User name="John Doe" />
}
function User({ name }) {
   return <h1>Hello, {name}!</h1>; // Hello, John Doe!
}

```

<h3>React Children Props</h3>
<p>Props can also be conveyed by placing data between the opening and closing tags of a component. These props, passed in this manner, reside within the children’s property.</p>
<p>Example: consider passing content between the tags of the User component:</p>

```
function App() {
return (
   <User>
     <h1>Hello, John Doe!</h1>
   </User>
);
}
function User({ children }) {
  return children; // Hello, John Doe!

}
```

<h3>React Conditionals</h3>
<p>React components and elements can be conditionally displayed. One approach is to employ a separate return statement with an if-statement.</p>

```
function App() {
const isAuthUser = useAuth();
  if (isAuthUser) {
    // if our user is authenticated, let them use the app
   return <AuthApp />;
  }
// if user is not authenticated, show a different screen
  return <UnAuthApp />;
}
```

<p>If you wish to create a conditional within a return statement. To utilize the ternary operator, enclose the entire conditional in curly braces.</p>

```
function App() {
const isAuthUser = useAuth();
  return (
    <>
      <h1>My App</h1>
      {isAuthUser ? <AuthApp /> : <UnAuthApp />}
    </>
  ) 
}
```

<h3>React Lists</h3>
<p>Lists of React components can be generated using the .map() function, which allows us to iterate over arrays of data and produce JSX.</p>

```
function Players() {
const players = ["Messi", "Ronaldo", "Laspada"];
  return (
    <div>
      {players.map((playerName) => (
        <Player key={playerName} name={playerName} />
      ))}
    </div>
  );
}
```

<p>To include the key prop when looping over an array of data, and this key must be assigned a unique value, not merely an element index. In the above example, a unique value, the playerName, serves as the key.</p>

<h3>React Context</h3>
<p>React Context serves as a mechanism for seamlessly conveying data throughout our component tree, eliminating the need for relying solely on props.</p>
<p>The challenge with props lies in the occasional need to pass them through intermediary components that don’t necessarily require the data—an issue commonly referred to as props drilling.</p>
<p>Example: Consider this simplified scenario where props are passed unnecessarily through a ‘Body’ component:</p>

```
function App() {
return (
    <Body name="John Doe" />
  );
} 
function Body({ name }) {
  return (
    <Greeting name={name} />
  );
} 
function Greeting({ name }) {
  return <h1>Welcome, {name}</h1>;
}
```

<p>When implementing Context, we employ the createContext function provided by React. This function can be called with an initial value that becomes the starting point for the context.</p>
<p>The resultant context comprises a Provider and a Consumer property, both functioning as components. The Provider is wrapped around the component tree where the data needs to be propagated, while the Consumer is placed within the component set to consume this value.</p>

```
import { createContext } from 'react';

const NameContext = createContext('');

function App() {
  return (
    <NameContext.Provider value="John Doe">
      <Body />
    </NameContext.Provider>
  );
} 

function Body() {
  return <Greeting />;
}

function Greeting() {
  return (
    <NameContext.Consumer>
      {name => <h1>Welcome, {name}</h1>}
    </NameContext.Consumer>
  );
}
```

<h2>React Hooks</h2>
<p>The React library has incorporated numerous essential hooks</p>
<ul>
  <li>useState</li>
  <li>useEffect</li>
  <li>useRef</li>
  <li>useContext</li>
  <li>useCallback</li>
  <li>useMemo</li>
</ul>

<h3>useState</h3>
<p>When using useState, we initiate it at the top of our component, optionally passing an initial value for its state variable.</p> 
<p>Employing array destructuring on the returned value allows us to access both the stored state and a function to update that state.</p>

syntax:

```
import { useState } from 'react';

function MyComponent() {
  const [stateValue, setStateValue] = useState(initialValue);
}
```

Example

```
import { useState } from 'react';
function Counter() {
  const [count, setCount] = useState(0);
  function updateCount() {
   setCount(count + 1);
  }
  return <button onClick={updateCount}>Count is: {count}</button>;
}
```

<h3>useEffect</h3>
<p>The React useEffect hook comes into play when we need to interact with the external environment, such as making API calls. Its primary purpose is to handle side effects, encompassing operations beyond our application with unpredictable outcomes.</p>
<p>The basic syntax of useEffect involves providing a function as the first argument and an array as the second argument.</p>

```
import { useEffect } from 'react';
function MyComponent() {
   useEffect(() => {
     // Perform side effect here
   }, []);
}
```


