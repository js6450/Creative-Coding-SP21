## Week 3: Object Oriented Programming (OOP)

### What is an Object?

* [Object](https://en.wikipedia.org/wiki/Object_(computer_science)) is an abstract data type, which can include multiple **properties** and **methods**
* For example, let's think of the cat (the whole animal class) as an example of an object. (image source: [freeCodeCamp](https://www.freecodecamp.org/news/object-oriented-programming-concepts-21bb035f7260/))

![Diagram of objects in programming explained using the cat as an example](/_img/cat-oop.png)

* The Cat object can have properties and methods:
  * Properties:
    * Fur color: Color value(s)
    * Eye color: Color value(s)
    * Mood: Number value for level of mood (1 - 10, 1 not happy and 10 very happy)
    * Hungry: Number value for level of hunger (1 - 10, 1 not hungry and 10 very hungry)
    * Energy: Number value for level of energy (1 - 10, 1 not energetic and 10 very energetic)
  * Methods:
    * Sleep: Increases hungry and energy levels.
    * Play: Inreases mood level, decreases energy level. Cries "meow!".
    * Feed: Decreases hunry level, increaes mood level. Cries "meow!".
* There can be multiple instances of the cat object -- basically any individual cat is an instance of the Cat object.
* Summary: Objects are a way to group variables with related functions.

### What is Object-Oriented Programming (OOP)?

* An approach to programming based on the concept of objects -- objects as small building blocks of a program
* OOP programs contain classes and objects:
  * Classes: The definition for the data format and available methods. Template used to create objects.
  * Objects: Instances of classes. Created using the class template.

### Creating Classes in p5.js

* [Example code](https://editor.p5js.org/js6450/sketches/pChh4RQzm)
* Defining a class:
  * Start with the `class` keyword
  * The naming conventions for variables and functions also apply for class names. Conventionally (in languages other than JavaScript, it will actually cause an error if class name is not capitalized), class names are capitalized.

```js
class Bug{
  // code for the Bug class
}	
```

* Defining class constructor: similar to the `setup()` function -- you can use the `constructor` function to initialize values of class properties
  * Create a function called `constructor()`. **DON'T** write the `function` keyword inside class definition.
  * The `constructor()` function only runs **ONCE** when an object is first created using the class definition.
  * Properties that belong to the class must be chained with the `this` keyword. `this` keyword indicates that the particular property belongs specifically to an object.
  * In the code below, for each object created using the `Bug` class, the starting x, y and size variables will be randomized.

```js
class Bug{
  constructor(){
    this.x = random(width);
    this.y = random(height);
    this.size = random(20, 100);
    this.hue = random(360);
  }
}
```

* Defining class methods: Typically, object defined for p5.js have at least 2 methods -- one method to update a property to animate the visualization, and one method to actually display the visualization.

```js
class Bug {
  constructor() {
    this.x = random(width);
    this.y = random(height);
    this.size = random(20, 100);
    this.hue = random(360);
  }

  move() {
    this.x += random(-5, 5);
    this.y += random(-5, 5);
  }

  display() {
    stroke(0, 20);
    fill(this.hue, 100, 100, 10);
    circle(this.x, this.y, this.size);
  }
}
```

### Creating Objects using a Class

* You can create an object using a class definition with the `new` keyword:
  * You can save an object to a variable.
  * Typically, variables that save objects are defined as global variables, above and outside the `setup()` function.
  * Typically objects are created inside the `setup()` function.

```js
let bug = new Bug();
```

### Using Objects in `draw()`

* You can call methods of objects by chaining the variable storing the object with a dot, followed by the method function:
  * The dot indicates that you are referencing the property or method that belongs in the class definition.

```js
function draw() {
  bug.move();
  bug.display();
}
```

* Typically, the class methods are used inside the `draw()` function, in order to continuously move (update) and display visualizations within the p5.js canvas.

### Side Topic: HSB Color Mode

* Using [`colorMode()` function](https://p5js.org/reference/#/p5/colorMode) to change color mode from RGB to HSB.
* You can define maximum for color values within the `colorMode()` function:

```js
colorMode(HSB, 360, 100, 100, 100); //Use HSB color mode with 360 as maximum of hue, 100 as maximum of saturation, brightness and opacity.
```

* HSB is useful when you want to randomize one number to get a range of color hues.

### What is an Array?

* Array is like a list -- it is a **data structure** consisting of a collection of elements
* For example, let's say we want to keep track of the list of fruits we have in the fridge: 
  * banana
  * pineapple
  * apple
  * orange
  * strawberry
* In JavaScript, we can save the list of fruits into a variable by writing:

```js
let fruits = ['banana', 'pineapple', 'apple', 'orange', 'strawberry'];
```

* We can reference the elements inside the array with the **array index**:
  * Start counting with 0, instead of 1: the first element of the array is the 0th element.

| Array Index   | 0          | 1             | 2         | 3          | 4              |
| ------------- | ---------- | ------------- | --------- | ---------- | -------------- |
| Array Element | `'banana'` | `'pineapple'` | `'apple'` | `'orange'` | `'strawberry'` |

* In JavaScript we can get the value of an element in the array by referencing the array index number:

```js
console.log(fruits[0]); // Output: 'banana'
console.log(fruits[3]); // Output: 'orange'
```

* You can get the length of the array with the `length` property of the array:

```js
console.log(fruits.length); // Output: 5
```

### Creating multipe objects using Arrays

* [Code example](https://editor.p5js.org/js6450/sketches/H0jydV8Uu)
* Arrays, in combination of `for` loop and classes can be extremely powerful
