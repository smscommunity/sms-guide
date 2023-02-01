---
layout: default
title: Tutorial - Comparison video creation
permalink: /info/comparison-tutorial/
parent: Misc General Info
nav_exclude: true
---
# How to create a gameplay comparison video
*(A tutorial by **[1UpsForLife](https://www.speedrun.com/user/1UpsForLife)**)*  
This tutorial will explain one method of making gameplay comparison videos, using the free video editor Kdenlive.  
## Install Kdenlive
Visit the **[download page](https://kdenlive.org/en/download/)** and choose the version for your operating system. For Windows, I'd recommend the **Installable** version.  
## Set your project resolution
On the top menu bar, go to **Project -> Project Settings**. I recommend changing the project profile to **HD 1080p 30fps**. In a comparison video, two or more clips usually need to be shown at the same time, which will require making them smaller. Increasing the resolution will make the clips clearer.  
## Import your clips
Import the clips you'd like to use by pressing the **Add clip or folder** button in the top left of the **Project Bin** area.  
Drag your clips onto the timeline at the bottom of the screen.  
![](https://i.imgur.com/BySRjAu.png)  
**Warning**: If prompted, do not "switch to clip profile." This will change your project resolution to the resolution of one of your clips. This will likely make the quality low, because your individual clips will be downsized to fit two or more on screen for your comparison.  
## Position your clips on the screen
To play two videos at once, drag each video onto a different video track on the timeline. The video tracks are labeled V1 and V2.  
In the Main Effects window, open the **Transform, Distort and Perspective** submenu. Click and drag **Edge Crop** and **Transform** onto each of your clips on the timeline below.  
![](https://i.imgur.com/uVJcxZD.png)  
To edit the Edge Crop and Transform effects for a clip, click the clip on the timeline to highlight it in orange. The settings should appear above.  
Crop your clips to their desired size using the Top, Left, Bottom, and Right fields in the Edge Crop settings. Edit the pixel count directly by clicking the number and typing in a new number, or scroll while hovering over the bar.  
In the Transform settings, make sure both clips are the same size by typing the same value into the **Size** percentage field for both of them. (For videos with two clips, I recommend 66%.) Then, position it on the screen by changing the X and Y fields. Scrolling can help for finer adjustment.  
![](https://i.imgur.com/2Y69fOK.png)  
If you want to save your settings for these effects for future editing sessions, click the Save icon to the top right of the effect settings box. To access them later, press the "Show all custom effects" button (It's a star with a pencil, above the effects list).
## Edit your video
To change the length of a clip, hover over the beginning or ending in the timeline so your cursor turns into an arrow. Then click and drag to change the length.
To create text on the video, right click inside the **Project Bin** (where you imported your clips) and select **Add Title Clip**. Type in your text, style it the way you'd like, then press **Create Title**. Drag it onto the timeline alongside your videos in a new video track. (To add a new video track, right click the area to the left of the timeline and select **Insert track**.) To edit your text or its location on the screen, double click it in the timeline. This should open the same text editor as before.  
**Warning:** Clips may look laggy when playing them back in the editor. That's because the editor is applying the effects in real-time. It will likely look smooth after it's rendered (unless your source clips have issues).  
## Render your video
When you are done editing, press the Render button on the top of the screen (It has a red circle next to it).  
Most likely you will want to choose the **MP4** format under **Generic**, and select the **Full project** option to render the entire timeline. For the **Quality** option, lower numbers are higher quality but much larger file size. I'd recommend a quality of 23 to start out.   
Change the **Output file** on the top to save the final video in a folder you can easily access.  
In the **More options** checkbox area, **Parallel processing** may make the video render faster. However, if you see glitches in the final video, then try turning it off and re-rendering your video.  
Finally, upload the final product to YouTube and share!
