# Fonts
A font is a set of characters that have been paired together by a designer or other typographical stylist and match in look and feel. In web development, we have a range of fonts to choose from to create personalized designs for our websites and a couple ways in which we can choose to bring those fonts into our projects.

## Font family
`font-family: <font family name>;`

The `font-family` property allows developers to set the font on typographical elements. The property accepts font names that are either passed to the browser via an external font, or that are already available on the system. The browser font default for typographical elements is typically a serif font such as "Times New Roman" and is inherited by child typographical elements when set on a parent. 

It's very common to see `font-family` set on the `<body>` element because it allows the font family to be set in one place and then inherited by the entire page.

The `font-family` property can be set using two different methods:

1. Using the font family name, which goes in quotes:

```css
body {
  font-family: "Helvetica";
}
```

This method implies (and hopes!) that the user has that specific font available on their system.

2. Using a generic name, which does not need to go in quotes:

```css
body {
  font-family: sans-serif;
}
```

With a generic name, you let the browser/system supply the best font from what is available.

In the case of "sans-serif" a Windows computer will deliver "Arial" while a Mac will deliver "Helvetica". These are different fonts with the same base of "sans-serif".

Available generic names are:

* 'serif' (e.g., Times)
* 'sans-serif' (e.g., Helvetica)
* 'cursive' (e.g., Zapf-Chancery)
* 'fantasy' (e.g., Papyrus)
* 'monospace' (e.g., Courier)
* 'math' (this is used to show mathematical equations, etc.)

## Font stacks
A font stack is a list of font families that are listed in order of preference that reads from left to right. If the first font family listed isn't available, the font stack will move onto the second, and so on. Font stacks provide fall-backs and help ensure that our websites will render a font-family that we are happy with.

Let's say we have a special font called "Montserrat" that we have downloaded. The below code would set the font on the entire body of our HTML file.

```css
body {
  font-family: 'Montserrat';
}
```

When other users who have this font available visit the website, they would also experience the font "Montserrat", but users who do not have the font available would experience the website in the browser default, "Arial" (or another "sans-serif" font) to compensate.

To prevent this, we set font stacks to supply a list of desired fonts for the browser to fall back on as a fail-safe:

```css
body {
  font-family: 'lobster', 'wedding', cursive;
}
```

The above code above checks for font "lobster" first. If it isn't found, it then checks for "wedding" and if that isn't found, it defaults to a whatever cursive font is available.

An excellent resource for building a fail-proof font stacks is [http://cssfontstack.com/](http://cssfontstack.com/).

## Web fonts

Web fonts allow us to find fonts on the internet and link them into our stylesheets, making them fast and easy to use. Prior to the advent of web fonts, developers were limited to using font stacks that were "websafe", meaning a good percentage of users would have at least one of them installed. This was extremely limiting because there simply aren't that many to choose from, resulting in limited design options. 

There are various ways to use web fonts but we will be using the free option of [Google Web Fonts](http://www.google.com/webfonts).

### Using Google web font

Open up [web-fonts--conEd.html](https://hychalknotes.s3.amazonaws.com/web-fonts--conEd.html) to follow along. There are some fonts being used already in the document so you can see them in action!

* Head on over to [Google Web Fonts](http://www.google.com/webfonts) and find a font you like.

    ![](https://hychalknotes.s3.amazonaws.com/GoogleFontsImage1.png)
    
* Click on the font (in this example we will click on the first one, Roboto).

* Choose the weights that you wish to use by clicking on "+ Select this style". Weights will dictate the `font-weights` available to you. Not all fonts have a range of weights available. 

    ![](https://hychalknotes.s3.amazonaws.com/GoogleFontsImage2.png)
   
Note that the more fonts and the more weights you add to a page, the slower your page will load. As rule of thumb, try not to include more that 3-4 fonts/weights in production code.

* Some fonts have extended character sets available, making them a better option if your website will be in a language such as Russian or Vietnamese.

 ![](https://hychalknotes.s3.amazonaws.com/GoogleFontsImage3.png)

* Copy the code provided under "Use on the web" .

* Paste that line of code into the `<head>` of your document before your linked external stylesheet. This is to ensure that our styles have the "final word" on any styles coming in, because the CSS will override any unwanted styles coming in from Google Fonts.

* You can now use the value of the font name in your `font-family` stack, just as you would any other font. Google will recommend a good font-stack for you to use:

```css
body { 
  font-family: 'Roboto', sans-serif; 
}
```

> **Accessibility tip**
>
> There are a lot of really cool fonts around the web but try to keep in mind the legibility of your font. If the letters are small, can users with different needs read them?





