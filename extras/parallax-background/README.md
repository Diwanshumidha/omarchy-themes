# Parallax background plugin

A copy of Omarchy's built-in `omarchy.background` shell plugin that adds a
two-layer parallax effect.

If the current wallpaper is `<theme>/backgrounds/<name>.png` and the theme also has
`<theme>/parallax/<name>.png` (transparent foreground) and
`<theme>/parallax/<name>.bg.png` (background with the subject filled in), the
plugin draws the two layers and moves them by different amounts:

- **Workspaces:** the view drifts sideways as you go from workspace 1 to 10.
- **Mouse:** on an empty desktop, both layers follow the cursor slightly.

The foreground moves about 3x as far as the background. Wallpapers without a
`parallax/` folder are shown exactly as the stock plugin shows them.

## Install

Clone the stock plugin (this also switches your shell over to the clone), then
replace its `Background.qml` with this one:

```bash
omarchy plugin clone omarchy.background
cp Background.qml ~/.config/omarchy/plugins/$USER.background/Background.qml
omarchy restart shell
```

To go back to the stock plugin, swap `$USER.background` for `omarchy.background`
in `~/.config/omarchy/shell.json`.

## Tuning

In `Background.qml`:

- `parallaxPad` (40): how far the layers are enlarged past the screen edges
- `offsetX * 12` / `offsetY * 6` on `pbg`: background movement in px
- `offsetX * 34` / `offsetY * 16` on `fg`: foreground movement in px
