# Generic elements

Unlike a `<p>` element or `<h1`> element that have one specific purpose, there are HTML elements that do not inherently carry meaning with them. These _generic elements_ are often used to group or contain elements together for styling purposes.


## Span 

The `<span>` element is a small yet mighty HTML tag. A span is an inline element which means that it takes up only the space it needs and nothing more, which is we why we often find them in the middle of typographic elements. The span tag itself has no semantic meaning and is made up of an opening and closing tag.

Suppose we were writing a sentence about our favourite foods and wanted to add a background colour to each of the foods' names: My favourite foods are broccoli, goat roti, and eggs.

We would first wrap it in our paragraph tag to give it semantic meaning:

```html
<p>My favourite foods are broccoli, goat roti, and eggs.</p>
```

Then we wrap each food in a span with the class of food. We use a class so we can target just these specific spans with a style. Classes and styles will be explored in a later lesson.

```html
<p>My favourite foods are <span class="food">broccoli</span>, <span class="food">goat roti</span> and <span class="food">eggs</span></p>
```

![The sentence "my favourite foods are broccoli, goat roti and eggs" with broccoli, goat roti and eggs with a red background](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-25%20at%205.31.21%20PM.png)

> **Accessibility tip**
>
> AT would not recognize that the above words have a red background. If the above content with the red background is meant to have great importance such as emphasis applied to them, the `<em>` element would be a better choice.


## Div

The `<div>` element (short for "document division") is a generic structural element used to define and divide content for organization and styling. It is a block element by default, meaning it takes up the entire width of its container, regardless of the size of the content within it. 

Content in web page designs is visually broken up into chunks that sometimes don't correspond to the elements available to developers. The `<div>` element can be used to wrap other content elements and make them available to style as a group. `<div>` elements take an opening and a closing tag.

```html
<div>
  <h1>I'm the header</h1>
  <p>Cras mattis consectetur purus sit amet fermentum. Praesent commodo cursus magna, vel scelerisque nisl consectetur et. Duis mollis, est non commodo luctus, nisi erat porttitor ligula, eget lacinia odio sem nec elit. Vivamus sagittis lacus vel augue laoreet rutrum faucibus dolor auctor.</p>
</div>
```


### Div vs span

When should a `<div>` be used and when should a `<span>` be used? 

The technical difference between the two is that `<div>` is a block element and represents a division in your code, whereas `<span>` is an inline element that has no true meaning. Take a look at the previous example using `<div>` elements instead of spans:

```html
<p>My favourite foods are <div class="food">broccoli</div>, <div class="food">goat roti</div> and <div class="food">eggs</div></p>
```

![The sentence "my favourite foods are broccoli, goat roti and eggs" with broccoli, goat roti and eggs with a red background spanning across the screen](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-25%20at%205.31.15%20PM.png)

Why does each item break onto a new line? Because `<div>` is a block element, which means it should not be used inline, as it naturally takes up an entire line regardless of how much content it has inside of it.

In general, spans go inside other elements, such as `<p>` or `<h2>` (ie. inline) so we can later specifically target that bit of content. `<div>` elements are used to wrap larger sections of content together for structural and stylistic reasons.
