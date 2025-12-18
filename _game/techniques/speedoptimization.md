---
layout: default
title: Speed Optimization
permalink: /techniques/speedoptimization/
parent: Techniques
nav_order: 1
---
{: .no_toc }
# Speed Display Codes and Optimizing Gameplay

*forked from **Jpep** – [original](https://gist.github.com/JpepWasTaken/e8c2eec244e919f527f651f8fe4bdb29)*

1. TOC
{:toc}

#### Section 1 - Horizontal Speeds of movement options

| Movement option  | Horizontal Speed |
|---|---|
| Hoverslide  | Up to 100.5  |
| Any Jump  | Up to 80% of Mario's speed  |
| Rollout  | 55 |
| Dive (in the air)  | 48 |
| Dive (on the ground)  | Mario's speed + 15  |
| Walking  | Up to 32 |
| Hovering  | Down to 24  |
| Buttslide  | 80+ |
| Turbo (on land)  | 80.13 |
| Turbo (on water)  | 78.02 |


- When Mario is *hoversliding*, with the stick held in the direction he is moving, his horizontal speed increases by between 1 and 2 units per frame. The acceleration increases until the speed cap of 100.5 is reached.
- *Jumps* can conserve up to 80% of Mario's speed. Due to quarter-frame shenanigans, this number is an upper limit, and not every frame-perfect jump will conserve this much speed.
- The formula that calculates Mario's horizontal speed in the air has a fixed point at 56. In practice, this means that if Mario is in the air and his speed is *below* 56, and you are holding the stick in the direction of the movement, his speed will *slowly increase* up to 55. If his speed is *above* 56, it will *decrease* down to 55 instead.
- Mario's walking speed increases as he walks until it hits a softcap around 32. Then, It decreases back down to around 26, and so on. It takes 3 to 4 frames for a cycle to complete.



#### Section 2 - De Facto Speed

- When Mario is **grounded** and **moving on a slope**, he actually only moves at a portion of his speed called *defacto speed*. This portion is determined by the steepness of the slope. This is why watersliding on a steep slope in extremely slow.
- The speed on the speed display timer *does not* take slope steepness or defacto speed into account.
- Example of application in an IL: in [EG's 32.05 Pinna 3](https://youtu.be/WMAIWI7fkvw?t=24), he hovers up the last portion of the slope instead of walking. Although this reduces his speed on the speed display, it actually lets him move faster, because the hover puts Mario in an aerial state in which he is not slowed down by the slope.



#### Section 3 - Interaction between Horizontal and Vertical Speed

- Generally, Mario's jump height **depends on his horizontal speed** going into the jump. The exact information, found by Noki Doki, was compiled in this table:

|Jump  | Vertical Speed |
|-|-|
| Single | 42 + 0.25 * spd |
| Double | 52 + 0.25 * spd |
| Spin | 70 + 0.25 * spd |
| Triple | 75 + 0.15 * spd |
| Wallkick | 62 + 0.00 * spd |
| Sideflip | 70 + 0.00 * spd |
| Backflip | 70 + 0.00 * spd |

- This is how momentum spins work
- Note that a Triple will go higher than a spin until Mario has 50 speed.
- Example of use in an IL: In order to get a very good Pinna 6 ending, like in [this IL](https://youtu.be/rYumf09Xt5Y?t=22), it is necessary to jump off the orange block very early. However, if you do not jump on the frame where Mario's walking speed is highest, you will not get enough height to make it to the top after 3 wallkicks.

#### Section 4 - Rollout Vertical Speed

- Unlike other movement options, rollouts always give the same amount of vertical speed no matter Mario's horizontal speed. There are 5 possible rollout heights depending on if A is held for 1, 2, 3, 4 or 5 frames.
- This table records this information, assuming Mario is moving on flat ground.

| Rollout height  | Vertical speed on 1st frame  | 2nd  | 3rd  | 4th  | 5th  | 6th  | 7th  | 8th  | 9th  | 10th  | 11th  | 12th  | 13th  | 14th  | 15th | 16th | 17th | 18th | 19th | 20th |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1  | 34.00  | 17.12  | 13.12  | 9.12  | 5.12  | 1.12  | -2.88  | -6.88  | -10.88  | -14.88  | -18.88  | -22.88  | -26.88  | (land)  | 0.00  | 0.00  | 0.00 | 0.00  | 0.00 | 0.00 |
| 2  | 34.00  | 30.00  | 14.88  | 10.88  | 6.88  | 2.88  | -1.12  | -5.12  | -9.12  | -13.12  | -17.12  | -21.12  | -25.12  | -29.12  | (land) | 0.00  | 0.00  | 0.00 | 0.00  | 0.00  |
| 3  | 34.00 | 30.00  | 26.00  | 16.50  | 12.50  | 8.50  | 4.50  | 0.50  | -3.50  | -7.50  | -11.50  | -15.50  | -19.50  | -23.50  | -27.50 | -31.50  | -36.50  | (land) | 0.00  | 0.00  |
| 4  | 34.00  | 30.00  | 26.00  | 22.00  | 13.50  | 9.50  | 5.50  | 1.50  | -2.50  | -6.50  | -10.50  | -14.50  | -18.50  | -22.50  | -26.50 | -30.50  | -34.50  | (land) | 0.00  | 0.00 |
| 5  | 34.00  | 30.00  | 26.00  | 22.00  | 18.00  | 14.00  | 10.00  | 6.00  | 2.00  | -2.00  | -6.00  | -10.00  | -14.00  | -18.00  | -22.00 | -26.00  | -30.00  | -34.00 | -38.00  | (land)  |

You can use this table to determine how many frames A was held for in an IL *just from speed display!* No need for an input display for this!

- In addition to this, because of QF shenanigans, **rollouts don't let Mario keep the same amount of H speed when he lands**.
- On flat ground, 2F and 4F let him keep the most, then 1F, then 3F and 5F are tied for the least.
- This means that, if for instance you do a frame-perfect spinjumpdive out of a rollout, you will get much more height if the rollout was 2F than if it was 5F.
- Example of application in an IL: [Nail Strat](https://youtu.be/Y3ZF3DXhJ8I?t=21) does not work for certain rollout heights because of this mechanic. For this spacing, 3F and 4F are the necessary heights for it to work.
