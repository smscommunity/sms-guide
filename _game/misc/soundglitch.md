---
layout: default
title: Sound Glitch
permalink: /game/misc/soundglitch/
nav_order: 2
parent: Misc Game Info
---
# Sound Glitch  

## What Happens?

- [“Shine Get” jingle song doesn’t play.](https://youtu.be/IwojD6Hu8es) (easy identifier)
- All cutscenes last at least 6 seconds, [including death cutscenes](https://youtu.be/dPA_1zdUod8).
   - This effects cutscene behavior but not always visual length. [This can lead to weird behavior or time loss.](https://www.youtube.com/watch?v=OEJ80mihsVY)
- [Mario can't move after killing a Gatekeeper.](https://www.youtube.com/watch?v=agiRDebluMc) (Goop plants are also known as a “Gatekeeper”)
- Can happen while using practice codes
- Game becomes prone to crashing, especially when collecting a shine.  


## Technical Write-Up
*by Noki Doki*

Sound glitch is a poorly understood glitch in JP 1.0, which is triggered by unknown circumstances, and stays active until the game is turned off. Unlike its SM64 counterpart, SMS sound glitch can happen on mono audio. While it is active, the jingle that normally plays in the background while a Shine spawns is missing, the death fade-out takes longer, [short cutscenes last longer if a Shine is nearby](https://www.youtube.com/watch?v=VFKWhsmZpmA), and [Mario can't move after killing a Gatekeeper](https://www.youtube.com/watch?v=agiRDebluMc). But most notably, the game becomes prone to crashing upon grabbing a Shine.  

A potential lead is that the game is hard-coded to make cutscenes last at least 6 seconds (or 10 seconds for death cutscenes) when a secondary BGM track is playing, such as sewer music or timed event music. For example, cleaning a linked graffiti in Ricco 6 or Sirena 8 while the red coin event is ongoing will lead to an extended cutscene, and so will entering the sewers after dying (for example by [dying out of bounds under the sewers while riding Yoshi](https://www.youtube.com/watch?v=g-3BjUzjo90&t=35)).  

As for the Gatekeeper effect, it turns out Gatekeepers start a cutscene when defeated, but the associated camera movement doesn't exist, so the cutscene normally ends instantly. Under sound glitch, it's extended to 6 seconds like any other, but the camera still doesn't have anything to do, making it look like normal gameplay where the player has no control. This effect can again be observed without sound glitch, by shooting the final hit on the Bianco Gatekeeper while ground pounding into the nearby manhole. If timed so that Mario enters the sewers before the water hits the Gatekeeper, Mario will be unable to move until the statue FMV starts.  

So it seems that sound glitch would be related to some secondary BGM track that never properly ends? We also have a sound glitch crash log from Guy playing on practice codes, which was later reproduced on vanilla by Akane (with the only difference of SRR1 being 0000A032 instead of 0000B032).  

    ******** EXCEPTION OCCURRED! ********
    FrameMemory:804C55A0H
    CONTEXT:803EB5A8H  (DSI EXCEPTION)
    SRR0:   8004C5D8H   SRR1:0000B032H
    DSISR:  04000000H   DAR: 00000001H
    ---------------------------------TRACE
    Address:   BackChain   LR save
    80423C28:  80423C48    8004C524
      [8004C524]: .text [8004C504: 168H]
      processFrameWork__8JAIBasicFv JSystem.a JAIBasic.cpp
    80423C48:  80423C50    8004C4F4
      [8004C4F4]: .text [8004C4E4: 20H]
      startFrameInterfaceWork__8JAIBasicFv JSystem.a JAIBasic.cpp
    80423C50:  80423CC0    8017E5F8
      [8017E5F8]: .text [8017E530: E8H]
      mainLoop__6MSoundFv MSound.a MSound.cpp
    80423CC0:  80423F28    800F9CE4
      [800F9CE4]: .text [800F9954: 430H]
      gameLoop__12TApplicationFv System.a Application.cpp
    80423F28:  80423FF0    800FA058
      [800FA058]: .text [800F9D9C: 450H]
      proc__12TApplicationFv System.a Application.cpp
    80423FF0:  80424000    80005628
      [80005628]: .text [80005600: 44H]
      main main.o
    80424000:  FFFFFFFF    80005360
      [80005360]: .init [8000522C: 138H]
      __start os.a __start.c
    --------------------------------

The last saved LR value corresponds to the call to JAIBasic::checkDummyPositionBuffer(), which traverses a list of JAIDummyVec (this->field_0x0->field_0x22c), seemingly checks if each element represents a finished sound, and if so releases it by removing it from the list and inserting it at the start of this->field_0x0->field_0x228). However nothing ever seems to insert anything into field_0x22c, so this call effectively does nothing and the crash has to occur between it and the next function call from JAIBasic::processFrameWork().
