
In React, when a component's state or props change, the component is destroyed and recreated from scratch. This includes variables, functions and React nodes.
The entire component is recreated but this time the latest state value will be returned from `useState`. This process is called rerendering.

#### The useState Hook
The `useState` hook is a built-in hook in React that allows you to define state in a functional component.
It takes an initial value as a paramater and returns an array with two elements that we can deconstruct to get:
1. The current state value
2. A function to update the state value

```jsx
const [stateValue, setStateValue] = useState(initalValue);
```

#### Background update example:
```jsx
import React, { useState } from "react";
import "./App.css";

const COLORS = ["pink", "green", "blue", "yellow", "purple"];

function App() {
  const [backgroundColor, setBackgroundColor] = useState(COLORS[0]);

  const onButtonClick = (color) => () => {
    setBackgroundColor(color);
  };

  return (
    <div
      className="App"
      style={{
        backgroundColor,
      }}
    >
      {COLORS.map((color) => (
        <button
          type="button"
          key={color}
          onClick={onButtonClick(color)}
          className={backgroundColor === color ? "selected" : ""}
        >
          {color}
        </button>
      ))}
    </div>
  );
}

export default App;
```

Whenever `setBackgroundColor` is called, our `App` component is rerendered.
Essentially, the component is recreated which means the `onButtonClick` function and our `div` and `button`'s are recreated as well.
React takes the responsibility of keeping track of the latest state and providing it to the component.
The initial state value is only used for the component's first render and is ignored on subsequent renders.

![[background_update.png|1000]]

#### Hooks
Hooks are functions that let you use React features. All hooks are recognizable by the `use` prefix. For example, `useState` is a hook.
1. Hooks can only be called from the top level of a functional component
2. Hooks can't be called from inside loops or conditions

https://react.dev/learn/state-a-components-memory
https://react.dev/learn/render-and-commit


#### How to structure state
General rule: Don't put values in state that can be calculated using existing values, state, and/or props

##### State should not be mutated
State should be treated as though it were immutable, to change the state we should always use the `setState` function provided by our `useState`.
```jsx
function Person() {
  const [person, setPerson] = useState({ name: "John", age: 100 });

  // BAD - Don't do this!
  const handleIncreaseAge = () => {
    // mutating the current state object
    person.age = person.age + 1;
    setPerson(person);
  };

  // GOOD - Do this!
  const handleIncreaseAge = () => {
    // copy the existing person object into a new object
    // while updating the age property
    const newPerson = { ...person, age: person.age + 1 };
    setPerson(newPerson);
  };

  return (
    <>
      <h1>{person.name}</h1>
      <h2>{person.age}</h2>
      <button onClick={handleIncreaseAge}>Increase age</button>
    </>
  );
}
```

Using above example, we would only update the state with the `setPerson` function.
We can see that rather than mutating the `person` state variable, we create an updated copy of the current state, and then set the state using the new state object.

#### How State updated


