# Embodied VR Flying Locomotion System

A broom-riding locomotion system for Virtual Reality, built in **Unreal Engine**, based on and critically extending the work of [Hedlund et al. (2025) — *BroomBroom! Evaluation of Leaning and Controller-based Locomotion for Flying in Virtual Reality*](https://doi.org/10.1145/3756884.3766017).

**Authors:** [Anjolaoluwa Lasekan](https://github.com/Anjolash) ·  [Hu Congwei](https://github.com/DDesmond)  — Concordia University

---

## Overview

Most VR locomotion systems are designed for ground-based movement. This project tackles free-space flying with an embodied broomstick metaphor — designed specifically for users on swivel chairs — prioritizing presence, comfort, and intuitive control over the original paper's more experimental approach.

Key departures from the reference implementation (which was built in Unity):

- **Fixed hip-level pivot** — the broom behaves like a lever you steer, not a pointer you aim
- **Dynamics-based velocity** — smooth acceleration and asymmetric deceleration via Unreal's `FloatingPawnMovement`; no abrupt starts/stops
- **Dual-hand grip logic** — one hand = cruise speed, both hands = sprint; aligns naturally with leaning forward
- **Perceptual comfort features** — vignetting at high speeds, collision haptics, and pitch limits to reduce VR sickness
- **Canyon test environment** — built from real-world geographic data to stress-test maneuverability

---

## Features

| Feature | Description |
|---|---|
| Broomstick pivot interaction | Broom mounted at hip-level pivot; yaw free (360°), pitch limited (±60°/30°) |
| Smooth flight dynamics | Throttle-style input; gliding deceleration on release, firm braking on input |
| Dual-hand gear logic | Single grip = default speed cap; double grip = speed boost |
| Speed vignetting | Field-of-view contracts at high velocity to reduce peripheral motion sickness |
| Collision feedback | Visual shield effect + controller haptic vibration on impact |
| Canyon level | Complex terrain with variable-width paths and multi-level visual anchors |

---

## Built With

- **Unreal Engine 5**
- **Meta/OpenXR VR plugin**
- Blueprint (primary logic) + minimal C++ where needed

---

## Getting Started

### Prerequisites

- Unreal Engine 5.x
- A PC VR headset (tested on Meta Quest via Link)
- Controllers with haptic support

### Running the Project

1. Clone the repo
   ```bash
   git clone https://github.com/<your-org>/vr-broom-locomotion.git
   ```
2. Open the `.uproject` file in Unreal Engine 5
3. Enable the OpenXR / OculusVR plugin for your headset if not already active
4. Play in VR Preview mode or package for your target platform

---

## Controls

| Input | Action |
|---|---|
| Grip (one hand) | Hold broom — cruise mode |
| Grip (both hands) | Hold broom — sprint mode |
| Tilt broom (yaw/pitch) | Steer direction of flight |
| Right thumbstick | Throttle (accelerate / brake) |
| Swivel chair rotation | Full 360° yaw steering |

> The system is optimized for **seated play on a swivel chair**. Standing use is possible but long sessions may cause fatigue.

---

## Project Structure

```
Content/
├── Blueprints/
│   └── BP_Pawn          # Core VR pawn with broom interaction logic
├── Levels/
│   └── CanyonTest       # Main evaluation environment
├── Meshes/
│   └── Broom/           # Broom asset with pivot point setup
└── UI/
    └── VignetteMaterial # Speed-based FOV vignette
```

---

## Known Limitations

- No formal user study yet — evaluation is based on developer testing and informal observation
- HMD–pivot spatial drift can occur with large body movements (no dedicated hip tracker)
- Roll axis is locked; subtle roll during turns caused motion sickness in testing

---

## Based On

> Hedlund, M., Müller, F., Schmitz, M., Bogdan, C., Rey, R., Ghavamian, P., Tobin, D., & Matviienko, A. (2025). BroomBroom! Evaluation of Leaning and Controller-based Locomotion for Flying in Virtual Reality. *VRST '25*. https://doi.org/10.1145/3756884.3766017

---

## License

MIT