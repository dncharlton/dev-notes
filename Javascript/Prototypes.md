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
