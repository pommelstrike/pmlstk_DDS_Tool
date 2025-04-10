# Pommelstrike's DDS Channel Splitter
Support the development of this addon and others for future updates:

- [Ko-fi: Support Pommelstrike](https://ko-fi.com/pommelstrike) 
- [Patreon: Become a Patron](https://patreon.com/pommelstrike) it's free to join,! and the most updates are post there
- [Linktree: Find More Links](https://linktr.ee/pommelstrike) Comms / Releases

A Blender addon to split DDS texture files into separate grayscale TGA files for each channel with custom naming conventions. This addon supports splitting normal maps, metallic/roughness maps, opacity maps, glow maps, and also processes skin textures based on predefined mappings.

## Features

- **DDS Channel Splitting:**  
  Automatically splits DDS files into separate TGA files for each color channel.
  
- **Supports Multiple File Types:**  
  - **Normal Maps (`_NM`):** Splits into `Nrm_R.tga`, `Nrm_G.tga`, `Nrm_B.tga`, and `Nrm_A.tga`.
  - **Metallic/Roughness Maps (`_PM`):** Splits into `PM_R_Metallic.tga`, `PM_G_Roughness.tga`, and `PM_B_Ambient_Occlusion.tga`.
  - **Opacity Maps (`_BM`):** Creates a single `BM_A_Opacity.tga` from the alpha channel.
  - **Glow Maps (`_GM`):** Splits into separate files for each channel with a unique naming convention.
  - **Skin Textures:**  
    Uses predefined mappings for different skin texture types.  
    For example:
    - For files with the key **HMVY**, the following output files will be generated:
      - `L0_HMVY_Red_Hemo.tga`
      - `L1_HMVY_Grn_Mela.tga`
      - `L2_HMVY_Blu_Vein.tga`
      - `L3_HMVY_Alpha_Yellow.tga`
    - For files with the key **CLEA**, the addon produces:
      - `L4_CLEA_Red_Cavity.tga`
      - `L5_CLEA_Grn_Brows.tga`
      - `L6_CLEA_Blu_Lips.tga`
      - `A0_CLEA_Alpha.tga`
  - **Custom Support for `*_MSKcloth.DDS`:**  
    Generates three files:  
    - `MSKcloth_R.tga`
    - `MSKcloth_G.tga`
    - `MSKcloth_B.tga`
      
- **User Interface Integration:**  
  - A popover button appears in the 3D View Header next to the transform orientations section.
  - A dedicated sidebar panel in the 3D View (N-panel) provides similar functionality.
  - Includes a system console toggle.

- **Blender Version:**  
  This addon is written for Blender **4.1.1** and higher.

## Installation

1. **Download the Addon:**  
   [Download Pommelstrike's DDS Channel Splitter (ZIP)](https://github.com/pommelstrike/pmlstk_DDS_tex_split/blob/main/pommelstrike_DDS_Splitter.zip)

2. **Install via Blender Preferences:**  
   - Open Blender and go to **Edit > Preferences**.
   - Click on the **Add-ons** tab.
   - Click **Install...** at the top of the window.
   - Navigate to and select the downloaded ZIP file.
   - Once installed, enable the addon by checking the box next to its name.

3. **Save Preferences:**  
   Click **Save Preferences** if you wish to have the addon enabled on startup.

## Usage

1. **Set the DDS Folder:**  
   - In the 3D View Sidebar (under the Pommelstrike tab) or the popover from the header, locate the **DDS Folder** field.
   - Click the folder icon and navigate to the directory containing your `.dds` files.

2. **Split DDS Channels:**  
   - Click the **Split Channels** button.
   - The addon will process the DDS files based on their suffix conventions (e.g., `_NM`, `_PM`, `_BM`, `_GM`, `_MSKcloth` and skin texture keys such as `HMVY`, `CLEA`, and `MSK`).
   - Processed files are saved in a subfolder named **split-output** within your selected folder.

3. **View System Console:**  
   - The system console can be toggled using the **View System Console** button.

## Reported Console Messages

During execution, messages like the following will be reported:
- `Processed HUM_F_ARM_Rider_Gloves_X_BM (BM custom)`
- `Skipping HUM_F_ARM_Rider_Gloves_X_: no naming mapping defined.`
- `Processed HUM_F_ARM_Rider_Gloves_X_NM (NM custom)`
- `Processed HUM_F_ARM_Rider_Gloves_X_PM (PM custom)`

These messages indicate which files were successfully processed or intentionally skipped if no mapping is available.

## Skin Textures – Standard Mapping Output Example

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

Distributed under the terms of the MIT License. See [LICENSE](LICENSE) for more information.

## Contributing

Contributions, issues, and feature requests are welcome!  
Feel free to check the [issues page](https://github.com/pommelstrike/pmlstk_DDS_tex_split/issues) if you want to contribute.

---

*Pommelstrike's DDS Channel Splitter* is provided as-is, with support for various texture maps tailored for artists and technical directors working with DDS files in Blender.
