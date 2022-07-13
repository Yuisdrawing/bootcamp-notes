# CSS measurements

As we've seen with in some of our lessons, it's sometimes necessary to set heights and widths of elements or set a certain font size.

CSS has a range of options for how to do this, each with their own strength and best use case. 


## Pixels

Pixels are a static measurement type, which is to say that they do not change based on context (much like centimeters or feet); a pixel is a pixel no matter what it is applied to. This makes them useful for things that need a specific, predictable size, which will remain the same regardless of browser/window size.

Pixels can be applied to font sizes, like in the example below, which sets the `<h3>` elements to a font size of 20px

```css
h3 {
  font-size: 20px;
}
```

They can also be applied to widths or heights to give elements specific dimensions. The below is setting all `<section>` elements to have a width of 1080px:

```css
section {
  width: 1080px;
}
```


## Percentages

Unlike pixels, percentages are a variable measurement type. They are dynamic, changing dimensions based on their parent element's size.

For example, below is a `<div>` with a class of `wrapper`, which has two children inside of it - an `<aside>` with a width of 25%, and a `<main>` with a width of 75%.

```html
<div class="wrapper">
  <aside> 
    <p>I'm an aside!</p>
  </aside>	
  <main> 
    <p>I'm a main!</p>
  </main>
</div>
```

```css
.wrapper {
  width: 1000px;
}

aside {
  width: 25%;
}

main {
  width: 75%;
}
```

Behind the scenes, the browser is doing the math for us by calculating the width of the `<aside>` and `<main>` as percentages of their parent element's width.

In this case, the class of `wrapper` gives the parent a static width of 1000px. As a child of `.wrapper`, the `<main>`'s width is 75% of that 1000px, which works out to 750px. The `<aside>` element is also a child of `.wrapper` and has a width of 25% of 1000px, or 250px. 

![percentage widths](https://hychalknotes.s3.amazonaws.com/percentage-width-example--conEd.png)

The pixel value of the `.wrapper` could change to another value and its children would still take up 75% and 25% of that width, respectively. This makes our code easy to maintain and helps us use the browser to do the math for us!

Percentage values can also be applied to font sizes. In the example below, there is a `<div>` with a font size of 20px. It is using the power of inheritance to pass this font size to all of its children, except for the `<p>` element which is going to take 50% of its parent's font-size value.

```html
<div>
  <h1>My font-size is 20px</h1>
  <p>My font-size if 50% of my parent's font-size!</p>
</div>
```

```css
div {
  font-size: 20px;
}

div p {
  font-size: 50%;
}
```

In this case, a font size of 50% would be 10px. This method would ensure that the paragraph elements inside of the `<div>` would always be 50% smaller than whatever it set on the parent, regardless of what size is set on the `<div>`.


## Viewport units

The viewport is the current size of the visible content area of your browser. The viewport does not include the address or bookmarks bar but does include the space under the scrollbar - it is the entire area within which the HTML renders.

![Screen shot showing the viewport](https://hychalknotes.s3.amazonaws.com/vw-vh.png)

Keep in mind that the the size of the viewport is a relative value that changes with every user's device. For example, the size of the viewport on an 11" MacBook Air versus a 17" Alienware R5 are very different. This is similar to percentages in that values are dynamic and can change, but while percentage value is based on the size of a direct parent, a viewport unit looks to the entire viewport to determine its value.

Often websites feature full browser header images (also called hero images) or content that is relative to the size of the user's browser. It would be extremely difficult to ensure something fits 100% of the viewport across all devices - that's where viewport units come in!


### Viewport height

Viewport height (`vh`) measures the height of the user's viewport and returns a relative value. Think of it as a percentage that looks to the viewport directly to determine its value - the full height of the viewport, ie. 100% of viewport height, is `100vh`.

![viewport height displayed](https://hychalknotes.s3.amazonaws.com/bootcamp-vh.jpg)


```css
header {
  height: 100vh;
}
```

The above is the same as 100% height of the user's viewport. This is a very common value used to create the popular hero-image-style headers

```css
nav {
  margin-top: 20vh;
}
```
The above means that the `<nav>` would be 20% from the top of the user's viewport.


### Viewport width

Viewport width (`vw`) measures the width of the viewport and returns a relative value. Typically, you won't find as many uses for VW as you will for VH because percentage values would be better suited to deal with widths. That's because percentage values refer to the parent element instead of the entire browser, making them more predictable.

Note that the viewport width includes the space under the scroll bar.

![viewport height displayed](https://hychalknotes.s3.amazonaws.com/bootcamp-vw.jpg)

```css
section {
  margin-right: 10vw;
}
```

The above moves the `<section>` to the left by a distance that is 10% of the total viewport width.

Note that viewport units are [not fully supported in legacy browsers](http://caniuse.com/#search=view).


## Em

Em values, which represent relative measurement units, are similar to the percentage value in that children look to their parent to determine their true value.

Most commonly, `em`s come in handy when looking for sizes that are relative to one another. 

The below example has a font size of 10px set on the all `<section>` elements. All `<span>` elements that are children of `<section>` elements are then targeted with an element selector and given a font size of 1.2em.

```css
section {
  font-size: 10px;
}

section span {
  font-size: 1.2em; 
}
```

The span looks to its parent, or grand parent, or great-grand parent (etc.), to determine what size its `em` value represents. In this case, 1.2em produces a value of 12px:

Calculating `em` values:
`<parent's value in px>` * `<element's value without a measurement type>` = `<value in px>`

A common issue when using `em`s is that the value is a multiple of its parent's, resulting in some complicated math for nested elements. 

```css
section {
  font-size: 10px;
}

section p {
  font-size: 1.6em; /* produces 16px: 10px * 1.6 */
}

section p span {
  font-size: 1.6em; /* produces 25.6px: (10px * 1.6) * 1.6 */
}
```


## Rem

Rem stands for "Root ems"; this measurement type is a multiple of the font size set on the _root_ element of your document - ie. the `<html>` element (it is set there because the `<html>` element is the parent of all elements inside on our website). By setting a font size in pixels on the `<html>` element, we can then set a `rem` value on our other elements and they will scale appropriately.

Unlike `em`s, `rem`s do not scale based on their direct parent; instead they look directly to the root to determine their value. This avoids the tricky nesting issues that can arise when using `em`s.

The root value is usually a base of 10px or 20px, to make the math simple when scaling all the other elements in your HTML document based off of that value.

The below example has a font size of 20px set on the root. One selector is a paragraph element selector that is targeting all `<p>` elements, and the other is targeting `<span>`s nested in `<p>` elements. Both have the font-size value of 1.6rem.

```css
html {
  font-size: 20px;
}

p {
  font-size: 1.2rem; /* Produces 24px : 20px * 1.2 */
}

p span {
  font-size: 1.2rem; /* Produces 24px : 20px * 1.2*/
}
```

In the above example, both the of the selectors that have a font-size of 1.2rem look to the root value to determine their literal font size. In this case, both produce a value of 24px:

Calculating `rem` values:
`<root's value in px>` * `<element's value without a measurement type>` = `<value in pxs>`

`Rem`s make it easy to change every font size across your website because you can change it in one place, the root, and it will affect every element in a predictable way. 


## Use cases for measurement types

Which measurement type is the best to use? The short answer is - it depends!

Each type of measurement has its own strengths and weaknesses. Go through each question below and try to guess which measurement type would be best suited to the situation.

<details>
<summary>I want to set my image to take up the full height and width of my screen regardless of what device I am using.</summary>
Setting VH to 100 would be the best option!
</details>

<details>
<summary>I want to set my font size in a way that I could change the base font size to make all my fonts either larger or smaller.</summary>
This sounds like a job for Rems!
</details>

<details>
<summary>I want my banner to be 20% of the width of its parent.</summary>
This is a great job for a percentage instead of a measurement like VW. That's because a percentage looks to its direct parent to determine its value, whereas VW looks to the total browser width.
</details>

<details>
<summary>I want to set a margin that will increase and decrease as the parent gets larger and smaller.</summary>
Using a percentage would be ideal.
</details>


<details>
<summary>I want to set a padding size that will stay the same no matter how big or small my screen gets.</summary>
Using a pixel measurement would be ideal here because they are static (they don't change). 20px will always be 20px regardless of how big or small the parent or viewport is.
</details>



## Resources
* [Rem vs. em](https://medium.com/code-better/css-units-for-font-size-px-em-rem-79f7e592bb97)
