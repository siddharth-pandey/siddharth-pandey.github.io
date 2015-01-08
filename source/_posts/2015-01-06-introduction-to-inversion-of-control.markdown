---
layout: post
title: "Introduction to Inversion of Control"
date: 2015-01-06 19:42:43 +0000
comments: true
categories: [Software Practices, .NET, C#]
sharing: true
---

**What is Inversion of Control (IoC)?**
IoC is basically a pattern that we use to apply Depenency Inversion Principle.
Most people mix DIP, IoC and DI together! Its good to have your concepts clear.

**How does IoC relate to DIP?**
Please read [my post about DIP](http://siddharth-pandey.github.io/blog/2014/12/23/Introduction-to-dependency-inversion-principle/). This priciple says that the high level module should not depend on low level module.
<!-- more -->

It doesn't really says how to do it.
Basically, as discussed above, IoC is the concept or pattern(ish) that we use to define how DIP can be achieved.

Types of Inversion that can be used: 

 - Control over the interface between two systems or components: Interface Inversion
 - Control over the flow of an application: Flow Inversion
 - Control over dependency creating and binding: Dependency Creation or Binding Inversion. Dependency Injection is one of the way to invert control under this Dependency Creation type.




