# Paths & Minecraft Detection

This page describes how Bedrock Manager locates Minecraft game directories, detects running game instances, and launches the game.

---

## Minecraft Data Directory Paths (`com.mojang`)

Minecraft Bedrock Edition on Windows stores its runtime data inside the `com.mojang` directory. The location can vary depending on whether the game is running under the newer GDK packaging or traditional UWP packaging:

| Packaging Type | Default Directory Location |
| :--- | :--- |
| **Primary (GDK / Modern Store)** | `%APPDATA%\Minecraft Bedrock\Users\Shared\games\com.mojang` |
| **Legacy Fallback (UWP Package)** | `%LOCALAPPDATA%\Packages\Microsoft.MinecraftUWP_8wekyb3d8bbwe\LocalState\games\com.mojang` |

### Key Subdirectories inside `com.mojang`

```
com.mojang/
├── behavior_packs/           # Installed behavior pack folders
├── resource_packs/           # Installed resource pack folders
├── skin_packs/               # Custom & app-generated skin packs
├── minecraftWorlds/          # Save folders for local worlds
├── development_behavior_packs/ # Unpacked behavior packs under active development
├── development_resource_packs/ # Unpacked resource packs under active development
├── development_skin_packs/     # Unpacked skin packs under active development
└── world_templates/          # Installed world templates
```

---

## App Data & Session Storage

Bedrock Manager stores its own internal configuration, cache, and session files in:
```
%APPDATA%\Bedrock Manager\
├── config.json               # App preferences and settings
├── skin_editor_sessions/     # Autosaved skin canvas states and undo stacks
├── blob_cache/               # BYOS local content-addressed hash cache
└── logs/                     # Application diagnostic and install logs
```

---

## Process Detection & Game Launching

Bedrock Manager uses a non-intrusive detection pipeline to monitor Minecraft's runtime state:

1. **Registry Verification**: Inspects `HKCU\Software\Classes\Local Settings\Software\Microsoft\Windows\CurrentVersion\AppModel\Repository\Packages` for the registered `Microsoft.MinecraftUWP` package family.
2. **Process Polling**: Checks for active `Minecraft.Windows.exe` process instances using lightweight system queries (cached at 30-second intervals during idle).
3. **Launch Execution**: Launches the game using the registered Windows `minecraft:` URI scheme. When a launch is requested, the app enters a burst polling mode (2 second intervals for 20 seconds) to verify successful startup before returning to idle.
