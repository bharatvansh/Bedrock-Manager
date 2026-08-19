# Diagnostics & Error Logs

When an unexpected issue or addon installation problem occurs, Bedrock Manager provides built-in diagnostic tools and runtime logging to help identify and resolve the issue.

---

## Addon Installation Diagnostics (Process Log)

Bedrock Manager records all addon, world, and skin pack installation attempts in a local **Process Log** on the Install screen.

### Viewing Install Details & Repairs
1. Navigate to **Install** in the sidebar.
2. Scroll to the **Process Log** section beneath the file drop zone.
3. For any installation card, click **Show Details** (`›`) to view:
   - **Installed Items**: Pack names, internal folder targets, and actions taken (*Installed*, *Updated*, *Downgraded*, or *Reinstalled*), with quick shortcuts to open each target folder.
   - **Repairs Applied**: Automatic corrections performed by the installer, such as extracting embedded `.mcpack` archives or fixing manifest structures.
   - **Needs Attention**: Error messages and issue codes (such as missing pack dependencies, corrupted archives, or Java Edition packs).

### In-App Install Error Reporting
If an add-on fails to install or only installs partially:
1. Locate the failed entry in the **Process Log**.
2. Click the **Report** button on the entry card.
3. Bedrock Manager will automatically sanitize the error payload and submit the pack manifest and failure code directly to the development team for investigation.

> [!NOTE]
> The Process Log retains recent installation history across sessions (configurable up to 200 items in **Settings > Installation**). You can clear this history at any time by clicking the **Clear** button.

---

## Application Runtime & Debug Logs

Bedrock Manager is designed as a lightweight, privacy-first desktop application and **does not write background log files to your hard drive**.

### Terminal / Command Line Output
If you are troubleshooting an unexpected crash, deep link failure, or synchronization issue, you can view live diagnostic output by launching Bedrock Manager from a terminal:

**Windows (PowerShell or Command Prompt):**
```powershell
& "C:\Program Files\Bedrock Manager\Bedrock Manager.exe"
```

**Diagnostic Tags in Output:**
When running in debug mode, standard diagnostic tags stream to `stdout` and `stderr`, including:
- `[dotenv]` — Environment configuration loading status.
- `[migration]` — Legacy data migration traces.
- `[settings]` — Configuration file parsing and schema validation.
- `[InstallReport]` — Network dispatch and response statuses for error reporting.

### Webview Developer Console
To inspect UI rendering errors, client-side exceptions, or network requests:
- In development builds, press <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>I</kbd> (or <kbd>F12</kbd>) to open the webview developer tools and inspect the **Console** tab.

---

## Privacy & Data Sanitization

Bedrock Manager contains **zero background tracking telemetry**. Data is only transmitted when you explicitly use the in-app **Report** button on a failed install or submit feedback via **Settings > About > Send Feedback**.

When an error report is dispatched:
- **Filesystem Paths**: All Windows (`C:\Users\...`), UNC, and Unix home paths are scrubbed and replaced with `<path>` placeholders.
- **Personal Identifiers**: Email addresses are replaced with `<email>`.
- **Credentials & Tokens**: Sensitive auth tokens, secrets, and long hash strings are redacted to `<redacted>`.
- **Source Files**: Raw source archive paths on your machine are never uploaded; only the internal manifest JSON structure required to diagnose the pack issue is sent.

---

## Submitting a Bug Report

If you encounter an issue that cannot be resolved automatically:

1. **Check the Process Log**: Expand the affected item in **Install** to review specific error codes.
2. **Submit In-App**: Use the **Report** button directly on the failed card if available.
3. **Open a GitHub Issue**: Visit [GitHub Issues](https://github.com/bharatvansh/Bedrock-Manager/issues), choose the **Bug Report** template, and provide:
   - Your Bedrock Manager version (found in **Settings > About**).
   - Your Minecraft Bedrock version and Windows platform.
   - The error message or issue description from the Process Log.
4. **Community Support**: Join our [Community Discord](https://discord.gg/Wvst4znsgk) for direct troubleshooting assistance.
