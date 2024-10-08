## Prototype Basics

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

An example same as above using an `Array`
```js
let y = [];
y.__proto__;
/*
Output
[constructor: ƒ, concat: ƒ, pop: ƒ, push: ƒ, …]
*/
y.__proto__.__proto__;
/*
Output
{constructor: ƒ, __defineGetter__: ƒ, __defineSetter__: ƒ, …}
*/
```

This second chain is referring to `Object.prototype` We cab test the internal `[[Prototype]]` against the `prototype` of the constructor function see that they are referring to the same thing.

```js
y.__proto__ === Array.prototype; // true
y.__proto__.__proto__ === Object.prototype; // true
```

We can also use the `isPrototype()` method to accomplish this
```js
Array.prototype.isPrototypeOf(y);      // true
Object.prototype.isPrototypeOf(Array); // true
```

We can also use the `instanceof` operator to test whether the `prototype` property of a constructor appears anywhere within an object's prototype chain
```js
y instanceorf Array; // true
```

To summarise, all JavaScript objects have a hidden, internal `[[Prototype]]` property (which may be exposed through `__proto__` in some browsers). Objects can be extended and will inherit the properties and methods on `[[Prototype]]` of their constructor.

These prototypes can be chained, and each additional object will inherit everything throughout the chain. The chain ends with the `Object.prototype`.

### Constructor Functions
```js
function Hero(name, level) {
  this.name = name;
  this.level = level;
}

let hero1 = new Hero('Bjorn', 1);

/*
console.log(hero1)
Hero { name: 'Bjorn', level: 1 }
*/


Object.getPrototypeOf(hero1);
/*
Output
constructor: f Hero(name, level)
*/
```

Output will only show defined properties and not methods in the constructor. It is common practice in JavaScript to define methods on the prototype for increased efficiency and code readability.




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
