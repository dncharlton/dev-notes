1. Return a single root element

```jsx
function App() {
  return (
    <>
      <h1>Example Heading 1</h1>
      <h2>Example Heading 2</h2>
    </>
  );
}
```

2. Close all tags

```jsx
function App() {
  return (
    <>
      <input />
      <li></li>
    </>
  );
}
```

3. camelCase **most** things

```jsx
function App() {
  return (
   <div className="container">
     <svg>
       <circle cx="25" cy="75" r="20" stroke="green" strokeWidth="2" />
     </svg>
   </div>
  );
}
```


Converting HTML to JSX Example:

```html
<h1>Test title</h1>
<ol class="test-list">
  <li>List item 1
  <li>List item 2
  <li>List item 3
</ol>
<svg>
   <circle cx="25" cy="75" r="20" stroke="green" stroke-width="2" />
</svg>
<form><input type="text"></form>
```

1. Add single root element
2. Close li and input tags
3. camelCase 

```jsx
<div>
  <h1>Test title</h1>
  <ol className="test-list">
    <li>List item 1</li>
    <li>List item 2</li>
    <li>List item 3</li>
  </ol>
  <svg>
    <circle cx="25" cy="75" r="20" stroke="green" strokeWidth="2" />
  </svg>
  <form>
    <input type="text" />
  </form>
</div>
```

