## Week 1: What is "Creative Coding"?

### What is "Creative Coding"?

* What is coding / programming?
* How can you apply creativity to programming?
* What is the goal of creative coding?
  * Build [creative physical tools](https://www.youtube.com/watch?v=hFZFjoX2cGg)
  * Create [generative art](https://en.wikipedia.org/wiki/Generative_art) using [shapes](http://mariuswatz.com/works/abstract01js/) and [text](https://benfry.com/safire/)
  * Create [data visualizations](http://jillhubley.com/project/nyctrees/)
  * Create [immersive experiences](http://flong.com/archive/projects/augmented-hand-series/) and [installations](https://www.teamlab.art/w/shifting_valley_living_creatures/)
  * Build [interactive installations](https://www.youtube.com/watch?v=kV8v2GKC8WA)
  * Create [interactive films](https://stonewallforever.org/)



### Creative Coding: Digital and Physical

* Exploring creative coding in two domains:
  * Digital using [p5.js](https://p5js.org/) -- first half of semester
  * Physical using [Arduino](https://www.arduino.cc/) -- second half of semester



### What is [p5.js](https://p5js.org/)?

* Open-source **JavaScript** library for creative coding that provides us with tools that simplify the process of creating interactive visuals with code in the web browser.
  * Library: collection of pre-written code. 
* What is [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript)?
* What is [Open-source](https://en.wikipedia.org/wiki/Open-source_software)?
* Programming as **sketching** -- we will learn how to program through drawing!



### p5.js Web Editor

* Make [an account](https://editor.p5js.org/signup) to be able to save your p5.js sketches
* Provides code editor on the left side and render view on the right side.
* Also has a "console window" on the bottom-left section



### Structure of p5.js Projects

* HTML file
  * The actual contents for the HTML web page
  * Includes the "Canvas" HTML element -- where p5.js visualizations are being drawn
  * All files liked inside the HTML file: CSS file, p5.js library, JavaScript file
* CSS file
  * For styling the website -- don't need to worry too much about this as we will be creating visualizations with p5.js
* JavaScript files
  * p5.js library
  * sketch.js sketch: where you write your p5.js sketch code



### Pixels on a screen

* What is a [pixel](https://en.wikipedia.org/wiki/Pixel)?
  * 1 pixel = 1/96 inch (0.26mm)
  * Display / Screen resolution = number of pixels available for your display monitor to draw onto

* [Coordinate system](https://editor.p5js.org/js6450/sketches/gCoI-ztDu)
  * Specifying the location of our drawings by x and y coordinates
* **Canvas**
  * Our digital drawing board / area
  * (behind the scenes, if you are interested, check out [Canvas API](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API) article on MDN) 
  * With p5.js, we will be creating a digital canvas that we will draw onto.



### Functions

* What is a function?
  * A way of grouping chunks of code under a specified name
  * You can also provide **arguments** to functions to derive different output depending on input
  * Think of functions as vending machines:
    * Input: Coins, A button press
    * Something "functional" happens that translates inputs to an output
    * Output: The desired drink
  * Basic structure:

```js
// Defining function called functionName
function myFunction()){
  // add a lot of javascript code here
}

// Using functionName function
functionName();

// Defining function with arguments
// Multiple arguments given with comma in between
function addTwoNumbers(numOne, numTwo){
  // Don't worry two much about what the line below does
  // Just showing you that the arguments received can be used inside the function
  return numOne + numTwo;
}

// Using addTwoNumbers function
addTwoNumbers(3, 7);
```

* A lot of the p5.js library is based on functions



### Code Commenting

* You can add comments to your code -- these comments will be ignored by the complier / renderer / program.
* Use comments to write notes for yourself and others who are looking at your code

```js
// This is a JavaScript comment
```



### `setup()` and `draw()`

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



### Drawing Shapes with p5.js

* [p5.js references on shapes](https://p5js.org/reference/#group-Shape)

* [Coordinate System and Shapes](https://p5js.org/learn/coordinate-system-and-shapes.html) article on p5.js
* Short note on how to read p5.js references:
  * Taking a look at [`ellipse()` function](https://p5js.org/reference/#/p5/ellipse) documentation, for example:
    * Description: describes what the function does
    * Syntax: showcases one or more way(s) of how the function can be used
      * If any arguments inside the function is in square brackets ([ ]), the argument is optional.
    * Parameters: Describes what each of the arguments of the function will be used for
      * Order of arguments matter -- for example, the `ellipse()` function used used with arguments `ellipse(x, y, w, h)`, where the first number is used for the x coordinate for the ellipse center, the second number is for the y coordinate for the ellipse center, the third  number for the width of the ellipse and the forth number for the height of the ellipse.



### Color

* [p5.js references on color](https://p5js.org/reference/#group-Color)
* [Color](https://p5js.org/learn/color.html) article on p5.js
* Representations of color:
  * RGB (red, green, blue)
  * Hex (also red, green, blue but in hexadecimal numbers)
  * HSB (hue, saturation, brightness)
  * Opacity