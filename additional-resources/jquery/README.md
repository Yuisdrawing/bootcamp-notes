# jQuery
jQuery is a JavaScript library, meaning it is built off of JavaScript but uses unique built-in functionalities that are specific to jQuery. According to the [Stack Overflow Developer Survey Results 2019](https://insights.stackoverflow.com/survey/2019#technology-_-web-frameworks), jQuery is used by 48.9% of developers, more than any other JavaScript library like React or Angular. It was created as a way to simplify writing JavaScript code and has an easy to understand syntax that allows developers to select elements from the DOM (Document Object Model) using CSS selectors syntax.

For our sake, the DOM represents our HTML. JavaScript makes it possible to grab things in the HTML and manipulate them using JavaScript. This is also called "manipulating the DOM". 

JavaScript, and by consequence jQuery, is a programming language that plays a unique role in front-end development and is the only programming language that makes up the front-end development toolkit:

* HTML: defines the content
* CSS: defines the presentation
* JavaScript: defines the behaviour and functionality

## jQuery and front-end development
jQuery adds a level of interactivity to our websites that isn't possible with HTML and CSS. Here are a few examples of when you would use jQuery in a website:

* Events: Currently, the only "events" we have access to are done with CSS on `:hover` or `:checked`, but changes will only happen when a user completes an action. 

  With jQuery, we could imitate almost anything that a user might do. Click, right click, dropdown select, mouse move, window resize, scroll. etc.

* Changing CSS: JavaScript is able to dynamically apply or change CSS.
* Animations: jQuery allows animation creations on the DOM.
* AJAX: We are able send our requests for information to our or another server. Think of loading tweets or new Facebook posts without refreshing the page.
* Conditionals: JavaScript is programming language, which means that we can do analysis and conditionally execute code. For example, the below JavaScript is checking the length of a tweet:

```js
if(tweet.length > 280) {
  alert("Tweet is too long!");
}
```

## JavaScript vs. jQuery
JavaScript was written in **one week** for the Netscape browser. Microsoft then copied it with their implementation of "jScript". Needless to say, JavaScript is an interesting language with a lot of known quirks. Writing cross-browser JavaScript can be extremely prone to bugs.

jQuery makes writing JavaScript much, *much* easier. jQuery is written in JavaScript and we will be using the jQuery syntax instead of JavaScript.

For example, here is what changing a background using JavaScript would look like, with the first example representing Vanilla JavaScript and the second representing jQuery:

```js
document.getElementsByClassName('box')[0].style.background = "blue";
```

vs.

```js
$('.box').css('background','blue');
```

## Using jQuery
To use jQuery, the jQuery library has to first be imported into our HTML, similar to how we bring in Google Fonts in our `<head>` to get access to the fonts. This is an essential step that allows us to have access to jQuery.

To do this, a `<script>` element is used that goes at the bottom of the `<body>` element, before the closing `<body>` tag. Script elements have an opening and closing tag and are linked at the bottom of our HTML because bringing in scripts can block the rendering of elements on the page and could prevent a page from loading quickly if put in the `<head>` like the CSS.

The `<script>` element takes a `src` attribute that links to the jQuery library.

```html
<body>
  <!-- .. -->
  <script src="https://code.jquery.com/jquery-3.4.1.min.js" integrity="sha256-CSXorXvZcTkaix6Yvo6HppcZGetbYMGWSFlBw8HfCJo=" crossorigin="anonymous"></script>
</body>
```

When snippets were brought into our text editors, a jQuery snippet was (sneakily) included - type in `jquery + tab` to have the the jQuery library snippet come up.

Once we have linked in jQuery, there are two options for working with jQuery. Similar to CSS, it can be done internally or linked externally.

To use jQuery internally, it is done between `<script>` tags, below the jQuery library link.

```html
<body>
  <!-- .. -->
  <script src="https://code.jquery.com/jquery-3.4.1.min.js" integrity="sha256-CSXorXvZcTkaix6Yvo6HppcZGetbYMGWSFlBw8HfCJo=" crossorigin="anonymous"></script>
  <script>
    // jQuery here
  </script>
</body>
```
*Note: the additional script element is below the `<script> `element bringing in jQuery. This order is essential for the second `<script>` element to have access to the jQuery library.*

It can also be linked externally by using a `<script>` element and linking to the JavaScript sheet.

```html
<body>
  <!-- .. -->
  <script src="https://code.jquery.com/jquery-3.4.1.min.js" integrity="sha256-CSXorXvZcTkaix6Yvo6HppcZGetbYMGWSFlBw8HfCJo=" crossorigin="anonymous"></script>
  <script src="myScript.js"></script>
</body>
```

Note in the above example, the `<script>` element is linking to a JavaScript file, called "myScript.js" via a relative path.

## Document ready
Once jQuery has been loaded in at the bottom of our HTML, the next step to using jQuery is writing something called a "document ready".

The "document ready" is critical to your jQuery working properly. JavaScript works by interacting with the website, so when we run JavaScript, the website needs to be 100% loaded before we do anything.

The below is what makes up a document ready:

```html
<script>
  $(function() {
    // Document is ready! All your code goes inside.
  });
</script>
```
The `$` denotes access to jQuery's library and is jQuery specific. It lets the browser know that a jQuery function is starting.

By wrapping all of our jQuery code in a "document ready", it will wait until the entire website has finished loading before executing. Otherwise it would fire way too early, leading to unexpected results.

All pages only need a single "document ready". For now, put all your jQuery code inside of it.

Open up ["first-jquery-funTimes--conEd.html" by clicking here](https://hychalknotes.s3.amazonaws.com/first-jquery-funTimes--conEd.html) to practice setting up your own internal jQuery sheet by following the instructions inside of the HTML file. Check out the [answer key by clicking here](https://hychalknotes.s3.amazonaws.com/first-jquery-funTimes-ANSWER--conEd.html).

## Selectors
jQuery allows developers to select things directly on the DOM by using CSS selectors. Similar to CSS, by using selectors it is possible to make changes to those given elements or the elements around them.

jQuery uses `$('')` to wrap selectors and make it a jQuery Object that allows developers to work with the given element(s) in jQuery. 

* Element selector:
h1 → `$('h1')`

* Class selector:
.box → `$('.box')`

* Descendant selector:
.nav ul li → `$('.nav ul li')`

*Note: Single or double quotes are both ok to use in selectors, as long as you are consistent with your choice.*

For example, the `<p>` element in "first-jquery-funTimes--conEd.html" can be targeted using the below selector:

```js
$('p')
```

Just like with CSS, this would target all of the `<p>` elements on the page. 

## Methods
To make use of selectors, jQuery provides developers with methods. Methods are built in actions that jQuery comes with by default that allow the DOM to be manipulated in various ways.

Methods are made up of keywords, defined by jQuery, and are followed by smooth brackets where the action of that given method is written: 

`$('p').methodName(action of method);`

For example, using our `<p>` element selector in jQuery, we can dynamically add another `<p>` element directly underneath it by using the `append` method.

```js
$('p').append('<p>This is a new paragraph.</p>');
```

In the example above, we have selected all the `<p>` elements using a jQuery selector, using the `append` method, and append the HTML code:

```html
<p>This is a new paragraph.</p>
```

This appended code will now show up under every `<p>` element. *Note that the appended code is in quotes and will be considered invalid without them.*

### Alert
The `alert` method causes a message to pop up in a dialog box at the top of the screen. It asks the user to acknowledge the message by clicking "ok". Once the user clicks ok, the message will disappear and the rest of the page will now be accessible again.

`alert('Words that will show up in dialog box');`

*Note that the alert method stands on its own without requiring a selector*

Try using the `alert` method in our "first-jquery-funTimes--conEd.html".

There are hundreds of methods available that come built into jQuery. [Check them out in the jQuery documents by clicking here](https://api.jquery.com/jQuery/).

## Events and methods
Events are a huge part of jQuery because they allow actions to occur when something happens. For example, when a user clicks a button, a popup comes up to alert the user. 

General syntax:

```js
$('selector').event(function() {
  // Do this when the event happens
});
```

A "click" event, which will occur when a user clicks on specific elements that have been selected looks like the below:

```js
$('.clickMe').click(function() {
  alert('You clicked me!');
  // This alert is another method
});
```

In the above example, an element with the class of "clickMe", when clicked, is going cause an alert to come up that will say "You clicked me!".

Events can effect elements on the page. For example, by clicking a button, another element on the page is faded out by using the `fadeOut()` method.

```js
$('.fadeOut').click(function() {
  $('.boxFriend').fadeOut('slow');
});
```

The `fadeOut()` method alters the opacity, from 1 to 0, resulting in the element becoming `display:none`. `fadeOut()` takes a timing that will allow the effect to take longer or faster depending on the timing past to it. For example, in the code above the `fadeOut()` method was passed 'slow', resulting in a slow transition in opacity. It can also accept 'fast' or a number value which represents milliseconds. 

There is also a `fadeIn()` method which alters an element's opacity from 0 to 1.

A useful way to discover more methods and events is to read through the [the jQuery documentation](https://api.jquery.com/jQuery/), which outlines all the possible methods and events and how to use them. For example, learning about the `slideUp()` method by [reading the documentation](https://api.jquery.com/slideUp/) shows the following syntax for `slideUp()`:

`$('selector').slideUp('amount of time in ms or keyword');`

### Chaining methods
It is possible to "chain" methods onto each other to have them happen one after the other using the same selector. For example, if the desired effect was to have an element `fadeIn()` and then `slideUp()`, the syntax would look like the below:

`$('selector').fadeIn('slow').slideUp('slow');`

Download and open up [jquery-events-methods--conEd.zip](https://hychalknotes.s3.amazonaws.com/jquery-events-methods--conEd.zip) and follow the instructions inside of the HTML. The answer key is found inside of the folder. 

### Added & removing classes dynamically
jQuery makes it possible to add and remove CSS classes to help add, or remove, styles on elements. To do this, developers utilize the `addClass()` and `removeClass()` methods. Their syntax is very similar to other methods:

`$('selector').addClass('className');` OR
`$('selector').removeClass('className');`

A notable feature of the add/remove class methods is that the class name that is passed in does not take a `.`. In the example below, a `<ul>` is selected, and a class of "sillyBeans" is being removed. Usually when working with classes, a `.` is required, but by using the add/remove class methods, you are requesting that jQuery find those class names meaning jQuery is assuming that they begin with a `.` in the CSS.

`$('ul').removeClass('sillyBeans');`

Try adding a remove class and add class button to the jquery-events--conEd.html file.

#### Toggling classes
jQuery makes it possible to add and remove classes by using the `toggleClass()` method. This method will either remove OR add the class depending on if it already exists on the given selector.

`$('ul').toggleClass('sillyBeans');`

Try adding a `toggleClass()` method to the jquery-events--conEd.html file.

## this
A useful keyword to know about in JavaScript is `this`. The explanation of this can get [quite complex](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this). When working with jQuery and creating simple interactions, we will probably just want to use this to reference an element that triggered a function. In the example below, the keyword this refers to the button that has been clicked. Although there may be multiple buttons on the page, the one that is clicked is the one that sets off the code between the curly braces and causes it to execute, therefore it is what this represents.

```html
<button class="btn btn1">Click me, I'll disappear</button>
<button class="btn btn2">Click me, I'll disappear</button>
<button class="btn btn3">Click me, I'll disappear</button>
```

```js
$('.btn').click(function() {
      $(this).fadeOut('slow');
});
```

Toggling classes and `this` are extremely useful together and help create more intuitive events. 

Download and open up [list-this-toggle--conEd.zip](https://hychalknotes.s3.amazonaws.com/list-this-toggle--conEd.zip) and open up the answer key to see the behaviour we are working towards. 

### Toggling sibling elements
By using the `next()` method, developers can target the next direct sibling of a given element. This is the jQuery equivalent to the `+` selector in CSS.

Download and open up [toggle-next--conEd.zip](https://hychalknotes.s3.amazonaws.com/toggle-next--conEd.zip) to see how to use `next()`, this and `toggleClass()` together! The instructions are in the HTML and the answer key is in the same folder.

*Note: To select all adjustment siblings, the method `nextAll()` is available in jQuery.*

## jQuery vs. CSS
As a rule of thumb, developers should always try their best to use CSS over jQuery whenever possible. CSS is extremely lightweight and easy on the browser wheres jQuery can be harder on a browser to process.

## Exercise
* Create jQuery etch-a-sketch by [clicking here to download the exercise folder](https://hychalknotes.s3.amazonaws.com/toggle-sketch-jquery--conEd.zip). The directions are inside of the HTML document (at the bottom!). Open up the answer key in the browser [here](https://hychalknotes.s3.amazonaws.com/add-remove-toggle-class-ANSWER.html) to see what to work towards.
* Creating a jQuery hamburger Menu by [clicking here to download the exercise folder](https://hychalknotes.s3.amazonaws.com/hamburger-fun--conEd.zip). The directions are inside of the HTML document. Open up the answer key found in the same folder to see what to work towards.

## Resources
* [The DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
* [Google managed jQuery CDN link](https://developers.google.com/speed/libraries/#jquery)





