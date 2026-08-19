# Installation & System Requirements

Bedrock Manager runs natively on Windows 10 and Windows 11 as a standalone desktop application.

---

## System Requirements

| Requirement | Minimum | Recommended |
| :--- | :--- | :--- |
| **Operating System** | Windows 10 (64-bit, build 19041+) | Windows 11 (64-bit) |
| **Architecture** | x64 or ARM64 | x64 or ARM64 |
| **Minecraft Edition** | Minecraft: Bedrock Edition (Windows) | Minecraft: Bedrock Edition (latest retail) |
| **Runtime Dependency** | Microsoft Edge WebView2 (pre-installed on Windows 10/11) | Microsoft Edge WebView2 (Evergreen) |
| **Memory** | 256 MB RAM | 512 MB RAM |
| **Disk Space** | 30 MB for app installation | 500 MB+ (for skin sessions and backups) |

> [!TIP]
> Bedrock Manager works with Minecraft installed through the Microsoft Store or Xbox App. Ensure you have launched Minecraft at least once so the game generates the default `com.mojang` directory structure.

---

## Installing Bedrock Manager

1. Head over to the official download page at [bedrockmanager.app](https://bedrockmanager.app).
2. Choose the installer matching your system architecture:
   - **x64 (Standard Intel / AMD PCs)**: `bedrock-manager-[VERSION]-x64-setup.exe` (~8.9 MB)
   - **ARM64 (Snapdragon / Surface Pro X / ARM devices)**: `bedrock-manager-[VERSION]-arm64-setup.exe` (~8.1 MB)
3. Run the installer. It registers desktop shortcuts, start menu entries, and the `bedrock-manager://` deep-link URL handler.
4. Launch **Bedrock Manager** from the Start Menu or desktop shortcut.

---

## First Launch Verification

When Bedrock Manager opens, check the bottom of the left sidebar:
- If you see a green **"Launch Minecraft"** button or game status indicator, the app has located your Minecraft installation.
- If it indicates Minecraft was not found, verify that Minecraft is installed via the Microsoft Store, or specify your custom directory under **Settings > Directories**.

---

## Updating the Application

Bedrock Manager includes a built-in updater powered by Tauri. When a new version is released:
- A notification banner appears in the top navigation bar.
- You can manually check for updates anytime under **Settings > Updates**.
- Updates download directly and apply cleanly on restart without touching your installed packs, worlds, or skins.
