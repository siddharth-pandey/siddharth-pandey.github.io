---
layout: post
title: "How to get UnAuthorizedAccess (401) HTTP response when using ASP.NET Forms Authentication and AJAX?"
date: 2014-08-11 17:25:21 +0100
comments: true
categories: 
---

I've a ASP.NET MVC application that uses FormsAuthentication and this application gives single page application experience to users after a user is authenticated where it uses AJAX for all HTTP requests. 

The log out action that I have works fine if user uses the logout button in the user interface and the click handler than performs a HTTP POST to Logout action in Account controller.

Today,I was testing some other feature by setting 1 minute timeout for forms authentication in web.config. After a minute, when I performs a POST action to view a different view in my application, I was shown the user login page as set in the web.config under forms configuration. But I was not able to understand why is this happening. Later I figured out that the FormsAuthentication is doing its work and it detects that this user is not authorized. It then redirects the user to the login url as defined in the configuration.

<!-- more -->

However, my client-side code to handle 401 HTTP status-code was in place but it was not being called at all. That was something to worry about because while writing this code, I tested it many a times. By looking at the Network tab of my Chrome browser, I saw that the response of that request was not 401, it was a 302 i.e. a redirect to login page. And this was the reason my client-side 401 handler was not getting executed. Well, the handler just redirects user to login page so that browser can read the expired cookies.

To solve this issue, I added the code below in the **Global.asax.cs** which solved the FormsAuthentication redirect behaviour. The code below just resets the 302 back to 401 for AJAX requests.

```
protected void Application_EndRequest()
{
    var context = new HttpContextWrapper(this.Context);
    if (FormsAuthentication.IsEnabled && context.Response.StatusCode == 302 
        && context.Request.IsAjaxRequest())
    {
        context.Response.Clear();
        context.Response.StatusCode = 401;
    }
}
```

If you want to write a client-side handler to handle this HTTP status code, you can add the script below in your layout file. The code below assumes that you are using jQuery.

```
<script type="text/javascript">
    $(document).ajaxError(function (xhr, props) {
      if (props.status === 401) {
        location.reload();
      }
    });
</script>
```

**For applications running ASP.NET 4.5 can leverage **`HttpResponse.SuppressFormsAuthenticationRedirect` property and set it to true. When not using AJAX, this can be done in `Application_EndRequest` but if you are using AJAX then it should be done in `Application_BeginRequest` so as to immediately suppress the behaviour on every request. The code looks like this:

```
protected void Application_BeginRequest()
{
    HttpRequestBase request = new HttpRequestWrapper(Context.Request);
    if (request.IsAjaxRequest())
    {
        Context.Response.SuppressFormsAuthenticationRedirect = true;
    }
}
```

With above changes and the client-side error handler, everything should work as expected.



