# Box-sizing

CSS Dimensions can help us size elements, and borders can help us add a border to those element, but how do these fit together? 

The property of `box-sizing` helps developers control how the heights and widths of our elements are calculated. `box-sizing` can take two values:
* `content-box` or 
* `border-box`


The Box Model is responsible for how every element is laid out and displayed based on its width, height, padding and margin. Making up [the box model](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model) we have:

* Content box: The area where your content is displayed, which can be sized using properties like width and height.
* Padding box: The padding sits around the content as white space; the amount of padding can be controlled with CSS.
* Border box: The border box represents a border that wraps the content and any padding. Its size and style can be changed using border properties in CSS.
* Margin box: The margin is the outermost layer, wrapping the content, padding and border as whitespace between this box and other elements, allowing for space between elements. Its size can be controlled using CSS properties. 

![Box-model](https://hychalknotes.s3.amazonaws.com/box-model--conEd.jpg)

<!-- ![Box model with three boxes side by side](https://hychalknotes.s3.amazonaws.com/box-model-3boxes--conEd.jpg) -->



## Box-sizing: content-box

`box-sizing: content-box` is the CSS default for how to calculate an element's dimensions. It adds the padding and border values to the overall height and width of the element.

#### Adding margin

In the example below, the square is 150px by 150px because we have set a height and a width of 150px. We know that the `margin` property helps us push elements away from each other, represented by the `aliceblue` margin of 20px on the top and left of the square.

```html
<div class="square">Hello!</div>
```

```css
body {
  background-color: aliceblue;
}
.square {
  background: forestgreen;
  width: 150px;
  height: 150px;
  margin: 20px;
}
```

![green square, with margins](https://hychalknotes.s3.amazonaws.com/pre-box-sizing-example1-1box--conEd.png)

#### Adding padding
Adding the `padding` property is used to create "breathing room" for the content inside of an element as shown by the 25pxs of padding added below.

```css
.square {
  background: forestgreen;
  width: 150px;
  height: 150px;
  margin: 20px;
  padding: 25px;
}
```

![green square, with margin and padding](https://hychalknotes.s3.amazonaws.com/pre-box-sizing-example2-1box--conEd.png)

The unexpected result is that the square has increased in size! It is no longer 150px by 150px, but 200px by 200px because `box-sizing: content-box` results in padding increasing the overall size of the element:

Width: 150px + (25px * 2) = 200px

Height: 150px + (25px * 2) = 200px


#### Adding border
Adding a `border` to the `<div>` also increases the total size. Given that the square was 200px by 200px with the added padding, a border of 25px on all sides of the element will increase its dimensions to:

Width: 200px + (25 * 2) = 250px

Height: 200px + (25 * 2) = 250px


```css
.square {
  background: forestgreen;
  width: 150px;
  height: 150px;
  margin: 20px;
  padding: 25px;
  border: 25px solid black;
}
```

![green square, with margin, padding and border](https://hychalknotes.s3.amazonaws.com/pre-box-sizing-example3-1box--conEd.png)

Download and open up [box-model-fun--conEd.html](https://hychalknotes.s3.amazonaws.com/box-model-fun--conEd.html) in your text editor and browser. 

Play around with the padding, border and margin of each box and see how it can affect their total dimensions when using CSS's default setting of `box-sizing: content-box`.

### Box-sizing: border-box
Unlike `box-sizing: content-box`, `box-sizing: border-box` will respect the height and width set on an element and will not add the padding and border to the total dimensions.

If we take the previous example that has both padding and border set but add `box-sizing: border-box` we can rest assured that the elements with the class of "square" will remain 150px by 150px. This is ideal because it makes our elements predictable to work with and avoids any tricky mental math.


```css
.square {
  background: forestgreen;
  padding: 25px;
  margin: 20px;
  width: 150px;
  height: 150px;
  border: 25px solid black;
  box-sizing: border-box;
}
```

![green square, with margin, padding, border and box-sizing: border-box](https://hychalknotes.s3.amazonaws.com/pre-box-sizing-example4-1box--conEd.png)

When starting your projects be sure to include the following code at the top of your CSS file.  The * character is a wildcard selector and selects everything on the page. It carries extremely low specificity, and we are using the power of inheritance to ensure all elements will inherit  `box-sizing: border-box`.

```css
html {
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}

*, *:before, *:after {
  box-sizing: inherit;
}
```

* Note: The `box-shadow` property is not a part of the box-model and as a result, sits outside of the border and would add to the total space an element is taking up.
