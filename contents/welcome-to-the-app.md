# Welcome to the App

### Strategy #1

You can write React within `script` tags in HTML pulling in the React library with a [cdn](http://www.webopedia.com/TERM/C/CDN.html).

Create a new project, and an `index.html` file in that project. Copy the content below and view the html file in your browser.

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

### Strategy #2

If you would like to use develop React apps with webpack, npm and babel, clone [this repository](https://github.com/applegrain/super-simple-react-project).
