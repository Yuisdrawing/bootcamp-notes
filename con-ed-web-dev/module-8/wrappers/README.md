# Wrappers
Wrappers are an essential aspect of all websites and bring together all of the concepts we have worked on so far.

A wrapper is a class that lives on an element, usually a `<div>`, that encapsulates other elements in the HTML to help:
* Center them
* Stop them from growing to a certain width while maintaining the overall look and spacing ratios of the webpage.
* Create consistent "straight lines" on our websites.

```html
<div class="wrapper">
    <section>
      <!-- ...content of website... -->
    </section>
</div>
```

## Syntax
Wrappers are usually made up of three parts:
* `max-width`: this is often around 1200px (but can be set to whichever amount you would like or has been given to you by a designer) and prevents the webpage content from growing too large. A `max-width` is especially vital as larger screens become more popular.
* `width`: a percentage width that the page will take up. The `max-width` will take effect once the percentage value becomes the same `width` as the `max-width` value. This can be any value you feel makes sense for your website or what is given to you by a designer. This is what will create a "straight line" effect to create gutters on your website until the `max-width` is reached.
* `margin`: set to "0 auto". This will center the wrapper and its contents. The top and bottom value of `margin` can be set to whichever value you would like, as long as the left and right values are left as `auto`.

```css
.wrapper {
    max-width: 1200px;
    width: 85%;
    margin: 0 auto;
}
```

Download [working-with-wrappers.html](https://hychalknotes.s3.amazonaws.com/con-ed-working-with-wrappers.html) to work off of as an example. 

If more content is added to "working-with-wrappers.html", as long as it is within the `<div>` with the class of "wrapper", the content will stay centered and the elements will keep their ratios regardless of the size of the browser. 

*Note: the name "wrapper" is an industry standard, but you could name this class whatever you want.*

## Using wrappers
A wrapper creates "clean lines" within the design. Instead of enveloping the entirety of the body, wrappers are often used inside sections like `<header>`s and `<section>`s to allow their content to meet size constraints.

A good example of wrappers in action can be found in full-bleed layouts. This is the style of design that makes it appear as if sections of the website take up the full width of the screen. 

The example below is a full-bleed design. The background expands to the edges of the browser and the content is contained and centered. The red line shows the effect that wrappers have of creating a "straight line" internally against the content.

![](https://hychalknotes.s3.amazonaws.com/fullbleed-design-wrapper--conEd.png)

Below is an example of a wrapper creating a full-bleed effect:

```html
<header>
    <div class="wrapper">
        <h1>This is the Title</h1>
    </div>
</header>

<section>
    <div class="wrapper">
        <p>this is a paragraph</p>
    </div>
</section>

<footer>
    <div class="wrapper">
        <p>This is the footer</p>
    </div>
</footer>
```

Why does the wrapper need to go on the inside of the sections and not on the sections themselves? If the wrapper class on the `<div>` in the `<footer>` is removed and instead placed directly on the `<footer>`, the wrapper would prevent the background from being "full bleed":

```html
<header>
    <div class="wrapper">
        <h1>This is the Title</h1>
    </div>
</header>

<section>
    <div class="wrapper">
        <p>this is a paragraph</p>
    </div>
</section>

<footer class="wrapper">
        <p>This is the footer</p>
</footer>
```

```css
.wrapper {
  max-width: 800px;
  width: 100%;
  margin: 0 auto;
}

header, 
section, 
footer {
    background: red;
}
```
![](https://hychalknotes.s3.amazonaws.com/full-bleed-example--conEd.png)

## Exercise

Download the [website with a wrapper file](../../exercises/STARTER--website-with-wrapper.zip?raw=true) and we'll work together adding a wrapper to a pre-exisitng website to see its benefits! You can find the completed [answer file here](../../exercises/ANSWER--website-with-wrapper.zip?raw=true).


