# Quickstart Guide

This 3 minute walkthrough covers the core workflow: installing an addon, creating a profile, attaching it to a world, and launching the game.

---

## Step 1: Install Your First Addon

You can install packs into Bedrock Manager through two methods:

### Method A: Drag and Drop (Fastest)
1. Grab any `.mcpack`, `.mcaddon`, or `.zip` file from your desktop or downloads folder.
2. Drag and drop it directly onto the Bedrock Manager window.
3. The app unpacks the archive, checks the manifest, repairs common formatting issues, and sorts files into `behavior_packs` and `resource_packs`.

### Method B: The Install Page
1. Click **Install** in the left sidebar.
2. Click **Browse Files** to select your pack or drop it in the dashed upload zone.
3. Review the parsed pack name, version, and manifest modules, then click **Complete Install**.

```
  [ .mcaddon Archive ]
           │ (Drag & Drop)
           ▼
  ┌─────────────────────────────────┐
  │      Bedrock Manager Engine     │
  │  - Validates manifest.json      │
  │  - Auto-repairs manifests       │
  │  - Atomic staging in temp dir   │
  └────────┬──────────────┬─────────┘
           │              │
           ▼              ▼
     Resource Pack   Behavior Pack
     (com.mojang)    (com.mojang)
```

---

## Step 2: Organize with an Addon Profile

If you play with multiple packs, profiles let you bundle them into reusable loadouts.

1. Navigate to **Profiles** in the sidebar.
2. Click **+ New Profile**, enter a name (e.g., *Survival Enhancements*), and pick an icon color.
3. Click **Add Packs** and select the resource and behavior packs you want to include.
4. Drag packs up or down to set priority (top packs override packs below them).
5. Click **Save Profile**.

---

## Step 3: Apply to a World or Global Resources

1. In the **Profiles** tab, click **Apply to World** on your newly created profile.
2. Select your target world from the dropdown list.
3. Bedrock Manager writes the pack configuration directly to the world's `world_resource_packs.json` and `world_behavior_packs.json`.

> [!TIP]
> Want a texture pack active everywhere across menus and servers? Click **Apply as Global Resources** on any profile containing resource packs.

---

## Step 4: Launch Minecraft

Click **Launch Minecraft** in the left sidebar. The app triggers the `minecraft://` protocol and tracks process launch state. When Minecraft loads, your world will already have all configured packs activated in the exact priority order you specified.
