---
layout: default
title: RTA Load References
permalink: /info/retime/llref/
grand_parent: Misc General Info
parent: Retiming
nav_order: 4
---

# RTA Load References

*This page can serve as a guide for determining what is and is not a loading frame.*

## Load Definition

A load is any point where the screen is pure black or white while preparing the next event. It isn't always obvious as to which which frames are pure black or white. Below are examples of transition frames between a load and an event. There are six major transistions that all act slightly differently: fades, circles, spirals, shine selects, sweeps, and diamonds. There will only be one load frame per group of transition frames.

Note: "transition ins" are transitions going into gameplay while "transition outs" are going into loads.

## Fades

Fade outs are the trickiest, but thankfully they're only used for FMV movies and Noki Bay. There are [14F](https://imgur.com/a/fade-out-14f-E1pvKCp) for GC fade outs and 12F for 3DAS fade outs. The only fade ins are Delfino Plaza loads from Noki Bay, which are [13F](https://imgur.com/a/dp-fade-13f-FcOMV5m) on GC and 11F on 3DAS. Note frame 2 of fade ins sometimes appears as pure black, but should not be treated as a load.

## Circles

Circles are used for FMVs, deaths, entering secrets, entering subareas. Circle outs are especially difficult due to dark loading zones. Circle outs are much more important, and take [25F](https://imgur.com/a/0vlrQfu) on GC and 16F on 3DAS. Circle ins take [28F](https://imgur.com/a/qPSaj2E) on GC and 16F on 3DAS. Note there is no gameplay difference between console circle ins as you can control Mario as soon as the second transition frame.

Below is the first frame of a death. Note the first letter appeared but there is no smoke yet. Smoke appears on the next frame. Reference frame 1 will be 59F after this one.

<img src="https://i.imgur.com/AVmipAM.png" width="640" height="480">

## Spirals

Spirals are the most common and consistent type of transition. Spiral ins and outs haave the same transition animation, they are just reversed from one another. All spiral transitions take [39F](https://imgur.com/a/FDNfosi) on GC and 3DAS.

## Loads per Run

In the current any% route there are 180 loads. There will be 1 extra load for each death that occurs, and 2 extra loads (could look like 1) for each save-warp. Perceivably there might only be 161 with the use of hacked file as well as perfect cutscene mashing.

## Special thanks to the moderators of these communities for their consultation:

New Super Mario Bros. Wii

Sonic the Hedgehog (2006)

Sonic Unleashed
