# Safety & File Integrity

Because Bedrock Manager directly manipulates game saves, manifests, and archives, several automated safety systems protect against data loss, corrupt writes, and malicious archive payloads.

---

## 1. Zip-Bomb & Path Traversal Protection

When extracting untrusted `.mcaddon`, `.mcpack`, or `.zip` archives from third-party websites, the decompression engine (`addon_installer.rs`) enforces strict bounds:

- **Entry Count Limit**: Maximum 100,000 files per archive.
- **Single File Size Limit**: Maximum 256 MB per uncompressed entry.
- **Total Archive Limit**: Maximum 4 GB cumulative uncompressed size.
- **Path Sanitization**: Rejects any archive entry attempting directory traversal (`../` or `..\`), absolute paths (`/` or `\`), or Windows drive prefixes (`C:`).

---

## 2. Atomic Stage-and-Swap Extractions

Partial archive extractions (caused by a sudden system crash, power cut, or disk full error) can leave a pack in a broken state that crashes Minecraft upon load.

To prevent this:
1. Archives are unpacked into an isolated temporary folder (`.tmp_<uuid>`) on the same disk volume.
2. The manifest and file structures are verified for integrity.
3. The temporary folder is swapped into the destination path using an **atomic filesystem rename** (`std::fs::rename`).
4. If an extraction fails at any step, the temporary directory is cleaned up, leaving your existing library untouched.

---

## 3. Safe Deletion via Recycle Bin

When deleting packs, worlds, or skins from Bedrock Manager:
- The app utilizes the native Windows `trash` crate to move items directly to the **Windows Recycle Bin**.
- Items are never permanently erased by default, allowing you to restore accidentally deleted content directly from your desktop Recycle Bin.

---

## 4. World Save Safety & Dual NBT Writes

When modifying world gamerules or editing NBT:
- Bedrock Manager checks whether `Minecraft.Windows.exe` is currently running. If the game is open, you are prompted to save and exit to avoid write conflicts.
- Both `level.dat` and `level.dat_old` are updated simultaneously with identical byte payloads. If Minecraft detects a mismatch or partial write during startup, it automatically recovers from `level.dat_old`.
