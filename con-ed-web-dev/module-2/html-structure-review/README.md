# HTML structure review

In HTML, we use elements to present our content and define structure. Elements are made up of tags that surround content. The closing tag has a `/` pre-pended to its name.

```html
<tagname>content goes in here</tagname>
```

Every HTML page must contain the following structure.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>Tony's Puppies</title>
  </head>
  <body>
    <p>I just love puppies!</p>
  </body>
</html>
```

The `<html>` element surrounds all of our content and contains our `<head>` and `<body>` elements.

The `head` element contains content like our `<title>` tag and links to other files that may need to be included, such as stylesheets and scripts.

The `body` element contains all of the markup for our page that humans will interact with.