# Lists

Lists make up an important element in web development. While we might think of a list as only a traditional "to-do" list or grocery list, in web development a list is anything that is a series of grouped elements. This includes galleries (which are often lists of images) and navigations (list of links).


## Types of lists

There are two types of lists - ordered lists `<ol>`, and unordered lists `<ul>`.

* Ordered lists carry with them implicit meaning that the order of their list items are important.
* Unordered lists carry the implicit understanding that the order of items in them is not integral and the list items can go in any order without the list losing meaning.

```html
<ol>
  <li>One</li>
  <li>Two</li>
  <li>Three</li>
</ol>

<ul>
  <li>Milk</li>
  <li>Bread</li>
  <li>Eggs</li>
</ul>
```

![A ordered list followed by an unordered list](https://hychalknotes.s3.amazonaws.com/unordered-ordered-default--conEd.png)

By default, ordered lists come with a numerical order whereas unordered lists come with bullets.


### Syntax

Both unordered and ordered lists are block elements that have an opening and a closing tag. They are both made up of list items, `<li></li>` which are also block elements that include an opening and closing tag.

It's important to note that both unordered and ordered lists can only have list items as direct children or else the HTML is considered invalid.

Anything can be nested inside of a list item, including inline elements, block elements, and inline-block elements.

```html
<h2>Fun facts about me</h2>
<ul>
  <li>
    <a href="https://www.google.ca/">Google is my favourite website.</a>
  </li>
  <li>
    Green is my favourite colour.
  </li>
  <li>
    I <strong>love</strong> spending time at the beach.
  </li>
</ul>
```

Note that while `<p>` elements denote text, as we've seen, `<li>` elements are one of the few elements where you do not need to include a `<p>` element to nest text within them.


## List styles

Lists come with a range of default styles.

Create an HTML file called "working-with-lists.html" to follow along with the examples below.


### List style positioning

`list-style-position: <outside or inside>;`

In the below example, we can see that the default styling on list items places bullets "outside" the list item's content. `list-style-position` controls whether the bullets are considered "inside" or "outside" of the content.

```html
<ol>
  <li>One</li>
  <li>Two</li>
  <li>Three</li>
</ol>

<ul>
  <li>Milk</li>
  <li>Bread</li>
  <li>Eggs</li>
</ul>
```

```css
li {
  background: rgb(185, 215, 84);
}
```

![The ordered and unordered list with the background colour green without the numbers or bullets coloured](https://hychalknotes.s3.amazonaws.com/unordered-ordered-green-background--conEd.png)

By default, all lists have a default value of `outside` for `list-style-position`, but it can be changed to be `inside` on our list items:

```css
ol,
ul {
  list-style-position: inside;
}
```

![The ordered and unordered list with the background colour green with the numbers or bullets coloured](https://hychalknotes.s3.amazonaws.com/unordered-ordered-list-green-background-inside--conEd.png)

Here we are putting the `list-style-position` property on the list parent elements (`ol` / `ul`), and it is inherited by all the children inside of the list. It can also be placed on individual `li` items.


#### Padding

By default, browsers generally style lists with a lot of margin and padding. This is clearly visible when list items are given more content and given different `list-style-position` values, as in the code below:

``` html
<ul>
  <li>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Laborum unde id quae aspernatur laboriosam at corrupti ducimus quos voluptatem modi.
  </li>
  <li>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Expedita repellendus, temporibus inventore esse ab tempora.
  </li>
  <li>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Vero itaque, nulla tenetur sed voluptates odit rem dicta quaerat temporibus aliquam repellat quos eveniet mollitia nostrum.
  </li>
</ul>

<ol>
  <li>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Laborum unde id quae aspernatur laboriosam at corrupti ducimus quos voluptatem modi.
  </li>
  <li>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Laborum unde id quae aspernatur laboriosam at corrupti ducimus quos voluptatem modi.
  </li>
  <li>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit. Laborum unde id quae aspernatur laboriosam at corrupti ducimus quos voluptatem modi.
  </li>
</ol>
```

``` css
ul {
  list-style-position: outside;
}

ol {
  list-style-position: inside;
}
```

![List style position shown for unordered list and ordered list.](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-06-07%20at%2011.16.59%20AM.png)

Notice the position of the bullets and what happens when the list wraps:

* With `list-style-position: outside;` there is padding beside the bullets, keeping the text wrap on the second line aligned with where the first line of text began.
* With `list-style-position: inside;` the padding is outside of the bullets, causing the text wrap to align the second line with the bullets themselves.

If this rendered code is inspected with Dev Tools, you can spot the purple padding in both list styles.

![Padding and margin highlighting show upon inspection of the unordered.](https://hychalknotes.s3.amazonaws.com/ul-outsideListStyle--conEd.png)
![Padding and margin highlighting show upon inspection of the ordered lists.](https://hychalknotes.s3.amazonaws.com/ol-insideListStyle--conEd.png)


### List style type

`list-style-type: <keyword>;`

Filled-in dots, or "discs", are the default style for unordered lists and decimal numbers for ordered lists, but those styles can be altered using the `list-style-type` property.

Note that the colours of list styles come from the `color` property that is set on the given `<li>`, `<ol>` or `<ul>`.

A complete breakdown of the available list styles can be found [here](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style-type#values).


Styles can be applied to individual list items or to the parent list element, with the list-style being inherited by all of the list items.

Below are some examples of list styles being manipulated on unordered lists:

```css
ul {
  list-style-type: square;
}
```

![Unordered list with black solid square bullets](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-05-06%20at%204.20.24%20PM.png)

```css
ul {
  list-style-type: circle;
}
```

![Unordered list with black circle bullets](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-05-06%20at%204.20.37%20PM.png)


It is common to remove the `list-style-type` completely, which can be done with the `none` value:

```css
ul {
  list-style-type: none;
}
```

![Unordered list without bullets](https://hychalknotes.s3.amazonaws.com/unordered-list-style-none--conEd.png)

### List style image

`list-style-image: url(relative or absolute path);`

The `list-style-image` property is used when developers would like to use their own images for the bullets of a list. It is very similar to `background-image` and requires a `url()` value to link to the relative or absolute image path.

In the below example, an absolute image path is used.

```css
ul {
  list-style-image: url(https://hychalknotes.s3.amazonaws.com/yellow-bullet.gif);
}
```

![Unordered list with an image of a yellow dot as bullets](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-05-06%20at%204.22.21%20PM.png)

## Removing default styling

It is very common to strip off base styles from lists by using the below CSS at the top of your stylesheet:

```css
ul {
  margin: 0;
  padding: 0;
}
```

It is important to note that by doing this, it will only appear as if the bullet points have been removed. They are technically still there because by default they are on the outside of the list.

To ensure they are fully removed, use `list-style-type: none;`

## Exercise

If you would like some extra practice styling lists, download the [list exercise starter file](../../exercises/list-style-exercise.html?raw=true). The completed file can be downloaded [here](../../exercises/list-style-exercise--ANSWER.html?raw=true).
