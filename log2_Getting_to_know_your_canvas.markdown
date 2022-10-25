---
layout: default
title:  "Getting to know your canvas"
num: 2
---

So, you’ve done already so much, and yet we await more from you! In this section (guess what) you’ll learn about the canvas, and how to draw. Learn, prosper, and spread the visuals!

## Structure of code, part 1
P5.js adds a specific structure to the code that isn't there in vanilla (normal) javascript. This is achieved with prenamed function, that p5.js expect you to define. We will see a few one along the way, but globaly, the structure is as follow:


```javascript
// Root

function setup() {
	// Is executed only once at the begining
  createCanvas(400, 400);

}

function draw() {
	// Is executed repetitively

}
```

Many things to explain here! 
 * Any lines that starts with `//` is called a comment. A line of code that is not going to be executed, but meant for the coder themselve. A good way to explain to others (or yourself in the future) what is happening in the code. Legibility is very important in bigger project!
 * Here we defined two functions (we'll see what exactly is a function later). As explained in the comments, the code in setup is executed once and that's it, while the one in draw is executed after setup and repetitively.
 * And we call a function (we ask to execute the code inside of it) called `createCanvas` which will define our drawing area. In order to call it, we just add `()` after its name!

Write the code above in your `script.js` file, and from now on, when you add code, ask yourself if it is meant to be executed only once, or in a loop!


## The coordinate system
So, tough luck, here no pencil, if you want to draw something, you’ll need to use... maths. Well, at least numbers.
You will draw using coordinates. Basically, your screen as a grid, full of pixel. In order to pinpoint one particular pixel, you need two pieces of info: at which height of the screen it is and at which width of the screen. Those are coordinates, symbolized as the couple (x,y), x on the horizontal axis, and y on the vertical one. This is in the end a classical two dimensional system. The origin (x=0 and y=0) is on the top left corner of your screen. Positive x goes toward the right, and positive y goes toward the bottom of your screen. Yep, a bit confusing.
It’ll all make sense (or at least a bit more) when you’ll start drawing shapes. And guess what, it’s the next section!

![Coordinate System](https://romamile.github.io/introcode/assets/grid.jpg)


## Drawing geometric primitives
In computer graphics, the basic items that you can draw are called geometric primitives (or just primitives). They range from the basic (dots, lines, rectangles) to the complex (cubes, spheres) to the esoteric (tea pot, monkeys... depending on the software/language you’re using). In our case, we’ll focus with simple ones: mainly dots, lines & rectangles.

For instance, if I want to draw a rectangle in p5.js, I write:

```javascript
  rect(10, 10, 50, 50);
```

Here again, we are calling a function, this time we have stuff between the parenthesis, numbers separated by commas. Those are called *parameters*, information that we feed the function, in order to parametrise its behavior. They are the input of the function. Now, each parametre has a different role. I could tell you, but even better if you manage to guess it by exploring! Try to change their value, and see how that affect your rectangle on screen, look at its position and its size. Playing with code (parameters, functions...) and seeing the result is a fondamental part of exploring and learniing about code. This is a very freeing aspect of code, I hope you will learn to enjoy it!

In this case, they correspond (in order) to position on the X axis, position on the Y axis, width, and height.

Other primitives behave in similar ways:

```javascript
line(10,10,10,90);       // Defines two coordinates in order, and join them in a line
ellipse(75,25,10,10);    // Defines the center, and radiuses of the ellipse
point(75,25);            // Defines a single position and draws a dot
```

Even if basic, you’ve learn a few tools that allow you to express yourself. Why don’t you try to make a little monster’s face out of these shapes?


## Drawing Images
Images behave in a very similar way to rectangle (you define where they are displayed, and their width and height). One big difference is that they need to be downloaded somehow! When you don't have too many of them, the easiest way in p5.js is to preload them.

```javascript
let img;

// Another prenamed function used by p5.js!
function preload() {
  img = loadImage("http://foodandcode.github.io/assets/images/footer_back.png");
}

function setup() {
  // Bellow is the line of code needed to display the image.
  // First the name of the image, then position along X and Y axis, then width and height  
  image(img,0,0,400,200);
}
```


## Colors
So, now you know to draw, let release the full spectrum of your creation by adding colors! The classic separation of color in computer science is over four components: Red, Green & Blue (or RGB), with transparency (or alpha). Each component is an integer (a number with no value after the comma,  no fraction part, no decimals; such as 0, 3, 34 or -20) between 0 and 255 (+1 to the person that guesses why 255 ;) ). 

![grayscale](https://romamile.github.io/introcode/assets/grayscale.jpg)

We have four main ways to apply color. You can apply colors:
 * along the edge of a shape (`stroke`)
 * inside a shape (`fill`)
 * to an image (`tint`)
 * to the whole canvas (`background`)

All four functions are behaving the same way. They expect 3 parameters, in order: Red, Blue, Green. And all but `background` can be used as well with a fourth parametre: transparency. For instance, for a red background with a blue rectangle:

```javascript
function setup() {
	background(255, 0, 0);
	fill(0, 0, 255);
	rectangle(10, 10, 50, 50);
}
```
Wonderful. It is good to imagine `fill`/`stroke`/`tint` as applying a specific color to a brush that you're then going to use to draw the next shapes. So if you want two blue rectangles, and then a green circle a little bit transparent, you would write:

```javascript
function setup() {
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


##d) Your first superpower: Randomness##
Now things are getting serious. Random seems at first … well, random, but there is way much more to it. Lucky you, random is awesome. Or should I say, it’s seen as awesome. What makes Generative Art more or less like a legal LSD is that the human brain is wired to search and find patterns (like when you look at clouds). So when you will show chaos, non organize mess, the brain will try to make sense of it and the spectator will see patterns. Call that co-creation. Yep, that’s fascinating.

In Processing, the basic function for randomness is the lengthy but well named `random(max)` function. Calling the random function will return you a floating number. A `float` is a number with a fraction part, such as 1.34, 10.567 or -13.00. You can call it in three different ways:

```java
random(max); // returns a float between 0 and max
random(min, max); // returns a float between min and max
```

Whenever you put values, would that be for the size or position of primitives, for colors, or for the size of your window, you can put random numbers. For instance, a rectangle with random color would be:

```java
fill(random(255), random(255), random(255), random(255));
rect(25,25,50,50);
```

Try to run multiple times your sketch to see what happens to your results. You will see that if randomness is awesome, controlled randomness is sometime better.

If you want to refer to the size of your windows, and not the resolution of your screen, then you can use two standard variables in Processing: width & height. So if you want a rectangle appearing at a random place in your screen:

```java
fill(random(255), random(255), random(255), random(255));
rect(random(width), random(height),50,50);
```

Try to add a few rectangles by repeating that last line, and see how they color merge depending on the alpha value you use. You can already realize that some range of alpha create better results than others.


##e) Adding dynamism##
I feel you. You want more. After all, this canvas is supposed to be modular, why are we keeping it static? Where is the life? Well, life is in this section.

There are two ways to program in Processing: the one we did (static mode, simple code straight laid down), in which the program follow a chronological line, from top to bottom, and then finish. Then there is another way (active mode, the de facto one), that allow repetition in the behavior. This is the common way to code in Processing. In order to use it, we define two standards functions: setup and draw. The setup function is called once, a the start of the program and after that, the function draw is called repetitively, as long as the program run. A common mistake is to mix both mode (static and active), it'll be clear later, but for now it means that you can't lay code as simply as before, it needs to go either in setup or draw. Here is the default look of your next program:

```java
void setup() {
    //What the function is supposed to do
}

void draw() {
    //What the function is supposed to do
}
```

We define here two functions. A function is defined by what it does, what you feed it (input) and what it return (output).
    The type of returned value is defined before the name of the function. In our case it’s void, meaning that it doesn’t return anything. As in our previous functions, we define the parameters (input) between parenthesis. We have none there. So no input and no output. The code that the function will execute is located between the braces { }. Those braces in general define what we call a block of code. It’s there that you will put the kind of code you wrote in previous sections.

Let’s use this new formalism to regularly add discs:

```java
void setup() {
  size(displayWidth, displayHeight);
  background(0,0,0);
}

void draw() {
  fill(random(255), random(255), random(255), random(255));
  ellipse(random(width), random(height), 50, 50);
}
```

Yay! But there could be a few tweaking… Let’s get rid of the stroke color, and let’s get rid of that annoying cursor. For that, call in the setup function `noStroke()` and `noCursor();`.
Now that’s better.
Even with such simple primitives and behavior, you can already create complex results. Try to tweak the value of alpha to see how to mix best the primitives. And you can also play on the canvas as a whole. Let’s get some shading over time by adding at the start of the draw function the following code:

```java
  fill(0, 0, 0, 20);
  rect(0, 0, width, height);
```

By adding black with a very low alpha, we can simulate a fading off of the drawing. Try to explore other possibilities with the tools you already have at hand.


##f) Interacting##
There are many ways to interact with Processing, would that be with your keyboard, your mouse, your mic, your camera, your smartphone, your Arduino, your ... ok you got it, with almost anything. This workshops doesn’t make an emphases on interaction, but it doesn’t mean you can’t add it on the side.

In this section, we’ll discover another Processing standard function that is triggered each time you press a key on your keyboard: keyPressed.
To sum up:
- setup is only called once, at the beginning
- draw is called endlessly (unless asked otherwise) after setup 
- keyPressed is only called when you press a key on your keyboard
- and as a bonus, guess what does the function mousePressed?

In order to use that function, you define it the same way you did for setup  and draw. Just write outside of any other function:

```java
void keyPressed() {
   //Do something when the key is pressed.
}
```

Whatever code you'll put there (drawing something, changing a color, calling other functions etc. etc.), it'll be executed when you press a key. Now of course, you'll want to have more precision in the selection of the key. That requires some stuff we'll see later on in the workshop (even more that the emphasis here is more on generative art than interactive art, that last part will be for another workshop!). One function that you can call by the press of a button that will be pretty useful is the `saveFrame(nameOfFile)` function. The name says it all: it save the frame as a picture in a file you decide the name of. These files are in your sketch directory, easily accessible from your Processing window by clicking on the menu *Sketch* -> *Show Sketch Folder*.

For instance, if you want to save what is displayed on your Processing window each time you press a key:

```java
void keyPressed() {
 saveFrame("output.png"); 
}
```

Unfortunately here the name is always the same. If you want save multiple frames like output-001.png, output-002.png, ... modify the function as follow: `saveFrame("output-###.png");`.

Another simple interaction that can be pretty useful is `mouseX` and `mouseY` which gives you respectively the x and y current position of the mouse. Try to draw a rectangle that follow your mouse using those variables!

##h) The full Monty##
Here is an example of what you can already realize with your skills. Try to understand the code and then mess with it. Changes the value, add some more rectangles, play with the colors (create a palette for instance!), try to get rid of the resetting `background(0)`... There are many stuff to play with here.

```java
void setup() {
  size(displayWidth, displayHeight);
  noCursor();
  noStroke();
  background(0);
}

void draw() {
  
}


void keyPressed() {
  
  background(0); // get rid of it if you want an accumulation
  
  // Stripe 1 Vertical
  fill(random(255), random(255), random(255), random(255));
  rect(random(width),0, random(300), height);
 
  // Stripe 2 Horizontal
  fill(random(255), random(255), random(255), random(255));
  rect(0,random(height), width,random(300));

}
```

