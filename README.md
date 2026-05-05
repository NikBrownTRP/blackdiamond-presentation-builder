# Sales Presentation Generator — Black Diamond Equipment

A web-based tool for creating professional sales presentations for **Black Diamond Equipment**. Built for product managers and sales teams who need to quickly assemble on-brand slide decks without design tools.

> **Zero dependencies.** Just open `index.html` in a browser and start building, or visit the hosted GitHub Pages URL once published.

---

## Builder Interface

The builder uses a three-panel layout: a slide list sidebar, a live preview, and a content editor.

- **Left sidebar** — slide list with thumbnails, drag-and-drop reordering, duplicate, hide/show, and delete controls
- **Top area** — live 16:9 preview that updates in real-time as you type
- **Bottom area** — dynamic form editor that adapts to the selected slide template
- **Editable title** — click the presentation name in the header to rename

---

## Brand Theme

Every slide uses the **Black Diamond** theme:

| Property   | Value                                            |
|------------|--------------------------------------------------|
| Background | Pure black `#000000`                             |
| Text       | White `#FFFFFF` / muted off-white `#C8C2B8`      |
| Accent     | Burnt Sienna `#B0532D`                           |
| Headings   | Oswald 700, uppercase, slight tracking           |
| Body       | Inter                                            |
| Logo       | Black Diamond white wordmark + diamond mark      |
| Brand line | "Live. Climb. Repeat." (editable per slide)      |

The palette and typography are derived from [eu.blackdiamondequipment.com](https://eu.blackdiamondequipment.com).

---

## Slide Templates

Seven templates cover common sales presentation needs.

| Template | Purpose | Key Fields |
|----------|---------|------------|
| **Title Page** | Opening brand statement | Title, subtitle, brand line, logo, background image |
| **Product Presentation** | Hero product showcase | Product name, tagline, selling points, image, badge |
| **Product Gallery** | Multi-image showcase | Heading, up to 3 images with captions, layout options |
| **Product Spec** | Technical details | Product name, specs table, features list, image |
| **Header + List** | Flexible content slide | Heading, bullet list, optional image, layout choice |
| **Data & Graph** | Charts and data visuals | Bar chart, XY line plot, or image + up to 8 detail notes |
| **Spotlight** | Apple-keynote-style highlight | Headline, tagline, full-bleed image, stat grid |

You can change a slide's template later without losing content — compatible fields (heading, image, bullets) carry over to the new template.

---

## Save / Load / Export

- **Save** — download as a `.json` file you can re-load later
- **Load** — open a previously saved `.json`, an exported `.html` (re-importable), or a `.pptx` (slides are auto-mapped to the closest template)
- **Export HTML** — single-file standalone slideshow (all images and CSS embedded as data URLs; works offline, on any device)
- **Export PDF** — multi-page PDF, one slide per page
- **Auto-save** — the in-progress deck is persisted to IndexedDB and restored on refresh

---

## Keyboard Shortcuts

| Shortcut          | Action                  |
|-------------------|-------------------------|
| `Ctrl/Cmd + S`    | Save                    |
| `F`               | Fullscreen preview      |
| `←` / `→`         | Previous / next slide   |
| `Esc`             | Exit fullscreen / modal |

---

## Local Development

```bash
# Serve locally (any static server works)
python3 -m http.server 8091
open http://localhost:8091/
```

After editing `css/slides.css`, run `bash build-css.sh` to re-embed the CSS into `index.html`'s `window.__SLIDES_CSS__` string. This is required so the **Export HTML** output renders correctly without external CSS files.

---

## Project Structure

```
.
├── index.html              # Single-page app
├── css/
│   ├── builder.css         # Builder UI chrome
│   └── slides.css          # Slide theme + template styles
├── js/
│   ├── controller.js       # State, CRUD, event wiring (entry point)
│   ├── templates.js        # 7 template definitions + render functions
│   ├── preview.js          # Live preview + fullscreen slideshow
│   ├── exporter.js         # JSON / HTML / PDF export
│   └── pptx-import.js      # PowerPoint → template mapper
├── assets/
│   ├── logo-bd-white.svg   # Black Diamond wordmark
│   └── placeholder.svg     # Default image fallback
├── vendor/
│   └── jszip.min.js        # Vendored for offline PPTX unzipping
└── build-css.sh            # Re-embeds slides.css into index.html
```

---

## Credits

Forked from the Tektro / TRP sales presentation generator. Theme rebuilt for Black Diamond Equipment.
