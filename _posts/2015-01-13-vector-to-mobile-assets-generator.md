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
in the most recent version (5.0 Lollipop at the moment) but it's excluded from the Support Library meaning that older 
devices still have to use PNG assets or leverage a third party libraries like [AndroidSVG](https://code.google.com/p/androidsvg/).

That's all very nice but you can't always use vectors, especially for the launcher et notification icons and other times 
you just want to use PNGs for your own reasons.

There are other solutions that exists but they all seem to take for granted that you have a raster file saved at maximum
size which I don't like since I'm working on vector files in illustrator.

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

* In CS6, it's possible to run a script by installing it in the proper directory. You simply need to drag and drop the scrip
into the right folder.

For Mac OS this should be in : **$YOUR_ILLUSTRATOR_ROOT_FOLDER/Presets/en_US/**

![layers](/assets/vector_mobile_assets_generator/install_1.png)
![layers](/assets/vector_mobile_assets_generator/install_2.png)
![layers](/assets/vector_mobile_assets_generator/install_3.png)

* If you do not want to install the script into your CS6 installation folder, it's also possible to run it from anywhere
by selecting from the **"Ctrl+F12"** shortcut.

![layers](/assets/vector_mobile_assets_generator/install_ctrl_f12.png)

### How to use it

* You will need to prefix the layers names with an '#' hashtag symbol otherwise it will not be picked up.

![layers](/assets/vector_mobile_assets_generator/how_to_layers.png)

* When you're ready to export your images, you should make so that your layers fit a normal MDPI screen, other exported
files will be shrunk or expanded relative to this size.

![layers](/assets/vector_mobile_assets_generator/how_to_artboard.png)

* Run the script

![layers](/assets/vector_mobile_assets_generator/how_to_run.png)

* Check inside the assets_dump folders containing all of your new files that were generated for you.

![layers](/assets/vector_mobile_assets_generator/how_to_success_dialog.png)

![layers](/assets/vector_mobile_assets_generator/how_to_assets_dump.png)

### Source code

Vector to Mobile Assets Generator is open source, 
the [full source code](https://github.com/DontBelieveTheByte/vector_to_mobile_assets_generator) is available on github.
Bug reports and constructive comments and suggestions are welcomed.

