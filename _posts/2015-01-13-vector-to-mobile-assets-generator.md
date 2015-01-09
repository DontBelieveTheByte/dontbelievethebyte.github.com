---
layout: post
category : projects
tagline: "Export Adobe illustrator vector files to all Android and iOS resolutions"
tags : [Android, ExtendScript, JavaScript, Adobe]
---
{% include JB/setup %}

### Overview

It's not secret that I prefer vector files over raster files whenever it's appropriate to use them.

Android has introduced the [VectorDrawable class](https://developer.android.com/reference/android/graphics/drawable/VectorDrawable.html)
in the most recent version (5.0 Lollipop) but it's excluded from the Support Library meaning that older devices still have to use
PNG assets or leverage a third party library like [AndroidSVG](https://code.google.com/p/androidsvg/).

That's all very nice but you can't always use vectors, especially for the launcher et notification icons and other times 
you just want to use PNGs for your own reasons.

There are other solutions that exists but they all seem to take for granted that you have a raster file saved at maximum
size 

### Supported resolutions

- LDPI 
- MPDI (set up as the base rate)
- HDPI
- XHDPI
- XXHDPI
- XXXHDPI
- Low *
- Normal *
- High *

***iOS support is untested, it should work in theory but it would be nice if an iOS developer gave some feedback regarding
if anything should be fixed.**

### Download

Direct download of [latest version](/assets/vector_mobile_assets_generator/vector_to_mobile_assets_generator_PNG.jsx).

### Installation

In CS6 (not tested with other versions), it's possible to run a script by installing it in the proper directory.

For Mac OS this should be :

On Windows : 

To execute the script, pull it from the menu.

If you do not want to install the script into your CS6 installation folder, it's also possible 

### How to use it

1. You will need to prefix the layers names with an '#' hashtag symbol otherwise it will not be picked up.
2. When you're ready to export your images, you should make so that your layers fit a normal MDPI screen, other exported
files will be shrunk or expanded relative to this size.
3. Run the script
4. Check the generated assets_dump folder for your new files.

### Source code

Vector to Mobile Assets Generator is open source, 
the [full source code](https://github.com/DontBelieveTheByte/vector_to_mobile_assets_generator) is available on github.
Bug reports and constructive comments and suggestions are welcomed.

