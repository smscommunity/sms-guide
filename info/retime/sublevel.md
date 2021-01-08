---
layout: default
title: Cutscene Sublevels
grand_parent: Info
parent: Retiming
nav_order: 2
---

# Cutscene Sublevel Retime

To convert an IL with SGT that includes an earlier segment (e.g. full level) into just a sublevel that started with an instantly-skippable cutscene (e.g. secret), do this:
1. Figure out how many frames were lost on skipping the cutscene.
    1. First compare the number of frames that the cutscene is visible to the optimal number (always 12).
    2. This count may be wrong because of frame drops though, so check it by comparing visuals on when the cutscene was skipped. See the table of *Cutscene Skip Visuals* below.
2. Frame-advance the first few frames that the SGT is visible on screen during the sublevel. You're looking for the frame the 4th character from the left settles into its final position ([example](https://cdn.discordapp.com/attachments/529145099003887618/796977267409813524/unknown.png)). This is the reference frame for the start of the level assuming the cutscene skip was optimal. If it wasn't, advance the level backwards by the number of frames lost on the skip. Make sure that the timer always decreases by 0.03 or 0.04, meaning no dropped/duplicated frames. Note down the time on the resulting frame.
3. The time the secret started is this time minus 2.00, and the final retime is the difference between the original SGT time of the full level and this start time.

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

## Rationale
This frame can always be seen in the video for any reasonable cutscene skip, and in this [sample of real sublevel ILs](https://tiny.cc/smsilretiming), the time showing on that frame is always at most 2.00, the number deducted. This gives a pessimistic estimate with low variance (the least possible time being 1.98).