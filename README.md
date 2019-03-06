# ffmpeg Cheatsheet

A cheatsheet for ffmpeg.

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

Given a width, like, 538px, you can resize a video while retaining the aspect ratio
using:

```
ffmpeg -i in.mp4 -filter:v scale="538:trunc(ow/a/2)*2" -c:a copy out.mp4
```

### Crop videos

Crop a 80x60 square at position (200, 100).

```
ffmpeg -i in.mp4 -filter:v "crop=80:60:200:100" -c:a copy out.mp4
```