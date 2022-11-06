---
layout: default
title:  "~= A Technical Interlude =~"
num: 4
---


We've done and explored quite a few things already. But now, if we look back at our code, on top of that proud feeling there is the realization that .... it's quite a mess!
Let's review a couple of things, and then use that to both clear our code and our mind (and our soul for those that feel the need).

First of all, you can sum up the basis of computing (and life?) withing two categories: **states** and **actions**. You are, and you do. What you do influence what you are, and what you are influence how you do things. You can take the exemple of a very lovely cat. A cat has a date of birth (a variable that will never change), a name (might change!), and a lot of other states that could evolve over time (favorite food, age, level of hungriness, asleep or not, ...). All those states can be described with **variables**. A name would be a string of character, an age would be a number, the fact that the cat is asleep or not could be a true/false value (called boolean or bool in programming). On the other side, the cat can do a few stuff: eat, meow at you strongly or softly, run at different speed, or throw up! We see here that some functions only affect the cat, some have outside results, and some can be parametrized (the speed of running for instance). Those actions can be described in term of **functions**. We'll see a bit closer below what is a formalisation that would fit both you (hopefully) and the computer we're trying to talk with.


## What's a variable again?
A variable is an information kept in memory on the computer. It is the sum of three things:
 1. A place where that variable is hold in the computer. As a shortcut, we use a **name** to access that (waaaay better than weird strings of numbers...)
 2. The **content** or value that is hold in that place on the computer. So what really matters to us! That would be the name of the cat, or its age.
 3. The way that content is read, defined as the **type** of the variable. Information in a computer is just a bunch of 0 and 1. We saw above that a name is a string, and an age would be a number. The computer needs to know how the content of the variable must be read.

Last, in order to tell the computer that we want to create a variable, we need the `let` keyword. It is used as bellow:

<img src="[https://i.imgur.com/ZWnhY9T.png](https://romamile.github.io/introcode/assets/variable_plus.png)" width=50% height=50%>

Here, we are telling the computer we are creating a variable called `myVariable`, and we are putting the value `45` in it. To be more precise, two things are happening at once:
 1. First we are **declaring** the variable. Giving it a name, but no content.
 2. Then we are **defining/initializing** it, by giving it its first content.

In some language, you need to precise the type (string, number, boolean...) of variable. In others (like here, in Javascript), the type is added by default, depending on the type of content you are assigning to the variable. Here we are assigning a number `45`, so the variable is a number.

Variable can be extra useful. To keep a state in your program, make it evolve over time, and create a behavior from it. Or even just to name things so the program is a bit more clear! Try to replace some numbers in your program by variables, just to see how it goes! It's as easy as replacing a number by the name of your variable! Magiiiiic!



## What's a function again?
Now that we **are**, let's **do** something. As a matter of fact, you've been using functions already quite a lot!! For instance `rect` is a function. And you've even used it with parameters, the things you put between parenthesis after the name of the function, like `rect(24, 24, 50, 50);`. In a similar way, you've already defined functions! Look at you, already doing so much! `setup` and `draw` are two functions that are expected by processing, and given special signification. So, you know already quite a bit, but let's review that.

First of all, if you wanted to use a variable, you would **declare** and **define** it, then **use** it. For a function, you still need to **declare** and **define** it (usually at the same time), and then to "use" it, you need to **call** the function, what you've already been doing with `rect` and the like.

Let's first look at calling a function as it's the thing we're most used to.

![Calling a function](https://romamile.github.io/introcode/assets/function_call.png)

To call a function, you just use its name, and feed it potential parameters inside the parenthesis, separated by commas. For rectangle, it was the position along the X axis, and the Y axis, width, height. Without a documentation, hard to know what parameters do! So 1) don't hesitate to read the [doc](https://p5js.org/reference/)! and 2) don't hesitate to modify those value and guesstimate what they do!

Now that we understand a bit better what a function is, let's see on the picture bellow how to define it and through that, what are the building blocks of a function!
A function is comprised 4 elements:
 1. As for variable, we need to reach the memory in the computer where we host it, and for that, similarly, we use a **name**
 2. Here the **content** isn't just a value, but a whooooole bunch of line of **code**. It's the "what" of the function, what does it do.
 3. As we saw with `rect` functions have potential **parameters** to affect the behavior of the function.
 4. One last thing that is optional as well is a **return**. It's not what the function does, but what it gives back once it's done. `rect` does something (drawing a rectangle), but doesn't returns anything. `millis` does something (measure the time elapsed since the beginning of the program) and returns something (that specific value).

![Defining a function](https://romamile.github.io/introcode/assets/function_def.png)


## Where should all this stuff go?
Ouf, almost done. After all, it's easy to overlook that section, you're not learning any new functions or super stuff to draw on the screen! But what you're getting is even more important => understanding of what you're doing. This is like getting better foundation that will allow you to create amazing little prototypes, games, experiences, art pieces, etc. etc.

One very classic misunderstanding when we start code (especially when we copy paste, which ... you never do of course?!), is not just *what does this line do?* but as well *where should it go?*. The more you'll understanding coding, the more you'll have already structured some code, the easier it will be. But this is an interesting step to reach. First of all, the execution of the code is sequential, in order. If you draw a rectangle, and then a circle, the circle will appear on top of the rectangle. If you divide a variable, and then use it, it will be the divided value that is being used. Second, in p5.JS we are already inheriting a structure that is perfect to learn this *where does what go?* in a safe environment.

```javascript
// ROOT

// Here you define variables to reuse

function setup() {
	// SETUP

	// Here you define code and variable that are meant to be used
	// only once, at the beginning of the program
}


function draw() {
	// DRAW

	// Here you define code and variable that are going to be 
	// repeatedly called in an endless loop

  // The draw function executes once, then loop back, execute again
  // and again, and again ... until you close the program

}

```


Most of your code will go in `setup` or `draw`. You might want to ask yourself the question *Is my code supposed to execute once/at the beginning, or regularly along the program?*, this will help you knowing where it should go.

Also, the structure above is the base. You might want to define other functions, but there should only be one `setup` and one `draw`!! If you see lines of code you should add to `setup`, add them to the function you've already created, and don't create a new one!

Alright, we're good with that, now let's hope the next section is less technical ;) See you there!



