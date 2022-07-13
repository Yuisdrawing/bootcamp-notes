# Nested lists

Lists can be nested inside one another to create multi-layered, intricate lists. A common example of a multi-layered list is a navigation with many levels that helps users find more specific sections of a website.

Thanks to semantic HTML, nesting lists within one another allows for relationships to form between them. When a list is nested inside of another, it is automatically considered a sub-list. Unordered and ordered lists can be "mixed and matched" when nesting.

```html
<ul>
    <li>
        <p>Milk</p>
    </li>
    <li>
        <p>Bread</p>
        <!-- first sublist begins -->
        <ul>
            <li>
                <p>Rye</p>
            </li>
            <li>
                <p>Whole Wheat</p>
            </li>
            <li>
                <p>Pumpernickel</p>
            </li>
        </ul>
        <!-- first sublist ends -->
    </li>
    <li>
        <p>Eggs</p>
    </li>
    <li>
        <p>Beer</p>
    </li>
    <li>
        <p>Sketti</p>
        <!-- second sublist begins -->
        <ul>
            <li>
                <p>Margarine</p>
            </li>
            <li>
                <p>Ketchup</p>
            </li>
        </ul>
        <!-- second sublist ends -->
    </li>
    <li>
        <p>Sauce</p>
    </li>
    <li>
        <p>Hot Dogs</p>
    </li>
</ul>
```

![An unordered list with two sublists](https://hychalknotes.s3.amazonaws.com/nested-list-unstyled--conEd.png)

Nested lists can be targeted using parent-child selectors:

```css
ul li ul {
    background: red;
}
```

![Same unordered list with two sublists with red background](https://hychalknotes.s3.amazonaws.com/nested-list-styled--conEd.png)

## Exercises

* Download [nested-lists--conEd.zip by clicking here](https://hychalknotes.s3.amazonaws.com/nested-lists--conEd.zip) and follow the instructions inside of the HTML file. Note that this exercise does not include `<p>` elements as children within the `<li>` -  it's important to get use to working with lists that utilize paragraph elements and those that do not as both are valid. The folder includes the answer key.
* To get even more experience with nested lists, download [nested-lists-more-practice--conEd.zip by clicking here](https://hychalknotes.s3.amazonaws.com/nested-lists-more-practice--conEd.zip). This element includes paragraph elements nested inside of `<li>`s. The folder includes the answer key.

