# Procedural Pack Icon Generator

Many community addons and custom packs lack a `pack_icon.png`, showing up as a generic placeholder icon in both Minecraft and your library.

Bedrock Manager includes a built-in **Procedural Icon Generator** that automatically creates high quality, pixel art style badges for any pack missing an icon.

---

## How It Works

When an addon without a `pack_icon.png` is imported, Bedrock Manager generates a distinctive, consistent badge based on the pack's unique identity. This ensures that every pack in your collection is immediately recognizable at a glance.

```
  [ Pack Identity ]
         │
         ▼
  ┌──────────────────────────────────────┐
  │     Procedural Generator Engine      │
  │  - Selects themed item silhouette    │
  │  - Applies pixel-art shading & depth │
  │  - Generates balanced color palette  │
  │  - Renders background frame & border │
  └──────────────────┬───────────────────┘
                     │
                     ▼
             [ pack_icon.png ]
```

---

## Generator Capabilities

### 1. 20+ Minecraft-Themed Silhouettes
The generator includes hand-crafted pixel-art masks covering a wide variety of Minecraft items and gear:
- **Weapons & Tools**: Swords, Pickaxes, Axes, Shovels, Shields, Bows
- **Armor**: Helmets, Chestplates, Boots
- **Artifacts & Utilities**: Potions, Enchanted Books, Compasses, Keys, Crystals, Gems, Hearts, Skulls, Flames, Orbs, Coins, Stars

### 2. Multi-Layer Pixel-Art Shading
Each badge is rendered with multi-tiered shading incorporating outer outlines, shadow depths, primary material tones, and top-edge specular highlights to match the authentic Minecraft art style.

### 3. Harmonic Color Palettes
Colors are automatically balanced to ensure strong contrast and readability, pairing vibrant item colors with coordinated backgrounds.

### 4. Background Styles & Framing
- **Backgrounds**: Radial glows, smooth linear gradients, vignettes, and ray bursts.
- **Frames**: Classic inventory slot borders, circular badge rings, or clean borderless styles.

---

## Customizing Pack Icons

You can customize or generate new icons for any installed pack at any time:

1. Open **Addons** from the sidebar.
2. Click any pack to open its inspector panel.
3. Click **Edit Icon** to open the icon customizer.
4. Choose a specific silhouette, roll a new randomized look, adjust color sliders, or upload a custom image.
5. Click **Apply Icon** to save the new `pack_icon.png` directly into your pack folder.