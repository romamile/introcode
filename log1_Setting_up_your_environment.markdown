---
layout: default
title:  "Setting up your environment"
num: 1
---

## Web development VS Native development
Coding is not just writing done lines of code, it's understanding processes, knowing your tools, and knowing for what to develop! At a time, you didn't have much choice, you would develop natively (meaning, for a specific platform). Now, web browsers are so powerful that they are almost their own Operating System. As such, you can develop for them, developing directly for the web. Web pages aren't anymore just ways to provide information; they can be whole fetched experiences: a social media platform, an online multiplayer game, a VR experience...

It can be hard to chose which to do, develop natively or on the web. Performances could be a reason to go native, maybe you don't have access to some specific things on a web browser... but the power of the net is usually summed up in "developed once, run everywhere". While design might change, you can run the same webpage on a smartphone (iPhone or Android), a PC (Window, Mac, Linux), a VR headset... This accessibility is what is at the core of the web, this is why we will go in that direction for this course.


## Online web development tools
Having the result of your code online is great for sharing and accessibility. In the same sense, hosting your code online can be very helpful. Easy setup, very accessible, and some magic that is called "hot reloading". You don't need anymore to compile, or relaunch anything, your output is reloaded as you type. Magical!

There are many tools doing such wonders online ([codepen](https://codepen.io), [jsbin](https://jsbin.com)), the one I'm proposing is [glitch](https://glitch.com). First of all, create an account on glitch, and click on <b>new project</b> on the top right, and select <b>glitch hello website</b>. Congratulation, you've just "coded" your first website, you deserve a break!

![Glitch UI](https://romamile.github.io/introcode/assets/glitchUI.png)

On the left you see the menu, with all your files (and a <b>+</b> to add some more!). On the right you have your file edit interface. On the bottom, you have the menu bar. You can already click on <b>Preview</b> and then on <b>Open preview pane</b> which will preview whatever you're doing in your project. On the top right, you will see <b>Share</b>. Click on that button, and then invite some projects members. Anybody you would want to collaborate with, and ... at least me: @romamile! This way I'll be able to access your code and help you directly, even when not physically present.
We are going to use glitch as a 


Here we'll code as cooking. You'll discover a lot of new ingredients. It's normal to be a bit afraid to use them at first. The way we'll use to get to know them is to use them. More and more. Don't be afraid of making mistakes, we promise you, you can't break anything.

## Our weapons of choice

So, web development. Usually, this means HTML, CSS and JavaScript. HTML is meant to be the content of your webpage, and its structure. CSS is meant to be how you display that content, the style of the page. And JavaScript is meant for... everything else! A lot of things that CSS can do now were only possible with JavaScript back in the days. Nowadays, JavaScript is pretty much on par with most standard development language. Not in "how you do things" but more in "what things you can do". 

Since we are not interested in a standard webpage, we'll try to get rid of HTML and CSS as soon as possible in order to focus on JavaScript. Specifically, we'll be using a library for JavaScript. Libraries are blocks of code that somebody else has already coded, for you to reuse. Very very neat shortcuts, and allows you to be much more productive, without doing everything from scratch! In this course, we will be using (p5.js)[https://p5js.org/] a JavaScript library inspired from (Processing)[https://www.processing.org] a wonderful Java library, one of the forefather of creative coding!
While it won't be of use right now, you might want to get [the reference page](https://p5js.org/reference/) kept open somewhere. Good for inspiration, to check examples, and to learn about stuff.

## Setting up our environment, at last!
Open back your glitch project, and open the `index.html` file. Delete everything, and copy the block of code bellow (only time you're allowed to copy paste, so enjoy!):

```html
<html>

  <head>
    <title>p5js Template</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.4.13/p5.js"></script>
    <script src="/script.js" defer></script>
  </head>
 
  <body style="padding:0px">
  </body>
 
</html>
```

Our focus is not on HTML or css, so we'll be quick (feel free to skip that). HTML is not a classic programing language, in that it's more a structure than a set of instructions. It is based on XML (yet another language...) and use tags. Those little words between `<` and `>`. Long story short, the most important things to know about them is that if you open a tag you then need to close it (same name, with a `/` just before the name for the closing one. So like `<html>` and `</html>`.
 
In order of what we're seeing:
 1. First, with the `<html>` tag, we... define an html document. Fair.
 2. Then the header `<head>` defines some global info about the page. Here it defines...
 3. ...with `<title>` the title of the page, and with `<script>` some code to import. The first is the library, the second will be our own code, in a separate file named `script.js`
 4. Last we have `<body>` where our content would be, if we had any! We just add some style to make it appear even more bland than it would otherwise.

Now, the result should be a wonderful white page. All that for that? Yes, a clean blank page is the perfect canvas to fill up! So look at the left menu and open up `script.js`, and see you in next section!


