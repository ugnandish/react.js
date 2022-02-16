<html>
  <body>
    <h1>React.Memo</h1>
    <div>
    <h2>What is Memoization?</h2>
    <p>Memoization is a process that allows us to cache the values of recursive/expensive function calls so that the next time the function is called so that the next time the function is called with the same argument(s), the cached value is returned rather than having to re-compute the function.</p>
    </div>
    <div>
    <h2>Why use Memoization in React</h2>
    <p>In React functional components, when props within a component change, the entire component re-renders by default.
      <br/>In other words, if any value within a component updates, the entire components will re-render, including functions/components that have not had their values/props altered.</p>
    </div>
    <div>
      <h2>React.Memo()</h2>
      <p><b>React.Memo()</b> is a higher-order component that we can use to wrap components that we do not want to re-render unless props within them change</p>
    </div>
  </body>
</html>
