# Getting Started With React

## Keep in mind

1. Reactjs a JavaScript package that simplifies the construction of graphic user interfaces.
2. You can think react as library (Js code pre-made)
3. react-dom provides DOM-specific methods that enable you to use React with the DOM. (it means you can manipulate the UI with JS)

## Step to produce

To use React in your newly created project, load two React scripts from an external website called unpkg.com.

```js index.html
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
```

Last time we develop like this:

```html index.html
<html>
  <body>
    <div id="app"></div>
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <script type="text/javascript">
      const app = document.getElementById('app');
      const header = document.createElement('h1');
      const text = 'Develop. Preview. Ship.';
      const headerContent = document.createTextNode(text);
      header.appendChild(headerContent);
      app.appendChild(header);
    </script>
  </body>
</html>
```

Instead of directly manipulating the DOM with plain JavaScript, remove the DOM methods that you had added previously, and add the ReactDOM.createRoot() method to target a specific DOM element and create a root to display your React Components in. Then, add the root.render() method to render your React code to the DOM.

Like i said before, it is PRE-MADE. So basically its already created, we just need to import this function and than we can create similar like before. BUT in easy way.

If you see, it is more readable and easy to develop.

```js index.html
<html>
  <body>
    <div id="app"></div>
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/jsx">
      const app = document.getElementById('app'); const root =
      ReactDOM.createRoot(app); root.render(<h1>Develop. Preview. Ship.</h1>);
    </script>
  </body>
</html>
```

But..
If you try to run this code in the browser, you will get a syntax error:

This is because <h1>...</h1> is not valid Javascript. This piece of code is JSX.

## What is JSX

Dont confuse with JSX term. JSX in easy way means HTML inside Javascript. So now you can write HTML syntax inside Javascript!

Because of that browsers don't understand JSX out of the box, so you'll need a JavaScript compiler. So behind the scene, before your code running in the browser it will compile your JSX into plain HTML and plain JS so browser can understand.

> You might asking what is the compiler name? the compiler name is BABEL.

So again, we import babel inside our project:

```js index.html
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
```

In addition, you will need to inform Babel what code to transform by changing the script type to type=text/jsx.

```html index.html
<html>
  <body>
    <div id="app"></div>
    <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <!-- Babel Script -->
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/jsx">
      const domNode = document.getElementById('app');
      const root = ReactDOM.createRoot(domNode);
      root.render(<h1>Develop. Preview. Ship.</h1>);
    </script>
  </body>
</html>
```

To confirm it's working correctly, open your HTML file in the browser.

## Lets compare

Comparing the declarative React code you just wrote:

```html index.html
<script type="text/jsx">
  const domNode = document.getElementById("app")
  const root = ReactDOM.createRoot(domNode);
  root.render(<h1>Develop. Preview. Ship.</h1>);
</script>
```

to the imperative JavaScript code you wrote in the previous section:

```js
<script type="text/javascript">
  const app = document.getElementById('app'); const header =
  document.createElement('h1'); const text = 'Develop. Preview. Ship.'; const
  headerContent = document.createTextNode(text);
  header.appendChild(headerContent); app.appendChild(header);
</script>
```
