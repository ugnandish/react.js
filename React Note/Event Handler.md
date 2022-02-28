<div>
<h1>Event Handlers</h1>
<p>Event handlers determine what action is to be taken whenever an event is fired. This could be a button click or a change in a text input. Essentially, event handlers are what make it possible for users to interact with your application.</p>
<p>Handling events with react elements is similar to handling events on DOM elements, with a few minor exceptions.</p>
</div>
<div>
  <h1>onClick Handler</h1>
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

