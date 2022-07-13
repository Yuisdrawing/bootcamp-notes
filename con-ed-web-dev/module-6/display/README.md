# Display

`display: <keywords>;`

The CSS property `display` allows developers to control if an element will be a block or inline element, and the layout method that an element's children will take. It accepts a range of keywords that affect the flow of the HTML.

Using `display` can help create complex layouts, and give developers more control over elements in both how they relate to other elements and the styles they can take on. By default, all elements have a display value. Display properties are not inherited by child elements.


## Block

`display: block;`

Block-level elements take up the entire width available to them, regardless of the amount of content. By default, they start on a new line. `<p>`, heading elements, `<div>`, `<ol>`, `<li>`, `<main>`, etc., are some examples of block elements.

```html
<p>cow</p>
<p>goat</p>
```

```css
p {
  background: orange; 
}
```

![Two paragraph elements with orange backgrounds](https://hychalknotes.s3.amazonaws.com/display-block-example1--conEd.png)

Their height and width can be adjusted using `height` and `width`, and they can encompass inline elements and other block elements. Block-level elements can also accept `margin` and `padding`.

In the example below, there is a `<p>` nested inside of a `<div>`, which are both block elements by default. The `<p>` has an `<em>` nested inside of it.

```html
<div>
  <p>hello<em>!</em></p>
</div>
```

```css
div {
  width: 700px;
  background: pink;
}

p {
  background: orange;
  padding: 30px 0;
}
```

![A div that is 700px wide with a pink background with a paragraph inside that says hello with a background of orange](https://hychalknotes.s3.amazonaws.com/display-block-em-nested--conEd.png)

Many block-level elements come with default padding and margin from the browser, and it is common to "strip" these defaults at the top of your CSS in order to work from a blank slate. If you are ever unsure which elements have default margin or padding, use your Dev Tools to help you out by inspecting the elements.

```css
p,
h1 {
  margin: 0;
  padding: 0;
}
```


## Inline

`display: inline;`

Unlike block elements, inline elements only take up as much width as they require for their content and they do not break onto a new line, meaning they can sit side by side. `<a>`, `<em>`, `<span>` etc., are some examples of inline elements.

```html
<p>I <em>love</em> to swim at <span>10:00pm</span></p>
<a href="https://en.wikipedia.org/wiki/Swimming">Learn more</a>
<a href="https://en.wikipedia.org/wiki/Swimming#Lessons">Sign up for lessons</a>
```

```css
em,
span {
  color: white;
  background: black;
}
```

![The words "love" and "10:00pm" with a black background and white text](https://hychalknotes.s3.amazonaws.com/inline--example1--conEd.png)

Notice how the links are sitting next to each other and do not take up their own lines the way a `<p>` would.

Inline level elements cannot be given a height, and applying top or bottom margin has no effect. This is because inline elements are, for the most part, typographical in nature or relate to typographical elements, meaning they must stay in a line with the elements they relate to.

```html
<p>Ready, <span>set</span>, go!</p>
```

```css
span {
  background: red;
  height: 200px;
}
```

The above height set on the `<span>` won't have an effect because it is an inline element.


## Inline-block

`display: inline-block;`

`inline-block` is the best of both `block` and `inline`; like an `inline` element, it only takes up the space that it needs (meaning it does not break onto a new line by default), but like a block element, it can accept height and margin on the top and bottom. Very few elements are inline-block by default; the `<button>` element is one of those that are:

```html
<button>Click me</button>
<button>Or click me!</button>
<button>Or me!</button>
```

```css
button {
  background: black;
  color: white;
  border: none;
  height: 70px;
}
```

![Three buttons side by side with a height of 70px](https://hychalknotes.s3.amazonaws.com/inlineBlock-example1--conEd.png)

> **Accessibility tip**
>
> What is the difference between an `<a>` and a `<button>`? A `<button>` is used to do something, such as bring up a sign-in pop-up window, whereas an `<a>` goes somewhere. They also interact differently with AT: The space or enter key triggers a button, whereas only pressing the enter key can trigger a link.


#### A note on images

While images are technically inline elements (they sit side by side by default), they are a unique case in that they behave as if they are inline-block - they can accept height, and vertical margin and padding. This is a purely technical point though, and in general you can just treat images as if they are inline-block.


## Converting elements

It is possible to change the `display` property on elements, and have them take on the attributes of a different `display` type to help create different layouts.

In the below example, there are two `<div>`s that are given a height and width, which they will accept because they are block elements by default. This also means that they will take up individual lines because block elements break to a new line.

```html
<div class="box1"></div>
<div class="box2"></div>
```

```css
div {
  height: 200px;
  width: 200px;
}

.box1 {
  background: peru;
}

.box2 {
  background: aqua;
}
```

![Two boxes, one if the background colour of "aqua" and the other with the background colour of "peru", one below the other](https://hychalknotes.s3.amazonaws.com/display-changing-values-example1--conEd.png)

If the `<div>`s in the above example are given a `display` value of `inline-block`, they will no longer break onto a new line. 

```css
div {
  height: 200px;
  width: 200px;
  display: inline-block;
}
```

![Two boxes, one if the background colour of "aqua" and the other with the background colour of "peru", next to each other](https://hychalknotes.s3.amazonaws.com/display-changing-values-example2--conEd.png)


## None

`display: none;`

`display` can also be given a value of `none`. This will remove the element completely from the rendered code, meaning it does not show up in the browser. This makes it invisible to sighted users and those using AT alike.

The footprint of the element is also removed and any subsequent content takes up the space that is available. 


### Visibility

Another property that appears to perform the same task as `display: none` is `visibility: hidden`. This property hides the element, but the space that the element would occupy remains.

## Display code along
Let's explore how the `display` property can be used to build out a horizontal navigation. Download and open up [navigation-display--conEd.zip by clicking here](https://hychalknotes.s3.amazonaws.com/navigation-display--conEd.zip).

[Click here to see what we are aiming towards](https://hychalknotes.s3.amazonaws.com/navigation-horizontal-codealong--conEd.png)

## Resources
* [List of block level elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements)
* [List of inline level elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elements)









