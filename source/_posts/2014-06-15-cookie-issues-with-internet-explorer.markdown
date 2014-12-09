---
layout: post
title: "Cookie issues with Internet Explorer."
date: 2014-06-15 00:07:17 +0100
comments: true
categories: [Browser, Internet Explorer]
sharing: true
---

Recently, I was working on a ASP.NET MVC 5 web application that was using cookies to store some user specific data. This was done by first serializing that object into forms authentication ticket and then encrypting this serialized data and setting this encrypted value to a cookie.
<!-- more -->
While developing this application, I was using Chrome, Firefox, Internet Explorer 10 to test my application and I faced no issues.

When this applicatoin was published on the testing environment, I again tested it on Chrome, Firefox to make sure nothing is broken. But when I tested it on Internet Explorer 10, I was not able to go to home page even after using the right credentials for user-login page. Before I thought it is a issue with user credentials but this was not the reason as the same credentials were working fine on other browsers. I then started my other virtual machines to test the app on IE 8 and 9 but without any success I found the same issue.

I spent many hours checking the logic to create and set cookies, expiration time on it, etc. but nothing helped me to understand the issue that was only happening on IE.

As per [this link](https://connect.microsoft.com/IE/feedback/details/905702/ie11-bug-cookies-fail-to-save-load-when-browsing-a-site-with-underscores-in-its-subdomain) I came to know that this behaviour is by design how IE works. It won’t set a cookie when the hostname/domain contains an underscore. This applies to all version of IE. Below is a comment from Microsoft in the link above:

> The behavior you are experiencing is "by Design". IE won’t set a cookie when the hostname/domain contains an underscore.
Technically, an underscore (like this _ ) is not a DNS character, and while Windows will let you use an underscore when naming your machine, it warns you that doing so may cause problems. Although other software may be more relaxed on whether to allow this, using an underscore in hostnames is not the RFC standard and we are committed to making our browser as standards compliant as possible. 

However, this issue was resolved when I modified the domain to not to have underscore character. And as per this change, I was able to log in successfully and get to the home page as authentication cookie was saved by IE and was sent to the server on every request which means user was authenticated.

Hope this post can save someone's time to solve cookie issues with Internet Explorer (all versions).

