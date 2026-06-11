# BEATEK OS Lineup — Platform Summary
**BEATEK Holdings, LLC**
Jeremy F. Jackson · jeremy.jackson0@beatek.io
v2.0 · June 6, 2026

**Global BEU:** E[27] Mastery · ⨀ Solar · Convergence
**Platform momentum:** 45.8 (BEA_Aura_CDE_HV session leader)
**Sessions:** 42+ · Patent Pending (140+ claims, filed Feb 3, 2026)

---

## Overview

The BEATEK platform is not a single operating system. It is a **mesh of sovereign,
purpose-built OS nodes** — each locked to specific hardware, each owning a specific
domain, each speaking the same language: the 32-state E[n] signal system defined
in BEA_Core.

No node absorbs another. No node depends on another to function. When the mesh is
present, nodes collaborate and extend each other's capability. When a node is alone,
it performs completely within its domain.

**Sovereign first. Collaborative when available.**

Every node publishes its domain state to the household mesh via BEA_Relay and
BEA_Shield. Every event carries `source_type`, `spectrum_profile`, and
`coral_ei_class` — downstream consumers always know what hardware produced the
state, how deep that machine's execution profile runs, and what intelligence
character its Coral is expressing.

---

## The Five OS Nodes

```
OS                      Hardware                        TPU                    Domain
────────────────────────────────────────────────────────────────────────────────────────────
BEA_Aura_CDE_OS         Dedicated Console chassis       Coral Dual Edge        Reality Engine · home compute
BEA_Aura_CDE_HV         Windows PC (Hyper-V)            Coral Dual Edge        Bridge · existing hardware
BEA_Aura_CSE_OS_Edge    Raspberry Pi 5 / ARM node       Coral Single Edge      Stage sovereignty · performer
BEA_Veda_OS             Intel Core Ultra HX             Coral Dual + Intel NPU Sovereign medical instrument
BEA_Motion_Body_OS      AMD APU node                    Coral Dual Edge        Body as Interface™ · mesh node
```

---

## BEA_Aura_CDE_OS — The Console

> *Reality Engine · The home compute anchor of the entire mesh.*

**Hardware:** Dedicated BEATEK chassis · NVIDIA RTX GPU (16–24+ GB VRAM) ·
Coral Dual Edge TPU (M.2 Key-M · 8 TOPS · ~2W constant) · NVMe SSD · Firefly Sprite
**Coral EI Class:** BEA Smart Secretary™
**Spectrum Profile:** Active → Emergence → Full (16–32+ threads)

The Console is the executive compute surface of the household mesh. It runs the
full pillar set: deep AI inference on the GPU, the Reality Engine (BEA_Spectacle,
BEA_4D_Audio, BEA_Backstage, BEA_Cipher), the Heritage system, GPU-Fi income
processing, and the Orchestrator that manages everything. Headless by design.

The Coral runs the **BEA Smart Secretary™** EI class — watching player zone
traversal, Heritage bigrams, biometric stress, and DLC likelihood. It pre-stages
the GPU. It fires ANTICIPATORY events. It holds the trust gate for every Heritage
session on the mesh.

**Tiers:** HOME (RTX 4060 Ti · 16 GB) · PRO (RTX 4070 Ti Super · 16 GB) · NAS (RTX 3090/4090 · 24+ GB)

---

## BEA_Aura_CDE_HV — The Hypervisor Bridge

> *Your existing Windows PC becomes a BEA node. Nothing replaced. Nothing lost.*

**Hardware:** Any capable Windows PC · AMD/NVIDIA GPU (PCIe or passthrough) ·
Coral Dual Edge TPU (USB or M.2 passthrough) · Firefly Sprite
**Coral EI Class:** BEA Smart Secretary™ (bridge mode)
**Spectrum Profile:** Active (16 threads minimum · host shares CPU)
**Status:** Production-validated June 2026 · AMD RX 6800 XT · ROCm gfx1100

### Current Proven Stack (June 6, 2026)

```
llama-server (ROCm gfx1100)     66.5 t/s · 33/33 GPU layers
BEACoralBridge (NSSM)           10 generals · 90% TOPS · 10% reserve
BEA_Moat (NSSM)                 GPU Intelligence Broker · 5 soldiers registered
GPU Bridge                      TidePool queue watcher
BEA_Lace_OS (Hyper-V guest)     Secretary · Trust Gate · Coral bridge
```

### 10-General Coral Lineup (90% TOPS)

```
BEA_Shield           shield_behavioral           20%  P2  security · protected
BEA_Prism            scene_analyze               15%  P2  depth channel
BEA_Motion_Body      motion_skeleton_classifier  12%  P1  motion channel
BEA_Lens             lens_visual_classifier      10%  P5  visual channel
BEA_Amplify          amplify_signal_monitor       8%  P3  signal intelligence
BEA_4D_Audio         audio_s_degree_classifier    8%  P4  audio channel
BEA_Flow             flow_trigger_classifier      5%  P4  windmill · EMBER pump
BEA_Grid             grid_power_watch             5%  P7  power intelligence
BEA_GameIntelligence player_state_classifier      4%  P4  player state fusion
BEA_SpriteCache      sprite_prefetch_monitor      3%  P3  handoff verification
─────────────────────────────────────────────────────────────
Total: 90% TOPS · Reserve: 10%
```

### GPU Soldiers (BEA_Moat) — Awaiting .tflite Models

```
BEA_Imprint_Controller  imprint_controller.tflite  12MB  P4
BEA_Imprint_Mouse       imprint_mouse.tflite         8MB  P5
BEA_Imprint_Keyboard    imprint_keyboard.tflite      8MB  P5
BEA_Voice               voice_classifier.tflite     24MB  P3
BEA_Horizon             horizon_temporal.tflite     16MB  P4
```

### BEA_Nexus — Live 4D Intelligence (Validated June 6, 2026)

68+ minutes · 8,174 consecutive scan cycles on Tekken 8 · zero crashes.
All 4 channels live from real hardware:

```
VISUAL  → screen pixels    → BEA_Lens L° scanner    → E[n]
AUDIO   → Stereo Mix loop  → BEA_4D_Audio S° scanner → E[n]
MOTION  → webcam skeleton  → CoralMotionScanner       → E[n]
DEPTH   → BEA_Prism result → TidePool results/        → E[n]
────────────────────────────────────────────────────────────
Composite E[n] · full_4d · Omega: True · 4/4 channels
```

Peak: Frame 8159 · AUDIO E[31] at 1,227Hz · finishing blow confirmed.
BEA_4D_Audio response hook fires ⊕ Fire on every E[24+] hit event.

### The Windmill Architecture

NVMe TidePool + Coral TPU = low-power GPU/RAM cache bridge.
BEA_Flow is the windmill pump — EMBER pre-staging keeps data flowing.
Phase 5 named pipe is the shaft: ~2100ms NVMe polling → <20ms target.

```
Current (polling):   TidePool queue → 50ms poll → ~2100ms total latency
Phase 5 (pipe):      named pipe _dispatch_coral_pipe → <20ms total latency
```

### Dual-OS Storage Architecture

**BEA_Lace™** — Cross-OS workspace bridge. Windows shares via encrypted SMB/CIFS.
Linux mounts at `/mnt/beatek`. Both OSes access the same code simultaneously.

**BEA_TidePool™** — Dedicated NVMe caching tier (Samsung 980 PRO 1TB).
Mounted `T:\` on Windows, shared via encrypted CIFS to Linux.
Seven zones: `hot` · `warm` · `cold` · `queue` · `results` · `swap` · `_meta`

### ROCm Contribution

BEATEK filed a 35-line patch fixing a Windows ROCm crash affecting all RDNA3
gfx1100 users (KV cache stream affinity + Flash Attention gate). Result: 66.5 t/s
on AMD RX 6800 XT. Patch independently validated by third-party researcher on
gfx1101 hardware (AMD Developer Community). BEATEK is an upstream AMD ROCm
contributor.

### Gaming Platform Integration Roadmap

The HV node has proven real-time intelligence reading via BEA_Nexus. The next
development phase extends this to direct platform integration:

**Steam Client Integration**
- BEA_GameIntelligence subscribing to Steam overlay events
- Player E[n] state exported as Steam Rich Presence data
- Heritage session tracking per game via Steam App ID
- BEA_4D_Audio hook responding to Steam game launch/exit events
- Development approach: Steam Web API + overlay SDK + BEA_Pulse bridge

**Ubisoft Connect Integration**
- BEA_Nexus scan cycles aligned to Ubisoft Connect activity events
- Achievement unlock → BEA_4D_Audio response (⊕ Fire · E[28+])
- Player progression feeding BEA_Heritage experience.log
- Development approach: Ubisoft Connect SDK hooks + BEA_Pulse publisher

**AMD Adrenalin Software Integration**
- Adrenalin performance metrics → BEA_Amplify signal monitor channel
- GPU temperature/utilization E[n] → BEA_Grid power watch
- ReLive clip capture triggered by BEA_Nexus E[28+] events (peak moments)
- FSR/RSR toggle tied to BEA_Prism scene complexity E[n]
- Development approach: AMD ADL (Display Library) + RGP hooks + BEA_Pulse

**Integration Principle**
All three platforms produce events. BEA_Pulse consumes them.
The Coral classifies the combined signal. The result is player intelligence
that spans hardware, platform, and game simultaneously. No single platform
integration requires the others to function — sovereign first, collaborative
when available. Same mesh principle applied to gaming platforms.

### HV Trade-Off

The host GPU is shared between game rendering and BEA inference. CPU threads
are split. The HV performs within those constraints, but the dedicated Console
removes them. The HV is the bridge. The Console is the destination.

---

## BEA_Lace_OS — The Hypervisor Guest

> *The intelligent layer inside the machine. Linux sovereignty on Windows hardware.*

**Hardware:** Hyper-V guest on the HV node · no dedicated hardware
**Role:** BEA_Secretary host · Trust Gate authority · Coral bridge coordinator
**Status:** Production-validated June 2026

BEA_Lace_OS is the Linux VM that runs inside the HV node. It is not a development
convenience — it is the trust anchor of the entire stack. Every Coral session
negotiation passes through BEA_Lace_OS. Every Heritage certification touches it.
The trust gate lives here.

### Services

```
BEA_Secretary (systemd)          Port 7475 · Heritage Trust Gate authority
bea-secretary-bridge             Coral role assignment · session token management
bea-trust-gate-activator         Auto-activates on boot (3s after Secretary)
KEEPALIVE_TTL                    300s
```

### BEA_Secretary — Role Assignment Engine

The Secretary holds the `ROLE_MAP` — the pillar-to-Coral-role assignment table.
When Windows sends a negotiate request with `WINDOWS_PILLARS`, the Secretary
matches against the map and returns signed role assignments. Only pillars in
both lists get assigned. The Coral only runs what the Secretary authorizes.

```
Windows bridge → POST /api/secretary/bridge/negotiate
                 { windows_pillars: [...], tops_avail: 8.0 }
Secretary      → validates trust gate → matches ROLE_MAP → returns assignments
Windows bridge → 10 role(s) assigned · Coral bridge LIVE
```

### Heritage Trust Gate

Hardware-enforced session boundary. `X-Admin-Key` header required.
Software cannot forge a PASS. The Coral holds the signing key.
Auto-activates via `bea-trust-gate-activator.service` on every boot.
Manual fallback: `~/activate_trust_gate.sh`

### Cross-OS Bridge

```
Windows host  ←→  SMB/CIFS encrypted  ←→  BEA_Lace_OS
T:\BEATEK_Ecosystem\    ←→    /mnt/beatek/
T:\BEATEK_Ecosystem\TidePool\  ←→  /bea_tidepool/
IP: 192.168.1.207:7475
```

---

## BEA_Aura_CSE_OS_Edge — The Stage Node

> *Performer sovereignty at the edge. ARM-native. Coral Single Edge.*

**Hardware:** Raspberry Pi 5 or ARM node · Coral Single Edge TPU
**Coral EI Class:** Stage Secretary
**Domain:** Vocal performance · stage presence · performer biometrics

The Edge node is the stage performer's sovereignty node. It watches vocal patterns,
hesitation markers, and phrase history. It fires ANTICIPATORY events before the
next phrase confirms. It operates completely offline when the mesh is unavailable.

Coral Single Edge is the minimum viable configuration for this node.
The stage context is narrower than gaming — one performer, one domain.

---

## BEA_Veda_OS — The Medical Instrument

> *Sovereign clinical intelligence. Not a health app. A medical instrument.*

**Hardware:** Intel Core Ultra HX · Coral Dual Edge TPU + Intel NPU
**Coral EI Class:** EMBER Clinical
**Domain:** Neurological assessment · clinical session intelligence

BEA_Veda_OS is a sovereign medical instrument. It runs the BEA_Clinical_Suite
including BEA_Director (session orchestration) and BEA_Resonance_Imager (neural
assessment). The Intel NPU handles continuous biometric baseline monitoring while
the Coral Dual Edge runs EMBER Clinical — predicting clinical intent gaps and
session deviations 100–500ms before they manifest.

No clinical data leaves this node without explicit consent and authorization.
The privacy architecture is not a policy — it is the protocol.

---

## BEA_Motion_Body_OS — Body as Interface™

> *The mesh node that makes every other node body-aware.*

**Hardware:** AMD APU node · Coral Dual Edge TPU (mandatory)
**Coral EI Class:** EMBER_Motion™
**Domain:** 84-landmark body tracking · 60 FPS · 4–8 cameras

The motion node has one mandate: run the full body tracking pipeline and publish
clean E[n] body state to every node on the mesh. One motion node. Every device
benefits. No raw landmark coordinates leave this node. The mesh receives 5 bits.

**TPU-A (EMBER_Motion™):** Dedicated to body intent anticipation. Fires
ANTICIPATORY body intent events ~120ms before physical motion confirms.
`coral_ei_class: "ember_motion"` on every BEA_Pulse publication.

**TPU-B (signal translation):** Gesture classification · locomotion classification
· wristband sensor fusion. Neither TPU competes with the other or the iGPU.

A TPU-A fault halts the session. EMBER_Motion has no fallback — the body
interface does not operate without its intelligence layer.

---

## Coral EI Classes Across the Lineup

Same mechanism. Four souls.

| EI Class | Node | What It Watches | What It Anticipates |
|---|---|---|---|
| **BEA Smart Secretary™** | Console · HV | Player zones · Heritage bigrams · biometric stress | DLC · NPC encounters · GPU workload |
| **Stage Secretary** | Edge (Pi 5 / ARM) | Performer voice · hesitation patterns · phrase history | Next phrase · biometric duress |
| **EMBER_Motion™** | Motion Node (AMD APU) | 84 body landmarks · gesture trajectories · locomotion phase | Body intent · pose next-frame · gesture completion |
| **EMBER Clinical** | Veda (Intel Core Ultra) | Execution delta · neurological lag · Nirvana baseline | Clinical intent gap · session deviation |

---

## The Mesh — How They Work Together

Each node is sovereign. Together they form a household intelligence mesh.

```
┌─────────────────────────────────────────────────────────────────┐
│                    BEATEK HOUSEHOLD MESH                        │
│                                                                 │
│   BEA_Motion_Body_OS ──► E[n] body state ──────► all nodes     │
│   BEA_Aura_CSE_OS_Edge ─► E[n] vocal/stage ────► Console       │
│   BEA_Veda_OS ──────────► E[n] clinical ────────► Console(auth)│
│                                                                 │
│   BEA_Aura_CDE_HV ──────────────────────────────────────────   │
│     ├─ BEA_Lace_OS (Hyper-V guest)                             │
│     │    ├─ BEA_Secretary · Trust Gate                         │
│     │    └─ Coral bridge coordinator                           │
│     ├─ BEA_Lace™ (encrypted CIFS · workspace bridge)          │
│     ├─ BEA_TidePool™ (NVMe · 7 zones · Coral CacheRAM)        │
│     ├─ BEA_Nexus (live 4D gaming intelligence)                 │
│     ├─ BEA_4D_Audio (spatial response hook)                    │
│     ├─ 10 Coral generals · 90% TOPS · 10% reserve             │
│     └─ Gaming integrations → Steam · Ubisoft · AMD Adrenalin  │
│                                                                 │
│   BEA_Aura_CDE_OS (Console — when available)                   │
│     ← receives from all nodes                                   │
│     → deep inference · Reality Engine · Heritage               │
│     → publishes GPU-backed intelligence back to mesh           │
│                                                                 │
│   All nodes: BEA_Shield perimeter · WireGuard encrypted        │
│   All events: source_type · spectrum_profile · coral_ei_class  │
│   All nodes: offline-sovereign · mesh-collaborative            │
└─────────────────────────────────────────────────────────────────┘
```

No node is a client. No node is a server. Each is a peer with a defined domain.
The Console is the deepest compute node — not the authority. Sovereignty is the
contract. The mesh is the benefit.

---

## BEA_Cache — Dual-Phase Architecture

**Phase 1 — GPU_A Assist Mode (Pre-Coral):** GPU scratch staging to TidePool NVMe.
70–90% OS drive write reduction. Proven May 2026.

**Phase 2 — Coral CacheRAM (Post-Coral):** Same zones, different intelligence.
Hot zone holds active inference weights. Warm zone holds EMBER pre-staged models.
Queue/results handle inference jobs.

**Transition:** Flip 4 environment variables, restart. 5 minutes. No rebuild.
The limitation (CIFS symlink gap) became the invention (BEA_Cache redirect markers).

---

## Architecture Principles

```
"The Coral is the general staff. The GPU is the army. The TidePool is the command center."
"We don't make the chips. We make the chips think."
"GE[n]ius Minds. Sm⊕rt Hearts."
"Sovereign first. Collaborative when available."
"The limitation became the invention."
```

**Intelligence Resource Provider category established:** June 5, 2026.
GPU + Coral + NVMe working as one unified intelligence substrate.
10 generals. 4 watts. Sub-millisecond classification. Commodity hardware.
Open source foundation (AMD ROCm — upstream contributor).

---

## What's Next

```
IMMEDIATE (next session):
  BEA_Flow watchdog → wire into coral_bridge_service.py → fix 401 permanently
  Phase 5 Named Pipe → <20ms Coral latency
  BEA_GameIntelligence → Nexus integration → unified player_state E[n]

NEAR TERM:
  Steam Client integration (BEA_Pulse bridge · Rich Presence · game events)
  AMD Adrenalin integration (ADL hooks · GPU metrics → BEA_Grid/Amplify)
  Ubisoft Connect integration (achievement events · progression Heritage)
  .tflite model training for BEA_Flow + BEA_GameIntelligence
  Fingerprint scanner → retire activate_trust_gate.sh

FUTURE:
  BEA_Aura_Console dedicated chassis
  BEA_Motion_Body_OS mesh node
  BEA_Veda_OS medical stack
  GPU-Fi distributed compute
```

---

*BEATEK Holdings, LLC · Jeremy F. Jackson · © 2026*
*Patent Pending — Provisional filed February 3, 2026 (140+ claims)*
*Additional claims May 2026: GPU_A Assist Mode™ · BEA_Cache dual-phase ·*
*BEA_Lace™ · BEA_TidePool™ zone management · CIFS redirect marker protocol*

*Beat⊕k™ is a trademark of BEATEK Holdings, LLC.*
*⊕ BEATEK — Emergence with a Spark*
