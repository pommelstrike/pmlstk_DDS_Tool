# Pommelstrike's DDS Tool (2025 Edition)

[![Demo Video - Full Workflow](https://img.youtube.com/vi/lV8tg81ZVs8/maxresdefault.jpg)](https://youtu.be/lV8tg81ZVs8?si=VgLyAFkKrhgFpEg8)  
[![Blender 4.1.1+](https://img.shields.io/badge/Blender-4.1.1%2B-blue.svg)](https://www.blender.org/)  
[![Addon Version](https://img.shields.io/badge/Version-3.6.48-brightgreen.svg)](https://github.com/pommelstrike/pmlstk_DDS_Tool/releases)  
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

**The most powerful, up-to-date, and user-friendly DDS workflow tool for Baldur's Gate 3 modding in Blender.**

Now with:
- **UNREAL ENGINE SWIZZLER** (one-click conversion of _orm / _arm / _m / _d / _n / _gm)
- **Compose DDS** now supports _Albedo → _BM, _Normal → _NM, _Physical → _PM
- **DDC – Document Channel Compose** (auto-pack loose channels from Substance Painter, Sketchfab, FAB, etc.)
- Full alpha decomposition for _PM
- Automatic OpenGL/DirectX normal map detection & fix
- Detailed report.txt with compression metadata
- Adjustable Metallic / Roughness / AO multipliers

### Support the Tool (Free to join!)
Your support keeps this tool alive and constantly updated.

- [Patreon (free to join – most updates posted here)](https://www.patreon.com/pommelstrike)
- [Ko-fi](https://ko-fi.com/pommelstrike)
- [Linktree – All Links & Commissions](https://linktr.ee/pommelstrike)

## Quick Reference – Which Button Do You Need?

| Your textures are…                                                  | → Use this button                     |
|---------------------------------------------------------------------|---------------------------------------|
| Already use BG3 suffixes **or** common alternatives (_Albedo, _Normal, _Physical, etc.) | **Compose DDS**                       |
| Unreal Engine packed textures (_orm, _arm, _m, _d, _n, _gm)          | **UNREAL ENGINE SWIZZLER**            |
| Separate channel files (Substance, Sketchfab, FAB, etc.)            | **DDC – Document Channel Compose**    |

Full detailed suffix reference → [**Wiki Page – Texture Processing Reference**](https://github.com/pommelstrike/pmlstk_DDS_Tool/wiki/Texture-Processing-Reference)

## Features Overview

- **Decompose DDS → TGA**  
  Splits any BG3 DDS into editable grayscale TGA channels with perfect naming.  
  Now includes **_PM alpha channel** and writes full compression metadata to `report.txt`.
  [Details on the wiki Compose Page](https://github.com/pommelstrike/pmlstk_DDS_Tool/wiki/Decompose-DDS-Reference)

- **Three independent composition paths**  
  1. **Compose DDS** – fastest single-file conversion (supports BG3 suffixes + _Albedo / _Normal / _Physical)  
  2. **UNREAL ENGINE SWIZZLER** – dedicated Unreal → BG3 conversion with swizzling + multipliers  
  3. **DDC – Document Channel Compose** – auto-combines loose channels (e.g. Metallic + Roughness + AO → _PM.DDS)

- **Smart Normal Map Handling**  
  Automatic OpenGL/DirectX detection with green-channel inversion when needed. Works in all three composition paths.

- **Adjustable Multipliers**  
  Metallic ×?, Roughness ×?, AO ×? – fine-tune your PBR values before export.

- **texconv-powered compression**  
  Correct BC1 / BC3 / BC4 per suffix. Outputs always uppercase `.DDS`.

- **Clean versioned output folders**  
  Never overwrites your work – creates `split-output_V1`, `orm_to_pm_output_V3`, etc.

## Installation

1. Download the latest release:  
   → [**pommelstrike_dds_tool.zip**](https://github.com/pommelstrike/pmlstk_DDS_Tool/releases/latest)

2. In Blender:  
   `Edit → Preferences → Add-ons → Install...` → select ZIP → enable the addon

3. (Optional) Set your texconv path – defaults to BG3 Toolkit location  
   If missing: download from [DirectXTex releases](https://github.com/microsoft/DirectXTex/releases)

## Usage – 30-Second Workflows

### 1. Decompose DDS files
- Set **Decompose Folder** → click **Decompose DDS Channels to TGA**  
  → Outputs go to `split-output_VX` with full `report.txt`

### 2. Fastest path – you already have correct suffixes (or _Albedo/_Normal/_Physical)
- Put files in a folder → set **Compose Folder** → click **Compose DDS**  
  Done. Fastest option.

### 3. Coming from Unreal Engine
- Put your _orm / _arm / _m / _d / _n / _gm files in a folder  
- Set **Compose Folder** → click **UNREAL ENGINE SWIZZLER**  
  Adjust multipliers if desired → perfect BG3 DDS files

### 4. Loose channels from Substance Painter / Sketchfab / FAB
- Put all channel files in one folder (any naming the tool recognizes)  
- Click **DDC – Document Channel Compose**  
  → Automatically creates _BM, _NM, _PM, _GM as needed

## Panel Location

Properties Editor → Texture or Material tab → **Pommelstrike DDS COMPOSE/DECOMPOSE TOOL**

(Also appears in Material properties – same panel)

## Known Issues / Tips

- Always check the **System Console** (button in panel) for detailed logs
- Use uppercase `.DDS` output – that's what BG3 expects
- Verify results with DDS viewers (e.g. Windows Texture Viewer or NVIDIA Texture Tools)

## Changelog Highlights (3.6.48 – Nov 2025)

- Added full alpha decomposition for _PM.DDS
- Added detailed DDS header parsing → `report.txt` now shows format, resolution, mipmaps
- Compose DDS now supports _Albedo → _BM, _Normal → _NM, _Physical → _PM
- UNREAL ENGINE SWIZZLER button renamed and improved
- DDC vastly improved channel recognition
- Normal map auto-detection refined
- Versioned output folders for all operations

## Support

Found a bug or want a new feature?  
→ [Open an issue](https://github.com/pommelstrike/pmlstk_DDS_Tool/issues)

Questions? Ask in the comments on Patreon or in the LARIAN BG3 Modding Discord (I’m usually around).

## License

MIT License – free to use, modify, and distribute.

---

**Last Updated: November 28, 2025**

Thank you for using the tool –  ✨
