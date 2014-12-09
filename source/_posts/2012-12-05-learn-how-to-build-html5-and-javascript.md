---
layout: post
title: "Learn how to build HTML5 and JavaScript Apps with MVVM and Knockout (Part - 1)"
date: 2012-12-05
comments: true
categories: [MVVM, JavaScript, CSS3, Knockout, HTML5]
---

One needs to understand the "Separation of Concerns" while building an application:  

1. The Structure i.e. HTML
2. Presentation i.e. CSS
3. Behaviour i.e. JavaScript

Do we use any UI patterns with JavaScript development, like 

1. MVVM or
2. Data binding structures

How should be write structured JavaScript? Should we write in a modular pattern?

<!-- more -->  
  
Also, all apps love data, so, how should we care about data and bindings. Somehow, we need to load data from somewhere, such as using an Ajax service or loading JSON data on your screen and after getting the data how will you respect changes from the user

Knockout is a JavaScript library that can solve the above issues in a very nice and efficient manner.

So, what is Knockout?

1. It allows you to have rich client-side interactivity for your UX provide a good pattern. 
2. It gives you a good separation of structure and behaviour.
3. It provides you to use declarative bindings to be able to help you bind your UI elements, in case, HTML or even may be CSS styles and classes down to your source object. 
4. Offers you to work in MVVM pattern.
5. It has a very good browser support. (IE6+, Firefox 2+, Chrome, Safari, Opera)

Key Concepts of Knockout:

1. Dependency Tracking via observables (eg: a property depending on another property and it is in sync with a UI control and vice-versa(optional).)
2. Declarative Bindings (Instead of using JavaScript to go through DOM and find a particular control with certain ID use can bind the control from the html itself to push data to the UI and pull data from UI again from/to the source object.)
3. Templating Support (eg: you might have repetitive structures in your webpage like list of abc or rows in a list box, rows in a table or li in a ul/ol. You can use templates to take care of those views. You can use jQuery templates with Knockout, or native templates of Knockout or any third party templating engine.)

Demo

- [Hello World Demo](http://codepen.io/siddharth-pandey/full/ovrxL) (Open in a good browser as CodePen needs it.)

The important factor is to understand the MVVM in terms of Knockout: the separation of concerns. 

1. MVVM is just a separation pattern and a way to organise your code structure to make it easier to maintain and to deal with separation and responsibilities.
2. Model-View-ViewModel
3. Not technology specific. ( you might have heard MVVM with XAML and now you are using with Knockout with JavaScript and HTML.)
4. Works well with data bindings. (in this case its html)

MVVM Components

1. We have a view which is this case is HTML. ( is the user friendly presentation of information)
2. We have our model which is in JSON. (javascript object in this case which has a property named as firstName)
3. Between above two, we have logic to separate to how to  present that model JSON data into the view itself and that is our view model. 

  1. It contains all the behaviour for the view that the view needs and can aggregate on or more models to show the data inside the view.
  2. Contains properties like firstName, methods and the Model.

Demo

- [A quick demo using JavaScript's object literal notation](http://codepen.io/siddharth-pandey/full/tcuob)
- [A quick demo using JavaScript's function](http://codepen.io/siddharth-pandey/full/dsmtH)
- [A quick demo](http://a%20quick%20demo%20using%20javascript%27s%20function/)

Visual Studio Extensions for your productivity

- Nuget - to manage 3rd party libraries and references.
- Web Essentials - code collapsing, vendor specific css properties, etc.
- Web Standards Update - html intellisense and validation.
- WoVS Default Browser Switcher - quickly change the default browser from visual studio.
- JSLint - javascript code analysis.
- CSSCop - catches common CSS issues.
- Resharper 6 (trial version only) - javascript refactoring tools.

Begin Coding with Knockout and Visual Studio

- Either download the JavaScript references from  [http://knockoutjs.com/](http://knockoutjs.com/).
- Either get the debugger or minified version from Github.
- Use Nuget to install Knockout.
- Add intellisense for Knockout in Visual Studio for any \*.js files by adding the following: & lt; reference path="/scripts/knockout-2.2.0.debug.js" / & gt; at script-page level.

  - After doing this, whenever you will type ko. you will see all the options that you can use from the Knockout library.
  - It has to be the first line of code in the page and you have to comment it using "///".
  - Or use a tool like Resharper that will add the intellisense support for your project by its own.

Key Resources

- Knockout  - [http://knockoutjs.com](http://knockoutjs.com/)
- Source Code - [https://github.com/SteveSanderson/knockout](https://github.com/SteveSanderson/knockout)
- Documentation - [http://jpapa.me/kodocs](http://jpapa.me/kodocs)
- Forums - [http://jpapa.me/koforum](http://jpapa.me/koforum)
- Tutorials - [http://learn.knockoutjs.com](http://learn.knockoutjs.com/)
- Stackoverflow - [http://jpapa.me/kostackoverflow](http://jpapa.me/kostackoverflow)
- Ryan Niemeyer's Blog - [http://www.knockmeout.net](http://www.knockmeout.net/)
- jsFiddle - [http://www.jsfiddle.net](http://www.jsfiddle.net/)
- CodePen.io - [codepen.io](http://codepen.io/)

Stay tuned for part - 2.