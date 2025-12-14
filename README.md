# MergeVideos-Windows

Merge a folder full of videos into **one** video — even if the files are a chaotic mix of codecs and formats.  
This is a **Windows-only** GUI script powered by FFmpeg.

🎬 Works with: MP4, MKV, MOV, WEBM, AVI, TS, M2TS, WMV (and more)  
🪟 Windows only: tested on Windows 10/11  
🚀 Optional: NVIDIA GPU acceleration (NVENC) if your FFmpeg supports it

---

## What it does

- You pick a folder of videos
- It sorts them in **natural order** (so `1, 2, 3... 10, 11...` not `1, 10, 100`)
- It converts them to a single consistent format/codec (because mixed codecs cannot be stitched as-is)
- It merges everything into **one** output file
- If anything fails, it shows the error in a window with a **Copy error** button

Basically: it’s duct tape for video folders. The good kind. The “fixes everything” kind.

---

## Requirements

1. Windows
2. FFmpeg + FFprobe installed and available in PATH
3. PowerShell (already included with Windows)

Note: FFprobe comes bundled with FFmpeg. You don’t install it separately.

---

## Install FFmpeg on Windows (not a nerd thing, it’s actually easy)

FFmpeg’s official site links to **compiled builds** because FFmpeg itself is primarily distributed as source code.  
Pick one of these two easy routes:

### Option A: Install with winget (fastest)

1) Open **Windows Terminal** or **Command Prompt**  
2) Run:

```powershell
winget install -e --id Gyan.FFmpeg
```

### Option B: Manual download (still easy)

1. Download a Windows build (contains `ffmpeg.exe` + `ffprobe.exe`)
2. Extract it to a simple folder like: `C:\ffmpeg\`
3. Add the `bin` folder to PATH:

   * Press the **Win** key, search: **Environment Variables**
   * Open: **Edit the system environment variables**
   * Click: **Environment Variables**
   * Under **System variables**, select **Path** -> **Edit**
   * Click **New** and add: `C:\ffmpeg\bin`
   * Click OK, OK, OK
4. Close and reopen Terminal

Recommended build sources:

```text
FFmpeg downloads page (official): https://www.ffmpeg.org/download.html
Gyan.dev Windows builds:         https://www.gyan.dev/ffmpeg/builds/
BtbN GitHub builds:              https://github.com/BtbN/FFmpeg-Builds/releases
```

### Confirm installation

Open a new Command Prompt and run:

```bat
ffmpeg -version
ffprobe -version
```

If both print version info, you’re done.

---

## How to use

1. Download this repo (green **Code** button -> **Download ZIP**) and unzip it
2. Double-click: `MergeVideos.cmd`
3. Choose your settings in the dropdowns:

   * Input folder (where your videos are)
   * Output file (optional; if you don’t pick one, it exports next to the script)
   * Format (MKV or MP4)
   * Codec (H.264 or H.265)
   * Acceleration (Auto / NVIDIA GPU / CPU)
   * Quality (Lossless / Very High / High / Medium / Small)
   * Speed (Fast / Balanced / Slow)
   * Audio (AAC or FLAC when using MKV)
4. Click **Start**

You’ll get a progress window showing:

* which file is being processed
* overall progress
* ETA

---

## Quality notes (read this before yelling at your screen)

* If your folder contains mixed codecs (VP9, AV1, H.264, etc.), **re-encoding is required** to merge into one continuous file.
* “Lossless” means: no *additional* quality loss during the re-encode step (but your originals may already be lossy).
* Lossless output files can be **huge**. Like “my SSD just looked at me funny” huge.

---

## GPU acceleration

If you have an NVIDIA GPU and your FFmpeg build supports NVENC, you can enable it in the dropdown.
If NVENC isn’t available, the script will fall back to CPU options.

---

## Trust & safety

This script is plain text. You can (and should) inspect it before running.

If you’re cautious (good instinct):

* open `MergeVideos.cmd` in Notepad and read it
* paste it into any AI/code-review tool and ask: “What does this do?” (totally fine)
* run it on a small test folder first

No installers, no hidden downloads, no mystery meat. Just FFmpeg doing FFmpeg things.

---

## Troubleshooting

### “FFmpeg not found”

* Install FFmpeg and add it to PATH (see install steps above)
* Restart Command Prompt/Terminal after changing PATH

### Some videos fail

* The error window includes a **Copy error** button
* Paste the copied text into a GitHub Issue and include:

  * the filename that failed
  * your chosen settings (format/codec/quality/speed/acceleration)

### MP4 output fails

* Try MKV. MKV is more forgiving and usually the best “just work” container.

---

## Roadmap (maybe)

* Drag-and-drop input folder
* Option to merge only a selected range (Episode 1–50)
* Remember last used settings

---

## License

MIT (do whatever you want, just don’t blame me if you merge your entire life into a single file).
