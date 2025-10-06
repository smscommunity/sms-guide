---
layout: default
title: Instamanta
permalink: /game/misc/instamanta/
nav_order: 2
parent: Misc Game Info
---
# Instamanta
*by Noki Doki*  

Clips:  
[SyrupSMS playing on Nintendont with practice codes](https://clips.twitch.tv/AbrasiveFunnyGoblinBlargNaut)  
[JustyceM playing on Nintendont without cheat codes](https://clips.twitch.tv/ModernImpartialPoxOSsloth)  

## What Happens
When the manta would split for the first time in the fight, it completely disappears instead. Some 8 seconds later, its death sound is played, the hotel cutscene starts, and the Shine appears.

## Theories
- This may be specific to Nintendont.
- This may be caused by the manta splitting on the seam between two floors (the side of the pool in one case, the stairs in the other).

## What's Really Going On
The function that spawns mantas on split adds an uninitialized floating-point variable to each component of the spawned mantas' direction vectors. Most values of that uninitialized variable will only bias the initial directions of the mantas, as the vector is then normalized, but if the value happens to be NaN, it will quickly leak over to the manta's position, preventing it from recovering in any way. However, there is no way to manipulate this variable in-game, so this is specific to Nintendont (and maybe other loaders that don’t clean the registers). But since the variable can’t change while the game is running, if you get instamanta once, you will get it every time until you completely exit the game.

## Reproducing (with hacks)  
- Putting the manta under the floor has no effect, it always stays at the highest floor level.
- Putting the manta under the death barrier makes it disappear, then kills it after 8 seconds; however it still moves around and puts goop on the floor until it dies.
- Putting the manta off the edges of the map horizontally makes it disappear and kills it after 8 seconds, without putting goop on the floor.
- Preventing the manta from spawning or initializing smaller mantas when it would split kills it immediately.  

## Random Manta Fact
When a manta splits, it calls RNG once to determine the facing angle of all the mantas it spawns, then spreads their directions over the full circle: if it’s spawning 2 mantas, they go 180° apart, 120° if it’s spawning 3, 90° if it’s spawning 4. 
