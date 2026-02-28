# BigFilePatcher — User Guide

## Table of Contents

1. [Getting Started](#getting-started)
2. [Patcher Tab](#patcher-tab)
3. [Texture Packs Tab](#texture-packs-tab)
4. [Folder Structure](#folder-structure)
5. [Editing Textures](#editing-textures)
6. [FAQ](#faq)
7. [Troubleshooting](#troubleshooting)

---

## Getting Started

### Requirements

- A copy of **KarmaZoo** on Steam
- Windows or Linux

### First-Time Setup

1. Extract the BigFilePatcher ZIP to any folder.
2. In Steam, right-click **KarmaZoo** → **Manage** → **Browse local files**.
3. Navigate to `resources/cookedData/` and copy `bigfile.bfdata`.
4. Paste it into the `input_bfdata` folder next to the BigFilePatcher executable.
5. Launch BigFilePatcher.

The application has two tabs: **Patcher** and **Texture Packs**.

---

## Patcher Tab

This is the main tab for extracting and patching textures.

### Extracting Textures

Click **"Extract Images from bigfile.bfdata"** to extract all game textures into the `base_images` folder. These are the original unmodified textures and serve as a reference for editing.

### Selecting an Image Source

Before patching, choose where your edited textures come from using the **Image Source for Patching** dropdown:

- **edited_images** (default) — uses images you manually edited and placed in the `edited_images` folder.
- **texturepacks/\<pack name\>** — uses a texture pack that you downloaded and installed from the Texture Packs tab.

Click **Refresh** next to the dropdown to update the list of available sources.

### Patching

Click **"Patch bigfile.bfdata with Selected Images"** to create a patched version. The result is saved in the `output_bfdata` folder. Copy the patched `bigfile.bfdata` back to the game's `resources/cookedData/` folder and launch KarmaZoo to see your changes.

### Log Output

The log area at the bottom shows detailed progress and any warnings during extraction or patching. Use the **Clear Log** button to reset it.

---

## Texture Packs Tab

This tab lets you browse, download, and share community-made texture packs.

### Creating an Account

Enter a **username** (3–32 characters, letters/numbers/underscores only) and a **password** (minimum 8 characters), then click **Register**. Your account will be created immediately.

> **Important:** Passwords cannot be changed after registration. Choose a secure password that you do not use elsewhere.

To log in next time, enter your credentials and click **Login**. Enable **"Save login"** to stay logged in between sessions.

### Browsing Packs

The **Browse Packs** sub-tab shows available texture packs as cards with a thumbnail, title, author, and stats (number of images, downloads, variants).

- Use the **Search** field to find packs by name or author.
- Use the **Sort** dropdown to sort by newest, oldest, most downloads, or title.
- Use the **Previous / Next** buttons to navigate pages.
- Click **Refresh** to reload the list.

### Viewing Pack Details

Click **View** on any pack card to see its full details:

- **Main image** and **screenshots** — click any image to view it at full size.
- **Description** with details from the author.
- **Stats** showing image count, download count, and file size.
- **Variants** — if the pack has variants (alternative versions), select them from the dropdown.

### Downloading and Installing

1. Click **"Download & Install"** in the pack details view.
2. The pack is downloaded and extracted to `texturepacks/<pack name>/`.
3. Switch to the **Patcher** tab and select the pack from the **Image Source** dropdown.
4. Patch as usual.

### Uploading Your Own Pack

Go to the **Upload / My Packs** sub-tab:

1. **Title** (3–100 characters) — name your texture pack.
2. **Description** (up to 2000 characters) — describe what your pack changes.
3. **Main Image** — click **Browse** to select a preview image (PNG, max 2 MB).
4. **Screenshots** — click **Browse** to select up to 5 additional preview images (PNG, max 2 MB each).
5. **Variant of** — if your pack is a variant of an existing pack, select the original from the dropdown. Leave as "(None - new pack)" for a standalone pack.
6. Click **"Publish Texture Pack"**.

Your texture ZIP is created automatically from the `edited_images` folder. Only valid texture files (matching the `bigfile_bfdata-XXXXXXXXXX.png` naming pattern) are included.

**Upload limits:** 3 uploads per day, 1 minute cooldown between updates.

### Managing Your Packs

The **My Published Packs** section at the bottom of the Upload tab shows all your published packs with their title, image count, downloads, and version.

- **Update Selected** — opens a dialog where you can update the title, description, main image, screenshots, and/or texture files of an existing pack.
- **Delete Selected** — removes the pack (soft delete).
- **Refresh My Packs** — reloads the list.

---

## Folder Structure

```
BigFilePatcher/
├── BigFilePatcher          (executable)
├── input_bfdata/           (place bigfile.bfdata here)
├── base_images/            (extracted original textures)
├── edited_images/          (your edited textures go here)
├── output_bfdata/          (patched bigfile.bfdata output)
├── texturepacks/           (installed texture packs)
│   └── <pack name>/
│       └── *.png
└── USER_GUIDE.md           (this file)
```

---

## Editing Textures

### Rules

1. **File format**: PNG only.
2. **File name**: Must match the original exactly (e.g. `bigfile_bfdata-0000000001.png`).
3. **File size**: The edited image **must not exceed** the original file size. If it does, patching will fail for that image.
4. **Partial edits**: You do not need to edit all images. Only place the ones you changed into `edited_images`.

### Tips

- Use the images in `base_images` as your starting point.
- To reduce file size, lower the compression level or reduce detail in transparent areas.
- Some textures appear as duplicates (e.g. images 116/117, 118/119, 120/121, 151/162). If you edit one, edit both to keep them consistent.
- Test your changes in-game frequently to catch issues early.

---

## FAQ

**Can I break my game with this?**
No. You can always restore the original file via Steam: Right-click KarmaZoo → Properties → Installed Files → Verify integrity of game files.

**Do other players see my textures?**
No. Texture modifications are local to your machine only.

**Why is my edited image rejected for being too large?**
The patching process replaces image data at fixed offsets in the binary file. A larger file would overwrite adjacent data and corrupt the game file. Try increasing PNG compression or simplifying the image.

**Can I use multiple texture packs at once?**
Not directly. You can only select one image source at a time. However, you could manually combine images from multiple packs into the `edited_images` folder.

**Is my password stored securely?**
Your password is hashed with bcrypt on the server and never stored in plain text. Locally, only your authentication token is saved (not your password). The token is stored in `~/.bigfilepatcher/auth.json` with restricted file permissions.

**What happens when I uninstall a texture pack?**
The pack's folder is removed from `texturepacks/`. The game is not affected — you would just need to re-patch with a different image source.

---

## Troubleshooting

| Problem | Solution |
|---|---|
| "bigfile.bfdata not found" | Place the file in the `input_bfdata` folder |
| "File too large" | Reduce image quality or use higher PNG compression |
| Game crashes after patching | Restore via Steam → Verify integrity of game files |
| Images not showing in Texture Packs | Ensure you have an internet connection |
| Can't register / login | Check that your username is 3–32 characters (letters, numbers, underscores) and your password is at least 8 characters |
| "Upload limit reached" | You can upload up to 3 packs per day. Wait 24 hours. |
| Pack download fails | Check your internet connection. Try again later. |
| Installed pack not showing in dropdown | Click **Refresh** next to the Image Source dropdown in the Patcher tab |
