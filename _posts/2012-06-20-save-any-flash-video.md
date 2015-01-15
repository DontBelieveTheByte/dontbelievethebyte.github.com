---
layout: post
category : projects
tagline: "Foolproof way to save flash videos"
tags : [Perl, scripts, projects]
---

### The problem

Flash makes it hard by default to get the files you're downloading, it uses black magic to try to hide them from your file 
browser.

There are many browser extensions when it comes to saving flash videos, there's also the excellent command line 
utility [youtube-dl](http://rg3.github.io/youtube-dl/) that works most of the time.

The problems is, that websites are trying to avoid user ripping away their videos and it's a cat and mouse game between 
the content providers who try to break such a thing and those who create this type of utilities to get around the limitations.

### The solution

The files flash is hiding from you still exist, you only need to know how uncover them, 
I was tired of typing the necessary commands all the time to save my flash videos in Firefox so I automated the process.

So here's the definitive way to save any flash video in Firefox using a small Perl script.

Just load the video in the browser like you normally would, you have to wait for the video to finish loading in your browser 
and run this script and voila!

      #!/usr/bin/perl
      ####
      #  This script will save all currently open Flash videos in firefox.
      #  Published under the GPLv3 license or later versions.
      #  Full license is available here : https://www.gnu.org/licenses/gpl.html
      #  (c) J-F B 2013
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
      ####
      use strict;
      use File::Copy;
      my $savePath;
      my @lsofOutput;
      #Save directory defaults to your Desktop, or is set by command line path argument.
      $savePath = ($ARGV[0]) ? $ARGV[0] : $ENV{HOME}."/Desktop";
      #Make sure the path exists and is writable.
      if (!-d $savePath && !-w $savePath){
              die "Cannot use specified directory" . $savePath . ".\n Either doesn't exist or unwritable.'\n";
      }
      #Call lsof and fill all videos into an array.
      if (-e '/usr/bin/lsof' && -x '/usr/bin/lsof'){
              print "Looking for videos...\n";
              @lsofOutput = `lsof | grep Flash`;
      } else {
              die "The lsof command doesn't seem available on this system."
      }
      print @lsofOutput;
      if (@lsofOutput){
      #If array is not empty, loop through the array and attempt to save video files to disk.
                      foreach my $video (@lsofOutput){
                              my @videoArr = split(/\s+/,$video);
                              my $from = "/proc/".$videoArr[1]."/fd/". substr($videoArr[3], 0, -1);
                              my $to = $savePath."/".substr($videoArr[8],5,-1).".flv";
                              copy($from,$to) ?  print "Saved $from to $to\n" : warn "Copying of $from to $savePath failed, might not be a valid file.\n";
                          }
      } else{
              print "No video was found during this instance.\n";
      }

### Installation
  
This works on a Mac or any Linux distribution because they both have **lsof**.
 
All you need to do is paste the code into a text file and make it executable.

    $ chmod +x save_flash_videos.pl

Run the program from the current directory

    $ ./save_flash_videos.pl

Or may you want to add the file to your path

    $ sudo cp save_flash_videos.pl /usr/bin/

### Source code

You can clone the git repository of this code on [github](https://github.com/DontBelieveTheByte/save_firefox_flash_videos).

Feedback is appreciated if you have a better way of doing it. 