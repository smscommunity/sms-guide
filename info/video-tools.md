---
layout: default
title: Video Tools
parent: Info
nav_order: 2
---

# Video Tools
{: .no_toc }

<details open markdown="block">
<summary>Table of contents</summary> {: .text-delta }
1. TOC
{:toc}
</details>

## Recording Short Videos
There are 2 options for recording videos (of, say, length <10 mins) that both make recording SMS ILs very low-effort. Both rely on you having already set up OBS to record/stream in general.

1. **Twitch Clips**  
You can stream to Twitch, post a message in your chat when you PB, then go back through the recording of your broadcast to clip it. You could also have your stream open in another window and make clips as you go. ILs longer than a minute require highlighting the video instead (after ending stream). Make sure that **store past broadcasts** is enabled in Twitch settings. Many people make an alt account to stream things they don't intend to be watched. *This is a good option for auto-hosted videos, but requires a permanently-live internet connection*.

2. **OBS Replay Buffer + YouTube**  
**OBS Replay Buffer** is a feature you can enable via its tab in OBS output settings (also available in [Streamlabs OBS](https://streamlabs.com/content-hub/post/instant-replays-in-streamlabs-obs)). It records your video in a fixed-size space in RAM that's cyclically overwritten, meaning the previous few minutes are available at any given time. Set the replay size to be longer than the IL, and bind a hotkey to **save replay**. Then, pressing the hotkey will save the last few minutes of recording onto your file system. Hence, when you PB, you just press the button to save a video. Make sure to check the size beforehand, and you must start the replay buffer in OBS before using it! These videos can then be put on a throwaway YouTube account; no need to present them or even title them. You may optionally crop the video before uploading (see below), but if not, please timestamp the link. *This is a good option for recording ILs offline, but requires more clicks to put them up online*.

<details markdown="block">
<summary> How to Streamline Uploading to YouTube </summary> {: .text-delta }
To streamline uploading clips to YouTube, edit a few default settings. In [YouTube Studio](https://studio.youtube.com/), click on Settings in the sidebar. Then in Channel > Advanced Settings, set your channel as "not made for kids", and in Upload Defaults, set Visibility to Public or Unlisted. Then, to upload videos, you can put them all in a folder and upload them all at the same time, but have to publish them one by one (but you receive a link once you complete the wizard each time, ready to paste in a sheet).
</details>

## Cropping Videos
Use [**LosslessCut**](https://github.com/mifi/lossless-cut) (download the latest release [here](https://github.com/mifi/lossless-cut/releases)). This is a simple GUI wrapper around the FFMPEG video tool library, which allows you to trim videos without re-encoding them. Encoding is the slow process of turning a video from a sequence of frames of pixels, which takes up enormous disk space, into files of manageable size, and has been done to every video you have. Encoded videos can't be split easily on a specific frame, but can on **keyframes**, which occur every few seconds in the video. LosslessCut picks these out and creates a cropped copy of your video, *instantly* and with *no quality degradation*. That's not possible if you just use a video editor or player. It is also lighter than such software.

Ensure *keyframe cut* (not "normal cut") is selected on the top-right. You can click on the seeking bar and press `alt + ←/→` to see where the keyframes are exactly and what your crop will look like. Press `i` to select start point and `o` to select end. Then click Export. *If you don't crop on a keyframe then I think the program snaps to the nearest inclusive one so the crop boundaries are slightly off*.

## Frame-Analysing Videos
You may want to **watch videos frame-by-frame**, or **retime videos**. On YouTube, you can do the former by pressing the `,` and `.` keys, but it's impossible on Twitch. In general, you need to download videos (see next section) to analyse them. **VirtualDub** is recommended for accuracy (though it's Windows-only) – install the [program](http://virtualdub.sourceforge.net/) and [extension](https://codecpack.co/download/FFInputDriver.html) (which makes it support a wider range of video formats).

Just click anywhere on the seeking bar and tap `←/→` to frame-advance. The HUD below gives you absolute frame-numbers, which you can subtract to find durations counted in frames. Go to *Video > Frame Rate* (or press `ctrl + r`) to see, at the top, the frame-rate of the video. Then a duration is the difference of two frame-numbers divided by the frame-rate.

## Downloading Videos
Tools for downloading videos I recommend:
* **Twitch Clips** – [Clipr.](https://clipr.xyz/) (online)
* **Twitch VoDs** – [Twitch Leecher](https://github.com/Franiac/TwitchLeecher/releases) (offline; allows cropping before downloading)
* **YouTube Videos** – [YouTube Cutter](https://youtube-cutter.org/) (online; allows cropping before downloading; a bit buggy so recommend including an extra 5s at the beginning of the crop; probably use something else to download full videos – no specific recommendations but I use [JDownloader](https://jdownloader.org/)).
