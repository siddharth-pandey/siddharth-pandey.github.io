---
layout: post
title: "How to add a set of directories to environment variable $PATH on a mac?"
date: 2014-06-06 12:22:14 +0100
comments: true
categories: [OSX, MAC, Terminal, Utilities]
sharing: true
---

I often find myself installing a software or package for my projects while working on mac where I need to add a specific path to my $PATH variable.
So, I thought to write this quick post. Below is the directions to achieve the above goals:
<!-- more -->
- Open Terminal on Mac from Applications or Spotlight.
- Now run the command below:


```
 sudo nano /etc/paths
```

- When prompted, you need to enter your password and hit Enter.
- If your password is correct, you will be shown a file. Go to the bottom of the file and enter the new path.
- Hit control + x to quit.
- Enter "Y" to save the modified buffer.

So, above are the steps you need to take in order to add a new path to $PATH variable on mac. To test it, open a new terminal window and type:

```
 echo $PATH
```
You will be able to see all the paths that exists including the one your have recently added. If in case, you don't see the path added by you then try following the above steps carefully.

