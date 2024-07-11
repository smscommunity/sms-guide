---
layout: default
title: RTA Load Removal
permalink: /info/retime/loadless/
grand_parent: Misc General Info
parent: Retiming
nav_order: 4
---

# RTA Load Removal

*Due to variance in load times, a seperate timing method was created. This page can serve as a guide for converting traditional RTA timing into Loadless Timing.*

## Load Definition

A load is any point where the screen is pure black or white while preparing the next event. It isn't always obvious as to which which frames are pure black or white. Below are examples of transition frames between a load and an event. There are five major transistions that all act slightly differently: fades, circles, spirals, sweeps, and diamonds. There will only be one load frame per group of transition frames.

### Fades

Fade outs are the trickiest, but thankfully they're only used for FMV movies and Noki Bay. There are [14F](https://imgur.com/a/fade-out-14f-E1pvKCp) for GC fade outs and 12F for 3DAS fade outs. The only fade ins are Delfino Plaza loads from Noki Bay, which are [13F](https://imgur.com/a/dp-fade-13f-FcOMV5m) on GC and 11F on 3DAS. Note frame 2 of fade ins sometimes appears as pure black, but should not be treated as a load.

## Loads per Run

In the current any% route there are 180 loads. There will be an extra load for each death that occurs, and two extra loads for each save-warp. Perceivably there might only be 161 with the use of hacked file as well as perfect cutscene mashing.

## Special thanks to the moderators of these communities for their consultation:

New Super Mario Bros. Wii

Sonic the Hedgehog (2006)

Sonic Unleashed
