# CSS Typography - Extended

## Text-decoration shorthand
`text-decoration: <text-decoration-line> <text-decoration-color> <text-decoration-style>;`

`text-decoration` can be written as a shorthand by writing the three values available to text-decoration, in whichever order, with a space separating each value.

The below would create an underline that is wavy in decoration and red in colour.

```css
  text-decoration: underline wavy red;  
```

The shorthand can also accept a single value, which is commonly used to remove the default underline on links:

```css
a {
  text-decoration: none;
}
```

## Text shadow
`text-shadow: <x offset value> <y offset value> <blur radius value> <colour in any color format>;`

Text shadow allows developers to apply shadows to text. This effect can definitely be abused, bringing back horrible/wonderful memories of Word Art. But it can also bring tasteful effects to websites.

Text shadow takes 4 values: horizontal offset, vertical offset, blur, and colour. It can also take multiple comma-separated values so you can add as many shadows to your text as you wish.

```css
.white-with-blue-shadow {
  text-shadow: 1px 1px 2px black;
}
```

![Screen shot of the text-shadow property being rendered with the values "1px 1px 2px black"](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-02-13%20at%205.47.22%20PM.png)

Open up [text-shadow--conEd.html](https://hychalknotes.s3.amazonaws.com/text-shadow--conEd.html) to play around.