---
layout: post
title: "The Building Blocks of JavaScript Programs"
date: 2012-11-30
comments: true
---

This post is second is series of learning JavaSciprt fundamentals. You may like to visit this article to go through all the posts in the series.  
  
Now, we will learn some building blocks the bits and pieces, that one should know to write JavaScript code.  
  
**The working demo for this post is [here](http://codepen.io/siddharth-pandey/full/Fxdol).**  

### Outline

- Comments - using which you can write some hints for a piece of code.
- Variables
- Null - a special object in JavaScript programs
- Undefined - which is slightly different primitive type in JavaScript.
- Finding Help - we will see where we can go for any assistance/docs for JavaScript.
- Objects
- Equality - how things are compared in JavaScript which one should be aware of it.

<!-- more -->

### Comments

- The comments in JavaScript is kind of similar to comments syntax available in Java.
- Comments is something that won't output anything as a result like your other piece of code, it is just for your use as it doesn't get rendered by the JavaScript interpreter. 
- Single line Comment - "//", this two forward slash characters is used for single line comments followed by any single line sentence. For example, "// this is a single line comment".
- Multiline Comment - "/\*  your content \*/", the syntax for this comment is forward slash and star to start with, put your multiline sentence after that and close it with start and forward slash. For example - /\* As you know this is a multiline comment, in which you can break the sentence into n number of lines.\*/.
- You might want to use comments for any piece of code in order to instruct yourself or to any other developer in the team that what that code does, etc.
- **The working demo for this post is  [here](http://codepen.io/siddharth-pandey/full/Fxdol).**

### Variables

- Variables in JavaScript are declared with 'var' keyword.
- Variables type is inferred, i.e. they don't have a type until a value has been assigned to a variable. When assigned, the type is then defined from type of value specified.
- **The working demo for this post is  [here](http://codepen.io/siddharth-pandey/full/Fxdol).**

### Null

- Is one of the JavaScript primitive types.
- Null means the absence of a value.
- But when null is used in any boolean expression like in case of a if condition, it evaluates to false.
- **The working demo for this post is  [here](http://codepen.io/siddharth-pandey/full/Fxdol).**

### Undefined

- Is also one of the JavaScript primitive types.
- It represents an unknown value i.e. a variable that has not been assigned anything.
- We encounter undefined when a non-existence object property is called.
- But when undefined is used in any boolean expression like in case of a if condition, it evaluates to false.
- **The working demo for this post is  [here](http://codepen.io/siddharth-pandey/full/Fxdol).**

### Finding Help

- [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/JavaScript)

### Objects

- Everything in JavaScript is an object except for the simple types like string, number, boolean, null and undefined.
- Objects are collection of properties and the values of those properties can be of any type.
- Objects are declared with the object literal notation.   
`var anobject = { firstValue: 'a', secondValue: 2 }; `

  - In the above example, we have created a anobject object, with two properties - firstValue with a string value and secondValue with a numeric value.
- In JavaScript, there is no class construct but we can define our objects and properties.
- **The working demo for this post is  [here](http://codepen.io/siddharth-pandey/full/Fxdol).**

### Equality

- Objects are only equal to them-self.
- Primitives are equal only if the values matches like ("Dog"==="Dog").
- There are two types of equality operators in JavaScript:

  - ==
  - ===
  - The difference between the two is type coercion.
  - == only checks for values but === check for values and also for the type.
  - Use === over == and !== over != as it gives a proper answer comparing value and the type. Although, the decision is yours. 
  - **The working demo for this post is  [here](http://codepen.io/siddharth-pandey/full/Fxdol).**

  [**Keep reading the other post in this series to learn JavaScript.**](http://learnwithsid.blogspot.com/2012/11/learning-javascript-fundamentals.html) Happy Learning!
