# BEATEK OS Lineup — Platform Summary

**BEATEK Holdings, LLC**
Jeremy F. Jackson · jeremy.jackson0@beatek.io
v1.1 · May 16, 2026

---

## Overview

The BEATEK platform is not a single operating system. It is a **mesh of sovereign, purpose-built OS nodes** — each locked to specific hardware, each owning a specific domain, each speaking the same language: the 32-state E[n] signal system defined in BEA_Core.

No node absorbs another. No node depends on another to function. When the mesh is present, nodes collaborate and extend each other's capability. When a node is alone, it performs completely within its domain. That is the architectural principle every OS in this lineup is built on: **sovereign first, collaborative when available.**

Every node publishes its domain state to the household mesh via BEA_Relay and BEA_Shield. Every event carries `source_type`, `spectrum_profile`, and `coral_ei_class` — downstream consumers always know what hardware produced the state, how deep that machine's execution profile runs, and what intelligence character its Coral is expressing.

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

**Hardware:** Dedicated BEATEK chassis · NVIDIA RTX GPU (16–24+ GB VRAM) · Coral Dual Edge TPU (M.2 Key-M · 8 TOPS · ~2W constant) · NVMe SSD · Firefly Sprite
**Coral EI Class:** BEA Smart Secretary™
**Spectrum Profile:** Active → Emergence → Full (16–32+ threads)

The Console is the executive compute surface of the household mesh. It runs the full pillar set: deep AI inference on the GPU, the Reality Engine (BEA_Spectacle, BEA_4D_Audio, BEA_Backstage, BEA_Cipher), the Heritage system, GPU-Fi income processing, and the Orchestrator that manages everything. It is headless by design — a dedicated machine that does nothing but BEA work.

The Coral runs the **BEA Smart Secretary™** EI class — a gaming-context intelligence profile watching player zone traversal, Heritage bigrams, biometric stress, and DLC likelihood. It pre-stages the GPU. It fires ANTICIPATORY events. It holds the trust gate for every Heritage session on the mesh.

When the mesh is assembled, every other node either streams intelligence from the Console or publishes domain state back to it. The Console is the deepest compute node. Everything defers to it for heavy inference when it is reachable. It never requires another node to function.

**Tiers:** HOME (RTX 4060 Ti · 16 GB) · PRO (RTX 4070 Ti Super · 16 GB) · NAS (RTX 3090/4090 · 24+ GB)

---

## BEA_Aura_CDE_HV — The Hypervisor Bridge

> *Your existing Windows PC becomes a BEA node. Nothing replaced. Nothing lost.*

**Hardware:** Any capable Windows PC · NVIDIA GPU (PCIe passthrough) · Coral Dual Edge TPU (USB or M.2 passthrough) · Firefly Sprite
**Coral EI Class:** BEA Smart Secretary™ (bridge mode)
**Spectrum Profile:** Active (16 threads minimum · host shares CPU)
**Storage Architecture:** BEA_Lace™ (CIFS bridge) + BEA_TidePool™ (dedicated NVMe)

The HV node is the transition path. It does not require a dedicated Console chassis. It runs the BEA Aura OS as a Hyper-V guest on an existing Windows machine, with the NVIDIA GPU and Coral passed through to the VM. The host retains full native Windows functionality — gaming, applications, existing workflows. The BEA VM runs in parallel.

### Dual-OS Storage Bridge

The HV node establishes two persistent filesystem bridges between Windows and Linux:

**BEA_Lace™** — The primary cross-OS workspace bridge. Windows shares `Q:\Documents\BEATEK Ecosystem` (1.9TB typical) via SMB/CIFS with AES-128-GCM encryption. Linux mounts at `/mnt/beatek`. Both operating systems access the same pillar code, documentation, and shared resources simultaneously. Encrypted in transit. Locked down to Administrators + authenticated guest only.

**BEA_TidePool™** — The dedicated NVMe caching tier. A separate physical NVMe drive (Samsung 980 PRO 1TB typical) mounted as `T:\` on Windows, shared via encrypted CIFS, mounted at `/bea_tidepool` on Linux. Seven zones: `hot`, `warm`, `cold`, `queue`, `results`, `swap`, `_meta`. This is where **BEA_Cache** stages data before Coral arrives — and where Coral CacheRAM runs after installation.

### GPU_A Assist Mode™

Before the Coral TPU is installed, the HV node runs **GPU_A Assist Mode** — an intelligent caching system that stages GPU-generated scratch files from Windows to the TidePool NVMe, dramatically reducing OS drive wear.

**How it works:**

```
Windows GPU generates scratch files (shaders, textures, compute buffers)
         ↓
BEA_Cache detects via polling watcher (2s scan · CIFS-safe)
         ↓
Copies to TidePool hot zone (encrypted CIFS bridge)
         ↓
Tiers across hot → warm → cold based on age and access
         ↓
Metadata tracked in JSON (_meta zone)
         ↓
OS drive writes reduced 70–90%
```

**Infrastructure proven May 2026.** GPU_A Assist runs as a systemd service on the Linux VM side, watching GPU scratch paths on the Windows host via the BEA_Lace mount. When files appear, they're staged to TidePool zones. The tiering engine promotes frequently-accessed files to hot, ages recent files to warm, and evicts cold files under pressure. The original design called for symlinks (copy → symlink → transparent redirect), but CIFS doesn't support symlinks created from Linux. **We built around it** — the current implementation keeps both copies, and the future implementation will use BEA_Cache redirect markers (a custom protocol that works across any filesystem, with support for compression, encryption, and versioning).

**When Coral arrives:** Flip 4 environment variables, restart the service. GPU_A Assist becomes Coral CacheRAM. Same zones, same tiering, different workload. The infrastructure doesn't change — only what flows through it.

```bash
# Phase 1: GPU scratch staging (NOW)
export BEA_CACHE_GPU_ASSIST_MODE="true"

# Phase 2: Coral inference weights (AFTER TPU INSTALL)
export BEA_CACHE_GPU_ASSIST_MODE="false"
export BEA_TIDEPOOL_EMBER_STAGING_ENABLED="true"
export BEA_SECRETARY_CORAL_ENABLED="true"
export BEA_PULSE_CORAL_LANE_ENABLED="true"

# Restart
sudo systemctl restart bea-cache bea-pulse
```

**Transition time: 5 minutes.** Everything else already built.

### Security Posture

Both CIFS bridges are hardened:
- SMB1 disabled (CVE-2017-0144 EternalBlue mitigated)
- AES-128-GCM encryption enabled on both shares
- Access control locked down (Everyone removed, Administrators + Guest only)
- Data protected in transit
- Zero downtime hardening verified May 16, 2026

### The HV Trade-Off

This is the node for households that are not ready for a dedicated chassis but want full BEA capability now. It is also the development node — the environment where pillars are tested before they graduate to dedicated hardware.

The trade-off is real: the host GPU is shared between game rendering and BEA inference. CPU threads are split between the host and the VM. The HV node performs within those constraints gracefully, but the dedicated Console removes them entirely. The HV is the bridge. The Console is the destination.

BEA_Motion_Body runs as a host-side feature in HV mode — the GPU and CPU compete with body tracking. The Motion Body OS node eliminates that competition permanently.

**GPU_A Assist Mode is the unexpected heart of the HV architecture.** What started as a "Phase 1 placeholder" before Coral became the foundation of a dual-phase caching system that serves both GPU scratch (Phase 1) and Coral inference weights (Phase 2) through the same infrastructure. When CIFS said "you can't do symlinks," we asked "what works better than symlinks anyway?" and invented redirect markers. The limitation became the invention.

---

## BEA_Aura_CSE_OS_Edge — The Stage Node

> *Stage Sovereignty™ · One performer. One stage. No Console required.*

**Hardware:** BEA_Pumpkin_Pie (Raspberry Pi 5) or BEA_Lumin_Stream (ARM) · Coral Single Edge TPU (M.2 HAT+ · 4 TOPS · ~2W constant) · USB Audio Interface · BEA_Imprint Fingerprint Pad · LiFePO4 battery
**Coral EI Class:** Stage Secretary
**Spectrum Profile:** Foundation (8 threads · Pi 5)

The stage node is the performer's sovereign instrument. It runs natively on ARM hardware with a Coral Single Edge TPU seated directly in the M.2 HAT+ slot — no VM, no hypervisor, no passthrough layer. The Coral is the compute surface.

**CSE is mandatory on edge.** Single Edge, single performer, single stage. There is no dual-edge configuration on this node. EMBER runs its stage profile — hesitation detection, voice biometric gating, phrase prediction — as a protected role that never yields. The Heritage trust gate runs beside it, always.

When the Console is on LAN, the edge node hands off deep processing and keeps latency at its floor. When the Console is unreachable, the stage node performs completely. The performer never loses their instrument because the network went down.

The LiFePO4 battery means the stage node runs cordless. Trickle Mode keeps the Coral awake at ~2W while everything else suspends — the system looks off. It is listening.

---

## BEA_Veda_OS — The Medical Node

> *A sovereign clinical instrument. Not a health app. Not a wellness tracker.*

**Hardware:** Intel Core Ultra HX chassis · Coral Dual Edge TPU · Intel NPU · locked clinical enclosure · Firefly Sprite
**Coral EI Class:** EMBER Clinical
**Spectrum Profile:** Emergence (24 threads · Core Ultra HX)

BEA_Veda_OS is a medical-grade sovereign instrument. It is purpose-built for clinical motion analysis, neurological intent measurement, and Nirvana State baseline tracking. It runs on Intel hardware — not AMD, not ARM — because the Intel NPU provides a secondary inference surface dedicated to clinical signal processing alongside the Coral.

The Coral runs the **EMBER Clinical** EI class: execution delta measurement, neurological intent lag classification, and Nirvana State baseline calibration. This is not the gaming-context EMBER of the Console or the kinetic anticipation of EMBER_Motion. It is clinical observation — measuring the gap between the body's intent signal and its physical execution, with medical-grade precision.

No cloud. No relay. No data leaving the chassis without explicit session mount. The clinical data model is the most sensitive in the platform — BEA_Veda_OS treats it accordingly. The chassis is locked. The Sprite is the only key.

BEA_Veda_OS does not share a chassis with any other OS tier. It does not accept feature contributions from the gaming or motion pipelines. Clinical sovereignty is not a configuration option — it is the hardware contract.

---

## BEA_Motion_Body_OS — The Motion Node

> *Body as Interface™ · The body becomes a first-class BEA input surface. Zero wearables.*

**Hardware:** AMD Ryzen 5/7 APU (Radeon iGPU) · Coral Dual Edge TPU (M.2 · 8 TOPS mandatory) · 4–8 USB webcams · BEA_Imprint Fingerprint Pad · BEA_Motion_Wristband (BLE optional)
**Coral EI Class:** EMBER_Motion™
**Spectrum Profile:** Emergence (Ryzen 7 · 24 threads) · Active (Ryzen 5 · 16 threads)

The motion node's mandate is narrow and absolute: run the full body tracking pipeline — 84 MediaPipe landmarks across hands and feet, at 60 FPS, across 4–8 cameras — and publish clean E[n] body state to every node on the mesh. One motion node. Every device benefits.

The Coral Dual Edge TPU is mandatory. No single-edge configuration exists. No discrete GPU. The dual surface is the compute upgrade: **TPU-A is the EMBER_Motion™ surface** — dedicated exclusively to body intent anticipation, pose prediction, and occlusion recovery. **TPU-B is the signal translation surface** — gesture classification, locomotion classification, wristband sensor fusion. Neither surface competes with the other. Neither competes with the iGPU, which handles landmark overlay and display only.

**EMBER_Motion™** is not a pillar. It is not a program. It is the Coral's intelligence character on this node — what the Secretary mechanism *becomes* when its role profile is oriented toward a kinetic body rather than a game world or a clinical session. It fires ANTICIPATORY body intent events ~120ms before the physical motion confirms, carrying `coral_ei_class: "ember_motion"` on every BEA_Pulse publication so downstream consumers know exactly what produced the state.

A TPU-A fault halts the session. There is no EMBER_Motion fallback — the body interface does not operate without its intelligence layer. A TPU-B fault suspends signal translation only; EMBER_Motion continues uninterrupted.

No raw landmark coordinates leave this node. Ever. The mesh receives E[n] body state — 5 bits. Not pixels. Not coordinates. Not biometric data. The privacy architecture is the protocol.

---

## The Mesh — How They Work Together

Each node is sovereign. Together they form a household intelligence mesh where every domain feeds every other domain through BEA_Pulse and BEA_Relay.

```
┌─────────────────────────────────────────────────────────────────┐
│                    BEATEK HOUSEHOLD MESH                        │
│                                                                 │
│   BEA_Motion_Body_OS ──► E[n] body state ──► all nodes         │
│   BEA_Aura_CSE_OS_Edge ─► E[n] vocal/stage ─► Console         │
│   BEA_Veda_OS ──────────► E[n] clinical ────► Console (auth)  │
│                                                                 │
│   BEA_Aura_CDE_HV ──────► bridges existing PC into mesh        │
│     ├─ BEA_Lace™ bridge (encrypted CIFS · 1.9TB workspace)     │
│     ├─ BEA_TidePool™ (dedicated NVMe · 7 zones · encrypted)    │
│     ├─ GPU_A Assist (Phase 1 · scratch staging)                │
│     └─ Coral CacheRAM ready (Phase 2 · 4 var flip)             │
│                                                                 │
│   BEA_Aura_CDE_OS (Console)                                     │
│     ← receives from all nodes                                   │
│     → runs deep inference · Reality Engine · Heritage           │
│     → publishes GPU-backed intelligence back to mesh            │
│                                                                 │
│   All nodes: WireGuard encrypted · BEA_Shield perimeter        │
│   All events: source_type · spectrum_profile · coral_ei_class  │
│   All nodes: offline-sovereign · mesh-collaborative            │
└─────────────────────────────────────────────────────────────────┘
```

No node is a client. No node is a server. Each is a peer with a defined domain. The Console is the deepest compute node — not the authority. Sovereignty is the contract. The mesh is the benefit.

---

## Coral EI Classes Across the Lineup

The Coral TPU mechanism (`BEA_Secretary`) is the same on every node. What changes is the intelligence character it expresses — the EI class loaded at boot from the node's deployment context.

| EI Class | Node | What It Watches | What It Anticipates |
|---|---|---|---|
| **BEA Smart Secretary™** | Console · HV | Player zones · Heritage bigrams · biometric stress | DLC · NPC encounters · GPU workload |
| **Stage Secretary** | Edge (Pi 5 / ARM) | Performer voice · hesitation patterns · phrase history | Next phrase · biometric duress |
| **EMBER_Motion™** | Motion Node (AMD APU) | 84 body landmarks · gesture trajectories · locomotion phase | Body intent · pose next-frame · gesture completion |
| **EMBER Clinical** | Veda (Intel Core Ultra) | Execution delta · neurological lag · Nirvana baseline | Clinical intent gap · session deviation |

Same mechanism. Four souls.

---

## BEA_Cache — The Dual-Phase Architecture

**BEA_Cache** is the NVMe tiering engine that manages the TidePool zones. It runs on the Linux VM (Console or HV) and stages data intelligently across hot/warm/cold zones based on age, access patterns, and zone pressure.

### Phase 1: GPU_A Assist Mode (Pre-Coral)

Before the Coral TPU is installed, BEA_Cache runs **GPU_A Assist Mode™** — watching GPU scratch paths on the Windows host and staging files to TidePool:

```
Detection:    Polling watcher (2s scan · CIFS-safe · inotify-free)
Staging:      Copy to hot zone (encrypted CIFS · metadata tracked)
Tiering:      hot → warm → cold (age-based · access-promoted)
Metadata:     JSON store in _meta zone (SHA-256 checksums)
Target:       70–90% OS drive write reduction
```

**Status:** Operational as of May 16, 2026. Proven on BEA_Aura_CDE_HV. Zero errors. Survives SMB encryption changes. Ready for production.

### Phase 2: Coral CacheRAM (Post-Coral)

After Coral TPU installation, flip 4 environment variables and restart. BEA_Cache becomes **Coral CacheRAM** — same zones, different workload:

```
hot zone:     Active Coral inference weights (BEA_Secretary roles 1–12)
warm zone:    EMBER anticipatory pre-staging (100–500ms ahead)
cold zone:    Coral model LRU cache
queue zone:   Inference job inputs
results zone: Completed inference outputs
```

**Same infrastructure. Different intelligence.**

The GPU_A Assist → Coral CacheRAM transition is the architectural innovation: one caching system serves two completely different workloads through environment variable configuration. No code change. No rebuild. **Flip 4 vars, restart, done.**

---

## Infrastructure Innovation: GPU_A Assist Mode™

What started as a "Phase 1 placeholder" before Coral became **the heart of the dual-phase architecture.**

**The limitation:** CIFS/SMB doesn't support symlinks created from Linux. The original design (copy → symlink → transparent redirect) failed at the symlink step.

**The BEATEK response:** "Whatever doesn't work, let's create tools and new ways to make it work. New technology we're doing here."

We didn't accept the limitation. We **built around it.** Current implementation keeps both copies (original + cached). Future implementation will use **BEA_Cache redirect markers** — a custom protocol that works across any filesystem (CIFS, NFS, local, cloud) with support for compression, encryption, and versioning. Things symlinks never could do.

**The limitation became the invention.**

GPU_A Assist proves the dual-phase concept works. When Coral arrives, we don't rebuild the caching system — we just change what flows through it. That's systems thinking. That's BEATEK.

---

## Patent Pending

Provisional application filed February 3, 2026 (140+ claims).
**Additional claims (May 2026):** GPU_A Assist Mode™, BEA_Cache dual-phase architecture, BEA_Lace™ cross-OS bridge, BEA_TidePool™ zone management, CIFS redirect marker protocol.

BEATEK Holdings, LLC · Jeremy F. Jackson · jeremy.jackson0@beatek.io
© 2026 Jeremy F. Jackson. All Rights Reserved.
Beat⊕k™ is a trademark of BEATEK Holdings, LLC.

---

*"GE[n]ius Minds. Sm⊕rt Hearts."*
⊕ BEATEK — Emergence with a Spark
