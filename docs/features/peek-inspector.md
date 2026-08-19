# Peek Inside Inspector

The **Peek Inside** inspector is a split-pane file explorer built into Bedrock Manager that allows you to inspect the internal files, scripts, manifests, and assets of any installed pack directly within the app.

---

## Accessing the Inspector

You can launch the inspector from the **Addon Library** (`/addons`):

1. Click any installed pack to open its **Detail Panel**.
2. Click the **Peek Inside** button in the action footer.
3. For **Addon Pairs** (linked Resource and Behavior packs), the panel displays dedicated **Peek RP** and **Peek BP** buttons so you can inspect either pack independently.

> [!NOTE]
> The Peek Inspector operates on packs currently installed on disk in your configured Minecraft directory. Packs that exist only in Cloud Metadata cannot be peeked until installed locally.

---

## File Tree & Directory Navigation

The left pane provides a virtual directory tree of the pack's folder hierarchy with rich visual indicators and navigation tools:

- **Bedrock Folder & File Recognition**: Recognized directories (`textures`, `scripts`, `functions`, `entities`, `models`, `sounds`, `animations`, `subpacks`, `ui`, `pbr`, `fogs`, `biomes`, etc.) and file types (`.json`, `.js`, `.ts`, `.lang`, `.mcfunction`, `.mcstructure`, `.png`, `.ogg`, etc.) are assigned distinct icons and color highlights.
- **File Metadata**: Displays exact formatted file sizes (B, KB, MB) and folder item counts.
- **Fast Search & Filter**: Type in the filter bar to instantly flatten the directory tree into a searchable list of matching files showing their full relative paths.
- **Expand & Collapse All**: Quickly expand or collapse all subdirectories with one click.
- **Open Folder in Explorer**: Click **Open Folder** in the modal header to reveal the pack's root directory in Windows Explorer or your native OS file manager.
- **Safety Limits**: Large packs are scanned up to a maximum directory depth of 10 levels and 3,000 files. If a pack exceeds this limit, an indicator displays `showing first 3,000 entries`.

---

## Integrated File Previewers

Selecting any file in the tree opens the right-hand preview pane. Pressing the <kbd>Escape</kbd> key closes the active preview first, and a second press closes the inspector modal.

### 1. Text & Code Viewer
- Displays raw file contents inside a clean, scrollable text viewer for `.json`, `.js`, `.ts`, `.mcfunction`, `.lang`, `.txt`, and other text-based files.
- Automatically handles UTF-8 text encoding.
- Text files exceeding **512 KB** are safely capped and display a `Preview truncated — file is larger than 512 KB` notice.
- Includes an **Open** button in the header to open the selected file in your system's default code or text editor.

### 2. Audio Player
- Embedded HTML5 audio player supporting `.ogg`, `.mp3`, and `.wav` sound files.
- Streamed directly from disk via the app's secure custom local file protocol.
- Includes playback controls, timeline scrubbing, track duration, and volume adjustment.
- Useful for auditioning custom mob sounds, ambient audio, and music discs.

### 3. Image & Texture Viewer
- Inline rendering for `.png`, `.jpg`, `.jpeg`, `.gif`, and `.webp` image assets.
- Allows immediate visual verification of item icons, block textures, UI sprites, and pack icons.
- If an image format cannot be rendered natively (such as `.tga`), the viewer displays a fallback state with an **Open** button to launch it in your OS image viewer.

### 4. Binary & Unsupported Files
- Files containing binary data (automatically detected by null-byte inspection) display a clean fallback view with file size and an **Open** button to launch them in an external program.

---

## Common Use Cases

- **Verify Manifests & Modules**: Review `manifest.json` UUIDs, module definitions, minimum engine versions, and dependencies.
- **Inspect Script Code**: Check TypeScript/JavaScript entry points in `scripts/` before loading an addon into your world.
- **Inspect Custom Functions**: Review `.mcfunction` commands to verify installation and setup instructions.
- **Audit Textures & Audio**: Preview custom sound effects and UI textures without needing to launch Minecraft.