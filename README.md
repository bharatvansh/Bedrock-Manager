<div align="center">

# Bedrock Manager

**The desktop management suite for Minecraft Bedrock Edition on Windows.**

[![Release](https://img.shields.io/badge/Release-v1.7.5-emerald?style=flat-square)](https://bedrockmanager.app/changelog.html)
[![Platform](https://img.shields.io/badge/Platform-Windows%2010%20%7C%2011-blue?style=flat-square)](https://bedrockmanager.app)
[![Architecture](https://img.shields.io/badge/Architecture-x64%20%7C%20ARM64-purple?style=flat-square)](https://bedrockmanager.app)
[![Documentation](https://img.shields.io/badge/Docs-Markdown-10b981?style=flat-square)](./docs/index.md)
[![Discord](https://img.shields.io/badge/Discord-Community-5865F2?style=flat-square&logo=discord&logoColor=white)](https://discord.gg/Wvst4znsgk)
[![Ko-fi](https://img.shields.io/badge/Ko--fi-Support-FF5E5B?style=flat-square&logo=kofi&logoColor=white)](https://ko-fi.com/modmcpe)

[Official Website](https://bedrockmanager.app) • [Documentation Portal](./docs/index.md) • [Download Installer](https://bedrockmanager.app) • [Community Discord](https://discord.gg/Wvst4znsgk) • [Support on Ko-fi](https://ko-fi.com/modmcpe) • [Report an Issue](https://github.com/bharatvansh/Bedrock-Manager/issues)

</div>

---

## Overview

**Bedrock Manager** is an offline-first desktop application designed to simplify managing Minecraft Bedrock content on Windows. It streamlines installing addons, organizing resource and behavior packs into reusable loadouts, modifying world gamerules and NBT data directly, designing skins in 2D and 3D, and performing cloud backups without touching hidden `com.mojang` folders manually.

The core desktop application is built with **Tauri v2 + Rust** and a **React 19 + TypeScript** frontend, delivering an installer under 10 MB, cold startup in milliseconds, and zero background telemetry.

---

## Key Capabilities

### 📦 Smart Add-on & Pack Management
- **Drag-and-Drop Installation**: Drop `.mcaddon`, `.mcpack`, or `.zip` archives directly into the app.
- **Manifest Auto Repair**: Automatically detects and resolves common schema errors, syntax issues, and compatibility conflicts in pack manifests.
- **Smart RP/BP Pairing**: Automatically links resource and behavior pack dependencies into clean, single card addons.
- **Recycle Bin Safe Deletion**: Deletions move files safely to the Windows Recycle Bin rather than permanently deleting them.

### 🔍 "Peek Inside" Archive Inspector
- Dual pane virtual explorer for examining archive contents before or after installation.
- Syntax highlighted code viewer for JSON manifests, TypeScript/JavaScript scripts, `.mcfunction`, and `.lang` localization files.
- Built-in audio player for `.ogg`, `.wav`, and `.mp3` sound files with scrubbing and volume control.
- High resolution texture and sprite viewer.

### 🗺️ World Management & Live NBT Editor
- **Direct `level.dat` Editing**: Modify gamerules (`keepInventory`, `mobGriefing`, `doFireTick`, etc.), game modes, difficulty, and custom seeds.
- **Active World Pack Management**: Link, prioritize, and manage resource and behavior packs assigned to individual worlds.
- **Atomic Safety**: Simultaneous updates to `level.dat` and `level.dat_old` prevent corruption from partial writes.

### 🎨 2D & 3D Skin Studio
- **3D Real-Time Viewport**: Hardware-accelerated 3D model painting powered by `skinview3d`.
- **Layer & Limb Toggles**: Hide individual body parts (arms, legs, head, torso) to paint obscured inner surfaces, and toggle outer overlay layers independently.
- **Animation Modes**: Preview skins under Idle, Walk, Run, Wave, and 360-degree rotation states.
- **Automatic Game Integration**: Generates and manages a native skin pack in `skin_packs/Bedrock Manager Skins` so custom skins appear directly in the in-game dressing room.

### 📑 Modular Addon Profiles
- Create custom pack loadouts (e.g. *Survival Enhancements*, *Shader Loadout*, *Multiplayer Clean*).
- Drag and reorder pack priority to control texture and behavior overrides.
- Apply profiles to any world or set them as Global Resources with a single click.

### ☁️ BYOS (Bring Your Own Storage) Cloud Backups
- Securely back up worlds and addons to your own Google Drive or Microsoft OneDrive (soon) account using OAuth2 with PKCE.
- **Content-Addressed Deduplication**: Identical pack files are hashed (SHA-256) and uploaded only once across all worlds.
- **Safe Delta Snapshots**: Fast incremental backups that only upload modified LevelDB chunks.
- **Pre-Restore Rollbacks**: Automatically creates a local safety snapshot before any restore operation.

---

## Documentation

Full technical documentation, user guides, format references, and troubleshooting workflows are available in our documentation hub:

👉 **[Read the Documentation](./docs/index.md)**

### Documentation Sitemap
- [Getting Started & Installation](./docs/getting-started/installation.md)
- [Quickstart 3-Minute Guide](./docs/getting-started/quickstart.md)
- [Add-on & Pack Management](./docs/features/addon-management.md)
- [Peek Inside Inspector](./docs/features/peek-inspector.md)
- [Worlds & Live NBT Editor](./docs/features/worlds-and-nbt.md)
- [Add-on Profiles & Loadouts](./docs/features/addon-profiles.md)
- [2D & 3D Skin Studio](./docs/features/skin-studio.md)
- [Procedural Icon Generator](./docs/features/icon-generator.md)
- [Marketplace Browser](./docs/features/marketplace.md)
- [BYOS Cloud Backups](./docs/features/cloud-sync-byos.md)
- [Bedrock File Formats & Manifests](./docs/advanced/file-formats.md)
- [Common Issues & Troubleshooting](./docs/troubleshooting/common-issues.md)
- [Version Changelog](https://bedrockmanager.app/changelog)

---

## Repository Purpose & Closed-Source Disclosure

The **Bedrock Manager** desktop application is distributed as a free community utility. This public repository serves as the:
1. **Official Documentation Portal**: Source files and technical guides for the Bedrock Manager documentation.
2. **Public Issue & Bug Tracker**: Community space for filing bug reports, requesting features, and tracking release milestones.
3. **Format & Technical Reference**: Open reference for Minecraft Bedrock manifest requirements, NBT schemas, and file structures.

---

## Community & Links

- **Official Website**: [https://bedrockmanager.app](https://bedrockmanager.app)
- **Discord Server**: [https://discord.gg/Wvst4znsgk](https://discord.gg/Wvst4znsgk)
- **YouTube Channel**: [@official-satellite](https://youtube.com/@official-satellite)
- **Support & Donations**: [Ko-fi (Mod MCPE)](https://ko-fi.com/modmcpe)
- **Issue Tracker**: [GitHub Issues](https://github.com/bharatvansh/Bedrock-Manager/issues)
- **Email Contact**: `admin@bedrockmanager.app`

---

## Credits & Creators

Built by **Mod MCPE** & **Blue Print** for the Minecraft Bedrock community:

- **Mod MCPE**: [CurseForge Profile](https://www.curseforge.com/members/mod_mc) • [Ko-fi](https://ko-fi.com/modmcpe)
- **Blue Print**: [CurseForge Profile](https://www.curseforge.com/members/blue_print)

### License

- Documentation & Guides: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
- Desktop Application: Closed source / Free Community Distribution.
