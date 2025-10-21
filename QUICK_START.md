# Quick Start Guide - BEA_BEM_Grid_1

## Getting Started in 5 Minutes

### Prerequisites Checklist

- [ ] Unity 2022.3 LTS or newer installed
- [ ] GPU with Compute Shader support
- [ ] Universal Render Pipeline (URP) knowledge
- [ ] Basic C# programming experience

### Setup Steps

1. **Open Project**
   ```powershell
   # Clone or download the project
   # Open Unity Hub > Add > Select BEA_BEM_Grid_1 folder
   ```

2. **Verify URP Configuration**
   - Check `Project Settings > Graphics > Scriptable Render Pipeline Settings`
   - Ensure URP asset is assigned

3. **Test Compute Shader Support**
   - Open `Window > Analysis > Profiler`
   - Check GPU module for compute shader compatibility

### First Run

1. Open the main scene from `Assets/Scenes/`
2. Press **Play** in Unity
3. Observe the emotional grid simulation
4. Use mouse/keyboard to interact with the grid

### Basic Interaction

| Input | Action |
|-------|--------|
| Left Click | Inject emotional state |
| Right Click | Remove emotional state |
| Space | Pause/Resume simulation |
| R | Reset grid |
| D | Toggle debug view |

### Understanding the Output

- **Colors**: Each emotional state has a unique color
- **Brightness**: Intensity of emotional state (0-255)
- **Movement**: State propagation and interaction
- **Decay**: Natural fading over time

### Common Issues

**Grid Not Updating**
- Check compute shader compilation in Console
- Verify GPU compatibility in Project Settings

**Performance Issues**
- Reduce grid size in BEAGrid component
- Increase update interval
- Check GPU profiler for bottlenecks

**Missing Emotional States**
- Verify all prefabs are in Prefabs folder
- Check `prefab_mapping.json` integrity
- Ensure prefab GUIDs are correct

### Next Steps

1. **Explore Scripts**: Examine `BEABit.cs` and `BEAGrid.cs`
2. **Modify Parameters**: Adjust grid size and update rates
3. **Add Custom States**: Create new emotional state prefabs
4. **Experiment**: Try different rule configurations

### Key Files to Understand

- `BEABit.cs` - Core emotional state class
- `BEAGrid.cs` - Main grid simulation logic
- `BEAController.cs` - Central system coordination
- `prefab_mapping.json` - Emotional state index mapping

### Development Workflow

1. Make changes to scripts
2. Test in Play mode
3. Monitor Console for errors
4. Use Profiler for performance analysis
5. Iterate and optimize

---

*For detailed documentation, see README.md and PROJECT_OVERVIEW.md*