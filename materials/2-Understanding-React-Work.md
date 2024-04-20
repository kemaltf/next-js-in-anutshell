# Rendering User Interfaces (UI)

To understand how React works, we first need a basic understanding of how browsers interpret your code to create (or render) user interfaces (UI).

When a user visits a web page, the server returns an HTML file to the browser that may look like this:

![Alt text](/Image/2.png)

The browser then reads the HTML and constructs the Document Object Model (DOM).

## What is the DOM?

The DOM is an object representation of the HTML elements. It acts as a bridge between your code and the user interface, and has a tree-like structure with parent and child relationships.

![Alt text](/Image/3.png)

The DOM is like a behind-the-scenes map or blueprint of that web page. It represents the stucture of the page and allows programs (like JS) to interact with it. Just like

> Think of it this way: imagine a house. The house itself is like the web page, and the blueprint that shows where all the rooms are and how they’re connected is like the DOM. Just as you can use the blueprint to change things in the house, like adding furniture or painting the walls, you can use the DOM to change things on the web page, like adding new content or making elements move around.
