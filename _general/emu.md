---
layout: default
title: Emulator
permalink: /setup/emu
parent: Setup
nav_order: 2
---

# Emulator Setup  

[Original Guide](https://imgur.com/a/tested-version-dolphin-5-0-11991-beta-metacor-qj6vrmM) by Metacor  
[Dolphin Download](https://dolphin-emu.org/)  

# Dolphin Settings  

**Game Properties**  
*Make sure options without checks are set as "undetermined", not "off"*  

Synchronize GPU Thread: On (Stops crashes from long play sessions, this may no longer be required)  
Leave all of the other options Undetermined (box within a box)  
- These options will use your current Dolphin Settings (DON'T uncheck them! Doing so will force all of these options to be turned off - likely causing Dolphin to lag significantly)

<img src="/sms-guide/assets/setup/emu/1.png">  

**Configuration**  

Enable Dual Core: On (Doesn't actually 'speedup' the game, just makes Emulation faster)  
Enable Cheats: Off (For Runs), On (For Practice)  
Auto Update: Don't Update (I'd recommend keeping the Dolphin version you use for Runs the same)  

<img src="/sms-guide/assets/setup/emu/2.png">  

**Interface**  

This tab is mostly cosmetic, but I'd recommend -  
Pause on Focus Loss: Off (Having this option 'On' will pause the game if you Alt+Tab)  
Show On-Screen Display Messages: Off (Hides the yellow text from appearing at the top left of the screen)
Always Hide Mouse Cursor: On (If you're using Region/Desktop Capture for stream)  

<img src="/sms-guide/assets/setup/emu/3.png">  

**Audio**

I've never experienced an issue with audio in dolphin, so these options may be irrelevant  
(I also skipped 'Paths', 'GameCube', and 'Wii', as these options wont matter)  

<img src="/sms-guide/assets/setup/emu/4.png">  

**Advanced**  

Everything on Default, using "JIT Recompiler (recommended)", I haven't had the need to test the other Engines as they're listed as slower. The other options are likely to break the game, or make gameplay speed not comparable to console.  

<img src="/sms-guide/assets/setup/emu/5.png">  

**Graphics - General**  
*(Most of the Gameplay Fixes are found in the Graphics Options)*  
Backend: Vulkan or Direct3D 12  
- Fixes improper Sirena 6 Emulation and Pianta 1 Chomp Behavior  
- Note: Vulkan doesn't allow Game Capture unless you're using OBS 25.0+
Aspect Ratio: Force 4:3  
- Fixes the game randomly switching to 16:9 for a split second, then back to 4:3  
Use Fullscreen: On (Reduces Input lag in Windows 10)  
Shader Compilation: Synchronous (Ubershaders)  
- Fixes issues with Micro-Stutters:  
  - if this doesn't fix it for you, then you may also need 'Compile Shaders Before Starting' to be Enabled.
*Keep in mind, if you're on a low spec computer, this has a chance to cause a lot of lag*

<img src="/sms-guide/assets/setup/emu/6.png">  

**Enhancements**  

Internal Resolution: Native (Keeps visual cues consistent with console (not including CRT blur))                                          
Anti-Aliasing: None & Anisotropic Filtering: 1x  
- Fixes some Goop from not rendering
Scaled EFB Copy: Off
- Fixes 'blocky' edges on Goop  
Force Texture Filtering: Off
- Contributes to Fixing bad Goop behaviors  
Disable Copy Filter: Off (Likely irrelevant)  
Force 24-Bit Color: On (Mostly creates less blocky shadows)
- Note: this might cause issues with Visual Cue setups when switching to console
- eg. Honey Skip \\\ On: [🔗](/sms-guide/assets/setup/emu/efbon.jpeg) | Off: [🔗](/sms-guide/assets/setup/emu/efboff.jpeg)

<img src="/sms-guide/assets/setup/emu/7.png">  

**Hacks**  

Skip EFB Access from CPU: Off  
Store EFB Copies to Texture Only: Off  
Defer EFB Copies to RAM: On  
Texture Cache Accuracy: Safe  
Store XFB Copies to Texure Only: Off  
- All of these options contribute to Fixing bad Goop behaviors  
Save Texture Cache to State: On  
- Fixes Goop being inconsistent while loading a Save State
Fast Depth Caluculation & Vertex Rounding & Disable Bounding Box: Off
- I have these settings off for emulation accuracy, but It's likely not required

<img src="/sms-guide/assets/setup/emu/8.png">  

**Advanced**  

Advanced Options mostly don't affect Speedrunning  
Enable Progressive Scan: On - Useful for PAL Runners  
Backend Multithreading: On - Could help poor performance issues (only available with Vulkan)  

<img src="/sms-guide/assets/setup/emu/9.png">  

# Input Lag

- Dont use the front USB ports, use the direct-to-motherboard back USB ports, and make sure they are at least USB 3.0
- Make sure you have the correct and updated drivers for your controller adapter, found [here](https://dolphin-emu.org/docs/guides/how-use-official-gc-controller-adapter-wii-u/)
- Make sure Vsync is off
- Play in fullscreen, and turn off borderless fullscreen
- Overclock your adapter, tutorial found [here](https://docs.google.com/document/d/1cQ3pbKZm_yUtcLK9ZIXyPzVbTJkvnfxKIyvuFMwzWe0/edit?tab=t.0)
