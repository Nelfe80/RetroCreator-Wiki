# Themes

A theme changes the whole look of an overlay — font, colors, panel background,
glow — **without touching your layout or data bindings**. Switch themes any
time; your widgets keep working exactly the same.

## Picking a theme

In the **Designer**, use the 🎨 selector in the toolbar. The choice is saved
with the document, and every browser source displaying that overlay follows
instantly on reload.

Five themes ship with Retro Creator:

| Theme | Vibe |
|---|---|
| `arcade-neon` | default — dark panels, gold accent, violet glow |
| `crt-classic` | green phosphor terminal, scanline-era monospace |
| `neogeo-red` | bold arcade cabinet, warm white on deep red |
| `minimal-broadcast` | clean, low-contrast, esports desk |
| `pixel-challenge` | playful pixel-party, magenta on purple |

The Lite edition uses the default theme; the selector unlocks with Pro.

## How a theme is built

A theme is just **five design tokens** — no images, no downloads, nothing to
license. Fonts are system fonts, colors are plain CSS values:

| Token | What it drives | Example |
|---|---|---|
| `font` | every text element | `"'Courier New',monospace"` |
| `text` | main text color | `"#c8ffc8"` |
| `accent` | scores, highlights, values | `"#7CFC00"` |
| `panel` | widget background | `"rgba(0,20,0,.88)"` |
| `shadow` | glow / drop shadow | `"0 0 6px rgba(124,252,0,.7)"` |

Because a theme carries **no media**, it weighs a few hundred bytes and can
never break an overlay: if a theme is missing, the default simply applies.

## Creating your own theme

1. Open your workspace folder: `%APPDATA%\RetroCreator\workspace`.
2. Create a `themes` folder if it does not exist.
3. Drop a JSON file per theme, for example `themes\sunset-drive.json`:

```json
{
  "id": "sunset-drive",
  "name": "Sunset Drive",
  "tokens": {
    "font": "'Segoe UI',system-ui,sans-serif",
    "text": "#ffe9d6",
    "accent": "#ff7a45",
    "panel": "rgba(30,12,24,.88)",
    "shadow": "0 2px 12px rgba(255,122,69,.55)"
  }
}
```

4. Reload the Designer — **Sunset Drive** appears in the 🎨 selector.

Rules of thumb:

- `id` is the technical name (lowercase, dashes) and must be unique;
  `name` is what the selector displays.
- Keep `panel` semi-transparent (`rgba(..., .7–.9)`) so gameplay stays visible
  behind the overlay.
- Test on a busy background: the `shadow` token is what keeps text readable.
- An invalid file is silently skipped — nothing can break your overlays.

Themes are also the first brick of **content packs**: a pack can ship several
themes (plus views and widgets) that install into the same workspace folders.
