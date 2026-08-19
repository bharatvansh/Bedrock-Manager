# Worlds & Level Settings

The **Worlds** page (`/worlds`) provides deep inspection, addon pack management, world creation, and structured `level.dat` NBT settings editing for your Minecraft Bedrock worlds.

---

## World Library & Dashboard

The Worlds dashboard organizes all locally discovered Minecraft Bedrock worlds with live metadata:

- **World Name**: Rendered with full Minecraft formatting code support (`§a`, `§l`, `§c`, etc.) and instant inline renaming.
- **Thumbnail & Visuals**: Displays `world_icon.jpeg` thumbnails with dynamic blurred background styling.
- **Quick Stats Bar**: Shows total world count and cumulative storage size across all profiles.
- **Card Metadata**: Displays game mode badge, difficulty, in-game days played, active resource/behavior pack counts, disk size, and last modified date.
- **Cloud Protection**: Displays the BYOS backup shield indicator when a world is protected in your cloud backup storage.
- **Search & Sort**: Filter worlds by name or sort by Last Played, File Size, and Alphabetical order.
- **Multi-Select & Bulk Actions**: Batch select multiple worlds to perform bulk `.mcworld` exports or bulk deletion.

---

## World Actions

Selecting any world opens the slide-over detail panel with the following actions:

| Action | Description |
| :--- | :--- |
| **Inline Rename** | Renames the world synchronously in both `levelname.txt` and the `level.dat` NBT `LevelName` tag with character and length validation. |
| **Export .mcworld** | Packages the complete world folder and automatically bundles referenced resource and behavior packs into a ready-to-share `.mcworld` archive. |
| **Open Folder** | Opens the world's storage directory in Windows File Explorer. |
| **Manage World Packs** | Opens the pack picker to link or unlink installed Resource Packs, Behavior Packs, and paired Addon bundles. |
| **Delete World** | Safely deletes the world directory to the Windows Recycle Bin. |

---

## World Creation Wizard

Bedrock Manager allows creating new worlds directly from the app without launching Minecraft:

1. **Template Discovery**: Scans your active profile's `minecraftWorlds` folder for a clean, vanilla template world to use as a base.
2. **Configurable Settings**:
   - **World Name & Seed**: Custom name and text/numeric seed (automatically converted into 64-bit NBT long integers).
   - **World Type**: Infinite, Flat, or Old generation types.
   - **Game Mode & Difficulty**: Survival, Creative, Adventure, or Spectator mode; Peaceful to Hard difficulty.
   - **Starter Options**: Toggle Cheats, Show Coordinates, Start with Map, and Bonus Chest.
3. **Automatic Sanitization**: Cleans experimental flags, resets player timestamps, and prepares LevelDB storage before saving.

---

## World Settings & Gamerule Editor

Bedrock Manager parses Bedrock Little-Endian NBT payloads directly, exposing curated gameplay rules and world flags:

### 1. General World Settings
- **Game Mode**: Switch between Survival (`0`), Creative (`1`), and Adventure (`2`).
- **Difficulty**: Switch between Peaceful (`0`), Easy (`1`), Normal (`2`), and Hard (`3`).
- **Require Resource Packs**: Toggle `texturePacksRequired` to force connecting players to download world resource packs.
- **World Spawn Location**: Directly configure `SpawnX`, `SpawnY`, and `SpawnZ` coordinates.

### 2. Game Rules (12 Standard Toggles)
Toggle rules instantly with automatic save:
- **Player & Gameplay**: Show Coordinates (`showcoordinates`), Immediate Respawn (`doimmediaterespawn`).
- **Combat & Damage**: Friendly Fire / PVP (`pvp`), Fall Damage (`falldamage`), Fire Damage (`firedamage`), Drowning Damage (`drowningdamage`).
- **World & Environment**: Fire Spreads (`dofiretick`), TNT Explodes (`tntexplodes`), Mob Loot (`domobloot`), Natural Regeneration (`naturalregeneration`), Tile Drops (`dotiledrops`), Respawn Blocks Explode (`respawnblocksexplode`).

### 3. Cheats & Advanced Controls (10 Settings)
When **Cheats** (`commandsEnabled` & `cheatsEnabled`) is enabled:
- **Environment & Cycles**: Daylight Cycle (`dodaylightcycle`), Weather Cycle (`doweathercycle`), Mob Spawning (`domobspawning`), Mob Griefing (`mobgriefing`), Entity Drops (`doentitydrops`).
- **Gameplay & Commands**: Keep Inventory (`keepinventory`), Command Blocks (`commandblocksenabled`), Minecraft Education Features (`educationFeaturesEnabled`).
- **Advanced Parameters**: Random Tick Speed (`randomtickspeed`) with numeric validation (0–4096).

### 4. Achievement Tracking & Warnings
- **Achievement Status**: Displays whether Xbox achievements are enabled, locked, or unknown based on the `hasBeenLoadedInCreative` marker.
- **Safety Warnings**: Warns users prior to saving changes if switching to Creative mode or enabling Cheats will permanently disable achievements on that world.

---

## Technical Details Disclosure

For addon creators and power users, the **Technical Details** section exposes deep world metadata:
- **World Seed**: Displays full 64-bit seed with one click clipboard copy.
- **World Generator**: Generator type (Infinite, Flat, Old).
- **Folder UUID / Directory Name**: Underlying folder hash with copy button.
- **Version Metadata**: Target game version (`lastOpenedWithVersion`) and base game version (`baseGameVersion`).
- **Active Experiments Count**: Total active creator experiments stored in the `experiments` compound.
- **Playtime & Time**: Total in game days and calculated world age derived from world ticks (`Time`).

---

## Save Safety & Atomic Writes

To prevent world corruption during save operations, Bedrock Manager employs a two-tier write safeguard:

1. **Dual-File Sync**: Simultaneously updates both `level.dat` and `level.dat_old` with identical Little-Endian binary payloads so Bedrock's automatic recovery mechanism does not revert your settings.
2. **Atomic Temp Swapping**: Writes the NBT payload to a temporary file (`.tmp`), flushes data to physical disk (`sync_all`), and atomically renames over the target file, ensuring power loss or IO interruption cannot leave behind a truncated file.