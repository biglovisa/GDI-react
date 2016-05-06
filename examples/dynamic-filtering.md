# Dynamic Filtering

For this example, you could continue by writing your React code in `script` tags in the HTML file, however, this is not very common in Front End Land.

Desired functionality:

![](http://g.recordit.co/lGXuM9xkik.gif)

### Welcome to the Repo

```sh
1 .
2 ├── lib
3 │   └── index.js
4 ├── public
5 │   ├── index.html
6 │   └── main.bundle.js
7 ├── .babelrc
8 ├── .gitignore
9 ├── README.md
10 ├── package.json
11 ├── server.js
12 └── webpack.config.js
```

There are 9 files and 2 folders in this repo, let's go through them one by one.

**2**: lib/: where we keep our actual code.

**3**: lib/index.js: the entry point to our application. Here's where the root component will live.

**4**: public/: where index.html and the JavaScript bundle lives (more on this in **11**).

**5**: public/index.html: our main index.html file. When we start the server, this file will render. Here's where we want to include our JavaScript code via `script` tags.

**6**: public/main.bundle.js: to make our code more performant, we use [webpack](https://webpack.github.io/docs/what-is-webpack.html) to create code bundles. Webpack takes a file and it's dependencies and generates a static asset of it.

**7**: .babelrc: config file for [Babel](https://babeljs.io/). Babel transpiles JSX to JavaScript, but it's primary use is for compiling newer JavaScript language features to an older version of JavaScript that the browser is using.

**8**: .gitignore: tells git to ignore some files in the repo.

**9**: README.md: README with instructions on how to get the app running.

**10**: package.json: we use [npm](https://www.npmjs.com) as our package manager and this is the configuration file.

**11**: server.js: a small [Express](http://expressjs.com/) server.

**12**: webpack.config.js: our configurations.

### Building

We are building `a search-based app that fetches data and live filters the data based on search terms`.

To achieve that, we need the following: data, an input field where we can enter search terms and a list that renders the data and filters it based on what the user enters in the input field. For the first iteration, we are going to read data from a text file. When we have the functionality implemented, we are going to fetch the data over HTTP using AJAX.

![](http://i.giphy.com/gwNs1Ga6F5RRK.gif)

**Guiding questions**:

* What might the component hierarchy look like?
* What components do you need - aka what are the different pieces of your application?
* In which components do we need to maintain state?
* Which components share information? How should this information be shared?
