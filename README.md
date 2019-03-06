# ffmpeg cheatsheet

A cheatsheet for [ffmpeg](https://ffmpeg.org/).

## Installing ffmpeg

The simplest way to install ffmpeg on macOS is by using
[brew](https://brew.sh/).

```
brew install ffmpeg
```

## Cheatsheet

The following are the most common commands that I use.

### Change File Type

To change the file type, specify the desired filetype in the output file.

For instance, to change a video from `.mov` to `.mp4`, you would run:

```
ffmpeg -i in.mov out.mp4
```

### Trim Video

Trim the start of a video using `-ss {SECONDS}`. Then, specify the duration using `-t {SECONDS}`.

For instance, if you want a video that is 5 seconds long that starts at 4.5 seconds in, you would use:

```
ffmpeg -i in.mp4 -ss 4.5 -t 5 out.mp4
```

### Slow Down a Video

Slow a video using a filter. This example slows the video by four times.

```
ffmpeg -i in.mp4 -filter:v "setpts=4.0*PTS" out.mp4
```

### Scale to a Specific Width

Given a desired video width, like, 538px, you can resize a video to that width while retaining the aspect ratio
using:

```
ffmpeg -i in.mp4 -filter:v scale="538:trunc(ow/a/2)*2" -c:a copy out.mp4
```

### Crop videos

Crop a 80x60 square at position (200, 100).

```
ffmpeg -i in.mp4 -filter:v "crop=80:60:200:100" -c:a copy out.mp4
```

### Generating a Poster Image

A poster image is an image that displays while a video is loading in the browser. It is particularly
valuable for mobile devices.

To generate a representative image from the 7th second of a video, you can run this command:

```
ffmpeg -i in.mp4 -ss 00:00:07.000 -vframes 1 out.jpg
```

For more common frame extraction commands, see
[this post](https://www.bugcodemaster.com/article/extract-images-frame-frame-video-file-using-ffmpeg).
