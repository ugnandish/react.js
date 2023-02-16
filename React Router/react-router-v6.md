<h1>React Router v6 Guide</h1>
<p>React Router is the most popular routing library in React. This article will be broken down into 4 sections.</p>
<ol>
  <li>React Router Basics</li>
  <li>Advanced Route Definitions</li>
  <li>Handling Navigation</li>
  <li>Routers In Depth</li>
</ol>

<h2>React Router Basics</h2>
<p>In order to use React Router on the web you need to run <b>"npm i react-router-dom"</b> to install React Router.<br/>
If you are using React Native you will need to install react-router-native instead.</p>
<p>There are three things you need to do in order to use React Router.</p>
<ol>
  <li>Setup your router</li>
  <li>Define your routes</li>
  <li>Handle navigation</li>
</ol>

<h3>Configuring The Router</h3>
<p>All you need to do is <b>"import"</b> the specific router you need <b>"BrowserRouter for the web"</b> and <b>"NativeRouter for mobile"</b> and wrap your entire application in that router.</p>

```
import React from "react"
import ReactDOM from "react-dom/client"
import App from "./App"
import { BrowserRouter } from "react-router-dom"

const root = ReactDOM.createRoot(document.getElementById("root"))
root.render(
  <React.StrictMode>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </React.StrictMode>
)
```

<h3>Defining Routes</h3>
<p>Defining routes is as simple as defining a single <b>Route</b> component for each route in your application and then putting all those <b>Route</b> components in a single <b>Routes</b> component.<br/> 
Whenever your URL changes React Router will look at the routes defined in your <b>Routes</b> component and it will render the content in the <b>element</b> prop of the <b>Route</b> that has a <b>path</b> that matches the URL.</p>
<p>The nice thing about React Router is that when you navigate between pages it will only refresh the content inside your <b>Routes</b> component. All the rest of the content on your page will stay the same which helps with performance and user experience.</p>

```
import { Route, Routes } from "react-router-dom"
import { Home } from "./Home"
import { BookList } from "./BookList"

export function App() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/books" element={<BookList />} />
    </Routes>
  )
}
```

<h3>Handling Navigation</h3>
<p>Normally in an application you would navigate with anchor tags, but React Router uses its own custom <b>Link</b> component to handle navigation.<br/>
This <b>Link</b> component is just a wrapper around an anchor tag that helps ensure all the routing and conditional re-rendering is handled properly so you can use it just like your would a normal anchor tag.</p>

```
import { Route, Routes, Link } from "react-router-dom"
import { Home } from "./Home"
import { BookList } from "./BookList"

export function App() {
  return (
    <>
      <nav>
        <ul>
          <li><Link to="/">Home</Link></li>
          <li><Link to="/books">Books</Link></li>
        </ul>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/books" element={<BookList />} />
      </Routes>
    </>
  )
}
```

<p>Another thing to note about our new code is that the nav we are rending at the top of our page is outside of our <b>Routes</b> component which means when we change pages this nav section will not be re-rendered as only the content in the <b>Routes</b> component will change when the URL changes.</p>

<h2>Advanced Route Definitions</h2>
<ol>
  <li>Dynamic Routing</li>
  <li>Routing Priority</li>
  <li>Nested Routes</li>
  <li>Multiple Routes</li>
  <li>useRoutes Hook</li>
</ol>

<h3>Dynamic Routing</h3>
<p>The simplest and most common advanced feature in React Router is handling dynamic routes.</p>

```
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/books" element={<BookList />} />
  <Route path="/books/:id" element={<Book />} />
</Routes>
```

<p>The final route in the above example is a dynamic route that has a dynamic parameter of :id. Defining dynamic routes in React Router is as simple as putting a colon in front of whatever you want the dynamic part of your route to be.</p>
<p>Pretty much always when you have a dynamic route like this you want to access the dynamic value in your custom component which is where the <b>useParams</b> hook comes in.</p>

```
import { useParams } from "react-router-dom"

export function Book() {
  const { id } = useParams()

  return (
    <h1>Book {id}</h1>
  )
}
```

<p>The <b>useParams</b> hook takes no parameters and will return an object with keys that match the dynamic parameters in your route. In our case our dynamic parameter is <b>:id</b> so the <b>useParams</b> hook will return an object that has a key of <b>id</b> and the value of that key will be the actual id in our URL.</p>
