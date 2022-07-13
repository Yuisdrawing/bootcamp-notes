# Floats
Before Flexbox was created, the developers of HTML and CSS did not plan for our web pages to be dynamically laid out like we see in modern layouts. They envisioned the internet to be a simple layout, with block elements laying out as they were always meant to: taking up the full width of the browser and sitting in their natural staking order.

```html
<img src="http://unsplash.it/200/200" alt="Unsplash placeholder image">
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nobis qui veritatis saepe cum corrupti ex quibusdam, magni quas autem, deserunt sint alias. At et, sed veniam, beatae porro animi qui.</p>
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nobis qui veritatis saepe cum corrupti ex quibusdam, magni quas autem, deserunt sint alias. At et, sed veniam, beatae porro animi qui. Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nobis qui veritatis saepe cum corrupti ex quibusdam, magni quas autem, deserunt sint alias. At et, sed veniam, beatae porro animi qui.</p>
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nobis qui veritatis saepe cum corrupti ex quibusdam, magni quas autem, deserunt sint alias. At et, sed veniam, beatae porro animi qui. Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nobis qui veritatis saepe cum corrupti ex quibusdam, magni quas autem, deserunt sint alias. At et, sed veniam, beatae porro animi qui.</p>
<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nobis qui veritatis saepe cum corrupti ex quibusdam, magni quas autem, deserunt sint alias. At et, sed veniam, beatae porro animi qui. Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nobis qui veritatis saepe cum corrupti ex quibusdam, magni quas autem, deserunt sint alias. At et, sed veniam, beatae porro animi qui.</p>
```

```css
body {
  text-align: center;
}

p {
  padding: 8px 0;
}
```

![](https://hychalknotes.s3.amazonaws.com/floats-example1--conEd.png)

The only accommodation to add more dynamic layouts was to allow images to have content wrap around them. To create the wrapping effect, developers used the CSS `float` property.

```css
/* .. */
img {
  float: left;
  margin-right: 12px;
}
```

![](https://hychalknotes.s3.amazonaws.com/floats-example2--conEd.png)

The `float` property is used to define whether or not the preceding elements will wrap around it, given that they have the space. The `float` property implies that a layout is made out of `block` elements and interprets all elements, whether they are inline or not, as block elements.

In the example above, the `<p>` elements move up next to the `<img>` because there is space available next to the `<img>` for the `<p>` elements to fill.

While Flexbox is a modern option, floats are still used and can be found in legacy projects and are sometimes used when developers feel that their target demographic might be working with a browser version that will struggle to support Flexbox.

## Syntax 
Floats go directly on the element that you would like other elements to wrap around.

`float: <right or left or none>;`

The `float` property accepts three values. `right` and `left` specify in what direction the element will float in and `none` is used to remove a floating behaviour off of an element. 

Try using floats for their traditional purpose of laying out images with text by downloading and opening up [image-float--conEd.html by clicking here](https://hychalknotes.s3.amazonaws.com/image-float--conEd.html) and following the instructions inside of the HTML file.

Check out the [answer key by clicking here](https://hychalknotes.s3.amazonaws.com/image-float-ANSWER--conEd.html).

## Layouts using floats
As developers continued to push the boundaries of CSS and HTML, the `float` property started being used to create modern layouts beyond what the property was originally intended for - wrapping images. While Flexbox is widely used today, it's important to understand how elements behave differently when using Flexbox and floats.

Download and open up [playing-with-floats--conEd.html](https://hychalknotes.s3.amazonaws.com/playing-with-floats--conEd.html) to follow along with the below.

Try flexing the `<p>` elements by giving the `<main>` element a  `display` value of `flex`. 

```css
main {
  display: flex;
}
```

This results in a behaviour that is familiar with Flexbox: the `<p>` elements will flex next to each other, each taking up about 50% of the width because they share equal amounts of content. This is a default behaviour of Flexbox because it is "helping" distribute the width along the flex children to ensure they fit within the flex parent.

Now remove the `display: flex` from the `<main>` and try floating the the `<p>` elements to the left.

```css
p {
  /* .. */
  float: left;
}
```

Why aren't the `<p>` elements moving next to each other? This is a key difference between Flexbox and floats: floats will not try to fit next to each other and will only float next to each other if there is available space. In this case, there is no available space.

To fix this issue, give the `<p>` elements a width to create space for them to float into:

```css
p {
  /* ... */
  width: 50%;
}
```

By giving the `<p>` elements a width of 50%, they will take up half of the available row. That is because a total row is 100%. If they were given more than 50%, they would not be able to successfully float next to each other.

What if margin of 10px is added on the left and right the `<p>` elements?

```css
p {
  /* ... */
  margin: 0 10px;
}
```
The `<p>` elements will no longer will able to float next to each other because according to the Box Model, the margin sits outside of the element. 

![Box-model](https://hychalknotes.s3.amazonaws.com/box-model--conEd.jpg)

This means that the `<p>` elements are now taking up 50% plus 10px of margin on the right and left side.

### Calc & floats
`Calc` is especially useful when working with floats and can help align items next to each other easily.

If we take the above problem of the `<p>` elements not being able to fit next to each other, we know that the `<p>` elements are taking up the space:

`width: 50% + 10px (right margin)+ 10px (left margin)`

OR 

`width: 50% + 20px (margins from both sides combined)`

This is a perfect job for `calc`:

```css
p {
  /* ... */
  width: calc(50% - 10px - 10px);
  /* This could have also been written as 
  width: calc(50% - 20px); */
}
```
## Code along: modern layout using floats
A standard Web page layout is to have a header and a footer, and in between those, a content area with a sidebar next to it.

Open up [layout-floats-twocolumn.zip](https://hychalknotes.s3.amazonaws.com/layout_floats--twocolumn.zip) to follow along.

In our example, we have our four main elements. Header, Section, Aside and Footer. As well, we'll have a surrounding element with a class of wrapper that contains our elements and centres them.

```html
    <div class="wrapper">
        <header>
            <h1>- Vacay -</h1>
        </header>

        <section>
            <h2>We got Vacations</h2>
            <p>We got, such vacations. Don't even worry about it. Are you worried because you should not be.</p>
        </section>

        <aside>
            <ul>
                <li>
                    <a href="#">Get Relaxing Vacays</a>
                </li>
                <li>
                    <a href="#">Get Exciting Vacays</a>
                </li>
                <li>
                    <a href="#">Get Adventurous Vacays</a>
                </li>
                <li>
                    <a href="#">Get Educational Vacays</a>
                </li>
            </ul>
        </aside>

        <footer>
            <p>Vacay - Copyright 2018</p>
        </footer>
    </div>
```

By default, our elements are 100% wide, so there is no need to apply any widths or floats to our header or footer. However, the `<section>` and `<aside>` need to be floated to sit next to each other. Keeping in mind that the two elements' widths must equal to 100% to be able to sit next to each other.

```css
section {
	/*add code here*/
    float: left;
    width: 60%;
}

aside {
	/*add code here*/
   	float: left;
    width: 40%;
}
```

With both the `<aside>` and `<section>` now side by side two issues have come up:
* The `<footer>` has jumped up
* The element with the class of "wrapper" has collapsed and is not longer wrapping around the elements it was before (the border has moved up!).

![width move](https://hychalknotes.s3.amazonaws.com/two-column-shot1.png)

These are unique situations that only occur when working with the `float` property. These are called "element collapse" because elements that have not been floated have "collapsed" by losing their original footprint and stacking order.

In this example:
* The `<footer>` has moved up because it doesn't recognize the space taken up the floated elements.
* The element with the class of "wrapper" no longer recognized the floated content, leading the the border which was enveloping all of the content to collapse and wrap the content that is not floated. In this case, the footer.

### Element collapse 
Floats were designed to float images within blocks of text that were meant to wrap around and continue down the page. In the case of this layout, there is no continued content to size accordingly, so the wrapper sizes to the next element that isn't floated. In this case, the footer.

There are two element collapse solutions to use when working with floats, one addresses the parent/wrapper collapse, the other addresses the collapse of subsequent sibling elements you do not wish to float.

### Clearfix
There is an industry standard set of CSS properties known as `clearfix` which solves the parent element collapse issue for us. It is included in the `setup` snippet.

```css
.clearfix:after {
  visibility: hidden;
  display: block;
  font-size: 0;
  content: " ";
  clear: both;
  height: 0;
}
```

The code above is using some advanced properties, but it is extremely effective in fixing the collapse problem in a non-invasive way.

To stop parent elements of floated items from collapsing, apply `clearfix` to the parent element.

```html
<section>
	<div class="wrapper clearfix">
		<div class="half">
			<p>The div that contains this paragraph is floated left</p>
		</div>
		<div class="half">
			<p>The div that contains this paragraph is also floated left</p>
		</div>
	</div>
</section>
```
In the code above, `clearfix` is placed on the parent `<div>` with the class of "wrapper" on it.

![width move](https://hychalknotes.s3.amazonaws.com/two-column-shot2.png)

### Clear: both
To address the collapse of sibling elements after the floated elements we can use the CSS property of `clear` with the value of "both". This prevents sibling elements of floated elements from floating up. It essentially stops the floating layout and returns the sibling element to their own block element state.

```css
footer {
  clear: both;
}
```

Below is our finished product.
![width move](https://hychalknotes.s3.amazonaws.com/two-column-shot3.png)
