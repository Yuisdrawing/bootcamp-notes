# CSS selectors

Selectors are used to target the elements on the page that we would like to style. They let us target single or multiple elements. Styling many elements at once helps keep our code maintainable, DRY (do not repeat yourself) and readable.

Selectors follow the K.I.S.S principal: "Keep it simple, silly!". The following are some selector types, from least specific to more specific. Always try to use the least specific selector available before applying more specific selectors. 


## Element selector

Also known as a "type selector", the element selector selects every instance of a given element in the HTML document. This selector is useful when you want to apply some general styles; for example, styling all of your `<h2>` or all of your `<p>` elements, since either of these often share similar looks across a website.

The CSS below selects all of the `<h2>` elements in the HTML document and turns them red:

HTML
```html
<h2>Welcome to our website</h2>
```

CSS
```css
h2 {
  color: red;
}
```

The below selects all of the `<p>` elements across the HTML document and turns them yellow:

HTML
```html
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod</p>
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod</p>
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod</p>
```

CSS
```css
p {
  color: yellow;
}
```

The selector for any element is that element without the opening and closing angle brackets (`<>`).

`<div>..</div>` &rarr; ` div { ... }`

`<h1>Some quote</h1>` &rarr;` h1 { ... }`


## Class selector

Using an element selector has its disadvantages; what if you want to style some `<h2>` elements on your page differently than others?

Let's say we have three paragraphs, but we only want the middle one to have an aqua background. The element selector wouldn't work because it would turn them all aqua:

```html
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod</p>
<p>tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam</p>
<p>quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo</p>
```
```css
p {
  background: aqua;
}
/* This gives ALL the paragraphs an aqua background; we only want the middle one. */
```

This is where the class selector comes in. The class selector is more specific than the element selector; it only targets the elements with a given specific HTML class attribute. 

In the below example, the middle `<p>` element has been given a class attribute with the value of "special":

```html
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod</p>
<p class="special">tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam</p>
<p>quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo</p>
```

In CSS, we use the `.` period to denote the class attribute.

The below selector targets all elements with the class of `special`, and turns their background aqua.

```css
/* Turns any element with a class of special aqua */
.special {
  background: aqua;
}
```

A class can be used multiple times, meaning if we wanted to also give an `<h3>` an aqua background, we could do so by giving it the `special` class as well:

```html
<h3 class="special">I'm special, too!</h3>
```

### Class names
You can name your classes whatever you like, but choosing descriptive names that describe the purpose of the style is the best way to stay organized and to future-proof your project.

A class name cannot contain spaces, but can use camel case (myClassName), kabob case (my-class-name) or snake case (my_class_name) to separate words. Similar to our file names, it doesn't matter which case style you pick as long as you are consistent.


## ID selector

It is also possible to style elements by targeting their `id` attribute. Remember that unlike classes, a given `id` can only be used once per HTML document, making them extremely specific, so it is best practice to avoid using an `id` to apply styles (`id` elements are often used as in JavaScript to target HTML elements, so `id` elements have other roles - just not in CSS). 

That said, you may run into code that styles by `id` in the wild, so it is important to recognize how to use them.

An `id` is selected in CSS with an octothorpe (hashtag):

```html
<p id="special">I have an id of special</p>
```
```css
#special {
  color: peru;
}
```

The naming conventions of an `id` are the same as a `class`.


### Element & class selector exercise
Practice writing out element and class selectors by opening [element-class-selector.html](../exercises/element-class-selector.html?raw=true) in your text editor and follow the instructions inside of the file.

If you get stuck, check out the answer key: [element-class-selector-ANSWER.html](../exercises/element-class-selector-ANSWER.html?raw=true).


## Grouping selectors

CSS makes it possible to target multiple different selectors and apply the same styles to all of them at once.

For example, if you would like all of your `<p>` elements as well as all of your `<h2>` elements to be the same colour, you could select both elements independently like so:


```css
p {
  color: tomato;
} 

h2 {
  color: tomato;
}
```

However, instead of writing the same style declaration twice, we can instead group the `<p>` and `<h2>` element selectors by separating them with a comma:

```css
p, 
h2 {
  color: tomato;
}
```

This method saves both space and time - now you can change the color of both element selectors in one place! The order of the selectors does not matter as long as they are separated by a comma. 

It can also be applied to selecting both an element and a class, like the example below which is selecting all `<p>` elements and all elements with the class of "unique" and giving them a font-size of 18px:

```css
p,
.unique {
  font-size: 18px;
}
```

You could also select elements with different classes. The example below is targeting all the elements with a class of "elephant", as well as elements with a class of "bigCat", and giving all of them a background of pink:

```css
.bigCat,
.elephant {
  background: pink;
}
```

This can be applied to any mix and any number of selectors:

```css
.dog,
.sillyDolphin,
h1,
.mouse,
p,
h4 {
  letter-spacing: 1.5px;
}
```

## Descendant selector

It may not always be efficient to add classes on every individual element we would like to target for styling, as it can lead to a cluttered-looking HTML document. CSS allows us to take advantage of the 'parent-child' relationship between nested elements, using what is known as a _descendant selector_.

The descendant selector first targets the parent and then narrows in on the children, and sometimes grand-children, to apply styles.

In the example below, we have two unordered lists. Both `<ul>` elements have their own unique classes, but there are no other classes being used on their children (the `<li>` elements) or their grand-children (the `<p>` and `<a>` elements):

```html
<ul class="groceries">
  <li>
    <p>Milk</p>
  </li>
  <li>
    <p>Eggs (on sale at <a href="#">No Frills</a>)</p>
  </li>
  <li>
    <p>Bread</p>
  </li>
  <li>
    <p>Red Bull (Please print this <a href="#">Coupon</a>)</p>
  </li>
</ul>

<ul class="sports">
  <li>
    <p>Soccer</p>
  </li>
  <li>
    <p>Basketball</p>
  </li>
  <li>
    <p>Hockey</p>
  </li>
  <li>
    <p>Irish Bog Snorkeling (read more <a href="#">here</a>)</p>
  </li>
</ul>
```

Our goal is to style only the list items in the first list, with the class of "groceries".

If we use the element selector `li { ... }` we would select every list item in both lists. With the help of the descendant selector, we can target the list items in the first list by targeting the parent-child relationship:

```css
.groceries li {
  color: green;
}
```

This selector is targeting all of the `<li>` elements nested inside an element with the class of "groceries". The parent-child relationship is denoted by a space between the selectors.

If we revisit the HTML, we can trace the parent-child relationship:

```html
<!-- the ul is a parent -->
<ul class="groceries">
    <!-- the li is a child of the ul -->
  <li>
    <p>Milk</p>
  </li>
    <!-- the links are grand-children of the ul, and a child of the li -->
  <li>
    <p>Eggs (on sale at <a href="#">No Frills</a>)</p>
  </li>
  <li>
    <p>Bread</p>
  </li>
  <li>
    <p>Red Bull (Please print this <a href="#">Coupon</a>)</p>
  </li>
</ul>

<ul class="sports">
  <li>
    <p>Soccer</p>
  </li>
  <li>
    <p>Basketball</p>
  </li>
  <li>
    <p>Hockey</p>
  </li>
  <li>
    <p>Irish Bog Snorkeling (read more <a href="#">here</a>)</p>
  </li>
</ul>
```

There is no limit to the number of child selectors you can use, however, try and take the shortest route when creating parent/child selectors and try not to go more than three levels deep. For example, if we wanted to style only the links that appear in the first list we could use this descendant selector:

```css
.groceries li a {
  color: green;
}
```

The above is targeting all of the anchor elements which are nested inside a list element, which themselves are nested inside an element with a class of groceries!

This CSS is also valid, and shorter:

```css
.groceries a {
  color: green;
}
```
The above is selecting all of the anchor elements nested inside of an element with the class of groceries, cutting out the `<li>` middle-person.


#### Descendant selectors vs. classes

Could we have just used a class to specify which element we wanted to target? Yes! That is always an option. There are many ways to accomplish any given task in web development and it's important to understand the options you have when working with selectors.

Using descendant selectors helps keep your HTML clean and avoids the need to come up with endless class names.


### Descendant selector exercise

Download [desc-exercise.zip](../exercises/desc-exercise.zip?raw=true) to try writing your very own descendant and multiple selectors.
