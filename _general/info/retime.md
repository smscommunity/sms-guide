---
layout: default
title: Retiming
permalink: /info/retime/
parent: Misc General Info
has_children: True
nav_order: 3
has_toc: false
---

# Retiming

This set of pages will cover standards, methods and rationale for timing SMS speedruns, with a focus on ILs, but a subset of these concepts covers RTA runs.

## Rationale
**Timing standards**  
The true length of a speedrun is the time calculated by the **in-game timer (IGT)** where available(using the Shine Get Timer or Quarter Frame Timer), and the **duration of the video** where not (video duration is always used with discretion as mentioned at the top of the SM64 Retiming Guide). This is respectively known as **video (re)timing** and **IGT (re)timing**. The current standard for retiming ILs and RTA speedruns for the leaderboards is the [SM64 Retiming Guide](https://docs.google.com/document/d/13dtZ8nkbbw4SDFgw_5GPCqY5NztabJJtnb0Z2yP-YBY/edit?tab=t.0#heading=h.3znysh7).  

**IGT is the standard for ILs**  
Almost all ILs use a mod of IGT known as *Shine-Get Timer (SGT)* as the timing standard, and where IGT is unavailable but desired, models are used to retime other runs to SGT. Hence, we'll split retiming methods into these categories:
* Video retimes: used typically for subsets of RTA runs (e.g. a level in Any%), which typically ban all cheat codes including SGT.
* SGT retimes: used typically for subsets of longer SGT runs (e.g. a secret from a full level), or for runs done on older versions of SGT.

**SGT retimes are always better than video retimes**  
This is because SGT is always consistent within a single gameplay segment (meaning between loads); videos however may drop or duplicate frames, which introduces error.

**SGT is inconsistent on loads**  
SGT works by recording timestamps of real time at the start and end of every gameplay segment between two loads (thus, it pauses between loads). This process introduces errors of up to a frame on a given timestamp, meaning durations of loads vary. Therefore, **every retime that includes a load comprises retimes of the individual gameplay segments plus an estimate for each load**. Estimates are derived by taking the highest value (possibly excluding anomalies) from a sample of loads stored [here](https://tiny.cc/smsilretiming).

**Video retimes are based on comparison to reference frames**  
A video retime is by definition the real-time duration between a start and end frame; here's the [**index of reference frames**](https://smscommunity.github.io/sms-guide/info/retime/boundary#reference-frames) used.

**Fast-text conversion**  
ILs allow the fast-text cheat code as standard, and there are models to convert runs without fast text as if they'd used fast text – see [here](https://smscommunity.github.io/sms-guide/info/retime/text/).

## Workflow

Let's go through each mechanic for retiming, loosely in the order you'd do them in.

### 1. Boundaries + Load Retiming
The first step is to figure out [**boundaries**](https://smscommunity.github.io/sms-guide/info/retime/boundary), meaning break down a full IL into loads and gameplay segments, and figure out which fixed estimates to use to time the load segments, and which reference frames to use to time the gameplay segment. The final retime is the sum of all the load and gameplay segment times.

### 2. Text Adjustments
Within each gameplay segment, for each instance of text, calculate [**text adjustment**](https://smscommunity.github.io/sms-guide/info/retime/text) in frames. Let's call the sum of this (over each instance of text) `n` in the next step.

### 3. Gameplay Retiming
Retime each gameplay segment using the reference frames:
   - (SGT retime) after moving the end reference frame forward by `n`, take the difference of the SGT shown on the reference frames. Adjustment may need to be done to the start frame's SGT value depending on the reference frame and load estimate (for the preceding load) being used – that's covered in the lists of [frames and estimates](https://smscommunity.github.io/sms-guide/info/retime/boundary/#reference-frames).
   - (video retime) subtract the frame numbers of the two reference frames, then subtract `n`, and finally divide this by the frame-rate (and round down to 2dp) to get the time in seconds. Be sure to check the frame-rate, particularly if it's 30, 60, 29.97, or 59.94. If it's one of the latter two then use the exact frame-rate instead (30/1.001 or 60/1.001 respectively).
