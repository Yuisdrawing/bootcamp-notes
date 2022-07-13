# SCSS Review

* How do we organize our SCSS?
<details>
  <summary>Answer</summary>

	SCSS is written in seperate files called partials, which are kept in a partials folder. Partials help keep our CSS organized by storing it in smaller, more maintainable, files instead of one long file.
</details>

* How can you replace long selector names in your SCSS file?
<details>
  <summary>Answer</summary>

	Nesting is used to keep your stylesheet organized and clean.
</details>

* How is the ampersand `&` used in SCSS?
<details>
  <summary>Answer</summary>

	The ampersand is used when nesting your selectors to refer to the parent selector.
</details>

* How are variable used in SCSS?
<details>
  <summary>Answer</summary>

	Variables are used to collect common styles and assign them a simple, memorable name in order to help keep our code DRY.
</details>

* How do you call a mixin that contains a placeholder value within a selector? 
<details>
  <summary>Answer</summary>

	Mixins are called using @include followed by the name of the mixin, with an argument passed into a set of smooth brackets containing the value you'd like to assign to the placeholder value. e.g. `@include mixinName(argument);` or `@include fontSize(36px);`.
</details>

### Bonus 

* What is the difference between SASS and SCSS
<details>
  <summary>Answer</summary>

	 Syntactically Awesome Style Sheet is the older version and doesn't use any brackets or semi-colons. Sassy CSS is the most commonly used and most up to date version and looks a lot more like CSS due to its use of brackets and semi-colons.
</details>
