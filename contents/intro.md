# Intro (30 min)

Websites have traditionally been built with three layers; HTML, CSS and JavaScript. These are usually kept separate from each other, but they are almost always used together.

HTML is the **text**, CSS is the **styling** and JavaScript makes it **interactive**.

```
  how it's developed                                  how it's used in the browser

  ----------------                                          ----------------
        HTML                                                HTML/CSS/JS/HTML
  ----------------                                          CSS/JS/HTML/CSS/
        CSS               -------------------------->       JS/HTML/CSS/JS/H
  ----------------                                          TML/CSS/JS/HTML/
     JavaScript                                             CSS/JS/HTML/CSS
  ----------------                                          ----------------
```

Developing websites with HTML, CSS and JavaScript (jQuery) works really well, but the more complex your app gets the more difficult it becomes the keep your data in sync. In very interactive websites, one button click could change the state of your application - your data - in many different ways.

After a little while, JavaScript front end frameworks and view layer libraries emerged and currently, the most popular ones include Ember, Angular, Backbone, Meteor and React. These tools are good for solving different problems, there's not __one__ tool that all developers agree is the best.

React has been around since March 2013 and is already used in major applications like Facebook, Instagram, Airbnb, PayPal, Periscope, Squarespace, Tesla Motors and [the list goes on](https://github.com/facebook/react/wiki/Sites-Using-React). React does not have a lot of opinions, can be dropped into almost any application and it adopts a component driven design. Instead of separating code in an HTML file, a CSS file and a JavaScript file, it separates it in components.

![](https://media.giphy.com/media/xTiTnlCeT1VFvlnVDO/giphy.gif)

### Component Driven Design

Today, large web applications are usually split up in order to separate concerns and make the functionality easier to reason about. The two main parts of a web app are the back end and the front end. The front end is everything the users interact with (the browser interface) and the back end is the code that supports the app functionality; a database, a server, services etc. These can communicate directly with each other or via [HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP).

```
-------------------------                                  ----------------------
|       Back end        |  -----------(data)------------>  |     Front end      |
|      Server/Api       |                                  |    HTML/CSS/JS     |
|                       |  <----------(actions)---------   |                    |
-------------------------                                  ----------------------
```

The idea of [separation of concern](https://en.wikipedia.org/wiki/Separation_of_concerns) and [single responsibility](https://en.wikipedia.org/wiki/Single_responsibility_principle) were some of the motivations behind component driven design - instead of viewing the front end as three layered it's composed of many small components. Each component is responsible for one part of the application.

For example, a simple contact form view could consist of a `header` component, a `body` component and a `footer` component. The body component could contain a `menu` component and a `contactForm` component. All HTML, CSS and JavaScript logic related to the `header`, should live in the `header` component etc.

### Exercise

What are some of the possible components of the following websites?

* https://www.girldevelopit.com/
* https://www.reddit.com/
* http://www.nytimes.com/

## Extra Resources

* [AJAX](https://developer.mozilla.org/en-US/docs/AJAX/Getting_Started)
