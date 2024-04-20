#### Rendering a list of elements in JSX

```jsx
function App() {
  return (
    <div>
      <h1>Animals: </h1>
      <ul>
        <li>Lion</li>
        <li>Cow</li>
        <li>Snake</li>
        <li>Lizard</li>
      </ul>
    </div>
  )
}
```

We can use an array to map its objects with embedded expressions using curly braces

```jsx
function App() {
  const animals = ["Lion", "Cow", "Snake", "Lizard"];

  return (
    <div>
      <h1>Animals: </h1>
      <ul>
        {animals.map((animal) => {
          return <li key={animal}>{animal}</li>;
        })}
      </ul>
    </div>
  );
}
```

We can also define do above as below:

```jsx
function App() {
  const animals = ["Lion", "Cow", "Snake", "Lizard"];
  const animalsList = animals.map((animal) => <li key={animal}>{animal}</li>)

  return (
    <div>
      <h1>Animals: </h1>
      <ul>
        {animalsList}
      </ul>
    </div>
  );
}
```


#### Rendering a list of components in JSX

```jsx
function ListItem(props) {
  return <li>{props.animal}</li>
} 

function List(props) {
  return (
    <ul>
      {props.animals.map((animal)}
	</ul>
  )
}
```