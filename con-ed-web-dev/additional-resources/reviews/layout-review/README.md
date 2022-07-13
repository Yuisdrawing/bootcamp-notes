# Layouts


### Layout Methods

* What is the difference between using `display: none` and `visibility: hidden`?
<details>
  <summary>Answer</summary>

	`display: none` completely removes the element from the rendered code, and no longer takes up any space. `visibility: hidden` will hide the element, but the element still takes up space in the layout. 
</details>

* What property is used to change the axis that a set of child elements are displayed on, and what values does it take?
<details>
  <summary>Answer</summary>

	`flex-direction` is used, which takes four different values: `row`, `row-reverse`, `column`, and `column-reverse`.
</details>

* What is the difference between justify-content and align-items?
<details>
  <summary>Answer</summary>

	`justify-content` aligns items along the main axis and distributes any free space between the flex children. `align-items` aligns items along the cross axis.
</details>

* What property can be used to force elements to appear in an unnatural order and what kind of value does it take?
<details>
  <summary>Answer</summary>

	The `order` property can be used to order elements in any order and it takes a numerical value.
</details>