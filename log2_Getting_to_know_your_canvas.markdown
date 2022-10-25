---
layout: default
title:  "Getting to know your canvas"
num: 2
---

So, you’ve done already so much, and yet we await more from you! In this section (guess what) you’ll learn about the canvas, and how to draw. Learn, prosper, and spread the visuals!

## Structure of code, part 1
P5.js adds a specific structure to the code that isn't there in vanilla (normal) JavaScript. This is achieved with pre-named function, that p5.js expect you to define. We will see a few one along the way, but globally, the structure is as follow:


```javascript
// Root

function setup() {
	// Is executed only once at the beginning
  createCanvas(400, 400);

}

function draw() {
	// Is executed repetitively

}
```

Many things to explain here! 
 * Any lines that starts with `//` is called a comment. A line of code that is not going to be executed, but meant for the coder themself. A good way to explain to others (or yourself in the future) what is happening in the code. Legibility is very important in bigger project!
 * Here we defined two functions (we'll see what exactly is a function later). As explained in the comments, the code in setup is executed once and that's it, while the one in draw is executed after setup and repetitively.
 * And we call a function (we ask to execute the code inside of it) called `createCanvas` which will define our drawing area. In order to call it, we just add `()` after its name!

Write the code above in your `script.js` file, and from now on, when you add code, ask yourself if it is meant to be executed only once, or in a loop!


## The coordinate system
So, tough luck, here no pencil, if you want to draw something, you’ll need to use... math. Well, at least numbers.
You will draw using coordinates. Basically, your screen as a grid, full of pixel. In order to pinpoint one particular pixel, you need two pieces of info: at which height of the screen it is and at which width of the screen. Those are coordinates, symbolized as the couple (x,y), x on the horizontal axis, and y on the vertical one. This is in the end a classical two dimensional system. The origin (x=0 and y=0) is on the top left corner of your screen. Positive x goes toward the right, and positive y goes toward the bottom of your screen. Yep, a bit confusing.
It’ll all make sense (or at least a bit more) when you’ll start drawing shapes. And guess what, it’s the next section!

![Coordinate System](https://romamile.github.io/introcode/assets/grid.jpg)


## Drawing geometric primitives
In computer graphics, the basic items that you can draw are called geometric primitives (or just primitives). They range from the basic (dots, lines, rectangles) to the complex (cubes, spheres) to the esoteric (tea pot, monkeys... depending on the software/language you’re using). In our case, we’ll focus with simple ones: mainly dots, lines & rectangles.

For instance, if I want to draw a rectangle in p5.js, I write:

```javascript
function setup() {
  createCanvas(400, 400);
	rect(10, 10, 50, 50);
}
```

Here again, we are calling a function, this time we have stuff between the parenthesis, numbers separated by commas. Those are called *parameters*, information that we feed the function, in order to parametrize its behavior. They are the input of the function. Now, each parameter has a different role. I could tell you, but even better if you manage to guess it by exploring! Try to change their value, and see how that affect your rectangle on screen, look at its position and its size. Playing with code (parameters, functions...) and seeing the result is a fundamental part of exploring and learning about code. This is a very freeing aspect of code, I hope you will learn to enjoy it!

In this case, they correspond (in order) to position on the X axis, position on the Y axis, width, and height.

Other primitives behave in similar ways:

```javascript
function setup() {
  createCanvas(400, 400);
	line(10,10,10,90);       // Defines two coordinates in order, and join them in a line
	ellipse(75,25,10,10);    // Defines the center, and radius of the ellipse
	point(75,25);            // Defines a single position and draws a dot
}
```

Even if basic, you’ve learn a few tools that allow you to express yourself. Why don’t you try to make a little monster’s face out of these shapes?


## Drawing Images
Images behave in a very similar way to rectangle (you define where they are displayed, and their width and height). One big difference is that they need to be downloaded somehow! When you don't have too many of them, the easiest way in p5.js is to preload them.

```javascript
let img;

// Another pre-named function used by p5.js!
function preload() {
  img = loadImage("http://foodandcode.github.io/assets/images/footer_back.png");
}

function setup() {
  createCanvas(400, 400);
  // Bellow is the line of code needed to display the image.
  // First the name of the image, then position along X and Y axis, then width and height  
  image(img,0,0,400,200);
}
```

Don't mind too much that first line with the keyword `let`. It allows to do wonderful things, but that's for later!


## Colors
So, now you know to draw, let release the full spectrum of your creation by adding colors! The classic separation of color in computer science is over four components: Red, Green & Blue (or RGB), with transparency (or alpha). Each component is an integer (a number with no value after the comma,  no fraction part, no decimals; such as 0, 3, 34 or -20) between 0 and 255 (+1 to the person that guesses why 255 ;) ). 

![grayscale](https://romamile.github.io/introcode/assets/grayscale.jpg)

We have four main ways to apply color. You can apply colors:
 * along the edge of a shape (`stroke`)
 * inside a shape (`fill`)
 * to an image (`tint`)
 * to the whole canvas (`background`)

All four functions are behaving the same way. They expect 3 parameters, in order: Red, Blue, Green. And all but `background` can be used as well with a fourth parameter: transparency. For instance, for a red background with a blue rectangle:

```javascript
function setup() {
  createCanvas(400, 400);
	background(255, 0, 0);
	fill(0, 0, 255);
	rectangle(10, 10, 50, 50);
}
```
Wonderful. It is good to imagine `fill`/`stroke`/`tint` as applying a specific color to a brush that you're then going to use to draw the next shapes. So if you want two blue rectangles, and then a green circle a little bit transparent, you would write:

```javascript
function setup() {
  createCanvas(400, 400);
	background(0, 0, 0);

	fill(0, 0, 255);
	rectangle(10, 10, 50, 50);
	rectangle(100, 200, 80, 80);

	fill(0, 255, 0, 80);
	ellipse(200, 200, 100, 100);
}
```

Oh, and if you want no stroke (or fill) for a specific shape, you can then call `noStroke()` (or `noFill()`). Also, if you want your shape to be totally seen, with no transparency, it means you want an alpha to be maximum (in our case, 255).

Did you try to draw a face in the previous section? If so, it’s time to add color to it!


