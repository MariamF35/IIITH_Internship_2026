# WEEK 2 TASKS

Video used for this task: 
https://www.youtube.com/watch?v=MNn9qKG2UFI

---

## Task 1 — Create Python Virtual Environment

```bash
python3 -m venv yolo_env
yolo_env/bin/activate
```

## Task 2 — Install Ultralytics

```bash
pip install ultralytics
```

## Task 3 — Run YOLO Object Detection

Python script:

```python
from ultralytics import YOLO

model = YOLO("yolo11n.pt")  # pretrained model

results = model.predict(
    source="week 1/frames1_30fps",
    save=True,
    conf=0.25
)

print("Detection completed")
```

Output saved in:

```
runs/detect/predict/
```

---

## BONUS — Convert detected images → video

```bash
ffmpeg -framerate 30 -i runs/detect/predict/frame_%04d.jpg -c:v libx264 detected_video.mp4
```

---
