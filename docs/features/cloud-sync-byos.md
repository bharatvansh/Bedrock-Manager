# Cloud Sync & BYOS Backups

Bedrock Manager provides a **Bring Your Own Storage (BYOS)** backup and synchronization engine. You can back up your worlds, addon collections, and profile configurations directly to your own Google Drive or Microsoft OneDrive(soon) account.

---

## Why BYOS (Bring Your Own Storage)?

Traditional cloud sync services often route your files through proprietary servers or impose monthly subscription fees. 

With BYOS:
- **Zero Third-Party Storage**: Your save data transfers directly between your local PC and your personal cloud provider.
- **Privacy First**: We do not store, inspect, or retain copies of your Minecraft worlds.
- **No File Size Caps**: Backup sizes are limited only by your own cloud storage quota.

---

## Architecture & Storage Format

The backup engine (`byos_backup.rs`) uses a content-addressed storage architecture designed for speed and minimal bandwidth:

```
  [ Local World / Packs ]
              │
              ▼
  ┌────────────────────────────────────────────────────────┐
  │                 BYOS Backup Engine                     │
  │  1. Compute SHA-256 hash for every file                │
  │  2. Check existing hashes against remote blob index    │
  │  3. Pack only new/modified files into 32 MB chunk packs│
  │  4. Upload snapshot manifest referencing blob hashes   │
  └──────────────────────────┬─────────────────────────────┘
                             │
                             ▼
              [ Google Drive / OneDrive ]
```

### Key Technical Properties
- **Content-Addressed Blobs**: If 5 different worlds use the exact same resource pack, that pack is uploaded only once.
- **Delta Uploads**: Subsequent world backups upload only changed LevelDB chunk files, making backup updates quick.
- **32 MB Chunk Packaging**: Small files are aggregated into balanced 32 MB archive chunks to stay within cloud provider API rate limits.

---

## Setting Up Cloud Backups

1. Open **Settings > Cloud & Backup**.
2. Click **Connect Google Drive** (or OneDrive).
3. Complete the standard OAuth2 browser authentication. The app securely stores access tokens locally using PKCE.
4. Configure your backup preferences:
   - **Inclusions**: Worlds, Resource Packs, Behavior Packs, Custom Skins.
   - **Schedule**: Manual only, On Startup, Daily, or Weekly.
   - **Retention Limit**: Keep the last *N* snapshots (older snapshots are automatically pruned).

---

## Restoring Backups Safely

Accidentally corrupting an active world during a restore is a real risk with standard file copying. Bedrock Manager mitigates this with a strict multi-step restore sequence:

1. **Diff Preview**: Before restoring, the app computes a detailed preview showing which files will be added, modified, or removed.
2. **Pre-Restore Rollback Snapshot**: An automatic local safety snapshot of your existing world is taken immediately before any files are overwritten.
3. **Atomic Swap**: Restored files are reconstructed in a staging area and swapped in atomically. If an error occurs, the pre-restore snapshot is restored instantly.
