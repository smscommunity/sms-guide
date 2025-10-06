---
layout: default
title: Circle-Mash
permalink: /il/retime/circle-mash/
grand_parent: Individual Levels
parent: Retiming
nav_order: 3
---

# Circle Mash Retime

Our goal is to retime a gameplay segment that starts with a circle mash *(= immediately-skippable cutscene outward circle wipe, e.g. all secrets, Pinna 3, Noki 3)* and has SGT visible (*e.g. secret-only retime from full-level*).

## Rationale
We can't see the SGT on the *start-zero* frame, when it'd equal zero on a run of solely this segment, so we have to use a later reference *start-visible* frame and replace the part before it with an estimate (a pessimistic one from a sample – see [here](https://tiny.cc/smsilretiming), *Circle* tab). In fact, since frames can be lost mashing the cutscene, we need a set of consecutive reference frames, and a way to calculate the cs-mash loss.

## Calculation
1. Figure out how many frames were lost on skipping the cutscene.
    1. First compare the number of frames that the cutscene is visible to the optimal number (always 12).
    2. This count may be wrong because of frame drops though, so check it by comparing visuals on when the cutscene was skipped. See the table of *Cutscene Skip Visuals* below.
2. Frame-advance the first few frames that the SGT is visible on screen during the sublevel. Each character of the SGT settles into its final position on a unique, consecutive frame; you're looking for the frame the 4th one from the left settles ([example](https://cdn.discordapp.com/attachments/529145099003887618/796977267409813524/unknown.png)). This is the reference frame for the start of the level assuming the cutscene skip was optimal. If it wasn't, advance the level backwards by the number of frames lost on the skip. Make sure that the timer always decreases by 0.03 or 0.04, meaning no dropped/duplicated frames. Note down the time on the resulting frame.
3. The SGT value the segment started at equals this time minus **2.00**, then the retime can be calculated by subtracting this from the end SGT value as usual.

## Cutscene Skip Visuals
We're looking for the first frame the transparent horizontal black bar appears to signify exiting the cutscene.

| Frames lost | Cutscene Duration | Cutscene Visual (+ Example) |
| - | - | - |
| 0 | 12 | [Large bar on 7th frame](https://youtu.be/KB3l5qn4ntA) |
| 1 | 13 | [Small bar on 7th frame](https://youtu.be/k1f7S9DGbT0) |
| 2 | 14 | [Large bar on 8th frame](https://youtu.be/sa6u4O9MT1M) |
| 3 | 15 | [Small bar on 8th frame](https://youtu.be/PQ6MSkcvy4I?t=32) |
| 4 | 16 | [Large bar on 9th frame](https://youtu.be/fBxF26ke1a8?t=52) |
| 5 | 17 | [Small bar on 9th frame](https://youtu.be/gKxrYjtW2uU) |
