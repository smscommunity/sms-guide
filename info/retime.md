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

This is a technical doc specifying standards for how to retime levels to conform with the shine-get timer ("SGT", used for ILs) in various situations. Note that the SGT is paused during loads, and most ILs are done with the *Fast Text* practice code, which is not usable in longer categories.

Evidence for rationale can be found [here](https://tiny.cc/smsilretiming).

**[Video Retime](retime/video)**  
For a level done without SGT, this will give a retime, though it won't account for loads or text.

**[Cutscene Sublevel Retime](retime/sublevel)**  
For a level done with SGT, this will give a retime of a final sublevel that loaded via an instantly-cancellable cutscene – notably all secrets.

**[Text Adjustment](retime/text)**  
This will adjust a raw retime (done from either video or timer) for any text done without the Fast Text practice code.

