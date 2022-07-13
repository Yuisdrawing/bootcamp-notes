# CSS dimensions

CSS dimensions help us change the size and spacing of our elements, using the various measurements types covered earlier in class.


## Height and width

`height` and `width` are two CSS properties that do exactly what they say they do; affect the width and height of our elements. Both can accept all of the measurement types - pixels, em, rem, percentage and viewport units. Most elements without content have no height or width on their own.

Create an HTML file called "height-and-width.html", with four `<div>` elements like these:

```html
<div class="box1"></div>
<div class="box2"></div>
<div class="box3"></div>
<div class="box4"></div>
```

Then add a little CSS to style each box:

```css
.box1 {
  background: red;
}

.box2 {
  background: blue;
}

.box3 {
  background: green;
}

.box4 {
  background: orange;
}
```

If you open up your file in your browser, you will see nothing rendered. This is because there is no content in our `<div>`s, meaning that the backgrounds we set on them have nothing to be backgrounds for! This is a common error developers run into - most elements need content, or height/width, to be seen.

We can help our elements be seen by adding some content to each box:

```html
<div class="box1">
  <p>Box #1</p>
</div>
<div class="box2">
  <p>Box #2</p>
</div>
<div class="box3">
  <p>Box #3</p>
</div>
<div class="box4">
  <p>Box #4</p>
</div>
```

If we now render our code, we can see our `<div>`s with their content. We can make the `<div>`s larger, smaller, taller or shorter by specifying a `width` and `height`.

Try adding the following CSS using a mix of pixel and percentage values: 

```css
.box1 {
  background: red;
  width: 200px;
  height: 200px;
}

.box2 {
  background: blue;
  width: 100%;
  height: 90px;
}

.box3 {
  background: green;
  width: 2000px;
  height: 150px;
}

.box4 {
  background: orange;
  width: 500px;
  height: 100%;
}
```

It should produce the following:

![width and height example](https://hychalknotes.s3.amazonaws.com/height-width-example-1--conEd.png)

We can break down what is happening in each box: 

1. Box #1 is 200px by 200px, which is exactly what is being rendered. Pixels are a static value and will produce exactly what we have asked them to.

2. Box #2 is spanning 100% of the browser and is 90px high. Note that a width of 100% on a block element like a `<div>` looks exactly like its default width: the full width of the browser. That makes width redundant in this case, meaning we could have specified only the height to make our code more DRY.

3. Box #3 is 150px high and 2000px wide. This is much wider than most screens so a scroll to the right is needed to see the entire box. As a best practice, we want to avoid side-scroll on our websites.

4. Box #4 is 500px wide and has a height of 100%. Despite the height being set, it has not changed - more on this below.

### Max- and Min Width and Height

The max-width property defines the maximum width of an element. If the content is larger than the maximum width, it will automatically change the height of the element. If the content is smaller than the maximum width, the max-width property has no effect.

The min-width property defines the minimum width of an element. If the content is smaller than the minimum width, the minimum width will be applied. If the content is larger than the minimum width, the min-width property has no effect.

The min-height and max-height properties will define minimum and maximum height of an element in the same manner.

To test these properties, copy and paste the following code in your text editor:

```html
<section class="parentBox">
    <div class="childBox1">
        <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Exercitationem, facilis!</p>
    </div>
    <div class="childBox2">
        <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Exercitationem, facilis!</p>
    </div>
  <div class="childBox3">
        <p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Nesciunt maxime veniam quod laborum itaque esse temporibus consequatur eaque laboriosam nulla obcaecati libero dolorum quo velit neque, provident exercitationem. Suscipit saepe placeat id voluptate, necessitatibus cupiditate est neque numquam perspiciatis soluta laudantium, cumque tempora animi. Velit nobis eos enim sunt. Neque eveniet placeat, quos repellat officia, libero rerum esse illum quisquam consequuntur numquam, debitis facere voluptatum aspernatur sed voluptates enim fugit eos eaque ea nobis ad? Eligendi cum blanditiis culpa animi excepturi? Illum natus assumenda provident unde autem aliquam animi, aspernatur officia esse, veniam a molestiae saepe accusantium quibusdam explicabo ullam, necessitatibus cumque dolor totam sequi doloribus ipsa reprehenderit. Pariatur labore hic provident nemo at, aspernatur beatae dolor laborum! Totam consequatur modi nobis magnam asperiores amet quas error! Culpa quo dolore corrupti quis, corporis totam pariatur non voluptatem, voluptates exercitationem provident vel. Facere, veniam. Quasi, alias error aspernatur molestiae magnam maiores facere fugit eius itaque eos eaque repudiandae accusantium quia numquam laboriosam! Corrupti, doloribus deserunt. Accusamus, neque molestias sed impedit dolorum suscipit iste voluptas aliquam ea. Nemo ipsa dolor doloremque commodi eligendi temporibus perspiciatis explicabo modi voluptatem, recusandae ipsam voluptates sunt iure tempora dolores architecto deserunt molestiae! Voluptas nam error impedit.</p>
    </div>
</section>
```

```css
.parentBox {
  border: 6px dashed chartreuse;
  width: 400px;
  text-align: center;
}

.childBox1{
  background-color: lightblue;
}

.childBox2{
  background-color: chocolate;
  min-height: 100px;
}

.childBox3{
  background-color: yellow;
  min-height: 100px;
}
```

In the example above because the minimum height is not specified for the first box its height defaults to `auto`, meaning that it will have the height of the content. For the second box the height will be set to 100px because this is the minimum value specified and the content fits inside this value. For the last box the content is larger than the minimum height of 100px, so the box will grow to accommodate the content.

Adding `min-width: 500px;` to any of these boxes would cause it to overflow from the parent container, as its minimum width now is larger than the width of the parent.

### Width vs. height at 100%

As the example above showed, a width of 100% takes up the entire width of the browser. (this is also the default behavior of block elements like `<div>`s). However, a height of 100% does not produce the same effect; we do not see the `<div class="box4">` with its `height: 100%;` taking up the entire height of the browser.

This is a bit of a CSS gotcha - a height of 100% on an element is looking to take up 100% of its parent's height. However, that parent must have a height set explicitly. Since the parent of `<div class="box4">` is the `<body>` element, and it does not have an explicit height, both elements remain the height of their contents (ie. their default heights). 

To test this out, copy and paste the following code in your text editor:

```html
<section class="parentBox">
  <div class="childBox">
    <p>Lorem ipsum!</p>
  </div>
</section>
```

```css
.parentBox {
  border: 6px dashed chartreuse;
  width: 400px;
  text-align: center;
}

.childBox {
  background: red;
}

/* This is to remove the default margin p elements come with */
p {
  margin: 0;
}
```

![Box with green online and red content](https://hychalknotes.s3.amazonaws.com/height-width-example-2-new--conEd.png)

In the example above, the elements with the classes of `.parentBox` and `.childBox` have no heights. By default, this means the heights are dictated by their content.

If you try giving the `.childBox` element a `height` of 100%, nothing changes. This is because the `.childBox` element doesn't understand what a height of 100% means. It is looking to its parent element to interpret 100%, but its parent, `.parentBox` has no explicit height, so it is simply the height of its contents, which is to say, the height of `.childBox` (which itself is automatically the height of the paragraph inside it).

Try giving the element with the class of `.parentBox` a `height` of 200px. This results in the child element taking on a height of 200px, because that is 100% of its parent element:

![](https://hychalknotes.s3.amazonaws.com/height-width-example-3--conEd.png)

If the height of 100% is removed from the element with the class of `.childBox`, the element itself will go back to being the height of its content only:

![](https://hychalknotes.s3.amazonaws.com/height-width-example-4--conEd.png)

The largest take away is that in CSS, `height: 100%` does not represent the browser's height, it is based on an element's parent's height, and if the parent element has no set height, the element will not grow.

If we would like our elements to take up 100% of the browser's height, using the viewport height unit to set `height: 100vh` is a better choice.


## Padding and margin

Where `height` and `width` take care of an element's overall dimensions, the `padding` and `margin` properties help to control the spacing in and around elements.

`Padding` helps increase the space within an element. Padding is used to create "breathing room" inside of an element.

`Margin` helps increase the space around an element (ie. between elements). 

![two boxes displaying margin & padding](https://hychalknotes.s3.amazonaws.com/padding-margin-example-image--conEd.jpg)

Create an html document called "margin-padding.html" and copy and paste the following html:

```html
<div class="box1">
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis.</p>
</div>

<div class="box2">
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis.</p>
</div>

<div class="box3">
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit,sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis.</p>
</div>
```

Let's also add some styling:

```css
.box1 {
  background: red;
}

.box2 {
  background: blue;
}

.box3 {
  background: green;
}
```

If you open this in your browser, the `<div>` elements will take up the full width of the browser without any width being set on them, regardless of how little content they contain. This is because they are block elements and this is their default width.

![three divs, one red, one blue and one green](https://hychalknotes.s3.amazonaws.com/margin-padding-example-1--conEd.png)

Add some `margin` to `.box1`, some `padding` to `.box2`, and both `margin` and `padding` to `.box3`:

```css
.box1 {
  background: red;
  margin: 20px;
}

.box2 {
  background: blue;
  padding: 20px;
}

.box3 {
  background: green;
  padding: 20px;
  margin: 40px;
}
```

![three div elements with different amount of padding](https://hychalknotes.s3.amazonaws.com/margin-padding-example-2--conEd.png)

1. `.box1` has 20px of `margin` outside the red on all sides, but the text is still flush against the sides of the `<div>`.

2. `.box2` has 20px of `padding` inside the blue, which means there's space between the text and the sides of the `<div>`, but it's right up against the side of the browser.

3. `.box3` has both `padding `and `margin`, which creates space both around the text and between this `<div>` and the blue element above it.


### Targeting individual sides

`padding/margin-[side]: <value in pixel, em, rem, percentage or viewport unit>;`

In the examples above, we supplied a single value of 20px for `margin` and `padding`, which affected all the sides of an element. In some cases though, we only want certain sides of an element to have `padding` or `margin`.

CSS allows us to specify an individual `margin` and/or `padding` value on each side of an element:

```css
.box1 {
  /* Specific margin values */
  margin-top: 10px;
  margin-right: 5%;
  margin-bottom: 10px;
  margin-left: 25px;

  /* Same goes for padding */
  padding-top: 10px;
  padding-right: 20px;
  padding-bottom: 25px;
  padding-left: 5%;
}
```

### Padding & margin shorthand
`margin/padding: <top value> <right value> <bottom value> <left value>;`

Similar to the `background` property, padding and margin have a shorthand property that can take multiple values for padding or margin. The values are written without commas separating them, and run clockwise; top, right, bottom, left. Some like to remember it by thinking of "trouble" (TRBL - top, right, bottom, left).

Below is the shorthand version of the long-hand written example from the "Targeting different sides" section above.

```css
.box1 {
  margin: 10px 5% 10px 25px;
  padding: 10px 20px 25px 5%;
}
```

The padding/margin shorthand can also accept a two-number notation. The first number specifies the top and bottom values and the second value specifies the left and right values.

```css
.box1 {
  margin: 10px 20px; 
  /* This renders the same as
  margin: 10px 20px 10px 20px; */
}
```

Neither long or short form is considered more "advanced" - developers write whichever style works best for them.


## Auto
The `auto` keyword allows an element to automatically calculate a value based on both its surroundings and content. Width and margin can accept the `auto` keyword, but padding cannot.


### Auto and width
Block elements have a width of "auto" applied by default - this is why they extend to the width of the browser regardless of the amount of content inside of them.


### Auto and margin

#### Centering
Often we will want to center our website on a page. CSS doesn't have a center property for elements, but we can use `auto` on our left and right margins to do this.

```html
<div class="centeringDiv"><p>I'm centered!</p></div>
```

```css
.centeringDiv {
  background: rebeccapurple;
  color: white;
  font-size: 3rem;
  padding: 40px;
  /* the code below centers the element */
  width: 800px;
  margin: 0 auto;
}
```

![centered div](https://hychalknotes.s3.amazonaws.com/centering-div-margin--conED.png)

This will set the top and bottom margins to `0` (zero), and the left and right to `auto`, which centers the element within the browser. The element that you are trying to center must have a width so the margin knows what space it has to work with when given the `auto` keyword. Behind the scenes, `auto` is splitting the `margin` available on both sides of the element.


#### Left and right
We can also use `margin-left` or `margin-right` with `auto` to help us position our elements.

Using `margin-[left/right]: auto` asks the browser to automatically calculate the margin for that side of that element based off of the available total margin on the left and right.

For example, the below code

```html
<div class="box">
  <p>margin-left: auto</p>
</div>
```

```css
.box {
  padding: 20px;
  width: 150px;
  background: peru;
  margin-left: auto;
}
```
results in

![margin-left auto example](https://hychalknotes.s3.amazonaws.com/margin-left--conEd.png)

Using `margin-left: auto` brings an element all the way to the right of our browser. That's because there was no right `margin` set, meaning `auto` was able to take up all of the margin on the left.


## Exercise
Sometimes it can be tricky to know when to use height or width and when to use padding and margin. 

Open up [margin-padding-exercise--conEd.html](https://hychalknotes.s3.amazonaws.com/margin-padding-exercise--conEd.html) in your code editor and browser. You will find a set of instructions in the document.

Open up [margin-padding-exercise-ANSWER--conEd.html](https://hychalknotes.s3.amazonaws.com/margin-padding-exercise-ANSWER--conEd.html) in your browser to see what you are working towards.
