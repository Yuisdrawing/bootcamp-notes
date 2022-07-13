# Styling forms

HTML forms were created before CSS, and as a result many users became used to certain patterns associated with forms. Browsers, in one of the few cases of uniformity across platforms, agreed to keep some of the key patterns and looks associated to forms to ensure smooth user experiences.


## General styling

Most form elements, including `<form>`, `<input>` elements, and `<label>` can be styled like any other HTML elements; they can be targeted normally in CSS, using classes, element selectors, etc:

```html
<form action="#" method="#" class="myForm" name="myForm">

  <div>
    <label for="userName">Name here:</label>
    <input type="text" id="userName" name="userName" required>
  </div>

  <div>
    <label for="userPassword">Password here:</label>
    <input type="password" id="userPassword" name="userPassword" required>
  </div>

  <button type="submit">Submit</button>

</form>
```

```css
.myForm {
  border: 1px solid black;
  width: 500px;
  padding: 10px;
  text-align: center;
}

input {
  width: 90%;
  border: 2px solid black;
  border-radius: 6px;
}

label {
  font-weight: bold;
}

div {
  margin-bottom: 10px;
}

button {
  background: black;
  color: white;
  padding: 5px;
  border: none;
}
```

![](https://hychalknotes.s3.amazonaws.com/form-styling-one--conEd.png)

Inputs can also be selected in CSS by specifying the input type:

```css
input[type="text"] {
  border: 2px solid blue;
}
```

An effectively styled form can often only require some thoughtful considerations around `margin`, `padding` `border` and incorporating focus and hover states. 

## Difficult to style form elements

Some form elements are either extremely difficult to style, or cannot be styled. Those that cannot be styled include color inputs, and the warning messages that comes up on failed form validation (ie. because of the `required` attribute, etc.).

### Checkbox and radio inputs

Checkbox and radio inputs can be styled, but it takes more effort.

First, the checkbox or radio buttons have to be stripped of their browser default styles. The best way to do this with form elements is to use the CSS property `appearance: none;`.

In the below example, `appearance: none;` has been set, so the checkboxes will disappear from view. _Vendor prefixes_ are used for the `appearance` property to ensure it is effective on all browsers.

```html
<form action="#" method="#" class="myForm" name="colorForm">

  <label for="pinkColor">Pink</label>
  <input type="checkbox" name="candyColorChoice" value="pink" id="pinkColor">

  <label for="yellowColor">Yellow</label>
  <input type="checkbox" name="candyColorChoice" value="yellow" id="yellowColor">

  <label for="greenColor">Green</label>
  <input type="checkbox" name="candyColorChoice" value="green" id="greenColor">

</form>
```

```css
form {
  width: 400px;
  display: flex;
  align-items: center;
}

input[type=checkbox] {
  -webkit-appearance:none;
  -moz-appearance:none;
  appearance:none;
}
```
![](https://hychalknotes.s3.amazonaws.com/checkboxes-appearence--conEd.png)

Next, new styles need to be given to the checkboxes so they are visible again.

```css
input[type=checkbox] {
  -webkit-appearance:none;
  -moz-appearance:none;
  appearance:none;
  border: 1px solid red;
  height: 12px;
  width: 12px;
  display: block;
  border-radius: 2px;
  margin: 0 10px;
}
```

![](https://hychalknotes.s3.amazonaws.com/checkboxes-styled-checkbox--conEd.png)

The checkboxes now appear, but have no behavior when clicked/checked. Like attributes, forms have their own unique pseudo selectors as well. For CSS to understand if we have "checked" or "unchecked" the checkbox or radio button, we can utilize the `:checked` and `:unchecked` pseudo selectors. Note that `:checked` and `:unchecked` are only available on radio and checkbox inputs.

Both selectors allow the CSS to apply styles if the checkbox or radio input is "checked" or "unchecked".

Below, a `:checked` pseudo selector is selecting only checkbox inputs which are checked, and applying a `::before` element:

```css
input[type=checkbox]:checked::before {
  content: '✚';
  color: #ff5a5f;
  display: block;
  font-size: 10px;
  line-height: 12px;
}
```

![](https://hychalknotes.s3.amazonaws.com/checkboxes-styled-checked--conEd.png)



### Select

The `<select>` and `<option>` elements are notoriously difficult to style. It is nearly impossible to expect consistent results across browsers when attempting to style them. So much so that the Mozilla Developer Network called it "a nightmare".

![](https://hychalknotes.s3.amazonaws.com/select-nightmare--conEd.png)

## Placeholder pseudo-element

Placeholders by default are not able to be styled, but as a work-around, browsers have created a pseudo-element that allows developers to control most aspects of placeholders.

```html
<form action="#" method="#" class="myForm" name="myForm">

  <label for="userName">Username:</label>
  <input type="text" id="userName" name="userName" required placeholder="type here">

  <button type="submit">Submit!</button>

</form>
```

```css
input[type="text"]::placeholder {
  color: green;
  letter-spacing: 2px;
}
```

![](https://hychalknotes.s3.amazonaws.com/placeholder-styled--conEd.png)


## Exercise

Download [form-styling.zip](../../exercises/form-styling.zip?raw=true) to style the existing form.

Open up the answer key in the browser for reference, play around with the form to check out some detailed stylings. The assets for styling the form (colors, font-sizes, etc) are provided in the CSS file.

## Resources
* [Styling forms, MDN](https://developer.mozilla.org/en-US/docs/Learn/HTML/Forms/Styling_HTML_forms)




