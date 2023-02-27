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

<h3>Routing Priority</h3>
<p>When we were just dealing with hard coded routes it was pretty easy to know which route would be rendered, but when dealing with dynamic routes it can be a bit more complicated.</br> For example.</p>

```
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/books" element={<BookList />} />
  <Route path="/books/:id" element={<Book />} />
  <Route path="/books/new" element={<NewBook />} />
</Routes>
```

<p>If we have the URL <b>/books/new</b> which route would this match? Technically, we have two routes that match.</br> Both <b>/books/:id</b> and <b>/books/new</b> will match since the dynamic route will just assume that new is the <b>:id</b> portion of the URL so React Router needs another way to determine which route to render.</p>
<p>In older versions of React Router whichever route was defined first would be the one that is rendered so in our case the <b>/books/:id</b> route would be rendered which is obviously not what we want.<br/> Luckily, version 6 of React Router changed this so now React Router will use an algorithm to determine which route is most likely the one you want.<br/> In our case we obviously want to render the <b>/books/new</b> route so React Router will select that route for us.</p> <p>The actual way this algorithm works is very similar to CSS specificity since it will try to determine which route that matches our URL is the most specific (has the least amount of dynamic elements) and it will select that route.</p>
<p>I also want to talk about how to create a route that matches anything.</p>

```
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/books" element={<BookList />} />
  <Route path="/books/:id" element={<Book />} />
  <Route path="/books/new" element={<NewBook />} />
  <Route path="*" element={<NotFound />} />
</Routes>
```

<p>A <b>"*"</b> will match anything at all which makes it perfect for things like a 404 page. A route that contains a <b>"*"</b> will also be less specific than anything else so you will never accidentally match a <b>"*"</b> route when another route would have also matched.</p>

<h3>Nested Routes</h3>
<p>This nesting is pretty simple to do.</p>
<p>All you need to do is make a parent <b>Route</b> that has the <b>path</b> prop set to the shared path for all your child <b>Route</b> components.<br/>
Then inside the parent <b>Route</b> you can put all the child <b>Route</b> components.<br/>
The only difference is that the <b>path</b> prop of the child <b>Route</b> components no longer includes the shared <b>/books</b> route.<br/>
Also, the route for <b>/books</b> is replaced with a <b>Route</b> component that has no <b>path</b> prop, but instead has an index prop. 
All this is saying is that the path of the index <b>Route</b> is the same as the parent <b>Route.</b></p>
<p>For example we have three routes that start with <b>/books</b> so we can nest those routes inside of each other to clean up our routes.</p>

```
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/books">
    <Route index element={<BookList />} />
    <Route path=":id" element={<Book />} />
    <Route path="new" element={<NewBook />} />
  </Route>
  <Route path="*" element={<NotFound />} />
</Routes>
```

<h3>Shared Layouts</h3>
<p>Let's imagine that we want to render a nav section with links to each book as well the new book form from any of our book pages.<br/>
To do this normally we would need to make a shared component to store this navigation and then import that into every single book related component.<br/>
This is a bit of a pain, though, so React Router created its own solution to solve this problem. If you pass an <b>element</b> prop to a parent route it will render that component for every single child <b>Route</b> which means you can put a shared nav or other shared components on every child page with ease.</p>

```
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/books" element={<BooksLayout />}>
    <Route index element={<BookList />} />
    <Route path=":id" element={<Book />} />
    <Route path="new" element={<NewBook />} />
  </Route>
  <Route path="*" element={<NotFound />} />
</Routes>
```

```
import { Link, Outlet } from "react-router-dom"

export function BooksLayout() {
  return (
    <>
      <nav>
        <ul>
          <li><Link to="/books/1">Book 1</Link></li>
          <li><Link to="/books/2">Book 2</Link></li>
          <li><Link to="/books/new">New Book</Link></li>
        </ul>
      </nav>

      <Outlet />
    </>
  )
}
```

<p>The way our new code will work is whenever we match a route inside the <b>/book</b> parent <b>Route</b> it will render the <b>BooksLayout</b> component which contains our shared navigation.<br/>
Then whichever child <b>Route</b> is matched will be rendered wherever the <b>Outlet</b> component is placed inside our layout component.<br/>
The <b>Outlet</b> component is essentially a placeholder component that will render whatever our current page's content is. This structure is incredibly useful and makes sharing code between routes incredibly easy.</p>
<p>Now the final way you can share layouts with React Router is by wrapping child <b>Route</b> components in a parent <b>Route</b> that only defines an <b>element</b> prop and no <b>path</b> prop.</p>

```
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/books" element={<BooksLayout />}>
    <Route index element={<BookList />} />
    <Route path=":id" element={<Book />} />
    <Route path="new" element={<NewBook />} />
  </Route>
  <Route element={<OtherLayout />}>
    <Route path="/contact" element={<Contact />} />
    <Route path="/about" element={<About />} />
  </Route>
  <Route path="*" element={<NotFound />} />
</Routes>
```

<p>This bit of code will create two routes, <b>/contact</b> and <b>/about</b>, which both are rendered inside the <b>OtherLayout</b> component. This technique of wrapping multiple <b>Route</b> components in a parent <b>Route</b> component with no <b>path</b> prop is useful if you want those routes to share a single layout even if they don't have a similar path.</p>

<h4>Outlet Context</h4>
<p>The final important thing to know about Outlet components is they can take in a context prop which will work just like React context.</p>

```
import { Link, Outlet } from "react-router-dom"

export function BooksLayout() {
  return (
    <>
      <nav>
        <ul>
          <li><Link to="/books/1">Book 1</Link></li>
          <li><Link to="/books/2">Book 2</Link></li>
          <li><Link to="/books/new">New Book</Link></li>
        </ul>
      </nav>

      <Outlet context={{ hello: "world" }} />
    </>
  )
}
```

```
import { useParams, useOutletContext } from "react-router-dom"

export function Book() {
  const { id } = useParams()
  const context = useOutletContext()

  return (
    <h1>Book {id} {context.hello}</h1>
  )
}
```

<p>we are passing down a context value of <b>{ hello: "world" }</b> and then in our child component we are using the <b>useOutletContext</b> hook to access the value for our context. This is a pretty common pattern to use since often you will have shared data between all your child components which is the ideal use case for this context.</p>
