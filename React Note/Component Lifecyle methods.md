<div>
<h1>Component Lifecyle methods</h1>
<p>When we create a react component, the component goes several stages in its lifecycle React provides a bultin method that we can overwritten at particular stage in a lifecycle.</p>
</div>
<div>
  <h2>Lifecycle for Class Component</h2>
  <ul>
    <li><strong>Mounting:</strong> when an instance of a component is being created and inserted into the DOM</li>
    <li><strong>Updating:</strong> when a component is being re-rendered as a result of changes to either its props or state</li>
    <li><strong>Unmounting:</strong> when a component is being removed from the DOM</li>
    <li><strong>Error Handling:</strong> when there is an error during rendering in a lifecycle method or in the constructor of any child component.</li>
  </ul>
</div>
<div>
  <div>
    <h3>Mounting</h3>
    <ul>
      <li>constructor</li>
      <li>staticgetDerivedStateFromProps</li>
      <li>render</li>
      <li>componentDidMount</li>
    </ul>
  </div>
  <div>
    <h3>Updating</h3>
    <ul>
      <li>staticgetDerivedStateFromProps</li>
      <li>shouldComponentUpdate</li>
      <li>render</li>
      <li>getSnapShotBeforeUpdate</li>
      <li>componentDidUpdate</li>
    </ul>
  </div>
  <div>
    <h3>Unmounting</h3>
    <ul>
      <li>componentWillUnmount</li>
    </ul>
  </div>
  <div>
    <h3>Error Handling</h3>
    <ul>
      <li>staticgetDerivedStateFromError</li>
      <li>componentDidCatch</li>
    </ul>
  </div>
  
</div>
