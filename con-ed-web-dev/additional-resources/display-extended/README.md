# Display - Extended

### Converting elements half step versus full step
With the `display` property, it's possible for almost any element to take on a different display value. For example, a `<span>`, which is `inline` by default, can accept the value of `block` and take on all the attributes that block-level elements have. 

```html
<span></span>
```

```css
span {
  display: block;
  width: 100px;
  height: 100px;
}
```

But the above results in what could have been achieved with a simple `<div>`, without the use of the `display` property.

As a rule of thumb, the display values given to elements to change their default behaviours should be done in "half steps" instead of full steps. 

![Image that shows that inline and block elements can become inline-block, but should never become the opposite of its own type](https://hychalknotes.s3.amazonaws.com/inline-block-diagram--conEd.jpg)

As we saw in the example above, a `<span>` can be made into a block-level element, but in this case, a `<div>` is more appropriate. A `<span>` taking on the value of `inline-block` is more appropriate because it respects the original purpose of a `<span>` as an inline element while still allowing it to take on some block-level attributes. 

As with most things in web development, there are exceptions to this rule.

## Exercise

Try practicing manipulating display values to solve common web development issues by opening up [this file by clicking here](https://hychalknotes.s3.amazonaws.com/display-exercise-image--conEd.zip) and trying to mimic the [final design which can be found by clicking here](https://hychalknotes.s3.amazonaws.com/display-exercise-image-ANSWER--conEd.zip).