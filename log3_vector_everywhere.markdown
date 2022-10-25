---
layout: default
title:  "A bit of movement"
num: 3
---


Now, all of that is great, but for something on the screen, it's extremely static! Let's make things move!

## Your first superpower: Randomness
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

## 2) Animation
Another possible brain. We'll animate our lovely shapes. This animation needs to be described. Two main ways arise:

  * a) constrained by time

We'll defined a movement using time, more precisely the function **millis** which gives us the number of milliseconds ellapsed. Let's divide this because it can gets high pretty quickly, and feed that to the position of a rectangle.

```javascrit
    background(0,0,0);
    rect(millis()/1000, millis()/500, 50, 50);
```

Ok, this is boring. You'd better use that new power on something more fun.


 * Remember the dreaded cosinus and sinus?! They are actually pretty fun

```javascript
      rect(width/2 + cos(millis()/100)*100, millis()/10, 50, 50);
```
 
 * the point is to experiment. You don't need to understand something to experiment, tweak and play with it. Even more: by experimenting and playing with it, you will get a better understanding. While understanding is often necessary to reach new height (or giving a less importance to chance on your way there), it's not a requirement to start doing.

```javascript
      rect(width/2 + cos(millis()/100)*100, height/2 + sin(millis()/100)*100, 50, 50);
```

```javascript
      fill(255,0,0,12);
      rect(width/2  + cos(millis()/100)*100 + random(10),
           height/2 + sin(millis()/100)*100 + random(10),
           50, 50); // Yep, you can do that. spaces or return to line are the same
```



## Adding dynamism
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


## Interacting
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


## 4) Press that button
  * Arcade buttons, mother of most interactions. Its child: the keyboard.
  * It's other child: all devices that are felt as one: foot pedal, makey makey...)
  * Use them. Like, now.

Another couple of functions, **keyPressed** & **keyTyped** for classic keys and control keys. But among those function, a most important new keyword: **if**. The base of coputation. Thesis could be written on it, its importance, what it means, what it represents. It's the atom of the computational world. What it does is test for something, and do one thing if it's true (and optionaly another if it's false). This is the basic of artificial reasoning. After the if, a condition is tested among parenthesis, and among curly brackets (as with functions), the block of code needed to be executed. If you want to do something when something is not valid, then use *else* as done below. You can test many things with conditions. Equality with *===*, comparison with *<* and *>*... many more that we'll discover another time!

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

