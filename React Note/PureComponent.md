<div>
  <h1>Pure Component</h1>
  <p>We have a lifecycle method called shouldComponentUpdate which by default returns true (Boolean) value.</p>
  <p><strong>Pure Components</strong> in React are the components which do not re-renders when the value of state and props has been updated with the same values. If the value of the previous state or props and the new state or props is the same, the component is not re-rendered.</p>
  <p><strong>Features of React Pure Components</strong></p>
  <ul>
    <li>Prevents re-rendering of Component if props or state is the same</li>
    <li>Takes care of “shouldComponentUpdate” implicitly</li>
    <li>State and Props are Shallow Compared</li>
    <li>Pure Components are more performant in certain cases</li>
  </ul>
</div>
