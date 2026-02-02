# Pose to Music Workshop

Turn body poses into musical notes in the browser using:

- Teachable Machine Pose model
- TensorFlow.js + tmPose
- Webcam input + Web Audio API

## How it works

- The app runs in `id_pose.html`.
- It loads `model.json`, `metadata.json`, and `weights.bin` from the project root.
- Each frame, it predicts the top pose class.
- If confidence is high enough, it plays a mapped note.

Use Teachable Machine's pose detector to generate the model/metadata/weights files. Name each pose as a single capital letter to denote a musical note. 

Current note map (same letter -> same note in octave 4):

- `A` -> A4 (440.00 Hz)
- `B` -> B4 (493.88 Hz)
- `C` -> C4 (261.63 Hz)
- `D` -> D4 (293.66 Hz)
- `E` -> E4 (329.63 Hz)
- `F` -> F4 (349.23 Hz)
- `G` -> G4 (392.00 Hz)

Class names can be either:

- `A` to `G`, or
- `Pose A` to `Pose G`

## Run locally

From the project folder:

```bash
python3 -m http.server 8000 --bind 127.0.0.1
```

Then open:

```text
http://127.0.0.1:8000/id_pose.html
```

Click **Start** and allow camera permission.

## Requirements

- A modern browser (Chrome/Edge/Firefox)
- Webcam access enabled
- Internet connection (CDN scripts are loaded from jsDelivr)

## Tuning

In `id_pose.html` you can adjust:

- `CONFIDENCE_THRESHOLD` (higher = fewer false triggers)
- `NOTE_FREQ` (change pitch mapping)
- `playNote()` envelope values (attack/decay/length)
