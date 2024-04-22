
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





