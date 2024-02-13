Constructor Function
```javascript
const User = function (name) {
  this.name = name
  this.discordName = '@' + name
}
```

Factory Function
```javascript
function createUser (name) {
  const discordName = '@' + name
  return { name, discordName }
}
```

the returned value will be an object holding two values

Using closures and factory functions together expands functionality even further, e.g.

```javascript
function createUser (name) {
  const discordName = "@" + name;

  let reputation = 0;
  const getReputation = () => reputation;
  const giveReputation = () => reputation++;

  return { name, discordName, getReputation, giveReputation };
}

const josh = createUser("josh");
josh.giveReputation();
josh.giveReputation();

console.log({
  discordName: josh.discordName,
  reputation: josh.getReputation()
});
// logs { discordName: "@josh", reputation: 2 }
```

An example of this with a calculator would be:
```javascript
const calculator = (function () {
  const add = (a, b) => a + b;
  const sub = (a, b) => a - b;
  const mul = (a, b) => a * b;
  const div = (a, b) => a / b;
  return { add, sub, mul, div };
})();

calculator.add(3,5); // 8
calculator.sub(6,2); // 4
calculator.mul(14,5534); // 77476
```

More Examples
```js
const Formatter = (function() {
  const log = (message) => console.log(`[${Date.now()}] Logger: ${message}`);
  const timesRun = [];

  const makeUppercase = (text) => {
    log("Making uppercase");
    timesRun.push(null);
    return text.toUpperCase();
  };

  return {
    makeUppercase,
    timesRun,
  }
})();

console.log(Formatter.makeUppercase("tomek"));
console.log(Formatter.makeUppercase("tomek"));
console.log(Formatter.makeUppercase("tomek"));
console.log(Formatter.timesRun.length);

Formatter.log("Hello");
```

[Article on Scope](https://wesbos.com/javascript/03-the-tricky-bits/scope)
[Article on Closure](https://wesbos.com/javascript/03-the-tricky-bits/closures)
