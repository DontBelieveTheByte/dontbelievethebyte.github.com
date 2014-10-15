---
layout: post
category : review
tagline: "Just another web scraper"
tags : [reddit, web scraper, perl]
---
{% include JB/setup %}

## Overview
For many reasons, social media is a great source of user generated content. 

Reddit has a lot of links and many of these link to imgur, the prefered way to share pictures on Reddit.

Sometimes it's convenient to be able to save a whole subreddit's picture content. 

Combined with a cron job running at regular intervals, it makes sure that you're not missing anything.

The original scraper coded in Perl is from Joshua ...., it wasn't attached to any public repository but 
the license allowed for modifications, so I did.

The main difference between the original script is how files are named according the post title instead of the
generated link from imgur. This proves to be sem