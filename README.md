<h3>React Elements</h3>
<p>React elements mirror regular HTML elements in their syntax. Any valid HTML element can be expressed in React.</p>

```
<h1>My Header</h1>
<p>My paragraph</p>
<button>My button</button>

<img src="my-image.png" />
<br />
<hr />
```

<h3>React Element Attributes</h3>
<p>JSX introduces a modified syntax for attributes, aligning with JavaScript’s camelCase convention. For instance, the class attribute in HTML becomes className in JSX.</p>

```
<div className="container"></div>
```

<h3>React Element Styles</h3>
<p>Applying inline styles in JSX involves using double curly braces instead of double quotes. Styles are expressed not as plain strings, but as properties within objects:</p>

```
<h1 style={{ fontSize: 24, margin: '0 auto', textAlign: 'center' }}>My header</h1>
```

<h3>React Fragment</h3>
<p>React provides a special element known as a fragment to address the requirement of returning all elements within a single parent component. This is essential as React mandates a single “parent” for returned elements. If you prefer not to use a container element like a div, you can use a fragment:</p>

```
function MyComponent() {
  return (
    <>
      <h1>My header</h1>
      <p>My paragraph</p>
    </>
 );
}
```


