# BigFilePatcher

Texture extraction, modification, and sharing tool for KarmaZoo. Extract, edit, and repack game textures with an easy-to-use GUI — or browse and install community-made texture packs. Available for Windows and Linux.

![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Linux-blue)
![Version](https://img.shields.io/badge/version-2.0-green)

## Features

- **Extract** all textures from `bigfile.bfdata`
- **Edit** textures with any image editor and patch them back
- **Texture Pack Sharing** — browse, download, and install community texture packs
- **Upload** your own texture packs for others to use
- **Variants** — publish alternative versions of existing packs

## Download

Download the latest release from the [Releases](../../releases) page:

- **Windows**: `BigFilePatcher-Windows.zip`
- **Linux**: `BigFilePatcher-Linux.zip`

Extract the ZIP and run the executable. No installation required.

## Quick Start

### Patching Textures

1. In Steam, right-click **KarmaZoo** → **Manage** → **Browse local files**
2. Copy `resources/cookedData/bigfile.bfdata` into the `input_bfdata` folder
3. Launch BigFilePatcher and click **"Extract Images from bigfile.bfdata"**
4. Edit images from `base_images` and save them to `edited_images` (same filename, PNG format)
5. Click **"Patch bigfile.bfdata with Selected Images"**
6. Copy the patched file from `output_bfdata` back to the game's `resources/cookedData/` folder

### Using Texture Packs

1. Go to the **Texture Packs** tab
2. Create an account or log in
3. Browse available packs, click **View** on one you like
4. Click **"Download & Install"**
5. Back in the **Patcher** tab, select the installed pack from the **Image Source** dropdown
6. Click **"Patch bigfile.bfdata with Selected Images"**
7. Copy the patched file from `output_bfdata` back to the game's `resources/cookedData/` folder

## Important Notes

- **File Size**: Edited images cannot exceed the original file size
- **Filenames**: Must match exactly (e.g. `bigfile_bfdata-0000000001.png`)
- **Backup**: Keep a backup of your original `bigfile.bfdata`
- **PNG Format**: All textures must be PNG files

## Troubleshooting

**"bigfile.bfdata not found"** — Place the file in the `input_bfdata` folder

**"File too large"** — Reduce image quality or compression level

**Game won't load** — Restore original via Steam (Right-click game → Properties → Installed Files → Verify integrity)

**Can't connect to texture pack server** — The server might be offline. Check your internet connection.

## License

See [LICENSE](LICENSE) file

## Disclaimer

Unofficial fan tool. Not affiliated with or endorsed by the KarmaZoo developers. For educational and personal use only.

AI-assisted development was used in parts of this project.
