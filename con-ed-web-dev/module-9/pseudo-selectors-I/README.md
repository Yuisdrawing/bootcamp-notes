# Pseudo Selectors

Elements have additional states that can be accessed with the usage of pseudo selectors. You'll also sometimes see them referred to as [pseudo classes](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes), but we'll be using the term _pseudo selectors_ throughout this course.

Pseudo selectors are accessible based on a number of factors like the location of a user's mouse (is it hovering over an element?) or how a user is interacting with an element (are they selecting/de-selecting a checkbox?) They are most commonly used on anchor elements to let users know the type of action happening on a given link.

All pseudo selectors append to existing selectors using a colon and utilize keywords to access a specific state:

```css
a:pseudoSelector {
  /* styles here */
}
```

There are many pseudo selectors available, but the most common ones are listed below.


## Hover

The `:hover` pseudo selector allows styles to be applied to an element when the user hovers over it with their mouse. It is most often used on anchor elements but can be applied to any element.

```css
a {
  color: blue;
}

a:hover {
  color: red;
} 
```

The above example sets all anchor elements to the colour blue, and allows them to turn red when they are hovered over.

> **Accessibility tip**
>
> Hovering over an element is only possible for users with a mouse. Users that use a keyboard to interact with a website would not be able to interact with elements that use hover alone.

## Focus
The focus state is available on elements when a user tabs to elements, using the `tab` key. Typically, the default focus state is a blue outline (as seen on Chrome) or dotted black outline around the element in focus (as seen on Firefox):

![](https://hychalknotes.s3.amazonaws.com/outline-google-example--conEd.png)

Note that focus relies on the `outline` property, which is specified the same way a `border` property is. The `outline` is not included in the box-model, and sits outside the border.

```css
a:focus {
  outline: 1px solid red;
  color: purple;
} 
```

The above example sets the focus state on anchor elements to have a 1px thick, solid red outline and changes the colour of the anchor element to purple.

> **Accessibility tip**
> 
> By default, there is an outline on certain elements when they are focused. There is a trend for people to remove this outline as it does not match the style of their site. However, removing the outline works against accessibility as this outline exists so that people using a keyboard to navigate can see where they currently are on a website. 
> To further help users, all elements that have a `:hover` effect should have the same effect applied to the `:focus` state as well. (WCAG Level A)

## Focus Within
The focus within state applies styles to an element that has received focus or has a child element that has received focus. In other words, the styles take effect when the element itself is in :focus, or if any of the element's children are in :focus.

```css
div:focus-within {
  background: darkcyan;
} 
```

```html
<div>
  <a href="#home">Home</a>
</div>
```

The above example sets the focus-within state on div elements if they have recieved focus or if children of the div elements have recieved focus to have a background of darkcyan.

This selector is especially useful when working with forms and lists.

## Active
The active state is shown when users are actively clicking on an element and is used on clickable elements like anchor elements. This state appears only while the element is being clicked and can be easily missed if a user clicks too fast.

```css
a:active {
  text-decoration: none;
  color: pink;
}
```

The above example removes the `text-decoration` on all anchor elements and turns them pink when clicked or when the user presses enter.

## Visited
The `:visited` pseudo selector allows styles to be applied to links that have already been visited by the user. Note that this pseudo selector is becoming less popular because there are limitations on how they can be styled for security reasons.

```css
a:visited {
  background-color: yellow;
}
```

The above example would allow anchor elements to have a background colour of yellow.

## Resources
* [Pseudo-selectors, MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes)
