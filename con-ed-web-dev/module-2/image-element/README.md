# Image element

The _image element_ allows us to use images on our website. Noticeably, it does not have a closing tag - only an opening tag. 

Its syntax looks like this:

```html
<img src="link to image source" alt="descriptive alt text">
```

It has two mandatory attributes:

* `src`: the source attribute, which defines a path to where the image is stored. If this isn't included, an image will not render.

* `alt`: this is the alternate text that describes the image, and appears when an image does not load This attribute is mandatory for accessibility reasons and it helps search engines understand the context of your images. It is important to provide a meaningful `alt` description for every image that carries with it vital meaning for the user.

> **Accessibility tip**
>
> It's important to include alt text in the `alt` attribute for all image elements. We can make the experience for those using screen readers, or those with slow internet connections, dramatically better by being descriptive. Instead of <code>alt="my cat"</code>, describe the picture as you would to someone who can't see it. <code>alt="My cat, Chloe, stretching in a ray of sunshine beside a window"</code>. Descriptive alt tags can make or break a user's experience.
>
> What if I don't think my image adds value?
>
> There are times when you don't need alt text. If the image doesn't add value or isn't useful to people using AT (for example, the picture is purely decorative), include the `alt` attribute, but leave it empty like so: `<img src="images/image.jpg" alt="">`. If you do not include a value for the `alt` attribute, screen readers know to skip describing the image. However, if you don't include an `alt` attribute at all, the image's file path will be read instead, creating a less than ideal experience for users utilizing AT.
>
> Words in images
>
> It's better to use actual text instead of images with text in them. AT can't read the text in images, they can only read alt text on the <code>img</code> element. Also, when images with text are zoomed, they can lose readability and become pixelated. 


## Image paths

An image element's source path, similar to the anchor element, can be absolute or relative.

An absolute image path is typically an image hosted elsewhere on the internet. An example would be to use an image sourced via Google image search or from an image placeholder service like placekitten.com.

A relative path is one that uses your HTML document as a starting point. This will be the path that leads out of your document, through folders or sub-folders, to end up at the image file.

```html
<!-- using an absolute url from another website -->
<img src="http://dogpictures.com/dog.jpg" alt="A placeholder image of a dog.">

<!-- using a url relative to the HTML page -->
<img src="images/dog.jpg" alt="My dog Hugo sitting in the grass.">
```

## Placeholder image generators

One of the many fun parts of being a web developer is using funny images as placeholders. In many of our examples, we will use random images that we found online. Sometimes a design will require a specific size of the image; instead of finding an image and using Photoshop to resize it, we can make use of services that provide placeholder images with the exact size we're looking for.

Here are a few options:

* [https://placekitten.com/](https://placekitten.com/)
* [https://picsum.photos/](https://picsum.photos/)
* [http://placehold.it/](http://placehold.it/)

For each of the above, instead of setting the image `src` to a URL that ends in a file extension that designates an image (like `.png, .jpg, .jpeg, .gif`), we set it to one of the previous URLs with the last two numbers being the `width` and the `height`:

```html
<img src="https://picsum.photos/350/150">
```

<img src="https://picsum.photos/350/150">

```html
<img src="https://placekitten.com/250/250">
```

<img src="https://placekitten.com/250/250">


## Exercise

Practice using a relative and absolute image path by [downloading this folder by clicking here](https://hychalknotes.s3.amazonaws.com/relative-images--conEd.zip). The instructions are inside of the "index.html" file.

You can see the [answer key by clicking here](https://hychalknotes.s3.amazonaws.com/relative-images-ANSWER-conEd.zip).


## Resources
* [Best practices for alt text](https://moz.com/learn/seo/alt-text)


