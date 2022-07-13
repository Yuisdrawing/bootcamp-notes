# What is CSS?
We use CSS (cascading stylesheets) to style our pages and help bring the HTML structure we have written to life! With CSS, the look, feel, size, color and virtually any visual aspect of the HTML elements on your page can be altered. 

The CSS spec (specifications) are being constantly worked on by the [CSS working group](https://www.w3.org/Style/CSS/members.en.php3) - a group of professionals who meet and discuss how to improve and evolve CSS on a regular basis - making the world of CSS an exciting one to be a part of! Some developers specialize in CSS because of its many intricacies.

## CSS syntax
CSS is made up of rules that dictate which element(s) we want to affect and how. Here is a rule that will change the text color of all  `<h3>` elements to red:

```css
h3 {
  color: red;
}
```

There are two key parts to a CSS rule: 
* Selector: Chooses the element(s) to which the styles will be applied. In the example above, we are targeting `<h3>` elements.

* Declaration: Where we define what styles we would like to apply. Inside the curly braces, we include properties and values. In the example above, the property is `color` and the value is `red`.

![Diagram](https://hychalknotes.s3.amazonaws.com/diagrams.png)

We can include as many properties and values as we want for any selector, just remember to use a colon between the property name and its value, and to end each declaration with a semicolon.

```css
h3 {
  font-size: 16px;
  background-color: yellow;
  color: red;
  /*etc...*/
}
```


### Colors in CSS

In the coming classes, we will be taking a look at different ways to choose a color as a value, but we'll look at one right away so we can play around with them:

* Named: You can use the name of the color for most basic colors (`red`, `green`, `blue`, `pink`, etc), as well as a few exotic ones like `papayawhip` and `palegoldenrod`. To see other available color names, visit [colours.neilorangepeel.com by clicking here.](http://colours.neilorangepeel.com/)

```css
h3 {
  color: palegoldenrod;
}
```

Take some time to find a color that speaks to you - many developers have a go-to color that they use a lot while they develop. 

## Where to write CSS

As it is a different language from HTML, CSS needs to be written in a different place for our text editor to recognize it. [Download this folder](https://hychalknotes.s3.amazonaws.com/writing-css--conEd.zip) and practice using each of the below methods as you work through them.

There are three places you can write your CSS:


### External stylesheet

External stylesheets are text files where all of the CSS lives, which use the file extension `.css` (like a `.html` file for our markup, but for our styles instead). It is common for this document to be named `style.css` or `styles.css`. This method is considered best practice and is what you will be using in your projects.

To connect our stylesheet to our HTML, a new `link` element is included in our HTML's `<head>` - `<link rel="stylesheet" href="">`. It is made up of:
* The `rel` attribute, which is defining the relationship as stylesheet. A CSS document will always have this relationship to HTML because its sole purpose is to act as a stylesheet.
* The `href` attribute, which acts the same as it does in an anchor element; will link to our stylesheet using a relative path.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>My Website</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

</body>
</html>
```

This linking method is most common because most sites have multiple pages that need the same styles. Linking a single stylesheet means that style changes made in that one file will be reflected on every page which links to it (ie. your entire site).


### Internal stylesheet

An internal stylesheet is written directly in the `<head>` of your HTML document. Instead of linking to an external stylesheet, all of the CSS is written in a `<style></style>` element, which is nested in the `<head>`.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>My Website</title>

  <style>
    h2 {
      color: red;
      font-size: 50px;
    }
  </style>

</head>
<body>

</body>
</html>
```

The `<style>` tag tells the browser that you are no longer writing HTML and everything inside of the tags is CSS. Though it will work when placed anywhere on the page, it is best practice to include it in the `<head>` element of your document.

We will be using internal stylesheets a lot to show examples in class because they are fast to set up. Note that in a professional setting, writing the styles in the `<head>` can be problematic because of how large and long styles can be. It would cause a lot of needless scrolling in your HTML document.


### Inline styles

Inline styles are written directly on individual HTML elements, using the `style` attribute on the element's opening tag.

```html
<h2 style="color:red; font-size:50px;">Hello, I'm a header with inline styles</h2>
```

The downside to this is that those styles only apply to that specific instance of that element. Besides not being very efficient, it's also hard to read. This method of writing styles is the least practical and should be avoided at all costs (but you'll see it around the internet)!


## Resources
* [CSS working group Twitter account](https://twitter.com/csswg?lang=en)
* [Lea Verou's Twitter account, CSS working group member](https://twitter.com/LeaVerou?lang=en)
