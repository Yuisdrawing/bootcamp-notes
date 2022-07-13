# Flexbox II: Flex children

Jump to:
* [Order](#order)
* [Align-self](#align-self)
* [Flex-basis](#flex-basis)
* [Flex-grow](#flex-grow)
* [Flex-shrink](#flex-shrink)


So far, this course has explored how flexbox relates to flex containers. For example, we know that to use flexbox, `display: flex` must be on the parent of the elements we would like to flex.

```html
<section>
  <div></div>
  <div></div>
  <div></div>
</section>
```

```css
section {
  display: flex;
}

div {
  background: orange;
  width: 120px;
  height: 120px;
}
```

We then add flexbox properties like `flex-direction` and `justify-content` to work along the two axes.

```css
section {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
}
```

These properties are great for generalized layout behavior, but don't let us control how the flex children behave individually. Fortunately, flexbox also has child-based properties, which unlike `justify-content`, `align-items` and `flex-wrap`, are specifically used on flex children.


## Order

`order: <numerical value>;`

By default, elements appear on our site in the order in which they are written in the HTML. That order can be altered by using the `order` property on individual flex children. 

`order` might be used if a user is able to interact with a group of elements and re-order them in some way, or in responsive design when certain elements need to be visually moved to appear first in a layout.

In the example below, there are three unordered lists. They appear in their default order (what is found in the HTML):

```html
<section>
  <ul class="acronyms">
    <li>CBC</li>
    <li>DRY</li>
    <li>NASA</li>
    <li>LASER</li>
  </ul>
  <ul class="drinks">
    <li>Chai</li>
    <li>Sugarcane Juice</li>
    <li>Matcha</li>
    <li>Horchata</li>
  </ul>
  <ul class="headwear">
    <li>Turban</li>
    <li>Earmuffs</li>
    <li>Niqāb</li>
    <li>Crown</li>
  </ul>
</section>
```

![](https://hychalknotes.s3.amazonaws.com/flexbox-order-01--conEd.PNG)

If we make the `section` a flex container, and give it `flex-direction: column`, everything appears the same. However, we can now use `order` on the flex children; we can move the `.acronyms` list to the middle with the following CSS:

```css
section {
  display: flex;
  flex-direction: column;
}

.acronyms {
  order: 2;
}

.drinks {
  order: 1;
}

.headwear {
  order: 3;
}
```

![](https://hychalknotes.s3.amazonaws.com/flexbox-order-02--conEd.PNG)

Elements will arrange themselves to appear in sequence from the lowest to highest `order` value.

Note that we do not have to explicitly set `order` values on all the children to use this property; by default all flex children have an `order` value of 0, so other elements with explicit `order` values will arrange themselves accordingly.

A few things to keep in mind when using `order`:
* It must go directly on the flex child/children.
* It can accept negative values.
* If two flex children are given the same `order` value, they default to the order in which they are written in the HTML.

> **Accessibility tip**
>
> The `order` property only affects the visual order of elements and does not affect the actual markup. Be careful when using this property, as AT will still read the order of elements as they appear in the markup. [Learn more about order here](https://developer.mozilla.org/en/docs/Web/CSS/order).

One common use of `order` is as a way to ensure an element will appear first, by giving it a negative `order` value:

```css
.wantToBeFirstAlwaysAndForever {
  order: -1;
}
```


## Align-self

`align-self: <keywords>;`

To gain further control over individual flex children, flexbox makes it possible for a flex child to override its parent's `align-items` value (because we all need to leave the nest at some point). Similar to `align-items`, it moves elements along the cross axis.

Align-self is useful in situations where you want all of your flex children to do one thing except for one of the items. It can be particularly helpful for forms where you want many of your elements to be left aligned but have the submit button break from that layout. 

Note that there is no `justify-self` available to move flex children individually along the main axis.

It accepts the following values:
* `flex-start`
* `flex-end`
* `stretch` - for this value to take effect, there cannot be a set height/width (depending on the cross axis).
* `center`

The below example shows `align-self` when the cross axis is vertical:

```css
section {
  display: flex;
  flex-direction: row;
}

.first {
  align-self: flex-start;
}

.second {
  align-self: flex-end;
}

.third {
  align-self: stretch;
}

.fourth {
  align-self: center;
}
```


![](https://hychalknotes.s3.amazonaws.com/align%20self.png)


By changing the `flex-direction` on the flex parent to `column`, the cross axis becomes horizontal. The below shows how the flex children would be laid out.

![](https://hychalknotes.s3.amazonaws.com/alignselfcolumn.png)


## Flex-basis
`Flex-basis: <dimension value in px, percentage, em, or rem or auto keyword>;`

Flex children can be given an initial width/height (depending on whether the `flex-direction` is column or row) using `flex-basis`. However, unlike width/height, the dimensions specified by `flex-basis` are not guaranteed; `flex-basis` is only an initial value, and flexbox can shrink or grow that value based on the flex parent's size. We saw this behavior previously, when we learned about [multi-line content and `flex-wrap`](https://github.com/HackerYou/con-ed-web-dev/tree/master/module-6/flex-one#multi-line-content).

`flex-basis` can accept any measurement values (pixels, percentages, etc.) or the `auto` keyword.

Let's look at an example using this HTML:

```html
<section>
  <div class="first">1</div>
  <div class="second">2</div>
  <div class="third">3</div>
  <div class="fourth">4</div>
</section>
```

We can set the following CSS (note that the `flex-direction` is `row`, and the flex container has a `width` of 1000px):

```css
section {
  display: flex;
  flex-direction: row;
  border: 1px solid black;
  width: 1000px;
}

div {
  background: green;
  border: 2px solid black;
  color: white;
  font-size: 40px;
  text-align: center;
}
```

![](https://hychalknotes.s3.amazonaws.com/flex-basis-01--conEd.PNG)

As we expect, each flex child is as wide as its contents. Now, let's give the flex children a `flex-basis: 200px` property:

```css
div {
  background: green;
  border: 2px solid black;
  color: white;
  font-size: 40px;
  text-align: center;
  flex-basis: 200px; /* This is the property we added! */
}
```

![](https://hychalknotes.s3.amazonaws.com/flex-basis-02--conEd.PNG)

Here we can see `flex-basis` behaving very much like `width`. All of the `div` elements are able to fit into the flex container with extra space left over, because  
`200px * 4 = 800px`  
Meaning there is 200px worth of extra space in the container.

If we shrink the flex parent to `600px`, making it 200px smaller than the total combined `flex-basis` values of the four children, then the child elements will resize themselves to fit in the container:

```css
section {
  display: flex;
  flex-direction: row;
  border: 1px solid black;
  width: 600px; /* This is the property we changed! */
}
```

![](https://hychalknotes.s3.amazonaws.com/flex-basis-03--conEd.PNG)

Conveniently, when we update the `flex-direction` property to `column` our `flex-basis` will now dictate the height. Therefore, `flex-basis` controls both width and height based on the `flex-direction`.


### Flex-basis and `auto`

The keyword `auto` can also be passed into `flex-basis`, which means the browser will look to the width or height of the flex children to determine how to render `flex-basis`, and if none are found then it is based on the size of their content. `auto` is the default value of `flex-basis`.

```css
div {
  background: green;
  border: 2px solid black;
  color: white;
  font-size: 40px;
  text-align: center;
  flex-basis: auto; /* This is the property we changed! */
}
```

![](https://hychalknotes.s3.amazonaws.com/flex-basis-04--conEd.PNG)


## Flex-shrink

`flex-shrink: <unitless positive numerical value>;`

As we saw in the example above, by default flex children can shrink uniformly to be contained in the width of their flex parent. This behavior can be changed by using `flex-shrink` on flex children. This value dictates how much a flex child will shrink relative to the other flex children.

By default, all flex children are assigned a `flex-shrink` value of `1`. This represents the relative amount by which they will shrink with respect to one another; all flex children having the same value (`1`) means they all shrink uniformly (ie. at the same rate).

However, look what happens in our example if we give all the `<div>` elements `flex-basis: 300px;`, and we also give the `<div>` with a class of `.second` the property `flex-shrink: 2;`:

```css
div {
  background: green;
  border: 2px solid black;
  color: white;
  font-size: 40px;
  text-align: center;
  flex-basis: 300px; /* This is the property we changed! */
}

.second {
  flex-shrink: 2; /* This is the property we added! */
}
```

![](https://hychalknotes.s3.amazonaws.com/flex-shrink-01--conEd.PNG)

The `.second` element shrinks twice as fast as the others. That is to say, for every 1 pixel one of the other elements loses, `.second` loses 2 pixels. `flex-shrink` essentially determines the ratio of rates at which the various elements shrink - in the case of our four child elements, that ratio is now 1:2:1:1.

To stop an element from shrinking, the value of "0" can be passed to `flex-shrink`:

```css
.third {
  flex-shrink: 0; /* This is the property we added! */
}
```

![](https://hychalknotes.s3.amazonaws.com/flex-shrink-02--conEd.PNG)

The `<div>` with a class of `.third` now cannot shrink. Its width is now the initial value specified by its `flex-basis` (300px). Our other elements are even smaller than before, especially `.second`, because there is even less space left to share between them.


## Flex-grow

`flex-grow: <unitless positive numerical value>;`

`flex-grow` allows flex children to expand into any remaining empty space in a flex container. Similar to its counterpart, `flex-shrink`, the `flex-grow` property determines the relative rates at which flex children grow.

The reason we have not seen this behavior up to now is that the default `flex-grow` value is `0`, meaning that by default, elements will not grow. 

Let's return to our example. Give the `<section>` a width of `1000px` again, and remove all the `flex-shrink` values. Then, set a `flex-basis` of `100px` on the `<div>` elements:

```css
section {
  display: flex;
  flex-direction: row;
  border: 1px solid black;
  width: 1000px; /* This is a property we changed! */
}

div {
  background: green;
  border: 2px solid black;
  color: white;
  font-size: 40px;
  text-align: center;
  flex-basis: 100px; /* This is a property we changed! */
}


/* Delete these styles: */

/* .second {
  flex-shrink: 2;
}

.third {
  flex-shrink: 0;
} */
```

![](https://hychalknotes.s3.amazonaws.com/flex-grow-01--conEd.PNG)


This is what we saw before. All the child elements are sized to their default width, as set by `flex-basis`. Now give all of the children a `flex-grow` value of `1`:

```css
div {
  background: green;
  border: 2px solid black;
  color: white;
  font-size: 40px;
  text-align: center;
  flex-basis: 100px;
  flex-grow: 1; /* This is the property we added! */
}
```

![](https://hychalknotes.s3.amazonaws.com/flex-grow-02--conEd.PNG)

The flex children all expand uniformly to fill the extra space! If we want them to grow at different rates, we can give one or more children different `flex-grow` values. For example, try applying a `flex-grow` of `4` to the element with the class of `.first`. This will cause that element to take up four times as much of the remaining space as the other elements:

```css
.first {
  flex-grow: 4; /* This is the property we added! */
}
```

![](https://hychalknotes.s3.amazonaws.com/flex-grow-03--conEd.PNG)

Note that the `.first` element isn't now four times larger than the others, but rather has taken up four times as much of the previously empty space. The others all grow at equal rates to one-another.


## Flex shorthand

`flex: <flex-grow> <flex-shrink> <flex-basis>;`

Flexbox offers a shorthand that combines `flex-shrink`, `flex-grow`, and `flex-basis`. It's a useful way to keep track of all properties on one line and can help make the relationship between the three properties more clear.

By default, the flex property is set to a `flex-grow` of 0, a `flex-shrink` value of 1, and a `flex-basis` of auto.

```css
div {
  flex: 0 1 auto;
}
```

Play around with [this navigation by clicking here](https://hychalknotes.s3.amazonaws.com/flex-shrink-grow-nav--conEd.html) to see the flex shorthand in action.

## Width/height vs. flex-basis
It's common to see some confusion between `flex-basis` and width/height on flex children. Here are some things to keep in mind:

* `flex-basis` will be respected before width/height, depending on the main axis. If for some reason `flex-basis` isn't respected (cross-browser issue, typos, etc.), the flex child will look to width or height.
* When no `flex-basis` is set, it defaults to `auto`. This means that it can accept `flex-grow` or `flex-shrink` and will act accordingly.

Does this mean width or height are interchangeable with flex-basis? No!

### Max & min-width
In addition to `width`, elements can also accept `min-width` and `max-width`. When a `min-width` is set on an element, the element cannot get any smaller than the specified size, and when a `max-width` is set on an element, it cannot get any bigger. These are useful for different window or screen sizes, to make sure things do not grow extremely large or shrink extremely small.

```css
section {
  max-width: 800px;
  width: 80%;
}
```

In the above example, the `<section>` element will take up 80% of the width, until it reaches its maximum width of 800px, and will stop growing.

A `min-width` can also be set to ensure an element cannot be smaller than a certain size.


```css
section {
  min-width: 200px;
  width: 60%;
}
```

In the above example, the `<section>` element will not be smaller than 200px, regardless of how small the browser becomes.

Note that `max-width` overrides `width` if `max-width` is larger than the `width` value, and `min-width` overrides both `max-width` and `width` if their values are smaller than the `min-width`.


### Max and min-height

The same logic applies to `max-height` and `min-height` as to `max-width` and `min-width`. As a rule of thumb, absolute heights should not be set on elements because it can cause the content to spill out of the container. Instead, the content and padding should dictate the height of elements.

When needed, a minimum or maximum value can help heights be dynamic. `min-height` is more common to use than `max-height` because as browsers get narrower, content becomes squished and lengthens naturally. A `min-height` can help prevent elements from becoming so short that their content breaks out, while allowing them to be taller where possible.

```css
section {
  min-height: 20vh;
}
```

The above example allows the `<section>` to have an initial value of 20vh, but can get taller as the browser gets narrower.

While `max-height`, `min-height`, `max-width`, and `min-width` are extremely useful, there are known issues on Internet Explorer when working with flexbox properties that can lead to layout issues. For example, Internet Explorer 11 cannot `align-items` properly if `min-height` is used.

`max-width` and `min-width` also prevent `flex-basis` from growing and shrinking with `flex-shrink` and `flex-grow`.

The solution is to be aware of the issues that can be caused by using the `min` and `max` values when working with flexbox, and if `flex-basis` is being used, it should be used consistently, without the use of the `min` and `max` values to avoid any unexpected issues.


## Example usage of flex properties

In the below example, we are trying to create a card layout with some text at the top of the card and a button that 'sticks' to the bottom regardless of the amount of content and the height of the container:

```html
<div class="container">
  <div class="card">
    <p>Lorem ipsum dolor sit.</p>
    <button>Ooh, a button</button>
  </div>
  <div class="card">
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Dignissimos, laboriosam, pariatur animi sapiente earum autem fugit ducimus incidunt dolorem a, consectetur sit!</p>
    <button>Ooh, a button</button>
  </div>
  <div class="card">
    <p>Lorem ipsum dolor sit amet.</p>
    <button>Ooh, a button</button>
  </div>
  <div class="card">
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
    <button>Ooh, a button</button>
  </div>
</div>
```
```css
.container {
  display: flex;
}

.card {
  margin: 8px;
  padding: 5px;
  border: 2px solid #77562b;
  /* The card is a flex child AND a flex parent! */
  /* Flex CHILD properties: */
  flex: 0 0 150px;
  /* Flex PARENT properties: */
  display: flex;
  flex-direction: column;
}

.card p {
  margin: 0;
  padding: 5px;
  background: #6d976d;
  /* Flex grow makes the p expand into any available space: */
  flex-grow: 1;
}
```

Using flexbox, the cards are laid out in a row, but the children of the individual cards themselves are being laid out using `flex-direction: column`. By giving the paragraph a `flex-grow` of 1, it will expand to take up the remaining space in the parent container, which will push the button to the bottom of the container.

![](https://hychalknotes.s3.amazonaws.com/flexgrowcard.png)


`flex-shrink` and `flex-grow` can be very useful when working with a navigation whose items do not need to all take up equal space. In the example below, one of the menu items is an icon that does not need as much room as its counterparts. By applying a `flex-grow` of 0 to the smaller item, and `flex-grow` of 1 to the larger items, the extra space will be divided equally among the larger menu items.

```css
nav {
  display: flex;
}

.nav-item {
  flex-grow: 1;
}

.home {
  flex-grow: 0;
}
```

![](https://hychalknotes.s3.amazonaws.com/flexgrowflexshrinkexmple.png)

Further to this, if there is a menu item that is being highlighted in a layout and therefore should take up more width than the rest of the items, you can apply a `flex-basis`, along `flex-shrink` of `0` to those items. As more menu items potentially get added to the nav, the highlighted menu item will continue to respect its  `flex-basis` and not shrink in size.

```css
nav {
  display: flex;
}

.sale-items {
  flex-basis: 50%;
  flex-shrink: 0;
}
```
![](https://hychalknotes.s3.amazonaws.com/flexbasisflexshrinkexample.png)

## Exercise
Open up [flex-2-exercises--conEd.zip](https://hychalknotes.s3.amazonaws.com/flex-2-exercises--conEd.zip) to practice a few of the flex properties we just learned.

Keep the answer key open in a tab for reference, resize the answer key to see spacing behaviour as the width of the screen changes.

## Resources
* [Flex properties available along both axes](../../additional-resources/flexbox-axes)
* [The difference between width & flex-basis](https://gedd.ski/post/the-difference-between-width-and-flex-basis/)
* [Flex order](https://css-tricks.com/almanac/properties/o/order/)
* [Flex-basis](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-basis)
* [Wes Bos's What the Flexbox](https://flexbox.io/)
* [Play around with Flexbox: Flexplorer](https://bennettfeely.com/flexplorer/)
