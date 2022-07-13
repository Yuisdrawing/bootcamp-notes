# Backgrounds

CSS allows backgrounds to be set on most elements, either as an image or a color. The background you set will appear within the dimensions of the given element and behind any of the child elements.

CSS backgrounds have a range of properties used to define how the background will appear.

Download the folder [backgrounds-fun--conEd.zip](https://hychalknotes.s3.amazonaws.com/backgrounds-fun--conEd.zip) and use it to play around with the below concepts.


## Background color
`background-color: <color value in any format>;`

To set a background color on an element, use the `background-color` property and set any of the color formats as the value:

```html
<header>
  <h1>Hello!</h1>
</header>
```

```css
header {
  background-color: #9000ff;
  color: white;
  height: 300px;
}
```

Try copying and pasting the code above and open it up in your browser.

Try removing the height from the header in your CSS to see what happens, and then try removing the `<h1>` from the header and check to see how it renders in your browser. The background should completely disappear. 

To set a background, there needs to be either content inside or a height value set on the element for the background to be seen. That's because elements, like `<header>`, do not have a height set by default and there is nothing for the background to be the background for. 

> **Accessibility tip** 
>
> Use caution when deciding background and text colors. Low contrasts can make content difficult or impossible to read. WCAG AA requires a contrast ratio of 4.5:1 for normal text and 3:1 for large text. Logos or brand names have no contrast requirements or minimums. [This is a great tool for checking color contrasts](http://leaverou.github.io/contrast-ratio/#%23555-on-white), and [this is another great resource, too](https://www.w3.org/TR/WCAG20#visual-audio-contrast-contrast).

## Background image
`background-image: url(<absolute or relative image path>);`

To set an image as a background, use the `background-image` property on the element you want to set the background image on.

Similar to a regular `<img>` element, the image source has to be provided and can be either an absolute or relative. But unlike an `<img>` element, the source is set in the CSS using `url()` as the value (not in the HTML with the `src` attribute) and the background image does not take an `alt` attribute. 

Setting an image element using an absolute image path:
```html
<img src="https://placekitten.com/200/300" alt="Placeholder image from placekitten.com">
```

Setting a background image using an absolute image path:
```css
body {
  background-image: url(https://www.google.com/images/srpr/logo3w.png);
  height: 800px;
}
```

Most of the time, `background-image` will have a relative image path because it's likely a background image will be an asset in your site folder. In that case, it would be a relative path:

```css
body {
  background-image: url(./assets/fishFriend.jpg);
  height: 800px;
}
```

There are a couple of things to note in the above code:

* The relative path: The relative path in this example starts with a `./`. Computers are extremely literal and need to understand exactly which path to go down to get to any resources we are linking to. 
    * no dots or slashes -> "Stay in the same level"
    * `./` -> "Stay at the same level"
    * `../` -> "Move outside of folder"
    * `../../` -> "Move outside of two levels of folders"

    Browsers read paths from right to left, meaning in the above code, the browser will look for the asset in this order:

    * An asset called "FishFriend.jpg"
    * That lives in a folder called assets
    * That assets folder lives on the same folder level as the CSS style sheet.

    Check out the additional resource about [pathing by clicking here](../../additional-resources/pathing) if you ever need help. 

* No `alt` attribute: Background images do not take an `alt` attribute, meaning they are not perceived or interacted with by AT. Background images are meant to be exactly that - backgrounds. They are there to enhance our website, not to provide context to our content the way an `<img>` element does. They are the "nice to have", but not the "crucial" images of your site.

> **Accessibility tip** 
>
> When should I use `background-image` vs. an `<img>` element?
>
> When the image provides context to the content of your page, use an image element. For example, if you were on a store's website that sold jackets, the images of jackets should be the `<img>` element because they are crucial to the understanding of the user and as a result, should not/do not belong in the "background". If the image is purely for aesthetics (i.e. if it disappeared, the user could still understand the website's content), use a background image. 
> Keep in mind that background-images do not take an `alt` attribute, meaning AT cannot interpret what they are and will not read them out loud to the user.

### Background repeat
`background-repeat: < repeat-x, repeat-y, repeat, or no-repeat>;`

Background images will by default repeat to fill the space available. How the background repeats and in what direction can be controlled with the `background-repeat` property.

To prevent it from repeating, pass in a value of `no-repeat`:

```css
header {
  background-image: url(./assets/fishFriend.jpg);
  background-repeat: no-repeat;
  height: 800px;
}
```

Once again, this relative file path to the image is telling the browser to look for the 'assets' folder on the same level as the current CSS style sheet.


### Background position

`background-position: < <x-axis> <y-axis> in pixel or percentage, or keyword>;`

To control which part of the background-image is shown or where we would like the background image to repeat, we can use the `background-position` property. It can accept up to two values, which specify a position along the x and y axes. 

The values passed to the `background-position` property can be keywords, pixels or percentages. This course is going to cover using keywords and pixels.


#### Keywords

Available values are `top`, `left`, `right`, `bottom` and `center`. By default, the browser uses `left top`. The keywords position the background image relative to the edges of the element.

The below example is positioning the background image to the left along the horizontal axis (x-axis) and the bottom of the vertical axis (y-axis)

```css
body {
  background-image: url(./assets/fishFriend.jpg);
  background-repeat: no-repeat;
  background-position: left bottom;
  height: 800px;
}
```

Keyword values also have the ability to center a background image along both axes using a single value of `center`

```css
body {
  background-image: url(./assets/fishFriend.jpg);
  background-repeat: no-repeat;
  background-position: center;
  height: 800px;
}
```

If only one value is passed in, the second value is assumed to be `center`

```css
body {
  background-image: url(./assets/fishFriend.jpg);
  background-repeat: no-repeat;
  background-position: bottom;
  /* The above is the same as writing `background-position: bottom center;` */
  height: 800px;
}
```

### Background size

`background-size: < <width> <height> in pixel or percentage, or keyword>;`

Background images render at their original size unless altered with the `background-size` property. Similar to `background-position`, `background-size` can accept either keywords, pixel or percentage values, and either a double or single value.

If two values are set, they dictate the width and height of the element. The below is setting the size of the element to a width of `200px` and a height of `100px`.

```css
body {
  background-image: url(./assets/whistler.jpg);
  background-repeat: no-repeat;
  background-size: 200px 100px;
  height: 800px;
}
```

Using a single value will set the width of an element to whatever value is specified and sets the height to auto:

```css
body {
  background-image: url(./assets/whistler.jpg);
  background-repeat: no-repeat;
  background-size: 200px;
  /* This is the same as writing background-size: 200px auto; */
  height: 800px;
}
```

#### Keywords

The `background-size` property has two available keywords: `contain` and `cover`.

`contain` allows the background image to scale as large as possible without being cropped or stretched.

```css
body {
  background-image: url(./assets/whistler.jpg);
  background-size: contain;
  height: 800px;
}
```

`cover` scales the image to be as large as possible without distorting it, but if the image ratio is larger than the element itself, the image will be cropped.

```css
body {
  background-image: url(./assets/whistler.jpg);
  background-size: cover;
  height: 800px;
}
```

<img src="https://hychalknotes.s3.amazonaws.com/background-size.png" alt="visual examples of what background-size does, showing differences between cover and contain.">


### Background attachment

`background-attachment: <keyword>;`

The `background-attachment` property dictates how a background image reacts when the user scrolls. It has two available keywords: `fixed` and `scroll`.

`fixed` gives a faux-parallax effect on background images. If the user scrolls, the background will not move with the element.

```css
body {
  background-image: url(./assets/whistler.jpg);
  background-size: cover;
  background-attachment: fixed;
  height: 800px;
}
```

`scroll` is the `background-attachment` default, and it allows the background image to behave as we expect when the user scrolls.

```css
body {
  background-image: url(./assets/whistler.jpg);
  background-size: cover;
  background-attachment: scroll;
  height: 800px;
}
```


## Background shorthand

It is possible to combine all the background properties in a single `background` property. This is known as writing shorthand. 

```css
body {
	background: [background-color] [background-image] [background-position] / [background-size] [background-repeat] [background-clip] [background-attachment];
}
```

(Note: The above shorthand includes a property called `background-clip`. This course does not cover that property but you can learn more about it by [clicking here](https://developer.mozilla.org/en-US/docs/Web/CSS/background-clip).)

So for example, we can write something like:

```css
body {
  background: red url(./assets/fishFriend.jpg) top right / 450px repeat-y fixed;
  height: 800px;
}
```

The background shorthand is special because it does not require every property in order to work. For example, if you did not include a `background-position` value in your shorthand, the `background` property would still work with the remaining values.


## Background gradients
Background gradients are a member of the background-image family, even though they are made up of colors. Gradients can help create beautiful effects over images or they can stand alone. They can be created using the `background-image` property or with the `background` shorthand.


### Linear gradient
`background-image: linear-gradient(<direction>, <color value>, <color value>... [ ... ] ...<color value>)`

A linear gradient is a CSS function that results in an image that consists of one or more colors blended together at certain points and on a certain angle. Its size will match the size of the element it is applied to.

The reason gradients must be written with the `background-image` or `background` shorthand property and not with the `background-color` property is that gradients are considered a special type of image in CSS.

A linear gradient accepts multiple values:
* The first value is the axis over which the gradient will form. It can be written in either of two ways:
  * In degrees, with the unit `deg`, to specify an angle measured clockwise from the top-center of the element.
  * Using the word `to`, followed by one or two directional keywords (`bottom`, `left`, `right` and `top`), to create values like `to right`, `to left bottom`, `to top left`, etc.
* Two or more color values. Gradients can accept any color format, including RGB/RGBA, hex or color keywords.

In the below example, there is a linear gradient at a 45 degree angle that will start with blue and transition to red:

```css
div {
  background-image: linear-gradient(45deg, blue, red);
  height: 600px;
}
```
In the below example, there is a linear gradient forming towards the top right of the element and will start with pure black transitioning to pure white. However, gradients can take as many colors as you'd like:

```css
div {
  background-image: linear-gradient(to top right, #000, #fff);
  height: 600px;
}
```

There are myriad combinations of colors and angles to shape linear-gradients and to help create or spark ideas it is effective to turn to a [Linear gradient generator](https://cssgradient.io/).


## Background-images and accessibility 
Words within images, including background-images, are not read by AT. To resolve this, there is a industry-standard class name called "sr-only" that allows developers to add text in that will be invisible to sighted users, but read out loud by AT.

The "sr-only" class looks like this and should go at the top of your CSS:

```css
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  border: 0;
  padding: 0;
  white-space: nowrap;
  clip-path: inset(100%);
  clip: rect(0 0 0 0);
  overflow: hidden;
}
```

This is going to "hide" the content but will still be read by screen readers. We need to have a height and width of 1px because anything smaller won't be read by a screen reader. The mix of other CSS properties ensures that visual users won't be able to see the content. 

For example, if you have a background-image that has the words "Huge Sale! 50% Off!" in it, add the following span nested inside the element holding the background-image:

```html
<span class="sr-only">
  <p>Huge Sale! 50% Off!</p>
</span>
```

This will make the <span> available to non-sighted users!

## Exercise
Download [this background exercise by clicking here](https://hychalknotes.s3.amazonaws.com/css-backgrounds--conEd.zip), and follow the instructions inside of the index.html. You can also open up the answer key in your browser to see what the end result should look like.

When in doubt, don't be afraid to look back in the notes or Google your question! Google is every developer's best friend - no one can know everything and there's no shame in the internet-please-help-me game. 

## Resources
* [A great tool to play around with background-position](https://www.w3schools.com/cssref/playit.asp?filename=playcss_background-position&preval=10px%20200px)
* [Using CSS gradients](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Images/Using_CSS_gradients)
* [Linear gradient generator](https://cssgradient.io/)
* [Background shorthand explanation](https://developer.mozilla.org/en-US/docs/Web/CSS/background)
* [Awesome background reference](https://cssreference.io/backgrounds/)


