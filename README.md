# ghostty-shaders

Pixel-art **snow** and **stars** shaders for [Ghostty](https://ghostty.org/).
Crisp, lightweight, and cozy — overlays the terminal without obscuring text.

<video src="https://github.com/user-attachments/assets/4901144e-e48a-4836-8b4a-80e3d6f46810" autoplay loop muted playsinline width="900"></video>

## What's here

| File | Effect |
| --- | --- |
| [`just-snow.glsl`](just-snow.glsl) | Pixel-snapped snowflakes with per-flake drift, sway, and flutter. |
| [`just-stars.glsl`](just-stars.glsl) | Sparse twinkling plus-shaped stars across a dark sky. |

Both sample the terminal texture as-is, so your prompt, colors, and content stay readable.

## Install

1. Drop the `.glsl` files into your Ghostty shaders directory:

   ```sh
   mkdir -p ~/.config/ghostty/shaders
   cp just-snow.glsl just-stars.glsl ~/.config/ghostty/shaders/
   ```

2. Point Ghostty at one of them in `~/.config/ghostty/config`:

   ```
   custom-shader = ~/.config/ghostty/shaders/just-snow.glsl
   custom-shader-animation = always
   ```

3. Reload Ghostty config (`Cmd+Shift+,` on macOS, or restart).

To swap shaders, edit `custom-shader` and reload.

## Tweaking

The top of each file has `#define`s you can change without touching the rest:

**`just-snow.glsl`**

| Define | Default | Effect |
| --- | --- | --- |
| `LAYERS` | `5` | Total parallax layers. |
| `SKIP_NEAR` | `4` | Skip this many nearest layers (controls density). |
| `DEPTH` | `0.4` | Parallax falloff. |
| `WIDTH` | `0.4` | Diagonal drift strength. |
| `SPEED` | `0.3` | Fall speed. |
| `PIXEL_SIZE` | `2.0` | Snap grid in screen pixels. Larger = chunkier flakes. |
| `CELL_SIZE` | `220.0` | Pixels between potential flake positions. |

**`just-stars.glsl`**

| Define | Default | Effect |
| --- | --- | --- |
| `LAYERS` | `10` | Total parallax layers. |
| `SKIP_NEAR` | `2` | Skip this many nearest layers. |
| `DENSITY` | `0.01` | Fraction of cells that contain a star. |
| `SPEED` | `0.3` | Twinkle rate. |
| `PIXEL_SIZE` | `0.7` | Snap grid in screen pixels. |

## Credits

The original "Just snow" shader is by **Andrew Baldwin** (2013) — [thndl.com](http://thndl.com), Twitter `@baldand`.
These files are reimplementations in a pixel-art style by **Eli Saliman** with **Claude**.

## License

Released under **CC BY-NC-SA 3.0** — matching the upstream license.
You may share and adapt for non-commercial use, with attribution, under the same license.
See [`LICENSE`](LICENSE) or <http://creativecommons.org/licenses/by-nc-sa/3.0/>.
