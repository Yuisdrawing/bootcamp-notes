# SCSS

So far, we've been working with CSS. It's been able to help us style our websites really well, but it has an extremely powerful cousin called [SASS](http://sass-lang.com/) (Syntactically Awesome Style Sheets) that can help us take our code to the next level.

SASS is a type of [CSS pre-processor](https://developer.mozilla.org/en-US/docs/Glossary/CSS_preprocessor) which, at its base, is CSS with superpowers. It extends what CSS is capable of doing by adding things that have the ability to make our workflow faster and create CSS that is more maintainable, organized, and modular. [Less](http://lesscss.org/) and [Stylus](http://learnboost.github.io/stylus/) are other examples of CSS pre-processors.

## SASS vs. SCSS

There are two syntaxes available for SASS:

- **SASS** is the older syntax. The largest difference is that it doesn't use any brackets or semi-colons. Instead, it relies on indentation and new lines to separate properties. Any file written in SASS must end with ".sass".

The below is SASS syntax:

```sass
ul
	display: flex
	background: black
	li
		flex: 1 0 auto
		a
			display: inline-block
			padding: 10px
```

- **SCSS (Sassy CSS)** is what we'll be using and is the most up to date (and constantly updated!) syntax in the SASS family. Despite it being spelled with a "C" instead of an "A", it is still pronounced as "SASS". Any file written in SCSS must end with ".scss".

Unlike its SASS sibling, SCSS looks a lot more like CSS because it uses brackets and semi-colons to separate properties.

The below is SCSS syntax:

```scss
ul {
  display: flex;
  background: black;

  li {
    flex: 1 0 auto;

    a {
      display: inline-block;
      padding: 10px;
    }
  }
}

/* or you could write vanilla CSS and still be valid! */
ul {
  display: flex;
  background: black;
}
```

Everything that is valid in CSS is valid in SCSS, which means that you can just write regular CSS in your `.scss` stylesheets and it will be valid - but you can also use some enhanced features that extend the capabilities of regular CSS.

![Diagram showing that everything in CSS is also a part of SASS](https://hychalknotes.s3.amazonaws.com/sass-css.png)


## Working with SCSS

The browser can only read three languages: HTML, CSS and JavaScript. Where does that leave SCSS?

To use SCSS, we need to use applications or tools that will process our SCSS and turn it into CSS that our browser can interpret. That means that without the use of an application or tool, a browser could not understand what styles are in our SCSS stylesheets.

![diagram showing a scss file being turned into css with the help of a compiler](https://hychalknotes.s3.amazonaws.com/compiling-scss.png)

**Using Live Sass Compiler**

We are going to be using a VSCode extension called [Live Sass Compiler](https://marketplace.visualstudio.com/items?itemName=ritwickdey.live-sass) to help us compile our SCSS to CSS.

Find the extension under the extensions tab in your VSCode and install it. 

![screenshot showing live sass compiler on vscode](https://hychalknotes.s3.amazonaws.com/live-sass-compiler.png)

Download [scss-starter--conEd.zip](https://hychalknotes.s3.amazonaws.com/scss-starter--conEd.zip). Unzip the content of this file and drag this folder into VSCode where it will create an independent workspace. 

This folder is a pre-configured project boilerplate that we can directly write SCSS in. Note that our project structure looks like this:

```
- scss-project 
    - .vscode
        - settings.json
    - styles
        - scss
          - styles.scss
    - index.html
```

Behind the scenes `.vscode` contains a pre-configured `setting.json` file that will help us make SCSS work in this project folder!

A few other notes on using Live Sass Compiler successfully:
- If you are using the the [Color highlight](https://github.com/egonyans/vscode-ext-color-highlight) extension ensure it is disabled as it will interfere with Live Sass Compiler.
- Make sure that your project folder is opened as the root workspace in your VSCode window. You can do this by dragging the folder into VSCode:
<img src="https://hychalknotes.s3.amazonaws.com/scss-workspace.png" alt="screenshot of scss workspace" width="280">

In order to activate the sass compiler we need to: 
- Press the "Watch Sass" button at the bottom of your VSCode window 
![screenshot showing watch sass button on vscode window](https://hychalknotes.s3.amazonaws.com/watch-sass-button.png)
**or,**
- Press `Cmd + Shift + P` to bring up the VSCode command palette, then type in "Live Sass", you will see options pop up. Select "Live Sass: Watch Sass"
![screenshot showing watch sass command on vscode window](https://hychalknotes.s3.amazonaws.com/watch-sass-command.png)

You will see the output window open as the indication of the compiler running. 

To verify that it's actually working and that the `.scss` file is compiling correctly. Try modifying and writting some css in the `styles.scss` file. Once you save the file, you should see a `styles.css` file that got automatically generated in your `/styles` folder. The `styles.css` file should have the styles you've written from `styles.scss`. 

If you've got the `styles.css` successfully generated, great! You are ready to utilize the power of SCSS! 👏

## Partials

Let's starts with understanding partials. SCSS partials are like puzzle pieces that come together to build out our styles. We use partials to organize our css into separate files so that it's more manageable. Without partials, our single stylesheet can get very long, messy and difficult to maintain. 

To create a partial, we need to pre-pend the file name with an underscore `_`. 

This will tell the compiler to treat it as a partial and not create a separate CSS file for it. 

For example, here are some of the common use cases for partials:
```bash
  _setup.scss
  _global.scss
  _nav.scss
  _footer.scss
```

Remember when we always had to include our setup snippet in the beginning of every stylesheet? Well, now we can place that chunk of code in a `_setup.scss` partial.

In order for us to combine different chunks of code partials together we need to use `@import` to import all our partials into `styles.scss` file. Think of `styles.scss` as our central collection point for all the our code snippets. 

Our `styles.scss` file content should look like this:
```scss
@import "./setup";
@import "./global";
@import "./nav";
@import "./footer";
```

The compiler will then take `styles.scss` as reference point and compile `styles.css` for us to use in our `index.html` file. 

You can open up [scss-example--conEd.zip](https://hychalknotes.s3.amazonaws.com/scss-example--conEd.zip) to explore what SCSS partials structure look like. 

Remember we should **always** link the `.css` file not the `.scss` file! Otherwise our styles will not load! The browser does not read SCSS!

![scss diagram](https://hychalknotes.s3.amazonaws.com/scss.jpg)

**Other notes about partials:**
- The order of `@import` statements matters! It will determine the order of styles in the compiled stylesheet.
- You will need to name the partials to be imported into the `style.scss` with underscores. You do not need the underscore or the `.scss` extension for the `@import` statements.
- Do not write styles in the `.css` file! They will be overwritten when a `.scss` file is saved. 


## Using SCSS

The best way to learn SCSS is by playing around with a SCSS file. Let's go back to our SCSS examples file to get started.

There's a lot going on in the folder, so let's break it down:

- There is an `index.html` - we're familiar with that: it's where our HTML lives. In it, we can see that it is linking to a `styles.css` file.
- There is a `/styles` folder. Inside of it there is:
  - `/scss` folder
  - `.scss` partials inside the `/scss` folder with everything imported into the `styles.scss` file.
  - An images folder, holding all of the images.

Let's write our first line of SCSS:
Head into `/scss` folder, and then into the header partial.

Set the h1 color to red - write it the same way you would write CSS:

```css
h1 {
  color: red;
}
```

Now save your file and open up the html in your browser. The h1 has turned red!

You've now written your first line of SCSS!

## Nesting

Nesting is one of SCSS's most powerful assets!

You can nest selectors instead of using long selector names, keeping your stylesheet organized, saving space and keeping your HTML nice and clean. You can even tack on additional characters to a selector using the `&` symbol!

A nested selector represents a child element.

```scss
ul.nav {
  background: red;
  width: 100%;
  li {
    border-right: 1px solid red;
    a {
      background: blue;
      padding: 10px;
      &:hover {
        background: yellow;
      }
    }
  }
}
```

Compiles to the following CSS

```css
ul.nav {
  background: red;
  width: 100%;
}
ul.nav li {
  border-right: 1px solid red;
}
ul.nav li a {
  background: blue;
  padding: 10px;
}
ul.nav li a:hover {
  background: yellow;
}
```

The ampersand `&` is used when nesting, and it truly carries a meaning here similar to _and_, _as well as_, _also_. The `&` references the parent selector when nesting. It is a powerful tool to organize and extend your SCSS.

See below for examples of the HTML and CSS/SCSS utilizing the power of `&`.

Adding a hover effect on `<button>` elements:

![Button element with a hover effect selector gif changing between nesting in SCSS and a regular CSS selector.](https://hychalknotes.s3.amazonaws.com/button-hover.gif)

Selecting a class name that is nested in a parent, where they share similar class names:

```html
<section class="blog">
  <p class="blog-content">Hello! I am some content for this blog.</p>
</section>
```

![An element with blog-content class gif changing between nesting in SCSS and a regular CSS selector.](https://hychalknotes.s3.amazonaws.com/blog-content.gif)

Codepen credit for the above gifs come from [this codepen](https://codepen.io/richfinelli/pen/qbZgQK/) by [Rich Finelli](https://codepen.io/richfinelli/).

**The Sass Inception Rule:** "Never nest more than three levels deep." <http://thesassway.com/beginner/the-inception-rule>

## Variables

Syntax: `$variableName: variableValue;`

Variables are another shining star in SCSS. Variables are used to hold reusable values. For example, you can specify a colour value to an easy-to-remember variable name and reuse it throughout the stylesheet.

```scss
$primary: #b3eb95;
$secondary: #ccc;
$basefont: "HelveticaNeue-Light", "Helvetica Neue Light", "Helvetica Neue",
  Helvetica, Arial, "Lucida Grande", sans-serif;

a.myLink {
  background: $primary;
}

p.confirm {
  border: 1px solid $primary;
  color: $secondary;
  font-family: $basefont;
}
```

Compiles to the following CSS

```css
a.myLink {
  background: #b3eb95;
}

p.confirm {
  border: 1px solid #b3eb95;
  color: #ccc;
  font-family: "HelveticaNeue-Light", "Helvetica Neue Light", "Helvetica Neue",
    Helvetica, Arial, "Lucida Grande", sans-serif;
}
```

Variables are incredibly useful to remove any repeated pieces of code. By collecting common styles and assigning them a simple, memorable name you can use quickly, you can cut down production time.

### Variables as strings

Variables can also hold strings, which are a series of text characters in quotes.

In the below example, we have set a variable called "anchorTagHoverFocus" that holds the pseudo-state of hover and focus on an anchor tag.

```scss
$anchorTagHoverFocus: "a:hover, a:focus";
```

We would use it like so:

```scss
main {
  padding: 10px;
  li {
    #{$anchorTagHoverFocus} {
      color: red;
    }
  }
}
```

It would compile to the following CSS

```css
main {
  padding: 10px;
}

main li a:hover,
main li a:focus {
  color: red;
}
```

This method of injecting a string into our code with the use of a variable is called "interpolation" and it can help save us from typing the same thing over and over again across our code.

You can see some variables in action in the "variablesMixins" partial.

### Variable names

Variable names should not contain specific numbers or colours because the variable values might change, rendering the name of the variable deceiving! For example:

```scss
$green: limegreen;
```

Would become very confusing if you changed your mind and gave it the color rebeccapurple:

```scss
$green: rebeccapurple;
```

The only specific colours you can use are white and black because every website will most likely have a variation of that colour and to change white value to another is consistent with the naming scheme.

**To do:**
Currently, the class of "bubble" and the images have a `border-radius` of 4px.

To make the code DRY and more maintainable try making a new variable, named `borderRadius`, to hold a value of 4px that can be used on the class of "bubble" and as well as the images. Add the new variable to the "\_variablesMixins.scss" file with the other variables.

## Mixins

Syntax:

```scss
@mixin nameOfMixin() {
  color: blue;
  font-size: 50px;
}
```

Mixins are a powerful tool to use when we want to repeat similar chunks of code. In the above example, the `mixin` named nameOfMixin holds two values.

To use it, we use `@include` within our selectors:

```scss
main {
  p {
    @include nameOfMixin();
  }
}
```

This would compile to the following CSS

```css
main p {
  color: blue;
  font-size: 50px;
}
```

Mixins save us tons of time because they allow us to use one line to call a whole bunch of styles at the same time!

We can also create mixins that allow arguments to be passed in to modify their output, making them dynamic.

In the below example, we use a placeholder variable called `$sizeValue` that doesn't hold any value yet - it is dynamic and it will change depending on what value we give it!

```scss
@mixin funFont($sizeValue) {
  font-size: $sizeValue;
  color: blue;
  font-weight: bold;
}
```

When the mixin is called within a selector, we pass in an "argument" with the value we need, and that value is supplied in the place of the placeholder variable.

```scss
h1 {
  @include funFont(36px);
}

p {
  @include funFont(14px);
}
```

This compiles to the following CSS

```css
h1 {
  font-size: 36px;
  color: blue;
  font-weight: bold;
}

p {
  font-size: 14px;
  color: blue;
  font-weight: bold;
}
```

We can even get SASS to do math for us! So far, we have been setting the base font size in our html to 62.5% to allow for easy rem calculation. Here's how we might make it even easier with a mixin:

```scss
@mixin fontSize($sizeValue) {
  font-size: $sizeValue * 1px;
  font-size: ($sizeValue/10) * 1rem;
}

h1 {
  @include fontSize(48);
}
```

Compiles to the following in CSS:

```css
h1 {
  font-size: 48px;
  font-size: 4.8rem;
}
```

You'll notice that when writing `font-size: $sizeValue * 1px;` we didn't have to wrap \$sizeValue \* 1px in our usual `calc()` function. For simple mathematical calculations in SCSS we can just write them as they are without wrapping them in a special function.

**Alternative Option**

If you are setting `html { font-size: 112.5% };` (for 18px) or `html { font-size: 125% };` (for 20px)  instead of `html { font-size: 62.5% }` (for 10px), just replace `font-size: ($sizeValue/10) * 1rem` for `($sizeValue/18) * 1rem` or `($sizeValue/20) * 1rem` in the previous mixin.

### Useful Mixins

**Positioning**

```scss
@mixin position($type, $top, $right, $bottom, $left) {
  position: $type;
  top: $top;
  right: $right;
  bottom: $bottom;
  left: $left;
}

.box {
  @include position(absolute, 10px, 10px, 5px, 10px);
}
```

**Centering**

```scss
@mixin centerFlex() {
  display: flex;
  justify-content: center;
  align-items: center;
}

header {
  @include centerFlex();
}
```

**To do:**
Try making your own mixin that contains the CSS filter `grayscale()` inside of it and ensure it takes in one argument so the amount of grayscale can be changed in the "variablesMixins" partials file.

## Functions
SCSS also comes with built-in functions to help make big jobs much easier!

A couple particularly useful built-in functions are the [`lighten`](http://sass-lang.com/documentation/Sass/Script/Functions.html#lighten-instance_method) and [`darken`](http://sass-lang.com/documentation/Sass/Script/Functions.html#darken-instance_method) functions. They create a lighter or darker version of any colour.

```scss
$primary: #b3eb95;

a.myLink {
  background: $primary;

  &:hover {
    background: lighten($primary, 10); //10% lighter than $primary;
  }
  &:visited {
    background: darken($primary, 10); //10% darker than $primary;
  }
}
```

You can find a full list [of SCSS Functions by clicking here](http://sass-lang.com/documentation/Sass/Script/Functions.html)

## SCSS gotchas

- If you make changes in your CSS file, they will not save. That's because the CSS updates completely every time you save your SCSS.
- The order of your partial imports matters! CSS reads top to bottom, so you will always want to put your setup, global styles, and variables/mixins as the first things to come in to your file. This will allow the styles further down to have access to them.
- Linking to background images is a common point of confusion because you must write the relative path to a background image as if it is coming from the CSS stylesheet. Don't forget that our SCSS is all being compiled to CSS. The compiled CSS is what the browser is using to understand our styles, meaning that we should link to background images as if we are linking from the compiled CSS file, and not our SCSS partials.

## Resources

- [SCSS Documentation](https://sass-lang.com/documentation)
- [Media Queries & SCSS](https://thoughtbot.com/blog/sasss-content-directive)
