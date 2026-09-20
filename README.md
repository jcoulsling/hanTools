# Hän Language Tools

A small suite of self-contained, offline-first HTML tools for Hän language
work — a picture-book layout editor, a syllabics word processor, a lesson
editor, and a lyric slide presenter. No build step, no dependencies beyond
what's already inlined in each file.

## Files

- **`index.html`** — launcher page; links to the four tools below
- **`print-layout-editor.html`** — Storybook Creator: page layout, text
  boxes, drag/resize, effects, PDF crop-import, print export
- **`han-word-processor.html`** — Syllabics Word Processor: CLC
  romanization → Unified Canadian Aboriginal Syllabics
- **`han-lesson-editor.html`** — Lesson Editor: paste raw notes, get an
  auto-formatted lesson document
- **`lyric-slides.html`** — Lyric Slides: bilingual song presenter

## Running locally

These are plain static files — no server or build required. Clone the repo
and open `index.html` directly in a browser, or serve the folder with any
static file server, e.g.:

```
python3 -m http.server 8000
```

then visit `http://localhost:8000`.

**Keep all five files in the same folder.** The launcher's links are
relative, and the Storybook Creator's syllabics mode talks to
`han-word-processor.html` directly (via a hidden iframe + postMessage) —
both break if the files are split up or renamed.

## Deploying

This repo needs no build step, so it works as-is on any static host:

- **Render** (Static Site): connect this repo, leave the build command
  empty, set the publish directory to `.` (repo root).
- **GitHub Pages**: enable Pages on this repo (Settings → Pages), serve
  from the root of the default branch.
- **Netlify / Vercel / any static host**: same idea — no build command,
  publish directory is the repo root.

## Notes

- Each HTML file is self-contained (styles, scripts, and in the word
  processor's case, an embedded custom font, are all inlined) except for
  a handful of CDN script/font includes (pdf.js, Google Fonts, mammoth.js)
  loaded at runtime — an internet connection is needed for those specific
  features (PDF import, custom fonts, .docx import) even though the tools
  otherwise work offline.
- Per-viewer data (autosave, etc.) is kept in the browser's local storage,
  not synced anywhere — nothing here talks to a backend.
