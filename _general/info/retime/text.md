---
layout: default
title: Text
permalink: /info/retime/text/
grand_parent: Misc General Info
parent: Retiming
nav_order: 2
---

# Retiming Text

Here's a method for retiming text from normal to fast ("!!!"). It's generic so applicable to any text, and yields a number of frames by which to adjust a gameplay segment timing, both for video and SGT retimes. Let's call the run being retimed the **subject** run.

## Rationale
Fast text replaces a sequence of normal textboxes with a single one saying "!!!", and the task of closing this single textbox asap is part of the execution of an IL. This is substituted with the task of closing the first textbox asap in the subject run; the others are ignored, or equivalently assumed to be executed perfectly.

## Calculation
We define three frames A, B, C to segment the text:
* **A**: the first frame the **first** textbox **appears**
* **B**: the first frame the **first** textbox **starts fading out**
* **C**: the first frame the **last** textbox **starts fading out**

First, we have the **raw** retime, which is the subject converted to IL timing before adjusting for text. We take this, then
* **α**: subtract the difference between the **A to C time** in the subject vs in an optimal run **with** fast-text
* **β**: add the difference between the **A to B time** in the subject vs in an optimal run **without** fast-text

The α-adjustment swaps the whole text segment in the subject with that of an optimal IL, then the β-adjustment reinstates the time lost executing the first textbox.

The optimal timings we need to know are therefore:
* **A to C with fast-text**. This should be **always 8f** (at 60Hz) and is hopefully level/language-independent.
* **A to B without fast-text**. This depends on the textbox and language, but a good authority for JP (at 60Hz) is the [1:07 Any% TAS](https://youtu.be/5VLKqijYrbA). E.g. this is **27f for JP Manta**.

Once both adjustments have been calculated in frames, the final retime of the containing gameplay segment is done as follows:
* for a *video retime*, the adjustment is deducted from the frame count, before it's converted into a time by dividing by the frame-rate.
* for an *SGT retime*, the IL is advanced backwards from the shine-get frame per the adjustment, then the time showing on the resulting frame is taken.

## Example – JJ Manta IL
This example will use the times on the in-video RTA timer so that ppl can frame-advance the [original YouTube video](https://youtu.be/l3DP9U068Nc?t=3463) to understand what's going on (press `,` and `.`). *An accurate retime should be done (1) by counting frames in the video rather than using the timer, and (2) using times expressed in integer frames rather than decimal seconds until the final conversion (to avoid rounding errors).*

Here are the important frames:

| frame | time |
| - | - |
| intro cs start       | 57:39.64 |
| A (first text start) | 57:50.82 |
| B (first text end)   | 57:51.75 |
| C (last text end)    | 58:03.44 |
| shine-get cs start   | 59:13.78 |

and the calculation *(note the optimal timings 8f and 27f mentioned earlier; the video is 30 fps exactly)*:

| step          | calc                      | result        |
| -             | -                         | -             |
| raw retime    | 59:13.78 – 57:39.64 =     | **1:34.14**   |
| A to C        | 58:03.44 – 57:50.82 =     | **12.62**     |
| α-adjustment  | 12.62 – 8f =              | **12.35**     |
| A to B        | 57:51.75 – 57:50.82 =     | **0.93**      |
| β-adjustment  | 0.93 – 27f =              | **0.03**      |
| final retime  | 1:34.14 – 12.35 + 0.03 =  | **1:21.82**   |

This run comes out to **1:21.80** using this technique with frame-counting.

Based off the TAS, [here](https://docs.google.com/spreadsheets/d/1UIAKOIdVCkfsMr4n3GOfkdQw3pircb-g6rghotKlHnM/edit?usp=sharing) are reference times for optimal text with no fast text (for β-adjustment)
