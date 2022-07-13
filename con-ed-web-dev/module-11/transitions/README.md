# Transitions

CSS allows developers to differently style multiple states on elements using pseudo-classes like `:hover` and `:active`. CSS _transitions_ let us easily animate the changes between states, to create smoother, more intuitive user experiences.

Create a file called `working-with-transitions.html` and add in the following code:

```html
<div class="boxFriend"></div>
```

```css
.boxFriend {
  width: 200px;
  height: 200px;
  background: darkslateblue;
}

.boxFriend:hover {
  width: 500px;
}
```

On hover, the `<div>` with the class of `boxFriend` will now snap quickly to have a width of 500px.

![](https://hychalknotes.s3.amazonaws.com/transition-no-transition-example--conEd.gif)

This effect is jarring and can leave users hesitant to interact with other sections of a website.

The CSS property `transition` offers ways to create smooth, dynamic transitions between an element's different states. It is made up of four values that each play a different role in creating a transition effect; we will look at each individually, but first here is an example of all of them being applied together:

```css
.boxFriend {
  width: 200px;
  height: 200px;
  background: darkslateblue;
  transition-property: width;
  transition-timing-function: ease-in; 
  transition-duration: 1s;
  transition-delay: 0.2s;
}

.boxFriend:hover {
  width: 500px;
}
```

![](https://hychalknotes.s3.amazonaws.com/transition-example-all-properties--conEd.gif)

In the above example, the transition is being set on the `width` property, and the cadence of the animation is named `ease-in`. It will take one full second to complete the transition, which will begin after a delay of 0.2 seconds from when the cursor begins to hover on the element.

The transition properties are placed on the element's original state. This is because we want the transition animation to happen when we hover on it, but also as the box shrinks once we stop hovering. The properties defined under `.boxFriend:hover` will only apply when we are hovering on the element, meaning that once the cursor moves outside of it, that CSS no longer applies, so any transitions defined there would stop applying as well and the box would just snap abruptly back to its original width instead of moving smoothly.


## Transition duration

`transition-duration: <length of time in seconds or milliseconds>;`

The `transition-duration` dictates how much time the transition takes to complete. It is set using seconds and milliseconds, and cannot accept negative values. This is the only transition property we have to explicitly set to make our transitions run, since its default value is `0`, so without setting our own value, different states have no animation between them and transition instantly (ie. in 0 seconds).

A good base value is 0.3s (0.3 seconds) or 300ms, (300 milliseconds) for most hover effects. Transitions that take multiple seconds can often impair the user experience of a website. 

```css
.boxFriend {
  width: 200px;
  height: 200px;
  background: darkslateblue;
  transition-duration: 0.8s;
}

.boxFriend:hover {
  width: 400px;
  height: 700px;
}
```

The above results in a smooth transition on all properties affected by the hover state, which takes 0.8 seconds to complete.


## Transition property

`transition-property: <keywords> or <specific property>;`

The `transition-property` property sets the property/properties to which the transition will be applied. It can be given one of three values:
* `all`: This is the default value. This value means that any transitions will be applied to every property that is changed in a different state (say, on hover).
* One or more specific, comma-separated properties to which the transition effects should be applied.
* `none`: This prevents any transition effects from running between the targeted element's states. We could still change the styles, but the change would be an instant jump instead of a smooth animation.

Here is an example of many properties changing on hover, so we use the `all` keyword to apply our transition across the board:

```css
.boxFriend {
  width: 200px;
  height: 200px;
  background: darkslateblue;
  transition-property: all;
  transition-duration: 1s;
}

.boxFriend:hover {
  width: 500px;
  height: 500px;
  border: 10px dotted green;
  background: yellow;
  border-radius: 50%;
  padding: 10%;
  margin: 50px;
}
```

If we only wanted to target some of the properties for animated transitions (say, the width and height), we could write them individually and comma-separated instead of using `all`:

```css
.boxFriend {
  width: 200px;
  height: 200px;
  background: darkslateblue;
  transition-property: width, height; /* This is the property we changed! */
  transition-duration: 1s;
}

.boxFriend:hover {
  width: 500px;
  height: 500px;
  border: 10px dotted green;
  background: yellow;
  border-radius: 50%;
  padding: 10%;
  margin: 50px;
}
```

Separating out individual properties to target like this also allows us to separately assign them different durations by similarly comma-separating them:

```css
.boxFriend {
  width: 200px;
  height: 200px;
  background: darkslateblue;
  transition-property: width, height;
  transition-duration: 1s, 4s; /* This is the property we changed! */
}

.boxFriend:hover {
  width: 500px;
  height: 500px;
  border: 10px dotted green;
  background: yellow;
  border-radius: 50%;
  padding: 10%;
  margin: 50px;
}
```

In the above example, the width transition will take one second to complete and the height will take four seconds. The browser matches the properties and durations in the order in which they are written in the CSS.

Note that not all CSS properties can be animated. For a complete list of those which can, [click here](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties).


## Transition timing function

`transition-timing-function: <keyword> or <cubic-bezier>;`

The `transition-timing-function` dictates at which rate the transition will flow (also known as an _acceleration curve_) during the length of its `transition-duration`.

`transition-timing-function` can be defined using one of the following options:
* Keywords
* A custom timing function, which is called a _cubic-bezier_. 


### Keywords

Keywords can be passed to `transition-timing-function` which will create appealing, smooth, transitions for us. They include:
* `ease`: The element will change slowly both at the beginning and end, and speed up in the middle. This is the default value, meaning if nothing is specified, the transition has a `timing-function` of `ease`.
* `ease-out`: The transition will move quickly at the beginning, and then slow down as it finishes.
* `ease-in`: The transition will move slow at the beginning and then speed up as it finishes.
* `ease-in-out`: The transition will move slow at the beginning, speed up in the middle, and slow down as it finishes. It is similar to the `ease` function.
* `linear`: The transition will move at the same rate throughout.

![easing example](https://hychalknotes.s3.amazonaws.com/transitionEasing.gif)

### Custom functions

If none of the keyword values suit the need of the transition, custom functions can be created and are represented by something called a cubic-bezier. A cubic-bezier is made up of four values: the first two values represent progression and the last two values represent time:

`transition-timing-function: cubic-bezier(.29, 1.01, 1, -0.68);`

A fast and easy way to create a custom function is by visiting [http://cubic-bezier.com/](http://cubic-bezier.com/). The website allows you to alter the curve of the graph, which will change the easing of the transition. 

Dev Tools also have a built-in cubic-bezier creator, which is useful for testing out how a custom function will look in action on your website.

![Image of the cubic-bezier creator in the dev tools](https://hychalknotes.s3.amazonaws.com/Screen%20Shot%202019-05-31%20at%2012.29.12%20PM.png)


## Transition delay

`transition-delay: <numerical amount in seconds or milliseconds>;`

The `transition-delay` property sets a delay on a transition, meaning that the transition will wait a certain amount of time before running. It has a default value of `0` which results in transitions firing right away.

Similar to `transition-duration`, `transition-delay` is most commonly written in seconds and milliseconds.

```css
.boxFriend {
  width: 200px;
  height: 200px;
  background: darkslateblue;
  transition-property: all;
  transition-duration: 0.5s;
  transition-timing-function: ease-out;
  transition-delay: 1s;
}

.boxFriend:hover {
  width: 500px;
  height: 500px;
}
```

The above will result in the transition waiting for one second before the transition begins.


## Multiple transitions

When working with multiple different properties changing between states, it is possible to create more complex effects by setting independent transition values for each property.

```css
.boxFriend {
  width: 200px;
  height: 200px;
  background: darkslateblue;
  border: 2px solid darkgoldenrod;
  transition-property: width, height, border-radius, border;
  transition-duration: 0.3s, 1s, 1.5s, 0.5s;
  transition-timing-function: ease-out;
  transition-delay: 1s, 0.4s, 2s, 1.3s;
}

.boxFriend:hover {
  width: 400px;
  height: 300px;
  border-radius: 20px;
  border: 10px solid pink;
}
```

In the above example, the duration and delay have been set for each changing property, but they all share `ease-out` as their timing-function.


## Shorthand

`transition: <transition-property> <transition-duration>  <transition-timing-function> <transition-delay>;`

A transition shorthand can optionally be used where each property is separated by a single space. 

```css
.boxFriend {
  width: 200px;
  height: 200px;
  border: 2px solid darkgoldenrod;
  background: darkslateblue;
  transition: all 0.8s ease-out 1s;
}

.boxFriend:hover {
  width: 400px;
  height: 300px;
  border-radius: 20px;
  border: 10px solid pink;
}
```

In the above example, the transition will affect all the properties targeted in the secondary state, will take 0.8 seconds to complete, with an `ease-out` function, and will begin after 1s.

It is common to see developers write with the transition shorthand and only reference some of the possible transition properties. For example, a common practice is to use the shorthand but to only write `transition-duration` and `transition-timing-function`, since `transition-property` is by default `all` and `transition-delay`is by default `0`, which are common transition property values. 

```css
.boxFriend {
  width: 200px;
  height: 200px;
  background: darkslateblue;
  transition: 0.2s linear;
}

.boxFriend:hover {
  width: 400px;
  height: 400px;
}
```

## Exercise
Transitions can take a design from a flat and underwhelming to a full and lively experience. 

Open up [lit-buttons--conEd.html](https://hychalknotes.s3.amazonaws.com/lit-buttons--conEd.html) in your text editor and your browser to explore how to couple transitions with other CSS properties to create some cool effects in your designs.

You can view a finished version of the buttons [here and compare to create the desired transitions](https://hychalknotes.s3.amazonaws.com/lit-buttons-ANSWER--conEd.html).
