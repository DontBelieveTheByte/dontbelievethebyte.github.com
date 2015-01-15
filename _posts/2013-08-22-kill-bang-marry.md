---
layout: post
category : projects
tagline: "A Symfony2 web application"
tags : [projects, webdev, PHP, Symfony]
---
{% include JB/setup %}

### Overview

I wanted to learn a new web framework and I heard a lot of good things about Symfony.

I decided to recreate my own flavour of the [Kill Bang Marry](http://archer.wikia.com/wiki/Kill_Bang_Marry) game from Archer but with 
celebrities. 


After I spent way too much time meticulously photoshopping over a hundred pictures to get the same cartoon 
effect as in Archer, I was ready to implement the logic. 

Here's the result: 

* The landing page makes you choose between playing with male of female celebrities, additionally you can access the statistics page from there.

![Landing page](/assets/img/kbm/screenshot0.png)

* Here's how a quiz starts, you have to click a a picture, the first click is kill, second is bang and the third is marry.

![KBM quiz](/assets/img/kbm/screenshot1.png)

* Images overlay you selection, pie charts with the results from other users are displayed along with comments and sharing box on social media 
appear after you've casted your vote.

![KBM quiz after vote](/assets/img/kbm/screenshot2.png)

* Stats are computed twice a day

![Statistics](/assets/img/kbm/screenshot3.png)

### What I have learned during this project

* Creating Symonfy [bundles](http://symfony.com/doc/current/cookbook/bundles/best_practices.html), [service containers](http://symfony.com/doc/current/book/service_container.html) and setting up [routing](http://symfony.com/doc/current/book/routing.html)

I have a bundle for managing users which makes extensive use of the hwi/oauth-bundle in order to sign in with Facebook, Google or 
Twitter. This was the hardest part of the project for me, since documentation is lacking at the moment and it involved a lot of trial and error.

Another bundle provides a quiz service to other component of the application, this bundle also exposes a command line utility 
useful working in concert with a combinatorics (found a use for my statistics courses) class that I created for generating all the quizzes.

I make extensive use of the routing system in place in order to filter input and provide valuable information to my controllers.

* [Doctrine ORM](http://www.doctrine-project.org/projects/orm.html)

I have a few entities for modeling quizzes, statistics, and users. The celebrities model doesn't change much and I keep it
 in memory from a hard coded array (probable a bad idea now that I think of it).

* [Assetic](http://symfony.com/doc/current/cookbook/assetic/asset_management.html) for managing assets

I use a custom function to concatenate my JavaScript and CSS files into a single file, less request on the server means 
that I can squeeze more performance out of it.

Additionally, static assets are served from an alternative cookieless domain along with CloudFlare CDN.

* [Automatic deployment](https://www.digitalocean.com/community/tutorials/how-to-set-up-automatic-deployment-with-git-with-a-vps) with [git hooks](http://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks)

I'm using git to push on a VPS, and additional commands are given in order to generate all the assets.

I also created a side project that [pre compresses relevant files](https://github.com/DontBelieveTheByte/HttpGzipStaticPreCompressor) instead of having the web server compress files on the fly 
in order to save CPU resources as much as possible that also runs as a hook.

* [Twig Templates](http://twig.sensiolabs.org/)

It is a really nice template system but I struggled really hard to make CSS work nicely on all types of devices.

* [Graceful degradation](http://en.wikipedia.org/wiki/Fault_tolerance)

I'm making extensive use of SVG so that my user interface scales nicely but it's not always possible to show on all devices so I feed 
them PNG 8-bit indexed files ([pngquant](http://pngquant.org/) produces files as much as 70% smaller without you noticing any difference).

A combination of CSS techniques and JavaScript with [Modernizr](modernizr.com) made it possible for the app to still work on all 
mobile devices even old iPhones and Android devices along with Internet Explorer to the latest Firefox and Chrome.