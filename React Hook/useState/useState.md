<div>
  <h1>useState</h1>
  <p>The useState Hook allows you to create, update and manipulate state inside functional components</p>
  <p>React has this concept of state, which are variables that hold data that our components depend on and many change over time.</p>
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
