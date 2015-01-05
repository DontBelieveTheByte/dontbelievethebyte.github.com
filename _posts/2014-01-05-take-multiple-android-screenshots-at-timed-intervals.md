---
layout: post
category : articles
tagline: "Take"
tags : [Android, Bash]
---
{% include JB/setup %}

## The Problem
Taking multiple screenshots from an Android device or emulator presents a few problems.
Different implementations of the emulator are buggy, especially since the introduction of the video capture feature on
KitKat and up when used in conjunction with the native GPU feature.

## A solution

Assuming you're already connected to an emulator using adb, you can take screenshots at different intervals using the
following script.

    #!/usr/bin/env bash

    if [[ $1 =~ ^-?[0-9]+$ ]]; then
        echo "Screenshots at interval of $1 seconds"
    else
        echo "Not a valid interval"
        exit
    fi

    while true; do
        DATE=`date +%H%M%S`
        adb shell screencap -p /sdcard/$DATE.png
        adb pull /sdcard/$DATE.png
        adb shell rm /sdcard/$DATE.png
        sleep $1;
    done
