# Colors

Colors can help make our websites rich and provide context to users, so they're a big part of styling.

Note that CSS was developed in the United States, so CSS color properties always spell "color" without the "u" - `color`, `background-color`, etc. 

In web development, there are six different color formats to choose from, each with its own strengths:

* Name
* Hex value
* RGB
* RGBA
* HSL
* HSLA

We are not going to be going over HSL and HSLA in this course, but you can learn about them [by clicking here](https://css-tricks.com/hsl-hsla-is-great-for-programmatic-color-control/).


## Name

As we've discovered through past lessons, CSS allows you to pass in a color name as a value. These colors have been agreed on by the web community and there are 147 color keywords in total for 138 colors (some are duplicates - like "grey" and "gray").

They range from ordinary colors, like "red" or "black", to fancier-sounding colors like:
- peru
- peachpuff
- dodgerblue
- ghostwhite (which is a slightly grey color...)
- rebeccapurple ([learn about the history of rebeccapurple by clicking here](https://css-tricks.com/rebbeccapurple-663399/))

We use the color names in CSS as below:

```css
p {
  color: seagreen;
}
```

Color keywords are useful when looking for a quick way to throw some color onto your website, but they're often replaced with other formats in professional settings because of their lack of range.

To view the full list of color keywords available, visit [http://colours.neilorangepeel.com/](http://colours.neilorangepeel.com/).


## Hex

Hex colors are made up of alphanumeric characters pre-pended by a `#`:

```css
p {
  color: #2E8B57;
}
```

They are made up of three pairs of alphanumeric digits which represent red, green and blue respectively. The characters that can be used range from 0-9, then a-f, where '0' represents the absence of color (black) and 'f' represents full color (white). The characters provided can be in either upper or lower case.

**Black** (`#000000`)

| r  | g  |  b |
|---|---|---|
| 00  |  00 | 00  |

**White** (`#ffffff`)

| r  | g  |  b |
|---|---|---|
| ff  |  ff | ff  |

**Red** (`#ff0000`)

| r  | g  |  b |
|---|---|---|
| ff  |  00 | 00  |

**Green** (`#00ff00`)

| r  | g  |  b |
|---|---|---|
| 00 |  ff | 00  |

**Blue** (`#0000ff`)

| r  | g  |  b |
|---|---|---|
| 00 |  00 | ff  |

For example, writing `palegoldenrod` as a hex value looks like this:

```css
p {
  color: #eee8aa;
}
```


### Shorthand 

Hex values can be shortened to three digits if the two digits that represent each Red-Green-Blue value are the same, meaning you can abbreviate each color channel using one character instead of two identical characters:

- `#000000` = `#000`
- `#ffffff` = `#fff`
- `#994499` = `#949`
- `#dd1122` = `#d12`

Hex codes are commonly used by developers because of how specific you can be with the choice of color. 

**Fun hex color facts:**
* The named keyword colors "aqua" and "cyan" have the same hex code.
* Hex codes sometimes spell words like #C0FFEE & #BADA55.


## RGB / RGBA
Similar to the hex code format, RGB relies on Red-Green-Blue values to create a color. To declare a color in RGB, three values between 0 and 255 must be passed in, separated by commas.

Pure black, or the absence of color: `rgb(0, 0, 0)`

| r  | g  | b |
|---|---|---|
| 0 |  0 | 0  |

Pure white, or the mix of every color: `rgb(255, 255, 255)`

| r  | g  | b |
|---|---|---|
| 255 |  255 | 255  |

Pure red : `rgb(255, 0, 0)`

| r  | g  | b |
|---|---|---|
| 255 |  0 | 0  |

Pure blue: `rgb(0, 0, 255)`

| r  | g  | b |
|---|---|---|
| 0 |  0 | 255  |

Limegreen: `rgb(50, 205, 50)`

| r  | g  | b |
|---|---|---|
| 50 |  205 | 50  |


In CSS it looks like this:

```css
p {
  color: rgb(46, 139, 87);
}
```

### Alpha
What makes RGB unique is its use of the alpha: RGBA. This fourth value passes an alpha transparency value to the color (ie. an opacity), represented by a decimal between 0 and 1. The closer the value is to 0, the more transparent the color will appear. The value of 1 will result in no transparency.

Black with 50% alpha: `rgba(0, 0, 0, 0.5)`

| r  | g  | b | a |
|---|---|---|--|
| 0 |  0 | 0  | 0.5 |

Tomato with 30% alpha: `rgba(255, 99, 71, 0.3)`

| r  | g  | b | a |
|---|---|---|--|
| 255 |  99 | 71  | 0.3 |


## Resources
* [ColorZilla - a Firefox extension that helps you discover what colors other sites are using](https://addons.mozilla.org/en-US/firefox/addon/colorzilla/?src=search)
* [A list of hex codes that form words](https://c0ffee.surge.sh/)
