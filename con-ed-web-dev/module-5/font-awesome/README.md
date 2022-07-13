# Font Awesome
Icon font libraries are an easy way to implement any number of icons easily into your website to help add visual cues for users. They allow developers to embed an icon "font" from a range of available icons within the given library, and manipulate size and colour using CSS, instead of having to download an image and change the size and colour in Photoshop.

[Font Awesome](https://fontawesome.com/) is one of the most popular libraries with a free option, but there are many available. If you haven't had a chance, please visit [Font Awesome by clicking here](https://fontawesome.com/start) and enter your email to start the sign up process.

![](https://hychalknotes.s3.amazonaws.com/fontawesome-signup--conEd.png)

Once you have an account, you will have access to the following page with a Font Awesome _kit_ created. This will allow us to use Font Awesome as a web font. 

![](https://hychalknotes.s3.amazonaws.com/fontawesome-kit--conEd.png)

In a similar way to linking to Google Fonts, Font Awesome must be linked into the `<head>` of your HTML file to make the icons available. The Font Awesome link should be placed in your `<head>` before your own style sheet.

Now that we have access to Font Awesome, create an HTML file called "using-font-awesome" and follow along with the directions below to add an icon.

Now an icon needs to be selected to be used on our page. The full gallery of options can be found at the [Font Awesome Gallery Page by clicking here](https://fontawesome.com/icons?d=gallery). 

If we select the Twitter icon, found [here](https://fontawesome.com/icons/twitter?style=brands), the below screen should appear. Copy and paste the available HTML in the top left and place it in the `<body>` of your HTML file.

![Screen shot of Font Awesome's Twitter Icon Screen](https://hychalknotes.s3.amazonaws.com/font-awesome-step2--conEd.png)

Notice that Font Awesome utilizes:
* The `<i>` element: While it used to mean "italic", it's intended to be used for "a span of text in an alternate voice or mood, or otherwise offset from the normal prose", which isn't used all that often in content, so Font Awesome has adopted it for it's brevity and default inline styling, creating a connection between "i" and the word "icon".
* The classes: "fab" and "fa-twitter" are some of the classes Font Awesome uses to bring in their icons. You can add classes to Font Awesome icons, but if you remove them the icon may not work.

Icon fonts can also be placed inside of other elements, like links:

```html
<a href="#">Buy now! <i class="fas fa-money-bill-alt buyNow"></i></a>
```

![](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-15%20at%2011.20.45%20AM.png)

Icons can be styled using CSS with the same properties that would be used on any typographical elements, like `font-size` and `color`:

```css
	i.buyNow {
		color: green;
		font-size: 50px;
	}
```

## Icons and accessibility 
Screen readers and other AT are able to read icons. Using the `aria-hidden` attribute, we can define which icons should be read out and which ones should be ignored by giving the attribute either a "true" or "false" value. 

If an icon is used for decorative purposes, we most likely do not want it to be read out by screen readers, so we will want to add `aria-hidden="true"` to the opening tag of the `<i>` element.

```html
<!-- Will not be read out by screen reader. The star is just a decorative element -->
<i class="fas fa-star" aria-hidden=“true”></i>
```

However, sometimes we do want icons to be read out by screen readers. If your icons have semantic meaning, Font Awesome recommends adding a few more things in the interest of accessibility:
* Adding `aria-hidden="true"` to the icon to hide it from screen readers
* Supplement it with a `<span>` that will hold the class of "sr-only". The `<span>` should include the text you would like the AT to read out loud but it will not be visible to sighted users. Font awesome deals the with the styling for "sr-only" class and will *visually* hide the span from users.

```html
<h2>From the AGO to Dumpling House:</h2>
<i class="fas fa-walking" aria-hidden="true"></i>
<span class="sr-only">Time by walking:</span>
<p>8 minutes</p>
<i class="fas fa-bicycle" aria-hidden="true"></i>
<span class="sr-only">Time by bike:</span>
<p>5 minute</p>
```
Which will render out:
![Example of semantic icons](https://hychalknotes.s3.amazonaws.com/icons.PNG)

The walking and bike icons have semantic meaning. We can convey what each one represents by creating the `<span>` with the class of "sr-only". This ensures that the icons are still accessible to users who do not visually benefit from icons.

Another way to make your icons accessible is with the `aria-label` attribute. This is great for interactive elements. For example, it is common to find sites that use icons to link users to their social media. Be sure to make these icons accessible, as you want people to know they serve a purpose and are clickable:

```html
<a href="https://www.instagram.com/learningcode" aria-label="Go to Canada Learning Code's Instagram page">
  <i aria-hidden="true" class="fab fa-instagram"></i>
</a>
```

# Resources
* [Font Awesome page on icon accessibility](https://fontawesome.com/how-to-use/on-the-web/other-topics/accessibility)
* [W3C's page on the `aria-hidden` attribute](https://www.w3.org/WAI/PF/aria/states_and_properties#aria-hidden)
