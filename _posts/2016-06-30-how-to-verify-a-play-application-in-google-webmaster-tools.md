+++
date = "2016-06-30T11:38:51+02:00"
title = "How to verify a Play Framework application in Google's Search Console"
tags = ["Play Framework", "Google Search Console"]

+++

In order to verify your website in Google's Search Console (previously 
called Webmaster Tools) you have to host a specific file at a specified 
URL. This is really simple to do and needs only two steps to fix.

<!--more-->

1.  First download the file provided by Search Console to the */public* 
    folder in your application.
2.  Add the following line to the */conf/routes* file:

> GET         /google(something).html    controllers.Assets.at(path="/public", file="google(something).html")

Replace (something) with the filename provided by Google.