# imgstrp

Re-encode a photo as a bare baseline JPEG.

Drops all metadata APP/COM segments (EXIF, XMP, ICC profile, MPF,
HDR gain-map, comments) and writes plain JFIF + image data only.
Pixel content is re-encoded; nothing is cropped or rotated.

## Needs

- `ffmpeg` (with `ffprobe`)
- `python3` (stdlib only)

## Install

```bash
cp imgstrp ~/.local/bin/imgstrp
chmod +x ~/.local/bin/imgstrp
```

## Usage

```bash
imgstrp INPUT [OUTPUT] [--max PX] [--quality N]
```

- `INPUT` — source image (any ffmpeg-readable format)
- `OUTPUT` — destination `.jpg` (default: `<name>-clean.jpg` next to input)
- `--max PX` — cap the long side at `PX` pixels; never upscales
- `--quality N` — ffmpeg mjpeg quality, 2 (best) to 31 (worst); default 2
- `-h, --help` — show help

## Examples

```bash
imgstrp photo.heic               # -> photo-clean.jpg, original size
imgstrp photo.jpg clean.jpg      # explicit output name
imgstrp scan.png --max 1600      # cap the long side at 1600 px
imgstrp photo.heic --quality 5   # smaller file, lower quality
```
