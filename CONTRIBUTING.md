# Contributing to Bedrock Manager Documentation

Thank you for your interest in improving the Bedrock Manager documentation!

---

## What Can You Contribute?

Community contributions across documentation, guides, format specifications, and issue tracking are warmly welcomed:

1. **Fixing Typos & Documentation Errors**: Improving clarity, fixing grammatical issues, or updating outdated descriptions.
2. **Writing Tutorials & Guides**: Adding practical guides for addon creators, skin artists, and server admins.
3. **Format Specifications**: Expanding documentation on Bedrock `manifest.json` schemas, Little-Endian NBT structures, and addon packaging.
4. **Filing Bug Reports & Feature Requests**: Helping troubleshoot and resolve issues you encounter, sharing reproduction steps or logs, and suggesting new features you'd like to see in the app.

---

## Documentation & Markdown Workflow

The documentation is written in standard [GitHub-Flavored Markdown (GFM)](https://github.github.com/gfm/). No Node.js or static site builder dependencies are required.

```bash
# 1. Fork and clone the repository
git clone https://github.com/<your-username>/Bedrock-Manager.git
cd Bedrock-Manager

# 2. Create a feature branch for your edits
git checkout -b docs/my-documentation-update
```

### Previewing Markdown

You can preview markdown files using any of the following methods:
- **VS Code / Editor Previews**: Use your editor's built-in Markdown preview (e.g. `Ctrl+Shift+V` / `Cmd+Shift+V` or `Ctrl+K V` in VS Code).
- **GitHub Web Interface**: Use the GitHub web editor or pull request preview to inspect rendered Markdown directly.
- **CLI / Markdown Viewers**: Any standard Markdown viewer or extension supporting GitHub-Flavored Markdown (GFM).

---

## Writing Guidelines

- **Language & Clarity**: All documentation must be in clear, concise English. If English is not your primary language, please translate and review your text using online translation tools before submitting.
- **Accurate Technical Terms**: Use correct Minecraft Bedrock terminology (`com.mojang`, `resource_packs`, `behavior_packs`, `level.dat`, `format_version`, UUIDs).
- **Code & File Links**: Ensure all relative Markdown links are valid and code snippets use appropriate language highlighters (`json`, `rust`, `ts`, `bash`, `powershell`).
