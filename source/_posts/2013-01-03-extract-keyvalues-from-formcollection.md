---
layout: post
title: "Extract key/values from FormCollection in ASP.NET MVC action method"
date: 2013-01-03
comments: true
categories: [MVC, ASP.NET, C#]
---

To avoid you from having to chase for the same information: here's how you extract key / value pairs from the FormCollection that comes as an argument in an ASP.NET MVC action method:  

    public ActionResult Create(FormCollection formCollection){ foreach (var key in formCollection.AllKeys) { var value = formCollection[key]; // etc. } foreach (var key in formCollection.Keys) { var value = formCollection[key.ToString()]; // etc. }}

<!-- more -->

Also, a final tip: If you find that the formCollection does not contain the key/value pairs you expected, check that   

1. Your controls reside within the correct form (you can have more than one)
2. Your controls have names (just having an id is not returning values in the formCollection)
Hope this helps. 
