---
layout: post
category : Article
tagline: "Binary clock Android application in Scala"
tags : [books, reviews]
---
{% include JB/setup %}

Let's make a [binary clock](http://en.wikipedia.org/wiki/Binary_clock) for Android using scala.

![binary clock](binary_clock.png)

We will clone a template project from Scaloid.

    git clone git@github.com:pocorall/hello-scaloid-sbt.git
    
I will rename the project folder to something more appropriate.

    mv hello-scaloid-sbt binary-clock
    

Lets move into the project directory.

    cd binary-clock

Let's remove the old git files, we'll start another git project from scratch.

    rm -rf .git
    git init
    git add .

I will assume that you already have the Android SDK set up and installed with your environment variables correctly defined 
along with SBT in order to build your Scala project.

If for some reason you get a similar error, you will need to set up your path correctly.
    
    
Lets change the project name and edit the build.sbt file using vim.

This is what my build file looks like.

    
Now lets run sbt for the first time, this step take a long time since it will take care to download 
all the necessary dependencies.


Additionally, Intellij IDEA will need the android support plugin, the sbt plugin and the scala plugin installed.


Before we can use the project inside Intellij IDEA, we will need to generate a local.properties files. In order to do that 
let's just run.

    android update project -p


