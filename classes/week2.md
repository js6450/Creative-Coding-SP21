## Week 2: Animation

### Review of `setup()` and `draw()`

* The fundamental building blocks of p5.js (these are also functions!)
* Part of default code when working on the p5.js web editor
* `setup()`
  * Per namesake, a place to store code that are for setting up configurations for our drawings
  * Everything contained within the `setup()` function **runs only ONCE**
  * Typical things we do inside `setup()`:
    * Create our canvas using `createCanvas()` function
    * Set initial background color using `background()` function
    * Upload / initialize any media assets (images and videos)
* `draw()`
  * Per namesake, a place to store code for drawing within your canvas
  * Everything contained within the `draw()` function **runs repeatedly in a loop** and continues running until we press the stop button in the p5 web editor, or navigate away from the webpage containing the p5.js sketch.
  * Since everything in the function runs repeatedly, it is a great place to animate our drawings by incrementing / decrementing certain values. More on this later. For now, we will stick to static drawings.

### Frames = how many times did the `draw()` function run?

* An animation is an illusion. Everytime we see an animation, we are actually seeing a sequence of still images that give us the illusion of movement
* When multiple images appear at a fast enough rate, our eyes translate and blend them into a single moving image.
* Each time the `draw()` function runs, we produce one frame.
* Frames Per Second (FPS)
  * p5.js will **TRY** to run a p5.js sketch at 60 FPS
  * FPS can be controlled using the `frameRate()` function --> can intentionally lower the frame rate to create a choppy animation.

### Creating Animations with p5.js

* Incrementing variables every `draw()` loop / frame
  * A technique we saw in the [Bouncing Ball sketch](https://editor.p5js.org/js6450/sketches/sNR7cpmEV)
* We just need to have a variable that changes over time that we can use to vary visual properties of elements on our sketch.
  * How may the value of a variable change over time?
    * Linearly (Increment / Decrement)
    * Exponentially
      * Challenge: How might you animate something exponentially? Can you create an ease-in and ease-out animation? (Hint: take a look at [the `lerp()` function](https://p5js.org/reference/#/p5/lerp). How might you use it to animate postion, size, and colors of shapes?)
    * Randomly
  * What visual properties can we animate?
    * Color
    * Position
    * Size
    * Number of elements

### The `frameCount` Variable

* A convenient variable to use to linearly animate a visual properity
* Returns the number of frames rendered since the beginning of the sketch (from the point the "play" button on the p5.js web editor is pressed)

### Random

* What is Random? What is it in terms of computer science? Can something be truely random?
* [Random](https://en.wikipedia.org/wiki/Randomness) vs [Noise](https://en.wikipedia.org/wiki/Perlin_noise) (more specifically, Perlin noise)



### Grouping Shapes

* You can "group" shapes together using `push()` and `pop()` functions
  * `push()` **MUST** always be followed by a `pop()`: they are an inseparable pair
  * Everything contained in between `push()` and `pop()` are grouped together.
  * Styles and transformations that happen inside the `push()` and `pop()` remain within.
* Can apply transformations and styles to the group of shapes at the same time.

### Transformations

* See a full list of transformation functions on this [p5.js reference page section](https://p5js.org/reference/#group-Transform)
* [`translate()` function](https://p5js.org/reference/#/p5/translate)
* [`rotate()` function](https://p5js.org/reference/#/p5/rotate)
* Using a combination of `translate()` and `rotate()` to rotate a shape at its center
  * Setting transformation origins with [`ellipseMode()` function](https://p5js.org/reference/#/p5/ellipseMode) and [`rectMode()` function](https://p5js.org/reference/#/p5/rectMode)