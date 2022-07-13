# Advanced Selectors - Extended

_This file contains additional CSS advanced selectors._

## Attribute selectors

### Contains
To target an element whose attribute value contains a certain text the asterisk can be used.

The example below will target all anchor elements whose href contains the text "donkey":
`a[href*="donkey"]`

```html
<div class="containsExample" >
    <a href="http://donkey.ca">Donkey</a>
    <a href="http://www.google.com">Google</a>
    <a href="http://donkeysanctuary.com">Donkey Sanctuary</a>
</div>
```
```css
.containsExample a[href*="donkey"] {
    border: 2px solid red;
	padding: 10px;
	display: inline-block;
}
```

![The first and third anchor elements whose href contains the text "donkey" has been targeted, and a red border has been added.](https://hychalknotes.s3.amazonaws.com/contains-selector--conEd.png)

### Ends with
To target an element whose attribute value ends with a certain text, the dollar sign can be used.

The example below will target all anchor elements whose href ends with the text "jpg".
`a[href$="jpg"]`

```html
<div class="endExample">
	<a href="http://google.com">Google.com</a>
	<a href="https://letslearnes6.com/imgs/me.jpg">RC Headshot</a>
	<a href="https://orig00.deviantart.net/af8c/f/2012/091/c/d/baby_fox_by_blood_charm-d4ummfk.png">baby fox picture</a>
</div>
```
```css
.endExample a[href$="jpg"] {
    color: goldenrod;
}
```

![The anchor with the href attribute whose value is ending in jpg (content of RC Headshot) is targeted, and has a colour of goldenrod.](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-20%20at%209.39.00%20AM.png)

## Pseudo class selectors

### First line
`::first-line` or `:first-line`

The first-line selector will target the first line of any block of text. It is technically considered a pseudo-element like the before and after elements.

This selector will behave responsively: if the words in the first line of a block of text changes due to width restrictions, the styles will still only be applied to the characters in that first line.

```html
<p class="firstLineExample">Lorem ipsum dolor sit amet, consectetur adipisicing elit.Aliquam, minus, quos, earum expedita obcaecati reprehenderitinventore libero atque veniam aut repellendus tenetur in repellat necessitatibus eveniet iure eos quaerat temporaveniam aut repellendus tenetur in repellat necessitatibus eveniet iure eos quaerat temporaveniam aut repellendus tenetur in repellat necessitatibus eveniet iure eos quaerat temporaveniam aut repellendus tenetur in repellat necessitatibus eveniet iure eos quaerat temporaveniam aut repellendus tenetur in repellat necessitatibus eveniet iure eos quaerat temporaveniam aut repellendus tenetur in repellat necessitatibus eveniet iure eos quaerat temporaveniam aut repellendus tenetur in repellat necessitatibus eveniet iure eos quaerat temporaveniam aut repellendus tenetur in repellat necessitatibus eveniet iure eos quaerat temporaveniam aut repellendus tenetur in repellat necessitatibus eveniet iure eos quaerat temporaveniam aut repellendus tenetur in repellat necessitatibus eveniet iure eos quaerat tempora!</p>
```

```css
p.firstLineExample::first-line {
    color: red;
}
```
![The first line of the lorem ipsum text has been targeted and has the colour of red.](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-20%20at%209.53.28%20AM.png)