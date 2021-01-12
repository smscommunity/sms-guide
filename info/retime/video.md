---
layout: default
title: Video Retime
grand_parent: Info
parent: Retiming
nav_order: 1
---

# Video Retime

To convert an IL without video into SGT timing, take the number of frames between the *start* and *end* frame, then divide by the frame-rate of the video, and round the result *down* to 2dp. *Check* that you have the correct frame-rate, particularly if it's 30 or 29.97. If it's 29.97 or 59.94, divide by the exact number (30/1.001 or 60/1.001) for complete accuracy.

This "number of frames" is a whole number equal to the difference between the absolute frame numbers you see in VirtualDub, and by the nature of discrete arithmetic, counts the number of frames from the start to the end *including* the start but *excluding* the end. That is, if the start is frame 2 and the end is frame 6, the difference (=4) counts frames 2,3,4,5.

The reference start and end frames for full levels are as follows:
* The **start** is always the first frame the level is visible after a load. Load frames are all-white (before level starts) and all-black (before sub-levels). Examples of start frames: [after all-white load](https://cdn.discordapp.com/attachments/316530740063895554/788138576042655814/unknown.png); [after all-black load](https://cdn.discordapp.com/attachments/529145099003887618/796964909522616321/unknown.png).
* The **end** is always the first frame the shine-get cutscene starts. This is the frame after the camera jumps. [Example](https://cdn.discordapp.com/attachments/529145099003887618/796966109311926302/unknown.png).

## Rationale
The timer for any IL always stops on the end frame as defined above. The start frame is more intractable because it's not possible to see the value of the timer, which isn't displayed before it starts, and isn't shown during the intro cutscene anyway. However, the start frame as defined above gives the best match of frame-counts to the values SGT would show, as can be seen from this [sample of real ILs](https://tiny.cc/smsilretiming) for both *full levels* and *sublevels preceded by cutscenes*. The SGT has inherent random variation at the start of a level, and this method gives pessimistic estimates, though not absolute bounds. Which is to say, a retimed IL might beat a time done on SGT, but it's very unlikely.
