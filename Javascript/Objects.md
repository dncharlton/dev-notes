**Object Literals**
```js
const myObject = {
  property: 'Value!',
  otherProperty: 77,
  "obnoxious property": function() {
    //function stuff here
  }
};
```

There are two ways to get information out of an object: Dot Notation and Bracket Notation
```js
// Dot Notation
myObject.property; // this will return the property 'Value!'

// Bracket Notation
myObject["otherProperty"]; // this is equivelant to myObject.otherProperty
// this can also be used with variables
const variable = 'otherProperty'
myObject[variable]; // this is equivelant to myObject["otherProperty"]
```

Dot notation is usually the preferred choice, but for some situations it is not possible to use.
For example `myObject."obnoxious variable"` is not possible as the property is a string

**Object Constructors**
```js
function Player(name, marker) {
  this.name = name;
  this.marker = marker;
}

const player = new Player('steve', 'X');
console.log(player.name) // 'steve'
```

```js
function Player(name, marker) {
  this.name = name;
  this.marker = marker;
  this.sayName = function() {
	console.log(this.name)
  };
}

const player1 = new Player('steve', 'X');
const player2 = new Player('also steve', 'O');
player1.sayName(); // 'steve'
player2.sayName(); // 'also steve'
```

