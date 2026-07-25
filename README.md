# Stage Sheets

A self-contained, offline-capable chord sheet and setlist manager built for live keyboard performance. No server, no build step, no dependencies — one HTML file.

---

## Features

### Library
- Song library with **folders and nested subfolders** (up to 3 levels deep)
- Per-song: title, artist, key, capo, tempo, chord sheet
- **Sort** by title, artist, or date created
- **Search** with inline clear button
- **Archive** songs non-destructively
- **Right-click context menu**: move to folder, add to setlist, archive, delete
- **Drag** songs between folders; drag folders to reorder

### Chord editor
- Monospace textarea with **live preview pane** (split, resizable)
- Formatting toolbar: **H1 / H2 / H3** headings, **Bold**, *Italic*, <u>Underline</u>, ~~Strikethrough~~
- **8 colour swatches** + hex colour syntax `{red:text}` or `{#ff8800:text}`
- **Section labels** auto-detected: `[Verse]`, `[Chorus]`, etc.
- **Chord detection** with colouring — standard chords, slash chords (`C/G`, `D/F#`), sus/dim/aug/add, bar notation (`| C | G | Am | F |`)
- **Strip lyrics** — remove lyric lines, keep chords and sections (respects selection)
- **Reflow chords** — redistribute chord tokens into N-per-line (respects selection)
- **Transpose** −/+ semitones with ♯/♭ toggle; per-song transpose memory
- **Find chords** button — opens Ultimate Guitar search for the song

### Page preview
- Scaled **page preview** matching the selected paper size
- Zoom controls (−/%) with stored zoom level
- Resizable split between editor and preview (drag handle)
- Respects margin, padding, and font size settings

### Perform view
- Song renders as a **page on a desk** — correct paper size, shadow, padding
- Sheet scroll, **prev/next song** navigation within a setlist
- Keyboard shortcuts: `← →` prev/next, `↑ ↓` transpose, `[ ]` font size
- Configurable **default view** (Perform or Edit) when opening a song

### Setlists
- Create setlists with **sub-setlists** (one level of nesting)
- Proper **breadcrumb navigation** (Sets › Vol.1 › Sub-set)
- **Drag-to-reorder** songs within a setlist
- **Drag-to-reorder** setlists and sub-setlists
- Add songs via right-click → "Add to setlist" from the song library
- **Play set** — opens first song in setlist context, ◀ ▶ navigates through
- **Print set** — prints all songs in the set, one per page

### Print / PDF
- **Print theme**: Light (paper) or Dark (PDF/tablet)
- **Page size**: A4, A5, A3, Letter, Legal, Tabloid, Custom (mm)
- **Page margins**: None / Narrow (12.7mm) / Normal (18mm) / Wide (25.4mm)
- **Text padding**: None / Small / Generous
- **PDF filename**: Artist – Title or Title – Artist
- Prints only the perform view, never the editor

### File management
- **File System Access API** (desktop Chrome/Edge): Open, Save, Save as, Reconnect
- **Fallback** (iOS / Firefox): Load JSON / Save JSON download
- Data file: `stagesheets-data.json` — store on OneDrive for cross-device access
- **Import** via file picker (replaces current library with confirmation)

---

## Usage

### Getting started
1. Download `StageSheets.html`
2. Open it in **Chrome** or **Edge** (desktop recommended for full FSA support)
3. Click **Save as…** and save `stagesheets-data.json` to your OneDrive folder
4. Add songs with the **+** button, paste chords from [Ultimate Guitar](https://www.ultimate-guitar.com)

### Cross-device workflow
- Edit on your MacBook → **Save** writes to OneDrive automatically
- Open on your tablet → click **Open…** → pick the same JSON from OneDrive
- OneDrive syncs the file; Stage Sheets reads and writes it directly

### Chord syntax
```
[Verse]
G                D
I found a love for me
Em               C
Darling just dive right in
```

### Formatting syntax
| Syntax | Result |
|---|---|
| `# Title` | H1 heading |
| `## Section` | H2 heading |
| `### Note` | H3 heading |
| `**text**` | **Bold** |
| `_text_` | *Italic* |
| `__text__` | Underlined |
| `~~text~~` | ~~Strikethrough~~ |
| `{red:text}` | Coloured text |
| `{#ff8800:text}` | Hex colour |
| `[Verse]` | Auto-styled section label |

### Keyboard shortcuts
| Key | Action |
|---|---|
| `← →` | Previous / next song (in a setlist) |
| `↑ ↓` | Transpose up / down |
| `[ ]` | Smaller / larger text |

---

## Browser support

| Browser | File access | Notes |
|---|---|---|
| Chrome (desktop) | ✅ Full FSA | Recommended |
| Edge (desktop) | ✅ Full FSA | Recommended |
| Safari (desktop) | ⚠️ Partial | FSA support varies |
| Firefox | ❌ No FSA | Use Load/Save JSON buttons |
| Chrome iOS | ❌ No FSA | Use Load/Save JSON buttons |
| Edge iOS | ❌ No FSA | Use Load/Save JSON buttons |

All browsers can use the app fully — the FSA limitation only affects direct file write. On non-FSA browsers, use **Save JSON** to download and **Load JSON** to import.

---

## File structure

```
stagesheets/
├── StageSheets.html        # The entire application (single file)
├── README.md               # This file
└── CHANGELOG.md            # Version history
```

The JSON data file lives separately (on OneDrive or wherever you choose) and is never committed to the repo — it contains your personal song library.

---

## Development

The app is intentionally a single HTML file with no build step, no bundler, and no external dependencies (fonts are loaded from Google Fonts when online; the app works offline otherwise).

The `<script>` block is divided into labelled regions for navigation:

- `FILE SYSTEM ACCESS & PROJECT BAR`
- `DATABASE`
- `MUSIC THEORY` — chord detection, transpose, render
- `STATE` — variables, persist, load
- `SIDEBAR` — songs, folders, drag-drop, context menus
- `MAIN` — perform view, editor, toolbar
- `NAVIGATION` — openSong, addSong, setlist navigation
- `PRINT & PAGE SETTINGS`
- `FILE I/O` — import, export, FSA open/save

To edit: open `StageSheets.html` in VS Code. Use the region comments to navigate. No npm, no terminal needed.

---

## Version

Current version is shown in the top bar next to "SONGS & SETLISTS".

See [CHANGELOG.md](CHANGELOG.md) for full history.

---

## License

Personal use. Not for redistribution.
