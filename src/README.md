# Hand Gesture Media Control

Control media playback on your computer using hand gestures detected through your webcam. Built with Python, MediaPipe, and OpenCV.

## What it does

Uses your webcam to track hand landmarks in real time and maps specific gestures to media controls — play/pause, volume up/down, skip tracks — without touching your keyboard or mouse.

## Tech Stack

- **Python 3.8+**
- **MediaPipe** — hand landmark detection (21 keypoints per hand)
- **OpenCV** — webcam capture and frame processing
- **PyAutoGUI / pycaw** — system-level media key simulation and volume control

## Project Structure

```
hand-gesture-media-control/
├── src/
│   ├── main.py              # Entry point — webcam loop and gesture dispatcher
│   ├── hand_detector.py     # MediaPipe hand tracking wrapper
│   └── gesture_mapper.py    # Maps detected gestures to media actions
├── requirements.txt
├── .gitignore
└── README.md
```

## Setup

### Prerequisites

- Python 3.8 or higher
- A working webcam

### Installation

```bash
# Clone the repo
git clone https://github.com/YASH-1507/hand-gesture-media-control.git
cd hand-gesture-media-control

# Create a virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Usage

```bash
python src/main.py
```

A webcam window opens showing your hand with tracked landmarks. Perform gestures to control media:

| Gesture | Action |
|---|---|
| Open palm (5 fingers) | Play / Pause |
| Thumb + Index pinch | Volume Up |
| Fist (closed hand) | Volume Down |
| Swipe right | Next Track |
| Swipe left | Previous Track |

Press `q` to quit.

## How It Works

1. **Capture** — OpenCV reads frames from the webcam at ~30 FPS
2. **Detect** — MediaPipe processes each frame and returns 21 hand landmarks with x, y, z coordinates
3. **Classify** — Custom logic calculates finger states (up/down) based on landmark positions to identify gestures
4. **Execute** — Recognized gestures trigger system media key events via PyAutoGUI

## Limitations

- Single-hand detection only
- Gesture recognition accuracy drops in low-light conditions
- Swipe gestures require calibration based on camera distance
- Currently supports Windows and macOS (Linux may need additional config for media keys)

## Future Improvements

- [ ] Add two-hand gesture support
- [ ] Implement configurable gesture-to-action mapping
- [ ] Add brightness control gestures
- [ ] Improve accuracy with a trained gesture classifier (e.g., TensorFlow Lite)
- [ ] Add on-screen visual feedback for recognized gestures
- [ ] Package as a system tray app

## License

This project is for educational purposes.
