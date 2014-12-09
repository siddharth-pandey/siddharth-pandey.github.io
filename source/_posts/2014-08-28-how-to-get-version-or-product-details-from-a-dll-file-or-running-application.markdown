---
layout: post
title: "How to get version or product details from a .dll file or running application?"
date: 2014-08-28 15:54:26 +0100
comments: true
categories: [C#, .NET, ASP.NET]
---

I came across a scenario where I had to access some information from a file with `.dll` extension. And then I thought to write this post. This information may include that assembly's product name, product version, file version etc. 
This scenario may be required either to read a `.dll` file from disk or from the current running application. The code below covers both the scenarios:

```
// From executing application.
string assemblyVersion = Assembly.GetExecutingAssembly().GetName().Version.ToString();

// From a physical file, provide full path to that file.
string assemblyVersion = Assembly.LoadFile('your assembly file').GetName().Version.ToString();

// From executing application, gives file version.
string fileVersion = FileVersionInfo.GetVersionInfo(Assembly.GetExecutingAssembly().Location).FileVersion;

// From executing application, gives product version.
string productVersion = FileVersionInfo.GetVersionInfo(Assembly.GetExecutingAssembly().Location).ProductVersion;

```
<!-- more -->