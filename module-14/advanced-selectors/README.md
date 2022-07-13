# Advanced selectors

We have covered a range of selectors and have gotten comfortable using them to create a range of designs. They include:

Type selector:
```css
p {

}
```

Parent-child selector:
```css
ul li {

}
```

Class selector:
```css
.className {

}
```

Selector list:
```css
.warning,
.error {

}
```

In addition to the above, CSS offers a range of advanced selectors to help target more specific elements in our code, preventing us from needing to litter our HTML with classes. 


## Multiple selector

`.className.AnotherClassName`

When selecting elements in CSS, we are able to chain together multiple selectors to target elements which match more than one attribute. For example, this can be useful to create specific selectors for elements which have multiple classes.

In the below example, there are a number of classes being used. We would like to target elements that only contain both the class of `.accent` and `.content`.

```html
<header>
  <h1>Ice Creamery</h1>
  <h2 class="accent content">I Scream You Scream, the Best Ice Cream in Town</h2>
</header>

<section>
  <h3 class="accent">About</h3>
  <p class="accent content">Ever since I was a youngster I loved making my own ice cream!</p>
  <p class="content">I loved making my own ice creams!</p>
</section>
```

By chaining multiple class selectors together with no spaces between them, we can target those elements like so:

```css
.accent.content {
  background: lightblue;
}
```

The order in which you provide the class names does not matter, the selector will apply to all elements supplied.

This would be the rendered result from the code above:

![A screen shot that shows some text with a blue background while other are left with a white background](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-04-17%20at%2011.59.36%20AM.png)

It is also possible to mix element and class selectors. Below there is an `<h1>` and a `<p>`, each with the same class of `.pirateLife`.

```html
<h1 class="pirateLife">I'm a pirate</h1>
<p class="pirateLife">row scuttle parrel provost Sail ho shrouds spirits boom mizzenmast yardarm. Pinnace holystone mizzenmast quarter crow's nest.</p>
<p>Deadlights jack lad schooner scallywag dance the hempen jig carouser broadside cable strike colors.</p>
```

The class of `.pirateLife` has its own styles applied already:

```css
.pirateLife {
  background: snow;
}
```

Using the multiple selector, we can select only the `<p>` element with the class of `.pirateLife` without affecting the `<h1>` that has the same class, or the other `<p>` element (which does not have the class), like so:

```css
p.pirateLife {
  color: black;
}
```


## Adjacent selector

`+`

The adjacent selector allows you to select an element that is an immediate sibling of another element. This selector utilizes the `+` symbol.

In the example below, the selector is targeting every element with a class of `.dog` that is an immediate sibling of an element with a class of `.cat`.

```html
<div class="cat">Cat</div>
<div class="dog">Dog</div>
<div class="dog">Dog</div>
```
```css
.cat + .dog {
  background: darkcyan;
}
```

![Dog div that is right after (direct sibling) of the cat div have the background of darkcyan](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-20%20at%209.35.07%20AM.png)

Good use case: Trying to apply padding to text, but only when it comes after an image element.


## Direct child selector

`>`

The direct child selector allows you to select elements which are specifically the direct children of another element. Grandchild, great-grandchild etc. elements will not be targeted by the direct child selector. This selector utilizes the `>` symbol.

In the example below, the selector is targeting all parent elements with the class of `.parent` and applying styles to all of the direct children with the class of `.child`.

```html
<div class="parent">
  Parent
  <div class="child">Child</div>
  <div class="child">Child</div>
  <div class="child">Child</div>
  <div class="anotherDiv">
    <div class="child">Child</div>
  </div>
</div>
```
```css
.parent > .child {
  background: darkcyan;
}
```
![Three child elements that are the immediate children of the div with the class of parent have the background of darkcyan. The final child element nested inside of an immediate child of the div with the class of parent is not targeted.](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-20%20at%209.35.19%20AM.png)

Good use case: Targeting specific lists' `<li>` elements in nested navigation menus.


## Following selector

`~`

The following selector (also called the "general sibling selector") allows developers to target elements that are siblings of another element, but unlike the adjacent selector, the targeted elements do not have to be an immediate sibling. This selector utilizes the `~` symbol.

In the below example, the following selector is targeting all the `<p>` elements that come after, and are siblings of, the `<img>`:

```html
<p>I'm a paragraph</p>
<p>I'm a paragraph</p>
<p>I'm a paragraph</p>
<img src="https://unsplash.it/200/300/?random">
<p>I'm a paragraph</p>
<p>I'm a paragraph</p>
<p>I'm a paragraph</p>
```
```css
img ~ p {
  background: darkcyan;
}
```

![The 3 paragraphs before the image element are not targeted, all 3 paragraphs after the image element have the background of darkcyan.](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-06-24%20at%2012.48.31%20PM.png)

The following selector will not target grandchild or great-grandchild elements, only direct sibling elements. Take a look at the example below to see this behavior in action.

```html
<p>I'm a paragraph</p>
<p>I'm a paragraph</p>
<p>I'm a paragraph</p>
<img src="https://unsplash.it/200/300/?random">
<p>I'm a paragraph</p>
<p>I'm a paragraph</p>
<p>I'm a paragraph</p>
<section>
  <p>paragraph child of a sibling!</p>
</section>
```
```css
img ~ p {
  background: darkcyan;
}
```

![The 3 paragraphs before the image element are not targeted, all 3 paragraphs after the image element have the background of darkcyan, the 4th paragraph that is a nested child is not targeted.](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-06-24%20at%2012.48.44%20PM.png)

Good use case: Targeting `<p>` elements that follow images to give give them correct spacing.


## Attribute selectors

`[href=""]`

Attribute selectors allow you to select elements with a specified attribute. We briefly looked at attribute selectors in [the form styling lesson](https://github.com/HackerYou/con-ed-web-dev/tree/master/module-13/form-styling) when selecting inputs: `input[type="text"]`.


### Exact attribute matching

Matching the exact attribute name and value of an element utilizes the square brackets and a equal sign.

```html
<div class="exactExample">
  <a href="http://google.com">Google</a>
  <a href="http://www.google.com">Google (with www)</a>
  <a href="http://mozilla.com">Mozilla</a>
</div>
```
```css
.exactExample a[href="http://google.com"] {
  background: green;
  color: white;
  padding: 10px;
  display: inline-block;
}
```
![The first anchor with an href matching exactly the attribute selector has been targeted. Just that one element.](https://hychalknotes.s3.amazonaws.com/exact-selector--conEd.png)


### Starts with

To target an element whose attribute value starts with a certain text, the caret, `^`, can be used.

The example below will target all anchor elements whose href starts with the text "https://" are selected and styled:

```html
<div class="startsExample">
  <a href="http://google.com">Google.com</a>
  <a href="https://cibc.ca">CIBC</a>
  <a href="https://google.com">Google.com</a>
  <a href="http://tsn.ca">TSN</a>
</div>
```
```css
.startsExample a[href^="https://"] {
  background: green;
  color: white;
}
```

![The anchor tags with the content of CIBC and Google.com have been target, as both of their hrefs start with the text "https://".](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-20%20at%209.38.52%20AM.png)


## Pseudo selectors

Another set of ways to extend selectors to be more specific is by using pseudo selectors. [We have previously seen some](https://github.com/HackerYou/con-ed-web-dev/tree/master/module-9/pseudo-classes-I), like `:hover` and `:focus`, but there are many others.


### First child

`:first-child`

The first-child selector targets the first child element of a specified parent.

This selector only works if the element targeted with the pseudo selector is the immediate first child of the specified parent.

```html
<section>
  <p>This is the first sentence</p>
  <p>This is the second sentence</p>
</section>
```
```css
section p:first-child {
  color: red;
}
```
![The first p element in the section is targeted and the text content now has the colour of red.](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-25%20at%204.05.40%20PM.png)


### Last child

`:last-child`

We can similarly use the `:last-child` selector to target the last child element of a specified parent.

This selector only works if the element targeted with the pseudo selector is the immediate last child of the specified parent.

```html
<section>
  <p>This is the first sentence</p>
  <p>This is the second sentence</p>
</section>
```

```css
section p:last-child {
  color: red;
}
```

![The last p element in the section is targeted and the text content now has the colour of red.](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-25%20at%204.05.46%20PM.png)

### Nth-child
`:nth-child()`

The nth-child selector allows you to provide arguments on which child elements to select inside of a parent.

The general syntax is as follows:

```css
element:nth-child(n) {

}
```

You can provide an argument in the smooth brackets which specifies which child to select. One example is to pass an argument of `even` or `odd` to select even or odd children respectively.

```html
<ul>
  <li>item 1</li>
  <li>item 2</li>
  <li>item 3</li>
  <li>item 4</li>
  <li>item 5</li>
  <li>item 6</li>
  <li>item 7</li>
  <li>item 8</li>
  <li>item 9</li>
  <li>item 10</li>
</ul>
```

```css
ul li:nth-child(even) {
  background: blue;
}
```
![All even lis (2, 4, 6, 8, and 10) in the ul have been targeted and have the background of blue, and all odd numbered lis have no special background colour.](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-25%20at%204.05.53%20PM.png)

To select all the odd number `<li>` elements in the `<ul>`, we can pass in `odd` as an argument to nth-child.

```css
ul li:nth-child(odd) {
  background: red;
}
```
![All odd lis (1, 3, 5, 7, and 9) in the ul have been targeted and have the background of red, and all even numbered lis have no special background colour.](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-25%20at%204.06.00%20PM.png)

To select a specific element, we can provide the number count of the element we want to select. For example, if we only wanted to select the fifth element in the list, we can pass in the argument `5`:

```css
ul li:nth-child(5) {
  background: blue;
}
```
![The 5th element with the text content of item 5 is targeted and has a background of blue, all other list elements have no special background colour.](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-25%20at%204.06.06%20PM.png)

For more complex selections, we can do a bit of algebra inside the smooth brackets to get a pattern of targeting every nth element.

For example, if we wanted to select every fourth element in the list we could pass in `4n`.

```css
ul li:nth-child(4n) {
  background: blue;
}
```

![Starting at the 4th element; every 4th element has a background of blue.(In our list of 10 items, items 4 and 8 have a background of blue.)](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-25%20at%204.06.12%20PM.png)

`:nth-child` can become pretty complex. For example:

`ul li:nth-child(3n + 2);`

The above means:
* Start on the second element.
* From there, go to every 3rd element.

To learn more about `:nth-child`, visit [nth-test.com](http://nth-test.com/) to play around with different recipes. 

CSS Tricks also has a great article on useful nth-child patterns: [https://css-tricks.com/useful-nth-child-recipies/](https://css-tricks.com/useful-nth-child-recipies/).


### Nth-of-type

`:nth-of-type()`

`:nth-child`, `:first-child`, and `:last-child` only work if the element attached to them is numerically the first, last, or whichever numbers(s) we specify with `:nth-child`. What if we wanted to select the first `<p>` element, but there were other child elements before it (ie. it wasn't the first child of its parent element)?

```html
<section>
  <h3>This is the title</h3>
  <p>This is the first sentence</p>
  <p>This is the second sentence</p>
</section>
```
```css
section p:first-child {
  color: red;
}
```

![An h3 and 2 p elements are rendered, none of them were targeted by section p:first-child, none of them have special colour.](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-25%20at%204.09.34%20PM.png)

The code above has not targeted any of the elements. The `<p>` element in this case is not the first child of the section; the `<h3>` is the first child, but that's not what we targeted in our CSS.

We can use `:nth-of-type` to target that first `<p>` element, being more specific with which element and which type we want to target in a list of children.

```html
<section>
  <h3>This is the title</h3>
  <p>This is the first sentence</p>
  <p>This is the second sentence</p>
</section>
```

```css
section p:nth-of-type(1) {
  color: red;
}
```

![The first paragraph in in the section is targeted and has a colour of red.](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-25%20at%204.06.24%20PM.png)

You can pass in any argument into `:nth-of-type` that you can pass into nth-child.


### First letter

`::first-letter` or `:first-letter`

The first-letter selector allows us to select the very first character (letter) in a typographic element. It is technically considered a pseudo-element.

A fun use of this selector is to turn the first character in a big block of text into a historiated initial.

```html
<blockquote class="firstLetterExample">Miss Brooke had that kind of beauty which seems to be thrown into relief by poor dress. Her hand and wrist were so finely formed that she could wear sleeves not less bare of style than those in which the Blessed Virgin appeared to Italian painters; and her profile as well as her stature and bearing seemed to gain the more dignity from her plain garments, which by the side of provincial fashion gave her the impressiveness of a fine quotation from the Bible, - or from one of our elder poets, - in a paragraph of to-day's newspaper. </blockquote>
```

```css
.firstLetterExample::first-letter {
  font-size: 30px;
  font-family: cursive;
  color: lavender;
}
```
![The first letter in the blockquote element, (the M is Miss) has been targeted, and now has a lavender colour with a larger font.](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-20%20at%209.53.21%20AM.png)


### Not

`:not()`

The `:not()` selector takes an argument for which element you do not wish to target.

For example, if we wanted to target all paragraphs except the one that has a class of `.item9` on it:

```html
<div class="items">
  <p class="item1">Item # 01</p>
  <p class="item2">Item # 02</p>
  <p class="item3">Item # 03</p>
  <p class="item4">Item # 04</p>
  <p class="item5">Item # 05</p>
  <p class="item6">Item # 06</p>
  <p class="item7">Item # 07</p>
  <p class="item8">Item # 08</p>
  <p class="item9">Item # 09</p>
  <p class="item10">Item # 10</p>
</div>
```

```css
.items p:not(.item9) {
  background: red;
}
```

![Every paragraph element except the one with a class of item9 has been targeted, and has a background of red.](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-20%20at%209.53.15%20AM.png)


### Checked

`:checked`

The checked selector allows you to target any input element that is in a checked state.

This selector allows for some fun interactivity as styles can be applied upon interaction with an input (any interaction that turns an input into a checked state).

```html
<input type="checkbox">
<input type="checkbox">
<input type="checkbox">
<input type="checkbox">
<input type="checkbox">
```

```css
input[type='checkbox']:checked {
  float: right;
}
```

![A cursor is clicking each of the 5 input of type checkboxes, once one of them is clicked, or put into a checked state, the checked selector targets them and they float right, dissapearing from the left hand side of the screen.](https://hychalknotes.s3.amazonaws.com/checked-gif.gif)

If the checked selector is used in conjunction with some other selectors, like the adjacent selector, we can affect the styles of another element!

We can hide or show a div by checking or unchecking an input.

```html
<input type="checkbox" class="toggle">
<div class="showMe">I can be hidden</div>
```

```css
.showMe {
  background: red;
  color: white;
  padding: 20px;
}

input[type='checkbox']:checked + .showMe {
  display: none;
}
```

![The input of type checkbox is checked, and the div with a class of showMe having a red background and text content "I can be hidden" is targeted and disappears. The rest of the content on the page moves up to take the space of the div with a class of showMe.](https://hychalknotes.s3.amazonaws.com/I-can-be-hidden.gif)


## Exercise

For some practice with the advanced CSS selectors, download [css-advanced-selectors--conEd by clicking here](https://hychalknotes.s3.amazonaws.com/css-advanced-selectors--conEd.html) and open up the answer key [css-advanced-selectors-ANSWER--conEd.html by clicking here](https://hychalknotes.s3.amazonaws.com/css-advanced-selector-ANSWER--conEd.html) in the browser for reference.


## Resources

* [:nth-child, MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-child)
