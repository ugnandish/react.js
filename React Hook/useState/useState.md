<div>
  <h1>useState</h1>
  <p>The useState Hook allows you to create, update and manipulate state inside functional components</p>
  <p>React has this concept of state, which are variables that hold data that our components depend on and many change over time.</p>
  <p>The value returned by useState() consists of an array with two values:
    <br/>The First value is the initial (or starting) value of the state variable.
    <br/>The Second value is a reference to the function that can be used to update the variable.</p>
  <p>Always use array destructing to assign both values at once so that they can be used in the component.</p> 
</div>

```
import React, {useState} from 'react'

function App() {
  const click = useState('useState');
  return(
    <h1>welcome to {click}</h1>
  )
}

export default App;
```
```
import React, {useState} from 'react';

function App() {
  const [click, setClick] = useState(0);
  return (
    <div>
      <p>you clicked {click} times</p>
      <button onClick = {() => setClick(click +1)}> click me </button>
    </div>
  );
}

export default App;
```
