# Introduction to HTML

Hypertext Markup Language (HTML) is the standard language that we use to create web pages. When we open an HTML file within a browser, the code is interpreted as a visual (or audible) web page.

Think of HTML as the structure of a building. It makes up the beams, walls and the floor of the secure structure that we live in. It won't be beautiful right away because we haven't painted the walls yet - that's CSS's job (another language entirely).

Using HTML, we can define how our content is interpreted and consumed by the browser and the user. When we write a text document, we might organize our content using headers, paragraphs, quotes, and lists. In HTML, we do the same. However, while we might bold or underline a header in a regular document, this is not done in HTML. That's what CSS is for. If you remember nothing else, remember that **HTML should only be used to show the structure and content of a website**.

## Base HTML structure
All websites include a standard base structure. This structure will be different based on the project and age of the web page.

The current standard page structure is below:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>My Website</title>
  </head>
  <body>
    <p>This is a paragraph!</p>
  </body>
</html>
```

You can view this in your browser or code editor by viewing [base-html--conEd.html](https://hychalknotes.s3.amazonaws.com/base-html--conEd.html).

**This is a great opportunity to try out opening a file in a new tab, by pressing `command` (Mac) / `ctrl` (PC) + click with your mouse.**

The base structure of a website is something that you will not be expected to type by hand, but it's important to become familiar with it and understand what each portion of the code does.

This structure should be included on every web page.

* `<!DOCTYPE html>`: Always the first thing in an HTML document, this tag tells the browser that the file is written in HTML5 (the latest version, which we are working with today).
* `<html lang="en"></html>`: This element _wraps_ (surrounds) all of the content of a webpage. It is always the outermost element of the HTML.
* `<head></head>`: The `head` element doesn't appear on the page itself. It is a place to provide information about the site to the browser.
* `<meta charset="UTF-8">`: `meta` tags give the browser specific information about the website it is displaying. In the case of this tag, it is telling the browser what set of characters it will be interpreting and printing to the page.
* `<title></title>`: This is where we write the title of the website. It doesn't appear on the page itself (since it's in the `head`), but this title will appear in the browser tab.
* `<body></body>`: This element wraps all of the content that will appear on the page. Everything that is viewable on a site is written between these tags.

> **Accessibility tip**
>
> Setting a language attribute for your page is extremely important! It allows search engines to properly index your site and allows Assistive Technologies like screen readers to interact meaningfully with the content. For example, if a user can only speak English, but a website is in French, if there is no language attribute, a screen reader would attempt to read the French page as an English page leading to mispronunciations and an overall poor user experience. Read more about it [here](https://www.w3.org/TR/2008/REC-WCAG20-20081211/#meaning-doc-lang-id). (WCAG Level A).


## HTML syntax

Syntax is a set of rules that makes up a language. Every language has syntax we must follow for it to make sense to others who interact with it, whether the language be German, Korean, or HTML. As web developers, this includes the browser! HTML syntax is what makes up the building blocks of the language.

Download [html-elements--conEd.html](https://hychalknotes.s3.amazonaws.com/html-elements--conEd.html) for a base file to work in.

**Don't forget to use to right click with your mouse and go to "Save Link As..." to save the link as a file.**

HTML is made up of _elements_ that describe our content. We create these elements by wrapping our content in _tags_.

```html
<h1>Hello!</h1>
```

Typically, elements will have an opening and closing tag that reference the name of the element, and the content that is read and interpreted by users goes within the tags.


## Creating elements

### Opening and closing tags

All opening tags begin with an opening angle bracket `<`, have the name of the element, and conclude with a closing angle bracket `>`.

```html
<p>
```

Following the opening tag, we insert the content we want to present.

```html
<p>Hey, I'm an element
```

Finally, we close the element by writing a closing tag. The closing tag pre-pends a forward slash `/` to the opening angle bracket.

```html
<p>Hey, I'm an element</p>
```

Note that there are some elements that have no closing tag, and thus contain no content. We'll explore those later in the course.


### Terminology

* Element: A structural component of a website that describes and contains our content.
* Tag: The opening and closing portion of element that wraps our content.



### Using HTML
Below is a `<p>`, a paragraph element, with an `<em>`, an emphasis element - inside of it.

```html
<p>Hello there! How are <em>you</em> today?</p>
```

The line above renders something that looks like this:

<p>Hello there! How are <em>you</em> today?</p>

We wrap everything in the `<p>` tag because we are describing the content as a paragraph. Inside of that we wrap "you" in an `<em>` tag because we are describing the content as something that has an emphasis, which can change the nuance of a sentence.

The outputted result from the browser is human readable text with some default styling that the browser has added for us. We will be changing this default styling later!


## Separation of content and style

**This is very important!**

You'll notice when we add elements to the page, that there is a bit of base styling when the page renders in the browser. This is from the browser, and provides a default look.

However, it is important to understand that marking up content with the proper elements helps to describe the content to the browser and assistive technologies; it has no meaningful or programmatic connection the styling of the element (even if the browser defaults make it seem otherwise).

You may have seen elements like the following used within web pages:
```html
<u>I'm underlined!</u>
<font color="blue">I'm blue!</font>
<center>I'm centered text!</center>
```

![depiction of invalid HTML elements that show style instead of structural meaning](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-13%20at%204.24.55%20PM.png)

We can see that the above tags have visual (ie. stylistic) effects on the elements, but this means nothing to:
* Assistive technologies (AT), like screen readers, which depend on the HTML being descriptive so that it can relay that meaning to the user. Assistive Technologies announce what they are reading and interpreting to the user out loud, but none of the above tags describe the elements' contents or their role on the page. If, for example, the underlined text is more important than other text, then that is content structure, and a meaningful HTML tag should be used to signify that importance. If it is underlined simply for stylistic reasons (i.e it is visually nice to look at), that is instead a job for CSS, which we'll learn later in this course.
* The browser (or SEO) would equally struggle to understand the meaning for the same reasons as AT.


## Nesting elements

_Nesting_ is an extremely important concept in coding because it signifies a parent-child relationship between elements, something that will become increasingly more vital as we move though this course. When we nest an element within another, we are wrapping an element around the others.

When you are nesting elements within each other, you must always close them in the reverse order that you opened them. Failing to do so will cause your HTML to be invalid and your page will break.

In the first example below, even though we close the `</div>` and `</strong>` tags, we do it in the wrong order. Because the `<div>` was the first element to be opened, it needs to be the last closed. 

**Incorrect 👎**
```html
<div>
  <h1>Welcome,</h1>
  <p>Today is <strong>September 1st</p>
</div>
  </strong>
```

**Correct 👍**
```html
<div>
  <h1>Welcome,</h1>
  <p>Today is <strong>September 1st</strong></p>
</div>
```
In the correct example, you can see the div element is **wrapping** all of the elements inside of it. We say that the div is the _parent element_ and everything inside are its _child elements_.


## Indentation

When nesting, it's a best practice to use indentation within our code to show structure. Indentation also helps us keep our code readable and easy to use.

```html
<div>
  <h1>I'm a title inside of a div!</h1>
  <p>I'm a paragraph inside of a div!</p>
</div>

```

There are some exceptions to this rule, like the elements `<span></span>`, `<em></em>` and `<strong></strong>` which go 'inline' with our content. We'll learn more about inline elements in detail later on in this course, but they look like this in our code:

```html
<p>Hello, I'm a <em>computer</em></p>
```

Download, unzip, and open [element-reindent--conEd.html](https://hychalknotes.s3.amazonaws.com/element-reindent--conEd.html) in your text editor. The goal is to indent the index.html file so the HTML is easier to read and navigate through. 

If you get stuck, check out the [answer key by clicking here](https://hychalknotes.s3.amazonaws.com/element-reindent-ANSWER--conEd.html).

## HTML comments
HTML comments help you stay organized as you write your code! To comment out any HTML code, place `<!--` and `-->` around the HTML. Commenting it out means that it will not render on the page when you load it in your browser (users will not see it!) but still remain in your HTML so you can revisit it later on.

In code, they look like this:

```html
<!-- This is a basic comment -->
<!-- <p>This is some <strong>HTML</strong> commented out -->
<!--
  This is a
  muli-line
  comment
-->
```
One useful way to use comments is to mark where content starts and stops:

```html
<!-- Header Code STARTS -->
  My HTML Code...
<!-- Header Code ENDS -->
```

You can also use comments to make notes right in your code editor! It's a great tool to remind yourself what you were doing so you can pick it back up another day or taking notes while you're in class about important information.

```html
<p> Some content for my page </p>
<!-- Finished adding the first p element Thursday night. TO DO: Add another Friday afternoon -->
<!--- A <p> needs both an opening and closing tag, with the content humans can see going inside the opening and closing tag --->
```

You can also use the comment shortcut to comment and uncomment your code that you've highlighted:

`command` + `/` on a Mac 

`ctrl` + `/` on a PC 

Try it out in your element reindent file that was used to practice indention!


## Attributes

On their own, HTML elements provide structure and meaning/context to our websites. To make elements more dynamic and to let us use them more robustly, we can give them _attributes_.

An attribute exists as a declaration within the opening tag of an element and provides a value with an equals sign and quotes.

```html
<div class="top"></div>
```

In the example above, there is a `<div>` element that has a _class_ attribute. The value of the class attribute is `top`. 

There are a range of attributes available and we will go into detail on the most commonly used attributes in the next few lessons.
