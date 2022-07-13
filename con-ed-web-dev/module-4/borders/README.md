# Borders

Borders add styling to our elements and help create visual breaks in our content. They take three properties that define their width, color and style: `border-width`, `border-color` and `border-style`.

The below would result in a border that is 10px thick, red in color and solid in style.

```css
.box1 {
  border-width: 10px;
  border-color: red;
  border-style: solid;
}
```


## Border style

`border-style: <border style name>;`

CSS borders come with a range of border styles that are specified by keywords. They include:

* Solid 
* Dotted
* Dashed
* Groove
* Ridge
* Inset
* Outset 

![Range of border styles](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-13%20at%205.37.41%20PM.png)

If this value is not included, the border will not appear.


## Border color

`border-color: <any color format value>;`

Borders can take any color format. If it is not specified, the color is inherited from the element to which the border is applied.


## Border width

`border-width: <numerical width in pixels, em or rem or keyword value>;`

Border width allows developers to control the thickness of the border. It can be set using `pixel`, `em` or `rem` values or with the following keywords:

* `thin`
* `medium`
* `thick`

Note that the keywords have no defined thickness and may not be consistent. The only consistent quality is that `thick` will be thicker than `medium`, and `medium` will be thicker than `thin`. If no width value is provided, it defaults to `medium`.


## Border shorthand

`border: <border-width> <border-style> <border-color>;`

To help limit the amount of lines of code, border has a shorthand that is commonly used. It is useful if you are creating a border has the same styles on all sides of the element.

The below code will create a border that is 10px thick, dotted in style and green in color.

```css
header {
  border: 10px dotted green;
}
```

Note that the order of the values in the shorthand does not matter.


## Targeting individual sides

`border-[side]-[property]: <value>;`

Similar to margin and padding, borders can be targeted by specific sides and given unique values. The sides are targeted with the keywords `top`, `right`, `bottom` and `left`.

For example, the below code is applying a border only to the bottom of the element: 

```css
.borderFun {
  border-bottom-width: 10px;
  border-bottom-color: red;
  border-bottom-style: solid;
}
```


## Border radius

`border-radius: <value in pixel or percentage>;`

Almost all elements in HTML are rectangles by default, which have 90 degree corners. There are cases where a design may call for softer edges, which is made possible by the `border-radius` property. It enables developers to round the corners of an element while the element's 'footprint' (the space it takes up) retains its original shape (ie. a rectangle). This means that while the element may appear smaller with a border-radius applied, that's just an illusion.

The below is an element with the class of `.box1`, with a border-radius of 12px applied.

```css
.box1 {
  background: red;
  height: 200px;
  width: 200px;
  border-radius: 12px;
}
```

![border radius example with 12px](https://hychalknotes.s3.amazonaws.com/border-radius-all-sides--conEd.png)

### Border-radius shorthand
`border-radius: <top-left-corner> <top-right-corner> 
<bottom-right-corner>
<bottom-left-corner>;` 

There is also a shorthand available to give an element's corners different values. It begins in the top left corner of the element and follows the order of corners in a clockwise order.

The below example has:
* A top-left border radius of 5px
* A top-right border radius of 10px
* A bottom-right border radius of 100px
* A bottom-left border radius of 1px

```css
.superCool {
  background: blue;
  height: 200px;
  width: 200px;
  border-radius: 5px 10px 100px 1px;
}
```

![different border-radius example](https://hychalknotes.s3.amazonaws.com/border-radius--example--conEd.png)

Similar to padding and margin, the shorthand for border-radius can be further shortened by using two values with the following syntax:

`border-radius: <top-left-corner>/<bottom-right-corner> <top-right-corner>/<bottom-left-corner>;`

```css
.sortaALime {
  background: lime;
  height: 200px;
  width: 200px;
  border-radius: 20px 80px;
}

```
![Lime green div with the same border-radius in the top left corner and the bottom right corner and a different corner radius in the top right corner and the bottom left corner.](https://hychalknotes.s3.amazonaws.com/border-radius-short-form--conEd.png)


## Making a circle

Any value over 50% border radius will result in a perfect circle, if the dimensions of the element are a perfect square to begin with. Setting border-radius to 50% or 100% to create a perfect circle is considered a best practice.

```css
img {
  border-radius: 50%;
}
```

![circular portrait of a golden retriever dog](../assets/border-radius-dog.png)


## Box-shadow

`box-shadow: <offset x value> <offset y value> <blur-radius value> <color in any format>;`

While not an official "border", the CSS property `box-shadow` creates a shadow-effect on either all sides, or a specific side of an element.

In the below example, the `<div>` has a box-shadow that is:
* 10px moved from the left. This is the offset x-value, and a negative value would result in the shadow being moved from the right.
* 10px from the top. This is the offset y-value, and a negative value would result in the shadow being moved from the bottom.
* Has a blur radius of 15px. The higher this number, the more intense the blur will be.
* A color of black.

```html
<div>
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nobis qui veritatis saepe cum corrupti ex quibusdam, magni quas autem, deserunt sint alias. At et, sed veniam, beatae porro animi qui. Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nobis qui veritatis saepe cum corrupti ex quibusdam, magni quas autem, deserunt sint alias. At et, sed veniam, beatae porro animi qui.</p>
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nobis qui veritatis saepe.</p>
</div>
```

```css
div {
  box-shadow: 10px 10px 15px black;
  width: 800px;
}
```

![A div with a black shadow coming out from the bottom-left of it](https://hychalknotes.s3.amazonaws.com/box-shadow--conEd.png)

Box-shadows can create a multiple border-effect, which is useful because an element can only accept a single border:

```css
div {
  width: 800px;
  border: 1px solid black;
  box-shadow: -10px -10px 1px black, -20px -20px 1px red, -30px -30px 1px green;
}
```

In the above example, three box-shadows are used. Notice that they are separated by commas. 

![A div with multiple box shadows coming out of the top-right in black, red and green](https://hychalknotes.s3.amazonaws.com/box-shadow-multiple--conEd.png)


## Exercise

Take a few minutes with your completed version of [css-margin-padding-exercise.html](https://hychalknotes.s3.amazonaws.com/css-margin-padding-exercise.html) from earlier in the class and try to change the layout to:

* Add borders to at least three elements.
* Give the wrapper a different border for each side.
* Properly center align the `<div>` with the class of ".moreinfo".
* Play around with margin and padding. Try using shorthand!