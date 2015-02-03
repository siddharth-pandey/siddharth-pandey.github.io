---
layout: post
title: "How to migrate an android project from Eclipse to Android Studio?"
date: 2015-01-23 14:32:46 +0000
comments: true
categories: [Java, Android, Android Studio, Eclipse]
sharing: true
---

This post can help you if you have been working on android projects in Eclipse with ADT and want to migrate that project to Android Studio.

Google had made Android Studio the official IDE for Android, so you should migrate to Android Studio to receive all the latest IDE updates.

<!-- more -->

[This is the link](https://developer.android.com/sdk/installing/migrate.html) that shows some steps how to migrate. Below are the same steps:

 - In Android Studio, close any projects currently open. You should see the Welcome to Android Studio window.
 - Click Import Non-Android Studio project.
 - Locate the project you exported from Eclipse, expand it, select the build.gradle file and click OK.
 - In the following dialog, leave Use gradle wrapper selected and click OK. (You do not need to specify the Gradle home.)

Android Studio properly updates the project structure and creates the appropriate Gradle build file.

You can also import the same project in Android Studio by selecting `Import Project` from `File` option in Android Studio. Locate the project and follow thesteps in the wizard. 

Hope following the steps above can help you migrate your project. If you face any issues, post a comment and I'll try help you to solve it.



