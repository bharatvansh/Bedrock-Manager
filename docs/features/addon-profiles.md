# Addon Profiles & Loadouts

**Addon Profiles** (`/addon-profiles`) allow you to create, save, and switch between modular presets of Resource and Behavior packs. Instead of manually enabling 15 different packs each time you create or switch worlds, you can apply an entire loadout with a single click.

---

## Why Use Profiles?

Different playstyles often require different collections of packs:
- **Survival Enhancement Loadout**: Clear water textures, custom UI, durability counters, and utility behavior scripts.
- **Shader / Aesthetic Loadout**: High-resolution PBR textures, custom skyboxes, and atmospheric audio packs.
- **Multiplayer / Realm Loadout**: Performance-optimized textures with minimal script overhead.

Profiles allow you to organize these setups independently of individual worlds.

---

## Creating & Managing Profiles

### 1. Create a New Profile
1. Navigate to **Profiles** in the sidebar.
2. Click **+ New Profile**.
3. Set a profile name and description, then pick a custom accent color and icon seed.

### 2. Add and Order Packs
1. Click **Manage Packs** inside your profile.
2. Select the resource and behavior packs you want to include from your library.
3. Use the drag handles to arrange the pack loading order.

> [!TIP]
> In Minecraft Bedrock, pack order matters. When two resource packs modify the same texture (for example, the diamond sword), the pack positioned **higher** in the stack overrides the pack below it.

---

## Applying Profiles

Profiles can be deployed in two ways:

### Apply to World
- Click **Apply to World** and choose any world from your save list.
- Bedrock Manager writes the exact pack ordering to the target world's `world_resource_packs.json` and `world_behavior_packs.json`.
- Existing packs on the world can be completely replaced or merged based on your selection.

### Apply as Global Resources
- Click **Apply as Global Resources**.
- Bedrock Manager writes the resource packs directly to your player's global configuration (`global_resource_packs.json`).
- These packs will be active in menus, server connections, and worlds that don't have conflicting local packs.

---

## Exporting & Sharing Profiles

- **Export Profile**: Saves your profile definition as a lightweight `.json` preset.
- **Import Profile**: Loads a profile configuration shared by a friend. If any referenced packs are missing from your library, Bedrock Manager highlights them so you can download the required packs.
