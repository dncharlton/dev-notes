Evert object in JavaScript has. `[[Prototype]]` We can demonstrate this with below:
```js
let x = {};
// or
let x = new Object();
```
To find the new `[[Prototype]]` of this newly created object, we will use `getPrototypeOf()` method:
```js
Object.getPrototypeOf(x);
/*
Output
{constructor: ƒ, __defineGetter__: ƒ, __defineSetter__: ƒ, …}
*/
```
Another way top find the `[[Protoype]]` is using the `__proto__` property. `__proto__` is a property that exposes the internal `[[Protoyype]]` of an object.
```js
x.__proto__;
/*
Output
{constructor: ƒ, __defineGetter__: ƒ, __defineSetter__: ƒ, …}
*/
```

When attempting to access a property or method of an object, JS will first search on the object itself, and if it is not ofund, it will search the objects `[[Prototype]]`. If after consulting both the object and the `[[Prototype]]` still no match is found, JS will check the prototype of the linked object and continue until the end of the prototype chain is reached.

At the end of the prototype chain in `Object.prototype`. All objects inherit the properties and methods of `Object`. Any attempt to search beyond the end of the chain results in `null`.

In our example, `x` is an empty object that inherits from `Object`. `x` can use any property or method that `Object` has, such as `toString()`.

```js
x.toString();
/*
Output
[object Object]
*/
```

The prototype chain is only one link long. `x` -> `Object`. We know this, because if we try to chain two `[[Prototype]]` properties together, it will be `null`.
```js
x.__proto__.__proto__;
/*
Output
null
*/
```



**Example**
```javascript
function Person(name) {
  this.name = name;
}

Person.prototype.sayName = function() {
  console.log(`Hello, I'm ${this.name}!`);
};

function Player(name, marker) {
  this.name = name;
  this.marker = marker;
}

Player.prototype.getMarker = function() {
  console.log(`My marker is '${this.marker}'`);
};

// Object.getPrototypeOf(Player.prototype) should
// return the value of "Person.prototype" instead
// of "Object.prototype"
Object.getPrototypeOf(Player.prototype); // returns Object.prototype

// Now make `Player` objects inherit from `Person`
Object.setPrototypeOf(Player.prototype, Person.prototype);
Object.getPrototypeOf(Player.prototype); // returns Person.prototype

const player1 = new Player('steve', 'X');
const player2 = new Player('also steve', 'O');

player1.sayName(); // Hello, I'm steve!
player2.sayName(); // Hello, I'm also steve!

player1.getMarker(); // My marker is 'X'
player2.getMarker(); // My marker is 'O'
```
