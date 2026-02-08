---
layout: default
title: Quarterframes
permalink: /game/misc/quarterframes/
nav_order: 3
parent: Misc Game Info
---
# Quarterframes

## What is a “frame”?

Sunshine runs at 29.97 frames per second.
Visually, Mario’s position, speed, and physics update once per frame (~33.37 milliseconds).

So you’d expect:

- Inputs → processed once per frame
- Physics → applied once per frame
- Movement → advances in full-frame steps

But that’s not what actually happens.

## What is a "quarterframe"?

Like Super Mario 64, Super Mario Sunshine runs physics checks on a "quarterframe" basis (4 times per frame). These are commonly referred to as "QF 0, QF 1, QF 2, and QF 3". While physics are checked 4 times a frame, your inputs are intuitavely only sent in at the first quarterframe, once per frame.  

This means:

- Mario can gain or lose tiny amounts of height or speed, seemingly at random.
- Even if everything looks identical visually, things can still be different (like fruit throws or wall interactions).

| Option  | QF Allignment |
|---|---|
| Pause  | +1 QF  |
| Pause and Save  | +2 QF  |
| Blue Coin Textbox  | Set to 3 |


| Object  | QF Reaction |
|---|---|
| Banana  | QF 0 - Pushback |
|   | QF 1 - Pushback |
|   | QF 2 - Pushback |
|   | QF 3 - Normal |
| Pineapple  | QF 0 - Normal |
|   | QF 1 - Pushback |
|   | QF 2 - Pushback |
|   | QF 3 - Normal |
| Coconut  | QF 0 - Pushback |
|   | QF 1 - Pushback |
|   | QF 2 - Pushback |
|   | QF 3 - Normal |
| Pepper  | QF 0 - Pushback |
|   | QF 1 - Pushback |
|   | QF 2 - Pushback |
|   | QF 3 - Pushback |
| Papaya  | QF 0 - Normal |
|   | QF 1 - Pushback |
|   | QF 2 - Pushback |
|   | QF 3 - Normal |
| Barrel  | QF 0 - Normal |
|   | QF 1 - Pushback |
|   | QF 2 - Pushback |
|   | QF 3 - Normal |

Video Explanations:
AverageTrey - SMS
{% include yt.html id="5BC_eRUNayA" %}  

Bismuth - SM64
{% include yt.html id="wjge1bVobN0" %}  

