# Image formats
There are several file types available for adding images to a web page. Each type is best suited for specific uses and comes with pros and cons. 

The many options can cause confusion, but as a rule of thumb, it's best to use the format that maintains the highest quality while reducing the file size. There are two main types of image formats:

* Lossless: the image can be made smaller with no loss to the quality (i.e it does not become pixelated). The image can be saved over and over without losing any quality.
* Lossy: the image is made smaller but loses some of the quality (i.e it becomes more grainy and less crisp). When saving an image in a lossy format repeatedly, the image quality gets progressively worse.

## JPEG/JPG
JPEG/JPG images use lossy compression. They can support a lot of rich colours and gradients making them optimal for photographic images. These files are generally larger than other image types. Most images online, especially larger images like hero images or photos that showcase works from an artist, are in JPEG/JPG format.

*Note: JPEG/JPG are exactly the same. JPEG was the original naming scheme, but older versions of Windows required three letter extension names, forcing the JPEG into JPG.*

The lossy compression makes this format less favourable for images with flat colours and line drawings as what should be sharp lines may end up looking fuzzy. 


Best uses for this image format: photographs and images with lots of rich colours and gradients, like backgrounds, header images and any image where the rich colour is meant to shine.

## PNG
The PNG file format was originally created in 1995 to replace the GIF image format.
There are two types of PNG formats, PNG-8 and PNG-24, and they both use lossless compression. 

### PNG-8
PNG-8 is short for "8-bit PNG" meaning the image is 8 bits per pixel. Similar to GIFs, this image format can only store 256 colours and supports transparency but it has better support for alpha transparency than GIFs.

![png-8 vs gif](http://i.stack.imgur.com/B09oZ.png)

Unlike GIFs, PNGs do not support animation.

Best uses for this image format: Images with simple colours including those that require alpha transparency.

### PNG-24
PNG-24 is short for "24-bit PNG" meaning it can hold many more colours than PNG-8. Just like PNG-8, PNG-24 also supports alpha-transparency.

However, PNG-24 files are usually much larger than JPEGs, GIFs and PNG-8s. Even though PNG-24s can handle many more colours, they are not meant to replace JPEGs.

Best uses for this image format: Images with rich colours, gradients and shadows, that all require transparency, alpha transparency or opaque background.

## GIF
GIF (Graphics Interchange Format) is probably best known for the ongoing war over its pronunciation (a hard "G" versus a soft "G"). GIFs use lossy compression and often have the smallest file size of all the image formats. However, GIFs can only take a maximum of 256 different colours so they are best used for images with minimal colour variation. Introduced in 1987, the  GIF is one of the oldest image file types.

GIF images can have transparency (though transparency is better handled with PNGs) and can also be animated.

![](https://media.giphy.com/media/JfDNFU1qOZna/giphy.gif)

Best uses for this image format: Images with simple colours, line drawings, icons and animations. 

## SVG
SVG (scalable vector graphics) is a vector graphic based on an XML(Extendible Markup Language) format. At their core, SVGs are made up of tags and attributes that define graphics. This makes it possible to manipulate graphics right in your code editor, without the use of Photoshop or Sketch. SVGs are known for scaling without losing clarity, having smaller than average file sizes and looking great on retina displays. 

Unlike other image formats, SVGs utilize the `<svg>` element, which is an inline element by default and has an opening and closing tag. They are also made up of the following elements as a base:
* `<g>`: Group the related elements together in an SVG.
* `<path>`: Define the coordinates of the graphic. This is because SVGs consist of circles, rectangles, and paths created in XML and combined into drawings on web pages, rather than consisting of a bitmap like other image types.

Download and open up [an SVG graphic of some happy marshmallows by clicking here](https://hychalknotes.s3.amazonaws.com/noun-project-marshmallows--conEd.svg) in your text editor to see SVG code in action.

There are a couple things to note when working with SVGs:
* It's extremely rare that developers will write out the coordinates from scratch. The large majority of SVGs are created in Sketch or Photoshop and exported as SVGs.
* There are sometimes inline styles used when working with SVGs. This may seem counter intuitive, but is common to see when working with SVGs.

*Note: SVGs are not supported in IE8 and below.*

Best uses for this image format: 2D shapes and icons (ex. cartoon graphics or illustrations) and animations. This is not an image format to be used with photos, despite the fact that SVGs can live within image elements.

## Styling SVGs
Styling SVGs with CSS is the same as for other HTML elements, however, there are CSS properties that are specific for SVG. The most common ones are:
* The `background` or `background-color` property becomes `fill` to change the colour of an SVG.
* The `border` property, becomes the `stroke` property.
* To add thickness, SVGs use the `stroke-width`, which can be done using pixels or a unitless number.

You can see the full of [list SVG properties by clicking here](http://www.w3.org/TR/SVG/propidx.html). 

It's important to note that styling SVGs will depend on how the SVG is being used and is interacting with the HTML. There are a couple ways to use SVGs:
* Inline SVGs
* Using an SVG as an image

## Inline SVGs
Because SVGs are based on XML, they can be added inline directly into an HTML document, making them inline SVGs. Inline SVGs also remove unnecessary HTTP requests. When defining images in an `<img>` tag, you are defining a file that the browser will *request*. This request will take up bandwidth and require time to download. Embedding SVGs inline cuts out the extra HTTP request, making your website faster.

Download, unzip and open up [using-SVGs--conEd.zip](https://hychalknotes.s3.amazonaws.com/using-SVGs--conEd.zip) to work with an inline SVG. Play around with the `stroke` and `fill` values both inline and using an internal style sheet.

Inline SVGs can be styled using inline styles or by using CSS. Keep in mind that inline styles are extremely hard to override, but are extremely common on SVGs and are an accepted method of styling in this case.

### Inline SVGs and accessibility
Inline SVGs can cause some issues for AT. To help avoid any issues, a few SVG-specific elements and attributes can be added in:
* The `role` attribute: On the `<svg>` opening tag, add a `role` attribute with the value of "img". This will allow the AT to interpret the SVG as an image.

```xml
<svg role="img">
    <title>Hippo in a bathtub</title>
    <!-- ...other svg elements -->
</svg>
```

* A `<title>` element: Gives the SVG a title that will show on hover. The `<title>` element has a closing tag and the content of the title goes in between the two tags. The element itself must be the title's parent element:

```xml
<svg role="img">
    <title>Hippo in a bathtub</title>
    <!-- ...other svg elements -->
</svg>
```
* A `<desc>` element: Allows for a description to be added to the svg element, similar to an `alt` attribute for images. It has a closing tag and the content of the description goes between the opening and the closing tags. 

```xml
<svg role="img">
    <title>Hippo in a bathtub</title>
    <desc>A green hippo sitting in a white bathtub smiling</desc>
    <!-- ...other svg elements -->
</svg>
```
* The `aria-labelledby` attribute: Helps connect relationships between elements. In this case, we would like AT to always associate the `<svg>` with its title and description, meaning the attribute should be included in the `<svg>` opening tag. To do this, give both the `<title>` and `<desc>` a unique ID and assign those IDs to the `aria-labelledby` attribute.

```xml
<svg role="img" aria-labelledby="hippoTitle hippoDesc">
    <title id="hippoTitle">Hippo in a bathtub</title>
    <desc id="hippoDesc">A green hippo sitting in a white bathtub smiling</desc>
    <!-- ...other svg elements -->
</svg>
```

## SVG as an `<img>`
SVGs can also be linked using an `<img>` element. Like other images, they should have a detailed `alt` description if one is necessary.

```html
<img href="myHorse.svg" alt="My horse, Moose, looking majestic in a field of flowers."
```

Unlike with inline SVGs, SVGs linked in this way cannot be styled using traditional external or internal style sheets, relying instead on inline styles in the SVG file itself.

### Finding & creating SVGs
SVGs can be created using vector graphics software such as Adobe Illustrator, [Sketch](https://www.sketchapp.com/) or a free online tool like [Draw Method](https://editor.method.ac/). There are also online resources such as [The Noun Project](http://thenounproject.com/) that have a wide variety of icons available for download.

But once we've found the perfect image to use, where do we actually get the SVG code?  We can simply open the SVG file in a text editor and there's the code.

#### Basic shape elements
SVG also contains the following set of basic shape elements:

* rectangles `<rect>`
* circles `<circle>`
* ellipses `<ellipse>`
* straight lines `<line>`
* polylines `<polyline>`
* polygons `<polygon>`

Each element has different attributes used to define various styles of the shapes.

```xml
    <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
        <rect x="10" y="30" height="100" width="100" style="stroke:#006600; fill: #cc0066;"/>
        <circle class="circle" cx="200" cy="80" r="30" fill="green"/>
        <line x1="300" y1="30" x2="300" y2="135" stroke="black" stroke-width="2"/>
    </svg>
```

<img src="https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-15%20at%2010.53.34%20AM.png">

The `x` and `y` attributes are used to determine the location of the rectangle, relative to the parent element's location. The `width` and `height` attributes determine the size of the rectangle. The style attribute can also be used to set inline CSS.

The location of the circle is determined by `cx` and `cy` and has a radius of `r`.

### Exercise
Download and open up [practicing-with-svgs--conEd.zip by clicking here](https://hychalknotes.s3.amazonaws.com/practicing-with-svgs--conEd.zip). The instructions are inside of the HTML file, and the answer key is included in the folder.

## Image optimization
It's important to use the correct image format and to optimize images properly. There are many factors to consider when using images in your projects:

* Use the appropriate file type based on what the image is being used for.
* Images should always be resized to the appropriate dimensions before using them in a web page.
* When saving images using an image editor such as Photoshop, use the "save for web" option.
* Try to keep your image file sizes as small as possible (up to 400KB as an absolute maximum).

Here are some handy tools:

* [TinyPNG](https://tinypng.com/)
* [Compressor.io](https://compressor.io/)
* [Image Optim](http://imageoptim.com/)
* [SVG Optimiser](http://petercollingridge.appspot.com/svg-optimiser)


## Resources
* [How to optimize images for the web](http://johnkuefler.com/how-to-optimize-images-for-the-web)
* [10 Must Know Image Optimization Tips](http://www.shopify.ca/blog/7412852-10-must-know-image-optimization-tips)
