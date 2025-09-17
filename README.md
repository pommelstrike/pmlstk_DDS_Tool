# Pommelstrike's DDS Tool

[![BG3 DDS TOOL - Compose to DDS Feature](https://img.youtube.com/vi/lV8tg81ZVs8/maxresdefault.jpg)](https://youtu.be/lV8tg81ZVs8?si=VgLyAFkKrhgFpEg8)

[![Blender Version](https://img.shields.io/badge/Blender-4.1.1%2B-blue.svg)](https://www.blender.org/)
[![Addon Version](https://img.shields.io/badge/Version-3.4.8-green.svg)](https://github.com/pommelstrike/pmlstk_DDS_tex_split/releases)

Support the development of this addon and others for future updates:
- [Ko-fi: Support Pommelstrike](https://ko-fi.com/pommelstrike)
- [Patreon: Become a Patron](https://patreon.com/pommelstrike) it's free to join, and the most updates are posted there
- [Linktree: Find More Links](https://linktr.ee/pommelstrike) Comms / Releases

A Blender addon for decomposing DDS texture files into separate grayscale TGA files for each channel with custom naming conventions, and composing TGA or PNG files back into DDS format. This addon supports normal maps, metallic/roughness maps, opacity maps, glow maps, cloth masks, and skin textures based on predefined mappings. DDS composition uses texconv.exe for block compression tailored to specific suffixes.



## Features

- **DDS Channel Decomposition:**
  Automatically splits DDS files into separate TGA files for each color channel.

- **Supports Multiple Decomposition File Types:**
  - **_NM Normal Map (`_NM`):** Splits into `Nrm_R.tga`, `Nrm_G.tga`, `Nrm_B.tga`, and `Nrm_A.tga`.
  - **_PM Metallic/Roughness/Ambient_Occlusion Map (`_PM`):** Splits into `PM_R_Metallic.tga`, `PM_G_Roughness.tga`, and `PM_B_Ambient_Occlusion.tga`.
  - **_BM - Opacity Map (`_BM`):** Creates a single `BM_A_Opacity.tga` from the alpha channel.
  - **_GM - Glow Map (`_GM`):** Splits into separate files for each channel with a unique naming convention.
  - **Custom Support for `*_MSKcloth.DDS`:**
    Generates three files:
    - `MSKcloth_R.tga`
    - `MSKcloth_G.tga`
    - `MSKcloth_B.tga`
  - **Skin Textures:**
    - **HMVY**, the following output files will be generated:
      - `L0_HMVY_Red_Hemo.tga`
      - `L1_HMVY_Grn_Mela.tga`
      - `L2_HMVY_Blu_Vein.tga`
      - `L3_HMVY_Alpha_Yellow.tga`
    - **CLEA**, the addon produces:
      - `L4_CLEA_Red_Cavity.tga`
      - `L5_CLEA_Grn_Brows.tga`
      - `L6_CLEA_Blu_Lips.tga`
      - `A0_CLEA_Alpha.tga`
    - **MSK:**
      - `L7_MSK_Red_horns_nail.tga`
      - `L8_MSK_Grn_Pigment.tga`
      - `L9_MSK_Blu_TearLip.tga`

- **DDS Composition from TGA/PNG:**
  Converts TGA or PNG files back into DDS with automatic compression based on suffixes. Outputs are saved in a `composed-dds` subfolder.
  - Supported suffixes and formats:
    - _PM: BC1_UNORM
    - _MSK: BC1_UNORM
    - _MSKCLOTH: BC1_UNORM
    - _BM: BC1_UNORM (allows alpha blending)
    - _NM: BC3_UNORM
    - _BMA: BC3_UNORM (allows opacity masking, no alpha blending)
    - _CLEA: BC3_UNORM
    - _HMVY: BC3_UNORM
  - Defaults to BC1_UNORM for unrecognized suffixes.
  - Requires texconv.exe (default path: `C:\SteamLibrary\steamapps\common\Baldurs Gate 3 Toolkit\texconv.exe`; customizable in the panel).

- **User Interface Integration:**
  - Panels in the Properties editor under Texture and Material contexts.
  - **Sidebar Visibility**: The addon panels are accessible in the main Properties editor (right panel). For enhanced workflow integration, enable the sidebar (N-panel) in the 3D Viewport via **View > Sidebar** (or press N), though primary controls remain in Properties for texture/material contexts.
  - Folder paths for Decompose and Compose operations.
  - Texconv path configuration.
  - Progress reporting in Blender's console (toggle via "View System Console").
  - Suffix preset info popup button for quick reference.

- **Error Handling and Progress:**
  - Validates directories and texconv.exe path.
  - Reports successes (e.g., "Processed [file]") and errors (e.g., "Failed [file]: [error]") in the console.
  - Skips unsupported files with warnings.

- **Blender Version:**
  This addon is written for Blender **4.1.1** and higher.

## Installation

1. **Download the Addon:**
   [Download Pommelstrike BG3 DDS Tool (ZIP)](https://github.com/pommelstrike/pmlstk_DDS_tex_split/releases)

2. **Install via Blender Preferences:**
   - Open Blender and go to **Edit > Preferences**.
   - Click on the **Add-ons** tab.
   - Click **Install...** at the top of the window.
   - Navigate to and select the downloaded ZIP file.
   - Once installed, enable the addon by checking the box next to its name.

3. **Save Preferences:**
   Click **Save Preferences** if you wish to have the addon enabled on startup.

## Usage

### Decompose DDS Channels

1. **Set the DDS Folder:**
   - In the Properties panel (Texture or Material context, under the Pommelstrike tab), locate the **Decompose Folder** field.
   - Click the folder icon and navigate to the directory containing your `.dds` files.

2. **Run Decomposition:**
   - Click the **Decompose DDS Channels to TGA** button.
   - The addon will process DDS files based on their suffixes (e.g., `_NM`, `_PM`, `_BM`, `_GM`, `_MSKcloth`, and skin keys like `HMVY`, `CLEA`, `MSK`).
   - Outputs are saved in a `split-output` subfolder within the selected directory.

### Compose TGA/PNG to DDS

1. **Prepare Input Files:**
   - Place TGA or PNG files in a folder, ensuring unique base names (e.g., `texture_PM.png`) and valid suffixes for compression.

2. **Set the Compose Folder:**
   - In the panel, locate the **Compose Folder** field and select the directory with your input files.

3. **Configure texconv.exe:**
   - Verify or update the **Texconv Path** field (defaults to BG3 Toolkit location). Download from [DirectXTex GitHub Releases](https://github.com/microsoft/DirectXTex/releases) if needed.

4. **Run Composition:**
   - Click the **Compose DDS** button.
   - The addon processes files, applying suffix-based compression via texconv.exe.
   - Check the console for progress (e.g., "Converted [file] to [file].DDS").

5. **View Results:**
   - Outputs (capitalized `.DDS` files) appear in a `composed-dds` subfolder.
   - Use tools like DDS Texture Informer by Neeston for verification.

6. **View System Console:**
   - Toggle the console with the **View System Console** button for detailed logs.

### Accessing Panels in Sidebar

To integrate the tool more closely with your 3D modeling workflow:
- Switch to the 3D Viewport.
- Enable the sidebar by selecting **View > Sidebar** from the menu or pressing **N**.
- While the primary panels are in the Properties editor, you can reference folder paths and operations here for quick access during scene navigation. For full functionality, return to the Properties editor under Texture or Material contexts.

## Reported Console Messages

During execution, messages like the following will be reported:
- `Processed HUM_F_ARM_Rider_Gloves_X_BM (BM custom)`
- `Skipping HUM_F_ARM_Rider_Gloves_X_: no naming mapping defined.`
- `Processed HUM_F_ARM_Rider_Gloves_X_NM (NM custom)`
- `Processed HUM_F_ARM_Rider_Gloves_X_PM (PM custom)`
- `Converted [base] to [base].DDS` (for composition)

These indicate successful processing, skips, or completions.

## Skin Textures – Standard Mapping Output Example
![demo](https://github.com/pommelstrike/pmlstk_DDS_tex_split/blob/main/decompose_addon_demo.gif)


![image](https://i.ibb.co/M56WNXWT/skin-fc.png)
The addon uses a predefined mapping for skin textures. Here are examples for two key mappings:

- **For a file with key `HMVY`** (e.g., `HUM_F_BODY_part_HMVY.DDS`), the output files will be:
  - `L0_HMVY_Red_Hemo.tga`
  - `L1_HMVY_Grn_Mela.tga`
  - `L2_HMVY_Blu_Vein.tga`
  - `L3_HMVY_Alpha_Yellow.tga`

- **For a file with key `CLEA`** (e.g., `HUM_F_BODY_part_CLEA.DDS`), the generated output files will be:
  - `L4_CLEA_Red_Cavity.tga`
  - `L5_CLEA_Grn_Brows.tga`
  - `L6_CLEA_Blu_Lips.tga`
  - `A0_CLEA_Alpha.tga`

## Connect

Support the development of this addon or stay connected for future updates:
- [Ko-fi: Support Pommelstrike](https://ko-fi.com/pommelstrike)
- [Patreon: Become a Patron](https://patreon.com/pommelstrike)
- [Linktree: Find More Links](https://linktr.ee/pommelstrike)

## Support

If you encounter any issues or have questions, please feel free to [open an issue](https://github.com/pommelstrike/pmlstk_DDS_tex_split/issues) in the repository.

## License

This project is distributed under the terms of the [MIT License](LICENSE). See the LICENSE file for details.

## Contributing

Contributions, issues, and feature requests are welcome!
Feel free to check the [issues page](https://github.com/pommelstrike/pmlstk_DDS_tex_split/issues) if you want to contribute.

---

*Last Updated: September 17, 2025*
