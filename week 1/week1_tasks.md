# WEEK 1 TASKS

## Task 1 — Extract frames from YouTube video

### Install tools

```bash
sudo apt update
sudo apt install ffmpeg
pip install yt-dlp
```

### Download video

```bash
yt-dlp -f mp4 -o video.mp4 "YOUTUBE_LINK"
```

### Extract images from video

Extract 1 frame per second:

```bash
mkdir frames
ffmpeg -i video.mp4 -vf fps=1 frames/frame_%04d.jpg
```

---

## Task 2 — Generate 1800 images & recreate video

Extract 30 fps for 1 minute:

```bash
ffmpeg -i video.mp4 -t 60 -vf fps=30 frames_30fps/frame_%04d.jpg
```

Recreate video from images:

```bash
ffmpeg -framerate 30 -i frames_30fps/frame_%04d.jpg -c:v libx264 -pix_fmt yuv420p output_video.mp4
```

---

## Task 3 — Add music to video

Download 1-minute free music from Pixabay.

Trim audio to 1 min:

```bash
ffmpeg -i music.mp3 -t 60 trimmed_music.mp3
```

Merge audio + video:

```bash
ffmpeg -i output_video.mp4 -i trimmed_music.mp3 -c:v copy -c:a aac final_video.mp4
```

---
