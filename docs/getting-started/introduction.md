# Introduction

**Bedrock Manager** is a desktop application built specifically for managing content in Minecraft: Bedrock Edition on Windows. It streamlines installing mods, managing resource and behavior packs, editing world settings directly via NBT, creating custom skins, and backing up save files.

---

## Why Bedrock Manager?

Managing Minecraft Bedrock content on Windows has traditionally been messy. Files live deep inside hidden AppData folders (`com.mojang`), manifests break when creators use newer or older format versions, and enabling multiple packs across different worlds requires repetitive manual setup in-game.

Bedrock Manager solves these problems by providing a unified, offline first dashboard that interacts directly with your local game files.

### Key Highlights

- **Offline-first Architecture**: Built on Tauri v2 and Rust for fast startup times, low RAM usage (~40–80 MB), and zero background telemetry.
- **Automatic Manifest Repair**: Automatically fixes common manifest problems, syntax errors, and schema inconsistencies so broken addons load properly.
- **Live World NBT Editing**: Edit `level.dat` gamerules, switch game modes, adjust spawn coordinates, and manage gameplay mechanics and cycle settings.
- **Real-time 3D Skin Studio**: Paint skins in both 2D and 3D viewports with live layer toggles, automatic 64×32 to 64×64 texture padding, and direct export into game dressing rooms.
- **BYOS Cloud Backup**: Back up worlds and addons to your own Google Drive storage using deduplicated chunking and pre-restore rollback protection.

---

## How It Works

Bedrock Manager communicates directly with your Windows Minecraft installation through local filesystem hooks:

1. **Path Resolution**: The app automatically detects standard Microsoft Store (UWP/GDK) install paths (`com.mojang`), as well as custom directories configured in Settings.
2. **Atomic Installation Pipeline**: When you import an archive (`.mcpack`, `.mcaddon`, `.zip`), the Rust backend stages files in a temporary sibling directory, validates the manifest structure, repairs known compatibility issues, and executes an atomic directory swap.
3. **World Configuration**: World pack associations (`world_resource_packs.json` and `world_behavior_packs.json`) are parsed and written directly, allowing you to configure pack priorities outside of Minecraft.

---

## Community & Open Documentation

While the Bedrock Manager desktop application itself is closed source and distributed as a free community utility, this repository hosts the public documentation, issue tracker, format specifications, and release notes.

- **Website & Downloads**: [https://bedrockmanager.app](https://bedrockmanager.app)
- **Discord Community**: [https://discord.gg/Wvst4znsgk](https://discord.gg/Wvst4znsgk)
- **Bug Tracker & Feature Requests**: [GitHub Issues](https://github.com/bharatvansh/Bedrock-Manager/issues)
