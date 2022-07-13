# Normalize & snippets
As we create more advanced code, we will need to make use of some tips and tricks to be more efficient.

## Normalize
An important tool that web designers and developers have in their tool belt is something called a CSS Normalize or a CSS Reset. This is a chunk of code developers use to help set up a base for their CSS.

In this course, we will be using CSS Normalize because not all browsers have the same default styling. All browsers come with style defaults, such as making all h1-h6 elements escalate in size and adding padding and margins to various elements. Though you may want to keep the default styles, they aren't consistent across all browsers. This can lead to problems down the road if your website does not look consistent across all browsers.

CSS Normalize fixes the issues found across browser defaults. It's a piece of CSS code, written and maintained by a developer who has openly shared their work, that we can either insert into the top of our CSS, or add as a separate stylesheet in the `<head>` of our HTML document.

When using Normalize, keep in mind the CSS Cascade: Normalize should always come at the top of your CSS because it's likely that you will apply custom styles that need to override Normalize. 

Triple click the snippet below to select all and copy CSS Normalize:

```css
html{line-height:1.15;-ms-text-size-adjust:100%;-webkit-text-size-adjust:100%}body{margin:0}article,aside,footer,header,nav,section{display:block}h1{font-size:2em;margin:.67em 0}figcaption,figure,main{display:block}figure{margin:1em 40px}hr{box-sizing:content-box;height:0;overflow:visible}pre{font-family:monospace,monospace;font-size:1em}a{background-color:transparent;-webkit-text-decoration-skip:objects}abbr[title]{border-bottom:none;text-decoration:underline;text-decoration:underline dotted}b,strong{font-weight:inherit}b,strong{font-weight:bolder}code,kbd,samp{font-family:monospace,monospace;font-size:1em}dfn{font-style:italic}mark{background-color:#ff0;color:#000}small{font-size:80%}sub,sup{font-size:75%;line-height:0;position:relative;vertical-align:baseline}sub{bottom:-.25em}sup{top:-.5em}audio,video{display:inline-block}audio:not([controls]){display:none;height:0}img{border-style:none}svg:not(:root){overflow:hidden}button,input,optgroup,select,textarea{font-family:sans-serif;font-size:100%;line-height:1.15;margin:0}button,input{overflow:visible}button,select{text-transform:none}button,html [type=button],[type=reset],[type=submit]{-webkit-appearance:button}button::-moz-focus-inner,[type=button]::-moz-focus-inner,[type=reset]::-moz-focus-inner,[type=submit]::-moz-focus-inner{border-style:none;padding:0}button:-moz-focusring,[type=button]:-moz-focusring,[type=reset]:-moz-focusring,[type=submit]:-moz-focusring{outline:1px dotted ButtonText}fieldset{padding:.35em .75em .625em}legend{box-sizing:border-box;color:inherit;display:table;max-width:100%;padding:0;white-space:normal}progress{display:inline-block;vertical-align:baseline}textarea{overflow:auto}[type=checkbox],[type=radio]{box-sizing:border-box;padding:0}[type=number]::-webkit-inner-spin-button,[type=number]::-webkit-outer-spin-button{height:auto}[type=search]{-webkit-appearance:textfield;outline-offset:-2px}[type=search]::-webkit-search-cancel-button,[type=search]::-webkit-search-decoration{-webkit-appearance:none}::-webkit-file-upload-button{-webkit-appearance:button;font:inherit}details,menu{display:block}summary{display:list-item}canvas{display:inline-block}template{display:none}[hidden]{display:none}
```
Don't be intimidated by the size of the chunk of code! You will never be expected to write it out on your own. Once you set it at the top of your CSS, you will write your own CSS below.

You can also download Normalize.css at [http://necolas.github.com/normalize.css/](https://necolas.github.io/normalize.css/).

Normalize, like `box-sizing: border-box` should be used on all of your websites.

## Snippets
One of the powerful features of text editors is the use of snippets. Snippets allow developers to use keywords to call up larger blocks of code that are tedious to type up time and time again, like `box-sizing:border-box` and CSS Normalize. 

Snippets are made up of a language called JSON, which stands for JavaScript Object Notation. JSON is a common language for writing data. With the help of snippets, we'll be able to type a couple words to bring up all the things we need to get our files started!

Download this [snippets file](./resources/snippets.json?raw=true) file to get started. 

Go to:

`Code > Preferences > User Snippets` for Mac 

`File > Preferences > User Snippets` for PC

A drop down should come up. Click on "New Global Snippets File..." option.

![Screen shot of the drop down opened on VS Code](https://hychalknotes.s3.amazonaws.com/snippetsVSCodeHowTo1--conEd.png)

This will allow you to name your snippet file. 

![Screen shot of the screen when the snippets window is open](https://hychalknotes.s3.amazonaws.com/snippetsVSCodeHowToNamingFile--conEd.png)

Name the file "personal" - which will result in the file name "personal.code-snippets" - and press enter. It will automatically open up in VS Code. Delete all of the content in that file.

Copy the JSON from the snippets file that was downloaded earlier and paste it in the "personal.code-snippets" file. Once you save the file, your snippets are ready to use.

### Using snippets
Within `<style></style>` tags in the head of an HTML file or in a CSS file, type the following commands, and then press `tab` to have the code written to your page

* `normalize` -> A minified version of normalized (the white space is removed).
* `borbox` -> Code to add border-box to the entire page.
* `sr-only` -> Code to add the sr-only class, to help add text for non-sighted users.
* `setup` -> The three above snippets combined into one command.

We also brought over some other snippets that we won't use just yet, but will come in handy later on.

## Resources 
* Make your own snippets with this handy [snippet generator](https://snippet-generator.app/)
