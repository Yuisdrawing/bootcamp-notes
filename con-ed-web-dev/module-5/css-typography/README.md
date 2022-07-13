# CSS typography

Understanding CSS typography is one of the best ways to make your site more user friendly and to add stylistic touches. Typography can also help make our sites more accessible and can make or break a website's feel and tone.

We have seen some typographical elements in earlier lessons, such as headings:

```html
<h1>Heading 1</h1>
<h2>Heading 2</h2>
<h3>Heading 3</h3>
<h4>Heading 4</h4>
<h5>Heading 5</h5>
<h6>Heading 6</h6>
```

As well as paragraph, emphasis and strong elements:

```html
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna deserunt mollit anim id est laborum.</p>

<p>Hey there my name is <strong>Juno</strong> and I <em>really</em> like to code HTML and CSS.</p>
```

Open up [learning-typography.html](../../exercises/learning-typography.html?raw=true) so you can follow along with the below concepts.


## Font size

`font-size: <font size in any measurement type, including pixel and rem>;`

The CSS `font-size` property allows developers to control the font size of typographical elements. It accepts any measurement type, and can be set directly or inherited from parent to children.

In the below example, the font size is being set in pixels directly on the paragraph element.

```css
p {
  font-size: 18px;
}
```

Or use the power of inheritance! If all the typographical elements inside of a parent largely share the same font size, it can be set on the parent and inherited by all of the children:

```css
section {
  font-size: 20px;
}
```

It is common to set the font size on the body and allow all elements to take a base font size. This allows code to be more DRY because it allows us to set the font size in one place instead of having to do so for each and every element. This ensures no elements are missed.

```css
body {
  font-size: 18px;
}
```

> **Accessibility tip**
>
> Font sizes should be legible for all users. Avoid setting a base font size, or using font sizes, below 18px. Note that pixels are a static measurement unit, meaning that it will not change, regardless of its parent's font size or the browser size.


### Relative font size

There are multiple types of relative font size measurement unit types available, such as percentage, em and rem. 

In this course, we are going to utilize the `rem` extensively. Using the `rem` measurement unit type as a font size is great for creating relative font sizes with respect to a root size.

The root is the `<html>` element and we can set a size on it so it will be inherited to all of the children within the document:

```css
html {
  /* makes the default font 20px */
  font-size: 125%;
}
```

Now whenever we want to declare a font size, a `rem` value can be used which is a multiple of the base size.

```css
/* 2.4rems = base font size ✕ 2.4 */
h1 {
  font-size: 2.4rem; /* 48px */
}

/* 1.8rems = base font size ✕ 1.8 */
h2 {
  font-size: 1.8rem; /* 36px */
}
```

While `rem` values can seem like a lot of work, they are extremely useful in larger and more advanced projects. If a larger font size is needed throughout, only one value needs to be changed for the entire document to be effected.

It is a best practice to set the root font size as a percentage because this allow users to adjust the default font size in their browser, whereas absolute pixel sizes prevent them from doing so. The default font size in most browsers is 16px, which is quite small, so we want to ensure we allow users to maintain that control.

This is an extremely powerful tool, not only for ease of use for developers, but also for accessibility, as it allows users to set different font sizes and the entire document will react appropriately.

### Alternative options

Other than 125%, 62.5% as the root percentage is the prevalent standard. The reason for this is it makes calculating rem values significantly easier as `font-size: 62.5%` results in `1rem = 10px`, `2rem = 20px`, `2.5rem = 25px`.

Importantly, we cannot leave our pages with a default font size of 10px. We need to make sure that when we are using 62.5% we are also including:

```css
body, p { 
 font-size: 1.8rem; /* 0.625 * 16px * 1.8 = 18px */
}
``` 


> **Accessibility tip**
>
> With the exception of captions and text in images, users should be able to zoom up to 200% with the font size growing accordingly. Setting a base value with a percentage is the only way to achieve this requirement  (WCAG AA). Read more about this requirement [by clicking here](https://www.w3.org/TR/UNDERSTANDING-WCAG20/visual-audio-contrast-scale.html).


## Font weight

`font-weight: <keyword or numerical value>;`

Fonts come with a variety of weights, which developers use to control the boldness of a font. They can be accessed via numerical values or keywords and can be inherited from parents.


 ### Numerical value

 Depending on the font, weight can be specified using any number between 1 and 1000, even though it is most common to see fonts set using a multiple of 100. The larger the number, the more bold the font will appear. 

```css
p {
  font-weight: 600; 
}
```

Note that many fonts by default only have the font weights of `400` and `700` available.


### Keyword

Instead of using numerical values, keywords can be used to set a font weight.

```css
p {
  font-weight: normal; /* 400 */ 
}

span {
  font-wight: bold; /* 700 */
}
```

If a parent is set to the `bold` or `normal` keyword, or their numerical equivalents, the `lighter` and `bolder` keywords can be used if the font family has the font weights available. The `lighter` and `bolder` keywords are relative values based off of the parent.

```html
<header>
  <h1>Hello!</h1>
  <h2>I like cats</h2>
</header>
```

```css
header {
  font-weight: bold;
}

h2 {
  font-weight: bolder;
}
```

In the above example, the `<h2>` would be a more intense bold than the `<h1>`, because the `<h1>` is inheriting the `font-weight` of `bold` from its parent, while the `<h2>` is set to a bolder weight than the same parent.


## Font style

`font-style: <keyword>;`

Similar to `font-weight`, `font-style` allows you to change the style of the font, if that font family has that style available. Font styles can be accessed via keywords and can be inherited from parent elements to typographical child elements.

The keywords include:
* `normal`: This is the default styling of the font-family.
* `italic`: This is what most users would understand as the classic italic font they have seen in the past. It is usually a sub-style of a given font and if not is not available, it defaults to `oblique`.
* `oblique`: While `oblique` can sometimes look like `italic`, it has some [technical differences](https://developer.mozilla.org/en-US/docs/Web/CSS/font-style).

> **Accessibility tip**
>
> Users with visual and cognitive concerns may have difficulties when dealing with text that is using the `italic` or `oblique`. Consider only using different font styles only when necessary. (WCAG AAA)


## Line height

`line-height: <numerical value, with or without a unit type>;`

Line height lets you explicitly set the height of a line of text as it appears in the browser. Designers may know this as "leading". This can dramatically help the readability of large blocks of text. It can be set using a variety of measurements including px, ems and percentages, or a unitless number that will multiple the font height. Line height may also be inherited by typographical elements from their parents. 

The below example is setting all `<p>` elements to a fixed line height of 1.5px:

```css
p {
  line-height: 1.5px;
}
```

We can also set it as a number without a measurement type, specifying a relative size based on the font size. This is an ideal approach because it ensures users who are enhancing their font sizes will not have any text cut off as line heights grow with the font size.

```css
p {
  font-size: 20px;
  line-height: 1.6;
}
```

In the above example, a line-height of 1.6 is set, meaning it is 1.6x the given font size. In this case, the line-height would be 32px.


## Text align

`text-align: <keyword values>;`

The `text-align` property allows developers to set the horizontal alignment of block-level elements, such as `<p>` or `<h3>`, using keyword values. It is inherited to all block-level children when set on a parent. The keyword values available include:

* `left`: Inline elements are aligned to the left side of the total element.
* `right`: Inline elements are aligned to the right side of the total element.
* `center`: Inline elements are aligned to the center of the total element.
* `justify`: Inline elements are spaced so they touch both the right and left side of the total element.

```css
p {
  text-align: right; 
}
```


## Text transform

`text-transform: <keyword values>;`

The `text-transform` property allows the CSS to control how text will be capitalized. It uses keywords to specify the use of capitalization in text. Sometimes a design calls for text that uses only uppercase letters. This can be accomplished using the following HTML:

```html
<nav>
  <ul>
    <li><a href="#">HOME</a></li>
    <li><a href="#">ABOUT</a></li>
    <li><a href="#">RECIPES</a></li>
  </ul>
</nav>
```
However, HTML should only be used to describe content, and this example is incorrectly using HTML for styling purposes. This is where `text-transform` is useful. Its keywords are:

* `uppercase`: All selected text becomes uppercase text.
* `lowercase`: All selected text becomes lowercase text.
* `capitalize`: All selected text has the first letter of every word turned into a capital letter.
* `none`: Removes all `text-transform` values from affecting the given element.

Taking the example from above, we can use `text-transform`:

```html
<nav>
  <ul>
    <li><a href="#">home</a></li>
    <li><a href="#">about</a></li>
    <li><a href="#">recipes</a></li>
  </ul>
</nav>
```

```css
li a {
  text-transform: uppercase;
}
```

This also future-proofs our code because we can change the capitalization later on just by altering one line of CSS instead of multiple words in our HTML.

> **Accessibility tip**
>
> It's best practice to use uppercase only for short words and sentences, as using all capitals can be difficult to read. Also note that screen readers can sometimes misinterpret all capitals as acronyms, and letters will be read individually. CONTACT US becomes CONTACT U.S.


## Text decoration

This property, `text-decoration`, helps style decorative lines around elements and is made up of three properties that accept keyword values. The most common default occurrence of `text-decoration` is on anchor elements which have a default `text-decoration` value of `underline`.


### text-decoration-line

Defines the type of line decoration will be used. The available types are:
* `underline`
* `overline`
* `line-through`
* `none` (this just looks like regular text)


![screen shot of text-decoration underline on the word underline](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-13%20at%205.45.03%20PM.png)

![screen shot of text-decoration overline on the word overline](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-13%20at%205.45.10%20PM.png)

![screen shot of text-decoration line-through on the word line-through](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-13%20at%205.45.17%20PM.png)


### text-decoration-color

`text-decoration-color` sets the color, using any color format, of the text-decoration-line. If none is set, it inherits the color of the element on which it is set.

```css
.line-through {
  text-decoration-line: line-through;
  text-decoration-color: pink;
}
```


### text-decoration-style

`text-decoration-style` sets the style of the `text-decoration-line`. It is very similar to setting a border-style, with the following options available:

* wavy
* solid 
* double
* dotted
* dashed

Note that unlike borders, padding cannot be added to create "breathing room" between the words and the underline, whereas it is possible to do this using a traditional border.


## Letter spacing

`letter-spacing: <numerical value in pixel, em or rem>;`

Letter spacing allows developers to control the amount of space in between letters using pixel, em or rem values, and can accept negative values. By default, letter spacing is dictated by the user agent, which is either the user or the browser defaults.

```css
h3.spacing {
  letter-spacing: 4px;
}
```

```css
h1,
h2,
h3,
h4,
h5,
h6 {
  letter-spacing: -1px;
}
```
![Screen shot of letter spacing of 4px and of -1px shown in an example](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-13%20at%205.50.38%20PM.png)

The `letter-spacing` property can help create subtle effects that can increase usability. In the below example, small caps are paired with the `letter-spacing` property to increase readability.

```css
.small-caps {
  letter-spacing: 2px;
  text-transform: uppercase;
}
```

![Screen shot of small caps with a letter-spacing of 2px](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-13%20at%205.50.43%20PM.png)

As with all typographic styling, all users should be kept in mind when changing letter spacing. A positive or negative value can impact the legibility of text for different users.


## Typography exercise

Download and unzip [the typography exercise by clicking here](https://hychalknotes.s3.amazonaws.com/typography-exercise--conEd.zip). 

The instructions for the exercise can be found in "typography-exercise.html" in your text editor. It's helpful to have "typography-exercise-ANSWER.html" file open in your browser to see the end goal.

