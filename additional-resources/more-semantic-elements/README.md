# More Semantic Elements

## Abbr
`<abbr>`: This tag helps to define an abbreviation or an acronym, like "HTML".

```html
<p>We use <abbr title="Hypertext Markup Language">HTML</abbr> to define the content of our websites.</p>
```

`<abbr>` and the title attribute together form a co-dependent relationship - whatever value you give to the title attribute, a screen reader will interpret as the full meaning of the abbreviated word. When a user hovers over the abbreviated word, the value of the title attribute will appear. 

Try copying and pasting the below into your text editor and bringing it up in your browser:

```html
Today, we're learning about different ways to use <abbr title="Cascading Style Sheet">CSS</abbr>.
```

The abbreviation element comes with default styling when paired with the `title` attribute but this styling can be modified using CSS. For accessibility purposes, it's best to avoid changing the default styling too much as users have come to associate certain styling and behaviours.

## Time
`<time>`: Used to define human-readbale date/time.

```html
<p>Our office will be open tomorrow morning at <time>10:00</time>.</p>
```

## Figure, img & figcaption
`<figure>`: Specifies an image, code chunk, illustration, or a diagram. Figures are also self-containing. Ideally, figures can be moved to a different part of the page without affecting the flow of content like a diagram in a textbook. Figures are often misused.

`<img>`: Defines an image that makes up a vital part of the page's meaning. Images can go anywhere on a page and not just nested within `<figure> `elements.

```html
<figure>
  <img src="chartAboutWeather.jpg" alt="A chart showing the weather patterns over the past 10 years in Canada.">
  <figcaption>Weather in Canada, 2000-2010.</figcaption> 
</figure>
```

`<figcaption>`: Defines a caption for the figure item. There should only be one figcaption nested inside of a figure (but not all figures need a figcaption). Figcaption can be included before or after the contained element.

```html
<figure>
  <figcaption>My cool headshot</figcaption>
  <img src="headshot.jpg" alt="Photo of the author looking straight towards the camera and smiling.">
</figure>
```