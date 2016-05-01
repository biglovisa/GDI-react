# Data Down, Events Up

Ok, so we know we can use `props` to pass down data to the child components. We know that props are immutable in the child components. Consider this; we have a `Root` components that's rendering a `Names` component. The `Names` components recieve an array of names from the `Root` component. In the `Name` component, we iterate over the array of names and render them on the page.

Now, we want to add a `remove` button next to each name so the user can remove names from the list. Since we are getting the array of names as a prop from the parent, we can't update the array in the `Names` component. We need to "signal" to the parent component that a change needs to be made to the array of names.

We do that by passing down a function as prop to the child component. That function accepts the index of the name we would like to remove from the array of names. When the child component wants to remove a name, we call the function passed down to us, and give it the index position as an argument. That function in the parent component will [filter](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) out the name with an index matching the index passed as an argument.

Let's code it!

The `Root` component has a `getInitialState` function which sets the initial value of our state, and in the return statement we render a component `Names` and pass it the array of names as a prop.

```js
var Root = React.createClass({
  getInitialState: function() {
    return { names: ["Grace", "Margaret", "Anita"] }
  },

  render: function() {
    return (
      <div>
        <Names names={this.state.names} />
      </div>
    )
  }
});
```

The `Names` component might look something like this:

```js
var Names = React.createClass({
  render: function() {
    var names = this.props.names.map(function(name, i) {
      return (
        <p key={i}>Hello, {name}!</p>
      )
    });

    return (
      <div>
        {names}
      </div>
    )
  }
});
```

In the `Names` component, let's add a button to remove the given name. The button has an `onClick` event handler, when it's clicked, the `handleClick` function at the top of the component is executed. The `handleClick` function takes an argument. In the `onClick` event handler, we bind the index of the name to be removed to the function call.

```js
var Names = React.createClass({
  handleClick: function(index) {
    this.props.onRemoveName(index);
  },

  render: function() {
    var that = this;
    var names = this.props.names.map(function(name, index) {
      return (
        <p key={index}>
          Hello, {name}!
          <button onClick={that.handleClick.bind(null, index)}>Remove</button>
        </p>
      )
    });

    return (
      <div>
        {names}
      </div>
    )
  }
});
```

Note that we are calling `this.props.onRemoveName` in the `handleClick` function. `onRemoveName` is a function that's passed down by the parent (`Root`) to the child. Let's add the prop in the `Root` component.

We pass down the prop `onRemoveName` to the `Names` component and when that function is called, we will log the index that was passed up to callback `handleRemoveName`.

```js
var Root = React.createClass({
  getInitialState: function() {
    return { names: ["Grace", "Margaret", "Anita"] }
  },

  handleRemoveName(index) {
    console.log('In root component', index);
  },

  render: function() {
    return (
      <div>
        <Names names={this.state.names} onRemoveName={this.handleRemoveName} />
      </div>
    )
  }
});
```

Did the index log correctly?

To complete the desired functionaly we need to filter out the clicked name from the array of names and then set the updated array as state with the function `setState()`.

```js
handleRemoveName: function(index) {
  var newNames = this.state.names.filter(function(name, i) {
    return i !== index;
  });

  this.setState({ names: newNames });
}
```

### Exercise

* Add a component `Animals` that's rendered in the `Root` component. `Animals` should have the same functionality as `Names`, but instead of human names it renders animal species.
* Add an input field that takes in new names. When a name is submitted, add it to the array of names in the `Root` component. The input field can live in the `Root` component.
* Can you move the input field to it's own `AddName` component and maintain the same functionality?
