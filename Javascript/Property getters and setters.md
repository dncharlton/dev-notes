#### Getters/Setter
```javascript
let user = {
  firstName: "Tom",
  lastName: "Smith",
  
  get name() {
    return `${this.firstName} ${this.lastName}`
  },
  
  set name(value) {
    [this.firstName, this.lastName] = value.split(" ");
  }
}

console.log(user.name) //Tom Smith
user.name = "Daniel Charlton"
console.log(user.name) //Daniel Charlton
```


## [Accessor descriptors](https://javascript.info/property-accessors#accessor-descriptors)

Descriptors for accessor properties are different from those for data properties.

For accessor properties, there is no `value` or `writable`, but instead there are `get` and `set` functions.

That is, an accessor descriptor may have:

- **`get`** – a function without arguments, that works when a property is read,
- **`set`** – a function with one argument, that is called when the property is set,
- **`enumerable`** – same as for data properties,
- **`configurable`** – same as for data properties.

For instance, to create an accessor `fullName` with `defineProperty`, we can pass a descriptor with `get` and `set`:

```js
let user = {
  name: "John",
  surname: "Smith"
};

Object.defineProperty(user, 'fullName', {
  get() {
    return `${this.name} ${this.surname}`;
  },

  set(value) {
    [this.name, this.surname] = value.split(" ");
  }
});

alert(user.fullName); // John Smith

for(let key in user) alert(key); // name, surname
```

Please note that a property can be either an accessor (has `get/set` methods) or a data property (has a `value`), not both.

Example
```js
function User(name, birthday) {
  this.name = name;
  this.birthday = birthday;

  // age is calculated from the current date and birthday
  Object.defineProperty(this, "age", {
    get() {
      let todayYear = new Date().getFullYear();
      return todayYear - this.birthday.getFullYear();
    }
  });
}

let john = new User("John", new Date(1992, 6, 1));

alert( john.birthday ); // birthday is available
alert( john.age );      // ...as well as the age
```



