# jQuery plugins
Along with jQuery, there are jQuery plugins that fellow developers have created to help integrate these interactions into a site without much trouble.

Integrating a jQuery plugin into your existing code is often quite simple. The developer will provide instructions on how to install their plugin with your code.

Let's take a look at how to integrate two useful jQuery plugins into our code.

For this lesson, download [jquery-plugins--conEd.zip by clicking here](https://hychalknotes.s3.amazonaws.com/jquery-plugins--conEd.zip) and open it in your text editor and browser.

## Flickity
[Flickity](http://flickity.metafizzy.co/) is a powerful tool that allows us to create galleries that work on touch devices.

The [documentation for Flickity](http://flickity.metafizzy.co/) is very detailed and makes it easy to understand and implement. Documentation is the key to using any plugin because it helps you understand the ins and outs of the given plugin.

Following the quick start, we can see that we need to include two files on our site, the jQuery plugin and the CSS go along with it. Often plugins will come with CSS that helps complete the effect.

Flickity offers a range of offers for it's use, but we will be using their CDNs for the CSS and the JS option, which can be found on [their website](http://flickity.metafizzy.co/).

The difference between the files is that the links with 'min' in their filename are 'minified'. That means all the unnecessary whitespace has been removed from the file, effectively making it smaller and faster to load onto our page.

### Implementation
First, we need to load the CSS into our page. Like before, we use a link tag to load the styles into the head of our file.

```html
<link rel="stylesheet" href="https://unpkg.com/flickity@2/dist/flickity.min.css">
```

Next, we need to load in the JavaScript. This will go at the bottom of our page in a very specific place. We need to use jQuery with our plugin, so our plugin needs to be loaded after jQuery, but before we set it up with our document ready.

```html
<script src="https://unpkg.com/flickity@2/dist/flickity.pkgd.min.js"></script>
```

### Initialization
Looking at the documentation, we can initialize our plugin in a few different ways. We're going to looking at the JavaScript initialization only.

In our document ready, we can select an element, and apply a method called `flickity` to it. Currently in our HTML, the class of "gallery" is on the `<ul>` that holds of all of our images.

```html
<script>
    $(function() {
        $('.gallery').flickity();
    });
</script>
```

### Options
Our gallery has some empty areas however. jQuery plugins will offer options that can be passed in. These options are settings created by the developer, that you can provide to tweak the functionality or look.

A list of options we can provide to Flickity can be found <a href="http://flickity.metafizzy.co/options.html" target="_blank">here</a>. Let's explore the 'wrapAround' option.

To provide options to a plugin, we pass them into the method we applied, surrounded by curly braces.

```html
<script>
    $(function() {
        $('.gallery').flickity({

        });
    });
</script>
```

In the documentation for <a href="http://flickity.metafizzy.co/options.html#wraparound" target="_blank">wrapAround</a>, it states that we have to provide an option of true to turn it on. The syntax is similar to how we create CSS properties and values.

```html
<script>
    $(function() {
        $('.gallery').flickity({
            wrapAround: true
        });
    });
</script>
```

## Smooth Scroll
Smooth Scroll is a great plugin that helps to animate the browser when clicking on in-page links. Instead of the hard jump to each id, we can utilize JavaScript to perform the in-between animations.

Visit the <a href="https://github.com/kswedberg/jquery-smooth-scroll" target="_blank">Github page for Smooth Scroll</a> to follow along.

However, there are a few pieces we can see that will help us install the plugin. We already know that we require the plugin to be imported into our page.

Again, we could download the JavaScript directly, or we could leverage a CDN. A search on Google for 'Smooth Scroll CDN' turns up the following link - <a href="https://cdnjs.com/libraries/jquery-smooth-scroll" target="_blank">https://cdnjs.com/libraries/jquery-smooth-scroll</a>.

Create a new script tag after the jQuery script tag and set the source to the CDN link.

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery-smooth-scroll/2.2.0/jquery.smooth-scroll.min.js"></script>
```

#### Implementation

Back on the Github page, it states the following:

"Works like this: `$('a').smoothScroll();`"

`$('a')` represents all `a` tags on the page. `.smoothScroll()` is a 'method' we are applying to them. This piece of code goes directly inside of our document ready function.

```html
<script>
    $(function() {
        $('.gallery').flickity();
        $('a').smoothScroll();
    });
</script>
```

Immediately you'll find that any links that go to 'id's are immediately scrolling!

### Options
Similar to Flickity, Smooth Scroll also has additional options that we can add in. When applying Smooth Scroll to the page, we can provide options to the page.

_Available options are located <a href="https://github.com/kswedberg/jquery-smooth-scroll#options" target="_blank">here</a>_

```html
<script>
    $(function() {
        $('a').smoothScroll({
            offset: 100
        });
    });
</script>
```

## Resources
* [Collection of jQuery plugins](http://www.unheap.com/)
