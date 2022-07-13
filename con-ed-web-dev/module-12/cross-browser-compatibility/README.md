# Cross-browser compatibility
In this course, we primarily use Firefox. It's important to understand the issues that can arise when working with different browsers. While all browsers have agreed on some concepts, such as the `<!DOCTYPE>` at the start of your HTML or that block and inline elements will behave in specific ways, there are actually few other concepts they have chosen to support and interpret in a similar way. This means that while we can expect flexbox properties to work on some browsers, they may not work on another the same way.

Why did browsers choose to take this approach to supporting different features? The simple answer is: because they are all trying to be unique and some pride themselves on being "on the cutting edge" (Firefox, Chrome) while others have taken another path (Internet Explorer).

```html
¯\_(ツ)_/¯ 
```

As developers, it's important that we plan ahead and understand how issues can arise and how to resolve them.

## Main browsers
There are five main browsers that developers should consider:
* Chrome
* Firefox
* Safari
* Internet Explorer/Edge
* Opera

Chrome, Firefox, Edge and Opera are evergreen browsers, meaning they update themselves automatically. Internet Explorer and Safari are not. 

The popularity of each browser is dependant on the project and the target audience. 

### Browser versions
Keep in mind that each browser also has different versions, meaning that some versions may support one feature while another may not.

As an industry standard, all evergreen browsers only need to be tested in their current version. 

For non-evergreen browsers:
* Safari: While it is pretty aggressive about updating, check support on the last two versions.
* Internet Explorer: Unfortunately, this browser is a pain for most developers as many modern CSS properties are not supported by it. Microsoft has recently announced they will be discontinuing support for IE 11. However IE is still being used in many areas, this is especially the case for larger organizations like major banks and governmental agencies. If your client uses an older version of IE, it is your job as a developer to support it. In all other cases, developers should support back to IE11.

As a general industry standard, if you're catering to a modern audience in most urban centers, you may be okay supporting the latest version. When in doubt, look at analytics data on what browsers site visitors are actually using via tools like Google Analytics. 

## The four Ws
It's easy to fall into the trap of never ending testing. Before you start working on your website, it's important to understand what demographics your website is targeted towards.

Ask yourself the 4 Ws when consider how you will approach testing your website:
* Where: Where do the users live that the website is targeting? Different regions will have higher rates of usage for certain browsers.

    StatCounter has a great map and stats that you can target by date range and region that can be [found by clicking here](http://gs.statcounter.com/browser-market-share/desktop-tablet-console/worldwide#monthly-201901-201906-map).
    
    In 2019, Chrome was the most widely used browser internationally. Each region has their own most used browsers, and the top three should be tested. Also keep in mind that those in more remote areas may have slower internet connections and that should be considered when testing.

* Who: Who is the website primarily targeted towards? The age range of the target demographic of your website should affect how you approach testing.

* What: What type of website are you building? Will it have a lot of graphics included? Will it need a fast internet speed to work properly? If so, does that match the "who" and "where" demographics?

* When: How long will your website be up? Will it be updated often or will it not be checked on for a couple months or years? If the website isn't going to be checked on often, ensure the code is future proofed with code that isn't in the experimental phase or hasn't been rendered obsolete (for example, `<center>` is no longer a valid tag in HTML5 and all centered items should be centered with CSS only).

If you are working on a project for a client or other stake-holders it's important to gather information about which browsers they need you to support. The scope of the work can be greatly affected by this. You'll need to account for cross-browser testing time as well as time to fix any bugs that are discovered in this testing process. It's also important to consider which operating systems are being supported. Browsers may behave differently on a mac vs a windows machine.

## CanIUse
[CanIUse.com](https://caniuse.com/) is a website that allows developers to check which properties are supported, and to what extent, on different browsers and their different versions. It also provides developers with useful insight about known bugs and issues on certain browsers when using specific properties. Web development moves extremely quickly and CanIUse is especially useful when trying out new properties.

For example, when looking up `position: sticky` on [CanIUse](https://caniuse.com/), the following table will come up: 

![Screenshot from the website CanIUse, showing the support for "position: sticky"](https://hychalknotes.s3.amazonaws.com/canIUse--conEd.png)

You can also see the [table live by clicking here](https://caniuse.com/#feat=css-sticky).

This table displays the support per browser and version using colours:
* A red background means there is extremely limited or no support.
* A yellow background means there is partial support.
* A green background means that there is enough support that you can feel comfortable using it.

It also provides information about known issues and bugs. For example, the last three versions of Chrome and Edge as well as Opera have partial support because `position: sticky` will not work when used in a `<thead>`, the table head element, or `<tr>`, the table row element. If our websites do not use tables, this issue isn't a concern at all. CanIUse also shows IE with a red background, meaning there is no support for `position: sticky`, which should be considered if the target audience are large users of IE.

Try looking up "CSS Filters" and "Flexbox" on CanIUse to learn about the support offered by each browser. 

Web development moves really fast. There will be new properties introduced in the CSS specifications in the future. So it's important for us to know which browsers have fully supported these properties and techniques before using them in our projects.

## Vendor prefixes
Vendor prefixes, also known as browser prefixes, help browsers give extra support to new CSS features. They became extremely popular when CSS3 came out, when a ton a new properties became available and browsers wanted to experiment with how they would implement the properties. Vendor prefixes cannot give support to properties that have no support, but add browser-specific support to certain properties that a browser is experimenting with.

Browser manufacturers each have their own vendor prefix that is pre-pended before the CSS property:
* Chrome, Safari: -webkit-
* Firefox: -moz-
* Internet Explorer: -ms-
* Opera: -o-

For example, `border-radius` was introduced with CSS3. While browsers were working on testing out what the property would look like on each of their products, developers would set `border-radius` like so:

```css
div {
    -moz-border-radius: 3px;
    -webkit-border-radius: 3px;
    -o-border-radius: 3px;
    -ms-border-radius: 3px;
    border-radius: 3px; 
}
```

Eventually, when full support was reached on new properties, developers could drop the prefixes and just use `border-radius` the way we do now:

```css
div {
    border-radius: 3px; 
}
```

When working with any new property, check CanIUse to see if a prefix is needed to ensure the property can run properly. CCS3 has been out for a while now, meaning prefixes are less common to see but are still used and important to understand.

## Tools
There are multiple tools developers can use to test their website across browsers and versions. 

* [Browser Stack](http://www.browserstack.com/): Provides live testing across multiple browsers and mobile devices. *Lets you test on Edge for free!*
* [Browser Shots](http://browsershots.org/): Gives you screenshots in many different types of browsers.
* [Virtual Box](https://www.virtualbox.org/): Regardless of PC/MAC/Linux, you can run a copy of windows right inside of your operating system. Microsoft knows the pain of testing on multiple versions of IE, so they have provided images of windows with different versions of IE loaded onto them. You can download them at [https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/](https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/). These are huge downloads, so plan to do so on a stable internet connection. To run them, you need a free program called Virtual Box — [https://www.virtualbox.org/](https://www.virtualbox.org/).

Don't forget, it's not possible for a website to look exactly the same across all browsers. Some inconsistencies will exist but it is the developers job to check for any of the following:
* Is the layout breaking?
* Is the design notably different to the point where the user has a dramatically less positive experience on one browser more than another?

 For more information visit [dowebsitesneedtolookexactlythesameineverybrowser.com/](http://dowebsitesneedtolookexactlythesameineverybrowser.com/)

# Resources
* [The Secrets of 'Can I Use' by Jen Simmons](https://www.youtube.com/watch?v=WM_cKHH7bZ0)
* [CSS2 vs CSS3](https://www.lifewire.com/css2-vs-css3-3466978)





