---
layout: post
category : articles
tagline: 
tags : [Linux]
---
Install VMware 7 on Linux 3.2 kernel
So if you're trying to delve into iOS development without having to pay for the Apple tax it seems you are left with two options.

Build a hackintosh
Run OS X inside a virtual machine
My laptop has weird hardware and I knew from the start by checking out the HCL (hardware compatibility list) on the OS x86 project page that it probably wouldn't play very nice with OS X. So I decided to install it in a virtual machine.

I didn't want to run Lion because it is more greedy than Snow Leopard and would quickly eat away my poor little 4GB or Ram.

You can get a ready made virtual machines from the usual places (*cough TPB*) if you're not into building your own from scratch. You can also find Lion images if that fits your need.

So the problem came along when I upgraded my Linux distribution from Linux Mint 11 which runs a 2.6 kernel to Linux Mint 13 which is now at version 3.2.

VMware's latest version is now at 8 but doesn't play along very nice with Snow Leopard so the only option was to find a patch for VMware 7.

Things needed :
VMware Workstation 7.1.6.
The 3.2 kernel module patch can be found here.
A modified kernel patch file can be found here.
This file in order to patch the VMware binary to unlock running Mac OS guests. Otherwise, the OS X operating system will always shutdown as it is not officially allowed to do so.
Here are the steps:
Install VMware like you normally would. The kernel modules will fail to compile but that's ok since we are going to patch it.
Extract the 3.2 kernel patch anywhere and run the executable script as root.
Go into the /usr/lib/vmware/module/source directory and find the file vmblock.tar.
Replace vmblock.tar with the vmblock.tar that you just downloaded. If you don't change this, not all modules will compile.
Run the vmware executable inside a terminal as root and watch all the modules finish compiling. When you're done, just close vmware.
Extract and apply the binary patch in order to be able to run OS guest operating system.
Open VMware as user.
Enjoy.