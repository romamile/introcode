---
layout: default
title:  "Variations"
num: 3
---


Now, all of that is great, but for something on the screen, it's extremely static! Let's make things move!


## Variation through variables
Up until now, we only put static numbers for the parameters of our drawing functions. That created static shapes, no surprise here! Now, we need to replace those numbers with things that can change. To that effect, we use variables. Instead of using a value, we're using something that holds a value, and can be either accessed or modified. For instance :


```javascrit
	// We definei/declare the variable here
let myVariable;

function setup() {
  	createCanvas(400, 400);
			// We instantiate the variable here (meaning we give it its first value
		myVariable = 0;
}

function draw() {

		// UPDATE
			// We update the value here
		myVariable = myVariable + 1;

		// DRAW
  	background(0,0,0);
			// We use the variable here
  	rect(myVariable, 10, 50, 50);
}
```

The magic keyword here is `let`, which allows you to create a variable. A variable is three things:
 * A **name**, here "myVariable";
 * A current **value**, its content, here "0" at the begining
 * A **type** which is a way to read the content (bits -0/1- in memory, Javascript doesn't make you declare type, it's automated depending on the value you're using. Here it's a number.

Beware of the vocabulary in the comments. You first *define/declare* a variable to be able to use it, then you *instantiate* it to assure that there is a value (and not the void!) on it, and then you can *update/use* the variable in your code.

We will see later different types, but for now, let's keep with numbers. You can use more or less all mathematical operation that you can imagine:


```javascrit
let myVaribable, a, b;

function setup() {
  	createCanvas(400, 400);
		myVariable = 0;
		a = 2;
		b = 5;
}


function draw() {

		// UPDATE
			// Addition
		myVariable = a + b;

			// Substracion
		myVariable = a - b;

			// Multiplication
		myVariable = a * b;

			// Division
		myVariable = a / b;

			// You can use shortcut if you apply the modification to yourself
		
			// This line is the same as myVariable = myVariable + 1;
		myVariable += 1;

			// And as a test, can you guess what this operator is doing?
		myVariable = b%2;


		// DRAW
  	background(0,0,0);
			// We use the variable here
  	rect(myVariable, 10, 50, 50);
}
```

Last, I've separated our `draw` loop in two subsections, *update* and *draw*. It's not necessary, but it's a lovely way to organise your code. First you update your information, and then you display it.


## Variation through time
Variable are amazing, but if you want to control a bit better your movement, you should rely on a code that is executed in a loop, at every frame (because your computer might lag!) you want to rely on a common frame: time. For that, we use`millis()`, yet another function. What it does is pretty straight forward, `millis` returns the numbers of milliseconds that have elapsed since the beginning of the program, starting at 0.

Let's use that new function to control the position/size of our shapes! Beware, now that we want to have some evolving result, we want to code inside of `draw` instead of `setup`!


```javascrit
function draw() {
  	background(0,0,0);
  	rect(millis(), 10, 50, 50);
}
```

That goes... pretty fast. Let's maybe use `millis()/1000` instead of `millis()` in our past code! This will divide the speed by 1000. You can try different numbers, or control other parameters from your code. Oh, and you remember those dreaded cosine and sine from math class?! They are actually pretty fun:

```javascript
function draw() {
    background(0,0,0);

		// Look how much we can combine functions inside one another!
    rect(100 + cos( millis() / 100 )*100, 10, 50, 50);
}
```

The point here is to experiment. You don't need to understand something to experiment, tweak and play with it. Even more: by experimenting and playing with it, you will get a better understanding. While understanding is often necessary to reach new height (or giving a less importance to chance on your way there), it's not a requirement to start doing.



## Variation through mouse
Randomness is awesome. Or should I say, it’s seen as awesome. People look for patterns in everything, and project over the simplest or most random things! In p5.js, the basic function for randomness is the well named `rando)` function. You can call it with one parameter or two, as follow:

```javascript
random(max); // returns a decimal number between 0 and max
random(min, max); // returns a decimal number between min and max
```

As for `millis()`, anywhere in your code that had number can be replaced with randomness. Try it with colors, positions, sizes, etc. etc. If you want to refer to the size of your window, you can use two standard variables: `width` & `height`, used as follow:

```javascript
fill(random(255), random(255), random(255), random(255));
rect(random(width), random(height),50,50);
```


## Variation through keyboard

Another way to add variation is for yourself to be in control of what's happening! For that to happen, you need to feed information to the computer through controllers. Mouse, keyboard, touch-pads, mic, camera... A lot of possibilities! For now, let's look at mouse & keyboard.

P5.js allows direct access of the position of the mouse, which makes using them pretty easy!

```javascript
function draw() {
    background(0,0,0);

    rect(mouseX, mouseY, 50, 50);
}
```

As easy as that! Try to apply that to different parameters of your code. If you want to trigger something (updating a value, drawing something, ...) you can do that with yet another pre-named function from p5.js called `mousePressed`, fitting name.

```javascript
void mousePressed() {
   //Do something when the mouse is pressed.

	 fill(255, 255, 255, 20);
	 ellipse(150 + random(100), 150 + random(100), 100, 100);

	// Just beware! if you're putting "background" in your draw loop,
	// ... you will only see that for a frame!
}
```


## TEMP KEYBOARD + IF

- keyPressed is only called when you press a key on your keyboard

In order to use that function, you define it the same way you did for setup  and draw. Just write outside of any other function:

```java
void keyPressed() {
   //Do something when the key is pressed.
}
```

Whatever code you'll put there (drawing something, changing a color, calling other functions etc. etc.), it'll be executed when you press a key. Now of course, you'll want to have more precision in the selection of the key. That requires some stuff we'll see later on in the workshop (even more that the emphasis here is more on generative art than interactive art, that last part will be for another workshop!). One function that you can call by the press of a button that will be pretty useful is the `saveFrame(nameOfFile)` function. The name says it all: it save the frame as a picture in a file you decide the name of. These files are in your sketch directory, easily accessible from your Processing window by clicking on the menu *Sketch* -> *Show Sketch Folder*.


Another couple of functions, **keyPressed** & **keyTyped** for classic keys and control keys. But among those function, a most important new keyword: **if**. The base of computation. Thesis could be written on it, its importance, what it means, what it represents. It's the atom of the computational world. What it does is test for something, and do one thing if it's true (and optionaly another if it's false). This is the basic of artificial reasoning. After the if, a condition is tested among parenthesis, and among curly brackets (as with functions), the block of code needed to be executed. If you want to do something when something is not valid, then use *else* as done below. You can test many things with conditions. Equality with *===*, comparison with *<* and *>*... many more that we'll discover another time!

Last: key and keycodes are the value of the key last types. Try it out a bit, it'll make way more sense that way than reading a wall of text.

```javascript
   function keyPressed() {
      if (keyCode === LEFT_ARROW) {
         background(255,random(255), 255);
            //keyCodes: https://p5js.org/reference/#/p5/keyCode 
      }
  }

   function keyTyped() {
      if (key === 'a') {
         background(255,0, 255);
      } else if (key === 'b') {
         background(255,255, 255);
      }

}
```

  * You can check out (or ask us) about other function involoved with the mouse and keyboard:  **mouseMoved**, **mousePressed**, **mouseReleased**, **keyReleased**...

