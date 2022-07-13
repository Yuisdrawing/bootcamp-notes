# Forms extended

## Additional input types

### Password

`<input type="password">`

The password input type automatically changes characters to dots so the password isn't revealed.

```html
<form action="#" method="#" class="myForm" name="myForm">

  <input type="password" id="userPassword" name="userPassword">
  <label for="userPassword">Enter your password, please!</label>

</form>
```

![Screen shot of a form with a label that says "Enter your password, please!" and a password input.](https://hychalknotes.s3.amazonaws.com/input-password--conEd.png)


### Email

`<input type="email">`

The email input type appears the same as a regular text input, but will automatically verify if the user has entered something formatted as an email address - ie. anything with an "@", and a ".com" or ".ca", etc. If a user has put something into the input which does not match the expected email pattern, an error is thrown.

```html
<form action="#" method="#" class="myForm" name="myForm">

  <label for="userEmail">Enter your email</label>
  <input type="email" id="userEmail" name="userEmail">

  <input type="submit">

</form>
```

![Screen shot of a form with a label that says "Enter your email" and an email input.](https://hychalknotes.s3.amazonaws.com/input-email--conEd.png)

In the rare cases where the email input type is not fully supported, the input is interpreted as a regular text input.


### Range

`<input type="range">`

The range input creates a slider that users choose a value between a minimum and maximum number. This range is set by giving the input `min` and `max` attributes with number values.

```html
<form action="#" method="#" class="myForm" name="myForm">

  <input type="range" id="levelOfCheesiness" name="levelOfCheesiness" min="0" max="11">
  <label for="levelOfCheesiness">Amount of Cheese</label>

</form>
```

In the above example, the minimum amount a user can choose is "0", which is the range at the leftmost side, and the maximum amount is "11" which is the range at the rightmost side of the slider.

![](https://hychalknotes.s3.amazonaws.com/input-range--conEd.png)

Additional attributes can also be used:
 * `step` allows users to move in set increments in the given range. For example, if `step` is set to `10`, the user can only select values in multiples of 10. If no `step` value is specified, the default value is 1.
 * `value` sets the default value, meaning that if the user does not select anything with the range input, the default value would be sent to the server.

```html
<form action="#" method="#" class="myForm" name="myForm">

  <input type="range" id="levelOfCheesiness" name="levelOfCheesiness" min="0" max="100" step="10" value="30">
  <label for="levelOfCheesiness">Amount of Cheese</label>

</form>
```

In the above example, a `step` of 10 has been applied, meaning users can increase and decrease the slider by values of 10.

A `value` of 30 has also been applied, meaning that if a user does not interact with the range input, it will default to a value of 30.

When this type of input is not supported, a text input is rendered in its place.

### Search
`<input type="search">`

The search input is very similar to the input text but is used for query searches.

```html
<form action="#" method="#" class="myForm" name="myForm">
  <label for="searchingFor">Enter your search term:</label>
  <input type="search" id="searchingFor">
  <input type="submit">
</form>
```

![Screen shot of a form with a label that says "Enter your search term:" and an search input.](https://hychalknotes.s3.amazonaws.com/input-search--conEd.png)

### File
`<input type="file">`

This input allows the user to select a file from their computer.

```html
<form action="#" method="#" class="myForm" name="myForm">
  <label for="uploadFile">Upload your file:</label>
  <input type="file" id="uploadFile">
  <button>Upload file</button>
</form>
```
![Screen shot of a form with a label that says "Upload your file:" and an search input.](https://hychalknotes.s3.amazonaws.com/input-file--conEd.png)

*Note: Multiple files can be chosen and uploaded by passing in the attribute `multiple` with the value of `multiple`. I.e. `multiple = multiple`.*

### Color
`<input type="color">`

The color input allows users to choose a colour through the use of a visual colour picker which may look different depending on the browser being used. The colour pickers cannot be styled.

```html
<form action="#" method="#" class="myForm" name="myForm">
  <label for="chooseColour">Choose a colour:</label>
  <input type="color" id="chooseColour">
</form>
```

![](https://hychalknotes.s3.amazonaws.com/input-colour--conEd.png)

It is possible to provide a default colour value by using the `value` attribute and can only accept a hex value as a colour format.

```html
<form action="#" method="#" class="myForm" name="myForm">
  <label for="chooseColour">Choose a colour:</label>
  <input type="color" id="chooseColour" value="#BADA55">
</form>
```
*Note: To see your value color update, be sure to do a hard refresh. A hard refresh is done by pressing `shift + command/option + R`*


## Additional form attributes

### Minimum and maximum character lengths

Using the `minlength` and `maxlength` attributes, developers can set the minimum and maximum number of characters that a text input can accept to be valid. Similar to `required`, the browser is doing some meaningful validation before sending the form to the server for us.

```html
<form action="#" method="#" class="myForm" name="myForm">

  <label for="firstName">Your Username:</label>
  <input type="text" name="userName" placeholder="ex. Captain Cool Beans" id="firstName" maxlength="8" minlength="2" aria-describedby="userNameLength">
  <p class="helperText" id="userNameLength">Note: Usernames must be longer than 2 characters and cannot be longer than 8 characters.</p>

  <button type="submit">Submit</button>

</form>
```

![](https://hychalknotes.s3.amazonaws.com/form-minmax--conEd.png)

In the example above, the input has been given a minimum length of 2 characters, and a maximum length of 8 characters. It has also been given a placeholder and some helper text below the input that allows users to understand what is expected of them.

> **Accessibility tip**
> The `aria-describedby` attribute is used to give further context to elements and forms. It will programmatically connect an element to a description using the description's `id` as the `aria-describedby` value.
>
> In the above example, the helper text is reliant on two key aspects to be successful: It is in close proximity to the input, making them visually related. and it uses `aria-describedby`. Helper text should not be hidden as both sighted and non-sighted users benefit from interacting with it.


### Value

The `value` attribute allows default values to be given to inputs that can be altered by the user. If unaltered, the `value`'s value is sent to the server.


```html
<form action="#" method="#" class="myForm" name="myForm">

  <label for="userPhone">Your phone number:</label>
  <input type="tel" id="userPhone" name="phoneNumber" value="416-">

</form>
```

![](https://hychalknotes.s3.amazonaws.com/value--conEd.png)

Note that the above uses the tel input, which is used for telephone numbers. It is useful because it brings up the users numerical keyboard on their cellphone automatically.


### Disabled

The `disabled` attribute disables a form element. Disabled elements will not receive focus and therefore will be skipped when a user tabs through (it will not be read out by AT). The values of disabled elements are also not editable and they will not be sent to the server. Disabled inputs often seem greyed-out, which is a common browser default.

Similar to `required`, it can be set by passing a value of `true` to the attribute or simply by using the keyword `disabled`.


```html
<form action="#" method="#" class="myForm" name="myForm">

  <label for="yourName"> Your name: </label>
  <input type="text" value="I won't be sent to the server" id="yourName" disabled>
  <!-- OR -->
  <!-- <input type="text" value="I won't be sent to the server" id="yourName" disabled="true"> -->

</form>
```

![](https://hychalknotes.s3.amazonaws.com/disabled--conEd.png)