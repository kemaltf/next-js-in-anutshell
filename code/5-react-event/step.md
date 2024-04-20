# Adding Interactivity

## Listening to events

Lets say we wanted to build some interface so you can add Like button inside the interface.

```js
function HomePage() {
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];

  return (
    <div>
      <Header title="Develop. Preview. Ship." />
      <ul>
        {names.map((name) => (
          <li key={name}>{name}</li>
        ))}
      </ul>
      <button>Like</button>
    </div>
  );
}
```

But the button not working for now. To make the button do something when clicked, you can use onClick event.

```js
function HomePage() {
  // ...
  return (
    <div>
      {/* ... */}
      <button onClick={}>Like</button>
    </div>
  );
}
```

> In React, event names are camelCased. The onClick event is one of many possible events you can use to respond to user interaction. For example, you can use onChange for input fields or onSubmit for forms.

## Handling events

You can define a function to "handle" events whenever they are triggered. Create a function before the return statement called handleClick():

```js
function HomePage() {
  // ...

  function handleClick() {
    console.log('increment like count');
  }

  return (
    <div>
      {/* ... */}
      <button onClick={handleClick}>Like</button>
    </div>
  );
}
```
