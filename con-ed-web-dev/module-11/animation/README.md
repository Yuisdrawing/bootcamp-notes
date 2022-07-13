# Animations

In addition to using transitions and transforms, there are a few other ways to add effects on websites. Keyframes help us bring everything together to create animations on our websites. Keyframes are so powerful that some web developers specialize in animations.

For example, [this character on CodePen is 100% CSS!](https://codepen.io/aakashrodrigues/pen/Gfhjw)


## Keyframes

Unlike most other CSS properties and values, keyframes are defined outside of the selector in which they're called. Like media queries, they use @-rules to signify that they are a keyframe.

Keyframes are made up of a timeline that maps out different points in an animation's life, and use %, or the keywords `from` and `to`, to mark different points within that timeline. 

In the below example, a keyframe called `snow` has been created using the @-rule, `@keyframes`.

```css
@keyframes snow {
  0% {
    top: 0;
  }

  100% {
    top: 100vh;
  }
}
```

It has two pieces in its timeline:
* `0%`, which represents the beginning of an animation. This could also have been the keyword `from`. When this keyframe is applied to an element, at the start of the animation, the property `top: 0` will be applied to the element's styles.
* `100%`, which represents the end of the animation. This also could have been the keyword `to`. At the end of the animation, the property `top: 100vh` will be applied to the element's styles.

The keyframe will automatically create an animated transition between the beginning and ending styles. 

Now that we have an animation, we need to use it! Download this [snow-animation--conEd.html file](https://hychalknotes.s3.amazonaws.com/snow-animation--conEd.html), and open it up both in your browser and text editor as we work through building out this animation. The snow animation is already in the CSS.

Let's add an HTML element that we will be adding our "snow" animation to by copy and pasting the below code. The `<div>` below holds something called a [Unicode character (Universal Coded Character Set)](https://en.wikipedia.org/wiki/List_of_Unicode_characters). Unicode characters are easy to quickly reference when we want a lightweight character! The below Unicode will render as a snowflake. 

```html
<div class="snowflake">&#10052;</div> 
```

Now let's target that div with the class of "snowflake" in our CSS and increase the font-size as well as make the position: absolute. We are making the `position: absolute` because the "snow" keyframe uses the keyword `top`, implying that the element must have access to that property.

```css
.snowflake {
  position: absolute;
  font-size: 40px;
  color: #fff;
}
```

Finally, let's add our animation of `snow` to the snowflake element with the `animation` property.

```css
.snowflake {
  position: absolute;
  font-size: 40px;
  color: #fff;
  animation: snow 3s linear infinite; /* This is the line we added! */
}
```


## Animation properties

General syntax: 
`animation: <animation-name> <animation-duration> <animation-timing-function> <animation-delay> <animation-iteration-count> <animation-direction>  <animation-play-state>;`

Let's break down the animation properties we applied to our animation on our snowflake:

`animation: snow 3s linear infinite;` contains four values.

* `snow`: The animation name. This is the same as what we named our keyframe. They must always be identical.
* `3s`: The duration it takes to complete the animation from start to finish in seconds. This value is mandatory, if you do not pass it in, your animation will not run! The "s" stands for seconds.
* `linear`: The animation-timing-function, which allows us to make smoother animations. Similar to transitions, the keywords available are `ease`, `ease-in`, `ease-out`, `ease-in-out` or `linear`. This can also be a cubic-bezier. [Check out this great visual resource to create your own cubic-beziers](http://cubic-bezier.com/#.17,.67,.83,.67). If not supplied, the default value is "ease".
* `infinite`: The number of iterations to complete. You could also set a number here, like 3, which would result it in running three times. If not supplied, the default value is 1.

Just like transitions, these can also be set independently:

```css
.snowflake {
  animation-name: snow;
  animation-duration: 3s;
  animation-timing-function: linear;
  animation-iteration-count: infinite;
}
```


### Additional animation properties 

Animations can get extremely intricate and have many properties applied to them:

```css
.snowflake {
  animation-delay: 1s;
  animation-direction: reverse;
  animation-fill-mode: forwards;
}
```

* `animation-delay`: Tells the animation to wait a set amount of time and then run. The default value is 0, meaning it will run right away. This is very similar to the delay on transitions.
* `animation-direction`: Tells the animation to play forwards, backwards, or alternate forwards then backwards. Keywords to use with this property are: 
  * `normal` for forwards. This is the default.
  * `reverse` for backwards.
  * `alternate` to alternate back and forth.
  * `alternate-reverse` to alternate, but start backwards then go forwards. 
* `animation-fill-mode`: Defines the styles that are applied to the element when the animation is not playing (before it begins, after it ends, or both). This is particularly useful for determining how animations end. 
  * `none`: Default value.
  * `forwards`: Element will retain its style from the last keyframe. The last keyframe depends on the values of `animation-iteration-count` and `animation-direction`. 
  * `backwards`: Element will retain its style from the first keyframe, which will depend on `animation-direction`. It will also retain its style during the `animation-delay` period. 
  * `both`: Animation will follow the rules of both backwards and forwards. 

### Keyframes values
Let's revisit our `snow` keyframes values:

```css
@keyframes snow {
  0% {
    top: 0;

  }
  100% {
    top: 100vh;
  }
}
```

Does the above mean that the animation "snow" will jump from top `top: 0` to `top: 100vh` ? 

While it may look that way looking at the code along, we saw in our browser that the animation will run smoothly between the two values. The power of keyframes is that they are doing a lot of work behind the scenes to make as smooth of a flow as possible to have the animation go from `top: 0` to `top: 100vh`, meaning at some point the browser will have a value of `top: 20vh`.

It's also important to note that as a best practice, we should aim to have a starting point for all of the properties we animate. For example, because `top: 100vh` was our endpoint, a `top` value should be set for the start point. If one is not set, the browser will look to the element's existing styles which can get lead buggy animations.

Try creating your own animation by downloading [fidget-animation--conEd.zip](https://hychalknotes.s3.amazonaws.com/fidget-animation--conEd.zip) and try recreating what you see in the answer key which is included in the folder.

#### Multiple values
Keyframes can also take multiple steps where you can apply diverse values by specifying at which time in the animation you would like something to happen.

Let's add on to the "snow" animation from earlier:

```css
@keyframes snow {
  0% {
    top: 0;
    /* note: transform's default value is none */
    transform: none;
  }
  10% {
    transform: translateX(20px);
  }
  20% {
    transform: translateX(100px);
  }
  30% {
    transform: translateX(20px);
  }
  40% {
    transform: translateX(100px);
  }
  50% {
    transform: translateX(20px);
  }
  60% {
    transform: translateX(100px);
  }
  70% {
    transform: translateX(20px);
  }
  80% {
    transform: translateX(100px);
  }
  90% {
    transform: translateX(20px);
  }
  100% {
    top: 100vh;
  }
}
```
Or you can match the points that have the same value together like the below: 

```css
@keyframes snow {
  0% {
    top: 0;
    /* note: transform's default value is none */
    transform: none;
  }
  10%, 30%, 50%, 70%, 90% {
    transform: translateX(20px);
  }
  20%, 40%, 60%, 80% {
    transform: translateX(100px);
  }
  100% {
    top: 100vh;
  }
}
```

Note that the the above is done with `transform: translateX()` instead of margin or padding, because `transform` is more performant than margin and padding, resulting in smoother animations.

Try making your own multi-step animations by downloading [coming-soon-animations--conEd.zip](https://hychalknotes.s3.amazonaws.com/coming-soon-animations--conEd.zip) and open the answer key in your browser to see what you should be aiming towards.

### Advanced exercise
If you want a more challenging animation exercise, try downloading [shape-animation--conEd.zip](https://hychalknotes.s3.amazonaws.com/shape-animation--conEd.zip) exercise and try to mimic the answer key!

## Animation libraries
One of the greatest parts of the web developer community is that folks are always creating tools that they open up for others to use - for free! Some such tools are animation libraries that make seemingly complicated animations as easy as adding a couple lines of code! 

### Animate.css
[Animate.css](http://daneden.github.io/animate.css/), created by Daniel Eden, is a library full of fun animations that are extremely easy to bring into our projects.

### Documentation
As with all libraries, the first thing we do to understand how to use it to read the documentation! Documentation is written by the author of the library on the ins and outs of their library. We can find the documentation for Animate.css on the [main page of their site](https://animate.style/#documentation).

Under the "Installation and usage" section in the Animate.css documentation, we can see it is giving us a couple options to add the library to our own projects. For this class, we will be looking at the option to add it directly to the head of our html document using a CDN.

![screenshot of the usage section of the Animate.css documentation](https://hychalknotes.s3.amazonaws.com/animateCSS-cdn.png)

A CDN (Content Delivery Network) is a network that delivers content to users. In this case, we can use the Animate.css CDN and bring in the whole library via a link in our head! Like CSS sheets, it is also considered a stylesheet because it will be bringing in styles! 

The concern with using a CDN, rather than downloading and linking to the library on your own server/computer, is that the CDN could go down or change at any time, causing the library to not load or improperly load on our end. This isn't a huge concern with well established, reliable providers like Animate.css though.

Go ahead and set up a new html file called `animation-library.html` and copy and paste the CDN link into your head.

Next in the documentation, it mentions that each element needs two classes to become animated:

1. the class of `animate__animated`
2. the class of the animation name preceded by `animate__`, like `animate__rubberBand` or `animate__shake`.

Add an image or heading to your "animation-library.html" file and try playing around with the library with the help of the documentation.

## Resources
* [MDN @keyframes](https://developer.mozilla.org/en-US/docs/Web/CSS/@keyframes)
* [Animatable CSS Properties](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_animated_properties)
