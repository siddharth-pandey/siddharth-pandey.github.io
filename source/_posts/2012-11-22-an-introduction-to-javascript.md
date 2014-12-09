---
layout: post
title: "An Introduction to JavaScript"
date: 2012-11-22
comments: true
categories: JavaScript
---

We will focus on JavaScript as a programming language rather than its usage in web or ajax based applications. Because, one should know the building blocks of a language to really make most out of it.  

### **Overview**

- What is JavaScript?
- Why is JavaScript important?
- History
- An Hello World demo
- [JS Bin](http://jsbin.com/) / [CodePen](http://codepen.io/) / [JSFiddle](http://www.jsfiddle.net/) / [JSDB](http://www.jsdb.org/)- a handy tool for you.


<!-- more -->

### What is JavaScript?

- It is a scripting language with no static/void/main.
- The language of the browser to handle scripting activities.
- Its a dynamic language which means that one can modify the objects/types on the fly.
- It supports function programming and object-oriented features like other languages for example - Ruby, C#, etc.
- If you are aware of Java syntax, you might find learning JavaScript easy as the syntax is somewhat same because it appeared around the same time when Java was very popular and had lot of buzz in the market.
- Other than the syntax, JavaScript as a language is more close to languages like Scheme and Self semantics.
- It is very simple to learn and is very small/compact.

### Why is JavaScript important?

- Almost all the computers on the planet have JavaScript interpreter. It is possibly the most used language on the planet.
- It has good browser support and vendor like Microsoft, Mozilla, Google, Apple, etc are researching continuously for JavaScript interpreters.
- AJAX/Rich Clients - You might have heard about these terms which uses JavaScript heavily. This was a turning point for this language as people then started focusing more on JavaScript to achieve more and more rich activity in the browser.
- It is a powerful and highly flexible language.
- The usage of JavaScript at server-side is also increasing because of the interest people have in JavaScript and the powerful interpreters.

#### To boost your interest to learn this language:

- A good example of a rich client interfaces in the the browser that you might be aware of or have used is Google Docs Interface where you can just start typing, give formatting from the toolbars, use drawing tools to draw different shapes, etc. 
- Another example can be [Processingjs](http://processingjs.org/), if you love animation. Try spending some time on the demos available on Processingjs website.
- Go to [BallDropping website](http://balldroppings.com/js/) and play with small white balls. It's a Chrome Experiment.
- Also, when playing with above demos, don't forget to open your system's task manager to see the CPU usage (especially for ball dropping animation, if you add many balls). You must know that even though it is possible to create such animations but sometimes, it's not the efficient way to achieve those animations.

### History

- Netscape wanted to have scripting capability to the browser & JavaScript was born.
- Developed by Brendan Eich. 
- First version - Netscape 2.0 (1995)
- Microsoft then implement their own version and named it as JScript (named differently to avoid issues with Javascript trademark).
- In 1996, JavaScript was submitted by Netscape to ECMA International to standardise it as ECMAScript in the ECMS 262 standard.
- Working with DOM within browser was somewhat odd because of different browser notations.
- People discovered JavaScript's brillance while working with Ajax/Web 2.0.
- To ease the cross-browser development, frameworks like prototype and jQuery were and still are a great help.
- The usage of JavaScript at server-side is also increasing. Example: Node.js, the event based web server and CommonJS,  the JavaScript standard library.

### An Hello World demo

- You can find the demo [here](http://codepen.io/siddharth-pandey/full/nEbBw). I will be using [CodePen](http://codepen.io/) to show all the demos. I like CodePen as it allows you to write HTML, CSS, JavaScript and run the sample within the browser. There are different alternatives as well that are listed above at the starting of this post. Feel free to try as they are free.
- Also, one needs to understand that all the browsers renders a webpage from top to bottom, so if you write a heavy script block or which needs some action by a user as in demo above, you won't be able to see the rest of the content below the script tag because it has not been rendered it. 
- To avoid the above problem, you should practise to include all your scripts just above the body end tag which will help in better performance of your webpage as it will load fast. Alternatively, you can run a script when the webpage has finished loading in the browser (example - _window.onLoad() or jQuery's ready() method_).

I think this is enough for a quick introduction to JavaScript and believe me, JavaScript is very important for developer and yeah, it is different to some of our mainstream languages like C# or Java. Also, it is easy to learn and powerful too. [**Keep reading the other post in this series to learn JavaScript.**](http://learnwithsid.blogspot.com/2012/11/learning-javascript-fundamentals.html) Happy Learning!
