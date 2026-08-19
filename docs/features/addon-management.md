# Addon & Pack Management

The **Addons** page (`/addons`) is your central library for viewing, filtering, inspecting, and managing all installed Minecraft Bedrock packs.

---

## The Library Interface

The library provides four dedicated view tabs:
- **All**: Displays all installed packs across all categories.
- **Add-ons**: Displays paired packs (where a Resource Pack and Behavior Pack belong to the same project).
- **Resource Packs**: Visual textures, models, animations, shaders, UI changes, and audio definitions.
- **Behavior Packs**: Entity behaviors, loot tables, recipes, custom items, blocks, and JavaScript/TypeScript scripts.

### Search and Filtering
- **Live Search**: Instant filtering across pack names and descriptions.
- **Sorting Options**: Sort by Date Modified (Newest / Oldest), Disk Size (Largest / Smallest), or Alphabetical (A–Z / Z–A).
- **Development Packs Toggle**: Toggle visibility for `development_resource_packs`, `development_behavior_packs`, and `development_skin_packs`.

---

## Smart Addon Pairing

In Minecraft Bedrock, full addons usually come as two distinct folders: a Resource Pack (RP) and a Behavior Pack (BP).

Bedrock Manager automatically scans manifests for linked UUIDs and dependency declarations. When matching pairs are found, they are grouped into a single unified **Addon Card**. This gives you a cleaner library view while still allowing you to inspect or configure each half independently.

---

## Pack Details & Actions

Clicking any pack opens the **Slide out Inspector Panel**:

| Detail / Action | Description |
| :--- | :--- |
| **UUID & Version** | View header UUID, version tuple `[x, y, z]`, and minimum engine version requirements. Click any UUID to copy it to your clipboard. |
| **Active Worlds List** | Displays every world where this pack is currently enabled in `world_resource_packs.json` or `world_behavior_packs.json`. |
| **Subpack Tiers** | If the pack includes subpack configurations (e.g. 16x/32x/64x texture resolutions or UI modes), the inspector lists all available tiers and memory targets. |
| **Peek Inside** | Opens the dual-pane archive browser to inspect textures, audio, and scripts without unpacking files manually. |
| **Export Archive** | Re-packs the pack into a clean `.mcpack` or `.mcaddon` file ready for sharing. |
| **Open Folder** | Opens the exact folder inside `com.mojang` in Windows File Explorer. |
| **Delete Pack** | Moves the pack folder to the Windows Recycle Bin using the native `trash` pipeline (never permanent unrecoverable deletion by default). |

---

## Multi-Select & Bulk Operations

Need to clean up multiple old packs or export a batch for a friend?
1. Click the **Select Mode** button in the top toolbar.
2. Check the boxes on the packs you want to manage.
3. Choose **Bulk Export** to package selected items into `.mcpack` files, or **Bulk Delete** to remove them safely to the Recycle Bin.

---

## Downgrade Protection

When installing a pack that you already have installed:
- If the incoming pack has a higher version, Bedrock Manager updates it cleanly.
- If the incoming pack has a lower version number than what is currently installed, the app flags the downgrade and asks for confirmation before replacing files.
- You can customize this behavior under **Settings > Installation > Downgrade behavior** (`Ask first` vs. `Allow silently`).
