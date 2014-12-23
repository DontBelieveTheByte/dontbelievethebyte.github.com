---
layout: post
category : projects
tagline: 
tags : [Perl, projects]
---

##Overview
Save Any Flash Videos In Firefox Using Perl

So I was tired of typing all the time to save my flash videos in Firefox.


I know there are extensions that can facilitate this task but they don't work with all the sites out there so I made a script to do it for me.
You have to wait for the video to finish loading in your browser and run this script and voila!



#!/usr/bin/perl
##
##save_flash_videos.pl
###This will save all open Flash videos in firefox.
###Public domain, do anything you want with this script.
##
use File::Copy;
#Save directory defaults to your home Desktop, change according to your liking.
my $savedir = $ENV{HOME}."/Desktop";
#call lsof and save the output
my @lsof_output = `lsof | grep Flash`;
#save all the videos
foreach $video (@lsof_output){
 my @lsof_arr = split(/\s+/,$video);
 my $from = "/proc/".$lsof_arr[1]."/fd/". substr($lsof_arr[3], 0, -1);
 my $to = $savedir."/".substr($lsof_arr[8],5,-1).".flv";
 copy($from,$to) or die "Copy failed: $!";
 }
##End of script


All you need to do is paste the code into a text file and make it executable.


$ chmod +x save_flash_videos.pl


Run the program from the current directory


$ ./save_flash_videos.pl


Or if you want to add the file to your path


$ sudo cp save_flash_videos.pl /usr/bin/


Feedback is appreciated if you have a better way of doing it. 