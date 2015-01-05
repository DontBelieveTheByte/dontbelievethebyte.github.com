---
layout: post
category : articles
tagline: "Squeeze more performance out of Drupal"
tags : [PHP, Drupal, webdev, articles]
---

## The problem

There is a problem with Drupal's plain vanilla cache system.

Although it makes an honest effort to save up scarce resources and minimize queries by bundling a lot of them together. Still, even with cache turned on,  the database has to be queried again every time a page gets hit.

It also means that Drupal still has to go execute some PHP code and actually goes through the whole bootsrap process. Now if you are on a VPS or a dedicated server, this might not be a problem until you get some more serious traffic and if you have a multi user site where users can log in and content is more dynamic there is a change you might already have a problem. You might want to take a look at other solutions like memcache, APC, using nginx as a proxy or even as your main web server.  Also, this article is not about scaling but about a cache module.

Boost may be right for you if you are on a shared hosting package (or not) and you mostly receive anonymous traffic. A typical use case would be on a blog, a small business page that doesn't change very often, a non profit organization, etc. Anything you can think about as long as the content is mostly static and you are also using Drupal for its convenience of organizing and maintaining content.


## What is Boost?

As the name implies, Boost really gives your Drupal 7 installation a boost but how?

The difference between serving static html files and serving dynamic content built and served in PHP is tremendous. When you start adding up all the queries that can go through a web server, especially with monster applications like Drupal and the fact that you might not be alone on that same server can bring your installation to a halt very quickly.

So what Boost actually does is it converts your dynamic PHP code that is normally seen as resource intensive for the web server and turns it into good old static html files (you can even compress the data) that can be served without breaking a sweat.


![Drupal boost](/assets/img/drupal-boost.png)


Here is the place where you can download the Boost module for Drupal. To install it you must have cleanURLs enabled. If your web server is running Apache, then you must be able to modify your site .htaccess file in order to complete the installation. Here's a video explaining it in more details.


Be sure to read the documentation to know if Boost is right for you set up.