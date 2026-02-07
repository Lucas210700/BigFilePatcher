# BigFilePatcher

Texture extraction and modification tool for KarmaZoo. Extract, edit, and repack game textures with an easy-to-use GUI. Available for Windows and Linux.

![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Linux-blue)

## Download

Download the latest release for your operating system from the [Releases](../../releases) page:

- **Windows**: `BigFilePatcher-Windows.zip`
- **Linux**: `BigFilePatcher-Linux.zip`

Extract the ZIP file and run the executable. No installation required!

## How to Use

### 1. Get bigfile.bfdata

1. In Steam, right-click **KarmaZoo** → **Manage** → **Browse local files**
2. Navigate to `resources/cookedData/`
3. Copy `bigfile.bfdata` to the `input_bfdata` folder

### 2. Extract Textures

- Launch the application
- Click **"Extract Images from bigfile.bfdata"**
- Textures will be extracted to the `base_images` folder

### 3. Edit Textures

- Edit any image from `base_images` with your favorite image editor (Photoshop, GIMP, etc.)
- **Important**: File size must be ≤ original size
- Save edited images to `edited_images` folder with the **same filename**

### 4. Patch & Play

- Click **"Patch bigfile.bfdata with Edited Images"**
- Copy the patched file from `output_bfdata` to the game's `resources/cookedData/` folder
- Launch KarmaZoo!

## Important

- **File Size**: Edited images cannot exceed original size
- **Filenames**: Must match exactly
- **Backup**: Keep a backup of your original `bigfile.bfdata`
- **PNG Format**: All textures are PNG files

## Troubleshooting

**"bigfile.bfdata not found"** - Place the file in the `input_bfdata` folder

**"File too large"** - Reduce image quality/compression

**Game won't load** - Restore original via Steam (Right-click game → Properties → Installed Files → Verify integrity)

## License

See [LICENSE](LICENSE) file

## Disclaimer

Unofficial fan tool. Not affiliated with or endorsed by the KarmaZoo developers. For educational and personal use only.
