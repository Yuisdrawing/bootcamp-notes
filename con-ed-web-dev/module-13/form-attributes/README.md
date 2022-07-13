# Form attributes

As the last section showed us, forms and attributes have a special relationship. There are even more unique attributes available that can help give the inputs more interactivity and usability. Any form or input can have multiple attributes that help us achieve different features.


## Placeholder

The `placeholder` attribute allows developers to set text in the content area of an input when it is empty. Whatever value the `placeholder` attribute is given clears when the user starts typing.

Placeholder text is a useful way to give users a hint for what should actually go inside the input, but **placeholders are not a replacement for labels**. This is because placeholders:
* Are not visible to AT, so using them instead of labels makes forms not meet accessibility standards (more on this below).
* Disappear when users start typing in them.

```html
<form action="#" method="#" class="myForm" name="myForm">

  <label for="userEmail">Provide your email address</label>
  <input type="email" id="userEmail" name="emailAddress" placeholder="unruly.cat@cmail.com">

</form>
```
![](https://hychalknotes.s3.amazonaws.com/placeholder--conEd.png)

> **Accessibility tip**
>
> It is common to see designs where labels are omitted for form elements, and placeholders are used instead. This is problematic as placeholders are not accessible. If you are given a design that does not include labels, you can instead use *visually hidden labels*, using a `sr-only` CSS class (you can find the CSS for this easily on google, and we've given it to you in your [setup snippet](https://github.com/HackerYou/con-ed-web-dev/tree/main/module-5/snippets#snippets)). Labels with one of these classes (and the associated CSS) do not visibly appear on the page but are still announced by screen readers.
> 
> In the below example, the label will appear off the screen, but still be read out by AT because the element will remain in the DOM.
> 
> ```html
> <form action="#" method="#" class="myForm" name="myForm">
> 
>   <label for="userEmail" class="sr-only">Provide your email address</label>
>   <input type="email" id="userEmail" name="emailAddress" placeholder="unruly.cat@cmail.com">
> 
> </form>
> ```
> 
> Note that using visibility-hidden or display-none will prevent AT from reading the content.


## Required

The `required` attribute allows developers to make an input mandatory, meaning a user cannot submit a form if that input is not completed.

It can be passed into inputs by adding the `required` attribute with a value of `true`, or by using the keyword `required`. Once applied to an input, the browser validates the input, checking to see if it has been filled out by the user before sending the information to the server. Before this attribute became available, this was only possible using JavaScript!

```html
<form action="#" method="#" class="myForm" name="myForm">

  <label for="firstName">Your first name:</label>
  <input type="text" id="firstName" name="firstName" required>
  <!-- OR -->
  <!-- <input type="text" id="firstName" name="firstName" required="true"> -->
  
  <button type="submit">Submit</button>

</form>
```
![](https://hychalknotes.s3.amazonaws.com/required--conEd.png)


## Resources
* [Using the aria-describedby attribute](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-describedby_attribute)
