# Bedrock File Formats & Manifests

This reference document outlines the core Minecraft: Bedrock Edition file formats, manifest specifications, and how Bedrock Manager parses, repairs, and handles them.

---

## Supported Archive Containers

| Extension | Internal Structure | Target Directory in `com.mojang` |
| :--- | :--- | :--- |
| **`.mcpack`** | Single pack containing `manifest.json` at root. | `resource_packs/`, `behavior_packs/`, or `skin_packs/` depending on module types. |
| **`.mcaddon`** | Multi-pack archive bundling one or more `.mcpack` files or nested pack subfolders. | Dispatched automatically to `behavior_packs/` and `resource_packs/`. |
| **`.mcworld`** | Complete world container containing `level.dat`, `levelname.txt`, `db/` (LevelDB), and optional pack configs. | Extracted into `minecraftWorlds/<generated_folder>/`. |
| **`.mctemplate`** | World template containing `world_template_manifest.json`. | Extracted into `world_templates/` or `minecraftWorlds/`. |
| **`.zip`** | Standard ZIP archive containing packs or worlds. | Auto-detected based on the presence of `manifest.json` or `level.dat`. |

---

## The `manifest.json` Specification

Every Bedrock pack requires a `manifest.json` in its root folder.

### Format Version 2 Example
```json
{
  "format_version": 2,
  "header": {
    "name": "My Custom Addon",
    "description": "Example resource and behavior pack",
    "uuid": "a1b2c3d4-e5f6-7a8b-9c0d-1e2f3a4b5c6d",
    "version": [1, 0, 0],
    "min_engine_version": [1, 20, 0]
  },
  "modules": [
    {
      "type": "resources",
      "uuid": "b2c3d4e5-f6a7-8b9c-0d1e-2f3a4b5c6d7e",
      "version": [1, 0, 0]
    }
  ]
}
```

### Automated Manifest Repair Engine

When an incoming pack contains formatting errors or schema issues, Bedrock Manager automatically diagnoses and resolves them during import:
1. **JSON Cleanup & Sanitization**: Strips UTF-8 Byte Order Marks (`\uFEFF`), cleans up single-line (`//`) and multi-line (`/* */`) comments outside strings, and resolves trailing commas.
2. **Schema & Version Normalization**: Resolves version format mismatches, missing required manifest headers, and schema discrepancies across Bedrock formats.
3. **Data Integrity**: Ensures required module fields and UUID definitions are well-formed before writing files to `com.mojang`.

---

## Bedrock Little-Endian NBT Specification

Bedrock Edition `level.dat` files use a custom Little-Endian Binary Named Binary Tag (NBT) format that differs from Java Edition's Big-Endian NBT format.

### Binary Header Structure

```
Offset (Bytes)    Size      Type               Description
────────────────────────────────────────────────────────────────────────────
0x00 .. 0x03      4 B       i32 (Little-Endian) Storage Version (e.g. 10)
0x04 .. 0x07      4 B       i32 (Little-Endian) NBT Payload Length in Bytes
0x08 .. End       Var       Binary NBT Payload  Root Compound Tag
```

### Tag Identifiers

| Tag ID | Type | Payload Description |
| :---: | :--- | :--- |
| `0x01` | `TAG_Byte` | 1 byte signed integer |
| `0x02` | `TAG_Short` | 2 bytes Little-Endian signed integer |
| `0x03` | `TAG_Int` | 4 bytes Little-Endian signed integer |
| `0x04` | `TAG_Long` | 8 bytes Little-Endian signed integer (64-bit) |
| `0x05` | `TAG_Float` | 4 bytes IEEE 754 floating point |
| `0x06` | `TAG_Double` | 8 bytes IEEE 754 double precision float |
| `0x07` | `TAG_Byte_Array` | 4-byte length prefix followed by raw bytes |
| `0x08` | `TAG_String` | 2-byte UTF-8 length prefix followed by string bytes |
| `0x09` | `TAG_List` | 1-byte element tag ID, 4-byte count, followed by items |
| `0x0A` | `TAG_Compound` | Key-value mapping terminated by `TAG_End` (0x00) |
| `0x0B` | `TAG_Int_Array` | 4-byte count followed by 4-byte integers |
| `0x0C` | `TAG_Long_Array` | 4-byte count followed by 8-byte integers |

Bedrock Manager's Rust parser reads and writes this structure directly, ensuring complete binary compatibility when modifying world settings or gamerules.
