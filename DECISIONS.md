# Decisions — fireplace

## 2026-11-24 — One Python script, no dependencies

It runs on the system `python3` with only the standard library, so the
whole thing is a single file with no build step or toolchain. At this
resolution (roughly 80×60 pixels, 12 fps) Python is fast enough. Pixels are
drawn as `▀` half blocks in 24-bit colour, and only changed cells are
redrawn each frame.

## 2026-11-24 — One colour ramp, layers combined with max()

The 16 colours are a single warm ramp sampled from a real fireplace video.
Stone, bark and flame are all indices into it, so the flame layer is just
`max(wall, flame)`. Cool flame is darker than the lit wall and disappears,
which gives see-through flame edges for free.

## 2026-11-24 — Flames from rising noise, not the DOOM effect

The DOOM fire effect looked grainy at pane resolution. The flames are two
value-noise textures that scroll upwards at different speeds and get eaten
away more with height, which breaks them into tongues like the video's.
Sampling pre-built textures keeps it cheap.

## 2026-11-24 — Logs in octants, everything else in half blocks

Unicode 16 octants (2×4 pixels per character) double the detail, but drawing
the whole scene with them costs about three times the CPU and loses the 8-bit
look. By default only the logs are drawn at octant resolution, as a separate
layer over the fire; the rest stays half blocks. Each octant cell can show two
colours, picked as the best split of its eight palette values. `--cells half`
and `--cells octant` are kept for terminals without Unicode 16 and for
comparison. Octants need a terminal that draws them itself (Ghostty does).
