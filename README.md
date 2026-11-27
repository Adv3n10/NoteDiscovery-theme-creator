# 🎨 NoteDiscovery Theme Creator

A visual theme editor for [NoteDiscovery](https://github.com/gamosoft/NoteDiscovery). Pick colours, watch a live replica of the app update, and export a ready-to-use theme `.css` file.

Single HTML file. No build step, no dependencies, works offline.

## Features

- **Live preview** of the NoteDiscovery UI: icon rail, sidebar, toolbar, split editor and markdown preview, status colours, buttons and shadows
- **Hover anything in the preview** to see which variables colour it and their values, and **click it** to jump to that colour
- **Every theme variable** from the [theme docs](https://github.com/gamosoft/NoteDiscovery/blob/main/documentation/THEMES.md), with a colour picker, hex/rgba field, opacity slider for `--accent-light`, and optional variables you can switch on or off
- **12 built-in themes** to start from (Dracula, Nord, Gruvbox, ...), shown as a grid with mini previews
- **Generator** that builds a full palette from one accent colour, dark or light, and keeps text readable (or press **Surprise me**)
- **Three-colour palette**: choose background, text and accent, and the rest is derived for you
- **Readability panel** that checks 15 text and background pairs (WCAG ratios), from body text to inline code, buttons and status messages
- **Undo and redo**, autosave in your browser, a changed-colour marker and per-colour reset to the starting value
- **Screen colour picker** (eyedropper) in Chromium-based browsers
- **Share a theme as a link**
- **Export**: validated CSS with the `@theme-type` header, colour swatches in the code view, download or copy, plus install steps
- **Import** a theme `.css` or saved project `.json` by dropping the file, choosing it, or pasting its contents
- **Save project** as `.json` to keep optional toggles, auto settings and shadow intensity
- Light, dark or system appearance for the editor itself
- Keyboard shortcuts: `Ctrl+Z` undo, `Ctrl+Shift+Z` redo, `Ctrl+S` download

## Usage

Best used on a desktop browser.

Use the [live version](https://adv3n10.github.io/NoteDiscovery-theme-creator/), or download this repo and open `index.html` in any modern browser. It is a single file with no build step and no server needed (fonts load from Google Fonts when online, and fall back to system fonts offline).

1. Pick a built-in theme, generate a palette from one colour, or derive one from three colours.
2. Fine-tune colours while watching the preview. Click any part of the preview to edit its colour.
3. Name your theme in the top bar, check the Readability panel, then click **Download** to save the `.css`.

## Installing your theme

1. Save the file as `themes/<theme-id>.css` in your NoteDiscovery folder. The file name must match the `data-theme` value.
2. *(Optional)* add an emoji for it in `backend/themes.py` under `theme_icons`.
3. Restart NoteDiscovery (`docker-compose restart`).
4. Select it in **Settings → Theme**. To make it the default for new browsers, set `ui.default_theme: <theme-id>` in `config.yaml`.

## Exported format

```css
/* @theme-type: dark */
/* My Awesome Theme - made with NoteDiscovery Theme Creator */

:root[data-theme="my-awesome-theme"] {
    /* Background colors */
    --bg-primary: #1f2937;
    /* ... all 19 required variables, plus optional syntax and link colours ... */
}
```

## Notes

- Code-block syntax colours in the preview approximate the app's highlight.js styles.
- Markdown callouts use fixed colours in NoteDiscovery and do not follow the theme.
- The preview replicates styles from NoteDiscovery's `index.html` and `markdown-preview.css`; if upstream changes them, the preview may drift slightly.

## Credits

Built with Claude (Anthropic).

## License

MIT, same as NoteDiscovery. This is an unofficial community tool and is not affiliated with the NoteDiscovery project.
