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




