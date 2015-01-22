---
layout: post
title: "Why does my mac terminal still uses an older version of Java?"
date: 2015-01-22 16:23:03 +0000
comments: true
categories: [OSX, MAC, Terminal, Utilities, Java, Android, Android Studio]
sharing: true
---

While I was working on my mac, I got a pop up to update Java running on it.
I did all the process that was required. It was also needed by one of my application being developed in Android Studio on latest platform. But when I  checked the version number using `System Preferences > Java` which opens the Java Control Panel in a separate window. If you click on the `About` button under `General` tab of this new window, it displays the Version details which said the following and with other copyright information:

<!-- more -->

```
Version 8 Update 31 (build 1.8.0_31-b13)
```

It was time to check within Terminal as well by following command:

```
java -version
```

That returned an older version of Java. `java version "1.6.xxx"`
I then wasted my time to solve this odd issue. Finally, I got a solution that I also need to [update JDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html) to work with Android Studio. Agree to the terms and conditions and download the file based on the product you have. 

Following the above steps, solved my version issue due to which I was not able to work with Android Studio. And running the above java version command in Terminal returned correct version.

While searching for the solution online, there were many other ways as well and obviously it depends on different kind of issues with java versions with XCode or Eclipse or Android Studio.  


