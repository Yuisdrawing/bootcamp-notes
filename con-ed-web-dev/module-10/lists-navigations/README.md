# Lists & navigations
It's very common to see lists being used as different navigations on a page.


## Drop-down navigation
A really useful part of building navigations with unordered lists is that we can create dropdown navigations with nothing but a few CSS rules, some clever positioning, and the :hover and :focus-within states.

Let's work through an example. Download and open [dropdown-navigation-codealong--conEd.html](https://hychalknotes.s3.amazonaws.com/dropdown-navigation-codealong--conEd.html) to see a basic navigation unordered list. Open up [the answer key here](https://hychalknotes.s3.amazonaws.com/dropdown-navigation-codealong-ANSWER--conEd.html) to see what the starter file will be turned into.

The assets are provided in the CSS as comments and some styles are already set up in the CSS.

Let's begin by adding a background image to our header, and styling it a bit.

```css
header {
    min-height: 100vh;
    background-image: url(https://hychalknotes.s3.amazonaws.com/camera-background.jpg);
    background-size: cover;
    background-position: center;
}
```

Our navigation is now harder to see! Let's add different colours to our main list and our nested lists so we can see where they are on the page.

```css
.main-menu {
    background: #fff;
}

.main-menu span {
    font-size: 10px;
    color: #D47642;
}

.main-menu li a {
    padding: 20px 30px;
    display: inline-block;
    color: black;
    text-decoration: none;
}

ul.sub-menu {
    background: #23322B;
}

ul.sub-menu li a {
    color: #fff;
}
```

Now let's make sure all the main menu items are next to each other, and are at the end of their main axis for that right-hand side look.

```css
.main-menu{
      display: flex;
      justify-content: flex-end;
}
```

Looking good!
To create our dropdown navigation we need to hide the submenus by default. The submenus do not appear unless they are in a hover or a focus-within state.

```css
ul.sub-menu {
    display: none;
}
```

How do we then show the submenus on hover or focus-within?

Here, we want to be able to style anything with a hover using focus-within, because this pseudo class activates when the element itself has received focus, as well as when any descendants of that element receives focus. We can use it here to create behaviours that would previously have been reliant on JavaScript.

Since we set the display property to none, we can switch that value to block on hover and focus-within.

```css
.main-menu li:hover ul.sub-menu,
.main-menu li:focus-within ul.sub-menu {
    display: block;
}
```

Now we should see a submenu when we hover or tab over its parent.

A new problem is that the submenu now pushes everything after it down. Why? Because we are using display: block;!

We want to position it so that it does not take up any extra space. It should "give up its seat". This is where we start to use position: relative and position: absolute.

We want the submenu to be absolute so that it doesn't take up any room within its parent, and we want the parent li to be relative so that we can base positioning off of that.

Adding left: 0 and right: 0 will ensure that the submenu will be the same size as the main menu li item.

```css
.main-menu li {
    position: relative;
}

ul.sub-menu {
    position: absolute;
    left: 0;
    right: 0;
}
```

Looking great! The functionality of the dropdown nav is done - just a few more hover and focus-within effects to add.

```css
.main-menu li:hover,
.main-menu li:focus-within {
    background-color: #829CA7;
}

ul.sub-menu li:hover,
ul.sub-menu li:focus-within {
    background-color: #829CA7;
}
```

Bam! With just that, we now have a fun and functional dropdown menu.

## Resources
* [:focus-within, MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus-within)