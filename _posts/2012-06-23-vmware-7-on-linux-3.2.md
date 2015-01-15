---
layout: post
category : articles
tagline: "How to install VMware 7 on Linux 3.2 kernel when it fails"
tags : [Linux, articles]
---

### The problem

The problem came along when I upgraded my Linux distribution from Linux Mint 11 which runs a 2.6 kernel to a newer Linux 
Mint 13 which is now at version 3.2 for the kernel.

VMware's latest version is now at 8 but doesn't play along very nice with Snow Leopard at the moment since it needs 
patching and my only option was to find a patch for VMware 7 in order to run it on the newer kernel.

### Steps to the solution :

1. Get VMware Workstation 7.1.6.
2. The 3.2 kernel module patch can be found [here](https://www.mediafire.com/da232dad2). **link is dead**
3. A modified kernel patch file can be found [here](https://www.mediafire.com/d342kko2). **link is dead**
4. This file in order to patch the VMware binary to unlock running Mac OS guests. Otherwise, the OS X operating system will always shutdown as it is not officially allowed to do so.
5. Install VMware like you normally would. The kernel modules will fail to compile but that's ok since we are going to patch it.
6. Extract the 3.2 kernel patch anywhere and run the executable script as root.
7. Go into the /usr/lib/vmware/module/source directory and find the file vmblock.tar.
8. Replace vmblock.tar with the vmblock.tar that you just downloaded. If you don't change this, not all modules will compile.
9. Run the vmware executable inside a terminal as root and watch all the modules finish compiling. When you're done, just close vmware.
10. Extract and apply the binary patch in order to be able to run OS guest operating system.
11. Open VMware as user.
12. Enjoy.