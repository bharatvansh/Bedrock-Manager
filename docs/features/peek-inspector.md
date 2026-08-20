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

- **Level-Order (BFS) Traversal**: Scans directories using a breadth-first arena traversal, ensuring critical root files (such as `manifest.json`, `pack_icon.png`, and `pack_icon.tga`) are indexed first before any safety limits are met.
- **Noise & Artifact Filtering**: Automatically filters out build artifacts, version control directories, and OS junk files (including `.git`, `.vscode`, `.idea`, `.DS_Store`, and `Thumbs.db`).
- **Bedrock Folder & File Recognition**: Recognized directories (`textures`, `scripts`, `functions`, `entities`, `models`, `sounds`, `animations`, `subpacks`, `ui`, `pbr`, `fogs`, `biomes`, etc.) and file types (`.json`, `.js`, `.ts`, `.lang`, `.mcfunction`, `.mcstructure`, `.png`, `.tga`, `.ogg`, `.fsb`, `.wem`, etc.) are assigned distinct icons and color highlights.
- **File Metadata & Stats**: Displays formatted file sizes (B, KB, MB), item counts, and consolidated directory stats in the header subtitle.
- **Fast Search & Filter Bar**: Filter files in real time with instant match highlights and a one-click clear (<kbd>✕</kbd>) button.
- **Expand & Collapse All**: Integrated toolbar buttons to expand or collapse all subdirectories in a single click.
- **Open Folder in Explorer**: Click **Open Folder** in the modal header to reveal the pack's root directory in Windows Explorer.
- **Safety Limits**: Scans up to a maximum directory depth of 10 levels and 10,000 files, displaying `showing first 10,000 entries` if a pack exceeds the threshold.

---

## Integrated File Previewers

Selecting any file in the tree opens the right-hand preview pane. Pressing the <kbd>Escape</kbd> key closes the active preview first, and a second press closes the inspector modal.

### 1. Syntax-Highlighted Code & Text Viewer
- **Custom Syntax Highlighting**: Fast client-side tokenizer supporting `.json`, `.js`, `.ts`, `.mcfunction`, `.lang` localization files, `.html`, and `.css`.
- **In-File Search**: Press <kbd>Ctrl</kbd> + <kbd>F</kbd> (or <kbd>Cmd</kbd> + <kbd>F</kbd>) to open the in-file search bar with live match counts and <kbd>Enter</kbd> / <kbd>Shift</kbd> + <kbd>Enter</kbd> navigation.
- **Line Numbers & Metadata**: Full line numbering, line count badge, and detected language indicators.
- **JSON Formatting Toggle**: Format and beautify minified JSON manifests or structure definitions with a single click.
- **Word Wrap & Clipboard Tools**: Quick toggle for word wrapping long lines and a one-click **Copy to Clipboard** button.
- **Safety Cap**: Files exceeding **512 KB** display a `Preview truncated — file is larger than 512 KB` notice.
- **External Editor**: Includes an **Open** button in the header to open the file in your default code editor (e.g. VS Code).

### 2. Waveform Audio Player & SoundBank Inspector
- **Custom Waveform Visualizer**: Interactive audio waveform canvas rendered directly from decoded sound data with hover timestamp seeking.
- **HTTP `206 Partial Content` Range Streaming**: Custom local file streaming protocol enables instant seeking and scrub playback without waiting for complete file buffering.
- **FSB SoundBank & Multi-Stream Playback**: Native decoding of FMOD SoundBanks (`.fsb` and `.wem` FSB5 Vorbis/PCM) via Rust `fsbex`. Includes a stream selector dropdown and previous/next track navigation buttons for multi-track banks.
- **Supported Formats**: `.ogg`, `.mp3`, `.wav`, `.fsb`, and `.wem`.
- **Playback Controls**: Play/pause, interactive scrub bar, elapsed/total duration, loop toggle, and volume slider.

### 3. Image & Texture Viewer
- **Supported Formats**: Native rendering for `.png`, `.jpg`, `.jpeg`, `.gif`, `.webp`, and `.tga` (including `pack_icon.tga` and TGA block/entity textures decoded on-the-fly via Rust).
- **Pixel-Art vs. Smooth Scaling**: Low-resolution in-game textures (< 256×256 px) automatically render with crisp nearest-neighbor pixelated scaling, while high-resolution pack icons and artwork use smooth scaling.
- **Dimension Metadata**: Displays the image's natural dimensions (e.g., `16 × 16 px`, `512 × 512 px`) in the viewer badge.

### 4. Binary & Unsupported Files
- Files containing binary data (automatically detected by null-byte inspection) display a clean fallback view with file size and an **Open** button to launch them in an external program.

---

## Common Use Cases

- **Verify Manifests & Modules**: Review `manifest.json` UUIDs, module definitions, minimum engine versions, and dependencies.
- **Inspect Script Code**: Check TypeScript/JavaScript entry points in `scripts/` before loading an addon into your world.
- **Inspect Custom Functions**: Review `.mcfunction` commands to verify installation and setup instructions.
- **Audit Textures & Audio**: Preview custom sound effects, multi-track FSB soundbanks, and UI textures without needing to launch Minecraft.