# Positioning Review

* What CSS declarations should be used to create layouts? Which should not be used?
<details>
  <summary>Answer</summary>

	We should use `flex` and `display` to create layouts. `position` should never be used to create layouts.
</details>

* What are some examples of when to use the `position` property on an element?
<details>
  <summary>Answer</summary>

	Bumping something by just a few pixels, overlapping two elements or having something burst out of its wrapper, or placing an element in the corner of a parent element no matter what size the parent element is, are all examples of when to use `position`.
</details>

* What is the difference between `position: relative` and `position: absolute`?
<details>
  <summary>Answer</summary>

	`position: relative` will position an element in relation to its immediate parent whereas `position: absolute` will position an element in relation to the body.
</details>

* What four properties does the `position` declaration use to determine its position?
<details>
  <summary>Answer</summary>

	`top`, `right`, `bottom`, and `left` are the four properties used to dictate the position of an element with `position` on it.
</details>

* What position is the newest addition to the position family?

<details>
  <summary>Answer</summary>

	`position:sticky`
</details>





### Bonus 

* Imagine a nav bar that starts at the bottom of the page, moves up to the top of the page on scroll, and stops and sticks to the top of your page as the user scrolls all the way to the bottom of the page. How would you write the CSS rule that allows the nav bar to behave this way?
<details>
  <summary>Answer</summary>

	 ```nav {
		 position: sticky;
		 top: 0;
	 }```
</details>
