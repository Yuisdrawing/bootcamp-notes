
# Responsive Web Design - Extended

## Orientation media query
The orientation media query can be used to specify the overall ratio of height and width of a webpage. It has two keyword options:

* portrait: the height is greater or equal to the width.
* landscape: the width is greater or equal to the height. 

*Note: This media query is not for the orientation of the device, but the orientation of the viewport*

```css
@media (orientation: landscape) {
    body {
        background: aqua;
    }
}
```

The above code would cause the background to become the colour of aqua when the viewport has a width that is greater or equal to the height.

It can be mixed and matched with other media query types by adding the `and` keyword in the media query

```css
@media (orientation: landscape) and (max-width: 1000px) {
    body {
        background: aqua;
    }
}
```
The above code would cause the background to become the colour of aqua when the viewport is 1000px or under and the viewport width is greater or equal to the height. Both of the statements must be true for the code to run.

## Media type
Media queries can accept an additional argument that declares the media type. By default the value is `screen`, and is therefore not necessary to write out normally. 

The three other specialized options are:
* `speech`: Styles that would be applied only for screen readers. Unfortunately, not all AT accept this query the same way resulting in mixed coverage. Instead of using this media type, utilize accessibility best practices throughout your code.
* `print`: Styles that are applied when a user prints styles.
* `all`: This would allow the media query styles to reach all three mediums of `speech`, `print` and `screen` 

### Print
Ever have to print a website and end up using 5 pages filled with useless ads or huge images? This is where print media queries come in handy. 

```css
@media print {
    aside,
    .large-images {
        display: none;
    }
}
```
It is common to see print-focused media queries remove content to keep the page simple for users when they are printing.

To allow the print-focused media queries to be picked up by the browser, create another stylesheet that will hold all of the unique print styles. When linking to the stylesheet, include a `media` attribute with a value of "print". 

```html
<link rel="stylesheet" href="print.css" media="print">
```

This is a great idea if you are creating a site that you think people might print out. Examples might be a recipe site, real estate listings or blog posts.

Open up [this recipe site by clicking here](https://smittenkitchen.com/2018/10/even-more-perfect-apple-pie/) and open a print preview to see how the print stylesheet is affecting the site's appearance.

* [Print stylesheet - the definitive guide](https://www.webcredible.com/blog/print-stylesheet-definitive-guide/)
