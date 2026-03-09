# BEA_Aura_OS

> **Console as Cloud™ — The Operating System of the BEA Aura Console**

**Owner:** Jeremy F. Jackson · BEATEK Holdings, LLC
**Patent:** Provisional Filed February 3, 2026 — 111+ Claims
**License:** MIT (community) / Commercial (partners)
**GitHub:** [github.com/BEAT-K](https://github.com/BEAT-K)
**Tests:** 1,968 passing across 25 pillar modules

---

## What Is BEA_Aura_OS?

BEA_Aura_OS is the software foundation of the **BEA Aura Console** — a home computing platform that replaces cloud subscriptions with hardware you own. The OS coordinates four life pillars — Gaming, Security, Health, and Income — through a single mathematical language called **BEA™ (Binary E-motion Arithmetic)**.

Every pillar, every sensor, every data event runs through the same 32-state encoding framework. Audio frequencies, light wavelengths, GPU workloads, heart rate samples, network packets — all become a common language that allows cross-pillar intelligence impossible in single-purpose devices.

```
Traditional Cloud:                  Console as Cloud™:

  YOUR DATA ──────────────► AWS     YOUR DATA ──────► YOUR CONSOLE
  YOUR MONEY ─────────────► GOOGLE  YOUR MONEY stays  YOUR CONSOLE
  YOUR GPU TIME ──────────► AZURE   YOUR GPU TIME ──► YOUR EARNINGS
                                    THEIR MONEY ────► YOUR CONSOLE
```

---

## The BEA™ Framework

Everything in the ecosystem speaks the same mathematical language.

| Symbol | Name | Formula / Role |
|---|---|---|
| E[0]–E[31] | 32 Binary States | 5-bit encoding across all signal domains |
| S° | Sound Degree | `log₂(f_audio / 440 Hz) × 12` — maps frequency → state |
| L° | Lumen Degree | `(λ_visible / 555 nm) × 360°` — maps wavelength → state |
| E° | E-motion Temperature | 0–100 intensity scalar for any signal |
| ⊕ | Fire Operator | Amplification / constructive addition |
| ⊖ | Water Operator | Reduction / dissolution |
| ⊗ | Air Operator | Cross-domain resonance |
| ⨀ | Solar Operator | Radial broadcast |
| ≠ | Ether Operator | Divergence / contrast |
| ⧖ | Temporal Operator | Simultaneous resonance / sync delivery |

The 5-bit state encoding carries: **Intensity · Frequency · Phase · Coherence · Latency**

---

## The Four Pillars

### Gaming
*BEA Spectacle · BEA 4D Audio · BEA Motion Body*

Immersive gaming on monitors you already own. Not VR — better than flat. Parallax depth, spatial audio, and full-body webcam tracking for 350 million PC gamers who never bought a headset.

### Security
*BEA Shield*

GPU-accelerated network security running locally. 10 GB/s malware scanning vs 100 MB/s CPU. VPN, camera AI, parental controls, and zero subscription fees. Neighbor Security-as-a-Service on NAS tier: $20–40/month per household.

### Health
*BEA Health · Physiological Duress Detection*

Biometric sovereignty — heart rate, HRV, sleep, overtraining — from any wearable, stored with AES-256 encryption on your console. Your data never leaves your home. Cross-pillar **Physiological Duress Detection™**: involuntary stress triggers silent 911 dispatch, evidence saves, and coercion-aware vault behavior.

### Income
*GPU-Fi · GPU-Verse*

Idle GPU hours become passive income. GPU-Fi rents spare cycles to ML trainers ($200–500/month on Pro tier). GPU-Verse hosts virtual worlds, casinos, and arenas ($5k–20k/month on NAS tier). BEA_Grid and BEA_Ledger track power costs and handle 1099-K reporting automatically.

---

## Hardware Tiers

| | **Mini** | **Pro** | **NAS** |
|---|---|---|---|
| **Price** | $949 | $1,999 | $2,999 |
| **GPU** | RTX 5060 Ti 16GB | RTX 5070 Ti 16GB | RTX 5080 24GB |
| **CPU** | Ryzen 7 5700X | Ryzen 7 5700X | Ryzen 9 5950X |
| **RAM** | 32 GB DDR4 | 32 GB DDR4 | 64 GB DDR4 |
| **Storage** | 2 TB NVMe | 8 TB RAID 1 | 16 TB + hot-swap |
| **Network** | 2.5 GbE + WiFi 6 + 10 GbE SFP+ | same | Dual 10 GbE + IPMI |
| **GPU-Fi** | Home only | $200–500/mo | Coordination |
| **GPU-Verse** | Consumer | — | $5k–20k/mo |

Every tier includes: USB fingerprint reader · BEA Spectacle · BEA 4D Audio · BEA Motion Body · BEA Shield · BEA Health · Physiological Duress Detection

---

## Module Overview

### BEA_Core — Foundational Signal-Physics Layer
**163 tests | `BEA_Core/`**

The mathematical bedrock of the entire BEA ecosystem. All pillars depend on this module for signal encoding, operator definitions, and state scanning. Zero async — pure, deterministic computation.

Key files: `scanner.py` · `estates.py` · `operators.py` · `s_degree.py` · `l_degree.py`

- 32-state 5-bit encoding: Intensity · Frequency · Phase · Coherence · Latency
- `EState` IntEnum with all 32 named emotional states
- 6 pure BEA operators: ⊕ Fire · ⊖ Water · ⊗ Air · ⨀ Solar · ≠ Ether · ⧖ Temporal
- `S°` formula: maps audio frequency to BEA state
- `L°` formula: maps visible wavelength to BEA state
- `BEAScanner` base class: all pillar scanners subclass this

---

### BEA_Pulse — Inter-Pillar Event Bus
**44 tests | `BEA_Pulse/`**

The central nervous system of the OS. Every pillar publishes E-motion state transitions (E[n] → E[m]) to BEA_Pulse and subscribes to events from other pillars. Built on Python `asyncio` with optional Redis backend for multi-node NAS deployments.

Key files: `broker.py` · `event.py` · `publisher.py` · `subscriber.py` · `redis_backend.py`

- NORMAL / HIGH / CRITICAL priority levels — CRITICAL events (duress) are never dropped
- Six BEA operators tag the cause of every transition
- Native delivery is ⧖ Temporal (simultaneous resonance broadcast)

---

### BEA_Beatbox — Emotional Beat Generation & Recognition
**80 tests | `BEA_Beatbox/`**

32-state emotional beat synthesis, beatbox vocal classification, and drum pattern generation grounded in the BEA framework.

Key files: `emotion_engine.py` · `beatbox_scanner.py` · `beatbox_recognizer.py` · `pattern_engine.py` · `operator_effects.py` · `elemental_kits.py` · `bea_logic.py`

- Maps vocal sounds to E[0–31] via S° scanning
- BEA Logic™ Creative Mathematics: Emergence (1+1=3) and Divergence
- Elemental kits: Fire / Water / Air / Solar
- 6 BEA operator acoustic effects applied in real time

---

### BEA_Vault — Encrypted Personal Data Vault
**51 tests | `BEA_Vault/`**

AES-256-GCM on-device file vault for health records, financial data, and identity files. Never leaves your console.

Key files: `vault_core.py` · `vault_manager.py` · `vault_record.py` · `decoy_vault.py` · `vault_scanner.py` · `integration.py`

- File categories: HEALTH_RECORDS · FINANCIAL · EVIDENCE · USER_FILES · SECURITY_AUDIT
- Duress-mode decoy vault: show attacker a plausible fake vault under coercion
- States: LOCKED · UNLOCKED · DECOY
- Integrates with BEA_Shield (duress), BEA_Health (records), BEA_GPU_Fi (earnings)

---

### BEA_Relay — Multi-Node Mesh Networking & Sync
**50 tests | `BEA_Relay/`**

Peer-to-peer mesh networking for offline-first data replication and biometric-authenticated sync between BEA Aura console nodes.

Key files: `relay_node.py` · `relay_sync.py` · `relay_schema.py` · `relay_scanner.py` · `integration.py`

- LAN discovery via UDP multicast on port 7420
- Node types: MINI · NAS · CLOUD · SERVER
- Sync data types: HEALTH · SHIELD · GPU_FI · VAULT · FLOW
- Offline-first queue: records delivered when nodes come back online
- Biometric token-based peer authentication

---

### BEA_Flow — Cross-Pillar Workflow Automation
**50 tests | `BEA_Flow/`**

Native IFTTT for BEA_Aura_OS. Define trigger/action chains across any combination of pillars, powered by BEA_Pulse events.

Key files: `flow_schema.py` · `flow_engine.py` · `flow_library.py` · `flow_scanner.py` · `integration.py`

- FlowTrigger: source pillar + event type + optional field conditions (EQ, GT, LT, NE, IN, CONTAINS)
- FlowAction: pillar command annotated with a BEA operator
- FlowRun: execution record with success/failure/error status
- 12 pre-built flows covering all four pillars, ready to activate

---

### BEA_Lens — Visual Intelligence Engine
**47 tests | `BEA_Lens/`**

L°-based visual signal scanner. Mirrors the S° audio framework for the light domain.

Key files: `l_degree_scanner.py` · `lens_scanner.py` · `frame_processor.py` · `scene_classifier.py` · `lumen_operator_effects.py` · `wellness_signals.py` · `integration.py`

- L° formula: `(λ_visible / 555 nm) × 360°` — maps 380–740 nm to BEA states
- 9 scene classes: BRIGHT · DARK · INDOOR · OUTDOOR · SUNNY · INDOOR_LIGHTING · SCREEN · TRANSITIONAL · CUSTOM
- Eye strain tracking and wellness signal detection
- Integrates with BEA_Spectacle (vision wear) and BEA_Health

---

### BEA_Ledger — On-Device Financial Accounting
**59 tests | `BEA_Ledger/`**

Double-entry ledger for the BEA Aura Console. Tracks GPU-Fi rental income, GPU-Verse hosting revenue, BEA_Shield SaaS income, operating expenses, and IRS 1099-K reporting — entirely on your hardware.

Key files: `ledger_engine.py` · `ledger_schema.py` · `ledger_scanner.py` · `tax_reporter.py` · `integration.py`

- Income sources: GPU_FI_RENTAL · GPU_VERSE_HOSTING · SHIELD_SAS
- Entry types: INCOME · EXPENSE · FEE · REFUND
- 1099-K auto-generation when income exceeds $20,000 USD
- Milestone notifications: $100 · $1,000 · $5,000 · $10,000
- No cloud, no subscription — runs entirely on your console

---

### BEA_Grid — Power & Energy Management
**58 tests | `BEA_Grid/`**

Tracks per-pillar GPU/CPU power consumption, applies time-of-use utility rates, schedules GPU-Fi jobs during off-peak hours, and computes real-time earnings-per-kWh ROI.

Key files: `grid_engine.py` · `power_sampler.py` · `rate_scheduler.py` · `grid_schema.py` · `grid_scanner.py` · `integration.py`

- Power sources: BATTERY · GPU · CPU · CHARGER
- Grid zones: OFF_PEAK · SHOULDER · PEAK · CRITICAL
- Auto-pause GPU-Fi when electricity cost exceeds 16¢/kWh
- Auto-throttle when GPU temperature exceeds 90°C
- Supports flat-rate and Super TOU electricity schedules

---

### BEA_Shell — Unified CLI
**67 tests | `BEA_Shell/`**

Single `bea` command routing to all BEA_Aura_OS pillar subcommands. Each pillar self-registers through PillarAdapter subclasses.

Key files: `shell_engine.py` · `shell_registry.py` · `shell_schema.py` · `shell_coloring.py` · `cli.py` · `integration.py`

- PillarAdapter: per-pillar command registration
- Live status, pillar list, and command history via ShellMetaAdapter
- E-motion color coding in terminal output:

| States | Color |
|---|---|
| E[0–7] | Gray |
| E[8–11] | Red |
| E[12–15] | Yellow |
| E[16–19] | Green |
| E[20–23] | Cyan |
| E[24–27] | Blue |
| E[28–31] | Magenta |

---

### BEA_Director — Multi-Camera Cut Engine
**76 tests | `BEA_Director/` · `BEA_Director_macOS/`**

Automatic multi-camera video cut direction for live productions and gaming streams. Selects the best camera angle based on real-time scene analysis and confidence scoring.

Key files: `director.py` · `director_scanner.py` · `shot_selector.py` · `output_switcher.py` · `crew_roles.py` · `confidence_evaluator.py`

- Multi-camera coordination with automatic cut timing
- Scene confidence evaluation per angle
- Gaming stream optimization
- macOS companion package for cross-platform production

---

### BEA_Identity — Multi-User Biometric Authentication
**54 tests | `BEA_Identity/`**

Multi-user identity and access management for the BEA Aura Console. Supports owner, user, child, and guest profiles with biometric authentication and per-profile pillar permissions.

Key files: `identity_schema.py` · `profile_registry.py` · `session_manager.py` · `portable_profile.py` · `pillar_context_bridge.py` · `identity_scanner.py` · `integration.py`

- Session types: OWNER · USER · CHILD · GUEST
- Maximum 8 profiles per console
- Biometric stored as SHA-256 hash — never plaintext
- 3 failed auth attempts → AUTH_FAILED_REPEATED (critical — surfaces to BEA_Shield)
- PortableProfile: HMAC-SHA256 signed with expiry for cross-household use
- Child profile defaults: GPU-Fi disabled, Vault disabled
- PillarContextBridge: `asyncio.gather()` for parallel context switching across all pillars on login

---

### BEA_Recovery — Power-Loss State Resilience
**61 tests | `BEA_Recovery/`**

Console state resilience and crash recovery. Checkpoints all pillar states continuously, detects unclean shutdown via dirty bit, reconciles interrupted GPU-Fi jobs at boot, and posts automatic refunds.

Key files: `checkpoint_engine.py` · `recovery_engine.py` · `reconciliation_engine.py` · `job_recovery_manager.py` · `dirty_bit.py` · `recovery_schema.py` · `recovery_scanner.py` · `integration.py`

- Continuous pillar state checkpointing
- DirtyBit flag distinguishes clean shutdown from power loss
- Boot-time reconciliation: restore or resume interrupted jobs
- GPU-Fi job classification: RESUME · REFUND · PARTIAL_REFUND
- LedgerRefundAdapter posts refunds to BEA_Ledger automatically

---

### BEA_Firefly_Sprite — USB Installer & Hardware Validator
**162 tests | `BEA_Firefly_Sprite/`**

The 64 GB USB bootable entry point for all BEA Aura Console setup. Validates hardware, installs the OS, hosts live demos, and performs disaster recovery.

Sub-modules: `sprite_agent/` · `discovery/` · `validation/` · `installer/` · `demo/` · `recovery/` · `launcher/` · `autorun/` · `sprite_sdk/` · `sprite_core/` · `sprite_partition/` · `sprite_certifier/` · `onsite_dlc/`

- Three operating modes: INSTALL · DEMO · RECOVERY
- Validates hardware against BEATEK certified hardware database
- Automatic foundation pillar installation
- LAN PXE server for network OS transfer
- Live BEA Aura demo environment on host PC — no console required
- Vault data preservation during recovery wipe
- Autorun scripts for Windows (.inf), macOS (.command), and Linux (.sh)
- `sprite_core`: SpriteMode · TinyAIDimension · SpriteEdition · SpriteCapabilityProfile · DimensionalContentLayer · DimensionalContentMap
- `sprite_partition`: 4-partition layout (boot, OS, BEA_Cache cold tier, recovery)
- `sprite_certifier`: BEATEK hardware certification pipeline
- `onsite_dlc`: invisible Console DLC delivery — zero host awareness required

---

### BEA_SpriteCache — Predictive SSD Asset Prefetch Engine
**43 tests | `BEA_SpriteCache/`**

Onboard predictive caching engine that runs on the **Firefly Sprite's TinyAI processor**. Watches game state, predicts what assets the host iGPU needs next, and pre-loads them into host system RAM before the GPU asks for them. Zero host CPU cost. Zero network dependency. The core invention enabling PS2–PS4 quality on the 1.2 billion PCs in active use with integrated graphics only.

Key files: `sprite_cache_manager.py` · `tinyai_engine.py` · `asset_graph.py` · `prefetch_buffer.py` · `console_handoff.py`

- TinyAI on Sprite silicon predicts next 2–3 seconds of asset demand
- USB-C UASP (450 MB/s) or Thunderbolt 4 (3,500 MB/s) DMA reads from NAND
- Per-session reinforcement learning: edge probability +0.08 on hit, −0.03 on miss
- Console handoff state machine: NOT_PRESENT → DETECTED → SYNCING → ACTIVE
- On Console detected: dumps full asset library to BEA_Cache cold tier, then retires
- Confidence score: `ln(1+n) / ln(6)` — saturates near 1.0 after ~5 sessions

---

### BEA_Cache — NVMe Storage Tiering Engine
**78 tests | `BEA_Cache/`**

Three-tier NVMe cache manager coordinating hot, warm, and cold storage across all pillars. Atomic SHA-256 verified writes prevent silent data corruption. Priority-driven eviction keeps the most latency-sensitive assets closest to the GPU.

Key files: `cache_engine.py` · `tier_manager.py` · `cache_schema.py` · `cache_scanner.py` · `integration.py`

- Tiers: HOT (VRAM-adjacent) · WARM (system RAM) · COLD (NVMe pool)
- Priority map: audio=4 · vpn=3 · gpu=2 · ai=1
- Atomic writes with SHA-256 integrity verification — no partial writes
- BEA_SpriteCache deposits to cold tier on Console handoff
- BEA_AI DLC downloads land in cold tier before silent promotion

---

### BEA_AI — Platform Intelligence Coordination Layer
**100 tests | `BEA_AI/`**

The intelligence coordination layer of the BEA Aura platform. Not an LLM wrapper. Not a cloud API. The module that owns every AI decision across the platform — from TinyAI running on a Firefly Sprite, to the full Console BEA_AI receiving that context when the player walks through their front door, to the background compute delivering DLC while the player is already in the game.

Sub-modules: `tinyai/` · `console_ai/` · `dlc/` · `transition/` · `fusion/` · `context/` · `integration.py`

**TinyAI (Sprite silicon — 500 MB → 4 GB GGUF Q4_K_M):**
- Dimensional host assessment on plug-in: 1D / 2D / 3D / 4D tier selection
- Drives BEA_SpriteCache prefetch prediction
- Domain Q&A for Sprite Agent — fully offline, no network required
- Per-session player model learning; packages full context for Console handoff

**Console BEA_AI (RTX 5060 Ti → RTX 5080):**
- Receives TinyAI handoff on Sprite LAN arrival — upgrades dimension automatically
- NPC intelligence enrichment with cross-session memory
- Silent DLC orchestration via `dlc/` — background download to BEA_Cache cold tier
- Dimensional transition effects: 1D CRT scanline · 2D mip-map weave · 3D Matrix/Animus · 4D BEA-Verse tesseract fold
- BEA Fusion GPU pool: host GPU + Console GPU unified; latency-aware remote fallback via BEA_Shield VPN
- HRV → stress level → difficulty model adjustment via BEA_Health

**Design constraints enforced:** zero host CPU · absolute privacy boundary (no raw biometrics) · base game always complete without DLC · graceful fallback 4D→1D · no cloud dependency in core path

---

### BEA_Context_Bridge — Emotional Memory Engine
**91 tests | `BEA_Context_Bridge/`**

Cross-session emotional memory for the BEA ecosystem. Records and replays BEU (BEA Emotional Unit) state transitions within and across sessions, enabling the Console to remember how a user felt — not just what they did. Also ships an MCP server for direct Claude Desktop integration.

Key files: `context_engine.py` · `beu_schema.py` · `context_scanner.py` · `session_bridge.py` · `mcp_server.py` · `integration.py`

- BEU state transition log: session-scoped emotional trajectory
- Cross-session retrieval: context-aware recall of prior emotional states
- MCP server: exposes BEU history to Claude Desktop for emotionally-aware AI responses
- Feeds BEA_AI player model context and BEA_Health trend analysis

---

### BEA_Aura_Orchestrator — Central Coordination Brain
**TypeScript | `BEA_Aura_Orchestrator/`**

The central nervous system of the BEA Aura Console at the system level. Orchestrates GPU container allocation, slices VRAM across competing pillar workloads, receives WireGuard VPN tunnel intake from BEA_Shield, and maintains a live registry of all active subsystems.

Key files: `orchestrator.ts` · `gpu_scheduler.ts` · `vram_slicer.ts` · `subsystem_registry.ts` · `wireguard_intake.ts`

- GPU container orchestration: per-pillar VRAM budgets enforced at runtime
- VRAM slicing: BEA_AI · BEA_Shield · BEA_GPU_Fi compete on a priority queue
- WireGuard intake: routes remote console sessions from BEA_Shield VPN
- Subsystem registry: live health map of all running BEA pillars
- Graceful degradation: evicts lower-priority containers under pressure, never drops Security or Duress workloads

---

### BEA_4D_Audio — 4D Environmental Acoustics
**`BEA_4D_Audio/`**

Environmental acoustics simulation with haptic controller synchronization for immersive gaming and VR audio.

Key files: `audio_engine.py` · `sound_source.py` · `spatial_processor.py` · `reverb_zone.py` · `operator_effects.py` · `s_degree_scanner.py` · `haptic_sync.py`

- S° scanning: maps frequencies (20 Hz–20 kHz) to BEA states
- HRTF-personalized 3D spatial audio
- GPU-accelerated ray-traced acoustics
- 6 BEA operator acoustic effects in real time
- VR controller haptic synchronization at sub-10 ms latency
- Acoustic material properties: absorption, diffusion, reflection coefficients

---

### BEA_Shield — Security & Threat Detection
**`BEA_Shield/`**

Multi-layer GPU-accelerated network security: 2FA, biometric-authenticated VPN, physiological duress detection, AI camera monitoring, and parental controls.

Sub-modules: `server/` (security daemon) · `client/` (React Native) · `docs/`

- GPU malware scanning: 10 GB/s (vs 100 MB/s CPU)
- Network gateway mode: protects every device in the home
- Camera AI: face recognition, license plate reading, package detection
- VPN server: secure remote access to your own console
- Integrates with BEA_Identity (auth failures) and BEA_Health (duress signals)

---

### BEA_Health — Health & Wellness Tracking
**`BEA_Health/`**

On-device biometric monitoring from any compatible wearable, stored with AES-256 encryption on your console.

Sub-modules: `src/` · `tests/` · `scripts/` · Docker support

- Compatible: Apple Watch · Samsung · Garmin · Fitbit · Oura · Polar
- Metrics: heart rate, HRV, sleep quality, stress, exercise, overtraining
- 72-hour pre-symptom illness detection
- Data never leaves the console — no cloud, no subscription
- Cross-pillar duress detection feeds BEA_Shield

---

### BEA_GPU_Fi — GPU Rental Income Platform
**`BEA_GPU_Fi/`**

Rent spare GPU cycles to ML model trainers through the GPU-Fi marketplace. BEA_Grid manages scheduling; BEA_Ledger handles accounting.

Sub-modules: `src/` · `client/` · `cli/` · `config/` · `sdk/` · `docs/` · `kiosk/`

- Conservative earnings: $200–500/month (Pro tier)
- 15% BEATEK platform fee
- Kiosk UI for token verification
- Real-time earnings-per-kWh ROI from BEA_Grid integration
- GPU-Verse tier: host virtual worlds for $5,000–20,000/month (NAS)

---

### BEA_Spectacle — Vision Wear Integration
**`BEA_Spectacle/`**

AR/VR vision wear integration for immersive gaming and daily life on monitors people already own.

- Head-tracked parallax rendering on 1–3 monitors
- Eye-tracking anomaly detection feeds Physiological Duress Detection
- Integrates with BEA_Lens for light-domain E-motion mapping
- 350M+ monitor gamers vs 20M headset owners — the larger market

---

### BEA_Speakerbox — Professional Voice-Over Production
**84 tests | `BEA_Speakerbox/`**

Professional voice-over production engine grounded in the BEA E-motion mathematical framework. Not a standalone app — a Console component that processes locally and streams to thin-client apps via BEA_Shield VPN.

Key files: `vocal_processor.py` · `voice_scanner.py` · `spatial_voice.py` · `session_recorder.py` · `performance_engine.py` · `director_engine.py` · `bea_logic.py` · `integration.py`

- `VoiceScanner` subclasses `BEAScanner` — voice frequencies → S° → E[0–31]
- 6 BEA operators (⊕⊖⊗⨀≠⧖) map to vocal character + 6 performance metrics
- 15 emergent vocal effects from operator combinations
- BEA Logic™: Emergence (1⊕1=3) and Divergence applied to voice dynamics
- SpeakerboxBridge feeds → BEA_Beatbox, BEA_4D_Audio, BEA_Health

---

### BEA_Motion_Body — Full-Body Motion Capture
**`BEA_Motion_Body/`**

84 anatomical landmark webcam tracking. Hands and feet. Zero wearables required.

Sub-modules: `bea_motion_body/` · `bea_motion_glove/` · `bea_motion_legs/` · `bea_motion_intelligence/` · `client_apps/`

- WiFi-based, low-latency sensor integration
- ML gesture recognition via `bea_motion_intelligence/`
- iOS, Android, and web client apps
- Heel locomotion for seated, fatigue-free gaming
- $0–199 vs $500–2,000 for VR full-body tracking

---

### BEA_Lumin_Pi — TV & Speaker Satellite
**311 tests | `BEA_Lumin_Pi/`**

Raspberry Pi-based satellite node that turns any TV and speaker system into a BEA-aware display terminal. Connects to the BEA Aura Console over LAN, receives E-motion state from BEA_Pulse, and adapts its audio-visual output accordingly. Operates in 7 auto-selected modes based on detected LAN services.

Key files: `lumin_core.py` · `lumin_hardware.py` · `lumin_modes.py` · `lumin_scanner.py` · `integration.py`

- 7 operating modes auto-selected from LAN environment (TV, Speaker, Mirror, Ambient, Gaming, Health, Security)
- UDP heartbeat on port 7474 — low-latency state sync from Console
- `LuminPiHardwareValidator`: 10 certification categories, validates against REFERENCE_HARDWARE spec
- `LuminPiHardwareMonitor`: real-time hardware health telemetry (simulate=True for CI)
- `LuminPiSystemHealth`: aggregates CPU, GPU, memory, temperature into a single health state
- BEA_Shield VPN opt-in (disabled by default) — enable for remote satellite access
- `LuminCompanionSpec` resides in Firefly Sprite SDK — zero circular dependency

---

## Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    BEA_Aura_OS                          │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  BEA_Shell (unified CLI)          BEA_Aura_Orchestrator │
│                                   (GPU · VRAM · VPN)    │
│  ┌─────────────────────────────────────────────────┐   │
│  │             BEA_Pulse (event bus)               │   │
│  │   pub/sub · asyncio · BEA operators · Redis     │   │
│  └─────────────────────────────────────────────────┘   │
│          │         │         │         │                │
│   ┌──────┐  ┌──────┐  ┌──────┐  ┌──────┐  ┌──────┐   │
│   │Gaming│  │Securi│  │Health│  │Income│  │Found.│   │
│   │      │  │ ty   │  │      │  │      │  │      │   │
│   │4D    │  │      │  │      │  │GPU-Fi│  │Vault │   │
│   │Audio │  │Shield│  │Health│  │Grid  │  │Relay │   │
│   │Spec- │  │Ident-│  │      │  │Ledger│  │Flow  │   │
│   │tacle │  │ity   │  │      │  │      │  │      │   │
│   │Motion│  │Recov-│  │      │  │      │  │Cache │   │
│   │Body  │  │ery   │  │      │  │      │  │Lens  │   │
│   └──────┘  └──────┘  └──────┘  └──────┘  └──────┘   │
│                                                         │
│  Foundation: BEA_Core — BEA™ E-motion Framework        │
│  BEAScanner base · 32 states · S° · L° · E°            │
│                                                         │
│  Satellites: BEA_Lumin_Pi (TV/speaker) ←── LAN         │
│                                                         │
└─────────────────────────────────────────────────────────┘

Network: BEA_Relay (mesh sync) ↔ BEA_Firefly_Sprite (install/boot)
Context: BEA_Context_Bridge ↔ Claude Desktop (MCP server)
```

### BEAScanner Contract

Every pillar implements a BEAScanner subclass:
1. Receives domain-specific events
2. Maps them to E[0–31] BEA states
3. Emits transitions via BEA_Pulse
4. Tracks ScanResult: `bea_state`, timestamp, event detail

### Integration Pattern

Each pillar's `integration.py` provides:
- Per-pillar **Adapter** classes (e.g., `HealthVaultAdapter`, `GridLedgerAdapter`)
- **Broadcaster** class that emits to BEA_Pulse
- Optional specialized adapters (e.g., `LedgerRefundAdapter`, `PillarContextBridge`)

### Async Architecture

- All pillars use Python `asyncio` internally
- BEA_Pulse broker is async-first with optional Redis backend
- Test framework: `anyio` — use `@pytest.mark.anyio` per async test function
- No `pytest-asyncio`, no class-level markers, no async fixtures

---

## Getting Started

### Requirements

- Python 3.10+
- `numpy >= 1.20.0`
- `anyio` (for async tests)

### Install

```bash
pip install -e .
```

### Run Tests

```bash
make test        # Run all 1,968 pillar tests
make check       # Tests + linting
make lint        # Linting only
```

### Validate Hardware

```bash
make gpu-validate    # Pre-flight GPU hardware check
python BEA_Aura_GPU_Validator.py
```

### Run Demos

```bash
make demo
python audio_scan_demo.py
python visual_scan_demo.py
python multinode_sync_demo.py
```

### CLI

```bash
bea status           # System status
bea pillars          # List active pillars
bea vault unlock     # Unlock encrypted vault
bea grid status      # Power and earnings snapshot
bea ledger summary   # Income and tax summary
```

---

## Test Summary

| Module | Tests | Domain |
|---|---|---|
| BEA_Core | 163 | Signal-physics foundation |
| BEA_Pulse | 44 | Event bus |
| BEA_Beatbox | 80 | Emotional audio |
| BEA_Vault | 51 | Encrypted storage |
| BEA_Relay | 50 | Mesh networking |
| BEA_Flow | 50 | Workflow automation |
| BEA_Lens | 47 | Visual intelligence |
| BEA_Ledger | 59 | Financial accounting |
| BEA_Grid | 58 | Power management |
| BEA_Shell | 67 | CLI |
| BEA_Director | 76 | Multi-camera direction |
| BEA_Identity | 54 | Biometric auth |
| BEA_Recovery | 61 | Crash resilience |
| BEA_Firefly_Sprite | 162 | Installer / validator / DLC / certification |
| BEA_SpriteCache | 43 | Predictive asset prefetch, TinyAI session learning, Console handoff |
| BEA_Cache | 78 | NVMe tiering (hot/warm/cold), priority eviction, atomic SHA-256 writes |
| BEA_AI | 100 | TinyAI, Console AI, DLC, transitions, fusion, context, integration |
| BEA_Speakerbox | 84 | Voice-over production, S° vocal scanning, BEA operator effects |
| BEA_Context_Bridge | 91 | Emotional memory engine, BEU state transitions, MCP server |
| BEA_Notify | 67 | Push notifications — DASHBOARD / TOAST / MOBILE / EMERGENCY; CRITICAL gate |
| BEA_Voice | 62 | On-device voice commands — "Hey BEA" → intent → BEA_Shell; duress E[28+] path |
| BEA_Update | 57 | OTA pillar update manager — SHA-256 + Ed25519, BEA_Grid scheduling, auto-rollback |
| BEA_Plugin | 53 | Pillar Extension SDK — BEAPillar base class, shell/pulse/flow bridges, entry-point discovery |
| BEA_Lumin_Pi | 311 | TV/speaker satellite — 7 LAN modes, hardware validator, system health |
| BEA_Aura_Orchestrator | TS | GPU containers, VRAM slicing, WireGuard intake, subsystem registry |
| **Total** | **1,968** | **All passing** |

---

## Project Structure

```
BEA_Aura_OS/
├── README.md
├── LICENSE
├── Makefile
├── pyproject.toml
├── setup.py
├── requirements.txt
├── conftest.py
├── bea_config.py               # 30+ environment variables
├── bea_logging.py              # JSON + rotating file logging
├── scanner.py                  # BEAScanner core implementation
├── __init__.py                 # Root package: BEAScanner, quick_scan helpers
│
├── BEA_Core/                   # Signal-physics foundation (32-state, operators, S°/L°)
├── BEA_Pulse/                  # Inter-pillar event bus
├── BEA_Beatbox/                # Emotional beat engine
├── BEA_Vault/                  # AES-256-GCM file vault
├── BEA_Relay/                  # Mesh networking & sync
├── BEA_Flow/                   # Workflow automation
├── BEA_Lens/                   # Visual intelligence
├── BEA_Ledger/                 # Financial accounting
├── BEA_Grid/                   # Power management
├── BEA_Shell/                  # Unified CLI
├── BEA_Director/               # Multi-camera cut engine
├── BEA_Director_macOS/         # macOS companion
├── BEA_Identity/               # Biometric auth
├── BEA_Recovery/               # Crash resilience
├── BEA_Firefly_Sprite/         # USB installer + sprite_core/partition/certifier/onsite_dlc
├── BEA_4D_Audio/               # Spatial audio
├── BEA_Shield/                 # Security daemon
├── BEA_Health/                 # Health monitoring
├── BEA_GPU_Fi/                 # GPU rental income
├── BEA_Spectacle/              # Vision wear integration
├── BEA_Motion_Body/            # Full-body tracking
├── BEA_Speakerbox/             # Professional voice-over production
├── BEA_SpriteCache/            # Predictive SSD asset prefetch engine
│   ├── sprite_cache_manager.py #   Main orchestrator
│   ├── tinyai_engine.py        #   Prediction + session learning
│   ├── asset_graph.py          #   Cluster + transition graph
│   ├── prefetch_buffer.py      #   Host RAM prefetch store
│   └── console_handoff.py      #   BEA_Cache handoff state machine
├── BEA_Cache/                  # NVMe tiering: hot/warm/cold, priority eviction
├── BEA_AI/                     # Platform intelligence coordination layer
│   ├── integration.py          #   BEA_Pulse broadcaster
│   ├── tinyai/                 #   TinyAI: dimensions, domain, session, core
│   ├── console_ai/             #   Console AI: handoff, NPC, world state
│   ├── dlc/                    #   Silent DLC: registry, network, loader
│   ├── transition/             #   Effects 1D–4D + world swap manager
│   ├── fusion/                 #   GPU pool: remote bridge, handoff, fusion
│   └── context/                #   Player model, sync, biometric context
├── BEA_Context_Bridge/         # Emotional memory engine + MCP server
├── BEA_Aura_Orchestrator/      # TypeScript: GPU/VRAM orchestration, WireGuard intake
├── BEA_Notify/                 # Push notifications (4 channels, CRITICAL gate)
├── BEA_Voice/                  # Voice commands ("Hey BEA" wake word)
├── BEA_Update/                 # OTA update manager (SHA-256 + Ed25519, auto-rollback)
├── BEA_Plugin_SDK/             # Pillar Extension SDK (BEAPillar ABC, entry-point discovery)
├── BEA_Lumin_Pi/               # TV/speaker satellite (7 modes, hardware validator)
│
├── tests/
│   ├── test_integration.py     # Cross-pillar integration tests
│   ├── test_scanner_contract.py
│   └── bea_scanner_contract.py
│
├── README/                     # Theory & architecture docs
│   ├── BEA_Core_Technical_Architecture.md
│   ├── 32_state_table.md
│   ├── electronic_motion.md
│   ├── formulas.md
│   └── HOW_GPU_FI_WORKS.md
│
├── audio_scan_demo.py
├── visual_scan_demo.py
├── multinode_sync_demo.py
└── BEA_Aura_GPU_Validator.py
```

---

## Key Configuration

`bea_config.py` exposes all tuneable parameters as environment variables:

```bash
# Audio
BEA_AUDIO_REFERENCE_HZ=440        # S° reference frequency

# Grid / Power
BEA_GRID_PAUSE_THRESHOLD=0.16     # Pause GPU-Fi above 16¢/kWh
BEA_GRID_THERMAL_THRESHOLD=90     # Throttle above 90°C

# Identity
BEA_MAX_PROFILES=8
BEA_AUTH_FAIL_THRESHOLD=3

# Ledger
BEA_TAX_THRESHOLD_USD=20000       # 1099-K filing threshold
```

---

## The Mission

> **"The Fifth Freedom: Own the infrastructure running your software."**

Open source adds four freedoms: run, study, redistribute, improve.
BEATEK adds a fifth: **own the machine your software runs on.**

Open source software running on Amazon AWS means Amazon profits from your work.
That same software running on your BEA Aura Console means you profit from your infrastructure.

---

## Get Involved

| Role | What We Need |
|---|---|
| **Contributors** | Python engineers, ML/CV specialists, GPU developers, full-stack |
| **Partners** | Hardware OEMs, distributors, security firms, health tech |
| **Investors** | Aligned with owned-infrastructure, anti-subscription mission |
| **Early Adopters** | Console pre-orders launching Q2 2026 |

**Contact:** jeremyjackson7@proton.me
**GitHub:** [github.com/BEAT-K](https://github.com/BEAT-K)
**License:** MIT (community) / Commercial (partners)

---

*BEATEK Holdings, LLC · Founded by Jeremy F. Jackson · Patent Pending · 2026*
