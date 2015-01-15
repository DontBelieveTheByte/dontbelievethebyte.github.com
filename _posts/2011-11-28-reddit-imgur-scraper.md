---
layout: post
category : projects
tagline: "Collect content from reddit"
tags : [Perl, projects, scripts, web scraping]
---
{% include JB/setup %}

## Overview

For many reasons, social media is a great source of user generated content.

[Reddit](http://reddit.com) has a lot of images and most of these link to [imgur](http://imgur.com) which is the official 
preferred way to share pictures on Reddit.

Sometimes it's convenient to be able to save a whole subreddit's picture content.

This script combined with a cron job running at regular intervals makes sure that you're not missing anything.

Although I appreciate the fact that Joshua Hull put the script out there, it didn't exactly fit my needs.

The original scraper from is coded in Perl wasn't attached to any public repository but
the license allowed for modifications and distribution, so I did.

### Original script 

    #!/usr/bin/env perl
    
    #   Reddit Image Scraper: A perl script to download images hosted on
    #   the imgur.com hosting service linked from a subreddit at reddit.com
    #   Copyright (C) 2011 Joshua Hull
    
    #   This program is free software: you can redistribute it and/or modify
    #   it under the terms of the GNU General Public License as published by
    #   the Free Software Foundation, either version 3 of the License, or
    #   (at your option) any later version.
    #
    #   This program is distributed in the hope that it will be useful,
    #   but WITHOUT ANY WARRANTY; without even the implied warranty of
    #   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    #   GNU General Public License for more details.
    #
    #   You should have received a copy of the GNU General Public License
    #   along with this program.  If not, see <http://www.gnu.org/licenses/>.
    
    use strict;
    use warnings;
    use JSON;
    use WWW::Mechanize;
    
    die "Usage: $0 subreddit [...]\n" unless @ARGV;
    
    foreach my $arg (@ARGV) {
    
        # Create the directory if necessary.
        mkdir $arg unless -d $arg;
    
        my $url = "http://www.reddit.com/r/$arg/.json?limit=1000";
        print "Downloading from http://www.reddit.com/r/$arg\n";
        my $mech = WWW::Mechanize->new;
        $mech->get($url);
        my $json_string = $mech->text();
    
        my $json = JSON->new;
        my $json_text = $json->allow_nonref->utf8->relaxed->decode($json_string);
        my $posts = $json_text->{data}->{children};
        foreach my $post (@{$posts}) {
            my $domain = $post->{data}->{domain};
            my $url = $post->{data}->{url};
            if ( $domain =~ m/i.imgur.com/){
                my $file_name = substr $url, -9;
         if (-f "$arg/$file_name"){
         } else {
                 print "      Downloading $url\n";
                 $mech->get($url,':content_file' => "$arg/$file_name");
                 print "      Done.\n";
         }
            }
        }
    }

### Modified Perl Script

The main difference between the original script is how files are named according the post title instead of the
generated link from imgur which help preserve semantic meaning. 

I just wanted to dump all the images with the name of the file matching the title of the original post on reddit separated 
with underscores instead of the original file name from imgur.

In order to customize which subreddit you'll be scraping, all you really need to do is to fill the @subreddits array with 
the name of the subreddits you want to scrape separated by commas.

Here's an example to download the current images on [r/pics](www.reddit.com/r/pics) and [r/funny](www.reddit.com/r/funny) :

my @subreddits = ("pics", "funny");

So the subreddit pics and funny will be scraped, two directories will be created and all your image files will be there.

    #!/usr/bin/env perl
    
    #   Reddit Imgur Scraper
    #   Copyright (c) J-F B, 2013
    #   This program is heavily based on Reddit Image Scrapper by Joshua Copyright (C) 2011 published under the same license.
    #   
    #   This program is free software: you can redistribute it and/or modify 
    #   it under the terms of the GNU General Public License as published by
    #   the Free Software Foundation, either version 3 of the License, or
    #   (at your option) any later version.
    #
    #   This program is distributed in the hope that it will be useful,
    #   but WITHOUT ANY WARRANTY; without even the implied warranty of
    #   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    #   GNU General Public License for more details.
    #
    #   You should have received a copy of the GNU General Public License
    #   along with this program.  If not, see <http://www.gnu.org/licenses/>.
    
    use strict;
    use warnings;
    use JSON;
    use WWW::Mechanize;
    use YAML::Tiny;
    
    #Load the configuration file.
    my $config = YAML::Tiny->read('config.yml');
    #Set the path where to save the images.
    my $savePath = $config ->[0]->{savePath};
    #Verify is we can use the specified directory from the configuration path.
    if (!-d $savePath && !-w $savePath){
            die "Cannot use specified directory" . $savePath . ".\n Either doesn't exist or unwritable.'\n";
    }
    print "Saving to :  $savePath\n";
    # #Loop over the subreddits array and save the images.
    foreach my $sub (@{$config->[0]->{subreddits}}) {
        # Create the subreddit directory only if necessary.
        mkdir $savePath."/".$sub unless -d $savePath."/".$sub;
        my $url = "http://www.reddit.com/r/$sub/.json?limit=200";
        print "Downloading from http://www.reddit.com/r/$sub\n";
        my $mech = WWW::Mechanize->new;
        $mech->get($url);
        my $json_string = $mech->text();
        my $json = JSON->new;
        my $json_text = $json->allow_nonref->utf8->relaxed->decode($json_string);
        my $posts = $json_text->{data}->{children}; 
        foreach my $post (@{$posts}) {
            my $domain = $post->{data}->{domain};
            my $url = $post->{data}->{url};
            my $title = $post->{data}->{title};
            my $score = $post->{data}->{score};
            #Verify if the post has a high enough score to be worth saving.
            if ($config->[0]->{score} < $score) {
                print "saving : $title \n";
                if ( $domain =~ m/i.imgur.com/){
                    $url =~ /(gif|png|jpeg.|jpg)$/i;
                    my $file_ext = '.'.$1;
                    my $realfile_name = substr $title, 0, 200;
                    print $url.'\n';
                    $realfile_name =~ s/[^a-zA-Z0-9]/-/g;
                    if (!-f "$sub/$realfile_name$file_ext"){
                            $mech->get($url,':content_file' => "$savePath/$sub/$realfile_name"."$file_ext");
                    }
                }
            }
        }
     }
     
Just like any perl script it's appropriate to make it executable.

    $ chmod +x reddit_imgur_scraper.pl
     
You can then set up a cron job to schedule timed scrapping or just call it manually from the directory where you want you 
content to fall. Just make sure that your cron jobs run at regular enough intervals to capture everything you need.

### Source code

You can clone the git repository of this code on [github](https://github.com/DontBelieveTheByte/reddit-imgur-scraper).

### Fix problems

Is this script complaining about something missing? 

You probably need help installing missing perl modules.

If perl complains you're missing modules, just do the following:

    perl -MCPAN 'e shell'
    install "$WHATEVER_MODULE_YOURE_MISSING"
    exit

That's it for now.
