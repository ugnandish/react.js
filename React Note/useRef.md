<h1>useRef hook</h1>
<p><b>Ref</b> means just reference, so it can be a reference to anything (DOM node, Javascript value, etc). The <b>useRef</b> hook returns a mutable object which doesn’t re-render the component when it’s changed. Think it like useState, but unlike <b>useState</b>, doesn’t trigger re-render of the component. The object that useRef returns have a current property that can hold any modifiable value.</p>
<p>
  
```Syntax:</b>
const refContainer = useRef(initialvalue);
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
