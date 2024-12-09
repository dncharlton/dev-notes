
Using a key with below TODO list example, when the "key" is updated for any reason, React will match the keys of the previous list to the updates list.
If there are any changed, React will only update the items that have changed. This is more dynamic than using a custom prop such as `todo={todos}`.

Keys are passed into the component or a DOM element as a prop.
```jsx
<Component key={keyValue} />
//or
<div key={keyValue} />
```

An example of using keys with a TODO:
```jsx
const todos = [
  { task: "mow the yard", id: uuid() },
  { task: "Work on Odin Projects", id: uuid() },
  { task: "feed the cat", id: uuid() },
];

function TodoList() {
  return (
    <ul>
      {todos.map((todo) => (
        // here we are using the already generated id as the key.
        <li key={todo.id}>{todo.task}</li>
      ))}
    </ul>
  );
}
```

It is good practice to ensure that a unique ID is assigned to items in a list. Whether this is being handled by DB or yourself in frontend, this should be attached somehow.
