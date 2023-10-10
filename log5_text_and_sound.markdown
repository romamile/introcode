---
layout: default
title:  "Text & Sound"
num: 5
---


They say that one picture is worth a thousand words, I still hope you're happy to read me. That being said, it's time for you to write! p5.js isn't a word processor for sure, but it allows quite a few things to do when playing with text. And we start with some good news: at its core, drawing text is extra easy, and done as in the example bellow:


```javascript
	// Should that line go in setup? Or in draw? Who's to know...
text('These are the best of the possible words.', 10, 30);
```

What do we have here? A new function `text`, which -spoiler alert- draws text. Three parameters then, the last two are numbers, defining the position of the top left corner of the text you're going to display. A bit like for the shapes, especially `rect`. Now, hmmm a string of character surrounded by quote marks. We already found that, when we tried to import a picture. This is a new type of value: string, meant to define a text. So, we have string for text and number for ... well, numbers. You can use it in variable as well, for instance:


```javascript
let myVar1 = "Oh my, I'm a variable!"
text(myVar1, 10, 30);
```

These would be used to keep track of name of players and score in video games for exemple. Also, you can apply colors, yay!


```javascript

fill(255, 0, 0);
stroke(0, 0, 0);

let myVar1 = "Oh my, I'm still a variable!"
text(myVar1, 10, 30);
```

If you want to be a little bit more precise in how you organise your text, you can align it with `textAlign` and change its size with `textSize`. Easy!

```javascript
textSize(16);
textAlign(RIGHT);
text('ABCD', 50, 30);
textAlign(CENTER);
text('EFGH', 50, 50);
textAlign(LEFT);
text('IJKL', 50, 70);
```

Last, you can use `textFont` to change the font. Some are possibly installed on your system, some ... are not! For the others, you'd have to get them online, ask me in person if you really want to use different ones :p

```javascript
textFont("Cambria");
text("Am I installed on your system?", 40, 60)
textFont("Arial");
text("Am I installed on your system?", 40, 80)
textFont("Times New Roman");
text("Am I installed on your system?", 40, 100)
textFont("consola");
text("Am I installed on your system?", 40, 120)
```


## Sound
Let's make some noooooise! Which is not so far from what we did with pictures. First, you preload them, then we can play them (and stop them, so ... not totally like pictures). Let's review how we're using assets (so that works for pictures, and for sounds).

First of all, click on the menu on the left on **Assets**. Then, a button on the top bar will appear, **Upload an asset**. Click on it, and upload any file you want. If you don't have music on your computer, you can search for some online. Once it's good, you'll see a new assets on the main panel. Click on it, and on the bottom of the new panel, you'll see **copy URL**. Click on it, and now you have that URL saved in your clipboard! You can use **paste** either with *Ctrl+V* or with your mouse to access it.

Now that it's done, let's see how to trigger some sound!


```javascript

let song;

function preload() {
	// If you have already the function preload defined, just add to it the bellow line
  song = loadSound("THE LINK TO YOUR SONG ASSET");  
}

function setup() {
  // ALL YOUR PREVIOUS CODE
  // ...
  // ...

	song.play();

}

```

Great, some music that is playing. But what if we need to stop it? We can do that by 1) checking if it's playing, and 2) stopping it or playing it, accordingly. Let's do that at the click of the mouse!


```javascript
function mousePressed() {
  if (song.isPlaying()) {
    // .isPlaying() returns a boolean
    song.stop();
  } else {
    song.play();
  }
}

```

You can make a test on `mouseX` and `mouseY` to trigger different sound depending on its position, and create a sampler!

Now you have everything you need to create a little video game or experience. Sound, movement, test & reaction, text, etc. etc. It's time for you to explore a bit on your own, and create your own project. If you want to explore a bit more p5js, its website has wonderful resources: [https://p5js.org/](https://p5js.org/)

