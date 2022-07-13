# HTML Review

### HTML fundamentals

* What does HTML stand for?
<details>
  <summary>Answer</summary>

  Hypertext Markup Language
</details>

* Describe what HTML is for.

<details>
  <summary>Answer</summary>
Like the structure of a building, the bricks and beams, it creates semantic structure of the site and determines how our content will be interpreted.
</details>

* What should we always name the main HTML file of our site?
<details>
  <summary>Answer</summary>
Index.html
</details>

### Web accessibility

* At what point in a project should we start thinking about accessibility?
<details>
  <summary>Answer</summary>
From the beginning! Accessibility means everyone, regardless of ability, can perceive, understand, navigate, interact and contribute with our websites.
</details>

### Anatomy of HTML

* What is an element?
<details>
  <summary>Answer</summary>
A structural component that describes content.
Looks like: &lt;p>This is my content &lt;/p>
</details>

* What is a tag?
<details>
  <summary>Answer</summary>
The opening and closing portion of an element.
Looks like: &lt;em>Important stuff here &lt;/em>
</details>

### Invalid or less used elements

* What are some examples of invalid or obsolete elements?
<details>
  <summary>Answer</summary>
Elements such as &lt;marquee> and &lt;centre> are no longer used, as they describe presentational qualities and not the content. The underline tag &lt;u>, only makes sense to people who can see the underline, while &lt;em> connoted emphasis, which can be interpreted by all users, and their assistive devices.
</details>

### Div or span?

* What is the difference between a `<div>` and a `<span>`?
<details>
  <summary>Answer</summary>
&lt;div> is block element.
&lt;span> is inline element.
</details>

* What do `<div>` and a `<span>` have in common?
<details>
  <summary>Answer</summary>
Both are generic elements.
</details>

### Semantic elements

* How would you describe semantic elements?
<details>
  <summary>Answer</summary>
Semantic elements make HTML contextually meaningful.
</details>

* What are some examples of semantic elements?
<details>
  <summary>Answer</summary>
header, footer, main, nav, section, article, aside, figure, figcaption, etc.
</details>

* Why are semantic elements important/helpful?
<details>
  <summary>Answer</summary>
They are more descriptive, they help with readability and are accessibility and SEO friendly.
</details>

### Attributes

* What are some examples of attributes?
<details>
  <summary>Answer</summary>
A couple are: class, id, title, src, href & alt.
</details>

* What is the difference between an `id` and a `class`?
<details>
  <summary>Answer</summary>
An id can only be used once per document whereas a class can be used many times.
</details>

* Name some attributes we no longer use, and why.
<details>
  <summary>Answer</summary>
align, color, size, bgcolor, font are some examples because they relate to presentation.
</details>

### Anchor tags

* How would we use anchor tags to link to a location on the same page?
<details>
  <summary>Answer</summary>
Pass in the id of the element you wish to anchor to eg: &lt;a href="#about">About&lt;/a>
goes to &lt;section id=”about”>About Section&lt;/section>
</details>

### Images

* What attributes are associated with image elements?
<details>
  <summary>Answer</summary>
src=””, alt=””
</details>

* What are these attributes associated with images for?
<details>
  <summary>Answer</summary>
src: The source of your image file. 

alt: The alternate text that describes an image. Helpful for both search engines and visually impaired users.
</details>

* What are the two ways you can reference an image file and what do they do?
<details>
  <summary>Answer</summary>
Absolute & relative paths.

Absolute image paths are typically links to images on other websites.

Relative image paths uses your document as the starting point and leads out of your document, through folders or sub-folders, to end up at the image file.
</details>

### Comments 

* How do we write comments in HTML?
<details>
  <summary>Answer</summary>
&lt;!-- -- this is my comment -- -->

</details>

* What are some of the reason we use comments?
<details>
  <summary>Answer</summary>
-Remind ourselves why we wrote the code this way.

-Explain to future developers what’s going on.

-To hide existing code without deleting it.
</details>

### Bonus 

* What is the official name of #?
<details>
  <summary>Answer</summary>
Octothorpe
</details>
