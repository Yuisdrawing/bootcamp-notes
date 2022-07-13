# Form elements

The `<form>` element wraps all forms. It is a semantic, block-level element that has both an opening and closing tag - `<form></form>`.

The opening `form` tag can take a number of attributes, some of which are required to give it the ability to communicate with a server:

```html
<form action="sendEmail.php" method="POST" class="myForm" name="myForm">
  <!-- inputs go here -->
</form>
```

* `action`: The address of a server side file that will handle the information sent to it. In this example, there is a PHP file called "sendEmail.php".
* `method`: Generally `POST` or `GET` which are two ways of sending information to a server. `POST` is used when sending secure information like passwords.
* `name`: Can be applied to both the form and its inputs. It's a way of referencing the form when you get into both JavaScript and server side languages.
* `class`: Just like any other element, we can add classes (and/or an id) to a form.


## Basic form structure

Forms can be made up of numerous elements including various types of inputs with labels, fieldsets with legends, selects, and a submit input or button. They follow a basic pattern; all `<input>` elements must be nested inside a `<form>` element, and all `<input>` elements must have an associated `<label>`:

```html
<form action="#" method="#" class="myForm" name="myForm">

  <label for="userName">Enter your name:</label>
  <input type="text" id="userName" name="userName">

</form>
```

![Screen shot of a form with a label that says "Enter your name:" and a text input.](https://hychalknotes.s3.amazonaws.com/label-input-example--conEd.png)

Each element is a building block of a form:
* The `<form>` element contains the form. Every element nested inside of it is related to that form.
* The `<label>` element offers direction to users and provides a caption for the related input. For example, the above `<label>` is providing context to the input below it.
* The `<input>` element is where the user enters their information. In the example above, the input is a text input. There are many input types that provide different cues to users and the browser, which will be explored later in this class.


## Labels

Labels represent a caption for their associated inputs and are vital for user understanding. They are inline elements that have an opening and closing tag.

Their syntax is as follows: `<label for="associatedInputId">Label wording</label>`

While a `<label>` should be visually connected to their associated `<input>` by either being next to, below or above it, this is only beneficial for sighted users. To connect them programmatically, a `<label>` and `<input>` need additional attributes:

```html
<form action="#" method="#" name="myForm">

  <label for="userName">Enter your name:</label>
  <input type="text" id="userName" name="userName">

</form>
```

* The `<input>` needs to be given an `id`. Since they can only be used once per HTML document, an `id` paired with an `<input>` can only be used to reference that unique `<input>`.
* A `<label>` needs to be given a `for` attribute with a value which matches the `id` on the `<input>` it is referencing.

This creates a relationship between the `<label>` and the `<input>`, making it accessible for users utilizing AT, making them SEO friendly and helping the browser understand the relationship between the two HTML elements.

It also makes it possible to now click on a `<label>` and for focus to be given to the associated `<input>`. This is beneficial to users using a touch-screen device and those with visual or motor impairments, as it makes it easier to click on a given input.


## Input types

Forms can contain a variety of specific input types that carry semantic value. These allow users and browsers to identify the input, and for unique actions, like a telephone-number input bringing up the number pad on a phone when in focus.

Inputs are inline elements and are self closing, meaning they do not require a closing tag:

```html
<input type="text" id="someTextInput" name="someTextInput">
```

They must be nested within a `<form>` element to be valid, and should always have an associated `label`.


Create an html file called `learning-forms.html` to practice using the below input types.


### Text

`<input type="text">`

Text inputs create a single-line text field.

```html
<form action="#" method="#" name="myForm">

  <label for="userName">Enter your name:</label>
  <input type="text" id="userName" name="userName">

</form>
```

![Screen shot of a form with a label that says "Enter your name:" and a text input.](https://hychalknotes.s3.amazonaws.com/label-input-example--conEd.png)


### Radio

`<input type="radio">`

Radio inputs allow multiple options to be presented to a user but only allow for the user to select one option. They are called "radio buttons" because they are meant to look like the push-buttons that were found on old fashioned radios.

Radio buttons accept two key attributes:
* A `value` attribute, which is the value that will be passed to the server if a given radio button is the one selected.
* A `name` attribute, which allows radio buttons to be "grouped", limiting users to select only one option in a given group.

It is best to group radio inputs within a `fieldset` that has a `legend`.
* Fieldsets group together related inputs to provide more meaning to both AT and the browser.
* A legend is like a label for the entire group of inputs within a fieldset, which is needed since each radio button also uses its own individual label. 

```html
<form action="#" method="#" class="myForm" name="myForm">

  <fieldset>
    <legend>Choose your pizza size:</legend>
    
    <label for="small">Small</label>
    <input type="radio" name="pizzaSize" value="small" id="small">

    <label for="medium">Medium</label>
    <input type="radio" name="pizzaSize" value="medium" id="medium">

    <label for="large">Large</label>
    <input type="radio" name="pizzaSize" value="large" id="large">
  </fieldset>

</form>
```

Note: The default styling of a fieldset is easily removed with CSS like this:

```CSS
fieldset {
  border: 0;
}
```


![Three radio buttons with the values of Small, Medium and Large](https://hychalknotes.s3.amazonaws.com/input-radio--conEd.png)

In the above example, users are only able to check one of the options of "Small", "Medium" or "Large" because they share the same `name` value.

Radio buttons can also accept a default value by passing in the attribute of `checked` and value of "true", or simply the keyword `checked`:

```html
<input type="radio" name="pizzaSize" value="medium" checked>
  <!-- OR -->
  <!-- <input type="radio" name="pizzaSize" value="medium" checked="true"> -->
```

Both are valid and have the same outcome.

![Medium radio value selected](https://hychalknotes.s3.amazonaws.com/input-radio-checked--conEd.png)


### Checkbox

`<input type="checkbox">`

Checkbox inputs are very similar to radio inputs with a key distinction - checkbox inputs allow users to select multiple values in a given group.

Checkboxes should be grouped within a `fieldset` with a `legend`.

Similar to radio inputs:
* A matching `name` value allows the checkbox inputs to create a group-relationship.
* A `checked` or `checked="true"` allows for default value(s) to be checked.
* The `value` attribute is what is passed to the server.

```html
<form action="#" method="#" class="myForm" name="myForm">

  <fieldset>
    <legend>Choose your toppings</legend>

    <label for="pepperoni">Pepperoni</label>
    <input type="checkbox" name="topping" id="pepperoni" value="pepperoni">

    <label for="olives">Olives</label>
    <input type="checkbox" name="topping" id="olives" value="olives" checked>

    <label for="hotsauce">Hotsauce</label>
    <input type="checkbox" name="topping" id="hotsauce" value="hotsauce">

    <label for="mushroom">Mushroom</label>
    <input type="checkbox" name="topping" id="mushroom" value="mushroom" checked>

    <label for="bacon">Bacon</label>
    <input type="checkbox" name="topping" id="bacon" value="bacon">

    <label for="sunDriedTomatoes">Sun Dried Tomatoes</label>
    <input type="checkbox" name="topping" id="sunDriedTomatoes" value="sunDriedTomatoes">

    <label for="pineapple">Pineapple</label>
    <input type="checkbox" name="topping" id="pineapple" value="pineapple">
  </fieldset>

</form>
```

![](https://hychalknotes.s3.amazonaws.com/input-checked--conEd.png)


## Select

```html
<select>
  <option value="value1">value1</option>
  <option value="value2">value2</option>
</select>
```

Selects allow users to choose a single value from a given list. They are not `input` elements, but share a number of similar attributes.

Selects are made up of:
* The `<select>` element, which encompasses all of the options inside of it. It has an opening and closing tag and is an inline element.
* A set of `<option>` elements for the user to choose from. Options but they must all be nested within the `<select>` element to be grouped together. By default, the first `<option>` will be displayed in the select on page load, and it is common to see the first `<option>` with `disabled`, `selected` and an unassigned `value` attribute, so that the user cannot defer to a default value when the form is submitted.

```html
<form action="#" method="#" class="myForm" name="myForm">

  <label for="levelOfSpiciness">How spicy?</label>
  <select id="levelOfSpiciness" name="levelOfSpiciness">
    <option value disabled selected>Please choose an option</option>
    <option value="noSpice">No Spice</option>
    <option value="mild">Mild</option>
    <option value="medium">Medium</option>
    <option value="spicy">Spicy</option>
    <option value="deathlySpicy">I've made a terrible mistake</option>
  </select>

</form>
```

![](https://hychalknotes.s3.amazonaws.com/input-select--conEd.png)

Similar to radio and chckbox inputs, the `value` attribute is what is sent to the server when a given option is selected.

To provide a default value to a `<select>` element, the `selected` or `selected="true"` attributes can be passed to a given `<option>`.

```html
<form action="#" method="#" class="myForm" name="myForm">

  <label for="levelOfSpiciness">How spicy?</label>
  <select id="levelOfSpiciness" name="levelOfSpiciness">
    <option value disabled>Please choose an option</option>
    <option value="noSpice">No Spice</option>
    <option value="mild">Mild</option>
    <option value="medium">Medium</option>
    <option value="spicy" selected>Spicy</option>
    <option value="deathlySpicy">I've made a terrible mistake</option>
  </select>

</form>
```

![](https://hychalknotes.s3.amazonaws.com/input-select-selected--conEd.png)


Selects can also accept the attribute keyword `multiple`, meaning that users can choose multiple values at once by holding down command/ctrl (Mac/PC) and clicking the options.

```html
<form action="#" method="#" class="myForm" name="myForm">

  <label for="levelOfSpiciness">How spicy?</label>
  <select id="levelOfSpiciness" name="levelOfSpiciness" multiple>
    <option value disabled>Please choose an option</option>
    <option value="noSpice">No Spice</option>
    <option value="mild">Mild</option>
    <option value="medium">Medium</option>
    <option value="spicy" selected>Spicy</option>
    <option value="deathlySpicy">I've made a terrible mistake</option>
  </select>

</form>
```
![](https://hychalknotes.s3.amazonaws.com/input-select-multiple--conEd.png)


### Textarea

`<textarea></textarea>`

Unlike the text input, the textarea element accepts multi-line text. It has an opening and closing tag, and is an inline element.

```html
<form action="#" method="#" class="myForm" name="myForm">

  <label for="feedback">Please provide feedback</label>
  <textarea name="userFeedback" id="feedback"></textarea>

</form>
```

![](https://hychalknotes.s3.amazonaws.com/input-textarea--conEd.png)

Textareas can accept a range of unique attributes and features:
* Text can be written in between the opening and closing tags of a textarea. That text will remain even when users begin to write in the textarea.
* A `cols` attribute, which represents columns and a `rows` attribute, which represents rows. The values of these attributes will signify the height and width of the textarea.
* `minlength` and `maxlength` attributes that take numerical values that represent the minimum and maximum characters the textarea will accept.

```html
<form action="#" method="#" class="myForm" name="myForm">

  <label for="feedback">Please provide feedback</label>
  <textarea name="userFeedback" id="feedback" cols="30" rows="10" minlength="5" maxlength="200">
    My feedback is...
  </textarea>

</form>
```

![](https://hychalknotes.s3.amazonaws.com/input-textarea-col-row--conEd.png)


### Submit button

Within a form, a button will become a submit button by default unless you write some extra code to override this behaviour. It is recommended that you specify the `type="submit"` anyway for improved semantics. 

```html
<form action="#" method="#" class="myForm" name="myForm">

  <label for="terribleSecret">What are you hiding??</label>
  <input type="text" id="terribleSecret" name="terribleSecret">

  <button type="submit">Submit this!</button>

</form>
```

While by default `<button>` elements in a form have a `type` value of `submit`, they can instead be given the `type` value `reset`. This allows users to clear out the content of their form.

```html
<form action="#" method="#" class="myForm" name="myForm">

  <label for="terribleSecret">What are you hiding??</label>
  <input type="text" id="terribleSecret" name="terribleSecret">

  <button type="submit">Submit this!</button>
  <button type="reset">Clear form, I don't want to give you my secrets</button>

</form>
```

![](https://hychalknotes.s3.amazonaws.com/input-submit-04--conEd.png)


## Exercise

Download [form-elements-exercise.zip](../../exercises/form-elements-exercise.zip?raw=true) to practice using some form elements. Note there is no CSS required for this exercise - it is simply to practice with form elements!

Open up the answer key in the browser for reference of what elements to put onto the form.

## Resources
* [A complete list of available inputs](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)
* [Even more form elements to explore](https://github.com/HackerYou/con-ed-web-dev/blob/main/additional-resources/forms-extended/README.md)

