---
layout: post
category : articles
tagline: "Debug remotely on Android via SSH tunnel"
tags : [android]
---

{% include JB/setup %}

![debuggin](/assets/img/debug-joke.jpg)

### Overview

Suppose you have an Android emulator running on another computer or simply a real connected device via USB and you want to be able to 
install and debug an application from your current workstation.

### How to do it

It turns out that it's pretty easy to do so using an ssh tunnel just make sure that the emulator is already running on the remote computer.

    $ ssh -NL 5556:localhost:5554 -L 5557:localhost:5555 $REMOTE_USER@$REMOTE_HOST

The **-N** switch means to not execute a remote commands, it's a de facto standard flag for forwarding stuff through ssh in general.

The **-L** switch is simply for binding the correct ports.

So respectively : 

* remote port 5554 will be mapped to port 5556 on your local computer

* remote port 5555 will be mapped to port 5557 on your local computer

This even/odd pairing is needed not to interfere with the devices physically connected to your current workstation.

Once the connexion is established, open up another terminal and kill adb.

    $ killall adb

Listing the devices will restart adb and you should see the newly connected android device.

    $ adb devices
    * daemon not running. starting it now on port 5037 *
    * daemon started successfully *
    List of devices attached 
    5200fe4259bcc000	device

Then, just run your application like you normally would from Android Studio or Eclipse and close the tunnel when you're done.
