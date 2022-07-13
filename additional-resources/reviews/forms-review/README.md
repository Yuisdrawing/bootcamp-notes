# Forms Review

* Name some of the attributes that a typical form element might take.
<details>
  <summary>Answer</summary>

	Form attributes includes action, method, class, and name.
</details>

* What inline element should always be paired with a form element, and how do you programmatically connect the two?
<details>
  <summary>Answer</summary>

	The `<label>` element should always be paired to an input, and they are connected by giving the input a unique `id` and the label a matching `for` value.
</details>

* See how many `<input>` types you can name.
<details>
  <summary>Answer</summary>

	`<input type="text">`, `<input type="password">`, `<input type="email">`, `<input type="search">`, <input type="file">`, `<input type="color">`, `<input type="range">`, `<input type="radio">`, `<input type="checkbox">`, `<select>`, `<textarea>`, `<input type="submit">`, and `<button>`
</details>

* How does the input type `password` change the behaviour of the input?
<details>
  <summary>Answer</summary>

	The password input type automatically changes the characters to dots to hide the user input as it is typed.
</details>

* How can you change what is written in an input by default, before the user ever changes it? And how can you style it?
<details>
  <summary>Answer</summary>

	You can change what is written in an input by assigning a `placeholder` attribute on the input in the HTML. You can style that placeholder in CSS by using double colons, written like `input[type="text"]::placeholder`.
</details>

* Which form inputs have been called a "nightmare" to change their styling?
<details>
  <summary>Answer</summary>

	The `<select>` and `<option>` inputs are nearly impossible to expect consistent results across browsers when styling them.
</details>

### Bonus 

* How can you prevent the user from resizing a textarea element on your website?
<details>
  <summary>Answer</summary>

	 You can remove the ability to resize the textarea by selecting the element in css and adding the declaration `resize: none`.
</details>
