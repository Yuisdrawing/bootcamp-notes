# Favicons
Favicons are those little images that show up on your browser's tabs. They are usually logos representing their respective websites and they help users to work quickly through tabs or identify websites saved in their bookmarks. 

![Screen shot with a red arrow pointing to the Github favicon](https://hychalknotes.s3.amazonaws.com/favicon-example--conEd.png)

In the example above, the red arrow is pointing to the Github favicon, which is also the Github logo. There are also other favicons, including Gmail, Trello, and Xero. 

To set a favicon, add a `<link>` element in the `<head>`, with the `type` attribute of "image/IMAGETYPE", an `href` attribute linking to a png or ico image format and a `rel` attribute set to "icon". 

The .ico image format is used for icons because it was made popular by Microsoft. Microsoft was the first company to use bookmarks with images and, as a result, their format became very popular and is still used today. 

```html
<link type="image/png" href="images/favicon.png" rel="icon">
```

As a best practice, favicons should use a relative link instead of an absolute link. This ensures the image will always be available. 

Regardless of how large the png or ico image is, the browser will display it at 16x16 pixels. But, it's not a bad idea to make the image a little larger (32x32 or 48x48) as some devices are starting to use the favicon for larger bookmarking purposes. Regardless of which size you choose, the image must be kept a square.

## Exercise
Try setting up a favicon by [downloading an example by clicking here](https://hychalknotes.s3.amazonaws.com/favicon-fun--conEd.zip) and opening it up in VSCode. There is a favicon ready for you to use in the images folder. The answer key can be [found by clicking here](https://hychalknotes.s3.amazonaws.com/favicon-fun-ANSWER--conEd.zip). 

## Resources
* [Favicon generator](https://favicon.io/)