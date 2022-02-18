<div>
  <h1>useState</h1>
  <p>The useState Hook allows you to create, update and manipulate state inside functional components</p>
  <p>React has this concept of state, which are variables that hold data that our components depend on and many change over time.</p>
  <p>The value returned by useState() consists of an array with two values:
    <br/>The First value is the initial (or starting) value of the state variable.
    <br/>The Second value is a reference to the function that can be used to update the variable.</p>
  <p>Always use array destructing to assign both values at once so that they can be used in the component.</p> 
  <p>with every render, the function being rendered is a new one - how does the 'state' persist then? Behind the scenes, there's an object representing the functional      component in the memory, which has a stack of its own.<p>
  <p>whenever the useState() hook is used, the value of the state variable is changed and the new variable is stored in a new cell in the stack.</p>
  <p>The stack pointer is incremented simultaneously to point towards the last cell. The value pointed to by this stack pointer is used after every render on a deliberate refresh from the user, the stack is dumped, and a fresh allocation in the memory is done when the component is rendered</p>
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
```
import React, {useState} from 'react'

function App() {
  const [click, setClick] = useState(0);

  return (
    <div>
      <p>You're clicked {click} times!</p>
      <p>The number of times you have clicked is {click % 2 == 0 ? 'even!' :'odd!'} </p>
      <button onClick = {() => setClick(click => click+1)}> Click me </button>
    </div>
  );
}

export default App;
```

<p>Example: Updating state based on previous state (useState with a number)</p>

```
import React, { useState } from 'react';

function StepTracker() {
  const [steps, setSteps] = useState(0);
  function increment() {
    setSteps((prevState) => prevState + 1);
  }
  return (
    <div>
      Today you've taken {steps} steps!
      <br />
      <button onClick={increment}>I took another step</button>
    </div>
  );
}

export default StepTracker;
```
<p><b>useState with an array</b></p>

```
import React, { useState } from 'react';

function ListOfThings() {
  const [items, setItems] = useState([]);
  const [itemName, setItemName] = useState('');

  const addItem = (event) => {
    event.preventDefault();
    setItems([
      ...items,
      {
        id: items.length,
        name: itemName,
      },
    ]);
    setItemName('');
  };

  return (
    <>
      <form onSubmit={addItem}>
        <label>
          <input name="item" type="text" value={itemName} onChange={(e) => setItemName(e.target.value)}
          />
        </label>
      </form>
      <ul>
        {items.map((item) => (
          <li key={item.id}>{item.name}</li>
        ))}
      </ul>
    </>
  );
}

export default ListOfThings;
```
<p>State variables can be arrays too. This is especially useful when one needs to deal with multiple values without finding the need to declare multiple state variables using useState()</p>

```
import React, {useState} from 'react'

function App() {
  const [click, setClick] = useState([]);
  const addNumber = () => {
    setClick([...click, {id:click.length, value:Math.random()*10}]);
  };

  return (
    <div>
      <ul>
        {click.map(item => (<li key={item.id}> {item.value} </li>))}
      </ul>
      <button onClick = {addNumber}> Click me </button>
    </div>
  );
}

export default App;
```
```
import React, { useState } from 'react';

function LessText({ text, maxLength }) {
  const [hidden, setHidden] = useState(true);
  if (text.length <= maxLength) {
    return <span>{text}</span>;
  }
  return (
    <>
    <span>
      {hidden ? `${text.substr(0, maxLength).trim()} ...` : text}
      {hidden ? (
        <a onClick={() => setHidden(false)}> read more</a>
      ) : (
        <a onClick={() => setHidden(true)}> read less</a>
      )}
    </span>
  </>
  );
}

export default LessText; 

import React from "react";
import LessText from './components/useState/Example5';
function App() {
  return (
    <div>
      <LessText
    text={`Focused, hard work is the real key
      to success. Keep your eyes on the goal, 
      and just keep taking the next step 
      towards completing it.`}
    maxLength={35}
  />
    </div>
  );
}
export default App;
```
