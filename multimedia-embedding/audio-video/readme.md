# Video and audio content

Now that we are comfortable with adding simple images to a webpage, the next step is to start adding video and audio players to your HTML documents! In this article we'll look at doing just that with the `<video>` and `<audio>` elements; we'll then finish off by looking at how to add captions/subtitles to your videos.

## Video and audio on the web

### The `<video>` element

The `<video>` element allows you to embed a video very easily. A really simple example looks like this:

```HTML
<video src="rabbit320.webm" controls>
  <p>
    Your browser doesn't support HTML video. Here is a
    <a href="rabbit320.webm">link to the video</a> instead.
  </p>
</video>
```

The features of note are:

- src
In the same way as for the `<img>` element, the src (source) attribute contains a path to the video you want to embed. It works in exactly the same way.

- controls
Users must be able to control video and audio playback (it's especially critical for people who have epilepsy.) You must either use the controls attribute to include the browser's own control interface, or build your interface using the appropriate JavaScript API. At a minimum, the interface must include a way to start and stop the media, and to adjust the volume.

```HTML
<video controls>
  <source src="rabbit320.mp4" type="video/mp4" />
  <source src="rabbit320.webm" type="video/webm" />
  <p>
    Your browser doesn't support this video. Here is a
    <a href="rabbit320.mp4">link to the video</a> instead.
  </p>
</video>
```

Here we've taken the src attribute out of the actual `<video>` tag, and instead included separate `<source>` elements that point to their own sources. In this case the browser will go through the `<source>` elements and play the first one that it has the codec to support. Including WebM and MP4 sources should be enough to play your video on most platforms and browsers these days.

Each `<source>` element also has a `type` attribute. This is optional, but it is advised that you include it. The `type` attribute contains the `MIME type` of the file specified by the `<source>`, and browsers can use the `type` to immediately skip videos they don't understand. If `type` isn't included, browsers will load and try to play each file until they find one that works, which obviously takes time and is an unnecessary use of resources.

### Other `<video>` features

There are a number of other features you can include when displaying an HTML video. Take a look at our next example:

```HTML
<video
  controls
  width="400"
  height="400"
  autoplay
  loop
  muted
  preload="auto"
  poster="poster.png">
  <source src="rabbit320.mp4" type="video/mp4" />
  <source src="rabbit320.webm" type="video/webm" />
  <p>
    Your browser doesn't support this video. Here is a
    <a href="rabbit320.mp4">link to the video</a> instead.
  </p>
</video>

```

Features include:

- width and height
You can control the video size either with these attributes or with CSS. In both cases, videos maintain their native width-height ratio — known as the aspect ratio. If the aspect ratio is not maintained by the sizes you set, the video will grow to fill the space horizontally, and the unfilled space will just be given a solid background color by default.

- autoplay
Makes the audio or video start playing right away, while the rest of the page is loading. You are advised not to use autoplaying video (or audio) on your sites, because users can find it really annoying.

- loop
Makes the video (or audio) start playing again whenever it finishes. This can also be annoying, so only use if really necessary.

- muted
Causes the media to play with the sound turned off by default.

- poster
The URL of an image which will be displayed before the video is played. It is intended to be used for a splash screen or advertising screen.

- preload
Used for buffering large files; it can take one of three values:

  - "none" does not buffer the file
  - "auto" buffers the media file
  - "metadata" buffers only the metadata for the file

### The `<audio>` element

The `<audio>` element works just like the `<video>` element, with a few small differences as outlined below. A typical example might look like so:

```HTML
<audio controls>
  <source src="viper.mp3" type="audio/mp3" />
  <source src="viper.ogg" type="audio/ogg" />
  <p>
    Your browser doesn't support this audio file. Here is a
    <a href="viper.mp3">link to the audio</a> instead.
  </p>
</audio>

```

This takes up less space than a video player, as there is no visual component — you just need to display controls to play the audio. Other differences from HTML video are as follows:

- The `<audio>` element doesn't support the width/height attributes — again, there is no visual component, so there is nothing to assign a width or height to.
- It also doesn't support the poster attribute — again, no visual component.

## Displaying video text tracks

Now we'll discuss a slightly more advanced concept that is really useful to know about. Many people can't or don't want to hear the audio/video content they find on the Web, at least at certain times. For example:

- Many people have auditory impairments (such as being hard of hearing or deaf) so can't hear the audio clearly if at all.
- Others may not be able to hear the audio because they are in noisy environments (like a crowded bar when a sports game is being shown).
- Similarly, in environments where having the audio playing would be a distraction or disruption (such as in a library or when a partner is trying to sleep), having captions can be very useful.
- People who don't speak the language of the video might want a text transcript or even translation to help them understand the media content.

Wouldn't it be nice to be able to provide these people with a transcript of the words being spoken in the audio/video? Well, thanks to HTML video, you can. To do so we use the WebVTT file format and the `<track>` element.

WebVTT is a format for writing text files containing multiple strings of text along with metadata such as the time in the video at which each text string should be displayed, and even limited styling/positioning information. These text strings are called cues, and there are several kinds of cues which are used for different purposes. The most common cues are:

- subtitles
Translations of foreign material, for people who don't understand the words spoken in the audio.

- captions
Synchronized transcriptions of dialog or descriptions of significant sounds, to let people who can't hear the audio understand what is going on.

- timed descriptions
Text which should be spoken by the media player in order to describe important visuals to blind or otherwise visually impaired users.

A typical WebVTT file will look something like this:

```Text
WEBVTT

1
00:00:22.230 --> 00:00:24.606
This is the first subtitle.

2
00:00:30.739 --> 00:00:34.074
This is the second.
```

To get this displayed along with the HTML media playback, you need to:

- Save it as a .vtt file in a sensible place.
- Link to the .vtt file with the `<track>` element. `<track>` should be placed within `<audio>` or `<video>`, but after all `<source>` elements. Use the kind attribute to specify whether the cues are subtitles, captions, or descriptions. Further, use srclang to tell the browser what language you have written the subtitles in. Finally, add label to help readers identify the language they are searching for.

Here's an example:

```HTML
<video controls>
  <source src="example.mp4" type="video/mp4" />
  <source src="example.webm" type="video/webm" />
  <track kind="subtitles" src="subtitles_es.vtt" srclang="es" label="Spanish" />
</video>
```

[Find working example by clicking here](https://github.com/iandevlin/iandevlin.github.io/tree/master/mdn/video-player-with-captions)
