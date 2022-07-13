# CSS Review

### CSS fundamentals

* What does CSS stand for?
<details>
  <summary>Answer</summary>

	Cascading Stylesheets
</details>

* Describe what CSS is for.

<details>
  <summary>Answer</summary>

	CSS brings style to our HTML structure by altering the look, feel, size, colour and virtually any visual aspect of the HTML elements.
</details>

* Where should we write our CSS?
<details>
  <summary>Answer</summary>

	CSS should be written in an external stylesheet, connected to our HTML using a `<link>` element in the `<head>`
</details>

### CSS Rules

* What are the two key parts that make up a CSS Rule?
<details>
  <summary>Answer</summary>

	A CSS Rule is made up of a selector and a declaration.
</details>

* How do we define styles inside of a CSS declaration?
<details>
  <summary>Answer</summary>

	A CSS declaration is made up of a property and value.
</details>

* What are the three properties that make up a wrapper?
<details>
  <summary>Answer</summary>

	`max-width`, `width`, and a `margin`. 
</details>
### Cascade, Specificity, and Inheritance

* What does the cascade dictate, and how can you override it?
<details>
  <summary>Answer</summary>

	The cascade dictates what styles will be rendered based on the order in which they fall in your stylesheet. The cascade can be overwritten using specificity - the more specific the selector, the higher the priority.
</details>

* What types of properties are affected by inheritance?
<details>
  <summary>Answer</summary>

	CSS allows typographical properties to be set on a parent element and inherited by all of its children.  
</details>

* What does the inherit keyword allow us to do?
<details>
  <summary>Answer</summary>

	Inherit allows us to tell an element to respect its parent element. 
</details>

### Pseudo-classes, z-index, & before/after elements

* What are some of the most commonly used pseudo-elements?
<details>
  <summary>Answer</summary>
	
	Some of pseudo-elemnets you'll see most often include hover, focus, active, and visited.
</details>

* When looking to create shapes with before and after elements, what is the name of the property that needs to be given an empty value in order to properly render the element on the page?
<details>
  <summary>Answer</summary>
	
	`content: '';` is typically the first property-value pair given to a before or after element that is going to be made into a shape with CSS.
</details>

*	What does `z-index` affect and what type of value does it accept?
<details>
  <summary>Answer</summary>

	`z-index` will affect where an element stacks on a website's z axis, as opposed to its x and y axis, and it accepts any unitless whole number.
</details>

### Cross-browser compatibility & floats

* Which browser is most important to consider in your web development?
<details>
  <summary>Answer</summary>

	The short answer is... ALL OF THEM! For every project a developer should take into consideration which browsers should be prioritized based on the expected target audience and the browsers expected to be used. 
</details>

* When using floats element collapse is a common problem. How do you fix it?
<details>
  <summary>Answer</summary>
	
	By ensuring that the class of clearfix is defined in your setup snippet, and by applying a class of clearfix to the parent of any floated elements, you will prevent element collapse from occuring.  
</details>

### Bonus 

* Who is the namesake of the blur effect applied by the CSS blur filter function?
<details>
  <summary>Answer</summary>

	Blur() applies what is known as a "Gaussian blur," named after the scientist and mathematician Carl Friedrich Gauss. 
</details>
