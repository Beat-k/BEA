# BEAGrid-Demo_Unity Project Overview

## 🧠 What is BEAGrid-Demo_Unity?

BEAGrid-Demo_Unity is a comprehensive Unity-based demonstration of the Behavioral Emotional Architecture (BEA) framework—a system for modeling, visualizing, and computing emotional states as mathematical entities. This project showcases real-time emotional computing, interactive grid-based visualization, and health monitoring integration, all built on a robust 4-bit emotional architecture.

## 🎯 Key Features

- **4-Bit Emotional Grid**: Each cell represents one of 16 emotional states (E[0]–E[15]) using a 4-bit identifier, supporting intensity, decay, and propagation.
- **Symbolic Operators**: Implements BEA mathematical operators (⊕ Combust, ⊖ Balance, ⊗ Fuse, ⊘ Diffuse, ⊙ Gate) for emotional state interactions.
- **Real-Time Visualization**: 3D grid with material-based rendering, dynamic color mapping, and animated transitions.
- **Health Monitoring**: Simulated heart rate and stress data influence grid evolution and emotional state propagation.
- **Editor Tools**: Custom Unity Editor windows for grid management, setup automation, and prefab repair.
- **AI & TTS Integration**: BEATRIX voice assistant for grid control and TTSEngine for emotional context audio feedback.
- **Modular Architecture**: Clean namespace separation (Grid, Editor, UI, Core, Services) for maintainability and extensibility.
- **Python Backend**: Includes Python implementations for cross-platform research and algorithmic prototyping.

## 🏗️ Project Structure

```
BEAGrid-Demo_Unity/
├── Grid/                  # Core grid data structures
│   ├── BEA_Grid.cs
│   └── BEAGridManager.cs
├── Prefabs/               # 16 emotional state prefabs (E_0 to E_15)
├── Shaders/               # Custom shaders for visualization
├── BEAGridComponent.cs    # MonoBehaviour wrapper for 3D visualization
├── BEAController.cs       # Main orchestrator and health integration
├── BEACalc.cs             # BEA operator logic
├── BEABit.cs              # Emotional data structure
├── BEAGameCalculatorUI.cs # Calculator-style UI
├── BEAGridUI.cs           # Grid visualization UI
├── BEAInteractiveUI.cs    # Advanced UI system
├── BEAInteractiveUI_TMP.cs# TextMeshPro-based UI
├── EmotionalStateVisualizer.cs # 3D state rendering
├── EmotionalStatePalette.cs    # Color mapping
├── HealthMonitor.cs       # Biometric simulation
├── TTSEngine.cs           # Text-to-speech system
├── BEATRIXInterface.cs    # AI assistant integration
├── BEAGridManagerEditor.cs# Editor window
├── BEASetupUtility.cs     # Project setup automation
├── BEAPrefabRepairUtility.cs # Prefab maintenance
├── CalculationService.cs  # Service architecture
├── InputHandler.cs        # User input management
├── Python Implementation/
│   ├── bea_engine.py      # Core BEA logic
│   └── bea_gridbrain_calc.py # Advanced calculations
```

## 🚀 How It Works

- **Grid Evolution**: Each frame, BEAbits (grid cells) update their state, interact with neighbors, and propagate emotional changes using BEA operators.
- **Visualization**: Emotional states are rendered in 3D with color, animation, and effects reflecting intensity and transitions.
- **Health Data**: Heart rate and stress levels (simulated or real) modulate grid behavior and emotional propagation.
- **Editor Tools**: Unity Editor windows allow live tuning of grid parameters, prefab management, and automated setup.
- **AI & TTS**: BEATRIX enables voice control of grid operations; TTSEngine provides spoken feedback with emotional context.
- **Python Backend**: Enables algorithmic prototyping and research outside Unity.

## ✨ Example Emotional States

- **E[0] Neutrality** 😐
- **E[1] Curiosity** 🤔
- **E[2] Calmness** 😊
- **E[3] Ignition** ❤️
- **E[4] Excitement** 🔥
- **E[5] Strength** 💪
- **E[6] Wonder** ✨
- **E[7] Amusement** 😄
- **E[8] Concern** 😰
- **E[9] Sadness** 😢
- **E[10] Anger** 😠
- **E[11] Anxious** 😵
- **E[12] Confusion** 🤯
- **E[13] Heartbreak** 💔
- **E[14] Dissolution** ☠️
- **E[15] VoidPeak** 🖤

## 🧩 Integration & Extensibility

- **Modular Design**: Add new emotional states, operators, or UI components easily.
- **Service Architecture**: CalculationService and ICalculationService support extensible grid operations.
- **Editor Automation**: BEASetupUtility and BEAPrefabRepairUtility streamline project setup and maintenance.
- **Cross-Platform**: Python backend enables research and prototyping outside Unity.

## 📚 Documentation & Support

- See `GITHUB_README_SUMMARY.md` and `README.md` for full technical documentation, setup instructions, and advanced usage.
- For web and Android BEA calculator projects, see related repositories:
  - [BEA-Game-Calculator-Demo (Web)](https://github.com/Beat-k/BEA-Game-Calculator-Demo-v1.git)
  - [BEA Calculator Android](https://github.com/Beat-k/BEA-Game-Calculator-Android-Demo.git)

## 🔮 Vision

BEAGrid-Demo_Unity is part of a broader initiative to make emotional intelligence computable, visual, and interactive—bridging the gap between human experience and digital systems. The framework is designed for research, education, game development, and therapeutic applications, with extensibility for future AI and biometric integrations.

---

© 2025 Jeremy F. Jackson. All Rights Reserved. **Beat⊕k™** is a trademark of Jeremy F. Jackson.
