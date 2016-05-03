# Components and Component Hierarchy

When you build UI's (user interfaces) with React, the line between HTML and JavaScript becomes a bit fuzzier. In React, you keep HTML and JavaScript together. Instead of splitting up your view in JavaScript and HTML, you split it up in __components__. You build out the separate pieces of your view in components, which you then compose to a whole.

For example, what are some of the different sections of this view:

![](../../assets/sample-view.png)!

A header, a menu and a content box with an image.

In React, this would translate to three components, each component holding the JavaScript and HTML for that section.

```js
<div>
  <Header />
  <Menu />
  <ContentBox />
</div>
```

### Exercise

What are some possible components of the following websites?

* https://www.girldevelopit.com/
* https://www.reddit.com/
* http://www.nytimes.com/

###

### Syntax

Each component has _one_ `render` function which returns what should be rendered on the DOM.

```js
var Menu = React.createClass({
  render: function() {
    return (
      <div>
        <a href="home.html">Home</a>
        <a href="about.html">About</a>
        <a href="contact.html">Contact</a>
      </div>
    )
  }
});
```

In the above component, we are writing JavaScript and returing HTML. This is great since it makes it easier to create abstractions around our view layer. As of now, there's some duplication in our component. The links are almost exactly the same. Instead, we can iterate over the menu types and create the link element dynamically.

In the return statements, JavaScript that we want to be evaluated (here, the local variables `type` and `capitalizedType`) should be enclosed in curly braces `{jsVariable}`.

```js
var Menu = React.createClass({
  render: function() {
    var types = ['home', 'about', 'contacts'];

    var links = types.map(function(type, i) {
      var capitalizedType = type.slice(0,1).toUpperCase() + type.slice(1)
      return (
        <a href="{type}.html" key={i}>{capitalizedType}</a>
      )
    });

    return (
      <div>
        {links}
      </div>
    )
  }
});
```

---

### Exercise

Let's write our first component!

In a new directory, create a file called `index.html`.

```html
<!DOCTYPE html>
<html>
<head>
  <title>React Example</title>
</head>
<body>

</body>
</html>
```

In the `<head>`, add the necessary React cdns. We also need to require [Babel](https://babeljs.io/), a JavaScript compiler. Some of the JSX is not recognized by browsers and needs to be "translated" to an older version of JavaScript.

```html
<head>
  <title>React Example</title>
  <script src="https://fb.me/react-15.0.1.js"></script>
  <script src="https://fb.me/react-dom-15.0.1.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.24/browser.min.js"></script>
</head>
```

We can add our React code straight in the HTML file using `<script>` tags. To make Babel compile the JavaScript, we add set the type to `text/babel`.

```html
<script type="text/babel">
  // react goes here
</script>
```

Time for React! Let's write a component called `HelloWorld` and, for now, render the string `Hello, World!`.

```html
<script type="text/babel">
  var helloWorld = React.createClass({
    render: function () {
      return (
        <h1>Hello, World!</h1>
      );
    }
  });
</script>
```

As of now, the React component doesn't yet show up on the page. We need to tell it to render. We call the function `ReactDOM.render()` with two arguments; the component that should be rendered and _where_ on the DOM it should render. In this case, we tell it to render in an html element with id `container`.

```html
<div id="container"></div>
<script type="text/babel">
  var helloWorld = React.createClass({
    render: function () {
      return (
        <h1>Hello, World!</h1>
      );
    }
  });

  ReactDOM.render(<helloWorld />, document.getElementById('container')
  );
</script>
```

### Extra

* Can you iterate over an array of names (`["Grace", "Margaret", "Anita"]`) and render them on the page? See the link example below if you are unsure.
* Can you render an input field, have the user inser their name and then render `Hello, UserName!`?

---

### Component Hierarchy

In React, we typically have one root component which renders all other components. In the sample view above, with a header, menu and content section, the view could be rendered in a `Root` component like this:

```js
var Root = React.createClass({
  render: function() {
    return (
      <div>
        <Header />
        <Menu />
        <ContentBox />
      </div>
    )
  }
});

ReactDOM.render(
  <Root />,
  document.getElementById('container');
);
```

The `Header` component might look something like this:

```js
var Header = React.createClass({
  render: function() {
    return (
      <div>
        <h1>Caporama Travels</h1>
        <p>Email | 123.456.7890</p>
      </div>
    )
  }
});
```

The `Menu` component might look something like this:

```
var Menu = React.createClass({
  render: function() {
    var types = ["menu", "about", "contact"];

    var links = types.map(function(type, i) {
      capitalized = type.slice(0,1).toUpperCase() + type.slice(1);
      return (
        <a href="{type}.html">{type}</a>
      )
    });

    return (
      <div>
        {links}
      </div>
    )
  }
});
```

and the `ContentBox` component might look something like this:

```
var ContentBox = React.createClass({
  render: function() {
    return (
      <div>
        <img src="/assets/las-ventas-group-photo.jpg">
        <h3>About Caporama Travels</h3>
        <p>
          // text
        <p>
      </div>
    )
  }
});
```

The `Root` component is rendering the `Header`, `Menu`, and `ContentBox` components. This makes it the `Root` the parent component to the components it renders. In this example, at the top of our component hierarchy is the `Root` component which renders all subsequent child components. You can visualize this either as a russian doll (each doll keeps the next one), or as a root system like below.

![](https://media.giphy.com/media/3JKjWIEcJvg9W/giphy.gif)

### Exercise

* What could the component hierarchy of the following pages be:
  * http://www.nytimes.com/
  * https://www.reddit.com
  * http://www.hummusapien.com/

---

Code:

```html
<!DOCTYPE html>
<html>
<head>
  <title>React Example</title>
  <script src="https://fb.me/react-15.0.1.js"></script>
  <script src="https://fb.me/react-dom-15.0.1.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.24/browser.min.js"></script>
</head>
<body>
  <div id="container"></div>
  <script type="text/babel">
    var HelloWorld = React.createClass({
      render: function () {
        return (
          <h1>Hello, World!</h1>
        );
      }
    });

    ReactDOM.render(
      <HelloWorld />,
      document.getElementById('container')
    );
  </script>
</body>
</html>
```
