---
layout: post
title: "Introduction to Dependency Inversion Principle"
date: 2014-12-23 22:40:12 +0000
comments: true
categories: [Software Practices, .NET, C#]
sharing: true
---

Vocabulary required for this article:

 - Dependency Inversion Principle (DIP): This is a principle used in architecting software.
 - Inversion of Control (IoC): This is a pattern used to invert interfaces, flow and dependencies.
 - Dependency Injection (DI): This is the implementation of IoC to invert dependencies.
 - Inversion of Control Container: A framework to do dependency injection.
 - Interface: The term interface will refer to externally exposed way to interact with something.

**What is Dependency Inversion Principle?**

Many developers gets confuse and mix up the terms like DIP, IoC and DI without even understanding the concepts. The root that one needs to know is DIP. It basically states that **instead of lower level modules defining an interface that higher level modules depend on, higher level modules define an interface/abstraction that lower level modules implement.**

<!-- more -->
There are two scenarios in the above concept that we can discuss: 

 - Scenario-1 When lower level modules define an interface that higher level modules depends on: In this case, we will have to change/modify higher level module whenever we modify existing or add new lower level modules with their interface which is not good. For example, lower level modules can be database or service class which may define their interface. In this case, higher level module will have to be changed whenever we modify lower classes.

 - Scenario-2 When higher level module defins an interface that lower level modules implement. In this case, we invert the dependency so that higher level module defines the interface which lower level modules implements i.e. lower level class needs to obey that interface. In this case, high level and low level class both depends on the interface that is defined by the high level class. Say suppose, if we want to add new low level class, it must obey the interface if it wants to be used by high level class. In this way we have inverted the dependency and high level class now controls the usage. Both depends on the interface and now high level class doesn't needs to be changed even in we add low level class with their own implementations.

**Bob Martin's Paper**

[Read his Article in C++ Report May 1996 as he invented this principle and also gave some examples.](http://www.objectmentor.com/resources/articles/dip.pdf)

Here is an summary of what Uncle Bob said:

 - High-level modules should not depend on low-level modules. Both should depend on abstractions.
 - Abstractions should not depend upon details. Details should depend upon abstractions.

He also gave these examples in his paper:

 - **The Copy Program**: [This is the link to view and download sample console application](https://github.com/siddharth-pandey/TheCopyProgram) that discuss the concept of DIP with a simple Copy Program.
 - **Layering**: Say suppose you have an application with layers in it for example, Policy Layer (pl), Mechanism Layer (ml), Utility Layer (ul) in decreasing order of levels i.e. pl calls ml and ml calls ul which means pl depends on ml and ml depends on ul directly. Any changes in ul will add some changes to be done in ml and thus, in pl. This is not a good software design as when a low level module is changed, high level modules needs to be changed which will happen a lot of time during the life time of the project. With the help of DIP, Uncle Bob defines an interface for each layer. For example, pl defines a Mechanism Interface which any layer can implement if it wants itself to be consumed by pl. In our case, its ml. And similarly, ml defines a Utility Interface which ul can obey. So, now the layers don't depend on each other directly, instead the depend on the abstraction defined by high level modules. Any changes to the lower level modules will not effect high level modules because they will obey the abstractions defined by the high level module. So using this concept, we can provide different implementation for Mechanism (ml-2) just by implementing Mechanism Interface and this will not effect pl in any manner.
 - **Button/Lamp (Inverted)**: Uncle Bob gave an example of a button directly depending on lamp in which case, button that has a on and off behaviour will not be reusable as it directly depends on a lamp. So, with the help of DIP, he adds a `IButtonClient` which `Button` and `Lamp` depends on. IButtonClient has On and Off method members using which Button defines a basic abstraction of general on and off behaviour and can act as a base class. Different kind of buttons can then either use Button as abstract class or IButtonClient to provide a different implementation if they want. In this way, both will not depend on each other directly and will also have no effect if the other is modified. That means, they both are reusable. Now, any device like lamp, mobile, computer, etc. can just implement IButtonClient and now they have on and off behaviour of Button deriving from Button abstract class. Here we have created double abstraction by using interface as well as an abstract class.



