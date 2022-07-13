# Anchor elements

_Anchor elements_ (also called links, link tags, or anchor links) allow us to create a quick path to other web pages or to places within our own website. It is an inline element that includes both an opening and closing tag.


Anchor elements require a `href` (hypertext reference) attribute which tells the link where the user will go when the link is clicked and includes the user-viewable text in between the opening and closing tags. Its syntax looks like this:

```html
<a href="">content user will interact with and click on</a>
```

## Linking externally

Anchor elements can be used to link to external sites. When we link externally, it is called an absolute link. Here are a few examples:

```html
<a href="http://google.com">Google.com</a>
<a href="https://www.canadalearningcode.ca/">Visit the Canada Learning Code site!</a>
```

Renders as:

<a href="http://google.com">Google.com</a>

<a href="https://www.canadalearningcode.ca/">Visit the Canada Learning Code site!</a>


## Linking internally

Anchor elements can also be used to link to other pages within a multi-page site. A link to an internal page is called a relative link.

To do this, we will need to have more than one HTML file to link to. Create a new folder called `multi-page-website`, and in it create:

* A main HTML file called `index.html`. 
* Another HTML file called `about.html`.

Within our `index.html`, we'll have a link to the `about.html` page, like so:

```html
<a href="about.html">About</a>
```

Naming your main HTML file `index.html` is a convention you always want to stick with. Not only is it a standard industry convention but it is also the name that servers will look for when they need to return a default HTML file when we access URLs in the browser. 

### Linking within a page

Using the power of the `id` attribute, it is possible to link within an HTML page.

Have you ever seen a URL that looks like this?

[https://en.wikipedia.org/wiki/Toronto#Infrastructure](https://en.wikipedia.org/wiki/Toronto#Infrastructure)

When you visit it, the link is going to bring you to the Infrastructure section of the Toronto Wikipedia page.

That octothorp (hashtag/hash symbol) designates an element's `id`. Because `id`s can only be used once per page, it's perfect for targeting a section that we want to move to on our current page.

In your `index.html` file within your multi-page-website folder, create an `h2` with the `id` of "food".

```html
<h2 id="food">Foods I Like</h2>
```
We can now create an anchor tag that will bring the user to the `<h2>` above by referencing the `id` name like so:

```html
<a href="#food">See Foods I Like</a>
```

If we are on another page (for example, `about.html`) and want to link to the `<h2>` that has the `id` of "food" in the `index.html` page, we link that page `id` like so:

```html
<a href="index.html#food">See Foods I Like on another page</a>
```

You can use `id`s to link to any element.

Download [link-within--conEd.zip](https://hychalknotes.s3.amazonaws.com/link-within--conEd.zip) and create a navigation based on the available markup.


## Other elements as links

You can also wrap an anchor element around another element to make it a link, like the below image:

```html
<a href="https://en.wikipedia.org/wiki/Kangaroo" title="Click here to go to the wikipedia page about Kangaroos.">
  <img src="https://picsum.photos/200/300" alt="Placeholder image">
</a>
```

Renders as:

<a href="https://en.wikipedia.org/wiki/Kangaroo" title="Click here to go to the wikipedia page about Kangaroos.">
<img src="https://picsum.photos/300/300" alt="Placeholder image">
</a>


## Opening links in a new window 

If we click the links in the above examples, they will open in the current window. It's common for developers to set up links such that they are opened in a separate window so users are not taken away from the current website.

Adding the `target` attribute, with the value of `_blank` will help our links open in a new page.

```html
<a href="https://www.google.ca" target="_blank">Go to Google</a>
```

> **Accessibility tip**
>
> Older versions of AT may not announce that the link will open in a new window, despite the `target` attribute. To help support them, along with users who may be confused by windows opening in a new tab, consider adding the helper text that the link will open a new window somewhere around the link. An icon or small image could also be used to signify the page being opened in another window, but be sure that `alt` text is included.
