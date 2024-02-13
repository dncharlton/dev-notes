#### Key Differences Summary
- `var` declarations are globally scoped or function scoped while `let` and `const` are block scoped.
- `var` variables can be updated and re-declared within its scope; `let` variables can be updated but not re-declared; `const` variables can neither be updated nor re-declared.
- They are all hoisted to the top of their scope. But while `var` variables are initialised with `undefined`, `let` and `const` variables are not initialised.
- While `var` and `let` can be declared without being initialised, `const` must be initialised during declaration.

#### var
`var` are globally or functionally/locally scoped variables. The scope is global when the variable is defined outside of a function. 
`var` variables can be redeclared and updated.

`var`'s can be hoisted e.g:
```javascript
console.log (greeter);
var greeter = "say hello"
```
is interpreted as:
```javascript
var greeter;
console.log(greeter); // greeter is undefined
greeter = "say hello"
```

The re-declaration of `var` variables can become a problem when you redeclare variables unknowing that they have  been declared before. e.g.:
```javascript
var greeter = "hey hi";
var times = 4;

if (times > 3) {
  var greeter = "say Hello instead"; 
}

console.log(greeter) // "say Hello instead"
```

#### let
`let` blocks are scoped and are bound within their respective `{}` blocks. e.g:
```javascript
let greeting = "say Hi";
let times = 4;

if (times > 3) {
	let hello = "say Hello instead";
	console.log(hello);// "say Hello instead"
}
console.log(hello) // hello is not defined
```

`let` variables can be redefined by **not redeclared** e.g:
```javascript
let greeting = "say Hi";
if (true) {
  let greeting = "say Hello instead";
  console.log(greeting); // "say Hello instead"
}
console.log(greeting); // "say Hi"
```

In this instance both variables get treated as their own variables inside of their instances.

`let` also allows hoisting however instead of being `undefined` it will report a `Reference Error` as it will be left undefined.

#### const
`const` variables remain with the scope and cannot be redeclared or redefined. all `const` variables must be defined at the time of declaration. Example:
```javascript
const greeting = {
  message: "say Hi",
  times: 4
}
```
We cannot update greeting like below:
```javascript
greeting = {
  words: "Hello",
  number: "five"
} // error:  Assignment to constant variable.
```
But we can do this:
```javascript
  greeting.message = "say Hello instead";
```

Just like `let` and `var`, `const` can be hoisted but will report not initialized.
