# 2D & 3D Skin Studio

The **Skins** studio (`/skins`) provides a full skin library and an interactive 2D and 3D editor for creating, customizing, and exporting Minecraft character skins.

---

## Skin Library & Import

The skin library manages all your saved and imported skin files:
- **Import Skin**: Import any standard 64×64 or 64×32 `.png` skin image.
- **Legacy Skin Normalization**: Older Minecraft skins often use the 64×32 format (where left and right limbs share mirrored textures). Bedrock Manager automatically parses and upgrades 64×32 skins to the modern 64×64 format by expanding the canvas and padding empty regions with transparency.
- **Model Support**: Fully supports both **Steve (Classic 4-pixel arms)** and **Alex (Slim 3-pixel arms)** geometries.

---

## The 3D Viewport (`skinview3d`)

The 3D studio renders your character model in real time with hardware-accelerated WebGL:

### Interactive 3D Painting
- Paint directly onto the 3D model geometry. The editor automatically projects your brush strokes onto the underlying UV texture coordinate map.

### Layer & Body Part Toggles
- **Body Parts**: Toggle visibility for Head, Torso, Left Arm, Right Arm, Left Leg, and Right Leg. Hiding limbs makes it easy to paint obscured surfaces (such as the inner side of arms and legs).
- **Overlay Layer**: Toggle the outer jacket/hat/sleeve overlay layer independently of the base skin layer.

### Pose & Animation Controls
- Preview your skin under various animation states:
  - **Idle** (subtle breathing animation)
  - **Walk** (standard player walking cycle)
  - **Run** (sprinting motion)
  - **Wave** (arm greeting)
  - **Auto-rotate** (continuous 360-degree inspection)

---

## The 2D Pixel Canvas Editor

For precision pixel art, switch to or use the split 2D editor:

| Tool | Function |
| :--- | :--- |
| **Pencil** | Single-pixel drawing with customizable brush sizes. |
| **Eraser** | Clears pixels to full transparency (ideal for outer layer editing). |
| **Paint Bucket (Fill)** | Flood fills contiguous regions of matching color. |
| **Eyedropper** | Picks colors directly from either the 2D canvas or 3D model. |
| **Grid Overlay** | Toggles pixel grid boundaries for accurate alignment. |
| **Color Palette** | Save custom color swatches and access recently used colors. |
| **Undo / Redo** | Multi-step history stack for safe experimenting. |

---

## In-Game Skin Pack Generation

In Minecraft Bedrock, imported raw PNGs often reset or lack proper dressing room categorization.

Bedrock Manager automates this by generating a dedicated, app-managed skin pack inside your game directory:
1. When you save or activate a skin, the backend creates a valid Bedrock skin pack in `skin_packs/Bedrock Manager Skins`.
2. It generates compliant `manifest.json` and `skins.json` definitions mapping the geometry (Classic vs Slim) and texture paths.
3. When you open Minecraft, your custom skins appear directly in the **Dressing Room > Classic Skins > Bedrock Manager Skins**.
