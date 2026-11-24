# fireplace

A small 8-bit fireplace to keep in a terminal pane: logs, flames, sparks and a
firelit stone wall.

## Running it

It's a single Python 3 script with no dependencies, for macOS and Linux.

```sh
./fireplace
```

Press `q`, `Esc` or `Ctrl-C` to put it out. To have it everywhere, copy or
symlink it somewhere on your `PATH`, such as `~/.local/bin`.

It needs a terminal with 24-bit colour. The logs are drawn with Unicode 16
octant characters, which only some terminals draw themselves (Ghostty does).
If the logs look wrong, use `--cells half`.

## Options

| Option | |
| --- | --- |
| `--clock` | Show the time above the fire |
| `--fps N` | Frames per second (default 12) |
| `--scale N` | Screen pixels per fire pixel (default: fit the pane) |
| `--seed N` | Lay out the same stones and logs every time |
| `--cells half\|octant\|mixed` | Half blocks, octants, or half blocks with octant logs (default) |
| `--dump COLSxROWS` | Write raw RGB frames to stdout instead of drawing |
| `--frames N` | Frames to write with `--dump` (default 120) |

`--dump` makes frames of 2×4 pixels per character, so a video preview of an
80×30 pane looks like this:

```sh
./fireplace --dump 80x30 | ffmpeg -f rawvideo -pix_fmt rgb24 -s 160x120 -r 12 -i - fire.mp4
```

## Licence

MIT
