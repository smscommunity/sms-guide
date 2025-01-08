---
layout: default
title: Boundaries
permalink: /info/retime/boundary/
grand_parent: Misc General Info
parent: Retiming
nav_order: 1
---

# Boundaries

*The statistical reference used for boundary timing is [here](https://tiny.cc/smsilretiming)*.

Retiming is based on reference frames and possibly load estimates, but which should be used is somewhat complicated. To explain different types of reference frames, we need to go through the theory of retiming a load, then we'll list the reference frames and  the load estimates.

## Load Retiming
In every level, there is a duration when the SGT is *running, but invisible* (during the start cutscene and while sliding into view right after it) – let's call this the segment's *intro*. Then it ends up looking like this:
- segment 1 intro
- segment 1 gameplay
- segment 1/2 load (sgt paused)
- segment 2 intro
- segment 2 gameplay
- ...
- segment n gameplay

The big nuance here is that, since the SGT is invisible during an intro, the reference frame for the start of a segment has to be some time after the frame on which the SGT started timing that segment (equivalently, where it would start if that segment were run in isolation). Using the above abstraction as an example, this implies two methods for how to retime, say, the segment 1/2 load:
1. **Combined**: Estimate the SGT difference between segment 1 end reference frame, and segment 2 start reference frame.
    - This means we only need take one estimate to time the load.
    - However, our segment 2 retime is meaningless in isolation – i.e. it doesn't give a retime of segment 2 that's compatible with segment-2–only runs.
2. **Separated**: Estimate the SGT value at the start of segment 2 intro, based on a segment 2 start reference frame, then base the load estimate on that.
    - This means estimating the segment 1/2 load and segment 2 intro separately, which compounds error.
    - However, we can use our estimate to time segment 2 by itself.

In practice, which method is chosen depends on two things:
- the purpose the retiming model was created for;
- whether the intro is a fixed length or not (the one case where it isn't is instantly-skippable intro cutscenes) – these must use separated estimates.

Separated estimates are always used for **secret levels**, both because of the variable intro and because secret-only ILs are well-entrenched on the main IL sheet. This means we can use the same model to (1) SGT-retime a full level to a secret only and (2) video-retime a full level from Any%. Most other situations use combined estimates, notably **hotel entry**, **casino entry**, **King Boo entry**, but separated models could be made for them if needed.

## Reference Frames
So based on the above, we'll define different reference frames for different situations, of three types. Each is defined with reference to what SGT would do if enabled, whether it's enabled or not.
- **end frame**: the frame the SGT freezes or ends on, which is always used for that segment's end.
- **start-zero frame**: the frame the timer starts for a segment (the SGT is always invisible in ILs).
- **start-visible frame**: an arbitrary frame (picked by convention) as a reference for the start of a segment, where SGT must be fully visible.

Now, we'll give visuals for each frame, so the frame can be identified when SGT is absent, or in an outdated version of SGT that doesn't freeze for example.

### End Frames
**End: shine get**  
The first frame of the shine-get cutscene (camera cuts from level camera to focusing on Mario and the shine), for every level.  
[Example](https://imgur.com/0svbX94) of the correct end frame.  
[Example](https://imgur.com/JfHZPLm) of the frame immediately before, as a visual cue.

**End: Bowser defeated**  
The first frame the FLUDD textbox is visible and semi-transparent (camera cuts to bathtub tipping cutscene).  
[Example](https://imgur.com/ZmdvFmk)

**End: non-text circle fadeout**  
The first frame the circle is (barely) visible in the top-left and top-right (but not bottom-left and bottom-right) corners, for all inward circle wipes that aren't triggered by closing a textbox. *E.g. all secrets, Gelato 4, King Boo boss room; **not casino entry**.*  
[Example](https://imgur.com/tvPSmFJ) 

**End: Sirena hotel/casino entry**  
Four frames after the first frame the last textbox has started to fade out.  
[Example](https://imgur.com/6XF1U7E)

### Start-Zero Frames
**RTA Start-zero**  
The frame in which a run is started, one frame before the text disappears. Used for Speedrun.com leaderboard retimes.  
[Example](https://imgur.com/mduPB9o) of the correct start frame.  
[Example](https://imgur.com/wkp45G3) of the frame immediately after, as a visual cue. Often used for Autosplit.

**IL Start-zero Frames**  
These are only visible for video retimes; SGT retimes would have to estimate them from start-visible frames. The start-zero frame is always the first frame that the segment is visible after the load, whether it has an intro cutscene or not. To our knowledge, that makes video retimes more pessimistic than what SGT would give in at least 80% of samples for every situation – see the "sgt-perf" samples in the *Circle* and *Start* tabs in the [reference](https://tiny.cc/smsilretiming).  
*A common mistake is to confuse this frame with the frame before – the last all black/white frame in the load.*  

[Example](https://imgur.com/dRfNcED) of the **correct** frame.  
[Example](https://imgur.com/Cw9p0j2) of the **incorrect** frame, one frame before.

### Start-Visible Frames

**Start-visible: circle-mash intro (sgt retime)**  
See [**circle mash retimes**](circle-mash). This method always first estimates the start-zero frame, then may extend into a separated load estimate (if there's another segment preceding it). A *circle-mash* is an outward circle wipe with immediately-skippable cutscene, used in e.g. all secrets, Pinna 3, Noki 3.  
[Example](https://imgur.com/lKZFbZu)

**Start-visible: direct circle intro**  
The frame the (transition) circle cuts the left vertical edge of the water tank in the FLUDD HUD – also the frame SGT is first fully visible if present. Applies to e.g. Sirena Hotel, Casino, King Boo.  
[Example](https://imgur.com/KVikwj9)

## Load Estimates
All of these are pessimistic estimates derived from the samples in the [reference](https://tiny.cc/smsilretiming). Check the previous section for explanations of the reference frames these are based on.

**Secret Transition: 0.90**  
*(SEPARATED: secret entry end → secret start-zero)*  
Includes any transition that fades out with an inward circle wipe and fades in with an circle-mash (= outward circle wipe with immediately-skippable cutscene). *E.g. all secret entries, gelato 4*.

**Sirena Hotel Entry: 0.90 (NTSC-J/U) / 0.83 (PAL)**  
*(COMBINED: hotel entry end → casino entry start-visible)*  

**Sirena Casino Entry: 1.29**  
*(COMBINED: casino entry end → boss entry start-visible)*  

**King Boo Boss Entry: 1.33**  
*(COMBINED: boss entry end → boss first-visible)*  
