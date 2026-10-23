# Procedural Pack Icon Generator

Many community addons and custom packs lack a `pack_icon.png`, showing up as a generic placeholder icon in both Minecraft and your library.

Bedrock Manager includes a built-in **Procedural Icon Generator** that creates a distinctive voxel-island scene for any pack missing an icon.

---

## How It Works

When a freshly installed pack has no `pack_icon.png`, its Install result card shows an inline icon suggestion with a preview plus **Regenerate** and **Add icon** actions.

```
  [ Pack Identity ]
         │
         ▼
  ┌──────────────────────────────────────┐
  │     Procedural Generator Engine      │
  │  - Builds an isometric voxel island  │
  │  - Applies a themed biome palette    │
  │  - Seeds the first look from the     │
  │    pack name for a consistent feel   │
  └──────────────────┬───────────────────┘
                     │
                     ▼
             [ pack_icon.png ]
```

---

## Generator Capabilities

- **Biome-Themed Islands**: Each icon is a small isometric floating-island diorama rendered in an art-directed biome palette.
- **Seeded First Look**: The initial suggestion is seeded from the pack name so it feels intentional; every **Regenerate** rolls a fully random new island.
- **One-Click Save**: **Add icon** writes the chosen render straight into the pack folder as `pack_icon.png`, ready for Minecraft to display.
