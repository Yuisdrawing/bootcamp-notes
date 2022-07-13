# Advanced layouts

Flexbox allows developers to create fluid layouts using its two axes, the main axis and the cross axis. With the addition of flex-basis, many complex layouts are made possible with a few lines of code.

The key to good web development is creating consistent, predictable code. Developers should be able to code and understand the behaviors that will be rendered in our browsers. Using advanced layout methods, we can create even more consistency to our rendered layouts.


## Multi-unit layouts

As more advanced layouts are created, developers may use different unit values. For example, percentages are extremely useful for larger layout pieces, which may have unequal amounts of content that you would like to keep a consistent size in relation to the size of the browser. Other units like vw, vh, or pixels can be better suited for margins.

Download and unzip [multi-unit-layout](../../exercises/multi-unit-layout.zip?raw=true) to follow along with the examples below.

Currently in index.html, the `<article>` with a class of `.firstArticle` and the `<article>` element with a class of `.secondArticle` are not sitting next to each other. Let's give them percentage widths, meaning that each `<article>` element will grow or shrink accordingly as the browser gets larger or smaller.

```css
.firstArticle {
  width: 80%;
  /* will take up 80% of the total width of its parent */
}

.secondArticle {
  width: 20%;
  /* will take up 20% of the total width of its parent */
}
```

By flexing the element with a class of `.articleSection`, the `<article>` elements will flex next to each other.

```css
section {
  background: #E9DFD9;
  display: flex;
}
```

Because we have given widths to our elements, we assume that what is being rendered is the first element taking up 80% of the width, and the second taking up 20%. Is that really the case? To test this out, apply `flex-wrap: wrap;` to `.articleSection`.

```css
section {
  background: #E9DFD9;
  display: flex;
  flex-wrap: wrap;
}
```

The flex children have wrapped onto separate lines, because while 80% + 20% = 100%, there is also horizontal margin on both `<article>` elements:

```css
article {
  border: 2px solid #404041;
  padding: 10px;
  margin: 0 10px;
}
```

The total width of the elements plus the margin is greater than 100%:  
`80% + 20% + 10px + 10px + 10px + 10px = 100% + 40px`
This makes the second element wrap onto the next line. The `<article>` elements are now truly 20% and 80% in width; that means that before they were slightly smaller though - why?

The wonders of Flexbox, that's why!
* Flexbox forces its flex children to fit on a single line - regardless of set widths - by manipulating their sizes; that is unless `flex-wrap: wrap` is set on the flex parent. Once `flex-wrap: wrap` applied, the flex children's widths will no longer be manipulated by flexbox. 


A quick review of the Box Model:
The Box Model dictates how everything on the internet is layed out. 

![Box model with three boxes side by side](https://hychalknotes.s3.amazonaws.com/box-model-3boxes--conEd.jpg)

By default, we apply `box-sizing: border-box` in our `setup` snippet to ensure that padding and border are included in the total calculation of height and width on elements. Margin is *not included* in that amount, meaning our elements will have a footprint beyond the size of their set widths when they have margin applied.

Revisiting our code in "multi-unit-layout--conEd.zip", the `<article>` elements have 10px of `margin` on the left and right. This means that the amount of space needed by each `<article>` element is determined by:

`<article> width - left margin - right margin = total width`

OR 

`<article> width - both left and right margins combined = total width`

![mathdog](http://i.giphy.com/UKkes2qN2T70s.gif)

### Calc
Because Flexbox will force items to take on certain sizes, a common question is, "Do developers worry about the Box Model or perfect sizing when working with Flexbox?"

The answer is that good code is predictable code, and Flexbox manipulating our values for us is unpredictable and unsuitable. To help make code predictable, CSS has a property called `calc`. This property **calc**ulates values; it allows us to pass in equations, and does the heavy lifting for us.

`calc` can be used anywhere a unit is expected. For example, to resolve the issue from above, `calc` can be used to figure out the total width of the `<article>` elements:

```css
.firstArticle {
  width: calc(80% - 10px - 10px);
  /* width: calc(total width - left margin - right margin); */

  /*   OR   */

  width: calc(80% - 20px);
  /* width: calc(total width - both left and margin values); */
}

.secondArticle {
  width: calc(20% - 20px);
  /* width: calc(total width - both margin values); */
}
```

By using `calc`, the two `<article>` elements will now flex next to each other perfectly, without any shrinking from Flexbox!

`calc` can be used to calculate any numerical value (pixel, percentage, rem, etc.) and can be used to do any type of mathematical equation. 

```css
section {
  width: calc((100% / 3) + 20px);
}
```

The rules of BEDMAS (B - Brackets E - Exponents D - Division M - Multiplication A - Addition S - Subtraction) apply. Note that the white space in `calc` is essential and if the white space between the operators is not included, `calc` will not work. 

Incorrect 👎
```css
section {
  width: calc(65%-20px);
}
``` 

Correct 👍
```css
section {
  width: calc(65% - 20px);
}
```

### Min-width
The largest issue with setting a dynamic value like a percentage occurs when the browser is made smaller. When this happens, our `<article>` elements become extremely small because they are responding to the size of the parent and will, technically, become smaller and smaller forever. This is where static values like pixels shine!

We can prevent the `<article>` elements from becoming too small by giving them each a `min-width`:

```css
.firstArticle {
  width: calc(80% - 20px);
  min-width: 150px;
}

.secondArticle {
  width: calc(20% - 20px);
  min-width: 100px;
}
```

Once the `min-width` value is reached, the elements will stop shrinking and move to the next line because, remember, `flex-wrap: wrap` is set on the container.


### Viewport units and calc

When working with headers, especially headers that take up the full screen height (also known as "hero headers"), VH is extremely useful.

Create an HTML file called "vh-header" to follow along below.

We have seen how to create a header that takes up 100% of the viewport height. It would look something like the below:

```html
<header>
  <h1>My Website</h1>
</header>
```

```css
header {
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background: black;
  color: white;
  font-size: 40px;
}
```

![](https://hychalknotes.s3.amazonaws.com/dynamic-header--conEd.png)

The above should have no vertical scroll because of the height set.

What if we would like to add a navigation? 

```html
<nav>
  <ul>
    <li><a href="#">About</a></li>
    <li><a href="#">Contact</a></li>
  </ul>
</nav>

<header>
  <h1>My Website</h1>
</header>
```

```css
nav {
  min-height: 80px;
}
```

All of a sudden, our header will have a vertical scroll because the `<nav>` has added to the overall height, meaning our website is now `100vh` + the size of the `<nav>` (80px). This means that what we would like is a `<header>` that is `100vh - 80px`.

```css
header {
  /* ... */
  height: calc(100vh - 80px);
}
```

A popular use for `calc` is mixing `vw` units with `px` or `rem` values to create dynamically sized text. 

For example, for our header, we could set a text size of 10vw and it would increase and decrease in size as the browser gets larger or and smaller width-wise. 

```css
header {
  font-size: 10vw;
  /* ... */
}
```

While this may seem ideal, there are two large issues:
* The text can now become extremely small if the browser also becomes small. This is not ideal for smaller screen sizes like iPhones.
* This makes the text inaccessible. Viewport units cannot be scaled the same way as `rem`, `em` or `pixels` when users increase font size, meaning the text does not meet the WCAG A requirement.

By using `calc`, the font-size can be given a base static value in addition to a `vw` value that will increase and decrease with the browser size.

```css
header {
  font-size: calc(2rem + 1vw);
  /* ... */
}
```

In the above example, the typographic elements in the `<header>` will have a base value of 2rem, which is the smallest value they can be, plus a value of 1vw. The value of 1vw is dependant on how wide the browser is. This solution makes the text resizable and meets the accessibility standards.

## Exercise
Download and unzip [advanced-layout-bear-exercise--conEd.zip starter file by clicking here](https://hychalknotes.s3.amazonaws.com/advanced-layout-bears-exercise--conEd.zip). The instructions are in the CSS and HTML file. The folder includes the answer key.

## Resources
* [Solving centering problems with calc().](https://medium.com/@rbnhmll/love-in-the-time-of-calc-cc40142e4566)

