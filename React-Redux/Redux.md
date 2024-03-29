<div>
  <h2>What Is Redux?</h2>
  <p>Redux is also a library which is used widely for front-end development.<br/>Redux is a predictable state container for JavaScript applications. As an application grows, it becomes difficult to keep it organized and maintain data flow. That is where Redux comes to the rescue.<br/>It is basically a tool for managing both data-state and UI-state in JavaScript applications. Redux separates the application data and business logic into its own container in order to let React manage just the view.</p>
</div>
<div>
  <h2>Why Redux With React?</h2>
  <p>React follows the component-based approach, where the data flows through the components.</p>
  <p>The data in React always flows from parent to child components which makes it unidirectional. <br/>This surely keeps our data organized and helps us in controlling the    application better.</p>
  <p>State transfer between components is pretty messy in React since it is hard to keep track of which component the data is coming from. It becomes really complicated if users are working with a large number of states within an application.</p>
  <p>But what happens when we try to communicate from a non-parent component?</p>
  <p>A child component can never pass data back up to the parent component. React does not provide any way for direct component-to-component communication.
  <br/>Even though React has   features to support this approach, it is considered to be a poor practice.</p>
  <p>Redux solves the state transfer problem by storing all of the states in a single place called a store. So, managing and transferring states becomes easier as all the states are stored in the same convenient store. Every component in the application can then directly access the required state from that store.</p>
</div>
<div>
  <h2>Principles of Redux</h2>
  <p>Redux follows three fundamental principles:</p>
  <ul>
    <li><b>Single source of truth:</b> The state of the entire application is stored in an object/ state tree within a single store. The single state tree makes it easier to keep track of the changes over time and debug or inspect the application. For a faster development cycle, it helps to persist the application’s state in development.</li>
    <li><b>State is read-only:</b> The only way to change the state is to trigger an action. An action is a plain JS object describing the change. Just like the state is the minimal representation of data, the action is the minimal representation of the change to that data. An action must have a type property (conventionally a String constant). All the changes are centralized and occur one by one in a strict order.</li>
    <li><b>Changes are made with pure functions:</b> In order to specify how the state tree is transformed by actions, you need pure functions. Pure functions are those whose return values depend solely on the values of their arguments. Reducers are just pure functions that take the previous state and an action and return the next state. You can have a single reducer in your application and as it grows, you can split it off into smaller reducers. These smaller reducers will then manage specific parts of the state tree.</li>
  </ul>
</div>
<div>
  <h2>Advantages of Redux</h2>
  <ul>
    <li><b>Predictability of outcome –</b> Since there is always one source of truth, i.e. the store, there is no confusion about how to sync the current state with actions and other parts of the application.</li>
    <li><b>Maintainability –</b> The code becomes easier to maintain with a predictable outcome and strict structure.</li>
    <li><b>Server side rendering –</b> You just need to pass the store that is created on the server, to the client side. This is very useful for initial render and provides a better user experience as it optimizes the application performance.</li>
    <li><b>Developer tools –</b> From actions to state changes, developers can track everything going on in the application in real time.</li>
    <li><b>Community and ecosystem –</b> Redux has a huge community behind it which makes it even more captivating to use. A large community of talented individuals contribute to the betterment of the library and develop various applications with it.</li>
    <li><b>Ease of testing –</b> Redux code are mostly functions which are small, pure and isolated. This makes the code testable and independent.</li>
    <li><b>Organization –</b> Redux is very precise about how the code should be organized, this makes the code more consistent and easier when a team works with it.</li>
  </ul>
</div>
