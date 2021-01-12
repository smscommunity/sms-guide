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

This is a doc explaining the standards for how to retime levels to conform with the shine-get timer ("SGT", used for ILs) in various situations. Note that two ways in which IL timing deviates from (video-based) timing of longer categories are that it pauses during loads, and allows the *Fast Text* practice code, which saves time.

Evidence for rationale can be found [here](https://tiny.cc/smsilretiming).

**[Video Retime](retime/video)**  
For a level done without SGT, this will give a retime, though it won't account for loads or text.

**[Load Retime](retime/load)**  
Any level done without loadless SGT should be retimed in parts and summed, as explained here.

**[Cutscene Sublevel Retime](retime/sublevel)**  
For a level done with SGT, this will give a retime of a final sublevel that loaded via an instantly-cancellable cutscene – notably all secrets.

**[Text Adjustment](retime/text)**  
This will adjust a raw retime (done from either video or timer) for any text done without the Fast Text practice code.

