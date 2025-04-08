# Pommelstrike's DDS Channel Splitter Addon

![Blender Addon](https://img.shields.io/badge/Blender-3.0%2B-blue)
![Version](https://img.shields.io/badge/version-1.1.3-green)

## Overview

**Pommelstrike's DDS Channel Splitter** is a Blender addon designed to batch-decompose DirectDraw Surface (DDS) textures into individual greyscale TGA files. It supports custom naming conventions and special handling for normal maps (`*_NM`), packed maps (`*_PM`), and mask maps (`*_BM`). A progress bar and status reports help you monitor long-running operations.

## Features

- **Batch Processing**: Automatically scan a folder of `.dds` files and process them all.  
- **Custom Naming**: Outputs follow your specified naming scheme for various texture types.  
- **Special Map Support**:  
  - **Normal Maps (`*_NM`)**: Exports R, G, B, A channels to `Nrm_R.tga`, `Nrm_G.tga`, `Nrm_B.tga`, `Nrm_A.tga`.  
  - **Packed Maps (`*_PM`)**: Exports Red → `PM_R_Metallic.tga`, Green → `PM_G_Roughness.tga`, Blue → `PM_B_Ambient_Occlusion.tga`.  
  - **Mask Maps (`*_BM`)**: Exports Alpha → `BM_A_Opacity.tga`.  
- **Standard Mappings**: Handles suffixes `HMVY`, `CLEA`, `MSK` with pre-defined names.  
- **Progress Feedback**: Blender’s progress bar appears in the status bar and detailed messages appear in the **Info** area. Ensure the status bar is visible and expand the Info region (Window → Toggle System Console on Windows) if needed.  
- **Easy Installation**: Single Python file—no external dependencies.  

## Requirements

- **Blender 3.0 or newer**

## Installation

1. [Download](https://github.com/pommelstrike/pmlstk_DDS_tex_split/blob/main/pommelstrike_DDS_Splitter.zip) or clone this repository.  https://github.com/pommelstrike/pmlstk_DDS_tex_split/blob/main/pommelstrike_DDS_Splitter.zip
2. Open Blender and go to **Edit → Preferences → Add-ons**.  
3. Click **Install...** and navigate to `dds_channel_splitter.py`.  
4. Enable **Pommelstrike's DDS Channel Splitter** in the add-on list.  

## Usage

1. Switch to the **Image Editor** workspace.  
2. Press **N** to open the sidebar.  
3. Select the **Pommelstrike DDS Decompose Split** tab.  
4. In **DDS Folder**, browse and select the directory containing your `.dds` files.  
5. Click **Split Channels**.  
6. Monitor the **status bar** at the bottom of Blender for the progress bar, and check the **Info** area (Window → Toggle System Console) for detailed reports.  
7. The addon will create a `split-output` subfolder in the selected directory and populate it with your greyscale TGAs.  

## File Handling Logic

1. **Filename Parsing**: The addon looks at the last underscore-separated segment of each filename (e.g. `texture_NM.dds` → `NM`).  
2. **Armor Textures**:  
   - **NM** (`*_NM.dds`):  
     - **Nrm_R.tga**: Red channel  
     - **Nrm_G.tga**: Green channel  
     - **Nrm_B.tga**: Blue channel  
     - **Nrm_A.tga**: Alpha channel  
   - **PM** (`*_PM.dds`):  
     - **PM_R_Metallic.tga**: Red channel  
     - **PM_G_Roughness.tga**: Green channel  
     - **PM_B_Ambient_Occlusion.tga**: Blue channel  
   - **BM** (`*_BM.dds`):  
     - **BM_A_Opacity.tga**: Alpha channel  
3. **Skin Textures**: For files ending with the following suffixes, the addon exports four channels (R, G, B, A) with these exact filenames:  
   - **HMVY** (`*_HMVY.dds`):  
     - **L0_HMVY_Red_Hemo.tga** (R)  
     - **L1_HMVY_Grn_Mela.tga** (G)  
     - **L2_HMVY_Blu_Vein.tga** (B)  
     - **L3_HMVY_Alpha_Yellow.tga** (A)  
   - **CLEA** (`*_CLEA.dds`):  
     - **L4_CLEA_Red_Cavity.tga** (R)  
     - **L5_CLEA_Grn_Brows.tga** (G)  
     - **L6_CLEA_Blu_Lips.tga** (B)  
     - **A0_CLEA_Alpha.tga** (A)  
   - **MSK** (`*_MSK.dds`):  
     - **L7_MSK_Red_horns_nail.tga** (R)  
     - **L8_MSK_Grn_Pigment.tga** (G)  
     - **L9_MSK_Blu_TearLip.tga** (B)  
     - **(Alpha channel is not exported for MSK suffix)**  
4. **Output**: All generated `.tga` files are saved in the `split-output` subfolder of the selected directory.  

## Example

1. Open Blender and install the addon as described above.  
2. Switch to the **Image Editor**, press **N**, and select the **Pommelstrike DDS Decompose Split** tab.  
3. Set **DDS Folder** to the directory containing your `.dds` files.  
4. Click **Split Channels**.  

## Support & Links

- **Author**: pommelstrike  
- **URL**: https://linktr.ee/pommelstrike  

## License

This addon is released under the MIT License. See [LICENSE](LICENSE) for details.

---

> Developed with ❤️ by pommelstrike. Feel free to submit issues or pull requests on GitHub!
