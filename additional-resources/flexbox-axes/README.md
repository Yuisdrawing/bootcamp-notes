# Flexbox extended

## Flexbox axes

Flexbox works across two axes: the main and the cross axes. The axes are defined by the `flex-direction` value set on the flex parent. For example, `flex-direction: row;` sets the main axis to the horizontal axis, and the cross axis to the vertical axis.

### Main Axis Alignment
* `justify-content`: Distributes the space along the main axis as a group. This property is used on a flex parent.

### Cross Axis Alignment
* `align-items`: Dictates how flex children will move as a group on the cross axis. This property is used on a flex parent.
* `align-self`: Overrides the align-items value set on a flex parent. This property is used on a flex child.
* `align-content`: Distributes the space between multiple lines of flexed items. This property is used on a flex parent.

## Flexbox & size manipulation
Flexbox likes to "help" developers a lot. By default, flex children will be resized by Flexbox to fit the dimensions of their flex parent based off the size of the content in each flex child.

For example, in the below code, there are two `<p>` elements with different content amounts and no set width. By default, they are block elements which mean they will take up the entire block of space on the browser.

*Note: The assumption is that there is always box-sizing: border-box set on the root / that the setup snippet has been used*

```css
div {
  max-width: 1000px;
  border: 5px solid red;
}

p {
  border: 2px solid black;
  padding: 10px;
  font-size: 20px;
  margin: 0;
}
```

```html
<div>
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nobis qui veritatis saepe cum corrupti ex quibusdam, magni quas autem, deserunt sint alias. At et, sed veniam, beatae porro animi qui. Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nobis qui veritatis saepe cum corrupti ex quibusdam, magni quas autem, deserunt sint alias. At et, sed veniam, beatae porro animi qui.</p>
  <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Nobis qui veritatis saepe.</p>
</div>
```

![](https://hychalknotes.s3.amazonaws.com/advanced-layouts-example1--conEd.png)

If the two `<p>` elements with different content amounts are flexed next to each other, Flexbox will distribute the space in a way that allows them to be side-by-side horizontally.

```css
div {
  display: flex;
  /* default value of */
  /* flex-direction: row */
}
```

![](https://hychalknotes.s3.amazonaws.com/advanced-layouts-example2--conEd.png)

This is Flexbox "helping" us by assuming how we want our elements layed out. It's rare that we want the element with larger content to always take up more space by default.

By giving the `<p>` elements a width, we can predictably allow our elements to take up a certain amount of space that is not dictated by Flexbox.

```css
p {
  width: 500px;
}
```
![](https://hychalknotes.s3.amazonaws.com/advanced-layouts-example3--conEd.png)

In the example above, the `<p>` elements now take up 500px each, or half of the total available space of the parent, which is 1000px:

`500px + 500px = 1000px`

This works out perfectly, but what happens if each `<p>` element is given a width of 600px, for a total value larger than its container?

`600px + 600px = 1200px`

```css
p {
  /* ... */
  width: 600px;
}
```

Because the `<p>` elements are flexed, there will be no difference to what is rendered.

![](https://hychalknotes.s3.amazonaws.com/advanced-layouts-example3--conEd.png)

That is because Flexbox is "helping" by forcing the flex children to fit within their parent element and will not allow any children to spill over to another line.

Using `flex-wrap: wrap` on the parent will allow the flex children to flow over to the next line, taking up the true value of 600px each.

![](https://hychalknotes.s3.amazonaws.com/advanced-layouts-example4--conEd.png)

It is important to be aware of this effect. Flexbox is extremely useful but it has its quirks. These were originally meant to make life easier, but they can sometimes complicate things instead. 

### The 100% rule
As seen in the above example, all layouts rely on the "100% rule". The "100% rule" dictates that all horizontal layouts cannot exceed 100% of their container.

Given the example covered above, when the `<p>` elements were given 500px width each, they totaled the amount of their container, making it possible for them to sit side-by-side equally. 

This is also why the `<p>` elements could no longer successfully sit side-by-side when given a width of 600px in a total container width of 1000px; 
