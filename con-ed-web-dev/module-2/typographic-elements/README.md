# Typographic elements

## Headings

If we want to create page or section header titles for our content, we use _heading elements_ in our HTML. All heading elements have an opening and closing tag.

They are to be written like this:
```html
<h1>I'm an h1</h1>
<h2>I'm an h2</h2>
<h3>I'm an h3</h3>
<h4>I'm an h4</h4>
<h5>I'm an h5</h5>
<h6>I'm an h6</h6>
```

By default, these render in the browser as the following:

![The HTML headers 1 through 6](https://hychalknotes.s3.amazonaws.com/typography-headers-example--conEd.png)

Note that the appearance (size, weight, etc.) can be changed with CSS.

There may only be one `<h1>` element per HTML page (using more is bad practice, and will negatively affect accessibility and SEO). The rest of the heading elements may each be used as many times as needed to delineate sectional structure (like section or chapter headings in a book). Primary section divisions should use `<h2>`, then further division can be headed with `<h3>` elements, and so on.

> **Accessibility tip**
>
> Assistive Technologies are dependent on hierarchy to fully understand the content they are interacting with. Skipping headings can cause issues. For example, using an `<h1>` and an `<h3>`, but with no `<h2>` anywhere on the page, can disrupt the flow of your page and make it less accessible.


## Paragraphs

To define a paragraph of text, use the `<p>` element. It is made up of an opening and closing tag.

```html
<p>Maecenas sed diam eget risus varius blandit sit amet non magna. Aenean lacinia bibendum nulla sed consectetur. Nullam quis risus eget urna mollis ornare vel eu leo. Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.</p>
```
This will result in the following in the browser:

<p>Maecenas sed diam eget risus varius blandit sit amet non magna. Aenean lacinia bibendum nulla sed consectetur. Nullam quis risus eget urna mollis ornare vel eu leo. Aenean eu leo quam. Pellentesque ornare sem lacinia quam venenatis vestibulum. Fusce dapibus, tellus ac cursus commodo, tortor mauris condimentum nibh, ut fermentum massa justo sit amet risus.</p>

### Lorem ipsum generators

The above text is called _Lorem ipsum_. It is placeholder text that doesn't really mean anything. Developers use Lorem ipsum to show how content will be displayed before they have the real text to work with. There are a ton of ipsum generators, which you can use for free to add a bit of pizzaz to your every day coding.

Here are a few examples:

* [Cupcake Ipsum](http://www.cupcakeipsum.com/)
* [Bob Ross Ipsum](https://www.bobrosslipsum.com/)
* [Pirate Ipsum](https://pirateipsum.me/)


## Emphasis and strong

The `<em>` and `<strong>` elements are used within other typographical elements to specify how content is to be interpreted by the user. They are made up of an opening and a closing tag and are inline elements, which means they are nested inside of other elements, like a `<p>`, and will not break the paragraph onto a new line.

```html
<p>Yesterday <em>was</em> a great day but today is <strong>even better</strong>!</p>
```

By default renders as:
> Yesterday <em>was</em> a great day but today is <strong>even better</strong>!</p>

While the `<em>` element seems to italicize content, and the `<strong>` element seems to bold content, that is simply browser default styling - we can change this with CSS if we want. We use these tags to help describe how our content is to be understood by the user, their AT and the browser for SEO purposes, not how it is presented.

`<em>` - stresses emphasis of its content

`<strong>` - conveys strong importance or seriousness

Download [typographic-markup--conEd.zip](https://hychalknotes.s3.amazonaws.com/typographic-markup--conEd.zip). Unzip the folder and drag the folder into your text editor, then markup the content accordingly using the elements above.
