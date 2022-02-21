<div>
  <h2>What Is Redux?</h2>
  <p>Redux is also a library which is used widely for front-end development.<br/>It is basically a tool for managing both data-state and UI-state in JavaScript applications. Redux separates the application data and business logic into its own container in order to let React manage just the view.</p>
</div>
<div>
  <h2>Why Redux With React?</h2>
  <p>React follows the component-based approach, where the data flows through the components.</p>
  <p>The data in React always flows from parent to child components which makes it unidirectional. <br/>This surely keeps our data organized and helps us in controlling the    application better.</p>
  <p>The application’s state is contained in specific stores and as a result, the rest of the components remain loosely coupled.<br/>This makes our application more flexible   leading to increased efficiency. That’s why communication from a parent component to a child component is convenient.</p>
  <p>But what happens when we try to communicate from a non-parent component?</p>
  <p>A child component can never pass data back up to the parent component. React does not provide any way for direct component-to-component communication.
  <br/>Even though React has   features to support this approach, it is considered to be a poor practice.</p>
</div>
<div>
  <h2>Principles Of Redux</h2>
  <p>Redux follows three fundamental principles:</p>
  <ul>
    <li><b>Single source of truth:</b> The state of the entire application is stored in an object/ state tree within a single store. The single state tree makes it easier to keep track of the changes over time and debug or inspect the application. For a faster development cycle, it helps to persist the application’s state in development.</li>
    <li><b>State is read-only:</b> The only way to change the state is to trigger an action. An action is a plain JS object describing the change. Just like the state is the minimal representation of data, the action is the minimal representation of the change to that data. An action must have a type property (conventionally a String constant). All the changes are centralized and occur one by one in a strict order.</li>
    <li><b>Changes are made with pure functions:</b> In order to specify how the state tree is transformed by actions, you need pure functions. Pure functions are those whose return values depend solely on the values of their arguments. Reducers are just pure functions that take the previous state and an action and return the next state. You can have a single reducer in your application and as it grows, you can split it off into smaller reducers. These smaller reducers will then manage specific parts of the state tree.</li>
  </ul>
</div>
