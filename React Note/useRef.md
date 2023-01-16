<h1>useRef Hook</h1>
<p><b>Ref</b> means just reference, so it can be a reference to anything (DOM node, Javascript value, etc). The <b>useRef</b> hook returns a mutable object which doesn’t re-render the component when it’s changed. Think it like useState, but unlike <b>useState</b>, doesn’t trigger re-render of the component. The object that useRef returns have a current property that can hold any modifiable value.</p>
<p>
  
```Syntax:</b>
const refContainer = useRef(initialvalue); 

The initialValue is the initial .current property.
```
</p>

<h2>What is React useRef hook?</h2>
<p><b>useRef</b> is one of the standard hooks provided by React. It will return an object that you can use during the whole lifecyle of the component.</p>
<p>The main use case for the <b>useRef</b> hook is to access a DOM child directly.</p>
<p><b>useRef</b> can also be very useful to hold a mutable value across different renders of your component.</p>
<br/>
<p>you can initialize a new ref inside a component with the following code:</p>

```
// create a ref
const yourRef = useRef();
```

<p>you can optionally initialize it with a default value by passing it as an argument to the <b>useRef</b> hook</p>

```
// create a ref
const yourRef = useRef('hello world');
```

<p><b>Tip:</b> useRef is a hook, and as such can only be used in functional components! To use refs in class components, you have createRef instead</p>

<h2>How to use React useRef?</h2>
<p>To access a DOM element, you create a ref, assign it to the DOM element you want to target using its ref attribute, then you can use it!</p>
<p>once created, you can get and set the value of the ref by accessing the <b>.current</b> property of the object.</p>

```
//create a ref
const exampleRef = useRef();

//set the ref value
exampleRef.current = "Hello world";

//access the ref value
//this prints "Hello world" to the console
console.log(exampleRef.current);
```

For example, if you want to get the height in pixels of a DOM element.
```
import React from "react";
import { useEffect, useRef } from "react";

export default function App() {
  // create a ref
  const divElement = useRef();

  // trigger on the first render of the component 
  useEffect(() => {
    // get the height of the div element
    console.log(
      "The height of the div is: ", divElement.current.offsetHeight
    );
  }, []);

  return (
    <div ref={divElement}>
      <h1>Welcome to useRef!</h1>
    </div>
  );
}
```
<p><b>Tip:</b> In the above example I’ve used <b>useEffect</b> to only call <b>divElement.current.offsetHeight</b> once the component was first rendered. Indeed, at first, the ref is undefined, and it’s only once the component renders and the div is created that it holds its DOM element value!</p>

<h2>Warning of using useRef</h2>
<p>Some important things to keep in mind when using useRef are:</p>

<h3>A ref changing value doesn’t trigger a re-render</h3>
<p>For example, the following code has a bug! Can you find where it is?</p>

```
import React from "react";
import { useRef } from "react";

export default function App() {
  // create a ref
  const counter = useRef(0);

  // increase the counter by one
  const handleIncreaseCounter = () => {
    counter.current = counter.current + 1;
  };

  return (
    <div>
      <h1>Learn about useRef!</h1>
      <h2>Value: {counter.current}</h2>
      <button onClick={handleIncreaseCounter}>
        Increase counter
      </button>
    </div>
  );
}
```

<p>The issue is that clicking the button increases the variable counter as expected, but it doesn’t trigger a re-render so we see nothing on the screen!</p>

<h3>It is useless to add a ref to a dependency array</h3>
<p>Adding a ref to a dependency array will not trigger the callback! <br/>
For example, in the following example, you can click on the button all you want and it won’t print anything to the console!</p>

```
import React from "react";
import { useEffect, useRef } from "react";

export default function App() {
  // create a ref
  const counter = useRef(0);

  // increase the counter by one
  const handleIncreaseCounter = () => {
    counter.curent = counter.current + 1;
  };

  useEffect(() => {
    console.log("counter changed to: ", counter.current);
  }, [counter]);

  return (
    <div>
      <h1>Learn about useRef!</h1>
      <h2>Value: {counter.current}</h2>
      <button onClick={handleIncreaseCounter}>
Increase counter
    </button>
    </div>
  );
}
```

<p>To fix both of these bugs, you should use useState instead of useRef:</p>

```
import React from 'react';
import { useEffect, useState } from "react";

export default function App() {
  // create a counter
  const [counter, setCounter] = useState(0);

  // increase the counter by one
  const handleIncreaseCounter = () => {
    setCounter(counter + 1);
  };

  useEffect(() => {
    console.log("counter changed to: ", counter);
  }, [counter]);

  return (
    <div>
      <h1>Learn about useRef!</h1>
      <h2>Value: {counter}</h2>
      <button onClick={handleIncreaseCounter}>
        Increase counter
      </button>
    </div>
  );
}
```

<h3>When to avoid using useRef?</h3>
<p>Most of the time, if you want to persist state across re-renders of your components you should be using useState instead of useRef. Defaulting to useState, and then only using useRef.</p>

<h2>Examples</h2>
<h3>Example 1</h3>

```
function Form () {
  const nameRef = React.useRef()
  const emailRef = React.useRef()
  const passwordRef = React.useRef()

  const handleSubmit = e => {
    e.preventDefault()

    const name = nameRef.current.value
    const email = emailRef.current.value
    const password = passwordRef.current.value

    console.log(name, email, password)
  }

  return (
    <>
      <label>
        Name:
        <input
          placeholder="name"
          type="text"
          ref={nameRef}
    />
      </label>
      <label>
        Email:
        <input
          placeholder="email"
          type="text"
          ref={emailRef}
        />
      </label>
      <label>
        Password:
        <input
          placeholder="password"
          type="text"
          ref={passwordRef}
        />
      </label>

      <hr />

      <button onClick={() => nameRef.current.focus()}>
        Focus Name Input
      </button>
      <button onClick={() => emailRef.current.focus()}>
        Focus Email Input
      </button>
      <button onClick={() => passwordRef.current.focus()}>
        Focus Password Input
      </button>

      <hr />

      <button onClick={handleSubmit}>Submit</button>
    </>
  )
}
```
