---
layout: default
title: Sound Glitch
permalink: /game/misc/importantwriteups/soundglitch/
nav_order: 1
parent: Important Write-Ups
grandparent: Misc Game Info
---
# Sound Glitch  
*by Noki Doki*

Sound glitch is a poorly understood glitch in JP 1.0, which is triggered by unknown circumstances, and stays active until the game is turned off. Unlike its SM64 counterpart, SMS sound glitch can happen on mono audio. While it is active, the jingle that normally plays in the background while a Shine spawns is missing, the death fade-out takes longer, [short cutscenes last longer if a Shine is nearby](https://www.youtube.com/watch?v=VFKWhsmZpmA), and [Mario can't move after killing a Gatekeeper](https://www.youtube.com/watch?v=agiRDebluMc). But most notably, the game becomes prone to crashing upon grabbing a Shine.  

A potential lead is that the game is hard-coded to make cutscenes last at least 6 seconds (or 10 seconds for death cutscenes) when a secondary BGM track is playing, such as sewer music or timed event music. For example, cleaning a linked graffiti in Ricco 6 or Sirena 8 while the red coin event is ongoing will lead to an extended cutscene, and so will entering the sewers after dying (for example by [dying out of bounds under the sewers while riding Yoshi](https://www.youtube.com/watch?v=g-3BjUzjo90&t=35)).  

As for the Gatekeeper effect, it turns out Gatekeepers start a cutscene when defeated, but the associated camera movement doesn't exist, so the cutscene normally ends instantly. Under sound glitch, it's extended to 6 seconds like any other, but the camera still doesn't have anything to do, making it look like normal gameplay where the player has no control. This effect can again be observed without sound glitch, by shooting the final hit on the Bianco Gatekeeper while ground pounding into the nearby manhole. If timed so that Mario enters the sewers before the water hits the Gatekeeper, Mario will be unable to move until the statue FMV starts.  

So it seems that sound glitch would be related to some secondary BGM track that never properly ends? We also have a sound glitch crash log from Guy2308 playing on practice codes, which was later reproduced on vanilla by akane (with the only difference of SRR1 being 0000A032 instead of 0000B032).  



The last saved LR value corresponds to the call to JAIBasic::checkDummyPositionBuffer(), which traverses a list of JAIDummyVec (this->field_0x0->field_0x22c), seemingly checks if each element represents a finished sound, and if so releases it by removing it from the list and inserting it at the start of this->field_0x0->field_0x228). However nothing ever seems to insert anything into field_0x22c, so this call effectively does nothing and the crash has to occur between it and the next function call from JAIBasic::processFrameWork().
