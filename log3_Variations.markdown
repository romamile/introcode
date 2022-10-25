---
layout: default
title:  "Variations"
num: 3
---


Now, all of that is great, but for something on the screen, it's extremely static! Let's make things move!


## TEMP Compter with CPT and definition of variable

## Variation through time
Up until now, we only put static numbers for the parameters of our drawing functions. That created static shapes, no surprise here! With little effort, we can see already things moving. That little effort is called `millis()`, yet another function. What it does is pretty straight forward, `millis` returns the numbers of milliseconds that have elapsed since the beginning of the program, starting at 0.

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



## Variation through randomness
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
## Variation through interaction

Another way to add variation is for yourself to be in control of what's happening! For that to happen, you need to feed information to the computer through controllers. Mouse, keyboard, touch-pads, mic, camera... A lot of possibilities! For now, let's look at mouse & keyboard.

P5.js allows direct access of the position of the mouse, which makes using them pretty easy!

```javascript
function draw() {
    background(0,0,0);

    rect(mouseX, mouseY, 50, 50);
}
```

As easy as that! Try to apply that to different parameters of your code.


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

