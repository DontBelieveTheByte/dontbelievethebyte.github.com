---
layout: post
category : articles
tagline: ""
tags : [Drupal, webdev]
---
{% include JB/setup %}

### Overview
![Baconology.org](/assets/img/baconology/baconology.png)

[Baconology.org](http://baconology.org) was one of my first websites. I set it up four years ago to start learning about
Drupal, to learn about web development in general and to show the world my undying love for bacon.

It runs a Drupal 6 installation since the beginning with many modules, custom views and panels.
I know that I should have probably updated it to Drupal 7 or even 8 a long time ago but here comes the time that I'm
ready to pull the plug on the site since I no longer want to maintain it. Here's the recipe that I used in order to
archive my Drupal site.

### Strategy

I had a few options from the start.

- Using the [boost module](https://www.drupal.org/project/boost), since it serves static html content but the problem of
running PHP and a database in the background still remains.
- I could also use the [static generator module](https://www.drupal.org/project/static). This seemed perfect but it's
only compatible with Drupal 7. My site is too customized for a major version update to be a possibility in the present
scenario.
- Mirroring the content using a page scraper and installing back the result of those files onto my server.
That's the solution I settled for in the end.


### Backing up the live site
I already have a shell script running daily. It uses rsync to take care of mirroring files and pipes the result of a
mysqldump into a remote location.

I'm running a local copy of Drupal in order to archive the site faster but it shouldn't affect you if you do otherwise.
After modifying my /etc/hosts to point the domain to my localhost, copying the nginx configuration file,
installing the websites files and seeding the database I was ready to start.

### Problems
I did one last update of the Drupal core and all of the modules I'm using and problems started popping up.

For arbitrary reasons, it seems that the Drupal development team wanted to keep backwards compatibility at all cost. This
goes all the way back to

    strict warning: Non-static method view::load() should not be called statically in

This happens because I'm using PHP 5.5.6 which has a strict mode. PHP doesn't like when you call instance methods
in a static manner.

    #Bad
    view::load();
    #Good
    $view->load();

This produces a nasty error block message on top of every web page. Turning off and playing with PHP's error reporting
doesn't seem to fix any of the problem at all.

I found a fix by install the [Disable messages module](https://www.drupal.org/project/disable_messages) and checking off
 the appropriate permissions for anonymous users was enough to get rid of the nasty messages.

Any ajax request back to the server has to go, so I had to deactivate the infinite scroll module and reinstate the good
old pager. It's not a nice but I'm willing to live with the compromise.

If you have live filters or forms exposed to the user, they must go too.

### Generating the static content

I settled on [HTTrack](http://www.httrack.com/) for mirroring the whole website. The command line wizard got me going
quickly and I all had to do is wait for the job to finish. Since I'm running a local installation is was faster than
having to go through a remote internet connexion.

### Pulling the plug
After changing my nginx configuration to something more simple, I simply removed all the remaining PHP files
and replaced them with my static copy.


