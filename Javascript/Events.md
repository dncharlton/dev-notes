#### Method 1
```html
<button onclick="alert('Hello World')">Click Me</button>
```

#### Method 2
```html
<button id="btn">Click Me</button>
```

```js
const btn = document.querySelector('#btn');
btn.onclick = () => alert("Hello World");
```

#### Method 3
```html
<button id="btn">Click Me Too</button>
```

```js
const btn = document.querySelector('#btn');
btn.addEventListener('click', function (e) {
  alert("Hello World");
});
// 'e' is an object that references the event itself e.target contain the DOM
```


#### More examples:
```html
<div id="container">
    <button id="1">Click Me</button>
    <button id="2">Click Me</button>
    <button id="3">Click Me</button>
</div>
```

```js
// buttons is a node list. It looks and acts much like an array.
const buttons = document.querySelectorAll('button');

// we use the .forEach method to iterate through each button
buttons.forEach((button) => {

  // and for each one we add a 'click' listener
  button.addEventListener('click', () => {
    alert(button.id);
  });
});
```

Some useful events include:
- click
- dblclick
- keydown
- keyup