# think regularly

*A quiet 8-bit place for writers.*

A distraction-free writing app with the soul of a 90s electric typewriter and the look of a chill 8-bit afternoon. One warm yellow page, a pixel sun, slow-drifting clouds, and your words.

**Live:** https://frasay.github.io/thinkregularly/

## Features

- **One quiet page** — a light yellow-tinged paper sheet with chunky pixel borders. Nothing else fights for attention.
- **Autosaves as you write** — every keystroke saved to your browser (`localStorage`) within a third of a second, with a subtle `SAVED` readout in the status bar.
- **90s electric typewriter sounds** — synthesized entirely in code with the Web Audio API (no audio files, instant playback):
  - 4 daisy-wheel key variants with random pitch/tone jitter so no two taps sound alike
  - A deeper **spacebar** thunk
  - A softer **backspace** click
  - A mechanical clunk + **carriage-return ding** on Enter
- **Clean renaming** — the title at the top of the page *is* the filename. Click, type, Enter drops you into the body.
- **Multiple pieces** — a drafts drawer (`DRAFTS` or `Ctrl+K`) lists everything sorted by last touched. Create, open, delete.
- **Take your words with you** — `SAVE .TXT` downloads the current piece; `BACKUP ALL` exports a `.json` of everything.
- **8-bit chill** — pixel fonts (Press Start 2P + VT323), CRT scanlines, vignette, a pixel sun, drifting pixel clouds, and a little mint LED that blinks as you type.

## The v2 audio fix

Browsers create `AudioContext` in a **suspended** state until a user gesture, and `resume()` is asynchronous. v1 scheduled sounds *before* the resume completed, so they were silently dropped on some machines. v2 routes every sound through a gate that waits for the context to actually be `running`, and additionally unlocks audio on the first click or keypress anywhere on the page. Sound preference (on/off) is remembered between sessions.

## Keyboard shortcuts

| Keys | Action |
|---|---|
| `Ctrl+S` | Force save (it autosaves anyway) |
| `Ctrl+M` | Toggle typewriter sound |
| `Ctrl+K` | Open/close the drafts drawer |
| `Esc` | Close the drawer |
| `Enter` (in title) | Jump to the page |

## Running it

A single `index.html`. Open it in any modern browser, or serve via GitHub Pages (Settings → Pages → deploy from `main`, root).

## Notes

- Writing is stored in the browser you use it in. Use **BACKUP ALL** for a portable copy.
- Sound starts on your first keypress or click (browser autoplay policy).
- Built for laptop keyboards — Dell and ThinkPad approved.
