# Setting up an HTML file

Let's start our own HTML file from scratch!

Open up VS Code and press

`command` + `N` for Mac

`ctrl` + `N` for PC

to open a new file or you can go to File > New File in the top left of your text editor. Save the file as "typographic-elements.html" by either pressing

`command` + `S` for Mac

`ctrl` + `S` for PC

or you can go to File > Save in the top left of your text editor.

Saving the file with ".html" lets our text editor know that we will be working in an HTML file. You should now see HTML at the bottom of your text editor.

![screen shot of VSCode with a arrow pointing in the bottom right corner at the word "HTML"](https://hychalknotes.s3.amazonaws.com/VSCode-screenshot.jpg)

Conventionally, the HTML file for a website will be named `index.html`. This isn't a rule we always need to follow when we're creating examples or using our exercises but it will be best practice when you are making a website to be accessible by a live URL.

Now that our HTML file is ready to use, in the body section of your HTML type `!`, then hit the 'tab' button. You should get a full HTML skeleton!

![Screen shot of VSCode with base HTML skeleton shown](https://hychalknotes.s3.amazonaws.com/VSCode-screenshot-html.jpg)

There are some new meta tags in our `<head>`:

* `<meta charset="UTF-8">` specifies the kind of encoding we want for our page to prevent our content from being interpreted incorrectly. This is not something we will dive into in this course, but you can read more about HTML encoding [here](https://www.w3.org/International/questions/qa-html-encoding-declarations)
* `<meta name="viewport" content="width=device-width, initial-scale=1.0">` gives our pages the ability to resize given the size of the page. In this case, the meta tag is setting the content width to the width of the device that we are currently on, and has a default zoom of 1.0. This does not make our page responsive automatically, but without it, the code that makes our page responsive will not work.

