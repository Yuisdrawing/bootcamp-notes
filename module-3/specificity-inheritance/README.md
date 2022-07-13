# The cascade, specificity & inheritance

Three of CSS's most foundational concepts are also their most powerful; the cascade, specificity and inheritance. Using all three properly helps keep CSS DRY and easy to work with, and it allows developers to debug their code with ease.


## The cascade

The cascade (which is in CSS's name - Cascading Style Sheets) dictates what styles will be rendered, according to the order in which they appear in the document. CSS, like HTML, reads from the top-down and will favour anything that comes lower down in a stylesheet over something higher up. If the selectors are of the same value (more on that shortly), then the later styles will overwrite the earlier ones.

For example, below we see a `<p>` element first targeted with the element selector but then targeted again in a separate rule that is also attempting to change the color of the paragraph elements.

```css
p {
  color: blue;
}

p {
  color: darkolivegreen;
}
```

Because of the cascade, the `<p>` elements would end up being the color `darkolivegreen`. 

This applies to all types of selectors, including descendant selectors:

```css
.candy a {
  letter-spacing: 2px;
}

h1 {
  color: pink;
}

.candy a {
  letter-spacing: 5px;
}
```

In the above example, all of the links that are children of an element that has a class of "candy" would have letter-spacing of 5px and not the 2px that was first set on the links.


## Specificity

What happens when you write two rules that target the same element using different types of selectors?

Below, there is a rule targeting the class of "warning". In the same style sheet, there is another selector below it selecting `<p>` elements:

```html
<p class="warning">Heads up - lots of warnings to keep track of!</p>
```

```css
.warning  {
  color: blue;
}

p {
  color: red;
}
```

Despite the second rule coming in below the first, the first rule is what is rendered (ie. the paragraph will be blue) because the first rule is more specific.

Specificity will override the cascade if a selector is more specific than others below it. In the following example, the first rule will override the other two because it is the most specific:

```css
/* target p elements inside a twitter widget, inside a sidebar */
.sidebar .twitterWidget p {
  font-size: 24px;
}

/* make all p elements 14px font */
p {
  font-size: 20px;
}

/* target just the p elements in the sidebar */
.sidebar p {
  font-size: 18px;
}
```

Behind the scenes, CSS gives every selector a numerical value, and the selector with the highest value (ie. the most specific selector) is the rule that will be rendered. 

The math can get pretty complicated, but here is a brief overview:
* Element selectors carry low specificity.
* A descendant selector of two elements is more specific than a single element selector.
* A `class` is more specific than an element selector.
* An `id` is extremely specific.
* Inline-styles are even more specific.

When writing CSS, it is best practice to write the least specific styles you can, and then to move into more specific CSS as you need it. This is because it's easier to override less specific styles, whereas it is extremely difficult to override an `id` or an inline style, which can cause a lot of headaches down the line.

If two selectors have the same specificity, CSS falls back on the cascade to dictate what will be rendered.


### Universal selector

In some cases, you may want to select every element on your page and give them all the same style. The universal selector, also known as the wildcard selector, is the least specific of all selectors and uses the `*` to select all elements:

```css
* {
  color: black;
}
```

It is commonly used to set up base styles and carries extremely low specificity. We will be exploring case uses for the universal selector later in this course.


## Inheritance

Descendant selectors aren't the only things that benefit from a parent-child relationship; CSS allows typographical properties to be set on a parent and be inherited by all of its children. This can help keep code DRY and organized.

In the example below, there is a `<section>` that has two children, a `<p>` and an `<h2>`:

```html
<section class="content-box">
  <h2>Section Title</h2>
  <p>Some text within the section</p>
</section>
```

```css
.content-box {
  color: grey;
}
```

With the color being set on the parent element, both of the children will inherit the color grey.


### Body styles

To take full advantage of this power of inheritance, many developers set generic styles on the `<body>` element, which are passed down to all the children within in (ie. all the elements on the page). While only typographical properties are passed down from parent to children, this can help set a base font-size and color on all the elements inside of the HTML document and help keep your stylesheet DRY.

```css
body {
  font-size: 20px;
  color: lightgrey;
}
```

The above text would give all typographic elements within the `<body>` the color `lightgrey` and a `font-size` of `20px`, helping to avoid setting those styles individually on individual elements.

It's very likely that your headers will have a larger font size than the base size you set (for body text, etc), but these general styles can be overridden using the power of specificity and the cascade, to give headers, for example, their own styles.


### The `inherit` keyword

The `inherit` keyword allows us to tell an element to respect its parent element.

```html
<section>
  <p>Hello!</p>
</section>

<aside>
  <p>Hello again!</p>
</aside>
```

```css
p {
  color: sienna;
}

section {
  color: purple;
}

section p {
  color: inherit;
}
```

In the example above, despite the paragraph element selector targeting all the paragraph elements, the `<p>` inside of the section will respect whatever color is set on its parent. That is because of the `inherit` keyword and the higher specificity of the selector itself.


## Exercise

Download [css-csi.zip](../exercises/css-csi.zip?raw=true) and open up the answer key in your browser. Try your best to match the styles that are being rendered while following the instructions in the exercise to test out your debugging skills.

Pay attention to things like spelling, inheritance, the cascade, and specificity!

## Resources

* [CSS specificity: things you should know](https://www.smashingmagazine.com/2007/07/css-specificity-things-you-should-know/)
* [CSS specificity calculator](https://specificity.keegan.st/)
* [Specifics on CSS specificity](https://css-tricks.com/specifics-on-css-specificity/)
