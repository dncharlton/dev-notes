Functions are a type of value in JavaScript

##### Function Declaration
```js
function sayHi() {
  alert( "Hello" );
}
```

##### Function Expression
```js
let sayHi = function() {
  alert( "Hello" );
};                   // ; is purely visual, it is not required
```

In above examples, the declaration requires the user to call `sayHi()` in order to run the alert.
In the expression the variable `sayHi` received the value of the new function encapsulating the alert.

An example of both of these in action would be:
```js
function sayHi() {   // function declaration
  alert( "Hello" );
}

let func = sayHi;    // function expression

func(); // Hello     // alerts "Hello"
sayHi(); // Hello    // alerts "Hello"
```

##### Callback functions
A function that takes arguments and functions as arguments and return the required function bases off the the function criteria
```js
function ask(question, yes, no) {
  if (confirm(question)) yes()
  else no();
}

function showOk() {
  alert( "You agreed." );
}

function showCancel() {
  alert( "You canceled the execution." );
}

// usage: functions showOk, showCancel are passed as arguments to ask
ask("Do you agree?", showOk, showCancel);
```

If this was single use it could be written more simply as
```js
function ask(question, yes, no) {
  if (confirm(question)) yes()
  else no();
}

ask(
  "Do you agree?",
  function() { alert("You agreed."); },
  function() { alert("You canceled the execution."); }
);
```
This uses anonymous functions when calling `ask`, see `function() {}`

##### Function Expression vs Function Declaration
###### Function Expression
- Function Declaration: a function, declared as a separate statement, in the main code flow:

```js
// Function Declaration
function sum(a, b) {
  return a + b;
}
```

- A Function Expression is created when the execution reaches it and is usable only from that moment.
- In strict mode, when a Function Declaration is within a code block, it’s visible everywhere inside that block. But not outside of it.
- A Function Declaration is only visible inside the code block in which it resides.
###### Function Declaration
- Function Expression: a function, created inside an expression or inside another syntax construct. Here, the function is created on the right side of the assignment expression `=`:

```js
// Function Expression
let sum = function(a, b) {
  return a + b;
};
```

- A Function Declaration can be called earlier than it is defined.

##### Standard Function Summary
- Functions are values. They can be assigned, copied or declared in any place of the code.
- If the function is declared as a separate statement in the main code flow, that’s called a “Function Declaration”.
- If the function is created as a part of an expression, it’s called a “Function Expression”.
- Function Declarations are processed before the code block is executed. They are visible everywhere in the block.
- Function Expressions are created when the execution flow reaches them.

#### Arrow functions
Arrow functions assume a return of the expression at the end of the function.
```js
let func = (arg1, arg2, ..., argN) => expression;
```

Example translation of function expression to arrow function return the expression of arg1 + arg2:
```js
let sum = function(a, b) {
  return a + b;
};
```

```js
let sum = (a, b) => a + b;
```

The `sayHi` example can be written as:
```js
let sayHi = () => alert("Hello!");

sayHi();
```

They are very convenient for simple one-line actions, when we’re just too lazy to write many words.

##### Multiline arrow functions
We can use `{}` with arrow functions, however it now does not assume a return and requires it to be explicitly stated.

```js
let sum = (a, b) => {
  let result = a + b;
  return result; 
};

alert( sum(1, 2) );
```

##### Arrow Function Summary
Arrow functions are handy for simple actions, especially for one-liners. They come in two flavours:
- Without curly braces: (...args) => expression – the right side is an expression: the function evaluates it and returns the result. Parentheses can be omitted, if there’s only a single argument, e.g. n => n*2.
- With curly braces: (...args) => { body } – brackets allow us to write multiple statements inside the function, but we need an explicit return to return something.