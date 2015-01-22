---
layout: post
title: "How to implement feature toggles in .net application with FeatureToggle?"
date: 2015-01-16 10:27:50 +0000
comments: true
categories: 
published: false
---

###SimpleFeatureToggle

In asp.net web application, this toggle can be used by specifying following inside `app.config` or `web.config` file like this:

```
 <appSettings>
    <add key="FeatureToggle.ImportCustomerDataFeatureUsingSimple" value="true" />
  </appSettings>
```

In windows store or phone application, this toggle can be used by specifying following inside `app.xaml` file like this:

```
<Application.Resources>
    <system:String x:Key="FeatureToggle.ImportCustomerDataFeatureUsingSimple">true</system:String>
</Application.Resources>
```