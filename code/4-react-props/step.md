# Displaying Data with Props

So far weve code like this:

```html
<html>
  <body>
    <div id="app"></div>
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <!-- Babel Script -->
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/jsx">
      const app = document.getElementById("app")

      // Must be capitalized
      function Header() {
         return (<h1>Develop. Preview. Ship.</h1>)
       }

      const root = ReactDOM.createRoot(app);
      // We use our compontent like HTML
      root.render(<Header />);
    </script>
  </body>
</html>
```

But what if you want to pass different text or you don't know the information ahead of time because you're fetching data from an external source?

Regular HTML elements have attributes that you can use to pass pieces of information that change the behavior of those elements.

- For example, changing the src attribute of an <img> element changes the image that is shown.
- Changing the href attribute of an <a> tag changes the destination of the link.

In the same way, you can pass pieces of information as properties to React components. These are called props. Take for instance, the possible variations of a button:

Similar to a JavaScript function, you can design components that accept custom arguments (or props) that change the component's behavior or what is visibly shown when it's rendered to the screen.

Then, you can pass down these props from parent components to child components.

## Using props

In your HomePage component, you can pass a custom title prop to the Header component, just like you'd pass HTML attributes:

```html
function HomePage() { return (
<div>
  <header title="React" />
</div>
); }
```

And Header, the child component, can accept those props as its first function parameter:

```js
function Header(props) {
  return <h1>Develop. Preview. Ship.</h1>;
}
```

If you console.log() props, you can see that it's an object with a title property.

```js
function Header(props) {
  console.log(props); // { title: "React" }
  return <h1>Develop. Preview. Ship.</h1>;
}
```

Since props is an object, you can use object destructuring to explicitly name the values of props inside your function parameters:

```js
function Header({ title }) {
  console.log(title); // "React"
  return <h1>Develop. Preview. Ship.</h1>;
}
```

Then you can replace the content of the <h1> tag with your title variable.

```js
function Header({ title }) {
  console.log(title);
  return <h1>title</h1>;
}
```

If you open your file in the browser, you will see that it is displaying the actual word "title". This is because React thinks you're intending to render a plain text string to the DOM.

You need a way to tell React that this is a JavaScript variable.

## Using variables in JSX

To use the title prop, add curly braces {}. These are a special JSX syntax that allows you to write regular JavaScript directly inside your JSX markup.

```js
function Header({ title }) {
  console.log(title);
  return <h1>{title}</h1>;
}
```

You can think of curly braces as a way to enter "JavaScript land" while you are in "JSX land". You can add any JavaScript expression (something that evaluates to a single value) inside curly braces. For example:

1. An object property with dot notation:

```js
function Header(props) {
  return <h1>{props.title}</h1>;
}
```

2. A template literal:

```js
function Header({ title }) {
  return <h1>{`Cool ${title}`}</h1>;
}
```

3. The returned value of a function

```js
function createTitle(title) {
  if (title) {
    return title;
  } else {
    return 'Default title';
  }
}

function Header({ title }) {
  return <h1>{createTitle(title)}</h1>;
}
```

4. Or ternary operators:

```js
function Header({ title }) {
  return <h1>{title ? title : 'Default Title'}</h1>;
}
```

You can now pass any string to your title prop, or, if you used the ternary operator, you could even not pass a title prop at all, since you've accounted for the default case in your component:

```js
function Header({ title }) {
  return <h1>{title ? title : 'Default title'}</h1>;
}

function HomePage() {
  return (
    <div>
      <Header />
    </div>
  );
}
```

Your component now accepts a generic title prop which you can reuse in different parts of your application. All you need to do is change the title string:

```js
function HomePage() {
  return (
    <div>
      <Header title="React" />
      <Header title="A new title" />
    </div>
  );
}
```

5. Iterating through lists

It's common to have data that you need to show as a list. You can use array methods to manipulate your data and generate UI elements that are identical in style but hold different pieces of information.

Add the following array of names to your HomePage component:

```js
function HomePage() {
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];

  return (
    <div>
      <Header title="Develop. Preview. Ship." />
      <ul>
        {names.map((name) => (
          <li>{name}</li>
        ))}
      </ul>
    </div>
  );
}
```

You can then use the array.map() method to iterate over the array and use an arrow function to map a name to a list item:

```js
function HomePage() {
  const names = ['Ada Lovelace', 'Grace Hopper', 'Margaret Hamilton'];

  return (
    <div>
      <Header title="Develop. Preview. Ship." />
      <ul>
        {names.map((name) => (
          <li>{name}</li>
        ))}
      </ul>
    </div>
  );
}
```

Notice how you've used curly braces to weave in and out of "JavaScript" and "JSX" land.

If you run this code, React will give us a warning about a missing key prop. This is because React needs something to uniquely identify items in an array so it knows which elements to update in the DOM.

You can use the names for now since they are currently unique, but it's recommended to use something guaranteed to be unique, like an item ID.

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
    </div>
  );
}
```
