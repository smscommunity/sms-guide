---
layout: default
title: Individual Levels
permalink: /il/
has_children: True
nav_order: 3
has_toc: false
---

# Individual Levels
{: .no_toc }

1. TOC
{:toc}

## [IL Spreadsheet](https://sunmar.io/il){: .btn }

SMS has leaderboards on this spreadsheet for various individual-level–based categories, for practice, competition, and analysis. The full spreadsheet comprises tabs for:
* **ILs** – mostly-unrestricted ILs. The challenge of optimising a single level as much as possible co-exists with practice for Any% and other blue-coin–less categories.
* **RTA Strat ILs** – ILs on different strats to optimise and compare them. A kind of living documentation that gives an overview of how fast different things are.
* **120 ILs** – ILs with blue-coin requirements, for 120-Shine segment practice.
* **Misc ILs** – misc. ILs, motivated by bingo and category extension practice.
* **Best Splits/Segments** – for documenting your best times as achieved in Any% or 120-Shine runs.
* ***CE Extensions** – for extra category extensions (CEs); not ILs but just kept on this sheet.*

### Using the Sheet
First, **join** the sheet by messaging one of the admins mentioned on the sheet's front page on Discord with your Google account's email address. Be warned that **the name on your Google account will be clearly visible in the sheet's activity**. Once given access, you can freely edit the space at the end of each sheet – take out a row (column in the case of RTA Strat ILs) on any sheet you want by typing in your name, and now, you can enter your times. A mod will later protect your row so only you and the mods can edit it.

### Sheet Rules
[ILs Sheet Rules](/sms-guide/info/il/rules/){: .btn }

Please read the rules of the IL spreadsheet at this link. These rules apply to the main tab, **ILs**; other tabs loosely abide by these but their rules are informal and have some deviations. Check example videos from the sheet you're interested in and ask in the Discord's #help channel if still unclear.

### Setting Up Hardware
[Practice Codes](https://gct.zint.ch){: .btn }

ILs in SMS are based around the infrastructure of these cheat codes. This makes them accessible to every Wii and PC Dolphin emulator setup, but rarely any GameCube. Homebrew is required for Wii/GameCube. Timing is done via a hacked in-game timer, and selecting and resetting levels is done by holding button combinations during a load (usually an "exit area").

[Practice Codes Install Guide](https://gct.zint.ch/guide.html){: .btn }

Here's the installation guide. Please make sure to follow it exactly – particularly when it recommends something, you should see it as *mandatory* unless you know what you're doing or otherwise got things working. In particular, check that:
- (console) **your Homebrew installation did everything mentioned in the [linked guide](https://wii.guide)**;
- (console) **you're using [Nintendont 6.498 (Sept 2021) or later](https://zint.ch/NintendontPackager)** *(6.489 is also known to work well but earlier/later versions often don't)*;
- (emulator) **you're using a [recent (2020 or later) beta version of Dolphin](https://dolphin-emu.org/download/)**.
- (emulator) **your settings match our setup guide found [here](/sms-guide/setup/emu)**

ILs in SMS are less accessible in (mostly) requiring cheat codes and hacked Wiis, but this is necessary practically. Having to retime every IL from video is an unmanageable amount of work that sets back the accessibility (and popularity) of doing ILs far more. Having fast resets is also a substantial buff to how much they can get optimised, and like the previous point, how enjoyable and healthy they are to play, learn with and compete in.

## Submission Guide (ILs Sheet)
*These guidelines largely apply to the spreadsheet tabs other than "ILs" as well, but not entirely, and aren't currently rigidly enforced. Check examples from the sheet you want to submit to, and ask in the Discord for clarification.*
### Formatting
Make sure your time is formatted as `4.51` or `16.30` or `1:39.22`. This is different to what the timer looks like in-game – there's a `.` between the seconds and centiseconds, and a `:` after the minutes if required. Check back 10s after typing in a time; if it gets highlighted red then the formatting needs to be fixed. Misformatted times don't count for points/medals.

### Video?
All top 3 times (as well as specific setup-intensive levels as noted in their columns) must have a linked video. Video is otherwise optional, but highly encouraged. Let me explain why...

The cost of recording an IL video for someone who's able to record an Any% run is very small. See [this section](/sms-guide/info/video-tools/#recording-short-videos) to judge for yourself. The benefit is that you contribute to a collection of videos that can be used by everyone to learn strats, time strats, and get a feel for what level of play corresponds to what times. Videos also legitimise your runs and show respect for the competition, particularly when they rank highly for a specific level or you've reached a high overall level in points ranking.

[Video Tools Guide](/sms-guide/info/video-tools/){: .btn }

Everybody should check this out to find out what options are available for recording videos of ILs, as well as cropping, frame-analysing/retiming and downloading them. YouTube submissions are preferred, though Twitch clips are fine if that's simpler for you. Twitter is allowed but discouraged. These preferences are due to how easy it is to frame-advance and download videos, as well as Twitter's uncontrollable viewer-side video hyper-compression.

### Links
Hyperlinks are used to link videos for IL submissions; right-click a cell, then **Insert Link** (or ctrl+k). If you replace a time with video with one without video, check that the link is gone (possibly right-click, then **Remove Link**). Make sure to check [rules #4 and #5](/sms-guide/info/il/rules/) for the rules and guidelines the video must/should conform to.

If you're struggling to link a video (e.g. the link keeps getting recoloured black and not counted in your video count despite being there), try selecting the cell, menuing into *Format > Number > Plain Text*, then ctrl+k and click *Apply* – this is a known workaround for buggy link detection.

### Notes
Adding notes is a convenient way of commenting on your submissions in a way that's immediately apparent to people browsing the sheet. Right-click a cell and select **Insert Note**. Don't use comments, those can be deleted by anyone and are used to update mods about a WR on the RTA sheet.

### Comments
Adding a comment is our process of easily alerting the mods to update your newly achieved WR on the RTA sheet, since currently it is not automated. Just add a comment on your cell that has your time/submission as "new WR". Add the level name as well if you would like. The comment will be removed once a mod updated the WR row with your time.

### IGT

By default, all stated times for ILs must match the time shown in-game with the *Shine Get Timer* cheat code. However, you're allowed to submit times without the timer, e.g. from a full-game run, to be retimed by a mod; type `/ticket create [insert topic]` in any channel in the discord. Such submissions must be accompanied by a *cropped* (not timestamped) video, for ease of verification. If you're interested in learning how to retime your own videos, see [here](/sms-guide/info/retime/). The times are frame-counted and/or adjusted for loads/text.
