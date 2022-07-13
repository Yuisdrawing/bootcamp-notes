# Semantic elements

_Semantic HTML_ is markup that represents meaningful content structure to browsers and AT. _Semantic elements_ are used to define the role that content plays on a website (as opposed to purely presentational elements like `<div>`). We have already seen a few semantic elements, including `<p>`, `<h1>` and `<em>`, all of which carry explicit meaning regarding what kind of content they contain. In this section, we will dive deeper into semantic elements.

Consider a website built only with `div` elements to group content. It would look like this:

```html
<div>
  <h1>Lorem ipsum dolor sit</h1>
</div>
<div>
  <div>
    <p>Lorem ipsum dolor sit amet, consectetum adipiscing elit.</p>
    <p>Saepe enim fugit quo tempora! Facilis quos aperiam suscipit!</p>
  </div>
  <div>
    <p>Quos veritatis numquam nesciunt delectus, atque at laborum.</p>
    <p>Modi eos doloribus explicabo error deserunt nobis culpa.</p>
  </div>
</div>
<div>
  <p>Excepteur sint occaecat</p>
</div>
```

Sighted users would be able to look at the above code and attempt to guess what the website means and how the content is organized, but non-sighted users and the browser have no way to take meaning from the above; it is not accessible and would not be interpreted well by SEO.

Here is that same structure, but with semantic HTML:

```html
<header>
  <h1>Lorem ipsum dolor sit</h1>
</header>
<main>
  <section>
    <p>Lorem ipsum dolor sit amet, consectetum adipiscing elit.</p>
    <p>Saepe enim fugit quo tempora! Facilis quos aperiam suscipit!</p>
  </section>
  <section>
    <p>Quos veritatis numquam nesciunt delectus, atque at laborum.</p>
    <p>Modi eos doloribus explicabo error deserunt nobis culpa.</p>
  </section>
</main>
<footer>
  <p>Excepteur sint occaecat</p>
</footer>
```

The addition of `<header>`, `<main>`, `<section>`, and `<footer>` elements mean we don't simply have to infer meaning of the different code segments. The website now has semantic structure that it didn't have beforehand; it is both accessible and would perform well for SEO purposes because it is now more usable by humans and machines.

Notably, the first example using only `<div>`s and the second using semantic elements actually render the same way in the browser. Try it out by creating a file called "semantic-elements.html" and copying the two examples above. 

They render the same way because semantic elements are not meant to show on a screen to users, but support the following purposes:

* They make websites accessible.
* They support SEO.
* They make working as a developer easier and clearer.

`<div>` elements alone for structure do not, and cannot, provide the benefits listed above.


## Understanding semantic elements

Here are some of the available semantic elements you can use to give meaningful structure to your websites. 

Open up [semantic-elements-website-example--conEd.zip](https://hychalknotes.s3.amazonaws.com/semantic-elements-website-example--conEd.zip) to follow along with the examples mentioned below. 


### Header

`<header>`: Defines the header of a page or a section. It often contains the title of a page, and a tagline/subtitle.

```html
<header>
  <h1>The most important of titles!</h1>
</header>
```


### Main

`<main>`: Used for the main content of your page. It should only be used once in any given HTML document.

```html
<main>
  <p>Rainbows, butterflies and everything nice.</p>
</main>
```


### Navigation 

`<nav>`: Defines a section that contains links to other parts of your website or other websites. You can have more than one `<nav>` on your web page. For example, it's common to see a navigation near the top of a page and also in the footer of a page.

```html
<nav>
  <ul>
    <li><a href="home.html">Home</a></li>
    <li><a href="about.html">About</a></li>
  </ul>
</nav>
```


### Unordered list

`<ul>`: Defines an unordered list. Unordered lists can only take **one** type of element as direct children: `<li>`s (which represent a _list item_ element). Inside the `<li>`s you can have any element you'd like, maybe an `<img>` or an `<a>`, but the `<ul>` can only have `<li>`s as a direct child. 
You can use as many `<ul>`s as you would like on your page. Unordered means that the order of the items is not meaningful.

```html
  <ul>
    <li>
      <p>Pick up dry cleaning</p>
    </li>
    <li>
      <p>Give dog a bath</p>
    </li>
  </ul>
```


### Ordered list

`<ol>`: Defines an ordered list, with `<li>`s nested inside which represent a list item element. `<ol>` can be used many times on a site. An ordered list signifies that the order of the list items carries meaning. The same rule as above applies to `<ol>`s: you can only have `<li>`s as direct children to an ordered list. Within those list items, you can use any element you'd like!

```html
<section>
  <h2>Skills</h2>
  <ol>
    <li>
      <p>Coding</p>
    </li>
    <li>
      <p>Learning</p>
    </li>
  </ol>
</section>
```


### Section

`<section>`: Defines a section in a document. The elements nested inside of a `<section>` are generally related, and often a `<section>` will have its own heading (though not always).

```html
<section>
  <h2>About our class</h2>
  <p>Related information goes here</p>
  <p>We're cool humans learning to code</p>
</section>
```


### Article

`<article>`: Defines a complete and independent piece of content on your site. They are typically used for a post in a blog, a news article or individual comment.

```html
<article>
  <p>Vestibulum id ligula porta felis euismod semper. Donec sed odio dui.</p>
</article>
```


### Aside

`<aside>`: Defines a section of content that is secondary or complementary to the main content, meaning it supports the main content. They are often used for sidebars and can be inside or outside of the `<main>`. They must be siblings of whatever it is complementary to. 

```html
<aside>
  <p>Vestibulum id ligula porta felis euismod semper. Donec sed odio dui.</p>
</aside>
```


### Footer

`<footer>` : Defines the footer of a page. It can sometimes contain information about the page, such as who wrote/developed it, copyright information and sometimes links to related files/documents. It sits outside of the `<main>`.

```html
<footer>
  <p>Copyright 2014</p>
</footer>
```

The above elements are some of the semantic elements you will use the most often, but are only a handful of the semantic elements available! We will be covering other semantic elements throughout this course.

![Animated gif of a man saying "cool cool cool"](https://media.giphy.com/media/2HONNTJbRhzKE/giphy.gif)

You will never be expected to memorize every semantic element - when in doubt, these notes are here to help you! 


## Divs or semantic elements

The purpose of a semantic element is to create meaning for the browser and users. When none of the semantic elements make sense to use, choose a `<div>`. The best way to make this decision is to ask yourself "what role does this play on my website?". If nothing constructive comes to mind, it's likely a `<div>`.

Often, `<div>`s are used to group elements that will be styled together because you are simply making a *division* (more on that when we move into CSS).

Don't forget that `<div>` only means that it is a container of some kind, but it doesn't provide more information to the browser, screen reader or developer interacting with the code. 

Download and open up [semantic-structural-html--conEd.zip](https://hychalknotes.s3.amazonaws.com/semantic-structural-html--conEd.zip) in your text editor to practice using structural semantic elements.


## Resources

* [HTML Elements Reference, MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element)