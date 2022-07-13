# Backgrounds - Extended

_This file contains additional information on the CSS `background` property._

## Background-repeat

To repeat the background image along the `y-axis` (top-down):

```css
header {
  background-image: url(./assets/fishFriend.jpg);
  background-repeat: repeat-y;
  height: 800px;
}
```

To repeat the background image along the `x-axis` (left-right):

```css
header {
  background-image: url(./assets/fishFriend.jpg);
  background-repeat: repeat-x;
  height: 800px;
}
```

To repeat the background image along the `x-axis` and the `y-axis`:

```css
header {
  background-image: url(./assets/fishFriend.jpg);
  background-repeat: repeat;
  height: 800px;
}
```


## Background-postion

### Pixels

You can apply two values to the position of the background-image using pixels. The first value is the horizontal placement and the second value is the vertical:

```css
section {
  background-image: url(./assets/fishFriend.jpg);
  background-repeat: no-repeat;
  height: 800px;
  background-position: 20px 80px;
}
```

If only one value is passed in, the other value defaults to `center` or 50%;

```css
section {
  background-image: url(./assets/fishFriend.jpg);
  background-repeat: no-repeat;
  height: 800px;
  background-position: 20px;
  /* Which is really background-position: 20px center; */
}
```



