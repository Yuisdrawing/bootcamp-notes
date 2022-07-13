# Developer tools

_Developer tools_ (or just "dev tools"), are the secret weapon of any web designer or developer. They help us look at any website "behind the screens" to see exactly what is being rendered and to preview what any changes will look like.

Every browser has its own set of dev tools - Firefox and Chrome have some of the most powerful. They are all a little different but all generally accomplish the same set of base actions. 

Firefox's dev tools are packed with tons of helpful tools for developing a website, one of which is being able to inspect our elements to see exactly what is happening on them. That means we no longer have to guess what is happening on our pages - we can take a look at what is being rendered using dev tools.


## Trying dev tools

Download and upzip [dev-tools-testing--conEd.zip](https://hychalknotes.s3.amazonaws.com/dev-tools-testing--conEd.zip) and open up the index.html file in your browser.

**[Note that the [placebear](https://placebear.com/) image placeholder service has gone down, so the above example file now uses [placekitten](https://placekitten.com/) instead. However, the screenshots in this lesson still display the example using bears, as it was previously and in memoriam. 🐻🐱]**

Right-click the page and select "inspect element". This brings up two panels:

![Screen shot of dev tools in Firefox open with a website in the background](https://hychalknotes.s3.amazonaws.com/dev-tools--conEd.png)

On the left side of the panel, you can see the markup from the website, and on the right, you can see the CSS that applies to elements on the website itself.

You can also open up your dev tools with the keyboard shortcut `command` (Mac)/`ctrl` (PC) + `shift` + `C`.


## Editing a selector

We can edit our selectors right inside dev tools to preview what a change might look like. Click the cursor within a square icon (in top left corner of the panel) and then click the `<h1>` that says "The Fishing Bear". 

![A screenshot of the Fishing Bear website, with a red error pointing to the selector icon in the dev tools](https://hychalknotes.s3.amazonaws.com/dev-tools-inspector-icon--conEd.png)

In the panel, you can now see the CSS associated with that given element.

![A screenshot of the Fishing Bear website, with a red border around the CSS details about the h1 element](https://hychalknotes.s3.amazonaws.com/dev-tools-css-panel--conEd.png)

The CSS can be manipulated using the dev tools by clicking directly into the CSS panel and typing. The CSS in the dev tools is the same as the CSS in your text editor - it follow the same syntax and requires the same property names.

Dev tools are extremely helpful for figuring out which styles are being applied to which elements as well as quickly testing new styles on existing elements. 

Moving forward, try to have dev tools open as you work to spot issues and bugs.

Note that the changes in your dev tools are not saved, and will be lost if you refresh your page!
