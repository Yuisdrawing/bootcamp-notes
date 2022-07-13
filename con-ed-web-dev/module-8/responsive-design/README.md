# Responsive design
Responsive design, also known as RWD (responsive web design), is the principle that all web experiences should aim to cater to all devices, from mobile phones to large desktop screens. The experience across devices should be the same: a website should be easy to use and maintain its visual look and feel.

By shrinking, growing, hiding and re-organizing our content using HTML and CSS, we can ensure all users have the same experience across devices. In this course, we have been slowly building towards full responsiveness by adding percentage widths, `max-width` and `min-width` properties, as well as `flex-grow` and `flex-shrink`. They are excellent building blocks towards making your website responsive - similar to creating accessible websites, responsive design is something developers should be considering from the very beginning of development instead of later on.

As a general rule, when working with RWD, no information should be left out or removed to fit smaller devices. Content must adapt to fit the device.

![](https://hychalknotes.s3.amazonaws.com/cantina-responsive-example.png)

All of this is done using the same website, instead of making a secondary website for mobile use only, and users should be able to experience the responsive design changes as the browser shrinks and grows.

## History of RWD
Before certain features were introduced to CSS and HTML, web developers would create what we call "m dot" (mobile dot) sites to respond to the demand of users accessing websites through tablet and mobile devices. IMDB still has one that is active at [https://m.imdb.com/](https://m.imdb.com/), which means they are running two independent sites, one for desktop and one for mobile, and update them all accordingly when they have new content. The result is not especially resource friendly or efficient for developers.

Modern RWD introduces the concept of a single codebase and one website that reacts to its viewport size. With this, we only have to maintain and update content for a single website versus two (or more!).

![](https://hychalknotes.s3.amazonaws.com/aids-gov-example.png)

Developers are sometimes tasked with coming up with a tablet and mobile design on their own, and sometimes they are provided by the designers on their team.

## The viewport
As we have seen with viewport units, the viewport is the total viewable area of the screen. The viewport changes depending on the device - for example, tablets have a larger viewport than mobile devices.

Along with semantic elements, HTML5 introduced the `viewport` `<meta>` tag:

`<meta name="viewport" content="width=device-width, initial-scale=1.0">`

This tag is included in our VS Code setup (`! + Tab`) and allows for our sites to be responsive by allowing the browser to get information about how to scale the content and to what dimensions:

* `width=device-width`: sets the width of the page to follow the screen width of the device. This will vary depending on the device. This could be set to a value of, for example, 320px, and it will render the site as if the website browser was 320px wide. But there are hundreds of devices out there all with different sizes, so setting specific values can become a problem.
* `initial-scale=1.0`: this is responsible for the initial zoom level when the page is first loaded by the browser.

Neither of these values should be altered unless you have explicit understanding of why you are changing them.

The viewport meta tag won't automatically re-style your site on smaller screen sizes. It will, however, allow for the responsive features that we will be covering in this lesson to be effective. Without the viewport meta tag, a website cannot be responsive, making this tag vital to every website's `<head>`.

## Media queries 
Media queries are blocks of code in your CSS that will run by injecting or removing certain styles, depending on the rules you've set. Media queries are one of the reasons layouts can shift at certain browser sizes. They can add, remove or alter current styles.

### Syntax
Media queries are made up of a media at-rule and a set of conditions that, if true, will run the CSS rule inside of their brackets.

```css
@media (max-width: 500px) {
  p {
    color: red;
  }
}
```

In the above example, when the screen width is equal to or below 500px, all `<p>` elements will become the color red. The 500px above is where there will be a change in the appearance of the website and is called a *break point*. 

Notice in the above that one CSS rule is placed inside of what looks like another CSS rule. Media queries can accept multiple CSS rules that affect different parts of a website. Media queries are usually found at the bottom of a stylesheet.

```css
@media (max-width: 940px) {
  body {
    background: red;
  }
  
  h2 {
    font-size: 20px;
  }
}
```

In the above media query, when the browser is 940px or smaller, the `<body>` will have a `background` of red and the `<h2>` elements will have a `font-size` of 20px. In this example, 940px is the breakpoint. 

An easy way to visualize breakpoints is to set either a background color or a border on the body to make it obvious which breakpoint you are crossing.

Open [responsive-backgrounds--conEd.html](https://hychalknotes.s3.amazonaws.com/responsive-backgrounds--conEd.html) in your editor and browser, and take a look through the code.

*Note: Be mindful of the selectors being used and the order of media queries, as the cascade and specificity will impact if/how the media query will take effect. Try switching the order of the media queries in "responsive-backgrounds--conEd.html" to see what happens.*

## Dev Tools Responsive Mode
It's difficult to know what size our browser windows are just by looking at them. Luckily, Dev Tools come with a responsive mode that indicates the size of the browser window and makes it possible to view websites as they appear on other devices, like mobile phones and tablets.

If you open up Dev Tools, there is a mobile phone and tablet icon in the top right corner.

![](https://hychalknotes.s3.amazonaws.com/dev-tools-responsive--conEd.png)

You can now review the size of your browser as well as choose from other devices to view your website in.

![](https://hychalknotes.s3.amazonaws.com/dev-tools-reponsive-2--conEd.png)

## Media query types
Media queries can be customized to meet a range of specifications.

### Width
Width-based media queries are the most common type of media query. That is because users have an expectation for the content of the website to fit and adjust as they move their screen in and out width-wise. 

```css
@media (max-width: 600px) {
  section {
    flex-direction: column;
  }
}
```

The above media query is targeting all the sections and giving them the `flex-direction` of "column" when the screen is 600px wide or less. This creates a cascading-effect for the media query because it will carry the styles to every viewport width smaller than 600px, saving developers from having to rewrite it later on.

Media queries can also accept `min-width`.

```css
@media (min-width: 330px) {
  .special {
    width: 50%;
  }
}
```

The above media query targets all elements with the class of "special" and makes them a `width` of 50% on a viewport that is 330px or larger. Similar to using a `max-width`, this method is beneficial for passing one style and it applying to multiple viewport widths. 

As a rule of thumb it is best to stick with either using `max-width` OR `min-width` when using media queries. It is easy to lose track of media queries:

```css
@media (max-width: 830px) {
  h1 {
    color: blue;
  }
}

@media (min-width: 700px) {
  h1 {
    color: red;
  }
}

@media (max-width: 1000px) {
  h1 {
    color: purple;
  }
}

```

The above can get confusing and hard to keep track of. The below example, on the other hand, is more manageable and easier to debug.

```css
@media (max-width: 1000px) {
  h1 {
    color: purple;
  }
}

@media (max-width: 830px) {
  h1 {
    color: blue;
  }
}

@media (max-width: 700px) {
  h1 {
    color: red;
  }
}

```

In very specific cases, both a `min-width` and a `max-width` can be used to apply specific styles to a range of viewport widths:

```css
@media (min-width: 768px) and (max-width: 940px) { 
  section {
    justify-content: space-between;
  }
}
```

The above piece of code will only be applied when the width of the viewport is greater than or equal to 768px and less than or equal to 940px. Using this method should be used very rarely as utilizing the power of CSS in our media queries (allowing one piece of code to affect many viewport widths) is ideal.

### Height
Unlike width-based media queries, height queries are less common because users do not have the same expectations for items to resize vertically. Users expect to scroll vertically on a website to see more content.

```css
@media (max-height: 800px) {
  header {
    height: 80vh;
  }
}
```

The above changes the height of the `<header>` to 80vh when the viewport is 800px tall or smaller.

`min-height` and `max-height` can also be paired together the same way that `min-width` and `max-height` can be, but is extremely rare.

Heights in general are tricky in responsive design:
* A phone's browser bar takes up height, and there's generally a context menu at the bottom. 
* Users may be viewing your site from an in-app browser such as the Facebook or Twitter app.
* Some people use Google Chrome on the iPhone which takes up a different amount of vertical height.


## Width & height
In very specific cases, `min-width`, `max-width`, `min-height` and `max-height` can be combined. 

```css
@media (max-width: 900px) and (min-height: 200px) {
  p {
    line-height: 3.2;
  }
}
```

In the above example, the line height of `<p>` elements will changed to 3.2 when the viewport is both 900px wide or lower **and** 200px tall or higher.

As with all CSS, developers should avoid being extremely specific unless necessary. Extremely specific media queries should be avoided except in rare cases. That is because the above example only captures a very specific viewport, leaving hundreds of other viewport dimensions unattended to. It is inefficient and becomes very difficult to debug as more and more possible viewport dimensions are accounted for.

## Breakpoints
Breakpoints are the media query points that alter content on a page via CSS. There are two types of breakpoints:

* Major breakpoints: Affect content in multiple places on your website, such as sections that were once `flex-direction: row` becoming `flex-direction: column`. These make up the majority of breakpoints.
* Minor breakpoints: Affect smaller sections of your website that need small tweaks at certain breakpoints. These make up a very small minority of breakpoints. 

There is no right or wrong number of breakpoints, but a general rule of thumb is: the fewer the better. Around 4-6 should be enough to reach major breakpoints, with maybe 1 or 2 that are minor breakpoints. If many minor breakpoints are made, consider revisiting your code to bring in more responsive vales, such as percentages, `max-width` and `flex-grow`/`flex-shrink`.

Breakpoints are specific to each site, and should not cater to individual devices. Trying to cater to all device sizes will result in possibly hundreds of media queries that will, inevitably, override each other causing issues later on. 

Here are some general breakpoints that you can use to guide you:

```css
/* Portrait tablet and small desktops */
@media (max-width: 940px) {
}

/* Landscape phone to portrait tablet */
@media (max-width: 768px) {
}

/* Landscape phones and down */
@media (max-width: 480px) {
}
```

The best way to find breakpoints is to move your browser, with the help of Dev Tools, larger and smaller to see what "breaks", and making breakpoints to reflect those changes. If you are finding that you are writing breakpoints constantly, you should revisit your base code and see how you can make it more responsive-friendly using `percentages`, `calc`, etc. 

*Note: 320px - 350px is the smallest device most developers cater to. Under that value is becoming very rare on mobile devices.*

## The dreaded horizontal scroll
A large goal in RWD is avoiding any type of horizontal scroll, meaning no content is breaking out of its wrapper. This is also why width-based media queries are more common than height-based media queries - users expect to scroll vertically to view more information, but never want to scroll horizontally.

### Images
A common cause of horizontal scroll issues is images. By default, images will not automatically scale smaller or larger based on the size of the viewport.

Download [this exercise by clicking here](https://hychalknotes.s3.amazonaws.com/responsive-image--conEd.html) to see this in practice.

To fix this issue, we can add some default styles to images to help them resize with the viewport:

```css
img {
  max-width: 100%;
  height: auto;
}
```
This ensures that images will never be bigger than their parent element. 

### Fluid dimensions vs. fixed dimensions
Another common pain point that causes horizontal scroll is the use of fixed widths on elements, instead of using percentages and/or flex properties.

As you build out your websites, you should consider:
* Using percentages instead of fixed widths as much possible, or use flex properties like flex-shrink, flex-grow and flex-basis. This will allow for the layout to be fluid and will avoid the creation of needless breakpoints.
* Using internal wrappers to help contain content.
* Making use of Flexbox to create columns and rows as well as flex-wrap on parents to allow content to wrap to the next line.
## Code Along
Lets take a site we've already built and [make it responsive](./responsive-codealong/README.md)!
## Exercises
* Open up [this starter file by clicking here](https://hychalknotes.s3.amazonaws.com/flex-navigation-responsive-starter--conEd.zip) to work on creating a responsive navigation. The answer key can be [found by clicking here](https://hychalknotes.s3.amazonaws.com/flex-navigation-responsive-answer--conEd.zip).
* Open up [this folder which has three different exercises by clicking here](https://hychalknotes.s3.amazonaws.com/responsive-layout-exercises--conEd.zip). The folder includes the answer key.

## Resources
* [Additional Information on RWD](https://github.com/HackerYou/con-ed-web-dev/tree/master/additional-resources/responsiveness-extended.md)





