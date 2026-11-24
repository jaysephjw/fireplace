# Changelog

## 2026-11-24

First public release.

- A fireplace drawn in 24-bit colour: a stone wall and hearth lit by the fire,
  a pile of logs with glowing cracks, rising flames and sparks.
- Logs are drawn with Unicode 16 octants and everything else with half blocks.
  `--cells half` and `--cells octant` use one or the other throughout.
- Fits itself to the pane and redraws on resize.
- `--clock` shows the time above the fire.
- `--seed` lays out the same stones and logs every time.
- `--dump` writes raw RGB frames for previewing with ffmpeg.
