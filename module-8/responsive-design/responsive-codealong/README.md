# Making a site responsive

Let's take an exercise we've already built and turn into a responsive website!

Download the [website with wrapper](../../../exercises/STARTER--responsive-website-with-wrapper.zip?raw=true) answer key from our earlier Wrapper lesson and open it in VSCode and your browser.

Currently, our site is built to look great on desktop monitors, but now we want to make it dynamically render across multiple devices with varying screen sizes. 

## First breakpoint

Make sure to open your developer tools and toggle the rulers on so we can keep track of the width of our site as we change its width. As we scale our site down, we can start to see the way the image in our `Services` section can become too small below `1000px` width. Setting a `max-width` of `940px` will capture the average tablet in portrait mode and smaller laptop screens:

```css
@media (max-width: 940px) {

}
```

First, let's take a look at the header. The image in our header has disappeared, and the text in our `<h1>` starts to get cut off if we go much smaller. We can adjust these here to allow everything to continue to look great on smaller displays:

```css
@media (max-width: 940px) {
  header {
    background-position: center;
  }

  h1 {
    font-size: 7rem;
  }
}
```

In order to maximize the available space without shrinking our image too small, we can change the layout of our elements from a row, to a column using flexbox. We'll need to adjust the widths of our image and text to allow them to fill their new container size.

```css
@media (max-width: 940px) {
  .flexParent {
    flex-direction: column;
  }

  img {
    width: 100%;
    /* remove margin being applied on the desktop size */
    margin-right: 0;
  }

  .services p {
    width: 100%;
    margin-top: 40px;
    /* set the text align to match the About section below */
    text-align: center;
  }
}
```

Great! Everything should be looking nice at this point.

As we continue to scale down, we'll notice that our font sizes become too large again. The navigation could also be adjusted to take up less space on smaller device widths.

Let's add a second breakpoint of `500px` to capture mobile devices and adjust our font sizes:

```css 
@media (max-width: 500px) {
  h1 {
    font-size: 4rem;
  }

  h2 {
    font-size: 2.6rem;
  }

  h3 {
    font-size: 2.8rem;
  }

  li a {
    padding: 25px 10px;
    font-size: 1.8rem;  
  }
}
```
And there you go! With just two media queries, we've created a fully functional responsive website that will provide an excellent experience on all devices!

You can download the final files [here](../../../exercises/ANSWER--responsive-website-with-wrapper.zip?raw=true).
