# Counter

![](http://recordit.co/YFm33ErFti.gif)

We are starting with this html template:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Counter</title>
  <script src="https://fb.me/react-15.0.1.js"></script>
  <script src="https://fb.me/react-dom-15.0.1.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.24/browser.min.js"></script>
</head>
<body>
  <div id="container"></div>
  <script type="text/babel"></script>
</body>
</html>
```

Feel free to start coding or pseudo coding right away if you already have a plan for how to get it working.

In **part 1** there's a brief plan on what steps to follow when implementing the al =>ity. **Part 2** is more descriptive and explains each step more in detail. I would suggest that you read through part 1 and use part 2 as a reference - the numbers for the steps in part 1 and part 2 correspond!

Use at least none, one or both!

### Part 1

Some questions to ask yourself before you start:

* How should the value of the `count` be stored and where?
* What is the difference in functionality between `Add` and `Subtract`? Could there possibly be some code share?
* Should the user be able to count below 0? If not, how could we make sure the `count` never goes below 0?

Suggested steps:

1. Create a `Counter` component that renders "Count: 0" (hardcode the number for now)
2. Use `ReactDOM.render()` to render the `Counter` component
3. Create a button `Add`
4. Add the event listener on the button
5. When the button is clicked, increase the count by 1 and render it instead of the hardcoded value
6. Add a `Subtract` button that reduces the count by 1


### Part 2

**1**: First we need a `Counter` component where our main functionality will live. As for now, let's just render an `h1` tag with the string hardcoded. When we have implemented the count functionality, we will dynamically render it instead.

```js
const Counter = React.createClass({
  render: () => {
    return (
      <div>
        <h1>Count: 0</h1>
      </div>
    )
  }
});
```

**2**: This won't be any fun if it doesn't render! We need to use `ReactDOM.render()` to render the component in a specific place on the DOM. Outside of the `script` tags, add an empty div with id `container`. The first argument to `ReactDOM.render()` is the component to render - `Counter` - and the second argument is where it should render - in the empty div with id `container`.

```js
ReactDOM.render(<Counter />, document.getElementById('container'));
```

**3**: Add the `Add` button in the return statement so we have something to click.

```
return (
  <div>
    <h1>Count: 0</h1>
    <button>Add</button>
  </div>
)
```

**4**: Nothing happens when we click the button because we haven't added a callback to it yet. A callback is a piece of code that is passed as an argument to other code, which is then expected to execute it at a convenient time. In our case, we want the `handleClick` function (yet to be written) to execute when we click the button so we can handle the "reaction" to the click there.

```
return (
  <div>
    <h1>Count: 0</h1>
    <button onClick={this.handleClick}>Add</button>
  </div>
)
```

**5**: First, let's add the `handleClick` function. Run this in your browser with the dev tools open (`cmd` + `option` + `i`) - if you see it logging to the console, it's wired up correctly!

```html
const Counter = React.createClass({
  handleClick: function() {
    console.log('helo')
  },

  render: function() {
    return (
      <div>
        <h1>Count: 0</h1>
        <button onClick={this.handleClick}>Add</button>
      </div>
    )
  }
});
```

How should this be stored in the component? The `count` is a value that we need to render and update throughout the lifetime of the component, so, let's add it as state.

Add an `getInitialState` function to set an initial value for the state. In our case, it's just `0`.

```html
const Counter = React.createClass({
  getInitialState: function() {
    return { count: 0 }
  },

  handleClick: function() {
....
```

In the handle click function, we want to increase the value of `this.state.count` by 1 every time the `Add` button is clicked. We use the `this.setState()` function from React which allows us to update the state of the component. Note that the `this` in `this.setState` refers to the component itself.

```html
handleClick: () => {
  const modifiedCount = this.state.count + 1
  this.setState({ count: modifiedCount });
}
```

Last step is to update the JSX to render the current value of `this.state.count` instead of the hardcoded value.

```html
return (
  <div>
    <h1>Count: {this.state.count}</h1>
    <button onClick={this.handleClick}>Add</button>
  </div>
)
```

Next, add a `Subtract` button which when clicked will decrease the count with 1. Start by having a separate callback function (use `handleSubtract()` and `handleAdd()` instead of `handleClick()`) and then try to refactor to using only one function (eg `handleClick()`).
