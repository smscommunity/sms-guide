---
layout: default
title: Retiming
permalink: /info/retime
parent: Info
has_children: True
nav_order: 3
has_toc: false
---

# Retiming

This set of pages will cover standards, methods and rationale for timing SMS speedruns, with a focus on ILs, but a subset of these concepts covers RTA runs.

## Rationale
**Timing standards**  
The true length of a speedrun is the time calculated by the **in-game timer (IGT)** where available, and the **duration of the video** where not (video duration is always used with discretion since videos may have messed-up timing). This is respectively known as **video (re)timing** and **SGT (re)timing** – the latter after the *Shine-Get Timer (SGT)*, which is the universal IGT used in SMS.

**SGT is the standard for ILs**  
All ILs use SGT as the timing standard, and where it's unavailable but desired, models are used to retime other runs to SGT:
* Video retimes: used typically for subsets of RTA runs (e.g. a level in Any%), which typically ban all cheat codes including SGT.
* SGT retimes: used typically for subsets of longer SGT runs (e.g. a secret from a full level), or for runs done on older versions of SGT.

**SGT retimes are always better than video retimes**  
This is because SGT is always consistent within a single gameplay segment (meaning between loads); videos however may drop or duplicate frames, which introduces error.

**SGT is inconsistent on loads**  
SGT works by recording timestamps of real time at the start and end of every gameplay segment between load (thus, it pauses between loads). This process introduces errors of up to a frame on a given timestamp, meaning durations of loads vary. Therefore, **every retime that includes a load consists of retimes of the individual gameplay segments plus an estimate for each load**. Estimates are derived by taking the highest value (possibly excluding anomalies) from a sample of loads stored [here](https://tiny.cc/smsilretiming). These estimates are used in two contexts:
* to retime a mid-level load by comparing reference frames before and after *(e.g. Sirena hotel entry)*;
* to retime a non-initial gameplay segment with SGT visible by using frames where the SGT is visible to estimate the time the segment-only SGT would equal 0 *(e.g. [secret from full-level retime](retime/circle-mash))*.

**Video retimes are based on comparison to reference frames**  
A video retime is by definition the duration between a start and end frame; here's an [**index of reference frames**](retime#reference-frames).

**Fast-text conversion**  
ILs allow the fast-text cheat code as standard, and there are models to convert runs without fast text as if they'd used fast text – see [here](retime#load-estimates).

## Workflow
How to retime an IL step-by-step:
1. Break it down into loads and gameplay segments. The final result is the sum of the timings (in seconds to 2 decimal-places) of each of these segments.
2. For each load segment, estimate it using a constant (in seconds) from the [**load table**](retime#load-estimates). Not every load has been modelled yet, so some levels can't be retimed.
3. Within each gameplay segment, for each instance of text, calculate [**text adjustment**](retime/text) in frames. Let's call the sum of this (over each instance of text) `n` in the next step.
4. Retime each gameplay segment using the reference frames; how to retime gameplay segments depends on the level and whether the retime is based on SGT or video.
   - (SGT retime) after moving the ending reference frame forward by `n`, take the difference of the SGT shown on the reference frames. The one exception to this is that for levels with mashable circle intro cutscenes (like secrets), the start reference frame reading is adjusted using a special model – see [**circle-mash retimes**](retime/circle-mash).
   - (video retime) subtract the frame numbers of the two reference frames, then subtract `n`, and finally divide this by the frame-rate (and round down to 2dp) to get the time in seconds. Be sure to check the frame-rate, particularly if it's 30, 60, 29.97, or 59.94. If it's one of the latter two then use the exact frame-rate instead (30/1.001 or 60/1.001 respectively).

## Reference Frames
* **End**: a reference frame for the end of a segment is always the exact frame on which the SGT freezes (since SGT v2.1).
* **Start-zero**: these are reference frames for the start of a segment where SGT would equal zero if the segment were run in isolation. SGT is never visible on these frames, so they can't be used for SGT retimes unless they're estimated based on start-visible frames.
* **Start-visible**: these are reference frames for the start of a segment where SGT is or would be visible; the first such frame is known as *first-visible*. These are used in two contexts:
    * combined with a load estimate that directly connects the end frame of the preceding segment with this frame *(e.g. hotel entry)*.
    * (sgt retime) combined with a model that estimates the SGT that would appear on this frame, when it's the first segment of the retime. After deducting this estimate, it becomes a start-zero time *(e.g. secret-only from full-level)*. 

**Start-zero: (video retime)**  
The first frame of the intro cutscene being visible after the load (or the level if there is no cutscene), for every segment. *E.g. barely-visibe level demo at the start of a full level, pinhole at the start of either a secret demo or a direct load like Pinna 1.* This frame always matches where SGT would equal 0, and is usually pessimistic, meaning SGT tends to start fractionally later and give a better overall time (see the [sample](https://tiny.cc/smsilretiming), *Start* tab). A common mistake is to confuse this frame with the last frame of the load.

**Start-visible: circle-mash intro (sgt retime)**  
This uses a set of reference frames depending on context – see [**circle mash retimes**](retime/circle-mash); applies to any level starting with an immediately-skippable cutscene outward circle wipe, e.g. all secrets, Pinna 3, Noki 3.

**Start-visible: direct circle intro**  
The frame the (transition) circle cuts the left vertical edge of the water tank in the FLUDD HUD – also the frame SGT is first fully visible if present. Applies to e.g. Sirena Hotel, Casino, King Boo.

**Start-visible: Sirena hotel/casino entry**  
Four frames after the first frame the last textbox has started to fade out.

**End: shine get**  
The first frame of the shine-get cutscene (camera cuts from level camera to focusing on Mario and the shine), for every level.

**End: Bowser defeated**  
The first frame the FLUDD textbox is visible and semi-transparent (camera cuts to bathtub tipping cutscene).

**End: non-text circle fadeout**  
The first frame the circle is (barely) visible in the top-left and top-right (but not bottom-left and bottom-right) corners, for all inward circle wipes that aren't triggered by closing a textbox. *E.g. all secrets, Gelato 4, King Boo boss room; not casino entry.*

**End: Sirena hotel/casino entry**  
Four frames after the first frame the last textbox has started to fade out.

## Load Estimates
All of these are pessimistic estimates derived from samples published [here](https://tiny.cc/smsilretiming). Check the previous section for explanations of the reference frames these are based on.

**Secret Transition: 0.90**  
*(secret entry end → secret start-zero)*  
Includes any transition that fades out with an inward circle wipe and fades in with an immediately-skippable outward circle wipe. *E.g. all secret entries, gelato 4*.

**Sirena Hotel Entry: 0.90 (NTSC-J/U) / 0.83 (PAL)**  
*(hotel entry end → casino entry start-visible)*  

**Sirena Casino Entry: 1.29**  
*(casino entry end → boss entry start-visible)*  

**King Boo Boss Entry: 1.33**  
*(boss entry end → boss first-visible)*  
