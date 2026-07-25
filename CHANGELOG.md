# Changelog

All notable changes to Stage Sheets are documented here.

---

## v3.2.0 — 2026-07-25

### Added
- **Strip lyrics respects selection** — selecting lines in the editor before clicking Strip lyrics now strips only the selection
- **Default view toggle** — slider switch in the top bar to set whether clicking a song opens in Perform or Edit mode (persisted to data file)
- **Clear button in search** — × icon inside the search field to clear the filter without losing keyboard focus
- **Reflow chords** replaces Compact — prompts for N chords per line, redistributes chord tokens accordingly; respects selection

### Fixed
- Search input lost focus after every keystroke (full sidebar re-render replaced the input element); now only the list content re-renders on search
- Save button returned to Perform view even when editing; now stays on the current view

---

## v3.1.0 — 2026-07-21

### Added
- **Page size selector** — A4, A5, A3, Letter, Legal, Tabloid, Custom (mm) in print settings
- **Scaled page preview** in editor — preview pane shows the actual paper size as a scaled card with correct aspect ratio
- **Preview zoom controls** — −/% /+ buttons and Fit; zoom level persisted to data file
- **Perform view page-on-desk** — song renders as a physical page card on a grey desk background, sized to the selected paper
- **Resizable editor/preview split** — drag handle between textarea and preview; split ratio persisted
- **Print settings slide-up panel** — Page size, Print theme, Margins, Padding, PDF filename hidden behind a ⚙ button to free up space
- **Sub-setlists** — setlists can have one level of nested sub-setlists
- **Breadcrumb navigation** for setlists — `Sets › Vol.1 › Sub-set` with clickable segments
- **Drag-to-reorder setlists** and sub-setlists via ⠿ handle
- **Add to setlist** from song right-click context menu
- **Drag-to-reorder songs** within a setlist (replacing ▲▼ buttons)
- **Strip lyrics** toolbar button — removes lyric lines, keeps chords, sections, headings; collapses multiple blank lines
- **Version indicator** in top bar
- **Region comments** throughout the script for code navigation
- **Per-song transpose memory** shown in sidebar meta line

### Fixed
- Printing from Edit mode printed the editor form; now switches to Perform view, prints, then returns
- Dark print theme showed white border; `@page { margin: 0 }` added
- Page margins and text padding now apply correctly in print via CSS `@page` and `--print-padding`
- `loadFromData` did not reset tab/filter/collapsedFolders; fixed with explicit resets and `setTimeout` defer

---

## v3.0.0 — 2026-07-20

### Added
- **Folder system** — songs can be organised into folders and nested subfolders (up to 3 levels)
- **Drag-to-reorder folders** and songs between folders via ⠿ handle
- **Sort bar** — sort by Title, Artist, or Date created
- **Archive songs** — non-destructive hide; archived badge count; Show/Hide toggle
- **Right-click context menu** on songs: Archive, Move to folder, Delete, New folder from context
- **Right-click context menu** on folders: Rename, Delete folder (keep songs)
- **New folder from song context menu** — creates folder and moves song in one step
- **Nested folder visual styling** — left border line, inset background, subtler text
- **File System Access API** — Open, Save, Save as, Reconnect file; IndexedDB handle persistence
- **Non-FSA fallback** (iOS) — Load JSON / Save JSON download buttons
- **Import** via file picker with confirmation dialog
- **Editor/preview split pane** with live preview
- **H1/H2/H3 headings** via toolbar or `#`/`##`/`###` syntax
- **Bold, Italic, Underline, Strikethrough** via toolbar or `**`/`_`/`__`/`~~` syntax
- **8 colour swatches** + hex colour via `{colour:text}` syntax
- **Print theme** (Light/Dark) — controls PDF/print output colour scheme
- **Page margins** preset (None/Narrow/Normal/Wide)
- **Text padding** preset
- **PDF filename order** (Artist–Title or Title–Artist) — dynamic `document.title` before print
- **Setlists** — create, rename, reorder songs, play set, print set
- **Mobile responsive** — slide-in sidebar drawer with overlay, 44px tap targets, iOS zoom prevention
- **Dark/light theme** toggle
- **Keyboard shortcuts** — `← →` prev/next song in set, `↑ ↓` transpose, `[ ]` font size

### Fixed
- Bar notation (`| C | G | Am |`) now correctly detected as chord lines; pipes shown as dim separators
- Slash chords (`C/G`, `D/F#`, `Bm/D`) correctly coloured and transposed

---

## v2.0.0 — 2026-07-10

### Added
- Setlist system — create setlists, add songs, reorder with ▲▼, play set, print set
- Set context bar showing set name, position, and next song
- Per-song transpose memory
- Auto-scroll with speed slider
- Built-in metronome with tap tempo (later removed in v2.1.0)
- Keyboard shortcuts (Space = scroll, ← → = prev/next, ↑ ↓ = transpose)
- Print single song and print full set

---

## v1.0.0 — 2026-06-03

### Initial release
- Single-file HTML chord sheet library
- Song list with search
- Chord detection and amber colouring
- Section label detection (`[Verse]`, `[Chorus]`, etc.)
- Transpose −/+ with ♯/♭ toggle
- Font size control
- Auto-scroll
- Dark/light theme
- Ultimate Guitar deep-link per song
- Print support
- localStorage persistence
