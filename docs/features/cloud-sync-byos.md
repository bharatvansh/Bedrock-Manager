# Cloud Sync & BYOS Backups

Bedrock Manager provides a **Bring Your Own Storage (BYOS)** backup and synchronization engine. You can back up your worlds, addon collections, custom skins, and development packs directly to your personal cloud storage (Google Drive or Dropbox).

---

## Why BYOS (Bring Your Own Storage)?

Traditional cloud sync services often route your files through proprietary servers or impose monthly subscription fees. 

With BYOS:
- **Zero Third-Party Storage**: Your save data transfers directly between your local PC and your personal cloud provider.
- **Privacy First**: We do not store, inspect, or retain copies of your Minecraft worlds.
- **No File Size Caps**: Backup sizes are limited only by your own cloud storage quota.

---

## Architecture & Storage Format

Bedrock Manager stores backups in a **Transparent Storage Format** within a human-readable folder hierarchy (`BedrockManagerBackups/`) in your cloud storage. Content is packaged into standard, self-contained Minecraft archives:

```
  [ Local Worlds / Packs / Skins ]
                 │
                 ▼
  ┌────────────────────────────────────────────────────────┐
  │                 BYOS Backup Engine                     │
  │  1. Package item into .mcworld, .mcpack, or .png       │
  │  2. Verify modification timestamps and archive hashes  │
  │  3. Upload new or modified archives to cloud hierarchy │
  │  4. Update backup manifest and root README.txt         │
  └──────────────────────────┬─────────────────────────────┘
                             │
                             ▼
  [ Google Drive / Dropbox: BedrockManagerBackups/ ]
  ├── minecraftWorlds/          (.mcworld files)
  ├── resource_packs/           (.mcpack files)
  ├── behavior_packs/           (.mcpack files)
  ├── skins/                    (.png skin files)
  └── backup-manifest.json
```

### Key Technical Properties
- **Transparent Archives**: Backups are standard `.mcworld`, `.mcpack`, and `.png` files that can be downloaded and opened directly in Minecraft without special extraction tools.
- **Human-Readable Hierarchy**: Saves are organized into clean cloud directories mirroring your Minecraft layout, with a generated `README.txt` and `backup-manifest.json` at the root.
- **Hash Verification**: Unchanged items are detected via archive checksums and skipped, avoiding unnecessary bandwidth usage.

---

## Setting Up Cloud Backups

1. Sign in to your Bedrock Manager account, then open **Settings > Cloud & Backup**.
2. Pick a storage provider (Google Drive or Dropbox) and click **Connect**. One provider is active at a time.
3. Complete the standard OAuth2 browser authentication. Your connection is stored encrypted with your account and works across all signed-in devices, while backup files are always sent directly to your provider.
4. Configure your backup preferences:
   - **Inclusions**: Worlds, Resource Packs, Behavior Packs, Custom Skins, and Development Packs.
   - **Triggers**:
     - *Scheduled*: Daily, Weekly, or On Startup.
     - *Manual*: Use **Backup Now** to trigger an instant snapshot at any time.
   - **Saved Backup Points**: Keep the last 5, 10 (recommended), or 15 backup points.
   - **Automatic Pruning**: Older backups are cleaned up automatically to save cloud space.

---

## Recovery Center & Safe Restores

The built-in **Recovery Center** provides an interactive dashboard to inspect, export, or restore backed-up items:

- **Item Inspection**: Browse backed-up items by category (Worlds, Resource Packs, Behavior Packs, Skins), view snapshot history, and check live sync status.
- **Standalone Export**: Export any world, pack, or skin from any historical snapshot directly to disk as a standalone archive (`.mcworld`, `.mcpack`, or `.png`) without overwriting active game files.
- **Granular Conflict Resolution**:
  - *Worlds*: Choose **Restore as Copy** (restores to a new folder with a dated label) or **Overwrite Local** (safely moves the active world to the Windows Recycle Bin before staging the restore).
  - *Packs & Skins*: Overwrite existing files (moving old files to the Recycle Bin) or skip conflicting items.
- **Pre-Restore Rollback Snapshot**: An automatic safety snapshot of your local files is taken immediately before any overwrite operation.
- **Exit Guard**: The application intercepts window close requests while a backup or restore operation is in progress, preventing data corruption from partial writes.
