# Pommelstrike's DDS Channel Splitter


A Blender addon to split DDS texture files into separate grayscale TGA files for each channel with custom naming conventions. This addon supports splitting normal maps, metallic/roughness maps, opacity maps, MSKcloth, glow maps, and skin textures HMVY, CLEA, etc.

## Features

- **DDS Channel Splitting:**  
  Automatically splits DDS files into separate TGA files for each color channel.
  
- **Supports Multiple File Types:**  
  - **Normal Maps (`_NM`):** Splits into `Nrm_R.tga`, `Nrm_G.tga`, `Nrm_B.tga`, and `Nrm_A.tga`.
  - **Metallic/Roughness Maps (`_PM`):** Splits into `PM_R_Metallic.tga`, `PM_G_Roughness.tga`, and `PM_B_Ambient_Occlusion.tga`.
  - **Opacity Maps (`_BM`):** Creates a single `BM_A_Opacity.tga` from the alpha channel.
  - **Glow Maps (`_GM`):** Splits into separate files for each channel with a unique naming convention.
  - **Skin Textures:**  
    - Standard mapping based on predefined channels for keys such as `HMVY`, `CLEA`, and `MSK`.
    - **New Support for `*_MSKcloth.DDS`:** Generates three files:  
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
   - In the 3D View Sidebar (under the Pommelstrike tab) or in the popover from the header, locate the **DDS Folder** field.
   - Click the folder icon and navigate to the directory containing your `.dds` files.

2. **Split DDS Channels:**  
   - Click the **Split Channels** button.
   - The addon will process the DDS files according to their suffix conventions (e.g., `_NM`, `_PM`, `_BM`, `_GM`, and `_MSKcloth`).
   - Processed files are saved in a subfolder named **split-output** within your selected folder.

3. **View System Console:**  
   - The system console can be toggled using the **View System Console** button.

## Reported Console Messages

During execution, messages like the following will be reported:
- `Processed HUM_F_ARM_Rider_Gloves_X_BM (BM custom)`
- `Skipping HUM_F_ARM_Rider_Gloves_X_MSKcloth: no naming mapping defined.`
- `Processed HUM_F_ARM_Rider_Gloves_X_NM (NM custom)`
- `Processed HUM_F_ARM_Rider_Gloves_X_PM (PM custom)`

These messages indicate which files were successfully processed or intentionally skipped (if no naming mapping is available).

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
