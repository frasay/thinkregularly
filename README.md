# think regularly

*A quiet pixel place for writers.*

A distraction-free writing app with the soul of a 90s electric typewriter and the look of a chilled 8-bit afternoon. One light-yellow page, drifting pixel clouds, a little typewriter that jiggles as you type.

## v2 — what changed

- **Audio fixed.** Browsers suspend the Web Audio context until a user gesture is registered by the page itself. v2 unlocks and resumes the context on *any* pointer/key/touch event (capture phase), routes everything through a compressor, and raises the gain. Sound now starts reliably on your first click or keypress.
- **Full 8-bit visual overhaul.** Pixel fonts (Press Start 2P + VT323), pixel-art typewriter, animated drifting clouds, pixel sun, subtle CRT scanlines, chunky hard-shadow buttons, paper card with a thick pixel border.

## Features

- **One quiet page** — pale yellow sky, a paper card, your words.
- **Autosaves as you write** — every keystroke saved to `localStorage` within ~350ms, with a pixel SAVING/SAVED indicator.
- **90s electric typewriter sounds, synthesized in code** (no audio files):
  - 4 daisy-wheel key variants with random pitch/tone jitter
  - Deeper **spacebar** thunk · softer **backspace** click
  - Mechanical clunk + **carriage-return ding** on Enter
- **Clean renaming** — the title at the top of the page *is* the filename. Click, type, Enter to drop into the body.
- **Drafts drawer** — `DRAFTS` button or `Ctrl+K`. Sorted by last touched. Create, open, delete.
- **Exports** — current piece as `.txt`, everything as `.json` backup.
- **Sound preference persists** between sessions.

## Keyboard shortcuts

| Keys | Action |
|---|---|
| `Ctrl+S` | Force save (it autosaves anyway) |
| `Ctrl+M` | Toggle typewriter sound |
| `Ctrl+K` | Open/close the drafts drawer |
| `Esc` | Close the drawer |
| `Enter` (in title) | Jump to the page |

## Running it

Single `index.html`, zero build dependencies (pixel fonts load from Google Fonts with monospace fallback). Open in any modern browser, or via GitHub Pages:

1. Repo **Settings → Pages**
2. Source: **Deploy from a branch**, branch `main`, folder `/ (root)`
3. App appears at `https://frasay.github.io/thinkregularly/`

## Notes

- Writing is stored in the browser you use. Use **BACKUP ALL** in the drafts drawer for a portable copy.
- Sound begins after your first interaction with the page (a browser autoplay rule — v2 handles this automatically).
- Built for laptop keyboards — Dell and ThinkPad approved.
