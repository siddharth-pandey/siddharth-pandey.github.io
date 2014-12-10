---
layout: post
title: "How to customize Chrome Developer Tools?"
date: 2014-09-10 09:22:10 +0000
comments: true
categories: [Developer Tools, Tips & Tricks]
---

I spend most of my programming time within Visual Studio and I never liked the white theme that came out of the box. Same is with the Chrome Developer Tools. I use Dark theme for Visual Studio and want something similar for Chrome as well.

In version 32, custom.css was removed from Chrome. I'll be using an theme extension to setup a custom theme. The old way was to play with a local css file that you can rely on or add your own files.

<!-- more -->

There are many extensions which can help you to have this customization. For my purpose, I'm going to use [DevTools Theme: Zero Dark Matrix](https://chrome.google.com/webstore/detail/devtools-theme-zero-dark/bomhdjeadceaggdgfoefmpeafkjhegbo). Click on the link and install it to add it to Chrome.

Follow the steps below:
 - You need to enable a feature by navigating to [chrome://flags/#enable-devtools-experiments](chrome://flags/#enable-devtools-experiments). 
 - Once enabled, restart chrome.
 - Open Developer Tools and select Settings or gear icon at top right corner.
 - You should see an Experiments tab there, now enable **Allow Custom User Themes.**
 - Reload Developer Tools and you should now have the extension theme enabled.

See it was that easy to have a dark theme. However, if you want to create your own custom style, you will need to create your own extension. You could of course also just change the installed extension stylesheet, but you might want to check the licensing for whether its allowed or not!

If you have followed all the steps above, your developer tools will look like:

{% img center /images/chrome_dev_tools_dark_theme.png 'Dark Theme for Chrome Dev Tools' 'images' %}
