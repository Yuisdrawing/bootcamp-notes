# Transforms and perspective

Transforms are a powerful tool in CSS that allow elements to be visually moved, rotated, or made into different shapes. Transforms can be used to create unique designs and help developers avoid using design programs to alter elements.

Transforms are hardware accelerated and should be used when possible instead of other similar CSS properties. When an element is transformed, z-index is available for the elements affected by the transform.

Download and open up [css-transforms-practice--conEd.html](https://hychalknotes.s3.amazonaws.com/css-transforms-practice--conEd.html) to follow along with the examples below.


## Transform types

General syntax:

`transform: <transform function>(<transform function amount>);`


### Rotate()
`transform: rotate(<rotate amount in degree or turn>);`

The rotate transform function allows developers to control how an element is rotated. It can accept values in the form of a degree, which tells the element to rotate to a given degree, or a turn, which tells the element how many "turns" it should position itself to. A full turn is 360 degree. By default, elements rotate clockwise but negative values can be passed in to rotate them counter clockwise.

```css
.box1 {
  background: rgb(34,139,34);
  transform: rotate(45deg);
}
```

The above will rotate the element with the class of `box1` 45 degrees clockwise.

```css
.box2 {
  background: rgb(255,215,0);
  transform: rotate(-0.45turn);
}
```

The above will rotate the element with the class of `box2` 0.45 of a total turn, counterclockwise.


#### Transform origin

`transform-origin: <keywords or number value in pixels or percentages>;`

When working with any of the `rotate()` functions, the elements will always rotate around the center because the rotation point is by default is the center of the element. This can be changed by using the `transform-origin` property. It accepts two different types of values that specify where the `transform-origin` will be positioned:
* keywords: `top`, `bottom`, `left`, `right` and `center` can be used alone or together.
* number values: Using pixels or percentages, either together or as single values.`transform-origin` has a default value of `50% 50%`.

`transform-origin` can accept a single value or up to three different values. If a single value is passed in, it is applied to only the x-offset axis. If two are passed, the first value is passed to the x-offset value and the second will be passed to the y-offset axis. A third value would target the z-axis for 3D transformations.

In the below example, the `transform-origin` has an x-offset value of `top` and an y-offset value of `left`.

```css
.box3 {
  background: rgb(255,99,71);
  transform-origin: top left;
  transition: all 0.3s ease;
}

.box3:hover {
  transform: rotate(40deg);
}
```

In the example below, the `transform-origin` has an x-offset value of 90% and an y-offset value of 40px.

```css
.box3 {
  background: rgb(255,99,71);
  transform-origin: 90% 40px;
  transition: all 0.3s ease;
}

.box3:hover {
  transform: rotate(40deg);
}
```

In the example below, the `transform-origin` has an x-offset value and y-offset value of 60px.

```css
.box3 {
  background: rgb(255,99,71);
  transform-origin: 60px;
  transition: all 0.3s ease;
}

.box3:hover {
  transform: rotate(40deg);
}
```


### Scale()

`transform: scale(<scale amount a unitless numerical value>);`

The scale transform function allows developers to control how an element is scaled on a 2D plane. `Scale()` accepts unitless numbers that represent how that given element will be scaled and cannot accept negative values. Whatever value is passed into `scale()` will increase or decrease the element along the x and y axis by the given numerical value. The `scale()` function's default value is 1, meaning the element will not grow or shrink.

In the below example, the element with the class of `box1` will scale to two times its size along the x and y axis on hover.

```css
.box1:hover {
  transform: scale(2);
}
```

While negative values cannot be passed into the `scale()` function, it can accept decimal points larger than 0 but smaller than 1. In the example below, the element with the class of `box1` will scale to 0.4 times smaller than it's current size along the x and y axis.

```css
.box1:hover {
  transform: scale(.4);
}
```


#### ScaleX() and scaleY()

Similar to rotate, the `scale()` function can passed to either the x or y axis only. 

In the below example, the element with the class of `box2` will scale 5 times its original size along the x axis when in an active state. 

```css
.box2:active {
  transform: scaleX(5);
}
```

It's also possible to affect both the x and y axis in one `scale()` function by passing two values to it, with the first value representing the x axis and the second representing the y axis.

In the below example, the element with the class of `box2` will scale to 3 times its original size along the x axis and 7 times along the y axis.

```css
.box2:active {
  transform: scale(3, 7);
  /* the above is the same as writing
  transform: scaleX(3) scaleY(7); */
}
```


### Translate()

`transform: translate(<numerical value in px, percentages, rem or em for the x axis>, <numerical value in px, percentages, rem or em for the y axis>)`;

The translate function allows for elements to be repositioned along the x and y axis. It can accept any numerical value, including negative numbers. It is similar to `position: relative` because the elements move relative to their original position but maintain their footprint, meaning the original stacking order is persevered. As with positioned elements, the `translate()` function is best used to add "stylistic sugar" to designs and should not be relied on to create structure.

The translate() function accepts two values, with the first value moving the element along the x axis and the second value moving the element along the y-axis. If your browser is set to a language that reads from left to right by default, all positive values will move the element to the right and all negative values to the left.

The below code would move the element with a class of `box2` 10px along the x axis (to the right) and -30px along the y axis (up).

```css
.box2 {
  background: rgb(255,215,0);
  transform: translate(10px, -30px);
}
```

It can also accept a single value, which would move the element along the x axis only. In the below example, the element with the class of `box2` would move 180px to the right.

```css
.box2 {
  background: rgb(255,215,0);
  transform: translate(180px);
}
```

#### TranslateX() & translateY()

Like most other transform types, translate also has individual functions to specifically target the x or y axis.

```css
.box2 {
  background: rgb(255,215,0);
  transform: translateY(10px);
}
```

```css
.box2 {
  background: rgb(255,215,0);
  transform: translateX(-50px);
  /* This is the same as
  transform: translate(-50px); */
}
```


#### Positioning vs. transform: translate()

The transform function `translate()` behaves similarly to `position`. There are two key differences between them to help developers understand when to use which property:
* The translate() function is hardware accelerated, as are all transform functions whereas `position` properties are not. This means they will create smoother transitions and animations, making transform functions in general a better choice when working with elements that will be animated.
* `Position` properties are best used for making larger stylistic changes, such as creating a fixed menu or overlapping two elements to create unique designs. Transform functions are most effective when enhancing position properties. 


## Multiple transforms

It is possible to use multiple transforms on a single element by adding multiple transform functions **along the same line**, with a space separating each function.

```css
.box1 {
  background: rgb(34,139,34);
  transform: rotate(60deg) scaleX(2) scaleY(1.4);
  transition: all 0.8s ease-out;
}

.box1:hover {
  transform: rotate(180deg) scaleX(2) scaleY(1.4);
}
```

In the above example, even though only one transform function is changing on hover (`rotate()`), we rewrite all three functions (`rotate()`, `scaleX()` and `scaleY()`). This is because the property is `transform`, so when applying the transform on hover, the CSS cascade overwrites the entire previous `transform` property.

This can be seen more easily in that if multiple transform properties are added one after another to the same element, the CSS cascade applies only the last transform property passed in, like it would with any CSS property:

```css
.box1 {
  transform: rotate(60deg); 
  transform: scaleX(2);
  /* The CSS only applies the last transform (scaleX(2)) and ignores "transform: rotate(60deg);" */
}
```


## Transforms exercise

Transforms can be used for some pretty interesting effects. Download and open up [polaroid-exercise--conEd.zip](https://hychalknotes.s3.amazonaws.com/polaroid-exercise-transforms-conEd.zip) and try to recreate the answer key that is found in the folder.


## 3D transforms

So far we've talked about transforming elements on a 2D plane. CSS also has the ability to transform elements on the 3D plane.


### RotateY(), rotateX() and rotateZ()

The `rotate()` function also comes with sub-rotation types that allow developers to work along the 3D plane. A degree can be passed into `rotateY()` to rotate along the Y axis, `rotateX()` to work along the X axis, and `rotateZ()` to work along the Z axis (that is to say, `rotateZ()` has the same effect as `rotate()`).

In the below code, the element with a class of `box1` has been rotated 70 degrees along the Y axis.

```css
.box1 {
  background: rgb(34,139,34);
  transform: rotateY(70deg);
}
```

![Transform Rotate example](https://hychalknotes.s3.amazonaws.com/transform-rotate-y-example--conEd.png)

It appears as if a part of the element has gotten smaller. In reality, the element is now working in the 3D plane and our browser is currently only working in the 2D plane. This results in what looks like a smaller element when the element has actually rotated in a way that we can't perceive. This is where we can use the `perspective` property to perceive the 3D plane. 


### Perspective

`perspective: <numerical value using pixels, rem or em units>;`

When dealing with 3D animations, it's important to understand the `perspective` property. The `perspective` property deals with the perceived distance to the element, relative to its z-index. The `perspective` property is placed on the parent element of the element we are rotating 3 dimensionally . When we create animations without the perspective value, the animations do not look 3D. In order to create a 3D look for our animations, we need to add a perspective value larger than 0. Similarly, to remove a 3D effect we can use `perspective: none;` (the default).

When we have a perspective value that is greater than 0, your perspective gets greater, so objects become "farther" from the user's perspective. The closer the value is to 0, the more exaggerated the animation will be. The higher the number is the more subtle the animation will be. Perspective can take keywords (`none`), or values (`1000px`, `3rem`, etc).

Important to note that the `perspective` property should be placed on the parent element, not the transformed element itself. Think of it as activating the 3D space. 

Common perspective values are 800px, 1000px, or `none`. For example: 

``` html
<main>
  <div class="box box1"></div>
  <div class="box box2"></div>
  <div class="box box3"></div>
</main>
```

```css
main {
  display: flex;
  justify-content: center;
  align-content: center;
  flex-wrap: wrap;
  /* Adding perspective property on the parent container */
  perspective: 800px;
}

.box {
  width: 250px;
  height: 250px;
  margin: 15px;
}

.box1 {
  background: rgb(34,139,34);
  transform: rotateY(70deg);
}
```

The code above will give you this:

![Box with perspective 800px](https://hychalknotes.s3.amazonaws.com/perspective800.png)

Let's try a more exaggerated look:

```css
main {
  display: flex;
  justify-content: center;
  align-content: center;
  flex-wrap: wrap;
  /* Adding perspective property on the parent container */
  perspective: 200px;
}
```
![Box with perspective 200px](https://hychalknotes.s3.amazonaws.com/perspective200.png)

## Other translate functions
There are other transform functions, like `skew()` and `matrix()` that are not touched on in this lesson. You can check them out [by clicking here](https://developer.mozilla.org/en-US/docs/Web/CSS/transform). 
