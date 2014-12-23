---
layout: post
category : projects
tagline: "An open source music player for Android"
tags : [perl, projects]
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

Modified Perl Script

Although I appreciate the fact that Joshua Hull put it up there for free and also to distribute freely, it didn't really fit my exact needs.

I just wanted to dump the images with the name of the file matching the title of the original post on reddit separated with underscores instead of the original file name from imgur.

All you really need to use this script is to fill the @subreddits array with the name of the subreddits you want to scrape. In this example it looks like this :

my @subreddits = ("pics", "funny");

So the subreddit pics and funny will be scraped, two directories will be created and all your images files will be there.

Now, here is the modified script:


#!/usr/bin/env perl

#   Reddit Image Scraper: A perl script to download images hosted on
#   the imgur.com hosting service linked from a subreddit at reddit.com
#   Copyright (C) 2011 Joshua Hull

#Original source available where you got this file at
#   http://dontbelievethebyte.blogspot.com/2011/11/modified-reddit-perl-image-scraper.html .

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

#die "Usage: $0 subreddit [...]\n" unless @ARGV;
my @subreddits = ("pics", "funny");
foreach my $arg (@subreddits) {

    # Create the directory if necessary.
    mkdir $arg unless -d $arg;

    my $url = "http://www.reddit.com/r/$arg/.json?limit=50000";
    print "Downloading from http://www.reddit.com/r/$arg\n";
    my $mech = WWW::Mechanize->new;
    $mech->get($url);
    my $json_string = $mech->text();

    my $json = JSON->new;
    my $json_text = $json->allow_nonref->utf8->relaxed->decode($json_string);
 #print $json_string."\n";
    my $posts = $json_text->{data}->{children};
    foreach my $post (@{$posts}) {
        my $domain = $post->{data}->{domain};
        my $url = $post->{data}->{url};
 my $title = $post->{data}->{title};
 #print "$title\n";
        if ( $domain =~ m/i.imgur.com/){
     my $realfile_name = substr $title, 0, 200;
     $realfile_name =~ s/ /_/g;
            my $file_name = substr $url, -4;
  #print $file_name;
     if (-f "$arg/$realfile_name"){
  #rename "$file_name","$realfile_name";
     } else {
             #print "      Downloading $url\n";
             $mech->get($url,':content_file' => "$arg/$realfile_name"."$file_name");
  #rename $file_name,;
             #print "      Done.\n";
     }
        }
    }
}

Just like any perl script it's useful to make it executable (chmod +x). You can then set up a cron job to schedule timed scrapping or just call it manually from the directory where you want you content to fall.

You need help installing missing perl modules?

If perl complains you're missing modules, just do the following:

perl -MCPAN 'e shell'
install "replace this with whatever module name that needs to be installed"
exit

Done. That's it for now.
