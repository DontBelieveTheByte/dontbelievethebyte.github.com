---
layout: post
category : articles
tagline: "Squeeze more performance out of Drupal on shared hosting"
tags : [PHP, Drupal, webdev, articles]
---

### The problem

Let's face it, shared hosting sucks most of the time.

It's perfectly legitimate wanting to squeeze as much as you can from limited resources you're allotted. 

There is a problem with Drupal's plain vanilla cache system, although it makes an honest effort to save up scarce 
those scarce resources and minimize queries by bundling a lot of them together it's still very inefficient.

Because still, even with caching layer turned on, the architecture of Drupal makes it so that the database has to be 
queried again every time a page gets hit despite the active cache system.

It also means that Drupal still has to go execute some PHP code and actually goes through its whole bootstrap process. 

Even if you are on a VPS or a dedicated server, this might not be a problem until you get some more serious traffic or a 
sudden spike from one of you're glorious content going viral. 

Also, if you have a multi user site where users can log in and or and content is more dynamic, there is a chance that 
you might already have a problem or soon will. 

Of course if you control the hardware or can afford better servers, some other solution like memcache, APC, using nginx 
as a proxy or even as your main web server may be more appropriate before you scale horizontally.

Also, this article is not about scaling but about a cache module.

### Is it for me?

Boost may be right for you if you are on a shared hosting package (or not) and you mostly receive anonymous traffic. 

A typical use case would be on a blog, a small business page that doesn't change very often, a non profit organization, etc.

Anything you can think about as long as the content is mostly static but you are also using Drupal for its convenience of 
organizing and maintaining content.

### What is Boost?

As the name implies, Boost really gives your Drupal 7 installation a boost but how?

The difference between serving static html files and serving dynamic content built and served in PHP is tremendous.
 
When you start adding up all the queries that can go through a web server, especially with monster applications like Drupal 
and the fact that you might not be alone on that same server can bring your Drupal installation to a halt very quickly.

So what Boost actually does is it converts your dynamic PHP code that is normally seen as resource intensive for the web 
server and turns it into good old static html files (you can even compress the data) that can be served without breaking a sweat.

![Drupal boost](/assets/img/drupal-boost.png)


### Installation

You will need to set the appropriate permissions for Drupal to write the static files but that's pretty much all you need.

Here is the place where you can download the [Boost module](https://www.drupal.org/project/boost) for Drupal. 

To install it you must have clean URLs enabled. 

If your web server is running Apache, then you must be able to modify your site .htaccess file in order to complete the installation. 

Be sure to read the documentation to know if Boost is right for you set up.
