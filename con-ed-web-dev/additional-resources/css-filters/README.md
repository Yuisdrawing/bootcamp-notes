# CSS filters

CSS Filters are a powerful way to add interesting visual effects to elements that weren’t possible with CSS alone just a couple years ago! They apply styles to elements before they are rendered to a page and can be combined to make a ton of unique looks. While they’re used mostly on images, they can be used on a range of elements like `<p>`.

Many of the CSS filters will look familiar to anyone who has used a photo editing tool like Photoshop, giving more artistic control to developers directly in the browser! Another unique feature of filters is that most browsers, such as Firefox and Chrome, implement filters using hardware acceleration. This means that they have superior performance over other properties that may perform similar effects in CSS.

Download and use [css-filters-practice.html](https://hychalknotes.s3.amazonaws.com/css-filters-practice--conEd.html) to experiment with each of the filters below!

## Filter types
General syntax:

`filter: <filter function>(<filter function amount>);`

### Blur

`filter: blur(<blur amount in px, rem or em>);`


The blur filter function applies what is called a “Gaussian blur” (named after the scientist and mathematician Carl Friedrich Gauss) to reduce details in whatever it is applied to. It can accept any length value except for percentage, which dictates how many pixels on the screen will blur into each other, meaning the larger the number, the larger the blur! It has traditionally been applied to images, but it can be applied to other elements as well.

Its default value is 0, which results in no blur.

![photo of Carl Gauss](https://hychalknotes.s3.amazonaws.com/blur5px--conEd.png)


`filter: blur(5px);`

![wording blured](https://hychalknotes.s3.amazonaws.com/blur5pxParagprah--conEd.png)


`filter: blur(5px);`

Try adding a blur of 5px on the h1 in the file we downloaded. What happens to the border?

### Contrast

`filter: contrast(<contrast amount in percentage>);`

The contrast filter function adjusts the difference between the darkest and lightest parts of your element, usually an image (or something with many colours to contrast!). It accepts a percentage as a value and can accept numbers higher than 100%, but cannot accept negative values. Setting contrast to 0% or 0 will result in a completely grey element.

Its default value is 100% or 1, which results in an unchanged element.

![happy dog running](https://hychalknotes.s3.amazonaws.com/contrast0%25--conEd.png)


`filter: contrast(0%);`

![happy dog running](https://hychalknotes.s3.amazonaws.com/contrast80%25--conEd.png)


`filter: contrast(80%);`

![happy dog running](https://hychalknotes.s3.amazonaws.com/contrast150%25--conEd.png)


`filter: contrast(150%);`

Try adding a contrast of 50% on the first image in the file we downloaded.

### Brightness

`filter: brightness(<contrast amount in percentage>);`

The brightness filter function increases the brightness in a given element, usually an image, by increasing or decreasing the amount of black in relation to other colours. It’s very similar to contrast() in that it can accept a percentage value. Brightness can also accept values larger than 100% but cannot accept a negative value. Setting brightness to 0% or 0 will result in a black element.

Its default value is 100% or 1, which results in an unchanged element.

![a forest](https://hychalknotes.s3.amazonaws.com/brightness60%25--conEd.png)


`filter: brightness(60%);`

![a forest](https://hychalknotes.s3.amazonaws.com/brightness130--conEd.png)


`filter: brightness(130%);`

Try adding a brightness of 90% to the second image in the file we downloaded.

### Drop-Shadow

`filter: drop-shadow(<offset-x length> <offset-y length> <blur length> <colour>);`

Not to be confused with box-shadow, the drop-shadow filter function creates a blurred, offset version of the given element’s inner shapes whereas box-shadow creates a rectangular shadow around the entire element. Another large difference is that drop-shadow cannot take an inset value the way box-shadow can.

Here is an icon from the Noun Project:

![icon of a person playing a saxaphone](https://hychalknotes.s3.amazonaws.com/drop-shadow-filters--conEd.png)


`filter: drop-shadow(10px 10px 10px #000);`

![icon of a person playing a saxaphone](https://hychalknotes.s3.amazonaws.com/box-shadow-filters--conED.png)


`box-shadow: 10px 10px 10px #000;`

Try adding a drop-shadow of 2px 2px 2px #000 to the p tag in the file we downloaded.

### Grayscale

`filter: grayscale(<grayscale amount in number or percentage>);`

The grayscale filter function converts the given element, usually an image, to grayscale by converting the colours within it to different degrees of the colour gray. It can take a number or percentage value, but a percentage value is the most commonly used. Like other filter elements, it cannot take a negative value. Setting grayscale to 100% (or 1) will convert an element to a complete grayscale.

Its default value is 0% or 0, which results in an unchanged element.

![city with a canal](https://hychalknotes.s3.amazonaws.com/greyscale60%25--conED.png)


`filter: grayscale(60%);` → or grayscale(0.6)

![city with a canal](https://hychalknotes.s3.amazonaws.com/greyscale100%25--conED.png)


`filter: grayscale(100%);` → or grayscale(1)

Try using grayscale on one of the images in the file we downloaded.

### Opacity

`filter: opacity(<opacity amount in number or percentage>);`

The opacity filter function dictates the amount an element will appear transparent. It can take a number or percentage value, with 100% or 1 being full opacity and 0% or 0 being full transparency. It cannot accept a negative value.

Its default value is 100% or 1, which results in a fully visible/opaque element.

This element is extremely similar to the CSS property ‘opacity’, which in essence has the same effect on elements. The largest difference is that some browsers implement filters using hardware acceleration meaning that `filter: opacity()` will have better performance than with the opacity property.

![](https://hychalknotes.s3.amazonaws.com/opacity-filter--conEd.png)


`filter: opacity(0.4);`

OR

`opacity: 0.4;`

### None
All CSS filters can take the value of none, which would remove any filters on an element.

`filter: none;`

Other CSS filters include:
Invert, sepia & hue-rotate. Visit the MDN docs on CSS filters to learn how to use them here: [https://developer.mozilla.org/en-US/docs/Web/CSS/filter](https://developer.mozilla.org/en-US/docs/Web/CSS/filter).

### Multiple filter values
What if you want to use multiple filters on one element? You must declare them on the same line together, without commas. Please keep in mind that the order in which you state the filters will affect the end result.

![](https://hychalknotes.s3.amazonaws.com/contrastBrightness--conED.png)


`filter: contrast(180%) brightness(120%);`

Vs.

![](https://hychalknotes.s3.amazonaws.com/brightnessContract--conED.png)


`filter: brightness(120%) contrast(180%);`

The two images look super similar, but take a look at the middle blue colour, next to the yellow. There's a slight difference in how the blue is being rendered. While this change may not make-or-break your website, it's important to keep in mind that the order of filters will affect the outcome you get!

> **Accessibility tip**
>
> Some users may have different colour settings on their devices or may be affected by colour blindness. It's important to note that if the filters you are applying are vital to the understanding of your content, they should be included in either an alt tag (for images) or written out clearly in an explanation for users.
> WCAG requires a contrast ratio of at least 4.5:1 for normal text and 3:1 for large text, and a contrast ratio of at least 3:1 for graphics and user interface components (for example, form input borders). (WCAG Level AA)

### Filter inheritance
If a filter style is set on a parent, it will be inherited by all the children. For example, if we take this header

![header with words](https://hychalknotes.s3.amazonaws.com/inherited-pre-blur--conEd.png)

and set `filter: blur(8px);`, all of the children within the header will inherit the CSS filter.

![Blured Header](https://hychalknotes.s3.amazonaws.com/inherited-blur--conEd.png)

Which means all of the elements inside of other header will also have a blur of 8px.

### CSS filter browser support
As of 2019, CSS Filters are supported on Firefox and Chrome, have partial support on Edge and have no support on Internet Explorer or Opera Mini (shocker!). To use them in Safari, it is required to use the vendor prefix: -webkit-.

*Please note: filters are currently in the “experimental” phase in the current CSS spec, but the ones noted above are all expected to get through! It’s worth noting that their behaviour may change in the future depending on the conclusions the CSS Working Group comes to.*

### Filters in Dev Tools
Firefox has fantastic Dev Tools to help us make the most out of filters!

Next to any filters in your CSS, in your dev tools, you'll notice a circle that is half gray and half white. If you click on it, Dev Tools gives you the chance to customize and stack other filters on your element!

![Firefox Filters Dev Tools](https://hychalknotes.s3.amazonaws.com/firefox-filter-dev-tools--conEd.png)

### Exercise
Follow the instructions inside of the [exercise by clicking here](https://hychalknotes.s3.amazonaws.com/css-filters-instagram--conEd.zip) to mimic the [answer key by clicking here](https://hychalknotes.s3.amazonaws.com/filters-exercise-instagram-ANSWER--conEd.zip).

### Resources
* [MDN CSS Filters](https://developer.mozilla.org/en-US/docs/Web/CSS/filter)
* [CSS Filter Generator](https://cssgenerator.org/filter-css-generator.html)
* [CSS Filters Demonstration by Instructor Robin Hamill](https://codepen.io/rbnhmll/full/JxzOBB)
