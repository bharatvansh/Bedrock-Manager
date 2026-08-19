# Common Issues & Solutions

This page addresses common issues encountered when managing packs, worlds, and skins in Minecraft Bedrock Edition.

---

## 1. Windows SmartScreen or Antivirus Warning During Installation

**Symptom**: When running the installer (`.exe`), Windows Defender SmartScreen displays a blue pop-up stating *“Windows protected your PC”* or your antivirus software warns that the app is unrecognized.

**Cause**:
Bedrock Manager is a free, independently developed community tool. Because it is not signed with an expensive enterprise Extended Validation (EV) certificate, Windows SmartScreen treats newly released builds as "unrecognized" until automated download reputation builds up. The application is completely safe and contains zero malware or telemetry.

**Solution**:
1. On the blue **Windows protected your PC** dialog, click the **More info** link.
2. Click the **Run anyway** button that appears at the bottom.
3. If third-party antivirus software blocks or quarantines the file, choose **Allow**, **Restore**, or add an exclusion for the installer.

---

## 2. Minecraft Directory Not Detected

**Symptom**: The sidebar displays *“Minecraft Not Detected”* and packs cannot be installed.

**Solutions**:
1. **Launch Minecraft Once**: If you recently installed Minecraft from the Microsoft Store, launch the game and enter a world once so Minecraft creates the default `games/com.mojang` folders.
2. **Verify Custom Path**: If Minecraft is installed in a non-standard location or preview build, open **Settings > Directories**, click **Browse**, and manually select your `com.mojang` folder.

---

## 3. Pack Fails to Load in Minecraft (Red Incompatible Badge)

**Symptom**: A pack appears in Minecraft's Resource Pack or Behavior Pack menu with a red error indicator stating it is incompatible.

**Causes & Solutions**:
- **Minecraft Version Mismatch (`min_engine_version`)**: The pack requires a newer version of Minecraft than the one currently installed. Check the pack's requirements and update your Minecraft client via the Microsoft Store.
- **Missing Required Dependencies**: Some Behavior Packs require a companion Resource Pack (or specific dependency UUIDs) to function. In Bedrock Manager, navigate to **Add-ons**, click the pack to open the details panel, and verify that all packs listed under **Dependencies** are installed and active.
- **Manifest Formatting Issues**: If an older pack uses malformed JSON or legacy schema fields, re-importing the pack archive (`.mcpack` / `.mcaddon`) through Bedrock Manager will automatically correct common syntax flaws.

---

## 4. World NBT Changes Not Showing in Game

**Symptom**: You modified gamerules or world settings in Bedrock Manager, but the world settings remain unchanged when loading the game.

**Solution**:
- Minecraft caches `level.dat` in memory while the game is active. If you edit world settings while the world or game is running, Minecraft will overwrite your changes upon saving. Always close the game before applying NBT edits in Bedrock Manager.

---

## 5. Custom Skins Not Appearing in the Dressing Room
**Symptom**: You saved a custom skin in Bedrock Manager, but cannot find it in Minecraft.
**Causes & Solutions**:
- **Restart Minecraft**: Minecraft only scans the `skin_packs` directory when the game launches. If Minecraft was open when you saved or imported your skin, fully close and restart Minecraft.
- **Navigate to Classic Skins (Owned Skins)**:
  1. Open Minecraft and click **Dressing Room**.
  2. Select a character slot and choose **Change Classic Skin** (or click the green **Classic Skins / Coat Hanger** icon on the left sidebar).
  3. Under **Owned Skins**, find and expand the **Bedrock Manager Skins** pack.
  4. Select your custom skin and click **Equip**.
- **Ensure the Skin Was Saved**: Open Bedrock Manager's **Skins** studio and confirm your skin appears in your saved list. Saving updates the native skin pack inside `<com.mojang>/skin_packs/Bedrock Manager Skins/`.

---

## 6. Google Drive Cloud Sync Authorization Error

**Symptom**: Connecting Google Drive in **Settings > Cloud & Backup** fails with a redirect error.

**Solution**:
- Ensure your default browser allows local loopback redirects to `bedrock-manager://auth/callback` or `http://127.0.0.1`.
- If an ad-blocker or firewall intercepts the OAuth handshake, temporarily whitelist the application or retry authentication.