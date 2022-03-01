<div>
<h1>Event Handlers</h1>
<p>Event handlers determine what action is to be taken whenever an event is fired. This could be a button click or a change in a text input. Essentially, event handlers are what make it possible for users to interact with your application.</p>
<p>Handling events with react elements is similar to handling events on DOM elements, with a few minor exceptions.</p>
</div>
<div>
  <h2>onClick Handler</h2>
  <p>The React onClick event handler enables you to call a function & trigger an action when a user clicks an element, such as a button in your application.</p>
  <p>Event names are written in <strong>camelCase</strong>, so the onclick event is written as <strong>onClick</strong> in a react application. React event handlers appears inside <strong>curly braces</strong></p>
</div>
<div>
  <p>Example</p>
  <p>In HTML</p>

   ```
   <button onclick="abc()">Hi welcome</button>
   ```
  <p>In React</p>
  
  ```
   <button onClick={abc}>Hi welcome</button>
   ``` 
</div>
<div>
  <p>Another key difference is that, whereas you would simply <strong>return false</strong> to aviod default behavior in HTML, in react you must explicitly call <strong>PreventDefault</strong></p>
<span><strong>Note:</strong></span> 
<ul>
  <li>Don't add() in event handler</li>
  <li>Event handler is a function, and again don't add a function call</li>
</ul>
  
  ```
  <a href="#" onclick="console.log('The link was linked); return false" >Click me</a>
  ```
  
  ```
  import React from 'react'

  const App = () => {
    function handleClick(e) {
      e.preventDefault();
      document.write('the link was clicked');
    }
    return (
      <a href="#" onClick={handleClick}>Click me</a>
    )
  }

  export default App;
  ```

</div>
<div>
  <h2>Synthetic events in React</h2>
  <p>React implements a synthetic events system that brings consistency & high performance to React apps and interfaces. It achieves consistency by normalizing events so that they have the same properties across different browsers and plateforms.</p>
  <p>A synthetic event is a cross-browser wrapper around the browser's native event. It has the same interface as the browser's native event, including <strong>stopProgation()</strong> and <strong>preventDefault()</strong> expect the events work identically across all browsers</p>
  <p>It achieves high performace by automatically using event delegation. In actuality, React doesn't attach event handlers to the nodes themselves. Instead, a single event listener is attached to the root of the document. when an event is fired, React maps it to the appropriate component element.</p>
</div>
<div>
  <h2>Listening to events in React</h2>
  <p>Tolisten events in React, add the onClick attribute, which is the event handler to the target element. This specifies the function to be executed when that element is clicked.</p>
  
  ```
  import React, { Component } from 'react';

class Example2 extends Component {
  showAlert() {
    alert("I'm an alert");
  }
  render() {
    return (
      <div>
        <button onClick={this.showAlert}>Show Alert</button>
      </div>
    );
  }
}

export default Example2;
```
</div>

<div>
  <h1>Binding Event Handler</h1>
</div>
<div>
  <h2>Handling events in class components</h2>
  <h3>Binding in the render() method</h3>
  
  ```
  import React, { Component } from 'react';

class Example5 extends Component {
  constructor(props) {
    super(props);
    this.state = {
      name: '',
    };
  }
  ChangeText(event) {
    this.setState({
      name: event.target.value,
    });
  }
  render() {
    return (
      <div>
        <label htmlFor="name">Enter name</label>
        <input type="text" id="name" onChange={this.ChangeText.bind(this)} />
        <h3>{this.state.name}</h3>
      </div>
    );
  }
}

export default Example5;
```
  
  <h3>Binding in the constructor() method</h3>
  
  ```
  import React, { Component } from 'react';

class Example6 extends Component {
  constructor(props) {
    super(props);
    this.state = {
      name: '',
    };
    this.ChangeText = this.ChangeText.bind(this);
  }
  ChangeText(event) {
    this.setState({
      name: event.target.value,
    });
  }
  render() {
    return (
      <div>
        <label htmlFor="name">Enter name</label>
        <input type="text" id="name" onChange={this.ChangeText} />
        <h3>{this.state.name}</h3>
      </div>
    );
  }
}

export default Example6;
```
  <h3>Binding with arrow functions</h3>
  
  ```
  import React, { Component } from 'react';

class Example7 extends Component {
  handleEvent = (event) => {
    alert("I'm an clicked");
  };
  render() {
    return (
      <div>
        <button onClick={this.handleEvent}>Click me</button>
      </div>
    );
  }
}

export default Example7;
```
</div>

<div>
  <h2>Handling events in functional components</h2>
  <h3>Call an inline function in an onClick event handler</h3>
  <p>This is commonly used to avoid the extra function declaration outside the JSX, althrough it can be less readable and harder to maintain if the content of the inline function is too much.</p>
  
  ```
  import React from 'react';

const Example8 = () => {
  return (
    <>
      <button onClick={() => alert('Hello!')}>Click me</button>
    </>
  );
};

export default Example8;
```
  
<h3>Update the state inside an onClick event handler</h3>

```
import React, { useState } from 'react';

const Example9 = () => {
  const [count, setCount] = useState(0);
  return (
    <>
      <p>{count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <button onClick={() => setCount(count - 1)}>Decrement</button>
    </>
  );
};

export default Example9;
```

<h3>call multiple functions in an onClick event handler</h3>

```
import React, { useState } from 'react';

const Example10 = () => {
  const [count, setCount] = useState(0);
  const sayHello = () => {
    alert('Hello');
  };
  return (
    <>
      <p>{count}</p>
      <button onClick={() => {sayHello(); setCount(count + 1);}}>Hello and Increment</button>
    </>
  );
};

export default Example10;
```
</div>
