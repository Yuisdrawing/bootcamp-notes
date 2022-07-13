# Text editor customization

Text editors come with a lot right out of the box, but we can use extensions and settings to customize VS Code in a number of ways to suit our personal tastes and needs. We saw an example of this when we downloaded the open-in-browser extension on the first day of class.


## Themes

By default, VS Code uses a dark theme that we have all been using. We can change the theme, which is a type of extension, at any time to make our editors match **who we are inside**. 

There are some ready for us to choose from in VS Code without having to download them.

Go to:

`File > Preferences > Color Theme` on a PC

`Code > Preferences > Color Theme` on a Mac, or use the shortcut `Command + K` + `T`.

This will bring up a drop down list of built in themes installed on VSCode, along with any you may have previously downloaded.

Move up and down with your cursor to preview what the themes look like and if you find one you like, either click on it or press enter to make it your new colour theme. 

If you want a new colour theme that isn’t listed, there are hundreds of free options to choose from in the VS Code Marketplace. You can get to the VS Code Marketplace by clicking on the Extension button on the left side of your editor.

![Screen shot of the extensions marketplace icon](https://hychalknotes.s3.amazonaws.com/vscode-extension.png)

Once you’re there, type “theme” into the search bar. 

A ton of different themes will come up! We can practice setting up a theme together, by choosing the "Night Owl" theme by Sarah Drasner, or another one that you prefer! To install, click on the install button on the theme extension page.

![Screen shot of the "Night Owl" theme in VS Code](https://hychalknotes.s3.amazonaws.com/night-owl.png)

Once you download it, the colour theme pickers will drop down. Choose "Night Owl". Now your editor is using the Night Owl theme.

To change it to another colour theme that you have either already downloaded or already exists on your editor, head back into the colour theme picker by going to:

`File > Preferences > Color Theme` on a PC

`Code > Preferences > Color Theme` on a Mac or use the shortcut `Command + K` + `T`.  

There are a lot of different themes to choose from! Check out [this VSCode theme site](https://vscodethemes.com/) to see examples of some of the more popular ones.


## Extensions

Let’s explore some other extensions that help make the text editor even easier to use. The best part about most extensions is that you don’t need to turn them on - once you download them, they’re enabled right away.

Go into the extension finder, where we previously searched for the "Night Owl" theme, and we can download the following extension using the search bar:

* Indent-Rainbow:
This will help keep track of indentations in the most colourful way possible! To install it, click the install button like we did in our colour theme and the extension will be enabled immediately. 

There are plenty of other helpful extensions out there! Here's one list of [22 best Visual Studio Code extensions for web development](https://scotch.io/bar-talk/22-best-visual-studio-code-extensions-for-web-development), but a quick Google search will bring up lots of helpful extensions that other developers use!

## Settings

The base settings in your text editors can be changed to further customize your coding experience.

Access your settings by going to:

File > Preferences > Settings, or use the shortcut `ctrl` + `,` on a PC

Code > Preferences > Settings, or use the shortcut `command` + `,`  on a Mac

This is where all of the settings live! There are hundreds to go through but for now let’s look at some popular settings. 

We’re going to be using the search bar at the top of the settings to find each of the individual settings.

![Screen shot of VS Code's Setting's screen with a red arrow pointing to the search bar.](https://hychalknotes.s3.amazonaws.com/settingSearch-newIcon--conEd.png)

Font Size: Search “Font Size” in the settings search bar.

This will change the pixel size of the font in our text editor. You can make yours larger or smaller depending on your personal preferences.

![Screen shot of VS Code's Setting's screen with a red arrow pointing to the heading "Editor: Font Size"](https://hychalknotes.s3.amazonaws.com/fontSizeSettings-newIcon--conEd.png)

You can change anything from the font to how your text wraps in your editor! Feel free to browse through some of the settings you have access to. 

## Emmet

Now that we're comfortable with the syntax of HTML and CSS, we can leverage some tools to code faster and more efficiently. One of the most popular tools in the industry is [Emmet](http://emmet.io/), and it can help us build code quicker, and more effectively.

Luckily, Emmet comes pre-installed in VS Code.

### Emmet & HTML

Here are a few common Emmet shortcuts:

* `[element]` + `tab` creates that element and puts your cursor inside:
  * `span` + `tab` → `<span></span>`

* `[element.className]` + `tab` or `[element#idName]` + `tab` creates that element with the associated class or ID. If you were to leave out the `[element]` and just use the `#idName` or `.className`, VSCode will default to a `div`:
  * `div.goodDay` + `tab` → `<div class="goodDay"></div>`
  * `section#contact` + `tab` → `<section id="contact"></section>`
  * `.gallery` + `tab` → `<div class="gallery"></div>`

* `[element>childElement]` + `tab` creates nested elements
  * `ul>li` + `tab` → `<ul><li></li></ul>`

* `[element*5]` + `tab` creates the specified number elements of that kind
  * `span*2` + `tab` → `<span></span><span></span>`
  * `p.hello*2` + `tab` → `<p class="hello"></p><p class="hello"></p>`

All the above can be mixed and matched! Try pasting this in your editor:
* `ul.list.list-number-$*2>li.item.item$*2>h2{intense}+p>span{woah}`

### Emmet & CSS
When in CSS, you can usually just type the first few letters of what you want, and Emmet will figure out what you were looking for. Try some of the following:

* `posrel` →  `position: relative;`
* `posab` →  `position: absolute;`
* `c` →  `color: #`
* `w` →  `width: `
* `p` →  `padding: `

For a full list of all the shortcuts, check out the [Emmet cheatsheet](http://docs.emmet.io/cheat-sheet/)
