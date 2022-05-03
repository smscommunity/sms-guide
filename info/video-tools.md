---
layout: default
title: Video Tools
permalink: /info/video-tools
parent: Misc General Info
nav_order: 2
---

# Video Tools
{: .no_toc }

1. TOC
{:toc}

## Recording Short Videos
There are 2 options for recording videos (of, say, length <10 mins) that both make recording SMS ILs very low-effort. Both rely on you having already set up OBS to record/stream in general.

1. **Twitch Clips/Highlights**  
You can stream to Twitch. Whenever you PB, create a [**stream marker**](https://help.twitch.tv/s/article/creating-highlights-and-stream-markers) by typing e.g. `/marker bianco 3 39.08`. After ending stream, you can open the past broadcast in the Twitch [**highlighter**](https://help.twitch.tv/s/article/creating-highlights-and-stream-markers) – make sure that **store past broadcasts** is enabled in Twitch settings – and the markers appear in the timeline, allowing you to create **highlights**. Creating **clips** can be a bit faster, but they're limited to 1 minute in length. You can create clips on the spot though, if you have your stream up while streaming, or afterwards from stream markers – while in the highlighter, click the cog on the video player, then "copy the video URL at ...", paste it into a new tab and then create the clip from there. You can make an **alt account** to stream things you don't intend to be watched; you can save different stream keys to different OBS **profiles** to make it easy to switch between accounts. *This is a good option for auto-hosted videos, but requires a permanently-live internet connection*.

2. **OBS Replay Buffer + YouTube**  
OBS **replay buffer** is a feature you can enable via its tab in OBS output settings (also available in [Streamlabs OBS](https://streamlabs.com/content-hub/post/instant-replays-in-streamlabs-obs)). It records your video in a fixed-size space in memory that's cyclically overwritten, meaning the previous few minutes are available at any given time. Set the replay size to be longer than the IL, and bind a hotkey to **save replay**. Then, pressing the hotkey will save the last few minutes of recording to a file. Hence, when you PB, you just press the button to save a video. Make sure to check the replay size beforehand, and you must **start replay buffer** in OBS before using it! These videos can then be put on a throwaway YouTube account; no need to present them or even title them. You may optionally crop the video before uploading (see below), but if not, please timestamp the link. *This is a good option for recording ILs offline, but requires more clicks to put them up online*.

<details>
<summary markdown="span"> How to Streamline Uploading to YouTube </summary> {: .text-delta }

To streamline uploading clips to YouTube, edit a few default settings. In [YouTube Studio](https://studio.youtube.com/), click on Settings in the sidebar. Then in Channel > Advanced Settings, set your channel as "not made for kids", and in Upload Defaults, set Visibility to Public or Unlisted. Then, to upload videos, you can put them all in a folder and upload them all at the same time, but have to publish them one-by-one (by clicking Edit, selecting the third tab, then Publish). You receive a link each time you publish, ready to paste in a sheet.
</details>

## Cropping Videos
Use [**LosslessCut**](https://github.com/mifi/lossless-cut); download the latest release [here](https://github.com/mifi/lossless-cut/releases) (the zip is 450MB after extraction but starts instantly; the standalone exe is 100MB but takes about 7s to start).

**What it does:** every video you have has been *encoded* – the computationally-intensive and quality-degrading process of turning a video from a series of frames of pixels, which takes up enormous disk space, into video files of manageable size. The downside of encoding is that most frames are specified as differences from other frames, meaning the video can't be cropped to those frames without decoding and re-encoding, losing time and video quality. The other, standalone frames, known as **keyframes**, occur every few seconds in the video. LosslessCut lets you seek between these and then creates a trimmed copy of your video, instantly and with no quality degradation, and also starts up fast. None of these things are true of a full-on video editor like Premiere Pro.

**How to use:** click on the seeking bar, then press `alt + ←/→` to tab between the keyframes. Press `i` to select start point and `o` to select end. Then click Export (keep the advanced options default). *If you don't crop on a keyframe then the program snaps to the nearest inclusive one, whence the crop boundaries are slightly off, but the video is otherwise fine*.

To crop a video after uploading to YouTube, you can alternatively use YouTube Studio –  edit a video, then click Editor in the sidebar, then trim.

## Frame-Analysing Videos
You may want to **watch videos frame-by-frame**, or **retime videos**. On YouTube, you can do the former by pressing the `,` and `.` keys, but it's impossible on Twitch. In general, you need to download videos (see next section) to analyse them. **VirtualDub** is currently standardised for use in SMS (though it's Windows-only) – install the [program](http://virtualdub.sourceforge.net/) and [extension](https://codecpack.co/download/FFInputDriver.html) (which makes it support a wider range of video formats, notably mp4).

Just click anywhere on the seeking bar and tap `←/→` to frame-advance. The HUD below gives you absolute frame-numbers, which you can subtract to find durations counted in frames. Go to *Video > Frame Rate* (or press `ctrl + r`) to see, at the top, the frame-rate of the video. Then a duration is the difference of two frame-numbers divided by the frame-rate.

## Downloading Videos
Recommended tools for downloading videos:
* **Twitch Clips** – [Clipr.](https://clipr.xyz/) (online)
* **Twitch VoDs** – [Twitch Leecher](https://github.com/Franiac/TwitchLeecher/releases) (offline; allows cropping before downloading)
* **YouTube Videos** – [yt-dlp](https://github.com/yt-dlp/yt-dlp) (offline, command-line–based; this is standardised for retiming, using the `-f bestvideo` parameter).
* **YouTube Clips** – [YouTube Cutter](https://youtube-cutter.org/) (online; allows cropping before downloading; a bit buggy so recommend including an extra 5s at the beginning of the crop).
