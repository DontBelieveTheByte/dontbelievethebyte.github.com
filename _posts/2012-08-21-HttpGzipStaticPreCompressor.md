---
layout: post
category : projects
tagline: "Compress static files only once on a web server"
tags : [perl, script, nginx, webdev, projects]
---
{% include JB/setup %}

### Overview

This is a helper script to pre-compress files on a web server.

Instead of using on-the-fly compression with the [gzip module](http://nginx.org/en/docs/http/ngx_http_gzip_module.html) it's made 
to leverage the the [Http Gzip Static](http://nginx.org/en/docs/http/ngx_http_gzip_static_module.html) 
module which saves CPU resources by doing the works only once and also allows higher compression rates making both you and 
your users happy (good for mobile because of the smaller size).

### Requirements

- Any unix based system with gzip and touch commands installed

- Perl 5

### Usage

1. Change the @extensions array to indicate which type of files you want to compress.
2. Set a hard coded directory path by changing the $customDir variable or just use a command line parameter when invoking the script.
3. Run the script manually, when deploying/updating your app or set up a cron job to run it at regular intervals.

### Source

The full source code is available on [github](https://github.com/DontBelieveTheByte/HttpGzipStaticPreCompressor). 