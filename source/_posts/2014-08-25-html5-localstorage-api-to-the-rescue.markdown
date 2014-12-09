---
layout: post
title: "HTML5 LocalStorage API to the rescue"
date: 2014-08-25 12:34:12 +0100
comments: true
categories: [HTML5, Javascript, RequireJS, Modernizr]
---

Recently I had a need to use HTML5 LocalStorage API in my web application project. The requirement was to save the vertical scroll position of window when a user drills down to low level details by navigating to other view.
I didn't wanted to cookies because cookies are sent on every request to the server and I have no need to send this detail to the server as it is just related to client. 

Then I was left with LocalStorage and SessionStorage as options. I found that SessionStorage is not maintained when the page reloads and when the browser is closed. <!-- more --> So, I opted to use LocalStorage API for this use case and came up with the code below which is a localStorageWrapper module that can be accessed as a module when using RequireJS (a module loader). A client consuming this wrapper is able to set, get, check the existence of a key and clear all the items in client's localStorage. An item that can be save is made up of a key and a value. This value can be just a string or an javascript object that can be JSON stringified and then saved. This can be seen in the set function of the localStorageWrapper module below.

When using these fancy new HTML5 APIs, one should care about the browser support. You can use [CanIuse](www.caniuse.com) website to check it. This is a very good resource to check support for everything and anything related to web.

```
define([], function ($) {
    'use strict';
    var localStorageWrapper = {

        /* add data to localStorage */
        set: function (key, value) {

            /* if the value is an object, stringify it to save it in localStorage */
            if (typeof value === 'object') {
                value = JSON.stringify(value);
            }

            localStorage.setItem(key, value);
        },

        /* retrieve data from localStorage object */
        get: function (key) {
            var data;

            if (!this.hasData(key)) {
                return false;
            }

            data = localStorage[key];

            /* if the data is JSON, try to parse */
            try {
                return JSON.parse(data);
            } catch (e) {
                return data;
            }
        },

        /* check if the item exists and it has data */
        hasData: function (key) {
            return !!localStorage[key] && !!localStorage[key].length;
        },

        /* clear all the saved items in client's localstorage */
        clear: function() {
            localStorage.clear();
        }
    };


    return localStorageWrapper;
});
```

To properly provide graceful degradation, you can use [Modernizr](http://modernizr.com/) to check if client supports a particular HTML5 feature. 
When using Modernizr, the client code consuming the above module looks like:

```
    // using set member of localStorageWrapper
    if (Modernizr.localstorage) 
    {
        localStorage.set("uniqueKey1", "");
    }

    // using clear member of localStorageWrapper
    if (Modernizr.localstorage) 
    {
        localStorage.clear();
    }

    // using hasData and get member of localStorageWrapper
    if (localStorage.hasData("uniqueKey1"))
    {
        var value = localStorage.get("uniqueKey1");
    }
```
