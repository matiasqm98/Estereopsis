# Estereopsis

Native macOS app that converts 3D Blu-ray (MVC) ISOs and MKVs into **Full Side-by-Side or Over/Under MKV** files, ready to play on Vision Pro, projectors, 3D TVs and VR headsets. Apple Silicon.

<!-- screenshot -->

## Features
- **Convert:** ISO / MKV input; lists disc titles (duration, size, chapters) and recommends the longest. Full-resolution SBS or OU, 720p/1080p per eye, Full or Half size.
- **Change 3D format:** turn a finished SBS file into Over/Under (or back) for players that only accept one layout. Detects the source layout automatically (3D flag, aspect ratio, comparing the two halves of the frame), Full or Half output, optional eye swap.
- **Subtitles only:** add or replace subtitles on a finished 3D file without re-encoding.
- Audio tracks copied untouched; all audio and subtitle tracks detected and named automatically.
- Subtitles: none, burned in, 3D-duplicated track (adjustable size/height/depth) or plain track; built-in OCR for PGS (Apple Vision).
- Movie info (title, year, genre, director, producer, synopsis, poster) written as MKV tags + cover.
- Hardware HEVC (VideoToolbox) or H.264 on any Apple Silicon chip; bitrate presets computed from the final frame size.
- Post-conversion re-interleave so audio and video are properly ordered (no choppy audio or seek drops in Infuse/IINA). **Repair playback** tool for existing files.
- Queue, history, quick test clip, Settings window, keyboard shortcuts, accent colors, Liquid Glass on macOS 26+, English/Spanish.

## Requirements
- Apple Silicon, macOS 13+
- MakeMKV (separate install) only for ripping ISOs/discs; one-time setting to keep the 3D (MVC) track: see *MakeMKV setup* below.

## Bundled
ffmpeg/ffprobe, MKVToolNix (mkvpropedit, mkvextract) — GPL; [mvcdec](https://github.com/brunoga/mvc) — Apache-2.0. See `Resources/licenses`. MakeMKV is not redistributed.

Source code of the GPL components: [FFmpeg](https://ffmpeg.org/download.html#get-sources), [MKVToolNix](https://mkvtoolnix.download/source.html). The bundled ffmpeg is built with the FFmpeg-mvc patch; open an issue if you want the exact build sources.

## Install
Download `Estereopsis-1.1.1.dmg`, drag Estereopsis to Applications. The app is not notarized: first launch via right-click → Open. If macOS still refuses, run `xattr -dr com.apple.quarantine /Applications/Estereopsis.app` in Terminal.

## MakeMKV setup (only for ISOs / discs)

By default MakeMKV drops the second 3D view. In MakeMKV > Preferences > Advanced, set the *Default selection rule* to:

```
-sel:all,+sel:(favlang|nolang),+sel:mvcvideo,=100:all,-10:favlang
```

Estereopsis warns you in orange if an extracted file is missing the MVC track. Already extracted 3D MKVs don't need MakeMKV.

## Support

Something not playing right? In the app use **Help > Copy diagnostic report** and, for a finished file, **Help > Inspect 3D file...** (checks the 3D flag, SBS/OU, Full/Half, black bars and tracks), then open an issue and paste the result.

## Release notes

Each [release](../../releases) lists what changed. Latest: **1.1.1**: Half-SBS/OU without black bars, diagnostic report and 3D file inspector.

## License
Free, non-commercial personal project. Bundled tools keep their own licenses.
