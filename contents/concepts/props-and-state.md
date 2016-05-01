# Props and State

### Props

Parent components render child components, and through that link, parent components can send data down to child components. This means that we can introduce another layer of abstraction around our UI; information that we need in multiple components can be maintained in one place, and be passed down to the components that need that information.

For example, in the `Caporama Travels` sample view, the name of the company is included in both the `Header` and the `ContentBox`. Instead of having it hardcoded in the `Header` component and the `ContentBox` component, we can pass the `title` down from the `Root` component to the child components as a `prop`.

Below, the local variable `title` is being passed down as the prop `companyTitle`. The way we access these values in the `Header` and `ContentBox` component is by `this.props.companyTitle`.

**Root component**
```js
var Root = React.createClass({
  render: function() {
    var title = "Caporama Travels";

    return (
      <div>
        <Header companyTitle={title} />
        <Menu />
        <ContentBox companyTitle={title} />
      </div>
    )
  }
});

ReactDOM.render(
  <Root />,
  document.getElementById('container');
);
```

**Header component**
```js
var Header = React.createClass({
  render: function() {
    return (
      <div>
        <h1>{this.props.companyTitle}</h1>
        <p>Email | 123.456.7890</p>
      </div>
    )
  }
});
```

**ContentBox component**
```js
var ContentBox = React.createClass({
  render: function() {
    return (
      <div>
        <img src="/assets/las-ventas-group-photo.jpg">
        <h3>About {this.props.companyTitle}</h3>
        <p>
          // text
        <p>
      </div>
    )
  }
});```

**NOTE: Props are immutable in the child component!**

### Exercise

* In our React example, pass a `name` property to the `HelloWorld` component and render the greeting using the passed down prop. For example, if the value of the `name` property passed down is `Elsa`, the greeting should be `Hello, Elsa!`.
* Can you pass down multiple props to render a dynamic greeting and introduction? Examples on props: `location`, `age`, `name`, `interests`.
* Can you have the user enter their `location`, `age`, `name`, `interests` through input fields and then render the greeting and introduction with the user input?

### State

`State` is local to a component and it can only be updated from within that component. State can be passed down to child components as props.

When dealing with state in component, you need to define an initial value for it. For example, let's say we have a component with a button. When the button is clicked, we should increase a counter by 1.

Below, we have a `getInitialState` function. Here, we define a `clicked` state. We can access this value in the component as `this.state.clicked`, see the `h1` tag in the return statement. Also note the comma after the `getInitialState` function, in React components we separate functions with commas (components are just objects, and key value pairs in JavaScript are delimited by commas).

```js
var ClickableComponent = React.createClass({
  getInitialState: function() {
    return { clicked: 0 }
  },

  render: function() {
    return (
      <div>
        <button>Click me!</button>
        <h1>Clicked: {this.state.clicked}</h1>
      </div>
    )
  }
});
```

Currently, when we click the button, nothing happens. We need to add an event handler which can react to the button click. There are tons of [event handlers](https://facebook.github.io/react/docs/events.html) in React, they support almost all native browser events. We are going to use the `onClick` event handler.

```js
var ClickableComponent = React.createClass({
  getInitialState: function() {
    return { clicked: 0 }
  },

  handleClick: function() {
    console.log('Clicked!');
  },

  render: function() {
    return (
      <div>
        <button onClick={this.handleClick} >Click me!</button>
        <h1>Clicked: {this.state.clicked}</h1>
      </div>
    )
  }
});
```

Did you see `Clicked!` in your browser log?

What we really want to do in the `handleClick` function is to update the value of `this.state.clicked`. We can do this by using the `setState` function.

```js
handleClick: function() {
  this.setState({ clicked: ++this.state.clicked })
},
```

Now, if we check the browser, the counter increases with every click!

### Exercise

* Add a button that will decrease the counter by 1.
* Build on the `ClickableComponent`. Add another state `names` and set it to an empty array. Add an input field and set the placeholder to `Enter your name!`. When the user enters their name and clicks the button `Submit`, the name should be added to `this.state.names`. Iterate over the array of names and use them to output them in `p` tags as `Hello, Username!`.
