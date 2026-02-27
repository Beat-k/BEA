# BEA Motion Body™ — macOS Edition

> **The controller you don't wear. Rebuilt for Apple Silicon.**

[![Platform](https://img.shields.io/badge/platform-macOS%2014%2B%20ARM64-black.svg)](https://www.apple.com/macos/)
[![Apple Silicon](https://img.shields.io/badge/Apple%20Silicon-M1%2FM2%2FM3%2FM4-blue.svg)](https://www.apple.com/mac/)
[![Python](https://img.shields.io/badge/Python-3.12%2B%20ARM64-yellow.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-Commercial-red.svg)](https://beatek.io/licensing)
[![Patent Pending](https://img.shields.io/badge/Patent-Pending-orange.svg)](https://www.uspto.gov/)

---

**BEA Motion Body — macOS Edition** is a native Apple Silicon body and hand tracking platform
built on AVFoundation, Apple Vision framework, Core ML, and Metal. It is a **separate product**
from the cross-platform BEA Motion Body (Windows/Linux) edition, purpose-built for
professionals and studios on macOS.

**No MediaPipe. No OpenCV. No Rosetta. No workarounds.**

---

## Requirements

| Requirement | Minimum |
|-------------|---------|
| macOS | 14.0 Sonoma (ARM64) |
| Python | 3.12 (ARM64 native binary) |
| Hardware | Apple M1 or later |
| Camera | Built-in FaceTime HD or USB UVC |

---

## Quick Install

```bash
# ARM64 Python 3.12 required — verify before installing
python3 --version     # must be 3.12+
python3 -c "import platform; print(platform.machine())"  # must print arm64

pip install --prefer-binary "bea-motion-body-macos"
```

---

## Quick Start

```python
# Hand tracking
from bea_motion_glove_macos import HandTracker

tracker = HandTracker(cameras=1, confidence=0.8)
with tracker:
    for frame in tracker.stream():
        left, right = frame.hands
        print(f"Left index tip: {left.index_tip}")
        print(f"Gesture: {frame.gesture}")

# Leg / body tracking
from bea_motion_legs_macos import LegTracker, LocomotionMode

tracker = LegTracker(mode=LocomotionMode.HEEL, cameras=1)
with tracker:
    for frame in tracker.stream():
        print(f"Pedal state: {frame.pedal_state}")
        print(f"Kick event: {frame.kick_event}")
```

---

## Architecture

```
AVFoundation         → Camera capture (native auth, 4K, multi-device)
Vision Framework     → Hand/body pose estimation (VN requests, ARM64 native)
Core ML + ANE        → Gesture classification (.mlpackage, Neural Engine)
Metal / MetalKit     → Real-time skeletal overlay rendering
PyObjC              → Python bridge to all of the above
```

---

## Demos

```bash
python demos/demo_hands.py       # Hand pose + gesture recognition
python demos/demo_feet.py        # Leg tracking + locomotion
python demos/demo_full_body.py   # Full body skeletal overlay
python demos/demo_racing.py      # Racing pedal simulation
```

---

## Documentation

- [docs/INSTALLATION.md](docs/INSTALLATION.md) — Full setup guide
- [docs/APPLE_SILICON.md](docs/APPLE_SILICON.md) — Neural Engine optimization
- [docs/CORE_ML_MODELS.md](docs/CORE_ML_MODELS.md) — Model training and deployment
- [docs/AVFOUNDATION.md](docs/AVFOUNDATION.md) — Camera setup on macOS
- [docs/ENTERPRISE_LICENSING.md](docs/ENTERPRISE_LICENSING.md) — Licensing tiers

---

## Licensing

This is a commercial product. See [docs/ENTERPRISE_LICENSING.md](docs/ENTERPRISE_LICENSING.md).

**Contact:** jeremyjackson7@proton.me

---

**BEATEK Holdings, LLC** | *BEA Motion Body — macOS Edition* | *February 2026*

*macOS, Apple Silicon, Core ML, Vision, Metal, AVFoundation, and Neural Engine are
trademarks of Apple Inc. BEATEK Holdings, LLC is not affiliated with Apple Inc.*
