# 🎨 NoteDiscovery Theme Creator

A visual theme editor for [NoteDiscovery](https://github.com/gamosoft/NoteDiscovery). Pick colours, watch a live replica of the app update, and export a ready-to-use theme `.css` file.

Single HTML file. No build step, no dependencies, works offline.

## Features

- **Live preview** of the NoteDiscovery UI: icon rail, sidebar, toolbar, split editor and markdown preview, status colours, buttons and shadows
- **Every theme variable** from the [theme docs](https://github.com/gamosoft/NoteDiscovery/blob/main/documentation/THEMES.md) editable with a colour picker or hex field
- **Quick palette**: choose background, text and accent, and the rest is derived for you
- **Start from any built-in theme** (Dracula, Nord, Gruvbox, ...) or import an existing theme `.css`
- **Contrast checker** with AA/AAA ratings for text and accent colours
- **Hover a colour row** to outline where it is used in the preview
- **Export theme**: validated CSS with the `@theme-type` header, copy or download, plus install steps
- **Save project** as `.json` to keep editing later; your work is also kept in the browser automatically

## Usage

Best used on a desktop browser.

1. Open `notediscovery-theme-creator.html` in any modern browser.
2. Pick a starting theme, or generate a palette from three colours.
3. Fine-tune colours while watching the preview.
4. Click **Export theme**, then download the `.css`.

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

## License

MIT, same as NoteDiscovery. This is an unofficial community tool and is not affiliated with the NoteDiscovery project.
