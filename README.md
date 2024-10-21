##  Convert videos for twitter/X 
Uploading videos to X tends to be prone to errors since they are very picky about what formats they accept. This bash one-liner helps you convert to a format that works.
```
ffmpeg -i "$1" -c:v libx264 -crf 20 -preset slow -vf format=yuv420p -c:a aac -movflags +faststart "${1%.*}_twitter.mp4"
```

To use this one-liner, save it to a file (e.g. `convert_videos`) and make it executable with `chmod +x convert_videos`.

Then, you can run it by passing the input filename as an argument:
```bash
./convert_video video_clip.mp4
# output
video_clip_twitter.mp4
```
This will produce a new video file with the `_twitter` extension.


What is does:
- uses input video file ($1 in the command)
- strips out the file extension from the filename and attaches _twitter to it
- converts video to X acceptable format
