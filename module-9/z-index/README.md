# Z-index

`z-index: <unitless number value>;`

When working with the different position values, we saw that elements overlap each other. CSS allows developers to control how and in what order elements overlap each other using the `z-index` property.

Flexbox allows code to be perceived in two dimensions: rows and columns. This matches with the traditional view of X and Y coordinates when working with bar graphs, but `z-index` allows us to expand that view and bring in the z-dimension when working with positioned elements (other than static).

![Graphic that shows x-index](https://hychalknotes.s3.amazonaws.com/zindex-graphic--conEd.jpg)

When using the position values of `absolute`, `fixed` ,`relative` and `sticky`, the `z-index` allows us to overlap and stack elements in ways that we would not be able to in their natural stacking order.

For example, the following code has no positioning applied to it

```html
<main>
  <section class="one">
    <p>One</p>
  </section>
  <section class="two">
    <p>Two</p>
  </section>
  <section class="three">
    <p>Three</p>
  </section>
</main>
```

```css
section {
  width: 120px;
  padding: 8px 0;
  text-align: center;
}

.one {
  background: pink;
}

.two {
  background: green;
}

.three {
  background: orange;
}
```

It results in these elements being stacked in the order in which they appear in the HTML.

![](https://hychalknotes.s3.amazonaws.com/z-index-natural-stacking-order--conEd.png)

If `position: absolute` is added to the `<section>` elements, the third `<section>` will overlap the other two elements because, by default, the order in which they appear in the HTML determines how they overlap. The last elements will overlap the element before it, etc.

 This means that the first `<section>` is at the bottom, because it is the first in the natural stacking order and the second will be in the middle because it is the second in the stacking order.

```css
section {
  /* ... */
  position: absolute;
}
```

![](https://hychalknotes.s3.amazonaws.com/z-index-absolute-stacking-order--conEd.png)


The natural stacking order can be altered using `z-index`. By default, all elements have a z-index value of 0. The order in which they stack can be changed by passing any whole number into an element's z-index.

In the below example, a `z-index` of 10 has been given to the second section, making it the highest z-index and bringing it to the "top" of the stacking order.

```css
.two {
  /* .. */
  z-index: 10;
}
```

![](https://hychalknotes.s3.amazonaws.com/z-index-10-example--conEd.png)

Any unitless whole number can be passed into a `z-index`, but a best practice is to increment your `z-index` values by multiples of 10. This allows for easier readability and can greatly assist with troubleshooting. It also helps to avoid passing in extremely large numbers like 99999999 to ensure an element is on the top of the stacking order, at the detriment of the other elements in your project. 

Note that `z-index` will not work on elements with `position: static`.


## Exercise

Open up [z-index-practice by clicking here](https://hychalknotes.s3.amazonaws.com/z-index-practice--conEd.html) and try to stack the squares in the following order: Orange (on the top), red, green, blue.

You can find the [answer key by clicking here](https://hychalknotes.s3.amazonaws.com/z-index-practice-ANSWER--conEd.html).
