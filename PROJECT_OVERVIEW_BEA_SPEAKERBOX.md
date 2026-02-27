# BEA_Speakerbox™

**Professional Voice Over Production with BEA E-Motion Intelligence**

![Version](https://img.shields.io/badge/version-2.0.0-blue.svg)
![Python](https://img.shields.io/badge/python-3.8+-blue.svg)
![Tests](https://img.shields.io/badge/tests-84%20passing-brightgreen.svg)
![License](https://img.shields.io/badge/license-MIT%20%2F%20Patent%20Pending-orange.svg)

BEA_Speakerbox is a **professional voice-over production engine** — a BEA Aura Console component grounded in the BEA_Aura_OS mathematical foundation. It is **not** a standalone application. It requires **BEA_Core** and is designed to run as part of the BEA Aura ecosystem.

**Every parameter is derived from BEA math — not heuristics:**

- `VoiceScanner` subclasses `BEAScanner` — inherits S°, L°, and all 32 E-motion states
- Voice frequencies → S° Sound Degree → BEA state E[0..31]
- Dominant operator (⊕⊖⊗⨀≠⧖) → vocal character + 6 performance metrics
- **84 unit tests, all passing**
- **15 emergent vocal effects** from operator combination
- **Console-as-cloud:** processes locally on BEA Aura, streams to thin-client apps via BEA_Shield VPN

---

## BEA Aura Console Context

BEA_Speakerbox is not a standalone application — it is a platform component that **requires BEA_Aura_OS** as its foundation and is designed to run as part of the **BEA Aura Console**.

```
BEA Aura Console
├── BEA_Core              ← Mathematical foundation (required dependency)
├── BEA_Beatbox           ← Sibling — rhythm data feeds into Speakerbox
├── BEA_Speakerbox        ← THIS COMPONENT — voice processing engine
│   └── SpeakerboxBridge feeds → BEA_Beatbox, BEA_4D_Audio, BEA_Health
└── BEA_4D_Audio          ← Receives spatial voice positioning data
```

### Console as Cloud

> The BEA Aura Console is your **personal cloud server** — not AWS, Google, or Azure.
> When you are away from home, BEA_Speakerbox connects back to your console
> via BEA_Shield VPN for processing, storage, and multi-channel production.

```
At Home:
  [BEA_Speakerbox] ─── direct ──→ [BEA Aura Console]

Away from Home (Future App):
  [BEA_Speakerbox App] ←→ Internet ←→ [BEA_Shield VPN] ←→ [BEA Aura Console]
                                              ↑
                                    Your home console is the cloud.
                                    No subscription. No data mining.
```

---

## Architecture Overview

```
BEA_Speakerbox/
├── bea_logic.py          — BEA Logic™: Emergence (1⊕1=3) / Divergence (1⊕1≠3)
├── vocal_processor.py    — 6 BEA operators applied to vocal parameters
├── voice_scanner.py      — VoiceScanner subclasses BEAScanner (inherits S°, L°, 32 states)
├── performance_engine.py — Real-time performance metrics from BEA states
├── spatial_voice.py      — 4D spatial voice positioning (X, Y, Z, E-motion)
├── director_engine.py    — Voice coaching from BEA state analysis
├── session_recorder.py   — Frame capture, timeline, JSON export
├── integration.py        — Bridge to BEA_Beatbox / BEA_4D_Audio / BEA_Health
├── demo_standalone.py    — Zero-dependency demo (6 sections)
└── tests/
    └── test_speakerbox.py — 84 unit tests (all passing)
```

---

## Quick Start

```bash
# From BEA_Aura_OS root
python -X utf8 BEA_Speakerbox/demo_standalone.py

# Run tests
python -m pytest BEA_Speakerbox/tests/test_speakerbox.py -v
```

### Basic Usage

```python
from BEA_Speakerbox import (
    VoiceScanner, PerformanceEngine, DirectorEngine,
    SessionRecorder, BEAOperator,
)

scanner  = VoiceScanner()
engine   = PerformanceEngine()
director = DirectorEngine()
recorder = SessionRecorder()

# Scan a voice frame (fundamental frequency + amplitude)
scan  = scanner.scan_voice(freq_hz=220.0, amplitude=0.65, latency_ms=5.0)
state = engine.update(scan)

# Real-time coaching
tips = director.analyze_state(state)
for tip in tips:
    print(tip.label)

# Record the frame
recorder.record(scan, e_degree=state.e_degree, timestamp_ms=0.0)

print(f"BEA State: E[{state.beu}]  Operator: {state.operator.value}")
print(f"Clarity: {state.clarity:.0%}  Projection: {state.projection:.0%}")
print(f"Overall Score: {state.overall_score:.0%}")
```

---

## Core Concepts

### The 32 BEA States

All voice signals encode to one of 32 discrete states using 5-bit binary:

```
Bit: [4][3][2][1][0]
      │  │  │  │  └─ Intensity   (0=low amplitude, 1=high)
      │  │  │  └──── Frequency   (0=low F0, 1=high F0 ≥1kHz)
      │  │  └─────── Phase       (0=leading, 1=lagging formant)
      │  └────────── Coherence   (0=unstable delivery, 1=consistent)
      └───────────── Latency     (0=realtime <16ms, 1=buffered)
```

### The 6 BEA Operators for Voice

| Operator | Element | Voice Character |
|----------|---------|-----------------|
| ⊕ FIRE | Combust | Sharp consonants, bright presence, energetic delivery |
| ⊖ WATER | Balance | Warm tone, smooth vowels, rich low-mid resonance |
| ⊗ AIR | Dissolve | Breathy quality, airy release, intimate distance |
| ⨀ SOLAR | Amplify | Full projection, broadcast-ready, maximum resonance |
| ≠ ETHER | Diverge | Character voice, pitch drama, expressive contrast |
| ⧖ TEMPORAL | Resonate | Measured pacing, consistent timing, cadence lock |

### Voice Types

| Voice Type | Frequency Range | Amplitude | BEA States |
|------------|----------------|-----------|------------|
| Breath | < 80 Hz | < 0.12 | E[0..3] |
| Whisper | 80–3000 Hz | < 0.18 | E[0..5] |
| Emotional Low | 80–120 Hz | 0.05–0.35 | E[0..7] |
| Chest Voice | 80–200 Hz | 0.30–0.82 | E[1..7] |
| Mid Voice | 150–350 Hz | 0.20–0.82 | E[3..13] |
| Head Voice | 300–600 Hz | 0.25–0.82 | E[8..15] |
| Full Projection | Any | > 0.82 | E[20..31] |
| Emotional High | 350–1200 Hz | > 0.45 | E[14..23] |

### S° Sound Degree

```
S° = log₂(f / 440 Hz) × 12
```

- 440 Hz (A4) → S° = 0°
- 220 Hz (A3) → S° = −12° (one octave below)
- 880 Hz (A5) → S° = +12° (one octave above)

### E° Temperature

E° (0.0–100.0) scales vocal parameter intensity:
- E° 0 → subtle effect (barely noticeable)
- E° 50 → balanced character
- E° 100 → extreme expression

### BEA Logic™ for Voice

```python
from BEA_Speakerbox import bea_logic_result, EMERGENCE, DIVERGENCE

# Two voice states combining
result = bea_logic_result(5, 10)

if result.result_type == EMERGENCE:
    print(f"Breakthrough! Voice transcended both registers")
    print(f"E° gain: {result.e_temperature}")  # Energy boost from combination
elif result.result_type == DIVERGENCE:
    print(f"Maximum contrast — dramatic tension between states")
```

---

## Module Reference

### `VoiceScanner(BEAScanner)`

```python
scanner = VoiceScanner()  # subclasses BEAScanner — inherits S°, L°, all 32 states
result = scanner.scan_voice(
    freq_hz=220.0,        # Fundamental frequency
    amplitude=0.65,       # Normalised amplitude (0.0–1.0)
    latency_ms=5.0,       # Processing latency
    formant_f1=800.0,     # Optional first formant (improves phase bit)
    coherence_score=0.7,  # Optional delivery stability (0.0–1.0)
)
print(result.bea_state)   # 0–31
print(result.voice_type)  # VoiceType enum
print(result.operator)    # BEAOperator enum
print(result.s_degree)    # S° Sound Degree
print(result.confidence)  # 0.0–1.0
```

### `PerformanceEngine`

```python
engine = PerformanceEngine()
state = engine.update(scan, e_degree=75.0)

# Six performance metrics (all 0.0–1.0)
print(state.clarity)        # Articulation quality (coherence bit prevalence)
print(state.projection)     # Vocal energy (mean amplitude)
print(state.consistency)    # Stability (low state variance)
print(state.emotion_range)  # Expressiveness (fraction of 32 states visited)
print(state.pacing)         # Cadence control (TEMPORAL operator prevalence)
print(state.resonance)      # Tonal richness (SOLAR/WATER operator prevalence)
print(state.overall_score)  # Weighted composite (0.0–1.0)

# Session analysis
summary = SessionSummary.from_engine(engine)
print(f"Rating: {summary.rating}")  # Exceptional/Strong/Good/Developing/Needs Work
```

### `DirectorEngine`

```python
director = DirectorEngine()

# Real-time tips (up to 3, highest priority first)
tips = director.analyze_state(state)
for tip in tips:
    print(f"[{tip.priority.name}] {tip.tip}")
    # e.g. "[CRITICAL] Clarity low — sharpen consonants, open vowels"

# Post-session coaching report
report = director.generate_session_report(summary)
print(report.format())
# "Session Report — Rating: Strong"
# "+ Clear articulation (clarity 72%)"
# "- Explore more emotional registers"
# "Exercise: BEA state journey — read from E[0] to E[31]..."
```

### `SpatialVoice`

```python
sv = SpatialVoice()

# 4D position from BEA state
pos = sv.position_from_state(bea_state=11, e_degree=75.0)
print(f"X={pos.x:.3f}  Y={pos.y:.3f}  Z={pos.z:.3f}  E={pos.e_motion}")
print(f"Distance: {pos.distance:.2f}m")
print(f"Attenuation: {pos.attenuation_db:.1f}dB")
print(f"Azimuth: {pos.azimuth_degrees:.1f}°")

# Reverb parameters
reverb = sv.get_reverb_params(pos, RoomType.BOOTH)
print(f"Reverb mix: {reverb.mix:.2f}  Decay: {reverb.decay_ms:.0f}ms")

# 4D spatial journey
journey = sv.journey(start_beu=0, end_beu=31, e_degree=70.0, steps=8)
```

### `SessionRecorder`

```python
recorder = SessionRecorder()

# Record frames
recorder.record(scan, e_degree=65.0, timestamp_ms=0.0)

# Analysis
print(recorder.ascii_timeline())
# [FAAAASSSTTTWWW...]
# F=Fire⊕  W=Water⊖  A=Air⊗  S=Solar⨀  E=Ether≠  T=Temporal⧖

# Export
data = recorder.export_session_data()  # JSON-serialisable dict
json_str = recorder.export_json()
```

### `SpeakerboxBridge`

```python
bridge = SpeakerboxBridge()

# → BEA_Beatbox: speech pace drives beat tempo
rhythm = bridge.to_beatbox_rhythm(perf_state, words_per_minute=140.0)

# → BEA_4D_Audio: spatial position becomes 3D audio params
audio  = bridge.to_4d_audio_params(position, RoomType.BOOTH)

# ← BEA_Health: biometrics inform recording context
ctx    = bridge.from_health_state(hrv_ms=45.0, heart_rate_bpm=82.0)

# ← BEA_Shield: threat level → vocal urgency
alert  = bridge.from_shield_threat(threat_score=0.75)
```

---

## Operator Combination Effects

15 named emergent vocal effects from pairing two operators:

| Combo | Name | Character |
|-------|------|-----------|
| ⊕+⊖ | Resonance | Bright warmth — punchy yet full body |
| ⊕+⊗ | Spark | Breathy ignition — whispered urgency |
| ⊕+⨀ | Broadcast | Maximum energy — peak voice power |
| ⊕+≠ | Drama | Ignited contrast — character with urgency |
| ⊕+⧖ | Staccato | Rhythmic punch — timed bright attack |
| ⊖+⊗ | Mist | Warm breath — intimate floating warmth |
| ⊖+⨀ | Presence | Rich power — full-spectrum warmth |
| ⊖+≠ | Depth | Warm contrast — emotional resonance |
| ⊖+⧖ | Legato | Smooth cadence — flowing consistency |
| ⊗+⨀ | Ambient | Expansive breath — airy projection |
| ⊗+≠ | Whisper | Intimate contrast — hushed drama |
| ⊗+⧖ | Breath | Timed breathing — paced intimacy |
| ⨀+≠ | Signature | Powerful character — iconic voice |
| ⨀+⧖ | Anchor | Grounded power — authoritative cadence |
| ≠+⧖ | Cadence | Rhythmic contrast — dramatic pacing |

---

## Room Types

| Room | Reverb Mix | Decay | Character |
|------|-----------|-------|-----------|
| STUDIO | 0.05 | 120 ms | Dry, close, intimate |
| BOOTH | 0.12 | 300 ms | Professional VO booth |
| HALL | 0.45 | 1800 ms | Concert hall richness |
| CATHEDRAL | 0.80 | 4500 ms | Vast, ethereal, long |
| OUTDOOR | 0.20 | 500 ms | Open, diffuse |
| INTIMATE | 0.03 | 80 ms | Whisper distance |

---

## Development Roadmap

### Phase 1 — Console Engine (Now)
- Complete BEA_Aura_OS–grounded Python library
- 84 unit tests, all passing
- 7 production modules + integration bridge
- Standalone demo

### Phase 2 — Console Integration (BEA Aura Console Established)
- REST API server running on the console
- BEA_Shield VPN remote access
- Multi-channel session recording (sync with BEA_Beatbox rhythms)
- BEA_Health biometric integration (HRV → recording context)
- MIDI export from cadence data

### Phase 3 — BEA_Speakerbox App (Future)
- Thin iOS/Android client
- Mic → [Internet] → [BEA_Shield VPN] → [Console] → voice params back to app
- Offline cached mode (last 32 sessions stored locally)
- No subscription. No cloud provider. Your console is the cloud.

---

## Testing

```bash
# Run full test suite (84 tests)
python -m pytest BEA_Speakerbox/tests/test_speakerbox.py -v

# Run demo
python -X utf8 BEA_Speakerbox/demo_standalone.py
```

**Test coverage:**

| Class | Tests | Coverage |
|-------|-------|---------|
| TestBEALogic | 10 | BEA Logic™ combust, emergence, divergence |
| TestVocalProcessor | 11 | 6 operators, 15 combo pairs |
| TestVoiceScanner | 10 | Voice type classification, S° formula |
| TestPerformanceEngine | 13 | All 6 metrics, session summary |
| TestSpatialVoice | 10 | 4D positioning, reverb, journey |
| TestDirectorEngine | 10 | Coaching tips, session reports |
| TestSessionRecorder | 10 | Frame recording, export, timeline |
| TestIntegration | 10 | HRV→E°, HR→BEU, bridges |

---

## License

See [LICENSE](LICENSE) — MIT open source core + Patent Pending technologies.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

## Contact

**Jeremy F. Jackson d/b/a BEATEK Holdings, LLC**
Email: jeremyjackson7@proton.me
Subject: `BEA_Speakerbox — [topic]`

Issues: [GitHub Issues](https://github.com/Beat-k/BEA_Aura_OS/issues)

---

*BEA_Speakerbox™ — Where E-Motion meets the human voice.*
*Own It Once. Benefit Forever. Power to the People ⚡*
