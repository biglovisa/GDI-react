# JSX

If you know HTML, you know JSX.

This is valid JSX:

```
<h1>Hello, World!</h1>
```

This is also valid JSX:

```
const name = "Penny";

<h1>Hello, {name}!</h1>
```

JSX is XML-like syntax and any JavaScript enclosed in curly braces, `{}`, will be evaluated. So the above statement will evaluate to `Hello, Penny!`.

JSX is used in React components to more easily be able to

### Exercise

* Iterate over an array of names (`["Grace", "Margaret", "Anita"]`) and render them on the page.
* Render an input field, have the user inser their name and then render `Hello, UserName!`?
