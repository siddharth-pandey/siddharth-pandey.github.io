---
layout: post
title: "Where is SQLiteDatabase stored in a Android application?"
date: 2015-02-04 06:55:53 +0000
comments: true
categories: [Android, Java, Android Studio]
sharing: true
---

Recently I published an article to help my friend to understand [how to store data using SQLiteDatabase in Android application](http://siddharth-pandey.github.io/blog/2015/01/28/how-to-store-data-using-sqlitedatabase-in-android-application/).

<!-- more -->

I'm using Android Studio as my IDE. To view database, follow the steps below:

    - Run your application either in emulator or physical device.
    - In Android Studio, go to `Tools > Android > Android Device Monitor`. This will open in a separate window.
    - Select your choice of device at the left side of window.
    - Now select `File Explorer` tab from the right side of window.
    - Inside the details area of tab, navigate to `data > data > {your app package name} > databases > {your database name}`
