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

Basically: it’s duct tape for video folders.

---

## Requirements

1. **Windows**
2. **FFmpeg + FFprobe** installed and available in PATH  
   - Run `ffmpeg -version` in Command Prompt to confirm
3. PowerShell is already included with Windows

---

## How to use

1. Download this repo (green **Code** button → **Download ZIP**) and unzip it  
2. Double-click: `MergeVideos.cmd`
3. Select:
   - Input folder (where your videos are)
   - Output file (optional — if you don’t pick one, it saves next to the script)
   - Format (MKV or MP4)
   - Codec (H.264 or H.265)
   - Acceleration (Auto / NVIDIA GPU / CPU)
   - Quality (Lossless / Very High / High / Medium / Small)
   - Speed (Fast / Balanced / Slow)
4. Click **Start**

You’ll get a progress window showing:
- which file is being processed
- overall progress
- ETA

---

## Quality notes (read this before yelling at your screen)

- If your folder contains mixed codecs (VP9, AV1, H.264, etc.), **re-encoding is required** to merge into one continuous file.
- **Lossless** means: no *additional* quality loss during re-encode (but the original files may already be lossy).
- Lossless output files can be **huge**. Like “why is my SSD sweating” huge.

---

## GPU acceleration

If you have an NVIDIA GPU and FFmpeg supports NVENC, you can enable it in the dropdown.
If NVENC isn’t available, the script will fall back to CPU options.

---

## Trust & safety

This script is plain text. You can (and should) inspect it before running.

If you’re cautious (good instinct):
- open `MergeVideos.cmd` in Notepad and read it
- or paste it into any code-review tool / AI and ask: “What does this do?”
- run it on a small test folder first

No shady installers, no hidden downloads — just FFmpeg doing FFmpeg things.

---

## Troubleshooting

**“FFmpeg not found”**
- Install FFmpeg and add it to PATH

**Some videos fail**
- The error window includes a **Copy error** button — paste that into an issue and include:
  - the filename that failed
  - the chosen settings (format/codec/quality)

**MP4 output fails**
- Try MKV. MKV is more forgiving and usually the best “just work” container.

---

## Roadmap (maybe)

- Drag-and-drop input folder
- Option to merge only a selected range (Episode 1–50)
- Remember last used settings

---

## License

MIT (do whatever you want, just don’t blame me if you merge your entire life into a single file).
