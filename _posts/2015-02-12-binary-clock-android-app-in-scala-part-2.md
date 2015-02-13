---
layout: post
category : Article
tagline: "Build a binary clock Android application in Scala - Part 2"
tags : [Android, Scaloid, Scala]
---
{% include JB/setup %}

### Introduction

In the [first part](/article/2015/02/11/binary-clock-android-app-in-scala-part-1/) of this tutorial, 
we took care of cloning a template project and setting up our environment.

In this part, we will set up a new activity, define a new layout and clean up the project files.

### Layout

First, I'm going to create a new layout avoiding the traditional XML and doing it programmatically using only Scala.

![led_on](/assets/img/binary-clock/layout_screenshot1.png)

In order to do this, we're going to need two png drawables for the different states of the LEDs.

One for the on state.

![led_on](/assets/img/binary-clock/led_on.png)

Another for the off state.

![led_off](/assets/img/binary-clock/led_off.png)

Next, let's create a new activity that will replace the default HelloScaloid activity. 

I'm going to call this new activity BinaryClock that extends the SActivity and I'll define a few members.

I keep references to all the image views inside the class scope since they will be updated when the time changes from another method.

I also keep a single reference to the drawables I'll be using in order to avoid repeating myself.

Then I define layout parameters and gravities for the sake of clarity further down.

The lazy val declarations makes it possible to protect against NPE before the values are initialized during the oncreate 
callback event, it is only when these variables are de-referenced for the first that an object will be instantiated and 
their values will be set accordingly.

    class BinaryClock extends SActivity{
      //Seconds first column LEDs
      lazy val s0Led1 : SImageView = new SImageView()
      lazy val s0Led2 : SImageView = new SImageView()
      lazy val s0Led4 : SImageView = new SImageView()
      lazy val s0Led8 : SImageView = new SImageView()
    
      //Seconds second column LEDs
      lazy val s1Led1 : SImageView = new SImageView()
      lazy val s1Led2 : SImageView = new SImageView()
      lazy val s1Led4 : SImageView = new SImageView()
      lazy val s1Led8 : SImageView = new SImageView()
    
      //Minutes first column LEDs
      lazy val m0Led1 : SImageView = new SImageView()
      lazy val m0Led2 : SImageView = new SImageView()
      lazy val m0Led4 : SImageView = new SImageView()
      lazy val m0Led8 : SImageView = new SImageView()
    
      //Minutes first column LEDs
      lazy val m1Led1 : SImageView = new SImageView()
      lazy val m1Led2 : SImageView = new SImageView()
      lazy val m1Led4 : SImageView = new SImageView()
      lazy val m1Led8 : SImageView = new SImageView()
    
      //Hours first column LEDs
      lazy val h0Led1 : SImageView = new SImageView()
      lazy val h0Led2 : SImageView = new SImageView()
      lazy val h0Led4 : SImageView = new SImageView()
      lazy val h0Led8 : SImageView = new SImageView()
    
      //Hours first column LEDs
      lazy val h1Led1 : SImageView = new SImageView()
      lazy val h1Led2 : SImageView = new SImageView()
    
      //Drawables
      lazy val ledOffDrawable = getResources.getDrawable(R.drawable.led_off)
      lazy val ledOnDrawable = getResources.getDrawable(R.drawable.led_on)
    
      //Layout params definitions
      lazy val ledColumnLayoutParams = new LinearLayout.LayoutParams(40 dip, 200.dip)
      lazy val legendColumnLayoutParams = new LinearLayout.LayoutParams(20 dip, 200.dip)
      lazy val separatorColumnLayoutParams = new LinearLayout.LayoutParams(8 dip, 200 dip)
      lazy val squareElementLayoutParams = new LinearLayout.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, 40 dip)
    
      //Columns gravity definitions
      val ledColumnGravity = Gravity.BOTTOM | Gravity.CENTER_HORIZONTAL
      val legendColumnGravity = Gravity.TOP | Gravity.CENTER_HORIZONTAL
      val separatorColumnGravity = Gravity.BOTTOM | Gravity.CENTER_HORIZONTAL
      val squareElementGravity = Gravity.CENTER | Gravity.CENTER_HORIZONTAL
    }
    

After, I define a few helper methods that will take care of styling the UI elements. Each will accept a specific type of Android UI
widget and set the correct attributes.

    def styleBinaryPlaceHolder (t: STextView): STextView = {
      t height 40.dip  typeface Typeface.MONOSPACE textSize 10.dip gravity Gravity.CENTER textColor getResources.getColor(R.color.label)
    }
    
    def styleTimePlaceHolder (t: STextView): STextView = {
      t height 40.dip  typeface Typeface.MONOSPACE textSize 15.dip gravity Gravity.CENTER textColor getResources.getColor(R.color.label)
    }
    
    def styleLedDrawable (i: SImageView): SImageView = {
      i backgroundColor android.R.color.transparent imageDrawable ledOffDrawable layoutParams squareElementLayoutParams scaleType ImageView.ScaleType.FIT_CENTER
    }

Since we reference R.color into the previous methods, it's important to define colors.xml with the appropriate elements.
We only two colors, one the for background and another for the text labels. This also makes it easy to change colors later on.

    <?xml version="1.0" encoding="utf-8"?>
    <resources>
        <color name="background">#f62a2a2a</color>
        <color name="label">#ffffdf10</color>
    </resources>

Next, let's implement the onCreate method, it's analogous to the regular onCreate event from a Java Activity.

In this method, I will assemble the elements of the layout in 8 columns nested into a root layout of type of LinearLayout.

All the columns are also LinearLayouts but Scaloid provides syntactic sugar in order to avoid having to manually specify a 
vertical LinearLayout.

These columns of LinearLayouts contain various elements, either image views containing the LED drawables or text labels helping 
the user.

In order to style these elements, I call the helper methods that I previously defined.

    onCreate {
  
      //Linear layouts that will make all the different the columns
      val binaryLegendLeft = new SVerticalLayout {
        style {
          case t: STextView => styleBinaryPlaceHolder(t)
        }
        STextView("8")
        STextView("4")
        STextView("2")
        STextView("1")
      } gravity legendColumnGravity layoutParams legendColumnLayoutParams
  
      val binaryLegendRight = new SVerticalLayout {
        style {
          case t: STextView => styleBinaryPlaceHolder(t)
        }
        STextView("8")
        STextView("4")
        STextView("2")
        STextView("1")
      } gravity legendColumnGravity layoutParams legendColumnLayoutParams
  
      val hours0 = new SVerticalLayout {
        style {
          case t: STextView => styleTimePlaceHolder(t)
          case i: SImageView => styleLedDrawable(i)
        }
        this += h0Led1
        this += h0Led2
        this += h0Led4
        this += h0Led8
        STextView("H")
      } gravity ledColumnGravity layoutParams ledColumnLayoutParams
  
      val hours1 = new SVerticalLayout {
        style {
          case t: STextView => styleTimePlaceHolder(t)
          case i: SImageView => styleLedDrawable(i)
        }
        this += h1Led1
        this += h1Led2
        STextView("H")
      } gravity ledColumnGravity layoutParams ledColumnLayoutParams
  
      val minutes0 = new SVerticalLayout {
        style {
          case t: STextView => styleTimePlaceHolder(t)
          case i: SImageView => styleLedDrawable(i)
        }
        this += m0Led1
        this += m0Led2
        this += m0Led4
        this += m0Led8
        STextView("M")
      } gravity ledColumnGravity layoutParams ledColumnLayoutParams
  
      val minutes1 = new SVerticalLayout {
        style {
          case t: STextView => styleTimePlaceHolder(t)
          case i: SImageView => styleLedDrawable(i)
        }
        this += m1Led1
        this += m1Led2
        this += m1Led4
        this += m1Led8
        STextView("M")
      } gravity ledColumnGravity layoutParams ledColumnLayoutParams
  
      val seconds0 = new SVerticalLayout {
        style {
          case t: STextView => styleTimePlaceHolder(t)
          case i: SImageView => styleLedDrawable(i)
        }
        this += s0Led1
        this += s0Led2
        this += s0Led4
        this += s0Led8
        STextView("S")
      } gravity ledColumnGravity layoutParams ledColumnLayoutParams
  
      val seconds1 = new SVerticalLayout {
        style {
          case t: STextView => styleTimePlaceHolder(t)
          case i: SImageView => styleLedDrawable(i)
        }
        this += s1Led1
        this += s1Led2
        this += s1Led4
        this += s1Led8
        STextView("S")
      } gravity ledColumnGravity layoutParams ledColumnLayoutParams
  
      val separatorLeft = new SVerticalLayout {
        style {
          case t: STextView => styleTimePlaceHolder(t)
        }
        STextView(":")
      } gravity separatorColumnGravity layoutParams separatorColumnLayoutParams
  
      val separatorRight = new SVerticalLayout {
        style {
          case t: STextView => styleTimePlaceHolder(t)
        }
        STextView(":")
      } gravity separatorColumnGravity layoutParams separatorColumnLayoutParams
  
      //This is where we set the content view
      contentView = new SLinearLayout {
        this += binaryLegendLeft
        this += hours1
        this += hours0
        this += separatorLeft
        this += minutes1
        this += minutes0
        this += separatorRight
        this += seconds1
        this += seconds0
        this += binaryLegendRight
      }.gravity(Gravity.CENTER)
       .orientation(LinearLayout.HORIZONTAL)
       .backgroundColor(getResources.getColor(R.color.background))
       .layoutParams(new LinearLayout.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, ViewGroup.LayoutParams.MATCH_PARENT))
    }
    
### Result

    package com.dontbelievethebyte.binaryclock
    
    import android.graphics.Typeface
    import android.view.{ViewGroup, Gravity}
    import android.widget.{ImageView, LinearLayout}
    import scala.language.postfixOps
    import org.scaloid.common._
    
    class BinaryClock extends SActivity{
      //Seconds first column LEDs
      lazy val s0Led1 : SImageView = new SImageView()
      lazy val s0Led2 : SImageView = new SImageView()
      lazy val s0Led4 : SImageView = new SImageView()
      lazy val s0Led8 : SImageView = new SImageView()
    
      //Seconds second column LEDs
      lazy val s1Led1 : SImageView = new SImageView()
      lazy val s1Led2 : SImageView = new SImageView()
      lazy val s1Led4 : SImageView = new SImageView()
      lazy val s1Led8 : SImageView = new SImageView()
    
      //Minutes first column LEDs
      lazy val m0Led1 : SImageView = new SImageView()
      lazy val m0Led2 : SImageView = new SImageView()
      lazy val m0Led4 : SImageView = new SImageView()
      lazy val m0Led8 : SImageView = new SImageView()
    
      //Minutes first column LEDs
      lazy val m1Led1 : SImageView = new SImageView()
      lazy val m1Led2 : SImageView = new SImageView()
      lazy val m1Led4 : SImageView = new SImageView()
      lazy val m1Led8 : SImageView = new SImageView()
    
      //Hours first column LEDs
      lazy val h0Led1 : SImageView = new SImageView()
      lazy val h0Led2 : SImageView = new SImageView()
      lazy val h0Led4 : SImageView = new SImageView()
      lazy val h0Led8 : SImageView = new SImageView()
    
      //Hours first column LEDs
      lazy val h1Led1 : SImageView = new SImageView()
      lazy val h1Led2 : SImageView = new SImageView()
    
      //Drawables
      lazy val ledOffDrawable = getResources.getDrawable(R.drawable.led_off)
      lazy val ledOnDrawable = getResources.getDrawable(R.drawable.led_on)
    
      //Layout params definitions
      lazy val ledColumnLayoutParams = new LinearLayout.LayoutParams(40 dip, 200.dip)
      lazy val legendColumnLayoutParams = new LinearLayout.LayoutParams(20 dip, 200.dip)
      lazy val separatorColumnLayoutParams = new LinearLayout.LayoutParams(8 dip, 200 dip)
      lazy val squareElementLayoutParams = new LinearLayout.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, 40 dip)
    
      //Columns gravity definitions
      val ledColumnGravity = Gravity.BOTTOM | Gravity.CENTER_HORIZONTAL
      val legendColumnGravity = Gravity.TOP | Gravity.CENTER_HORIZONTAL
      val separatorColumnGravity = Gravity.BOTTOM | Gravity.CENTER_HORIZONTAL
      val squareElementGravity = Gravity.CENTER | Gravity.CENTER_HORIZONTAL
    
      onCreate {
    
        //Linear layouts that will make all the different the columns
        val binaryLegendLeft = new SVerticalLayout {
          style {
            case t: STextView => styleBinaryPlaceHolder(t)
          }
          STextView("8")
          STextView("4")
          STextView("2")
          STextView("1")
        } gravity legendColumnGravity layoutParams legendColumnLayoutParams
    
        val binaryLegendRight = new SVerticalLayout {
          style {
            case t: STextView => styleBinaryPlaceHolder(t)
          }
          STextView("8")
          STextView("4")
          STextView("2")
          STextView("1")
        } gravity legendColumnGravity layoutParams legendColumnLayoutParams
    
        val hours0 = new SVerticalLayout {
          style {
            case t: STextView => styleTimePlaceHolder(t)
            case i: SImageView => styleLedDrawable(i)
          }
          this += h0Led1
          this += h0Led2
          this += h0Led4
          this += h0Led8
          STextView("H")
        } gravity ledColumnGravity layoutParams ledColumnLayoutParams
    
        val hours1 = new SVerticalLayout {
          style {
            case t: STextView => styleTimePlaceHolder(t)
            case i: SImageView => styleLedDrawable(i)
          }
          this += h1Led1
          this += h1Led2
          STextView("H")
        } gravity ledColumnGravity layoutParams ledColumnLayoutParams
    
        val minutes0 = new SVerticalLayout {
          style {
            case t: STextView => styleTimePlaceHolder(t)
            case i: SImageView => styleLedDrawable(i)
          }
          this += m0Led1
          this += m0Led2
          this += m0Led4
          this += m0Led8
          STextView("M")
        } gravity ledColumnGravity layoutParams ledColumnLayoutParams
    
        val minutes1 = new SVerticalLayout {
          style {
            case t: STextView => styleTimePlaceHolder(t)
            case i: SImageView => styleLedDrawable(i)
          }
          this += m1Led1
          this += m1Led2
          this += m1Led4
          this += m1Led8
          STextView("M")
        } gravity ledColumnGravity layoutParams ledColumnLayoutParams
    
        val seconds0 = new SVerticalLayout {
          style {
            case t: STextView => styleTimePlaceHolder(t)
            case i: SImageView => styleLedDrawable(i)
          }
          this += s0Led1
          this += s0Led2
          this += s0Led4
          this += s0Led8
          STextView("S")
        } gravity ledColumnGravity layoutParams ledColumnLayoutParams
    
        val seconds1 = new SVerticalLayout {
          style {
            case t: STextView => styleTimePlaceHolder(t)
            case i: SImageView => styleLedDrawable(i)
          }
          this += s1Led1
          this += s1Led2
          this += s1Led4
          this += s1Led8
          STextView("S")
        } gravity ledColumnGravity layoutParams ledColumnLayoutParams
    
        val separatorLeft = new SVerticalLayout {
          style {
            case t: STextView => styleTimePlaceHolder(t)
          }
          STextView(":")
        } gravity separatorColumnGravity layoutParams separatorColumnLayoutParams
    
        val separatorRight = new SVerticalLayout {
          style {
            case t: STextView => styleTimePlaceHolder(t)
          }
          STextView(":")
        } gravity separatorColumnGravity layoutParams separatorColumnLayoutParams
    
        //This is where we set the content view
        contentView = new SLinearLayout {
          this += binaryLegendLeft
          this += hours1
          this += hours0
          this += separatorLeft
          this += minutes1
          this += minutes0
          this += separatorRight
          this += seconds1
          this += seconds0
          this += binaryLegendRight
        }.gravity(Gravity.CENTER)
         .orientation(LinearLayout.HORIZONTAL)
         .backgroundColor(getResources.getColor(R.color.background))
         .layoutParams(new LinearLayout.LayoutParams(ViewGroup.LayoutParams.MATCH_PARENT, ViewGroup.LayoutParams.MATCH_PARENT))
      }
    
      def styleBinaryPlaceHolder (t: STextView): STextView = {
        t height 40.dip  typeface Typeface.MONOSPACE textSize 10.dip gravity Gravity.CENTER textColor getResources.getColor(R.color.label)
      }
    
      def styleTimePlaceHolder (t: STextView): STextView = {
        t height 40.dip  typeface Typeface.MONOSPACE textSize 15.dip gravity Gravity.CENTER textColor getResources.getColor(R.color.label)
      }
    
      def styleLedDrawable (i: SImageView): SImageView = {
        i backgroundColor android.R.color.transparent imageDrawable ledOffDrawable layoutParams squareElementLayoutParams scaleType ImageView.ScaleType.FIT_CENTER
      }
    }


### Cleanup

We can now delete the HelloScaloid activity and commit our changes. 

We can also change the package name from the manifest.

    <?xml version="1.0" encoding="utf-8"?>
    <manifest xmlns:android="http://schemas.android.com/apk/res/android"
          package="com.dontbelievethebyte.binaryclock"
          android:versionCode="1"
          android:versionName="1.0">
        <application android:label="BinaryClock" >
            <activity android:name="BinaryClock"
                      android:label="BinaryClock">
                <intent-filter>
                    <action android:name="android.intent.action.MAIN" />
                    <category android:name="android.intent.category.LAUNCHER" />
                </intent-filter>
            </activity>
        </application>
    </manifest>

### Return 0

That's it for now.

In part 3, I will implement the logic that updates the SImageView(s) according to the current time and define another method 
that display a toast reflecting the current time in the traditional human readable form.
