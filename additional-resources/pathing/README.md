# Pathing
To connect to assets using a relative path, our computer needs explicit instructions on how to find the assets. Pathing is how we give instructions to the browser on how to navigate through our folders with the use of `..`, `.` and `/`.

## Same level
`./` OR nothing

```css
section {
    background-image: url(./assets/sillyGoose.gif);
}
```
OR

```css
section {
    background-image: url(assets/sillyGoose.gif);
}
```

## Move outside of folder, one level up
```css
section {
    background-image: url(../assets/sillyGoose.gif)
}
```
## Move outside of folder, two levels up
```css
section {
    background-image: url(../../assets/sillyGoose.gif)
}
```

`../` can be continuously chained to continue to move outside of folders.


### Practice
* [Open up pathing level 1 practice by clicking here](https://hychalknotes.s3.amazonaws.com/relative-image-practice-level1--conEd.zip). The answer key can be found by [clicking here](https://hychalknotes.s3.amazonaws.com/relative-image-practice-level1-ANSWER--conEd.zip)
* [Open up pathing level 1 practice by clicking here](https://hychalknotes.s3.amazonaws.com/relative-image-practice-level2--conEd.zip). The answer key can be found by [clicking here](https://hychalknotes.s3.amazonaws.com/relative-image-practice-level2-ANSWER--conEd.zip).