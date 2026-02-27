# BEA_Beatbox™

**Beatbox Recognition & Emotional Beat Generation**
*A BEA Aura Console Component*

[![Version](https://img.shields.io/badge/version-2.0.0-blue.svg)](https://github.com/Beat-k/BEA_Beatbox)
[![BEA_Aura_OS](https://img.shields.io/badge/requires-BEA__Aura__Core-purple.svg)](../README.md)
[![Python](https://img.shields.io/badge/python-3.8+-green.svg)](https://python.org)
[![License](https://img.shields.io/badge/license-MIT%20%2B%20Patent%20Pending-red.svg)](LICENSE)
[![Tests](https://img.shields.io/badge/tests-80%20passed-brightgreen.svg)](tests/)
[![Patent](https://img.shields.io/badge/Patent-Pending-orange.svg)](LICENSE)

> **BEA_Beatbox is a component of the BEA Aura Console ecosystem.**
> It requires [BEA_Aura_OS](../README.md) and is designed to run as part of the
> unified BEA Aura platform. Standalone mode is available for development and integration work.

---

## What Is BEA_Beatbox?

BEA_Beatbox is the **beatbox recognition and emotional beat generation** component of the
BEA Aura Console. Built entirely on the BEA_Aura_OS mathematical foundation, it maps
vocal sounds to BEA electronic motion states and generates drum patterns, audio parameters,
and elemental kit configurations driven by the same 32-state / 6-operator framework that
powers all four BEA Aura Console pillars.

**Every parameter is derived from BEA math — not heuristics:**

- Vocal frequencies → S° Sound Degree → BEA state E[0..31]
- BEA state + E° temperature → BPM, filter, volume, complexity
- Dominant operator (⊕⊖⊗⨀≠⧖) → pattern character + kit acoustic shape
- BEA Logic™ (1⊕1=3) → creative emergence detection between sound pairs

---

## BEA Aura Console Context

```
BEA Aura Console
├── BEA_Core             ← Mathematical foundation (required dependency)
├── BEA_Beatbox          ← THIS COMPONENT — emotional pattern engine
│   └── Feeds rhythm/tempo data → BEA_Speakerbox (speech pace → beat sync)
├── BEA_Speakerbox       ← Voice processing sibling
└── BEA_4D_Audio         ← Spatial audio consumer of Beatbox patterns
```

BEA_Beatbox and BEA_Speakerbox are **sibling components** — both inherit from BEA_Core.
Neither is the foundation the other builds on. BEA_Beatbox feeds rhythm and tempo data to
BEA_Speakerbox for speech-pace synchronization, and its elemental kit patterns drive
spatial operator effects in BEA_4D_Audio. BEA_Health provides biometric HRV input to
modulate E° temperature for pattern intensity.

### Integration Points

- **→ BEA_Speakerbox:** Speech pace (words per minute) drives beat tempo sync via `BeatboxBridge`
- **→ BEA_4D_Audio:** Elemental kit patterns drive spatial operator effects
- **← BEA_Health:** Biometric HRV data informs E° temperature for pattern intensity modulation

### Console as Cloud

> The BEA Aura Console is your **personal cloud server** — not a subscription to AWS,
> Google, or Azure. When you leave home, the BEA_Beatbox mobile app (coming after the
> console is established) connects back to **your own console** to access its processing
> power, your saved states, your patterns, and your biometric baselines.

```
Away from home
┌─────────────────────┐         Internet          ┌────────────────────────┐
│  BEA_Beatbox App    │ ◄──── your console ──────► │  BEA Aura Console      │
│  (iOS / Android)    │        not Big Tech        │  at home               │
│                     │                            │  ├── BEA_Beatbox       │
│  Thin client:       │                            │  ├── BEA_4D_Audio      │
│  UI + mic input     │                            │  ├── BEA_Health data   │
│  + pattern display  │                            │  └── BEA_Shield VPN    │
└─────────────────────┘                            └────────────────────────┘
```

You own the hardware. You own the processing. You own the data.
No monthly fee. No third-party cloud. Your console IS the cloud.

---

## Architecture

```
BEA_Beatbox/
├── __init__.py              # Public API — import from here
├── bea_logic.py             # BEA Logic™: Emergence (1⊕1=3) & Divergence (1⊕1≠3)
├── elemental_kits.py        # 6 elemental kits: Fire ⊕ / Water ⊖ / Air ⊗ / Solar ⨀ / Ether ≠ / Temporal ⧖
├── operator_effects.py      # 6 acoustic operators → AudioParams shaping
├── beatbox_scanner.py       # Vocal frequency → BEA state (extends BEAScanner)
├── pattern_engine.py        # 16-step drum pattern generation from E-states
├── emotion_engine.py        # EmotionBeatGenerator — core standalone API
├── beatbox_recognizer.py    # Sound classifier: KICK / SNARE / HAT / VOCAL_FX / …
├── integration.py           # Cross-project bridge (4D Audio, Speakerbox, Health, Shield)
├── demo_standalone.py       # Zero-dependency demonstration
└── tests/
    ├── __init__.py
    └── test_beatbox.py      # 80 unit tests
```

### Foundation — BEA_Aura_OS Imports

BEA_Beatbox imports directly from the BEA_Aura_OS root package:

| Imported From | What It Provides |
|---------------|-----------------|
| `scanner.BEAScanner` | S° Sound Degree, L° Lumen Degree, 32-state scanning |
| `bea_config.config` | Centralised environment configuration |
| `bea_logging.setup_logging` | Structured JSON-capable logging |

---

## Requirements

**Runtime:**
```
Python 3.8+
numpy >= 1.20.0
BEA_Aura_OS  (parent package — must be installed or on sys.path)
```

**Optional (for ecosystem integration):**
```
BEA_4D_Audio   — Spatial audio parameter routing
BEA_Speakerbox — Multi-channel output
BEA_Health     — Biometric state input (HRV → BEU, heart rate → E°)
BEA_Shield     — Threat level → beat state mapping
```

All optional integrations degrade gracefully — BEA_Beatbox operates fully standalone
when ecosystem components are unavailable.

---

## Quick Start

### Standalone Beat Generation

```python
from BEA_Beatbox import EmotionBeatGenerator

gen = EmotionBeatGenerator()

# Generate beat parameters from BEA state + intensity
state = gen.update_emotional_state(beu=11, e_degree=85.0)
print(state.summary)
# → E[11] Solar ⨀ | 128 BPM (Allegretto) | Filter 6850 Hz | Vol -1.6 dBFS | Kit: Solar | Complexity 0.55

# Get the 16-step drum pattern
pattern = gen.get_pattern_for_state(state)
print(pattern.ascii_grid())
#   KICK         │ █···█···█···█··· │
#   SNARE        │ ····█·······█··· │
#   HAT CLOSED   │ █·█·█·█·█·█·█·█· │
#   HAT OPEN     │ ·······█·······█ │
```

### Vocal Sound Recognition

```python
from BEA_Beatbox import BeatboxRecognizer

recognizer = BeatboxRecognizer()

# Classify a kick drum hit (75 Hz, high amplitude)
result = recognizer.recognize(freq_hz=75.0, amplitude=0.85, spectral_centroid=150.0)
print(result.summary)
# → Kick (sub-bass)      E[ 2] ⊖  S°= -31.8°  conf=0.69  f=75Hz
```

### BEA Logic™ — Creative Emergence

```python
from BEA_Beatbox import bea_logic_result, detect_emergence

# Test if two BEA states produce emergence (1 ⊕ 1 = 3)
result = bea_logic_result(5, 10)
print(result.description)
# → 1 ⊕ 1 = 3 — Emergence! E[5] ⊕ E[10] → E[15] (2 new bit(s) activated, transcendence achieved)

# Chain multiple states
from BEA_Beatbox import bea_logic_chain
chain = bea_logic_chain(3, 12, 7)
print(f"Final: E[{chain.combined_state}]  Type: {chain.result_type}")
```

### Emotional Journey

```python
gen = EmotionBeatGenerator()

# Generate all 32 states at E° = 75 (high intensity)
journey = gen.journey(start_beu=0, end_beu=31, e_degree=75.0)

for state in journey:
    pattern = gen.get_pattern_for_state(state)
    print(f"{state.state_label}  {state.bpm:.0f} BPM  density={pattern.hit_density:.2f}")
# → E[0] Fire ⊕   81 BPM  density=0.31
# → E[1] Fire ⊕   85 BPM  density=0.34
# → ...
# → E[31] Solar ⨀  203 BPM  density=0.62
```

### Health-Driven Beats (BEA_Health Integration)

```python
from BEA_Beatbox import BeatboxBridge

bridge = BeatboxBridge()

# Drive beats from biometric data
state = bridge.from_health_state(
    hrv_ms=45.0,           # Current HRV (below baseline = stress)
    heart_rate_bpm=92.0,   # Elevated HR = high E°
    baseline_hrv=55.0,
    resting_hr=62.0,
)
print(state.summary)
# Beat character reflects physiological state
```

---

## Core Concepts

### BEA E-motion States (E[0..31])

Every beatbox sound maps to one of 32 binary states via 5-bit encoding:

```
Bit: [4][3][2][1][0]
      │  │  │  │  └─ Intensity   (0=low amplitude, 1=high impact)
      │  │  │  └──── Frequency   (0=low F0/bass, 1=high F0/treble)
      │  │  └─────── Phase       (0=leading transient, 1=lagging decay)
      │  └────────── Coherence   (0=isolated hit, 1=rhythmically synced)
      └───────────── Latency     (0=realtime <16ms, 1=buffered)
```

**Beatbox frequency fingerprints:**

| Sound | Frequency Range | Typical BEA State |
|-------|-----------------|-------------------|
| Kick | 50–120 Hz | E[0..3] |
| Bass Tone | 80–260 Hz | E[2..5] |
| Snare | 150–450 Hz | E[4..7] |
| Vocal FX | 300–2500 Hz | E[8..13] |
| Hi-Hat Closed | 5–11 kHz | E[14..17] |
| Hi-Hat Open | 7–14 kHz | E[16..19] |
| Scratch | 150–9000 Hz | E[20..23] |
| Breath | 20–100 Hz | E[0..1] |

### Six BEA Operators — Elemental Kit Mapping

Each operator maps to a distinct percussive character:

| Kit | Operator | Percussive Character |
|-----|----------|----------------------|
| Fire | ⊕ Combust | Sharp transient attack, kick impact, high-energy ignition |
| Water | ⊖ Balance | Snare body warmth, resonant sustain, groove equilibrium |
| Air | ⊗ Dissolve | Cymbal decay, hi-hat breathiness, diffuse tail release |
| Solar | ⨀ Amplify | Full kit projection, peak amplitude, maximum drive |
| Ether | ≠ Divergence | Polyrhythm contrast, syncopation, pattern expectation break |
| Temporal | ⧖ Resonate | Groove lock, cadence alignment, metronomic consistency |

### BEA Logic™

```
1 ⊕ 1 = 3   (Emergence)   — Combined state has MORE active bits than either input
1 ⊕ 1 ≠ 3   (Divergence)  — States share no resonance, tension holds potential
```

Emergence is a deterministic bitwise test — not a metaphor:

```python
def bea_logic_emerged(a_state: int, b_state: int) -> bool:
    combined = combust(a_state, b_state)  # bitwise operation on 5-bit states
    return popcount(combined) > max(popcount(a_state), popcount(b_state))
    # True = new bit complexity created — emergence confirmed
```

Two states combine via `combust`. If the result activates more bits than either
input alone, emergence has occurred: the combination created a new signal property
that neither state possessed independently. This is the computational definition of
`1 ⊕ 1 = 3`.

### Six Elemental Kits

All 15 operator combination effects produce emergent kit blends:

| Combo | Kit Blend Name | Percussive Character |
|-------|---------------|----------------------|
| ⊕+⊖ | Groove | Punchy warmth — driven yet balanced |
| ⊕+⊗ | Snap | Sharp breathiness — tight attack with air |
| ⊕+⨀ | Blast | Maximum impact — full ignition at peak |
| ⊕+≠ | Flam | Ignited syncopation — accentuated contrast |
| ⊕+⧖ | Downbeat | Locked punch — metronomic attack |
| ⊖+⊗ | Brush | Warm decay — smooth diffuse tail |
| ⊖+⨀ | Thump | Full body warmth — deep resonant power |
| ⊖+≠ | Backbeat | Warm contrast — snare syncopation |
| ⊖+⧖ | Pocket | Groove lock — consistent warm cadence |
| ⊗+⨀ | Wash | Expansive cymbal — airy projection |
| ⊗+≠ | Ghost | Hushed contrast — soft syncopated air |
| ⊗+⧖ | Tick | Timed breath — paced hi-hat intimacy |
| ⨀+≠ | Crash | Powerful contrast — peak syncopation |
| ⨀+⧖ | Drive | Grounded power — locked full-spectrum |
| ≠+⧖ | Shuffle | Rhythmic divergence — timed expectation break |

---

## Running the Demo

```bash
# From BEA_Aura_OS root directory:
python -X utf8 BEA_Beatbox/demo_standalone.py
```

The demo runs six sections entirely standalone — no servers, no external components:
1. Emotional Beat Journey (E[0] → E[31])
2. BEA Logic™ Emergence & Divergence examples
3. All six elemental kits across E° temperatures
4. Beatbox sound recognition (frequency → category)
5. 16-step ASCII pattern display for key states
6. All 15 operator combination emergent effects

---

## Running Tests

```bash
# From BEA_Aura_OS root directory:
python -m pytest BEA_Beatbox/tests/test_beatbox.py -v
```

**80 tests** covering all modules:

| Test Class | Tests | Covers |
|-----------|-------|--------|
| `TestBEALogic` | 10 | combust, emergence, divergence, chain |
| `TestElementalKits` | 9 | all 4 kits, E° scaling, BEU mapping |
| `TestOperatorEffects` | 10 | all 6 operators, combos, AudioParams |
| `TestBeatboxScanner` | 10 | vocal scan, S°, frequency ranges |
| `TestPatternEngine` | 9 | 16-step patterns, density, grid display |
| `TestEmotionEngine` | 13 | BPM/filter/volume, journey, caching |
| `TestBeatboxRecognizer` | 9 | kick/hat/vocal classification |
| `TestIntegration` | 10 | HRV→BEU, threat→BEU, JSON bridge |

---

## API Reference

### `EmotionBeatGenerator`

```python
class EmotionBeatGenerator:
    def update_emotional_state(beu: int, e_degree: float) -> EmotionState
    def get_pattern_for_state(state: EmotionState) -> DrumPattern
    def journey(start_beu, end_beu, e_degree) -> list[EmotionState]
    def kit_params_for_state(state: EmotionState) -> KitParams
```

### `BeatboxRecognizer`

```python
class BeatboxRecognizer:
    def recognize(freq_hz, amplitude, spectral_centroid, latency_ms) -> RecognitionResult
    def recognize_sequence(sounds: list[tuple]) -> list[RecognitionResult]
```

### `BeatboxScanner`

```python
class BeatboxScanner(BEAScanner):
    def scan_beatbox_sound(frequency_hz, amplitude, latency_ms) -> BeatboxScanResult
    def scan_pattern(sounds: list[tuple]) -> list[BeatboxScanResult]
    def classify_sound(frequency_hz, amplitude) -> tuple[BeatboxSound, float]
```

### `PatternEngine`

```python
class PatternEngine:
    def get_pattern(beu: int, e_degree: float) -> DrumPattern
    def get_transition(beu_from, beu_to, e_degree, steps) -> list[DrumPattern]
```

### `BeatboxBridge`

```python
class BeatboxBridge:
    def to_4d_audio_params(state, position) -> AudioBridgeParams
    def to_speakerbox_message(state, pattern, event) -> str  # JSON
    def from_health_state(hrv_ms, heart_rate_bpm, ...) -> EmotionState
    def from_shield_state(threat_score, e_degree) -> EmotionState
    def full_pipeline(beu, e_degree, position) -> dict
```

### BEA Logic™

```python
combust(a, b) -> int                          # ⊕ Combust operator
detect_emergence(state_a, state_b) -> bool    # 1⊕1=3 check
detect_divergence(state_a, state_b) -> bool   # 1⊕1≠3 check
bea_logic_result(state_a, state_b) -> BEALogicResult
bea_logic_chain(*states) -> BEALogicResult    # Multi-state chain
```

---

## Future Development

### Phase 1 — Now (Current)
This SDK is the **console-side engine**. It runs on your BEA Aura Console and exposes
beat generation, pattern data, and vocal recognition over the local BEA ecosystem
(BEA_4D_Audio, BEA_Speakerbox, BEA_Health). All 80 tests pass. The foundation is solid.

### Phase 2 — BEA Aura Console Established
Once BEA Aura Console hardware ships and the platform is live:

- **Console API server** — BEA_Beatbox exposes a local network API so the mobile app
  can request states, patterns, and real-time recognition results from your console
- **Remote access via BEA_Shield VPN** — Secure tunnel from your phone back to your
  console when you're away from home. No third-party relay — direct console connection
- **Biometric sync** — BEA_Health data on your console feeds the app's beat generation
  in real time (your HRV drives your beats, locally processed on your hardware)
- **MIDI Export** — Convert 16-step `DrumPattern` objects to MIDI files for DAW use

### Phase 3 — BEA_Beatbox App
The **BEA_Beatbox mobile app** (iOS / Android) is a thin client that connects to your
home console:

- Mic input → sends audio to console for vocal recognition (processing stays on your hardware)
- Beat parameters ← streamed back from console in real time
- Pattern display, elemental kit selector, BEA Logic™ visualiser
- Works offline with cached last-known state when console is unreachable
- No subscription. No cloud account. Your console is the server.

> This app will be developed as a separate repository after the BEA Aura Console
> platform is established. The SDK built here is the backend it will connect to.

### Additional Roadmap Items
- **Live Performance Mode** — Low-latency vocal recognition with real-time pattern switching
- **BEA_Beatbox IoT** — Smart speaker integration (BEA_Speakerbox hardware)
- **Multi-user Collaboration** — BEA Logic™ emergence detection across performers in the same space

All future applications will connect to the BEA Aura Console. The console is the cloud.

---

## License

```
MIT License — Open Source Core
Patent Pending — BEA_Beatbox™ core technologies
Copyright © 2025 Jeremy F. Jackson d/b/a BEATEK Holdings, LLC
```

See [LICENSE](LICENSE) for complete terms.

Commercial use of patent-pending technologies requires licensing.
Contact: jeremyjackson7@proton.me

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

We welcome contributions to:
- Sound fingerprint accuracy improvements
- Additional beatbox sound categories
- Pattern template additions
- Platform-specific optimisations

---

## Contact & Licensing

**Jeremy F. Jackson d/b/a BEATEK Holdings, LLC**

- Commercial licensing: jeremyjackson7@proton.me
- Bug reports: [GitHub Issues](https://github.com/Beat-k/BEA_Aura_OS/issues)
- Subject line: `BEA_Beatbox — [Topic]`

---

*BEA_Beatbox is part of the BEA Aura Console — One device. Four pillars. Zero subscriptions.*
*Power to the People ⚡*
