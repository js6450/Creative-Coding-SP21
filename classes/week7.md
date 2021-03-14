## Week 7: Image Manipulation (+ more data viz)

[back to main](../index.md)



### Image Assets Used in Example Codes:

* found on the internet, but prepped (changed image sizes to be suitable for image manipulation) 

* [flower](flower.jpeg)
* [smile](smile.png)



### Loading Images

1. On the p5.js web editor: add the image file you want to use by going to Sketch Files > Upload File. Select or drop files in the popup window and make sure you see the image file appear in the Sketch Files directory (left-side window)
2. The image assets must be loaded in the `preload()` function -- remember that `preload()` function runs before `setup()` function

```js
let smile;
let flower;

// runs before setup()
function preload(){
  // load 'smile.png' file as image object and save to smile variable
  smile = loadImage('smile.png');
  // load 'flower.jpeg' file as image object and save to flower variable
  flower = loadImage('flower.jpeg');
}
```



### Displaying Images in the Canvas

* Use the [`image()` function](https://p5js.org/reference/#/p5/image) to display images

```js
// draw flower image at (0, 0) with image width of canvas width and image height of canvas height
// (0, 0) represents the top-left corner position of the image
image(flower, 0, 0, width, height);
```

* Specify the image object you want to draw as the first argument of `image()` function
* Specify the top-left position of the image as the second and third arguments
  * You can change this using the `imageMode()` function -- by using `imageMode(CENTER)`, the specified position will be used for the center point of the image
* Optionally, specify the width and height of the image
  * If unspecified, the native size of the image will be used



### Applying filters

* [Example Code](https://editor.p5js.org/js6450/sketches/UqVgxYfRM)
* Use the [`filter()` function](https://p5js.org/reference/#/p5/filter) to apply filters to images (all elements -- including shapes) drawn BEFORE the function is called

```js
// draw flower image at (0, 0) with image width of canvas width and image height of canvas height
// (0, 0) represents the top-left corner position of the image
image(flower, 0, 0, width, height);

// apply POSTERIZE filter with 5 color channels
filter(POSTERIZE, 5);
```



### Getting & Setting Pixel Data

* [Example Code](https://editor.p5js.org/js6450/sketches/xB7KbjAdy)
* NOTE: When using this method, make sure your image is VERY small (no more than 150px width and height), and avoid using this method in the `draw()` function. If using inside `draw()`, make image size much smaller.
* Getting pixel data using `.get()` method

```js
// get the pixel data located at (x, y)
// get() method returns an array of 4 numbers:
// col[0] is red value of the pixel
// col[1] is green value of the pixel
// col[2] is blue value of the pixel
// col[3] is alpha (transparency) value of the pixel
let col = smile.get(x, y);
```

* Setting pixel data using `.set()` method

```js
// set color at (x, y) to one with red value of 0, green value 0, blue value of 255 and alpha value of 255
// third argument of .set() method is an array of four numbers, like what we received as resuit of the .get() method
smile.set(x, y, [0, 0, 255, 255]); 
```

* Applying changes to pixel data to the image using `.updatePixels()` method

```js
// Apply newly set pixel values to smile image
smile.updatePixels();
```



### Getting the `pixels` array

* [Example Code](https://editor.p5js.org/js6450/sketches/AUPTNM1rG)
* Note: This method is more efficient than using `.get()` and `.set()` methods, but nonetheless is very "expensive" -- meaning this will slow your sketch & computer down a lot. Avoid using big image files with this method.
* Getting an array of pixels of an image using the `.loadPixels()` method

```js
// load pixels of flower image to flower.pixels array
flower.loadPixels();
```

* The `pixels` array is a one-dimensional array of numbers. For example, if an image only has 3 pixels, the `pixels` array will look like below:

```js
[255, 0, 0, 255, 255, 255, 0, 255, 0, 0, 255, 255]
```

* For each pixel in an image, there are 4 numbers in the `pixels` array, for red value, green value, blue value and alpha (transparency) value
* Iterating through rows and colums of pixels in an image using nested for-loops

```js
// iterate through all rows of pixels in flower image
  for(let y = 0; y < flower.height; y++){
    // iterate through all columns of pixels in flower image
    for(let x = 0; x < flower.width; x++){
      // pixels is an array of numbers -- need to calculate the index of the array using x and y position of the pixel
      let index = (x + y * flower.width) * 4;
      
      // flower.pixels[index] -- Red value
      // flower.pixels[index + 1] -- Green value
      // flower.pixels[index + 2] -- Blue value
      // flower.pixels[index + 3] -- Alpha (transparency) value
    }
  }
```

* Calculating the index of the pixel in the `pixels` array, based on the x and y position of the pixel -- take a look at the GIF in the Double For Loop section of the [Image Processing in p5.js](https://idmnyu.github.io/p5.js-image/) tutorial

```js
let index = (x + y * flower.width) * 4;
```



### More Data Viz + Image Manipulation

* [Code Example](https://editor.p5js.org/js6450/sketches/aPcQI44B0)
* Loading csv tables using [`loadTable` function](https://p5js.org/reference/#/p5/loadTable) in the `preload()` function

```js
function preload() {
  // load 'us-states.csv' file, specifying the type as 'csv' and indicating first row of table is 'header'
  // run parseData() function when table is loaded
  table = loadTable('us-states.csv', 'csv', 'header', parseData);
}
```

* loadTable creates a [p5.Table object](https://p5js.org/reference/#/p5.Table) with the given data -- use the methods of the p5.Table object to parse through saved table data
* Assets: map images edited using photoshop (got outline images, selected area inside outline and set color to a solid primary color)
  * Data: [New York Times](https://raw.githubusercontent.com/nytimes/covid-19-data/master/us-states.csv)
  * [New York State map](new_york.png)
  * [Florida State map](florida.png)